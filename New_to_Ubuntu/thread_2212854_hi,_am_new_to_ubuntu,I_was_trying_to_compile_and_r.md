---
title: "hi, am new to ubuntu,I was trying to compile and run my first java program in ubuntu"
date: 2014-03-23
forum: New to Ubuntu
---

### Post by imbugad on 2014-03-23
hi, am new to ubuntu,I was trying to compile and run my first java program in ubuntu , this is what i get in the terminal,WHAT CAN BE THE PROBLEM WITH MY PROGRAM?

 at java.lang.ClassLoader.defineClass1(Native Method)
    at java.lang.ClassLoader.defineClass(ClassLoader.java:643)
    at java.security.SecureClassLoader.defineClass(SecureClassLoader.java:142)
    at java.net.URLClassLoader.defineClass(URLClassLoader.java:277)
    at java.net.URLClassLoader.access$000(URLClassLoader.java:73)
    at java.net.URLClassLoader$1.run(URLClassLoader.java:212)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:323)
    at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:268)
Could not find the main class: HelloWorld. Program will exit.

---

### Post by Kris_Spencer on 2014-03-24
Hello. I have a couple of questions to see what the situation is exactly:

Is this the first time you've programmed with Java, or just on Ubuntu (Out of curiousity)?
Do you use an IDE, or do it manually by using javac?
Did you check your code for issues with the class and main method syntax issues?

---

