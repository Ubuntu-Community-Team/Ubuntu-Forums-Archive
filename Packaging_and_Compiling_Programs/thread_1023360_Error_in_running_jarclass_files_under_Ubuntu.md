---
title: "Error in running jar/class files under Ubuntu"
date: 2008-12-27
forum: Packaging and Compiling Programs
---

### Post by micromike09 on 2008-12-27
Hi, newbie here :). This is my first post and I think I'll be spending sometime on this forum. I just installed Ubuntu 8.04 - Hardy 32 bit. I compiled a basic java application in NetBeans 6.01 (Visual Application). I run the program fine under the IDE but when I try to run the jar file or the class files, I get errors. 

Here is what I get when I try to run the jar file by doing this:

"java -jar filename.jar"

I have these files on the Desktop folder.

output at the terminal >

~/Desktop$ java -jar DBMan.jar

Exception in thread "main" java.lang.NoClassDefFoundError: org/jdesktop/application/SingleFrameApplication
        at java.lang.ClassLoader.defineClass1(Native Method)
        at java.lang.ClassLoader.defineClass(ClassLoader.java:637)
        at java.security.SecureClassLoader.defineClass(SecureClassLoader.java:142)
        at java.net.URLClassLoader.defineClass(URLClassLoader.java:277)
        at java.net.URLClassLoader.access$000(URLClassLoader.java:73)
        at java.net.URLClassLoader$1.run(URLClassLoader.java:212)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:323)
        at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:268)
        at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:336)
Caused by: java.lang.ClassNotFoundException: org.jdesktop.application.SingleFrameApplication
        at java.net.URLClassLoader$1.run(URLClassLoader.java:217)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:323)
        at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:268)
        at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:336)
        ... 12 more
Could not find the main class: dbman.DBManApp. Program will exit.

I get the same error when I try to run the .class files.

I have the latest JVM on this system, I used sudo to get it not long ago.

Any ideas?

Thanks

Michael

---

