---
title: "Trouble while loading mysql connector/j."
date: 2009-11-17
forum: Programming Talk
---

### Post by javamaniac on 2009-11-17
Hi. I'm running under Ubuntu 9.10 (64-bit) and using JRE 1.6. I have an application written in java and it works perfectly under Windows Vista (34-bit). Now I'm trying to change my development platform to Ubuntu and have encountered a problem.

Here's the message excerpt that tomcat (6.0.18) throws:

```

SEVERE: Servlet.service() for servlet site threw exception
java.lang.ClassNotFoundException: com.mysql.jdbc.Driver
    at org.apache.catalina.loader.WebappClassLoader.loadClass(WebappClassLoader.java:1387)
    at org.apache.catalina.loader.WebappClassLoader.loadClass(WebappClassLoader.java:1233)
    at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:332)
    at java.lang.Class.forName0(Native Method)
    at java.lang.Class.forName(Class.java:186)
....

```Mysql seem to work fine, because I can execute my queries through MySQL Query Browser.

As far as I can understand my JDBC driver doesn't load properly. 
I've tried in terminal ```
apt-get install libmysql-java
```.
My CLASSPATH environment variable is set to 
```
/home/javamaniac/dev/packages/classpath/mysql-connector-java-5.1.10-bin.jar
```and appropriate .jar file is copied there.
I tried copying it to /usr/lib/jvm/java-6-openjdk/lib/ext/ - it didn't really helped.

Can any one please help?!

Thanks in advance.

---

### Post by theDaveTheRave on 2009-11-25
Hi javamaniac

The classpath seems to be a persistent problem on all platforms (as far as I am concerned).

The <export classpath... > command seems to put the classpath where you would want it, but it never has worked "properly" for me either.

Ultimately you have a few options.

I found that if I set the project properties in the IDE to point to the location where the connectJ sits, things generally work out!

Like me you have resorted to puting the jar file in the general location of
```

/usr/lib/jvm/java-6-openjdk/jre/lib/ext

```

Apparently however this is not the recommended course of action - if I set the classpath anywhere else it all falls apart!

Does your application work when run via the IDE (or from cli), without the use of tomcat?

I remember from reading the tomcat and apache docs that there is a specified place for the addition of the .jar files (can't find the correct page at the moment though, but it is there somewhere ;). Have you tried this location?

Also if you have it set in a "local" personal directory it may not work! Try using a "hard link" to the location or similar...

I'm not sure how helpfull all this is, but maybe it will help point you in the right direction, and at least you know you aren't alone in your classpath woes!

David

---

