---
title: "Installing SimpleBackUp"
date: 2008-02-26
forum: Packaging and Compiling Programs
---

### Post by nigel_salvador on 2008-02-26
I am trying to install SimpleBackUp for linux. It is a program that is written in Java. I have downloaded the archived file and extracted it. After running the configuration file (i.e. simplebackupconfig) I get the following error message:

Running Simple Backup Configuration Program in directory "/home/nigelsalvador/Downloads/SimpleBackup"
Exception in thread "main" java.lang.UnsupportedClassVersionError: org/sjrnet/versiontest/VersionTest (Unsupported major.minor version 49.0)
        at java.lang.ClassLoader.defineClass0(Native Method)
        at java.lang.ClassLoader.defineClass(ClassLoader.java:539)
        at java.security.SecureClassLoader.defineClass(SecureClassLoader.java:123)
        at java.net.URLClassLoader.defineClass(URLClassLoader.java:251)
        at java.net.URLClassLoader.access$100(URLClassLoader.java:55)
        at java.net.URLClassLoader$1.run(URLClassLoader.java:194)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.net.URLClassLoader.findClass(URLClassLoader.java:187)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:289)
        at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:274)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:235)
        at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:302)
nigelsalvador@nigelsalvador-desktop:~/Downloads/SimpleBackup$

Please help, I would like to get this thing up and running.

---

