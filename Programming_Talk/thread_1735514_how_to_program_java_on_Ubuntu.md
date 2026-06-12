---
title: "how to program java on Ubuntu ?"
date: 2011-04-21
forum: Programming Talk
---

### Post by tunechi on 2011-04-21
hi guys , i recently installed OPENJDK java 6 Runtime , anyways , i made a helloworld program to test it , in windows first i write in cmd javac HelloWorld.java , then java HelloWorld , i tried it here but it didnt work , i saved the file on desktop , how can i execute it and run it ?

thank you

---

### Post by orzechowskid on 2011-04-21
hi,

are you not able to edit your file?  Run javac?  Run java?  Something else?  what were the exact error messages you received?

---

### Post by tunechi on 2011-04-21
> **orzechowskid said:**
> hi,

are you not able to edit your file?  Run javac?  Run java?  Something else?  what were the exact error messages you received?
Satellite-L305:~/Desktop$ Run javac HelloWorld.java
Run: command not found
----Satellite-L305:~/Desktop$ java HelloWorld.java
Exception in thread "main" java.lang.NoClassDefFoundError: HelloWorld/java
Caused by: java.lang.ClassNotFoundException: HelloWorld.java
    at java.net.URLClassLoader$1.run(URLClassLoader.java:217)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:321)
    at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:266)
Could not find the main class: HelloWorld.java. Program will exit.
-----Satellite-L305:~/Desktop$

---

### Post by simeon87 on 2011-04-21
You have to type:

```
javac HelloWorld.java
```

to compile and

```
java HelloWorld
```

to run.

---

### Post by r-senior on 2011-04-21
Try ```
java HelloWorld
```

You only need to specify the .java extension when you are compiling:

```
javac HelloWorld.java
```

---

### Post by tunechi on 2011-04-21
> **simeon87 said:**
> You have to type:

```
javac HelloWorld.java
```to compile and

```
java HelloWorld
```to run.

lol , thats what i do on windows :D , anyways here is what i got
"-----Satellite-L305:~/Desktop$ javac HelloWorld.java
The program 'javac' can be found in the following packages:
 * openjdk-6-jdk
 * ecj
 * gcj-4.4-jdk
 * gcj-4.5-jdk
Try: sudo apt-get install <selected package>
"
i already download and installed openJDK java 6 Runtime ? what should i do now 

thanks

---

### Post by orzechowskid on 2011-04-21
the Java runtime is only a piece of Java called the JRE.  It lets you run Java programs.  If you want to compile your own, you need to install the whole JDK.  Try 'sudo apt-get install openjdk-6-jdk' and then see if the javac command shows up on your computer.

---

### Post by tunechi on 2011-04-21
> **orzechowskid said:**
> the Java runtime is only a piece of Java called the JRE.  It lets you run Java programs.  If you want to compile your own, you need to install the whole JDK.  Try 'sudo apt-get install openjdk-6-jdk' and then see if the javac command shows up on your computer.

thank you , donwloading hope it works

---

### Post by stchman on 2011-04-21
You need to install the whole shooting match(JDK), not just the JRE.

```

sudo apt-get -y install sun-java6-bin sun-java6-fonts sun-java6-jdk sun-java6-jre sun-java6-plugin

```Remember to enable the partner repository for 10.04 and later for the SUN(Oracle) Java.

Once this is done you can create/edit/compile Java programs as you would on any platform.

---

