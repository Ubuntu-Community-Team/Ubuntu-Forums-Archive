---
title: "Can't Launch Minecraft?"
date: 2017-07-06
forum: New to Ubuntu
---

### Post by iainsgw1 on 2017-07-06
I'm not sure if this is the right sub but I'll try
I downloaded minecraft from the official minecraft site and I'm using  OpenJDK Java 7 Runtime to launch it. I'm new to Ubuntu and I've tried  looking online for commands in the terminal to help me, but none of them  have worked. Whenever I try to launch Minecraft, the error shows up in  the launcher:

Exception in thread "main"  java.lang.UnsupportedClassVersionError: net/minecraft/client/main/Main :  Unsupported major.minor version 52.0
    at java.lang.ClassLoader.defineClass1(Native Method)
    at java.lang.ClassLoader.defineClass(ClassLoader.java:803)
    at java.security.SecureClassLoader.defineClass(SecureClassLoader.java:142)
    at java.net.URLClassLoader.defineClass(URLClassLoader.java:442)
    at java.net.URLClassLoader.access$100(URLClassLoader.java:64)
    at java.net.URLClassLoader$1.run(URLClassLoader.java:354)
    at java.net.URLClassLoader$1.run(URLClassLoader.java:348)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.net.URLClassLoader.findClass(URLClassLoader.java:347)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:425)
    at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:312)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:358)
    at sun.launcher.LauncherHelper.checkAndLoadMain(LauncherHelper.java:482)

If anyone could help it would be GREATLY appreciated. Thanks, Iain.

---

### Post by CatKiller on 2017-07-07
Does it work if you install oracle-java8-installer? I think I got my copy from [this PPA]("https://launchpad.net/~webupd8team/+archive/ubuntu/java").

---

### Post by josenj on 2017-07-08
The following commands helped me out:

```
sudo add-apt-repository ppa:openjdk-r/ppa
sudo apt-get update
sudo apt-get install openjdk-8-jdk

```
Then type:

```
sudo update-alternatives --config java
```

Select the number next to "/usr/lib/jvm/java-8-openjdk-amd64/jre/bin/java"  (notice java-8)

Then type:

> java -version

The last command should say: 

openjdk version "1.8.0_111"

You should be good to go.  You probably have 1.7 which Minecraft didn't like.  Seems to like 1.8 better.

Hope this helps!

---

