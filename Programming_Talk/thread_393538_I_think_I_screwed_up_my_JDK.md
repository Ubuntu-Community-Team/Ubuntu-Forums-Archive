---
title: "I think I screwed up my JDK"
date: 2007-03-25
forum: Programming Talk
---

### Post by Ashercim on 2007-03-25
Hi all.

I am somewhat new to linux but quite familiar with computers.  I need some help resolving a problem that I think is caused by incompatible Java versions.

I'm running Ubuntu 6.10 and recently tried to install the sun JDK 6.

I wrote a quick test app and this is what happened:

Exception in thread "main" java.lang.UnsupportedClassVersionError: Bad version number in .class file
        at java.lang.ClassLoader.defineClass1(Native Method)
        at java.lang.ClassLoader.defineClass(ClassLoader.java:620)
        at java.security.SecureClassLoader.defineClass(SecureClassLoader.java:124)
        at java.net.URLClassLoader.defineClass(URLClassLoader.java:260)
        at java.net.URLClassLoader.access$100(URLClassLoader.java:56)
        at java.net.URLClassLoader$1.run(URLClassLoader.java:195)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:306)
        at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:268)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
        at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:319)

The test app is just a basic 'hello world' type of program and compiles and runs on my windows machines.

What I've found is that it seems that the JRE itself wasn't upgraded to 1.6 when I installed the JDK.  The reason I believe this is true is this:

ashercim@command:~/Projects$ java -version
java version "1.5.0_08"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_08-b03)
Java HotSpot(TM) Client VM (build 1.5.0_08-b03, mixed mode, sharing)
ashercim@command:~/Projects$ 
ashercim@command:~/Projects$ javac -version
javac 1.6.0
ashercim@command:~/Projects$ 

I can't seem to uninstall or update Java at all on this machine.  I installed java originally using the instructions at sun's website for their self extracting .bin file.

My question specifically is this:
Am I correct that this program won't run because it is being compiled with a later version of the compiler than the JRE?

Will uninstalling and reinstalling java solve this problem?

If it will, how can I force java to be completely uninstalled?
(It doesn't show up in Add/Remove Programs)

Thanks in advance to anyone who can help.

---

### Post by josephus on 2007-03-25
Try this to make sure your system is pointed to the current verision

```
 sudo update-alternatives --config java
```

---

### Post by Ashercim on 2007-03-26
Thanks!

That did the trick.

I wish I asked you guys 2 days ago.  LOL

---

### Post by josephus on 2007-03-26
Glad to help.

---

### Post by Ramses de Norre on 2007-03-26
This will set all java-related programs to java 6:
```
sudo update-java-alternatives -s java-6-sun
```

---

