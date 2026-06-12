---
title: "Jetty Java issues"
date: 2008-06-04
forum: New to Ubuntu
---

### Post by AOZ on 2008-06-04
Hey guys Im just starting to play around with web app servers and im having alot of trouble with Jetty. I used tomcat for a while and it was really easy to use but the project im working on now runs on jetty so im tryign to get used to it. Whe i followed the tutorial on the jetty website i got my first problem..

after i start the server with
omar@omar-laptop:~/Desktop/Jetty$ java -jar start.jar etc/jetty.xml

i try to do this
omar@omar-laptop:~/Desktop/Jetty$ java org.mortbay.jetty.Server etc/admin.xml etc/demo.xml

but i get this error
Exception in thread "main" java.lang.NoClassDefFoundError: org/mortbay/jetty/Server
Caused by: java.lang.ClassNotFoundException: org.mortbay.jetty.Server
	at java.net.URLClassLoader$1.run(URLClassLoader.java:200)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:306)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:276)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:319)

I'v been tryign to figure out why this is happening for a while now and im getting pretty frustrated. Any help will be greatly appreciated.

oh and in case anyone is wondering...

omar@omar-laptop:~$ java -version

java version "1.6.0_06"
Java(TM) SE Runtime Environment (build 1.6.0_06-b02)
Java HotSpot(TM) Client VM (build 10.0-b22, mixed mode, sharing)

omar@omar-laptop:~$ echo $JAVA_HOME
/usr/lib/jvm/java-6-sun-1.6.0.06

omar@omar-laptop:~$ echo $CLASSPATH
/usr/lib/jvm/java-6-sun-1.6.0.06/lib

---

### Post by AOZ on 2008-06-04
bump

---

### Post by The Cog on 2008-06-04
It can't find the file org/mortbay/jetty/Server.class. I'm not familiar with jetty, but that's the root cause of the error message. Maybe there's a jar file that should be on your classpath, or copied into the JRE's lib/ext directory as an extension.

---

