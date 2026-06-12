---
title: "Running compiled java code only under super user"
date: 2009-03-06
forum: Programming Talk
---

### Post by borobudur on 2009-03-06
Hi,
I have the problem, that I can only run my compiled java code (javac) in super user mode. It's not the class-file itself (gave it already mod 777).

If I try to run it as the normal user it says
```
user@machine:~$ java HalloWelt
Exception in thread "main" java.lang.NoClassDefFoundError: HalloWelt
Caused by: java.lang.ClassNotFoundException: HalloWelt
    at java.net.URLClassLoader$1.run(URLClassLoader.java:200)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:307)
    at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:301)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:252)
    at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:320)
Could not find the main class: HalloWelt.  Program will exit.
```
Any idea?

---

### Post by Tuna-Fish on 2009-03-06
Your problem is that Java cannot find the class you are trying to run.

Java has quite a different idea how to run programs compared to how most other programming languages. If you make a python file called test.py, you'd expect that typing python test.py in the same directory would run test.py. You'd be correct. In the same way, you'd expect that being in the same directory and typing java HalloWelt would run the file, but this time you are just flat wrong.

When you type java SomeClass, java will **not** open a file SomeClass.class, but instead it will search for the correct class from it's own classpath. Right now, HelloWelt is not in the classpath, so java cannot find it.

Then why does sudo work? Root probably has . (<= the current directory) in it's classpath, so it works for him. You can either add . to yours, or just run your program with ```
java -cp . HelloWelt
```, and java will look for class hellowelt from your current directory.

---

### Post by shadylookin on 2009-03-06
my guess is that when you wrote the code you had it in a package

so if you wrote to so that the package was called MY_PACKAGE when you try and run it you have to be in the directory directly above MY_PACKAGE and type java MY_PACKAGE.HalloWelt

---

### Post by borobudur on 2009-03-06
shadylookin is that the case if you start developing in eclipse (opening there a project)?

---

### Post by shadylookin on 2009-03-06
> **borobudur said:**
> shadylookin is that the case if you start developing in eclipse (opening there a project)?

typically eclipse puts things into packages, but the only way to tell is to look at your java source by convention package declaration is the top line of a java source file.

---

### Post by borobudur on 2009-03-08
Thanks guys! In my hello world example the class path of the class file itself was missing. Thanks [Tuna-Fish]("http://ubuntuforums.org/member.php?u=157425")

---

