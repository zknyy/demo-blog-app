# 演示应用 blog

## 准备

建议先做好以下准备

1. 安装 JDK9+ （建议 JDK11）
2. 安装 IntelJ IDEA
3. 安装 Maven 并配置环境变量和国内镜像仓库
4. 安装 NodeJS 和 npm 并配置国内镜像仓库
5. 安装 Docker 配置国内镜像仓库
6. 安装 docker-compose
7. 安装 Kubernates 和 Helm

## 安装 JHipster

执行

```shell
npm install -g generator-jhipster
```

创建目录，执行

```shell
mkdir  demo-blog-app  && cd  demo-blog-app
```

初始化项目，执行

```shell
jhipster
```

得到如下（其中有些步骤是需要根据实际情况进行选择的）

```
INFO! Using JHipster version installed globally
INFO! Running default command
INFO! Executing jhipster:app
INFO! Options: from-cli: true


        ██╗ ██╗   ██╗ ████████╗ ███████╗   ██████╗ ████████╗ ████████╗ ███████╗
        ██║ ██║   ██║ ╚══██╔══╝ ██╔═══██╗ ██╔════╝ ╚══██╔══╝ ██╔═════╝ ██╔═══██╗
        ██║ ████████║    ██║    ███████╔╝ ╚█████╗     ██║    ██████╗   ███████╔╝
  ██╗   ██║ ██╔═══██║    ██║    ██╔════╝   ╚═══██╗    ██║    ██╔═══╝   ██╔══██║
  ╚██████╔╝ ██║   ██║ ████████╗ ██║       ██████╔╝    ██║    ████████╗ ██║  ╚██╗
   ╚═════╝  ╚═╝   ╚═╝ ╚═══════╝ ╚═╝       ╚═════╝     ╚═╝    ╚═══════╝ ╚═╝   ╚═╝

                            https://www.jhipster.tech

Welcome to JHipster v6.9.1
Application files will be generated in folder: /Users/demo/git/demo-blog-app
 _______________________________________________________________________________________________________________

  Documentation for creating an application is at https://www.jhipster.tech/creating-an-app/
  If you find JHipster useful, consider sponsoring the project at https://opencollective.com/generator-jhipster
 _______________________________________________________________________________________________________________

WARNING! Java 8, 11, or 12 are not found on your computer. Your Java version is: 13.0.1
WARNING! Your Node version is not LTS (Long Term Support), use it at your own risk! JHipster does not support non-LTS releases, so if you encounter a bug, please use a LTS version first.
? Which *type* of application would you like to create? Monolithic application (recommended for simple projects)
? [Beta] Do you want to make it reactive with Spring WebFlux? No
? What is the base name of your application? blog
? What is your default Java package name? com.demo.blog
? Do you want to use the JHipster Registry to configure, monitor and scale your application? No
? Which *type* of authentication would you like to use? JWT authentication (stateless, with a token)
? Which *type* of database would you like to use? SQL (H2, MySQL, MariaDB, PostgreSQL, Oracle, MSSQL)
? Which *production* database would you like to use? MariaDB
? Which *development* database would you like to use? H2 with disk-based persistence
? Do you want to use the Spring cache abstraction? Yes, with the Redis implementation
? Do you want to use Hibernate 2nd level cache? Yes
? Would you like to use Maven or Gradle for building the backend? Maven
? Which other technologies would you like to use?
? Which *Framework* would you like to use for the client? Angular
? Would you like to use a Bootswatch theme (https://bootswatch.com/)? Default JHipster
? Would you like to enable internationalization support? Yes
? Please choose the native language of the application Chinese (Simplified)
? Please choose additional languages to install English
? Besides JUnit and Jest, which testing frameworks would you like to use?
? Would you like to install other generators from the JHipster Marketplace? No

Installing languages: zh-cn, en
Git repository initialized.
Generating 2,048 bit RSA key pair and self-signed certificate (SHA256withRSA) with a validity of 99,999 days
	for: CN=Java Hipster, OU=Development, O=com.demo.blog, L=, ST=, C=

KeyStore 'src/main/resources/config/tls/keystore.p12' generated successfully.

```

此项目的主要特性如下：

