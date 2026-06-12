---
title: "Problem running compiled Java programs."
date: 2012-09-06
forum: Programming Talk
---

### Post by sogeking99 on 2012-09-06
I believe this is because I am using Javac version: 1.7.0_03 and maybe the wrong JRE? I am not sure what to do, how to find what versions I'm using really. 


Source Code:

```
class printTest {
    public static void main(String[] args){
        System.out.println("Hello, world!");
    }
}

```And this is the error I get when I try to run it:

```
Exception in thread "main" java.lang.UnsupportedClassVersionError: printTest : 
                                               Unsupported major.minor version 51.0
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
Could not find the main class: printTest. Program will exit.

EDIT: Sorry this is a mess, is there no code tags?

------------------
(program exited with code: 1)
Press return to continue
```

---

### Post by codemaniac on 2012-09-06
looks like a java version mess up .
You can check your java version by the below command .

```
java -version
```

A similar issue has been reported below .

[http://stackoverflow.com/questions/7237536/exception-in-thread-main-java-lang-unsupportedclassversionerror-a-unsupporte](http://stackoverflow.com/questions/7237536/exception-in-thread-main-java-lang-unsupportedclassversionerror-a-unsupporte)

---

### Post by ofnuts on 2012-09-06
Use java --version to see what JRE version you have

There is a parameter to Javac ("-target") to tell it to restrict generated code to some earlier version.

---

### Post by sogeking99 on 2012-09-06
Okay, this is the output:

```
owner@ubuntu:~$ java -version
java version "1.6.0_24"
OpenJDK Runtime Environment (IcedTea6 1.11.4) (6b24-1.11.4-1ubuntu0.12.04.1)
OpenJDK 64-Bit Server VM (build 20.0-b12, mixed mode)
owner@ubuntu:~$ 

```

---

### Post by steeldriver on 2012-09-06
if you have multiple versions of the jre or jdk installed, you should be able to use

```

sudo update-alternatives --config java
sudo update-alternatives --config javac

```to view and set the version

---

### Post by sogeking99 on 2012-09-06
> **steeldriver said:**
> if you have multiple versions of the jre or jdk installed, you should be able to use

```

sudo update-alternatives --config java
sudo update-alternatives --config javac

```to view and set the version

Thanks, this seems to have solved my problem.

---

