---
title: "iReport"
date: 2008-10-08
forum: New to Ubuntu
---

### Post by rybaxs on 2008-10-08
iReport is not working
from ghf

> 
Hi all
I installed iReport that uses JasperReports in Ubuntu 7.10 gutsy
from this repository

[http://srvremi.free.fr/ubuntu](http://srvremi.free.fr/ubuntu)

and its dependencies are :
sun-java6-jre
bubuntu-common
and the last one is available in ireport repository

but when I launch the application this error message appears in the terminal:
Exception in thread "main" java.lang.UnsupportedClassVersionError: org/jdesktop/swingx/JXTable (Unsupported major.minor version 49.0)
at java.lang.ClassLoader.defineClass0(Native Method)
at java.lang.ClassLoader.defineClass(ClassLoader.java :539)
at java.security.SecureClassLoader.defineClass(Secure ClassLoader.java:123)
at java.net.URLClassLoader.defineClass(URLClassLoader .java:251)
at java.net.URLClassLoader.access$100(URLClassLoader. java:55)
at java.net.URLClassLoader$1.run(URLClassLoader.java: 194)
at java.security.AccessController.doPrivileged(Native Method)
at java.net.URLClassLoader.findClass(URLClassLoader.j ava:187)
at java.lang.ClassLoader.loadClass(ClassLoader.java:2 89)
at sun.misc.Launcher$AppClassLoader.loadClass(Launche r.java:274)
at java.lang.ClassLoader.loadClass(ClassLoader.java:2 35)
at java.lang.ClassLoader.loadClassInternal(ClassLoade r.java:302)
at java.lang.ClassLoader.defineClass0(Native Method)
at java.lang.ClassLoader.defineClass(ClassLoader.java :539)
at java.security.SecureClassLoader.defineClass(Secure ClassLoader.java:123)
at java.net.URLClassLoader.defineClass(URLClassLoader .java:251)
at java.net.URLClassLoader.access$100(URLClassLoader. java:55)
at java.net.URLClassLoader$1.run(URLClassLoader.java: 194)
at java.security.AccessController.doPrivileged(Native Method)
at java.net.URLClassLoader.findClass(URLClassLoader.j ava:187)
at java.lang.ClassLoader.loadClass(ClassLoader.java:2 89)
at sun.misc.Launcher$AppClassLoader.loadClass(Launche r.java:274)
at java.lang.ClassLoader.loadClass(ClassLoader.java:2 35)
at java.lang.ClassLoader.loadClassInternal(ClassLoade r.java:302)
at it.businesslogic.ireport.gui.ValuesDialog.initAll( ValuesDialog.java:7
at it.businesslogic.ireport.gui.ValuesDialog.<init>(V aluesDialog.java:66)
at it.businesslogic.ireport.gui.MainFrame.<init>(Main Frame.java:532)
at it.businesslogic.ireport.gui.MainFrame.main(MainFr ame.java:8016)

they said in this site :
[http://www.jasperforge.org/index.php...tid=9&id=29576](http://www.jasperforge.org/index.php...tid=9&id=29576)
that the problem is from java version
but I modified the path of JAVA_HOME to /usr/lib/jvm/java-6-sun-1.6.0.03

so What is the problem ??





Sorry ghf, I have sufficient privileges to access your page,

What version is your iReport?
Did you copy the tool.jar from jre?

please reply..

---

### Post by ghf on 2008-10-08
iReport now is working well ..
it is iReport version 2.0
and no I didnt copy tool.jar

:)

---

### Post by rybaxs on 2008-10-08
> **ghf said:**
> iReport now is working well ..
it is iReport version 2.0
and no I didnt copy tool.jar

:)


Hi!.. iReport 2.0.X ? 
mine is 2.0.3

Can you help me.. When I compile and Execute iReport stop
responding. did u encounter this event?

---

