---
title: "compile java"
date: 2010-04-02
forum: Packaging and Compiling Programs
---

### Post by pythonsyntax on 2010-04-02
How do i compile a java program and when i compile it with javac all i get is errors not sure why?


I am useing gvim for my java programming.

---

### Post by pythonsyntax on 2010-04-02
[U]Exception in thread "main" java.lang.NoClassDefFoundError: test
Caused by: java.lang.ClassNotFoundException: test
    at java.net.URLClassLoader$1.run(URLClassLoader.java:217)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:319)
    at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:264)
    at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:332)
Could not find the main class: test. Program will exit.

[/U]

---

### Post by JCoster on 2010-04-02
Do you have a main method?  e.g.:
```
public static void main(String[] args) {
    // your initialisation code here
}
```

---

### Post by pythonsyntax on 2010-04-02
I found out i had to use javac file nam.java and java name to get it to work

---

