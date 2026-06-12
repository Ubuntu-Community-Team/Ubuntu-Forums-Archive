---
title: "NetBeans Unsupported major/minor version"
date: 2012-06-09
forum: Packaging and Compiling Programs
---

### Post by JakeFrederix on 2012-06-09
Hey everyone,

I ran into some issues while trying to compile a really straightforward Java program.

```
        
        JFrame frame = new JFrame("a frame");
        frame.add(new JButton("a button"));
        frame.pack();
        frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        frame.setVisible(true);

```When I compile it, and run it in Netbeans, it works just perfectly, and shows the JFrame and JButton.

When I try to open the .jar it produces (either by right-clicking and selecting "open with openjdk 6 runtime" or "openjdk 7 runtime", or by using the "java -jar" command) it fails.

output of java -jar <filename>
Exception in thread "main" java.lang.UnsupportedClassVersionError: javaapplication1/JavaApplication1 : Unsupported major.minor version 51.0
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
Could not find the main class: javaapplication1.JavaApplication1. Program will exit.

the output of javac -version:
javac 1.6.0_24

the output of java -version:
java version "1.6.0_24"
OpenJDK Runtime Environment (IcedTea6 1.11.1) (6b24-1.11.1-4ubuntu3)
OpenJDK 64-Bit Server VM (build 20.0-b12, mixed mode)

Can anyone help me out?

Thanks in advance.

---