1. Monolithic application （准备用 Kubernates 来编排应用）
2. 数据库方面：开发环境用 H2, 生产用 MariaDB （准备用 Kubernates 来编排）
3. 使用 Redis 来做分布式缓存 （准备用 Kubernates 来编排）
4. 暂时没有使用搜索引擎，消息队列，Kafka 等中间件
5. 支持国际化（中文和英文）

## 启动

启动服务

```shell
./mvnw
```

1. 下载 Maven 插件和依赖

2. 安装 nodejs

   ```shell
   [INFO] Installing node version v12.16.1
   [INFO] Unpacking /Users/demo/.m2/repository/com/github/eirslett/node/12.16.1/node-12.16.1-darwin-x64.tar.gz into /Users/demo/git/demo-blog-app/node/tmp
   [INFO] Copying node binary from /Users/demo/git/demo-blog-app/node/tmp/node-v12.16.1-darwin-x64/bin/node to /Users/demo/git/demo-blog-app/node/node
   [INFO] Installed node locally.
   [INFO] Installing npm version 6.14.5
   [INFO] Downloading https://registry.npmjs.org/npm/-/npm-6.14.5.tgz to /Users/demo/.m2/repository/com/github/eirslett/npm/6.14.5/npm-6.14.5.tar.gz
   [INFO] No proxies configured
   [INFO] No proxy was configured, downloading directly
   [INFO] Unpacking /Users/demo/.m2/repository/com/github/eirslett/npm/6.14.5/npm-6.14.5.tar.gz into /Users/demo/git/demo-blog-app/node/node_modules
   [INFO] Installed npm locally.
   ```

3. 初始化/安装 项目

   ```shell
   [INFO] Running 'npm install' in /Users/demo/git/demo-blog-app
   ...
   [INFO]
   [INFO] audited 2409 packages in 18.135s
   [INFO]
   [INFO] 74 packages are looking for funding
   [INFO]   run `npm fund` for details
   [INFO]
   [INFO] found 4 vulnerabilities (3 low, 1 high)
   [INFO]   run `npm audit fix` to fix them, or `npm audit` for details
   ```

4. 给出前端操作提示

   ```shell
   [INFO] --- frontend-maven-plugin:1.10.0:npm (webpack build dev) @ blog ---
   [INFO] npm not inheriting proxy config from Maven
   [INFO] Running 'npm run webpack:build' in /Users/demo/git/demo-blog-app
   [INFO]
   [INFO] > blog@0.0.1-SNAPSHOT webpack:build /Users/demo/git/demo-blog-app
   [INFO] > npm run cleanup && npm run webpack:build:main
   [INFO]
   [INFO]
   [INFO] > blog@0.0.1-SNAPSHOT cleanup /Users/demo/git/demo-blog-app
   [INFO] > rimraf target/classes/static/ target/classes/aot
   [INFO]
   [INFO]
   [INFO] > blog@0.0.1-SNAPSHOT webpack:build:main /Users/demo/git/demo-blog-app
   [INFO] > npm run webpack -- --config webpack/webpack.dev.js --env.stats=minimal
   [INFO]
   [INFO]
   [INFO] > blog@0.0.1-SNAPSHOT webpack /Users/demo/git/demo-blog-app
   [INFO] > node --max_old_space_size=4096 node_modules/webpack/bin/webpack.js "--config" "webpack/webpack.dev.js" "--env.stats=minimal"
   ```

5. 执行 Webpack

   ```shell
   [INFO] Webpack: Starting ...
   ...
   Webpack: Starting ...
   [INFO]
   [INFO]    ✔ Compile modules
   [INFO]    ✔ Build modules
   [INFO]    ✔ Optimize modules
   [INFO]    ✔ Emit files
   [INFO]
   [INFO] Webpack: Finished after 51.035 seconds.
   [INFO]
   [INFO]  DONE  Compiled successfully in 51043ms2:56:15 PM
   [INFO]
   [INFO]    460 modules

   ```

