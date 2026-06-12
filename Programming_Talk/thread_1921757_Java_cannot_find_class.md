---
title: "Java cannot find class"
date: 2012-02-07
forum: Programming Talk
---

### Post by rgreener25 on 2012-02-07
i wrote a simple Hello world app with class Hello and when i run it i get this ```
{CENSORED}/src java Hello
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
``` the directory contains 2 files Hello.class and Hello.java the code for Hello.java is here ```
class Hello {
  
  // main: generate some simple output
  
  public static void main(String[] args) {
    System.out.println("Hello, World!");
  }
}
```

---

### Post by doobrie on 2012-02-07
Looks like you've compiled it with one version of Java and are running it with another.  Check that your JRE and JDK are both the same version.

---

### Post by rgreener25 on 2012-02-07
how?

---

### Post by doobrie on 2012-02-07
> **rgreener25 said:**
> how?
You can check if this is the issue by opening a terminal and comparing the output of

```
java -version
```

and

```
javac -version
```

Can you do this and post the results?

---

### Post by Rafterman414 on 2012-02-07
Also ensure that the classpath is set correctly.

I think the only time that you can compile and run from different versions is if the JDK is an older version then JRE but not the other way around.

---

### Post by doobrie on 2012-02-07
> **Rafterman414 said:**
> Also ensure that the classpath is set correctly.

I think the only time that you can compile and run from different versions is if the JDK is an older version then JRE but not the other way around.
Yep, I think that's correct.

---

### Post by sffvba[e0rt on 2012-02-07
*Thread moved to **Programming Talk**.*


404

---

### Post by Zugzwang on 2012-02-08
@OP: A solution to your problem is posted in [this thread]("http://ubuntuforums.org/showthread.php?t=1906360"). Note that searching for the exception name in this forum would have brought the solution.

---

