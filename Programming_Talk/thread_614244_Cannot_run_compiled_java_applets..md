---
title: "Cannot run compiled java applets."
date: 2007-11-15
forum: Programming Talk
---

### Post by t0n1 on 2007-11-15
Hello.
I can compile Java applets, but I cannot run them. This is what I get:
```

tony@xenus:~/Information/Studies/Java$ javac Loke.java
tony@xenus:~/Information/Studies/Java$ java Loke
The program 'java' can be found in the following packages:
 * cacao
 * j2re1.4
 * kaffe
 * jamvm
 * java-gcj-compat
 * gij-4.1
 * gij-4.2
 * sablevm
Try: sudo apt-get install <selected package>
bash: java: command not found

```
However, installing those packages does not solve the problem.
I currently have java 1.6.0_03 from Sun installed.
Any help is appreciated.

---

### Post by geirha on 2007-11-15
```
update-java-alternatives --list
``` this will list the java distributions you have installed (through ubuntu's package system). Run ```
sudo update-java-alternatives --set java-6-sun
``` or whatever you wish to use. That command will ensure that java and javac points to the correct versions of java and javac.

---

### Post by t0n1 on 2007-11-16
Thank you, that worked.

---

