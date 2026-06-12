---
title: "Java Programming in Ubuntu 11.10"
date: 2011-11-17
forum: Programming Talk
---

### Post by Evelynn (#^.^#) on 2011-11-17
Hi, how is everyone? Can someone give me a step by step procedure on programming Java in Ubuntu 11.10 with gedit? I don't use Eclipse or Netbeans, I'm the old-fashioned type! (^o^)
I looked up tutorials and YouTube but they all seem confusing, especially when they give me the code in Debian and when I write it errors show up! (>_<)
Can someone give me instructions that work purely for Ubuntu 11.10? I intend to compile and run on the Terminal so if anyone can take the time to explain I would be much appreciated. Thank you!

---

### Post by raja.genupula on 2011-11-17
Hi man , you wanna execute a java program in Ubuntu.
normally you can go as you do in windows and here no need to add path variable directly you can do . have you installed java. if not 
just type " java" in terminal and it shows availabale ways you have to install java.choose the JDK version among the list and install it.after that type java and javac in your terminal and they show you some list.
 
open ternminal
gedit Hi.java
 
write the simple program
 
```
 
javac Hi.hava
java Hi

```
 
any thing else you want , type here i will try to do my best .

---

### Post by Evelynn (#^.^#) on 2011-11-17
Hi Raja! Thanks for replying (^_^)
I tried as you said and everything was set up well, but when I try to run a simple Hello World code I get an error:

```
Exception in thread "main" java.lang.UnsupportedClassVersionError: Java : Unsupported major.minor version 51.0
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
Could not find the main class: Java. Program will exit.
```Is it because I have to add a certain library that's different from Windows? Please let me know what's missing. Sorry if I'm asking for much, thanks again!

---

### Post by dave0109 on 2011-11-17
That means that the java bytecode has been compiled for 1.7, but you're running it on a JVM that doesn't support it, perhaps 1.6.

Does your PATH point to a javac in one place and a java in another?  Or are you compiling on Windows and running under Ubuntu, hence using different versions of Java.

You can force the Java Compiler to build for a specific version, by the following:-

```

javac -target 1.6 source.java

```

---

### Post by Evelynn (#^.^#) on 2011-11-17
When I first inputted javac I downloaded and installed openJDK1.7.0_01. If I have that version then shouldn't the JVM support the byte code I'm inputting?

I'm coding, compiling and running under Ubuntu, but I have no success in the running part yet. I thought I didn't need to add a path variable [<^_^;

When I input what you said this shows up:

```
javac: target release 1.6 conflicts with default source release 1.7
```

---

### Post by raja.genupula on 2011-11-17
sudo update-alternatives --config java
among the list choose which jvm you want.and then try again 
all the best

---

### Post by dave0109 on 2011-11-17
Certainly the JVM should run the code that you're compiling, assuming that it is indeed the same version.

What is the output to the following commands:
```

which java
which javac

```

Also, regarding the error you're getting.  I didn't realise that Java 1.7 has a bug (or feature) where the default for source and target are now 1.7, so you would need to specify 2 switches on the compiler line in order to reduce the byte code level:
```

javac -target 1.6 -source 1.6 source.java

```

However if your java and javac are at the same level, this should not be necessary.

---

### Post by gshendrick on 2011-11-17
Hi Evelynn (#^.^#),
I infer from your comments above that you are new to Java and that maybe you don't quite get that the syntax for the java SDKs are platform, read OS, independent. I don't mean to start a flame war, so, yeah, let's stipulate that sometimes there are bugs or inconsistencies between OSs, but that these are the exception rather than the rule. You do not have to worry if the code is written for Windows, Linux or BEOS when you write java. Java is platform independent, the VM, virtual machine, runs on top of the OS and executes your compiled java code. That being said there are different versions of the SDK, and so different versions of the VM, and that these differences are described by the Java API version.

If you write code that contains API calls which are part of the Java 7 API, and then try to compile the code on a Java 6 javac compiler, then you may have issues. By the way, this is an excellent reason to use an IDE such as eclipse, netbeans, etc... as the IDE can error check this sort of thing for you. However, I commend you for wanting to work in a light environment.

While there are some great suggestions regarding quick fixes to instantaneous problems coming up here, you may save yourself some time and trouble by checking out some of the documentation that is on your computer. The following command is going to help you a lot.
```

[user]$ man javac

```Sorry to go on at length, but I thought you could use the 100' perspective on this for a moment.

---

### Post by lisati on 2011-11-17
*Thread moved to **Programming Talk**.*

@Evelynn (#^.^#): If you're having trouble reading your posts, you might be able to adjust the font size in your browser.

---

