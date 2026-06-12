---
title: "netbeans web application"
date: 2011-05-31
forum: Programming Talk
---

### Post by RobikShrestha on 2011-05-31
I installed netbeans
created a new web application project
did not do anything else
and tried to run it
It does not run and here are its logs: (Application log and TOMCAT log). I am surprised that even an empty project cannot run because there is nothing wrong I could have done with it. Please help.

init:
deps-module-jar:
deps-ear-jar:
deps-jar:
library-inclusion-in-archive:
library-inclusion-in-manifest:
compile:
compile-jsps:
In-place deployment at /home/robik/NetBeansProjects/WebApplication1/build/web
Deployment is in progress...
deploy?config=file%3A%2Ftmp%2Fcontext1959296253389793810.xml&path=/WebApplication1
[http://localhost:8080/manager/deploy?config=file%3A%2Ftmp%2Fcontext1959296253389793810.xml&path=/WebApplication1](http://localhost:8080/manager/deploy?config=file%3A%2Ftmp%2Fcontext1959296253389793810.xml&path=/WebApplication1)
/home/robik/NetBeansProjects/WebApplication1/nbproject/build-impl.xml:683: The module has not been deployed.
BUILD FAILED (total time: 36 seconds)








Listening for transport dt_socket at address: 11550
java.util.logging.ErrorManager: 4
java.io.FileNotFoundException: /usr/local/apache-tomcat-6.0.26/logs/catalina.2011-05-31.log (Permission denied)
        at java.io.FileOutputStream.openAppend(Native Method)
        at java.io.FileOutputStream.<init>(FileOutputStream.java:207)
        at java.io.FileOutputStream.<init>(FileOutputStream.java:131)
        at org.apache.juli.FileHandler.openWriter(FileHandler.java:328)
        at org.apache.juli.FileHandler.<init>(FileHandler.java:65)
        at org.apache.juli.FileHandler.<init>(FileHandler.java:56)
        at sun.reflect.NativeConstructorAccessorImpl.newInstance0(Native Method)
        at sun.reflect.NativeConstructorAccessorImpl.newInstance(NativeConstructorAccessorImpl.java:57)
        at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(DelegatingConstructorAccessorImpl.java:45)
        at java.lang.reflect.Constructor.newInstance(Constructor.java:532)
        at java.lang.Class.newInstance0(Class.java:372)
        at java.lang.Class.newInstance(Class.java:325)
        at org.apache.juli.ClassLoaderLogManager.readConfiguration(ClassLoaderLogManager.java:515)
        at org.apache.juli.ClassLoaderLogManager.readConfiguration(ClassLoaderLogManager.java:460)
        at org.apache.juli.ClassLoaderLogManager.readConfiguration(ClassLoaderLogManager.java:286)
        at java.util.logging.LogManager$2.run(LogManager.java:278)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.util.logging.LogManager.readPrimordialConfiguration(LogManager.java:276)
        at java.util.logging.LogManager.getLogManager(LogManager.java:259)
        at java.util.logging.Logger.<init>(Logger.java:245)
        at java.util.logging.LogManager$RootLogger.<init>(LogManager.java:1104)
        at java.util.logging.LogManager$RootLogger.<init>(LogManager.java:1101)
        at java.util.logging.LogManager$1.run(LogManager.java:199)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.util.logging.LogManager.<clinit>(LogManager.java:176)
        at java.util.logging.Logger.getLogger(Logger.java:307)
        at org.apache.juli.logging.DirectJDKLog.<init>(DirectJDKLog.java:71)
        at org.apache.juli.logging.DirectJDKLog.getInstance(DirectJDKLog.java:17
        at org.apache.juli.logging.LogFactory.getInstance(LogFactory.java:171)
        at org.apache.juli.logging.LogFactory.getInstance(LogFactory.java:243)
        at org.apache.juli.logging.LogFactory.getLog(LogFactory.java:29
        at org.apache.catalina.startup.Bootstrap.<clinit>(Bootstrap.java:55)
java.util.logging.ErrorManager: 4
java.io.FileNotFoundException: /usr/local/apache-tomcat-6.0.26/logs/localhost.2011-05-31.log (Permission denied)
        at java.io.FileOutputStream.openAppend(Native Method)
        at java.io.FileOutputStream.<init>(FileOutputStream.java:207)
        at java.io.FileOutputStream.<init>(FileOutputStream.java:131)
        at org.apache.juli.FileHandler.openWriter(FileHandler.java:32
        at org.apache.juli.FileHandler.<init>(FileHandler.java:65)
        at org.apache.juli.FileHandler.<init>(FileHandler.java:56)
        at sun.reflect.NativeConstructorAccessorImpl.newInstance0(Native Method)
        at sun.reflect.NativeConstructorAccessorImpl.newInstance(NativeConstructorAccessorImpl.java:57)
        at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(DelegatingConstructorAccessorImpl.java:45)
        at java.lang.reflect.Constructor.newInstance(Constructor.java:532)
        at java.lang.Class.newInstance0(Class.java:372)
        at java.lang.Class.newInstance(Class.java:325)
        at org.apache.juli.ClassLoaderLogManager.readConfiguration(ClassLoaderLogManager.java:515)
        at org.apache.juli.ClassLoaderLogManager.readConfiguration(ClassLoaderLogManager.java:460)
        at org.apache.juli.ClassLoaderLogManager.readConfiguration(ClassLoaderLogManager.java:286)
        at java.util.logging.LogManager$2.run(LogManager.java:27
        at java.security.AccessController.doPrivileged(Native Method)
        at java.util.logging.LogManager.readPrimordialConfiguration(LogManager.java:276)
        at java.util.logging.LogManager.getLogManager(LogManager.java:259)
        at java.util.logging.Logger.<init>(Logger.java:245)
        at java.util.logging.LogManager$RootLogger.<init>(LogManager.java:1104)
        at java.util.logging.LogManager$RootLogger.<init>(LogManager.java:1101)
        at java.util.logging.LogManager$1.run(LogManager.java:199)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.util.logging.LogManager.<clinit>(LogManager.java:176)
        at java.util.logging.Logger.getLogger(Logger.java:307)
        at org.apache.juli.logging.DirectJDKLog.<init>(DirectJDKLog.java:71)
        at org.apache.juli.logging.DirectJDKLog.getInstance(DirectJDKLog.java:17
        at org.apache.juli.logging.LogFactory.getInstance(LogFactory.java:171)
        at org.apache.juli.logging.LogFactory.getInstance(LogFactory.java:243)
        at org.apache.juli.logging.LogFactory.getLog(LogFactory.java:29
        at org.apache.catalina.startup.Bootstrap.<clinit>(Bootstrap.java:55)
java.util.logging.ErrorManager: 4
java.io.FileNotFoundException: /usr/local/apache-tomcat-6.0.26/logs/manager.2011-05-31.log (Permission denied)
        at java.io.FileOutputStream.openAppend(Native Method)
        at java.io.FileOutputStream.<init>(FileOutputStream.java:207)
        at java.io.FileOutputStream.<init>(FileOutputStream.java:131)
        at org.apache.juli.FileHandler.openWriter(FileHandler.java:32
        at org.apache.juli.FileHandler.<init>(FileHandler.java:65)
        at org.apache.juli.FileHandler.<init>(FileHandler.java:56)
        at sun.reflect.NativeConstructorAccessorImpl.newInstance0(Native Method)
        at sun.reflect.NativeConstructorAccessorImpl.newInstance(NativeConstructorAccessorImpl.java:57)
        at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(DelegatingConstructorAccessorImpl.java:45)
        at java.lang.reflect.Constructor.newInstance(Constructor.java:532)
        at java.lang.Class.newInstance0(Class.java:372)
        at java.lang.Class.newInstance(Class.java:325)
        at org.apache.juli.ClassLoaderLogManager.readConfiguration(ClassLoaderLogManager.java:515)
        at org.apache.juli.ClassLoaderLogManager.readConfiguration(ClassLoaderLogManager.java:460)
        at org.apache.juli.ClassLoaderLogManager.readConfiguration(ClassLoaderLogManager.java:286)
        at java.util.logging.LogManager$2.run(LogManager.java:27
        at java.security.AccessController.doPrivileged(Native Method)
        at java.util.logging.LogManager.readPrimordialConfiguration(LogManager.java:276)
        at java.util.logging.LogManager.getLogManager(LogManager.java:259)
        at java.util.logging.Logger.<init>(Logger.java:245)
        at java.util.logging.LogManager$RootLogger.<init>(LogManager.java:1104)
        at java.util.logging.LogManager$RootLogger.<init>(LogManager.java:1101)
        at java.util.logging.LogManager$1.run(LogManager.java:199)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.util.logging.LogManager.<clinit>(LogManager.java:176)
        at java.util.logging.Logger.getLogger(Logger.java:307)
        at org.apache.juli.logging.DirectJDKLog.<init>(DirectJDKLog.java:71)
        at org.apache.juli.logging.DirectJDKLog.getInstance(DirectJDKLog.java:17
        at org.apache.juli.logging.LogFactory.getInstance(LogFactory.java:171)
        at org.apache.juli.logging.LogFactory.getInstance(LogFactory.java:243)
        at org.apache.juli.logging.LogFactory.getLog(LogFactory.java:29
        at org.apache.catalina.startup.Bootstrap.<clinit>(Bootstrap.java:55)
java.util.logging.ErrorManager: 4
java.io.FileNotFoundException: /usr/local/apache-tomcat-6.0.26/logs/host-manager.2011-05-31.log (Permission denied)
        at java.io.FileOutputStream.openAppend(Native Method)
        at java.io.FileOutputStream.<init>(FileOutputStream.java:207)
        at java.io.FileOutputStream.<init>(FileOutputStream.java:131)
        at org.apache.juli.FileHandler.openWriter(FileHandler.java:328)
        at org.apache.juli.FileHandler.<init>(FileHandler.java:65)
        at org.apache.juli.FileHandler.<init>(FileHandler.java:56)
        at sun.reflect.NativeConstructorAccessorImpl.newInstance0(Native Method)
        at sun.reflect.NativeConstructorAccessorImpl.newInstance(NativeConstructorAccessorImpl.java:57)
        at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(DelegatingConstructorAccessorImpl.java:45)
        at java.lang.reflect.Constructor.newInstance(Constructor.java:532)
        at java.lang.Class.newInstance0(Class.java:372)
        at java.lang.Class.newInstance(Class.java:325)
        at org.apache.juli.ClassLoaderLogManager.readConfiguration(ClassLoaderLogManager.java:515)
        at org.apache.juli.ClassLoaderLogManager.readConfiguration(ClassLoaderLogManager.java:460)
        at org.apache.juli.ClassLoaderLogManager.readConfiguration(ClassLoaderLogManager.java:286)
        at java.util.logging.LogManager$2.run(LogManager.java:27
        at java.security.AccessController.doPrivileged(Native Method)
        at java.util.logging.LogManager.readPrimordialConfiguration(LogManager.java:276)
        at java.util.logging.LogManager.getLogManager(LogManager.java:259)
        at java.util.logging.Logger.<init>(Logger.java:245)
        at java.util.logging.LogManager$RootLogger.<init>(LogManager.java:1104)
        at java.util.logging.LogManager$RootLogger.<init>(LogManager.java:1101)
        at java.util.logging.LogManager$1.run(LogManager.java:199)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.util.logging.LogManager.<clinit>(LogManager.java:176)
        at java.util.logging.Logger.getLogger(Logger.java:307)
        at org.apache.juli.logging.DirectJDKLog.<init>(DirectJDKLog.java:71)
        at org.apache.juli.logging.DirectJDKLog.getInstance(DirectJDKLog.java:178)
        at org.apache.juli.logging.LogFactory.getInstance(LogFactory.java:171)
        at org.apache.juli.logging.LogFactory.getInstance(LogFactory.java:243)
        at org.apache.juli.logging.LogFactory.getLog(LogFactory.java:298)
        at org.apache.catalina.startup.Bootstrap.<clinit>(Bootstrap.java:55)
May 31, 2011 8:57:34 PM org.apache.catalina.core.AprLifecycleListener init
INFO: The APR based Apache Tomcat Native library which allows optimal performance in production environments was not found on the java.library.path: /usr/lib/jvm/java-6-openjdk/jre/lib/i386/server:/usr/lib/jvm/java-6-openjdk/jre/lib/i386:/usr/lib/jvm/java-6-openjdk/jre/../lib/i386:/usr/lib/jvm/java-6-openjdk/jre/lib/i386/client:/usr/lib/jvm/java-6-openjdk/jre/lib/i386:/usr/lib/jvm/java-6-openjdk/jre/../lib/i386:/usr/java/packages/lib/i386:/usr/lib/i386-linux-gnu/jni:/lib/i386-linux-gnu:/usr/lib/i386-linux-gnu:/usr/lib/jni:/lib:/usr/lib
May 31, 2011 8:57:34 PM org.apache.coyote.http11.Http11Protocol init
INFO: Initializing Coyote HTTP/1.1 on http-8080
May 31, 2011 8:57:34 PM org.apache.catalina.startup.Catalina load
INFO: Initialization processed in 1096 ms
May 31, 2011 8:57:34 PM org.apache.catalina.core.StandardService start
INFO: Starting service Catalina
May 31, 2011 8:57:34 PM org.apache.catalina.core.StandardEngine start
INFO: Starting Servlet Engine: Apache Tomcat/6.0.26
May 31, 2011 8:57:34 PM org.apache.catalina.startup.HostConfig deployDirectory
INFO: Deploying web application directory examples
May 31, 2011 8:57:36 PM org.apache.jasper.EmbeddedServletOptions <init>
SEVERE: The scratchDir you specified: /usr/local/apache-tomcat-6.0.26/work/Catalina/localhost/examples is unusable.
May 31, 2011 8:57:36 PM org.apache.catalina.startup.HostConfig deployDirectory
INFO: Deploying web application directory docs
May 31, 2011 8:57:36 PM org.apache.jasper.EmbeddedServletOptions <init>
SEVERE: The scratchDir you specified: /usr/local/apache-tomcat-6.0.26/work/Catalina/localhost/docs is unusable.
May 31, 2011 8:57:36 PM org.apache.catalina.startup.HostConfig deployDirectory
INFO: Deploying web application directory manager
May 31, 2011 8:57:36 PM org.apache.catalina.startup.HostConfig deployDirectory
SEVERE: Error deploying web application directory manager
java.io.FileNotFoundException: /usr/local/apache-tomcat-6.0.26/conf/Catalina/localhost/manager.xml (No such file or directory)
        at java.io.FileOutputStream.open(Native Method)
        at java.io.FileOutputStream.<init>(FileOutputStream.java:209)
        at java.io.FileOutputStream.<init>(FileOutputStream.java:160)
        at org.apache.catalina.startup.HostConfig.deployDirectory(HostConfig.java:1013)
        at org.apache.catalina.startup.HostConfig.deployDirectories(HostConfig.java:964)
        at org.apache.catalina.startup.HostConfig.deployApps(HostConfig.java:502)
        at org.apache.catalina.startup.HostConfig.start(HostConfig.java:1277)
        at org.apache.catalina.startup.HostConfig.lifecycleEvent(HostConfig.java:321)
        at org.apache.catalina.util.LifecycleSupport.fireLifecycleEvent(LifecycleSupport.java:119)
        at org.apache.catalina.core.ContainerBase.start(ContainerBase.java:1053)
        at org.apache.catalina.core.StandardHost.start(StandardHost.java:785)
        at org.apache.catalina.core.ContainerBase.start(ContainerBase.java:1045)
        at org.apache.catalina.core.StandardEngine.start(StandardEngine.java:443)
        at org.apache.catalina.core.StandardService.start(StandardService.java:519)
        at org.apache.catalina.core.StandardServer.start(StandardServer.java:710)
        at org.apache.catalina.startup.Catalina.start(Catalina.java:581)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
        at java.lang.reflect.Method.invoke(Method.java:616)
        at org.apache.catalina.startup.Bootstrap.start(Bootstrap.java:289)
        at org.apache.catalina.startup.Bootstrap.main(Bootstrap.java:414)
May 31, 2011 8:57:36 PM org.apache.catalina.startup.HostConfig deployDirectory
INFO: Deploying web application directory host-manager
May 31, 2011 8:57:36 PM org.apache.catalina.startup.HostConfig deployDirectory
SEVERE: Error deploying web application directory host-manager
java.io.FileNotFoundException: /usr/local/apache-tomcat-6.0.26/conf/Catalina/localhost/host-manager.xml (No such file or directory)
        at java.io.FileOutputStream.open(Native Method)
        at java.io.FileOutputStream.<init>(FileOutputStream.java:209)
        at java.io.FileOutputStream.<init>(FileOutputStream.java:160)
        at org.apache.catalina.startup.HostConfig.deployDirectory(HostConfig.java:1013)
        at org.apache.catalina.startup.HostConfig.deployDirectories(HostConfig.java:964)
        at org.apache.catalina.startup.HostConfig.deployApps(HostConfig.java:502)
        at org.apache.catalina.startup.HostConfig.start(HostConfig.java:1277)
        at org.apache.catalina.startup.HostConfig.lifecycleEvent(HostConfig.java:321)
        at org.apache.catalina.util.LifecycleSupport.fireLifecycleEvent(LifecycleSupport.java:119)
        at org.apache.catalina.core.ContainerBase.start(ContainerBase.java:1053)
        at org.apache.catalina.core.StandardHost.start(StandardHost.java:785)
        at org.apache.catalina.core.ContainerBase.start(ContainerBase.java:1045)
        at org.apache.catalina.core.StandardEngine.start(StandardEngine.java:443)
        at org.apache.catalina.core.StandardService.start(StandardService.java:519)
        at org.apache.catalina.core.StandardServer.start(StandardServer.java:710)
        at org.apache.catalina.startup.Catalina.start(Catalina.java:581)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
        at java.lang.reflect.Method.invoke(Method.java:616)
        at org.apache.catalina.startup.Bootstrap.start(Bootstrap.java:289)
        at org.apache.catalina.startup.Bootstrap.main(Bootstrap.java:414)
May 31, 2011 8:57:36 PM org.apache.catalina.startup.HostConfig deployDirectory
INFO: Deploying web application directory ROOT
May 31, 2011 8:57:36 PM org.apache.jasper.EmbeddedServletOptions <init>
SEVERE: The scratchDir you specified: /usr/local/apache-tomcat-6.0.26/work/Catalina/localhost/_ is unusable.
May 31, 2011 8:57:36 PM org.apache.coyote.http11.Http11Protocol start
INFO: Starting Coyote HTTP/1.1 on http-8080
May 31, 2011 8:57:36 PM org.apache.jk.common.ChannelSocket init
INFO: JK: ajp13 listening on /0.0.0.0:8009
May 31, 2011 8:57:36 PM org.apache.jk.server.JkMain start
INFO: Jk running ID=0 time=0/64  config=null
May 31, 2011 8:57:36 PM org.apache.catalina.startup.Catalina start
INFO: Server startup in 1579 ms

---

### Post by r-senior on 2011-05-31
If you are controlling Tomcat from Netbeans it is usually better to download from the Apache Tomcat website, unpack under your home directory somewhere, and let Netbeans control it from there. Add it as a server withion Netbeans (you might need to create an admin user in tomcat-users.xml).

This:

```
java.io.FileNotFoundException: /usr/local/apache-tomcat-6.0.26/logs/catalina.2011-05-31.log (Permission denied)
```

suggests to me that Tomcat can't control the repository installed version.

You should be able to get your example running by deploying the WAR file to the repository installed Tomcat but for development/debugging it's better to do as suggested above.

---

### Post by r-senior on 2011-05-31
Have a look at this:

[http://ubuntuforums.org/showthread.php?t=1447417](http://ubuntuforums.org/showthread.php?t=1447417)

---

### Post by RobikShrestha on 2011-05-31
I downloaded tomcat 7.0.
I can't run the startup script. Here are the details:
I use open java and do not know how to setup class path variables.

robik@dhcppc0:~$ cd /home/robik/Software/apache-tomcat-7.0.14/bin
robik@dhcppc0:~/Software/apache-tomcat-7.0.14/bin$ sudo sh setclasspath
[sudo] password for robik: 
sh: Can't open setclasspath
robik@dhcppc0:~/Software/apache-tomcat-7.0.14/bin$ sudo sh setclasspath.sh
Neither the JAVA_HOME nor the JRE_HOME environment variable is defined
At least one of these environment variable is needed to run this program
robik@dhcppc0:~/Software/apache-tomcat-7.0.14/bin$ sudo sh catalina.sh
The BASEDIR environment variable is not defined correctly
This environment variable is needed to run this program
robik@dhcppc0:~/Software/apache-tomcat-7.0.14/bin$ sudo sh startup.sh
Cannot find ./catalina.sh
The file is absent or does not have execute permission
This file is needed to run this program



robik@dhcppc0:~/Software/apache-tomcat-7.0.14/bin$ java -version
java version "1.6.0_22"
OpenJDK Runtime Environment (IcedTea6 1.10.1) (6b22-1.10.1-0ubuntu1)
OpenJDK Server VM (build 20.0-b11, mixed mode)

---

### Post by r-senior on 2011-06-01
I did write instructions for Tomcat 7 in a post somewhere (you should find it with advanced search on my name and "tomcat"), but Netbeans 6.9 doesn't allow you to add Tomcat 7.x series as servers, only Tomcat 6.x.

At this stage, you won't see much of a difference. I'd leave the Tomcat 7 install where it is and unpack Tomcat 6 alongside it.

I think the problem you are having starting Tomcat is using sudo. This is a personal copy of Tomcat, so just start it by running the script:

```

./startup.sh

```

There's no need to set a JAVA_HOME or classpath, as long as you have a JDK installed. Check this by:

```

javac -version

```

---

### Post by r-senior on 2011-06-01
Just to show it works without a classpath and home:

```

$ echo $CLASSPATH

$ echo $JAVA_HOME

$ javac -version
javac 1.6.0_22
$ cd ~/Software/apache-tomcat-6.0.26/bin
$ ./startup.sh
Using CATALINA_BASE:   /home/richard/Software/apache-tomcat-6.0.26
Using CATALINA_HOME:   /home/richard/Software/apache-tomcat-6.0.26
Using CATALINA_TMPDIR: /home/richard/Software/apache-tomcat-6.0.26/temp
Using JRE_HOME:        /usr
Using CLASSPATH:       /home/richard/Software/apache-tomcat-6.0.26/bin/bootstrap.jar
$ netstat -plant | grep 8080
(Not all processes could be identified, non-owned process info
 will not be shown, you would have to be root to see it all.)
[COLOR="Red"]tcp6       0      0 :::8080                 :::*                    LISTEN      17758/java      [/COLOR]
$ ./shutdown.sh
Using CATALINA_BASE:   /home/richard/Software/apache-tomcat-6.0.26
Using CATALINA_HOME:   /home/richard/Software/apache-tomcat-6.0.26
Using CATALINA_TMPDIR: /home/richard/Software/apache-tomcat-6.0.26/temp
Using JRE_HOME:        /usr
Using CLASSPATH:       /home/richard/Software/apache-tomcat-6.0.26/bin/bootstrap.jar
$ netstat -plant | grep 8080
(Not all processes could be identified, non-owned process info
 will not be shown, you would have to be root to see it all.)

```

EDIT: Make sure you shutdown the repository installed Tomcat before attempting to start your local one, or you will get port conflicts on port 8080

---

### Post by r-senior on 2011-06-01
I notice you've decided to go with Glassfish in another post. Could you mark this thread solved?

---

