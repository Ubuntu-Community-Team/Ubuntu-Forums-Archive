---
title: "Installing jdk, first time with ubuntu - need help."
date: 2012-01-08
forum: Programming Talk
---

### Post by Charlie: on 2012-01-08
I'm a bit lost as to how to start with java development on Ubuntu 11.10.
(Not even sure if this is the right place to look for help :/)

Here's what I've done so far:
Installed openjdk-7-jdk, I assume... 
I used "apt-get install openjdk-7-jdk" and it finished without error.

After installing the jdk, I installed Geany (because it reminds me of TextPad) using:
"apt-get install geany"

When using "java -version" in a terminal here is the result:
```
:~$ java -version
java version "1.6.0_23"
OpenJDK Runtime Environment (IcedTea6 1.11pre) (6b23~pre11-0ubuntu1.11.10)
OpenJDK Server VM (build 20.0-b11, mixed mode)

```I wrote a simple program to display the name of a user, and compiled it in Geany, however when I try to execute it a terminal window pops up displaying this message:

```
Exception in thread "main" java.lang.UnsupportedClassVersionError: NamesDialog : Unsupported major.minor version 51.0
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
Could not find the main class: NamesDialog. Program will exit.


------------------
(program exited with code: 1)
Press return to continue

```I assume I'm making a very obvious error and a simple answer to get my stuff running will be appreciated. Let me know if I need to re-thread in a different part of the forums! Please be as clear and concise as possible with instructions because I am just getting started with linux and java alike.

---

### Post by ofnuts on 2012-01-09
What command did you use exactly to execute your code? Look more like a missing classpath to me.

---

### Post by Zugzwang on 2012-01-09
> **ofnuts said:**
> What command did you use exactly to execute your code? Look more like a missing classpath to me.

Don't think so. The error message "Unsupported major.minor version" sounds more like as if the program was compiled with a higher java version than it was executed with.

@OP: Try "javac -version" from the terminal. Does it show a java version of 1.7.something ? If yes, you have multiple JRE/JDKs installed. In this case, run "sudo update-alternatives --config java" to choose the newer one as the default for execution.

---

### Post by KdotJ on 2012-01-09
The OP stated that they installed **openjdk-7-jdk**, but the java --version shows Java 6...

Geany perhaps is using 1.7 and you terminal is using the 1.6 ?

---

### Post by Charlie: on 2012-01-11
Zugzwang, I think you're correct, thanks for helping me out!

@ofnuts: I was executing the code with the Geany GUI, if that answers your question. I don't know enough about the command-line yet to get into this stuff.

@KdotJ: That's exactly right. Thanks for the input.

Problem solved, 
```
sudo update-alternatives --config java
```fixed it instantly.

Thread may be closed, now.

---

