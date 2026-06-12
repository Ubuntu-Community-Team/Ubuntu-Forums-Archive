---
title: "Ubuntu 16.04 Maven dependencies download"
date: 2018-03-03
forum: Programming Talk
---

### Post by Drenriza on 2018-03-03
I have been trying to install and configure maven with what resources i have been able to find online
```
apt-get install maven
```

> 
Apache Maven 3.3.9
Maven home: /usr/share/maven
Java Version: 1.8.0_151, vendor: Oracle Corporation
Java home: /usr/lib/jvm/java-8-openjdk-amd64/jre
default locale: en_GB, platform encoding: UTF-8
OS name: "linux", version: "4.4.0-112-generic", arch: "amd64", family: "unix"


In /usr/share/maven-repo i see alot of different repositories (i presume) that contain different jar files.

**THE GOAL**
What i am trying to do is to download [org.apache.oltu.oauth2.client]("https://search.maven.org/#search%7Cga%7C1%7Ca%3A%22org.apache.oltu.oauth2.client%22") AND ALL ITS DEPENDENCIES so i end up with a series
of .jar files that i can import to my project and use.

But i am not a Maven person (zero knowledge) and i find very little documentation or forum topics to help with this.
I have found [https://stackoverflow.com/questions/7908090/downloading-all-maven-dependencies-to-a-directory-not-in-repository/7912247](https://stackoverflow.com/questions/7908090/downloading-all-maven-dependencies-to-a-directory-not-in-repository/7912247)
but it does not specify where to place the .pom, or what directory (example) you need to stand in before executing
```
mvn dependency:copy-dependencies
```
And does the .jar files go into the path of where you executed the above command from? Or do they go to a home path somewhere like /usr/share/maven/something or /usr/share/maven-repo/something

Seeking advice
Thanks in advance

---

### Post by r-senior on 2018-03-03
> **Drenriza said:**
> What i am trying to do is to download [org.apache.oltu.oauth2.client]("https://search.maven.org/#search%7Cga%7C1%7Ca%3A%22org.apache.oltu.oauth2.client%22") AND ALL ITS DEPENDENCIES so i end up with a series
of .jar files that i can import to my project and use.
That's not quite how you use Maven in practice.

Maven is a build tool that manages dependencies. Given a project (with a Maven-friendly structure), you create pom.xml in your project directory and configure your project attributes and dependencies. You then run maven and ask it to build your project.

```
$ mvn compile
```

The first time you do this, you will see it download all sorts of JAR files into your ~/.m2 directory. This is your local Maven repository. Subsequent compiles just pick up the downloaded dependencies from here. You don't ask it to download JAR files that you can add to your project, it builds your project using dependencies that you specify.

The official Maven beginners tutorial: [https://maven.apache.org/guides/getting-started/maven-in-five-minutes.html](https://maven.apache.org/guides/getting-started/maven-in-five-minutes.html)

More tutorials here: [http://www.mkyong.com/tutorials/maven-tutorials/](http://www.mkyong.com/tutorials/maven-tutorials/)

Maven is a beast. Very good but daunting at first. I used to use it but these days I prefer Gradle, which is simpler to use IMO (and still compatible with Maven repositories).

[https://docs.gradle.org/current/userguide/tutorial_java_projects.html](https://docs.gradle.org/current/userguide/tutorial_java_projects.html)

---

### Post by Drenriza on 2018-03-03
What?? Is it mandatory to run mvn compile or what does it do?

I thought mvn compile builded something from source.

Ye i saw the Maven guide.. I would not really call it a guide though, more of a "lets slap w/e information we think is good together with no real order".
I must admit that this is extremely fustrating because their is just _**NO**_ good resource to Maven, seen from the perspective from someone who has none.

---

### Post by r-senior on 2018-03-03
Yes, mvn compile builds your project from its source. It brings in all the dependencies as JAR files, adds them to your classpath and runs javac to compile your sources.

Maybe we should go back a step and you explain what you are trying to do. I assumed that you have a Java project where you want to use OAuth, i.e. that you are writing Java code and need to use the OAuth libraries?

---

### Post by Drenriza on 2018-03-03
> **r-senior said:**
> Yes, mvn compile builds your project from its source. It brings in all the dependencies as JAR files, adds them to your classpath and runs javac to compile your sources.

Maybe we should go back a step and you explain what you are trying to do. I assumed that you have a Java project where you want to use OAuth, i.e. that you are writing Java code and need to use the OAuth libraries?

Yes i have a Java EE web project where i would like to use Oauth2.
I saw that Apache has a Oauth2 .jar file to get an access token and work with this
[http://oltu.apache.org/download.html](http://oltu.apache.org/download.html) -> Apache Oltu OAuth2

I found a .jar file to this at [https://search.maven.org/#search%7Cga%7C1%7Capache%20oltu%20oauth2%20client](https://search.maven.org/#search%7Cga%7C1%7Capache%20oltu%20oauth2%20client)
But this .jar depends on other jars.

So what i read on the WWW was that you could use Maven to fetch Apache Oltu OAuth2 and it's dependencies as .jar files.
And that is what i have been trying to do with no success.

---

### Post by r-senior on 2018-03-03
You can use Maven to fetch dependencies, but usually in conjunction with Maven building your project.

When you say Java EE web project, are you using EJBs? Or is this just a Java web project using servlet/JSP, etc?

How are you building it at the moment? From an IDE? Ant?

---

### Post by Drenriza on 2018-03-03
> **r-senior said:**
> You can use Maven to fetch dependencies, but usually in conjunction with Maven building your project.

When you say Java EE web project, are you using EJBs? Or is this just a Java web project using servlet/JSP, etc?

How are you building it at the moment? From an IDE? Ant?

Thanks for the reply r-senior!

It's a servlet / JSP project built in Eclipse.
I have not used Ant or any other system of that sort.

---

### Post by r-senior on 2018-03-03
OK, good. The reason I asked about EJB, i.e. a full Java EE application is that they are a bit more difficult. If it's a Java web application that's easier.

Java web applications really benefit from a build tool like Maven or Gradle. Yes you can get by with Eclipse, configuring the build path and adding JAR files, but it becomes a bit of a configuration headache. Even very small web applications will have upward of 30 JAR files once all the dependencies are pulled in. Trying to upgrade even one of them to a newer version can trigger a chain of upgrades.

My recommendation to you would be to spend some time converting your project to a Gradle build. You can still use Eclipse for development but an external build, apart from managing dependencies, gives you more flexibility. I know this means spending time doing something that you didn't intend to do, but it will pay dividends. Gradle will be easier for you than Maven.

You'll be able to add OAuth and any subsequent dependencies effortlessly. You'll be able to upgrade dependencies just by changing a number in a configuration file. You'll be able to run your application from a command line with an embedded servlet container, without having to fiddle around with a Tomcat instance. You'll be able to package a WAR file and deploy it direct to Tomcat. You'll have the option of switching from Eclipse to a different IDE, or doing small fixes and testing just using a terminal. Your life (well the Java web part of it) will be much easier.

Ubuntu 16.04 has Gradle in the repos, but it's old. You could try it, but I'd recommend downloading Gradle 4.x and installing it manually:

[https://gradle.org/install/#manually](https://gradle.org/install/#manually)

Once you can run "gradle -v", follow this tutorial up to the point where it starts unit testing with Mockito. (You can go through it all if you want, but up to that point is what you need).

[https://guides.gradle.org/building-java-web-applications/](https://guides.gradle.org/building-java-web-applications/)

If you can follow that, you can then delete the example servlet and JSP and move your application into the same directory structure. You'll then have an iterative process of adding dependencies to build.gradle to make your existing project build. I'd be surprised if there were many.

Then you can add the Eclipse plugin to the project and use Gradle to generate an Eclipse project that you can open in Eclipse.

Then you can add your OAuth dependency and start working with OAuth. You'll be in a a much better position to take your project forward when you are building independent of Eclipse.

EDIT: I don't suppose your project is up on Github is it?

---

### Post by r-senior on 2018-03-04
I still recommend converting your project to a Gradle build, but if you really want to use Maven to get the JAR files, you can do it. (I was curious).

Assuming you have maven installed ...

```
$ cd ~/Desktop
$ mkdir download
$ cd download

```

Searching on mvnrepository.com (which is one way we can find Maven artifacts) leads us to this page for OAuth2:

[http://mvnrepository.com/artifact/org.apache.oltu.oauth2/org.apache.oltu.oauth2.client/1.0.2](http://mvnrepository.com/artifact/org.apache.oltu.oauth2/org.apache.oltu.oauth2.client/1.0.2)

It tells us that this is the section we need to use in a Maven POM for the dependency:

```
<!-- https://mvnrepository.com/artifact/org.apache.oltu.oauth2/org.apache.oltu.oauth2.client -->
<dependency>
    <groupId>org.apache.oltu.oauth2</groupId>
    <artifactId>org.apache.oltu.oauth2.client</artifactId>
    <version>1.0.2</version>
</dependency>
```

So create pom.xml in the directory you created:

*pom.xml*
```
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
  xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/maven-v4_0_0.xsd">
  <modelVersion>4.0.0</modelVersion>
  <groupId>org.ubuntuforums</groupId>
  <artifactId>download</artifactId>
  <packaging>jar</packaging>
  <version>1.0-SNAPSHOT</version>
  <name>download</name>
  <url>http://maven.apache.org</url>
  <dependencies>
    <dependency>
      <groupId>org.apache.oltu.oauth2</groupId>
      <artifactId>org.apache.oltu.oauth2.client</artifactId>
      <version>1.0.2</version>
    </dependency>
  </dependencies>
</project>

```

Now you can run the copy-dependencies task:

```
$ mvn dependency:copy-dependencies 
[INFO] Scanning for projects...
[INFO] 
[INFO] ------------------------------------------------------------------------
[INFO] Building download 1.0-SNAPSHOT
[INFO] ------------------------------------------------------------------------
[INFO] 
[INFO] --- maven-dependency-plugin:2.8:copy-dependencies (default-cli) @ download ---
[INFO] Copying org.apache.oltu.oauth2.client-1.0.2.jar to /Users/richard/Desktop/download/target/dependency/org.apache.oltu.oauth2.client-1.0.2.jar
[INFO] Copying json-20140107.jar to /Users/richard/Desktop/download/target/dependency/json-20140107.jar
[INFO] Copying commons-codec-1.9.jar to /Users/richard/Desktop/download/target/dependency/commons-codec-1.9.jar
[INFO] Copying org.apache.oltu.oauth2.common-1.0.2.jar to /Users/richard/Desktop/download/target/dependency/org.apache.oltu.oauth2.common-1.0.2.jar
[INFO] Copying slf4j-api-1.7.7.jar to /Users/richard/Desktop/download/target/dependency/slf4j-api-1.7.7.jar
[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESS
[INFO] ------------------------------------------------------------------------
[INFO] Total time: 2.154 s
[INFO] Finished at: 2018-03-04T06:43:58Z
[INFO] Final Memory: 12M/114M
[INFO] ------------------------------------------------------------------------
```

So that's copied the dependencies to the 'target/dependency' directory.

```
$ ls target/dependency
commons-codec-1.9.jar			org.apache.oltu.oauth2.common-1.0.2.jar
json-20140107.jar			slf4j-api-1.7.7.jar
org.apache.oltu.oauth2.client-1.0.2.jar
```

I still recommend moving your build to Gradle (or Maven) but this answers your original question I think.

---

### Post by r-senior on 2018-03-04
Doing the same thing with Gradle is slightly easier:

Assuming you have gradle installed ...

```
$ cd ~/Desktop
$ mkdir downloadGradle

```

Create 'build.gradle' with the following:

```
plugins {
    id 'java'
}       

repositories {
    mavenCentral()
}

dependencies {
    compile 'org.apache.oltu.oauth2:org.apache.oltu.oauth2.client:1.0.2'
}

task download(type: Copy) {
    from configurations.compile into 'dependencies/'
}
```

Then just run the 'download' task, which downloads the dependencies into the dependency directory:

```
$ gradle download
$ ls dependencies/
commons-codec-1.9.jar			org.apache.oltu.oauth2.common-1.0.2.jar
json-20140107.jar			slf4j-api-1.7.7.jar
org.apache.oltu.oauth2.client-1.0.2.jar
```

---

### Post by Drenriza on 2018-03-07
**r-senior **you are a hero.

The information you gave was super helpful and resulted in more information that i was seeking, which was impossible for Maven for me.
So far super awesome.

I followed the guides you have linked, which resulted in a working gradle installation.
I have installed the gradle plugin shipbuilder in Eclipse and of i am.

I tried to follow the gradle guide to create a new web application, but ended up with an application where i could not reach index.html,
and i was greeted with a "Directory: project/path" message from the gradle web service.

I than tried to see if i could create a a gradle ready dynamic web project, but it does not seem that their is any "easy" way to do this?
So you get the file and folder structure from the project template along with the tomcat library and web module version.

---

### Post by r-senior on 2018-03-09
> **Drenriza said:**
> I tried to follow the gradle guide to create a new web application, but ended up with an application where i could not reach index.html,
and i was greeted with a "Directory: project/path" message from the gradle web service.
I don't know why that would be. What version of gradle are you running and when do you get this message?

Could you post the output of "ls -R" from the root of your project so that I can see the file structure you created?

> I than tried to see if i could create a a gradle ready dynamic web project, but it does not seem that their is any "easy" way to do this?
So you get the file and folder structure from the project template along with the tomcat library and web module version.
Do you mean an Eclipse "Dynamic Web Project"? This will have the wrong directory structure for Gradle/Maven.

Something that Maven does do better than Gradle is "archetypes", which are template projects. Gradle doesn't really have this concept so creating projects is more of a manual process. But it's not difficult and you end up deleting things you don't want from an archetype anyway:

```
$ mkdir MyProject
$ cd MyProject
$ mkdir -p src/{main,test}/java/my/package
$ mkdir -p src/main/webapp
```

... where "my/package" is replaced by whatever package structure you want, e.g. org/ubuntu/demo.

Obviously you'd add a minimal configuration to build.gradle, e.g. 

```
plugins {
    id 'war'  
}

repositories {
    jcenter()
}

dependencies {
    providedCompile 'javax.servlet:javax.servlet-api:3.1.0' 
    testCompile 'junit:junit:4.12'
}
```

You can then either use the Buildship plugin to make an Eclipse project (File - Import - Gradle - Existing Gradle Project), or you can use Gradle to do it:

[https://docs.gradle.org/current/userguide/eclipse_plugin.html](https://docs.gradle.org/current/userguide/eclipse_plugin.html)

You might try this in your build.gradle (note the 'eclipse-wtp' plugin)

```
plugins {
    id 'war'  
    id ''eclipse-wtp'
}

...
```

Then ask Gradle to make an Eclipse project:

```
$ gradle eclipse
```

Personally I don't use the IDE plugins. I prefer importing a basic Gradle project into the IDE but you might want to try.

---

### Post by Drenriza on 2018-03-13
Thanks for your reply 2r-senior

I took a fresh crack at Gradle again and managed to get a working website, meaning that the projects is now built / compiled
and with Tomcat i can see the webpage as expected (2 pages).

I ended up with a build.gradle as seen below
```

apply plugin: 'java'
apply plugin: 'war'
apply plugin: 'eclipse-twp'
apply plugin: 'com.bmuschko.tomcat'

repositories {
    jcenter()
}

dependencies {
    providedCompile 'javax.servlet:javax.servlet-api:3.1.0'
    testCompile 'junit:junit:4.12'
}

/*
TOMCAT BUILD CONFIGURATION
*/
repositiroes {
    mavenCentral()
}

dependencies {
    def tomcatVersion = '8.5.29'
    tomcat "org.apache.tomcat.embed:tomcat-embed-core:${tomcatVersion}",
    "org.apache.tomcat.embed:tomcat-embed-jasper:${tomcatVersion}"
}

tomcat {
    httpProtocol = 'org.apache.coyote.http11.Http11Nio2Protocol'
    ajpProtocol = 'org.apache.coyote.ajp.AjpNio2Protocol'
}

/*
TOMCAT BUILD SCRIPT BUILD CONFIGURATION - EXTERNAL DEPENDENCIES
*/
buildscript {
    repositories {
        jcenter()
    }
    
    dependencies {
        classpath 'com.bmuschko:gradle-tomcat-plugin:2.4.2'
    }
}

```

I am not entirely sure what all this does, for example it seems that all the Tomcat lines is for having a working local Tomcat server, that you can use for tests on your local machine but i was not able to find
any folders or files that would indicate this in the project folder. Nor can i see that gradle has downloaded a local copy of Tomcat 8.5.29 in /opt/gradle.

It also seems that Gradle understand my structure (woohoo), since it adheres to the web.xml that i used to set the welcome page.
> 
- src[INDENT]   - main[/INDENT]
[INDENT=2]     - java[/INDENT]
[INDENT=2]     - resources[/INDENT]
[INDENT=2]             - webapp
[/INDENT]
[INDENT=3]                   - META-INF[/INDENT]
[INDENT=3]                   - WEB-INF[/INDENT]
[INDENT=4]         * web.xml[/INDENT]
[INDENT=4]                         - lib
[/INDENT]
 
I am thinking this is due to the war plugin? I have not found a site / quote that actually confirms this.

All in all i now have a working Gradle project, win. So lets see if i now can also get a working oAuth2 project working.

@r-senior I have a question at this point.
When i create a normal "dynamic web application" through Eclipse, it also includes a 'deployment descriptor' that in Eclipse
gives an easy overview of how your web.xml is structured and linked. Do you know if i can add this in Eclipse to my Gradle project? Since it's nice for the eyes and ones understanding

I know that web.xml is considered an older 'technology' but i prefer it over annotations.

---

### Post by r-senior on 2018-03-13
> **Drenriza said:**
> I took a fresh crack at Gradle again and managed to get a working website, meaning that the projects is now built / compiled
and with Tomcat i can see the webpage as expected (2 pages).
Good progress!

Some suggestions for your build.gradle ...

1. Be careful with typing. On line 3 you have "eclipse-twp" but this should be "eclipse-wtp". On line 18, you have "repositiroes" but this should be "repositories". These two lines will be being ignored.

2. Yes, the "war" plugin is the plugin that understands the "webapp" part of the project:

[https://docs.gradle.org/current/userguide/war_plugin.html](https://docs.gradle.org/current/userguide/war_plugin.html)

Note that the "war" plugin extends the "java" plugin, so you don't need to include that one.

3. You will see many examples with "apply plugin" at the top but the newer form is like this (which is neater and less to type):

```
plugins {
    id 'war'
    id 'eclipse-wtp'
    id 'com.bmuschko.tomcat' version '2.4.2'
}
```

Note that you don't need the buildscript section any more:

[https://plugins.gradle.org/plugin/com.bmuschko.tomcat](https://plugins.gradle.org/plugin/com.bmuschko.tomcat)

So I think your build.gradle can be simplified to:

```
plugins {
    id 'war'
    id 'eclipse-wtp'
    id "com.bmuschko.tomcat" version "2.4.2"
}

repositories {
    jcenter()
}

dependencies {
    def tomcatVersion = '8.5.29'
    tomcat "org.apache.tomcat.embed:tomcat-embed-core:${tomcatVersion}",
    "org.apache.tomcat.embed:tomcat-embed-jasper:${tomcatVersion}"

    providedCompile 'javax.servlet:javax.servlet-api:3.1.0'
    testCompile 'junit:junit:4.12'
}

tomcat {
    httpProtocol = 'org.apache.coyote.http11.Http11Nio2Protocol'
    ajpProtocol = 'org.apache.coyote.ajp.AjpNio2Protocol'
}
```

> 
I am not entirely sure what all this does ...
Neither am I ;). The simplified version has four sections:

1. The Gradle plugins that you want to use.
2. The repositories where Gradle should search for dependencies. Usually mavenCentral() or jcenter().
3. A list of dependencies that Gradle will add to your classpath. It will add their dependencies (transitive dependencies) too.
4. Specific configuration for your Tomcat plugin.

> , for example it seems that all the Tomcat lines is for having a working local Tomcat server, that you can use for tests on your local machine but i was not able to find any folders or files that would indicate this in the project folder.
You have added a Tomcat plugin that provides a Tomcat server that Gradle can control. This plugin adds a "tomcatRun" task so that you can run your web application on Tomcat like this:

```
./gradlew tomcatRun
```

Note that you don't actually *need* this. You could just make a WAR file and copy it to the auto-deploy directory of an existing Tomcat installation if you have one. This Tomcat plugin is just a convenient way to start an embedded Tomcat server from Gradle.

See how you get on with this Tomcat plugin. I think you might find the Gretty plugin more useful but we can leave that for another day. It should be simple to switch from one server plugin to another.

> Nor can i see that gradle has downloaded a local copy of Tomcat 8.5.29 in /opt/gradle
Gradle downloads dependencies to a user cache directory, which is usually ~/.gradle/caches. It will be under there ... somewhere ;)

> When i create a normal "dynamic web application" through Eclipse, it also includes a 'deployment descriptor' that in Eclipse
gives an easy overview of how your web.xml is structured and linked.
The web.xml *is* the deployment descriptor but I think I know what you mean:

[ATTACH=CONFIG]278936[/ATTACH]

I think if you type "eclipse-wtp" correctly in your build.gradle, then run the "eclipse" task to make an Eclipse project, it will work.

```
./gradlew eclipse
```

In Eclipse, "File - Open Projects from File System" to open the project directly.

I've put my version of this demo project on Github in case I want to try things out as you make progress with it:

[https://github.com/sanhozay/WebDemo](https://github.com/sanhozay/WebDemo)

---

### Post by Drenriza on 2018-03-17
Thanks for your reply @r-senior!

Ye i had a few typos in my gradle.build, thanks.
I knew these were their because it worked, but when i wrote my reply here i was forced to write it by hand and introduced them (my bad).
This is cause the machine i tested Gradle on is my anti-virus VM machine that cannot copy to the clipboard of the host.

I tried the 
```
plugin {[INDENT]id 'plugin'
[/INDENT]
}
```

but my Gradle would not accept this structure, which is why i used the other one as you see.
Also thanks for the simplification example of the build file, gives alot in terms of understanding.

Thanks! i found the embedded tomcat under ~/.gradle/caches just as you said.
This is nice to know.

Quick question @r-senior
We added the javax-servlet api with
```

providedCompile 'javax.servlet:javax.servlet-api:3.1.0'

```
But how did you know to call it javax.servlet:javax.servlet-api:3.1.0 and not something else?
Also how can i through providedCompile add the javax.servlet.http.HttpServlet-api .jar file?

I looked here [https://mvnrepository.com/artifact/javax.servlet.jsp/jsp-api/2.2.1-b03](https://mvnrepository.com/artifact/javax.servlet.jsp/jsp-api/2.2.1-b03) but i have been told that gradle do not support the command
```

// https://mvnrepository.com/artifact/javax.servlet.jsp/jsp-api
provided group: 'javax.servlet.jsp', name: 'jsp-api', version: '2.2.1-b03'

```

---

### Post by Drenriza on 2018-03-17
Sneeky sneeky

> But how did you know to call it javax.servlet:javax.servlet-api:3.1.0 and not something else?
Also how can i through providedCompile add the javax.servlet.http.HttpServlet-api .jar file?

So at [https://mvnrepository.com/artifact/javax.servlet/javax.servlet-api](https://mvnrepository.com/artifact/javax.servlet/javax.servlet-api) it says
```

// https://mvnrepository.com/artifact/javax.servlet.jsp/jsp-api
provided group: 'javax.servlet.jsp', name: 'jsp-api', version: '2.2.1-b03'

```

But gradle (as far as i am told) does not have a provided group method. So one can use providedCompile which makes the
jar file available to the project at runtime, but is excluded from the .war container.

So the command is as follows
```

// https://mvnrepository.com/artifact/javax.servlet.jsp/jsp-api
provided group: 'javax.servlet.jsp'(1), name: 'jsp-api(2)', version: '2.2.1-b03(3)'

```

```

providedCompile 'javax.servlet.jsp(1):jsp-api(2):2.2.1-b03(3)'

```

This is what i see works through trial and error.

---

### Post by r-senior on 2018-03-20
When you write a Gradle build file, you are actually writing Groovy code. We don't need to get too deep into Groovy and the way it implements Domain Specific Languages (DSLs), but when you declare a dependency, you are actually calling a method:

```
providedCompile([group: 'javax.servlet', name: 'javax.servlet-api', version: '3.1.0'])
```

The argument there is a Map (just like a Java Map) with three keys "group, name and version". You can declare your dependency like this and it will work.

Groovy has a few shortcuts that you can use to make the syntax more readable. Let's look at these step by step:

1. Leave out the square brackets for the map. This is how Groovy provides named parameters:

```
providedCompile(group: 'javax.servlet', name: 'javax.servlet-api', version: '3.1.0')
```

2. Leave out the parentheses for the function call

```
providedCompile group: 'javax.servlet', name: 'javax.servlet-api', version: '3.1.0'
```

3. Gradle then allows you to just pass a string, where the group, name and version are delimited by ':'. I couldn't find the relevant source code but I assume this string is broken up using a string tokenizer and converted to a map.

```
providedCompile 'javax.servlet:javax.servlet-api:3.1.0'
```

When you look for dependencies on mvnrepository.com, it will give you the form in (2) and make some assumptions about how you would declare the dependency, i.e. "provided".

```
provided group: 'javax.servlet', name: 'javax.servlet-api', version: '3.1.0'
```

Provided means the JARs are provided by something outside your project, e.g. Tomcat. So they won't be packaged into your WAR file. Because some APIs, e.g. the servlet API have compile-time dependencies (the Java interfaces) and runtime dependencies (the implementations of those interfaces), the Gradle WAR plugin distinguishes them using "providedCompile" and "providedRuntime". The "providedCompile" dependencies are needed to compile your project. The "providedRuntime" are needed when Gradle runs your project.

It is confusing, I know. The suggestion on mvnrepository.com is not how it works with the Gradle WAR plugin. You need "providedCompile".

In your case, you want the servlet API to be used during compilation, so you can use either:

```
providedCompile 'javax.servlet:javax.servlet-api:3.1.0'
```

or 

```
providedCompile group: 'javax.servlet', name: 'javax.servlet-api', version: '3.1.0'
```

You don't need a "providedRuntime" for the servlet API because that is handled by your Tomcat plugin. 

You figured out what you needed to do. The above explanation is just there to fill in a few gaps and you don't need to understand it to use Gradle.

---