6. 启动后台 BlogApp

   ```shell
   [INFO] --- spring-boot-maven-plugin:2.2.7.RELEASE:run (default-cli) @ blog ---
   [INFO] Attaching agents: []

           ██╗ ██╗   ██╗ ████████╗ ███████╗   ██████╗ ████████╗ ████████╗ ███████╗
           ██║ ██║   ██║ ╚══██╔══╝ ██╔═══██╗ ██╔════╝ ╚══██╔══╝ ██╔═════╝ ██╔═══██╗
           ██║ ████████║    ██║    ███████╔╝ ╚█████╗     ██║    ██████╗   ███████╔╝
     ██╗   ██║ ██╔═══██║    ██║    ██╔════╝   ╚═══██╗    ██║    ██╔═══╝   ██╔══██║
     ╚██████╔╝ ██║   ██║ ████████╗ ██║       ██████╔╝    ██║    ████████╗ ██║  ╚██╗
      ╚═════╝  ╚═╝   ╚═╝ ╚═══════╝ ╚═╝       ╚═════╝     ╚═╝    ╚═══════╝ ╚═╝   ╚═╝

   :: JHipster 🤓  :: Running Spring Boot 2.2.7.RELEASE ::
   :: https://www.jhipster.tech ::
   ```

7. 最后得到

```shell
......（中间有一段报错）
2020-06-21 14:56:49.632 DEBUG 5856 --- [  restartedMain] i.g.j.c.apidoc.SwaggerAutoConfiguration  : Starting Swagger
2020-06-21 14:56:49.648 DEBUG 5856 --- [  restartedMain] i.g.j.c.apidoc.SwaggerAutoConfiguration  : Started Swagger in 14 ms
WARNING: An illegal reflective access operation has occurred
WARNING: Illegal reflective access by org.xnio.nio.NioXnio$2 (file:/Users/demo/.m2/repository/org/jboss/xnio/xnio-nio/3.3.8.Final/xnio-nio-3.3.8.Final.jar) to constructor sun.nio.ch.KQueueSelectorProvider()
WARNING: Please consider reporting this to the maintainers of org.xnio.nio.NioXnio$2
WARNING: Use --illegal-access=warn to enable warnings of further illegal reflective access operations
WARNING: All illegal access operations will be denied in a future release
2020-06-21 14:56:50.630  INFO 5856 --- [  restartedMain] com.demo.blog.BlogApp                    : Started BlogApp in 16.274 seconds (JVM running for 17.366)
2020-06-21 14:56:50.638  INFO 5856 --- [  restartedMain] com.demo.blog.BlogApp                    :
----------------------------------------------------------
        Application 'blog' is running! Access URLs:
        Local:          http://localhost:8080/
        External:       http://127.0.0.1:8080/
        Profile(s):     [dev, swagger]
----------------------------------------------------------
```

浏览器打开 http://localhost:8080/

