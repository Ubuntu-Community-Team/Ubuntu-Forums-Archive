---
title: "Downloaded .jar file of Azureus and it's not working"
date: 2010-01-09
forum: Programming Talk
---

### Post by s3a on 2010-01-09
First of all, I'm purposely avoiding the repositories. I'm not interested in the program itself but the fact that it is written in Java. (maybe I will be interested in it when I use it)

I renamed the .jar file I downloaded as "az.jar" without the quotes and placed it on my desktop.

_Here is my problem:_
```
deniz@debian:~$ cd Desktop
deniz@debian:~/Desktop$ java -jar az.jar
Exception in thread "main" java.lang.NoClassDefFoundError: org/apache/commons/cli/ParseException
Caused by: java.lang.ClassNotFoundException: org.apache.commons.cli.ParseException
	at java.net.URLClassLoader$1.run(URLClassLoader.java:217)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:319)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:264)
Could not find the main class: org.gudy.azureus2.ui.common.Main. Program will exit.
deniz@debian:~/Desktop$ 

```

Why am I getting this message and what can I do about it?

Any help would be greatly appreciated!
Thanks in advance!

P.S.
Running my own (basic) program that I made and saved as a .jar file works so I assumed this would work too and was actually shocked when it didn't.

---

### Post by maddog39 on 2010-01-09
My hunch is that maybe somehow, thats not the full program. Clearly something is either missing or possibly just missing from the classpath. Given that, maybe someone else and provide some more insight than I.

---

### Post by kahumba on 2010-01-09
Azureus doesn't run by directly launching the .jar file.
The official site provides an archive with lots of stuff in it, unzip it, you should run the corresponding batch/shell script instead, it takes care of environment initialization and other stuff and then launches Azureus.

---

