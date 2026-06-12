---
title: "Trying to get Java to execute..."
date: 2012-03-13
forum: New to Ubuntu
---

### Post by D3vin on 2012-03-13
I am a total noob to Linux. I am in a "Intro to Java" class this semester and I am trying to get Java running correctly in Ubuntu 11.10. I got Windows 7 64-bit to compile and execute Java in cmd, but it's totally bugging me that I cannot get it to run in Ubuntu...

javac -version
javac 1.7.0_147


java -version
java version "1.6.0_23"
OpenJDK Runtime Environment (IcedTea6 1.11pre) (6b23~pre11-0ubuntu1.11.10.2)
OpenJDK 64-Bit Server VM (build 20.0-b11, mixed mode)

In my directory:
/usr/lib/jvm

It has the following folders.
java-1.6.0-openjdk
java-6-openjdk
java-1.7.0-openjdk-amd64
java-7-openjdk-amd64
java-7-openjdk-common
jdk1.7.0

I am having trouble executing java file. I get this message...

javac Hello.java

java Hello
Exception in thread "main" java.lang.UnsupportedClassVersionError: Hello : Unsupported major.minor version 51.0
	at java.lang.ClassLoader.defineClass1(Native Method)
	at java.lang.ClassLoader.defineClass(ClassLoader.java:634)
	at java.security.SecureClassLoader.defineClass(SecureClassLoader.java:142)
	at java.net.URLClassLoader.defineClass(URLClassLoader.java:277)
	at java.net.URLClassLoader.access$000(URLClassLoader.java:73)
	at java.net.URLClassLoader$1.run(URLClassLoader.java:212)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:321)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:266)
Could not find the main class: Hello. Program will exit.

Could it be my PATH is set to an older version of Java?

---

### Post by Gremlinzzz on 2012-03-13
This is the site i use to install Java might be helpful:popcorn:
[http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

---

### Post by D3vin on 2012-03-14
> **Gremlinzzz said:**
> This is the site i use to install Java might be helpful:popcorn:
[http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)


Thank you! But it didn't work. :confused: I uninstalled the Icetea plugin and installed the Oracle Java 1.6.0 JRE, also set it as primary.

Now it goes something like this.

java -version
java version "1.6.0_31"
Java(TM) SE Runtime Environment (build 1.6.0_31-b04)
Java HotSpot(TM) 64-Bit Server VM (build 20.6-b01, mixed mode)

java Hello
Exception in thread "main" java.lang.UnsupportedClassVersionError: Hello : Unsupported major.minor version 51.0
	at java.lang.ClassLoader.defineClass1(Native Method)
	at java.lang.ClassLoader.defineClassCond(Unknown Source)
	at java.lang.ClassLoader.defineClass(Unknown Source)
	at java.security.SecureClassLoader.defineClass(Unknown Source)
	at java.net.URLClassLoader.defineClass(Unknown Source)
	at java.net.URLClassLoader.access$000(Unknown Source)
	at java.net.URLClassLoader$1.run(Unknown Source)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(Unknown Source)
	at java.lang.ClassLoader.loadClass(Unknown Source)
	at sun.misc.Launcher$AppClassLoader.loadClass(Unknown Source)
	at java.lang.ClassLoader.loadClass(Unknown Source)
Could not find the main class: Hello.  Program will exit.

I saved the java file and class file in my Home folder.

---

### Post by Pjotr123 on 2012-03-14
Forget the Hello. You can check here whether Java works:
[http://www.java.com/en/download/installed.jsp](http://www.java.com/en/download/installed.jsp)

If that confirms that all is well, all is well. For all practical purposes, that's quite enough. At least for 99,9 % of the Ubuntu users. :-)

When no such confirmation: repeat the installation manual, and follow it to the letter this time. Success guaranteed. :cool:

---

### Post by lykeion on 2012-03-15
The error message "unsupported major.minor version" means that you compiled your class with a specific JDK, but then try to run it in an older version of JDK. In your case you are compiling with jdk1.7 and try to run it with java 1.6. I would suggest you to uninstall jdk1.7.0 and install jdk1.6, recompile and then you should be able to run it.

@Pjotr OP wanted help with compiling with Java JDK, not installing Java JRE/Plugin.

---

### Post by Immolatus on 2012-03-15
The easiest way to do this is to create a folder in /home, call it what you like and install the jdk there. What you've done from the looks of it is install the jdk alongside the openjdk wich is not necessary.
All you need to do is set the bash path variable.
With this done you can compile from the command line no problem.
The bash path is set in a hidden file in your /home called .bashrc.

---