![welcome](https://raw.githubusercontent.com/zknyy/demo-blog-app/master/screenshot/welcome.png)

# 环境依赖

## Maven

查看当前激活的 profile

```shell
./mvnw help:active-profiles
```

得到

```shell
[INFO]
Active Profiles for Project 'com.demo.blog:blog:jar:0.0.1-SNAPSHOT':

The following profiles are active:

 - webpack (source: com.demo.blog:blog:0.0.1-SNAPSHOT)
 - dev (source: com.demo.blog:blog:0.0.1-SNAPSHOT)
```

激活/取消激活 profile [貌似下面的命令不起作用，应该用 mvn]

```shell
./mvnw package --activate-profiles prod
./mvnw package -P !prod
```

用不同的 profile 来启动，执行

```shell
./mvnw -P prod,swagger
```

得到

```shell
2020-06-21 16:28:06.721  INFO 7812 --- [           main] com.demo.blog.BlogApp                    : Started BlogApp in 12.252 seconds (JVM running for 12.69)
2020-06-21 16:28:06.730  INFO 7812 --- [           main] com.demo.blog.BlogApp                    :
----------------------------------------------------------
        Application 'blog' is running! Access URLs:
        Local:          http://localhost:8080/
        External:       http://127.0.0.1:8080/
        Profile(s):     [prod, swagger]
----------------------------------------------------------
```

## Redis

启动 Redis 服务

```shell
docker-compose -f ./src/main/docker/redis.yml up -d
```

## MariaDB

启动 MariaDB 服务

```shell
docker-compose -f ./src/main/docker/mariadb.yml up -d
```

## phpmyadmin

启动 phpmyadmin，用于查看 MariaDB 数据，创建文件 ./src/main/docker/phpmyadmin.yml

```yaml
version: '2'
services:
  # Refers to https://github.com/fuadajip/dockercompose-mysql-phpmyadmin
  blog-phpmyadmin:
    image: phpmyadmin/phpmyadmin
    # links:
    #   - blog-mariadb
    ports:
      - '7777:80'
    environment:
      - PMA_ARBITRARY=1
      - PMA_HOST=blog-mariadb
      - PMA_PORT=3306
      - PMA_USER=root
      - PMA_PASSWORD=
      - MYSQL_PASSWORD=root
      - MYSQL_ROOT_PASSWORD=
    restart: always
```



## 结合 MariaDB + phpmyadmin

创建文件 src/main/docker/mariadb-phpmyadmin.yml 用于单独启动MariaDB + phpmyadmin

```shell
version: '2'
services:
  blog-mariadb:
    extends:
      file: mariadb.yml
      service: blog-mariadb
  blog-phpmyadmin:
    extends:
      file: phpmyadmin.yml
      service: blog-phpmyadmin
```

执行

```shell
docker-compose -f ./src/main/docker/mariadb-phpmyadmin.yml up -d
```

打开浏览器 http://localhost:7777 用户名 root，密码为空，得到

![](https://raw.githubusercontent.com/zknyy/demo-blog-app/master/screenshot/phpmyadmin.png)





## 构建 Docker 镜像

使用[Jib](https://github.com/GoogleContainerTools/jib)连接到本地 Docker 守护程序构建应用程序的 Docker 镜像，根据构建工具不同执行以下操作：

- 使用 Maven, 输入: `./mvnw package -Pprod verify jib:dockerBuild`
- 使用 Gradle, 输入: `./gradlew -Pprod bootJar jibDockerBuild`

在没有 Docker 的情况下构建应用程序的 Docker 镜像并将其直接推送到 Docker 仓库中，根据构建工具不同执行以下操作：

- 使用 Maven, 输入:: `./mvnw package -Pprod verify jib:build`
- 使用 Gradle, 输入: `./gradlew -Pprod bootJar jib`

执行 `【为了完成测试需要先将支持的环境服务启动】`

```shell
./mvnw package -Pprod verify jib:dockerBuild
```

> 会执行前端打包，构建，后端编译，测试，打包，并生成 Dockerfile？

得到

```shell
[INFO] Using credentials from Docker config (/Users/demo/.docker/config.json) for adoptopenjdk:11-jre-hotspot
[INFO] Using base image with digest: sha256:9f53368957d42b201dc7b2f1f085067ab6a30ab9d18b9c2a2da6a7512fbdc117
[INFO]
[INFO] Container entrypoint set to [bash, -c, /entrypoint.sh]
[INFO]
[INFO] Built image to Docker daemon as blog
[INFO]
[INFO] A new version of Jib (2.4.0) is available (currently using 2.3.0). Update your build configuration to use the latest features and fixes!
[INFO] https://github.com/GoogleContainerTools/jib/blob/master/jib-maven-plugin/CHANGELOG.md
[INFO] Please see https://github.com/GoogleContainerTools/jib/blob/master/docs/privacy.md for info on disabling this update check.
[INFO]
[INFO] Executing tasks:
[INFO] [==============================] 100.0% complete
[INFO]
[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESS
[INFO] ------------------------------------------------------------------------
[INFO] Total time:  05:03 min
[INFO] Finished at: 2020-06-21T22:34:38+08:00
[INFO] ------------------------------------------------------------------------
```

检查，执行

```shell
docker images
```

得到名为 blog 的镜像

```
REPOSITORY          TAG     IMAGE ID            CREATED             SIZE
blog             latest     e5a275f41e16        4 minutes ago       297MB
```

## 容器整合 docker-compose 启动

修改文件：./src/main/docker/app.yml  增加对 blog-phpmyadmin 引用

```yaml
version: '2'
services:
  blog-app:
    image: blog
    environment:
      - _JAVA_OPTIONS=-Xmx512m -Xms256m
      - SPRING_PROFILES_ACTIVE=prod,swagger
      - MANAGEMENT_METRICS_EXPORT_PROMETHEUS_ENABLED=true
      - SPRING_DATASOURCE_URL=jdbc:mariadb://blog-mariadb:3306/blog?useLegacyDatetimeCode=false&serverTimezone=UTC
      - JHIPSTER_CACHE_REDIS_SERVER=redis://blog-redis:6379
      - JHIPSTER_CACHE_REDIS_CLUSTER=false
      # - JHIPSTER_CACHE_REDIS_SERVER=redis://blog-redis:6379
      # - JHIPSTER_CACHE_REDIS_CLUSTER=true
      - JHIPSTER_SLEEP=120 # gives time for mariadb server to start
    ports:
      - 8080:8080
  blog-mariadb:
    extends:
      file: mariadb.yml
      service: blog-mariadb
  blog-redis:
    extends:
      file: redis.yml
      service: blog-redis
  blog-phpmyadmin:
    extends:
      file: phpmyadmin.yml
      service: blog-phpmyadmin
```

执行

```shell
docker-compose -f app.yml up -d
```

得到

```
Creating network "docker_default" with the default driver
Creating docker_blog-app_1        ... done
Creating docker_blog-mariadb_1    ... done
Creating docker_blog-redis_1      ... done
Creating docker_blog-phpmyadmin_1 ... done
```

等待 120 秒后（The application will start in 120s...），打开浏览器访问 http://localhost:8080/ 得到

![welcome](https://raw.githubusercontent.com/zknyy/demo-blog-app/master/screenshot/welcome.png)

# 增强改造

为应用加入 DLS 

## JDL

打开 https://start.jhipster.tech/design-entities  选择 `Design Entities`

在 `Blog` 上 Open 查看得到

![welcome](https://raw.githubusercontent.com/zknyy/demo-blog-app/master/screenshot/JDL.png)

复制所有内容并创建文件 ./blog.jdl

```java
entity Blog {
    name String required minlength(3),
    handle String required minlength(2)
}

entity Entry {
	title String required,
	content String required ,
    date Instant required
}

entity Tag {
	name String required minlength(2)
}


relationship ManyToOne {
	Blog{user(login)} to User,
    Entry{blog(name)} to Blog
}

relationship ManyToMany {
	Entry{tag(name)} to Tag{entry}
}

paginate Entry, Tag with infinite-scroll
```

导入JDL，执行

```shell
jhipster import-jdl blog.jdl
```










# [TODO...]

# 以下是 JHipster Readme

---

# blog

This application was generated using JHipster 6.9.1, you can find documentation and help at [https://www.jhipster.tech/documentation-archive/v6.9.1](https://www.jhipster.tech/documentation-archive/v6.9.1).

## Development

Before you can build this project, you must install and configure the following dependencies on your machine:

1. [Node.js][]: We use Node to run a development web server and build the project.
   Depending on your system, you can install Node either from source or as a pre-packaged bundle.

After installing Node, you should be able to run the following command to install development tools.
You will only need to run this command when dependencies change in [package.json](package.json).

    npm install

We use npm scripts and [Webpack][] as our build system.

Run the following commands in two separate terminals to create a blissful development experience where your browser
auto-refreshes when files change on your hard drive.

    ./mvnw
    npm start

Npm is also used to manage CSS and JavaScript dependencies used in this application. You can upgrade dependencies by
specifying a newer version in [package.json](package.json). You can also run `npm update` and `npm install` to manage dependencies.
Add the `help` flag on any command to see how you can use it. For example, `npm help update`.

The `npm run` command will list all of the scripts available to run for this project.

### PWA Support

JHipster ships with PWA (Progressive Web App) support, and it's turned off by default. One of the main components of a PWA is a service worker.

The service worker initialization code is commented out by default. To enable it, uncomment the following code in `src/main/webapp/index.html`:

```html
<script>
  if ('serviceWorker' in navigator) {
    navigator.serviceWorker.register('./service-worker.js').then(function () {
      console.log('Service Worker Registered');
    });
  }
</script>
```

Note: [Workbox](https://developers.google.com/web/tools/workbox/) powers JHipster's service worker. It dynamically generates the `service-worker.js` file.

### Managing dependencies

For example, to add [Leaflet][] library as a runtime dependency of your application, you would run following command:

    npm install --save --save-exact leaflet

To benefit from TypeScript type definitions from [DefinitelyTyped][] repository in development, you would run following command:

    npm install --save-dev --save-exact @types/leaflet

Then you would import the JS and CSS files specified in library's installation instructions so that [Webpack][] knows about them:
Edit [src/main/webapp/app/vendor.ts](src/main/webapp/app/vendor.ts) file:

```
import 'leaflet/dist/leaflet.js';
```

Edit [src/main/webapp/content/scss/vendor.scss](src/main/webapp/content/scss/vendor.scss) file:

```
@import '~leaflet/dist/leaflet.css';
```

Note: There are still a few other things remaining to do for Leaflet that we won't detail here.

For further instructions on how to develop with JHipster, have a look at [Using JHipster in development][].

### Using Angular CLI

You can also use [Angular CLI][] to generate some custom client code.

For example, the following command:

    ng generate component my-component

will generate few files:

    create src/main/webapp/app/my-component/my-component.component.html
    create src/main/webapp/app/my-component/my-component.component.ts
    update src/main/webapp/app/app.module.ts

## Building for production

### Packaging as jar

To build the final jar and optimize the blog application for production, run:

    ./mvnw -Pprod clean verify

This will concatenate and minify the client CSS and JavaScript files. It will also modify `index.html` so it references these new files.
To ensure everything worked, run:

    java -jar target/*.jar

Then navigate to [http://localhost:8080](http://localhost:8080) in your browser.

Refer to [Using JHipster in production][] for more details.

### Packaging as war

To package your application as a war in order to deploy it to an application server, run:

    ./mvnw -Pprod,war clean verify

## Testing

To launch your application's tests, run:

    ./mvnw verify

### Client tests

Unit tests are run by [Jest][] and written with [Jasmine][]. They're located in [src/test/javascript/](src/test/javascript/) and can be run with:

    npm test

For more information, refer to the [Running tests page][].

### Code quality

Sonar is used to analyse code quality. You can start a local Sonar server (accessible on http://localhost:9001) with:

```
docker-compose -f src/main/docker/sonar.yml up -d
```

You can run a Sonar analysis with using the [sonar-scanner](https://docs.sonarqube.org/display/SCAN/Analyzing+with+SonarQube+Scanner) or by using the maven plugin.

Then, run a Sonar analysis:

```
./mvnw -Pprod clean verify sonar:sonar
```

If you need to re-run the Sonar phase, please be sure to specify at least the `initialize` phase since Sonar properties are loaded from the sonar-project.properties file.

```
./mvnw initialize sonar:sonar
```

or

For more information, refer to the [Code quality page][].

## Using Docker to simplify development (optional)

You can use Docker to improve your JHipster development experience. A number of docker-compose configuration are available in the [src/main/docker](src/main/docker) folder to launch required third party services.

For example, to start a mariadb database in a docker container, run:

    docker-compose -f src/main/docker/mariadb.yml up -d

To stop it and remove the container, run:

    docker-compose -f src/main/docker/mariadb.yml down

You can also fully dockerize your application and all the services that it depends on.
To achieve this, first build a docker image of your app by running:

    ./mvnw -Pprod verify jib:dockerBuild

Then run:

    docker-compose -f src/main/docker/app.yml up -d

For more information refer to [Using Docker and Docker-Compose][], this page also contains information on the docker-compose sub-generator (`jhipster docker-compose`), which is able to generate docker configurations for one or several JHipster applications.

## Continuous Integration (optional)

To configure CI for your project, run the ci-cd sub-generator (`jhipster ci-cd`), this will let you generate configuration files for a number of Continuous Integration systems. Consult the [Setting up Continuous Integration][] page for more information.

[jhipster homepage and latest documentation]: https://www.jhipster.tech
[jhipster 6.9.1 archive]: https://www.jhipster.tech/documentation-archive/v6.9.1
[using jhipster in development]: https://www.jhipster.tech/documentation-archive/v6.9.1/development/
[using docker and docker-compose]: https://www.jhipster.tech/documentation-archive/v6.9.1/docker-compose
[using jhipster in production]: https://www.jhipster.tech/documentation-archive/v6.9.1/production/
[running tests page]: https://www.jhipster.tech/documentation-archive/v6.9.1/running-tests/
[code quality page]: https://www.jhipster.tech/documentation-archive/v6.9.1/code-quality/
[setting up continuous integration]: https://www.jhipster.tech/documentation-archive/v6.9.1/setting-up-ci/
[node.js]: https://nodejs.org/
[yarn]: https://yarnpkg.org/
[webpack]: https://webpack.github.io/
[angular cli]: https://cli.angular.io/
[browsersync]: https://www.browsersync.io/
[jest]: https://facebook.github.io/jest/
[jasmine]: https://jasmine.github.io/2.0/introduction.html
[protractor]: https://angular.github.io/protractor/
[leaflet]: https://leafletjs.com/
[definitelytyped]: https://definitelytyped.org/
