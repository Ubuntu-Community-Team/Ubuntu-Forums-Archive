---
title: "Strange problem installing Java SDK"
date: 2007-03-09
forum: Programming Talk
---

### Post by snypylo on 2007-03-09
I'm fairly new to ubuntu, and am trying to install the java sdk.
My first try was downloading the rpm.bin from the sun website, then using alien on it to convert it into a .deb. This, i think, is the cause of most of the subsequent problems. It only seemed to install some of the j2sdk (java was there, but javac wasn't).
This didn't work and messed up my apt-get (it said something along the lines of 'j2sdk needs to be reinstalled but i can't find a source'). It wouldn't uninstall normally, so i used --force.
I can't remember exactly what i did afterwards, but it involved copying the java /bin files directly into/usr/bin, where they remain.

running javac now returns:

Error: could not find libjava.so
Error: could not find Java 2 Runtime Environment.

Running java -version returns:
java version "1.4.2-02"
Java(TM) 2 Runtime Environment, Standard Edition (build Blackdown-1.4.2-02)
Java HotSpot(TM) Client VM (build Blackdown-1.4.2-02, mixed mode)


I tried running java on some files i compiled earlier (on windows) and it returned;
Exception in thread "main" java.lang.UnsupportedClassVersionError: Triangle (Unsupported major.minor version 50.0)
        at java.lang.ClassLoader.defineClass0(Native Method)
        at java.lang.ClassLoader.defineClass(ClassLoader.java:539)
        at java.security.SecureClassLoader.defineClass(SecureClassLoader.java:123)
        at java.net.URLClassLoader.defineClass(URLClassLoader.java:251)
        at java.net.URLClassLoader.access$100(URLClassLoader.java:55)
        at java.net.URLClassLoader$1.run(URLClassLoader.java:194)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.net.URLClassLoader.findClass(URLClassLoader.java:187)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:289)
        at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:274)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:235)
        at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:302)


An interesting one is sudo apt-get install j2sdk:
Package j2sdk is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package j2sdk has no installation candidate


I have the JRE environment installed, according to synaptic. I think perhaps i messed up a bit :( .
Thank you for any and all replies!

---

### Post by monkeyking on 2007-03-09
I've always had problems installing java sdk on linux.
What I did was the following.

Installed the binary directly given on the webpage of sun.
Finding the correc twebpage at sun, is in itself quite a task.

Then the runtime java works.
But you still need to customize your path to the bin subfolder of your installation.
And then you need to add the classpath enviroment to you system.
If I remember correctly, that is the lib subfolder of your installation.

it seems stupid compared to apt-get/synaptic
but it works

---

### Post by hod139 on 2007-03-09
You can install the package sun-java5-jdk (sun-java6-jdk) and then set it as the default using the alternatives tools
```

sudo update-java-alternatives -s java-1.5.0-sun (java-6-sun)

```

If you want to install from Sun's website, don't download the rpm.  See phossal's sig for instructions.

---

### Post by snypylo on 2007-03-10
I finally fixed it! My problem was that i copied the rpm java files into bin, which didn't work.
So, i deleted those, and instead changed the path to the new install i got from the Phossal guide: [http://phossal.com/thread?view=702216931](http://phossal.com/thread?view=702216931)
and now it works fine! :) 
Thank you for your help.

---

