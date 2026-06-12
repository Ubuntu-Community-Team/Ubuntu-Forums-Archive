---
title: "java runtime"
date: 2008-07-03
forum: Packaging and Compiling Programs
---

### Post by e-nDrju on 2008-07-03
hi
maybe i put this thread into wrong section but I couldn`t find any better. I have a program written in java, which I use in Windows, but I wich I could use it on linux.
when i type    java xxxxx.jar i have error message:


Exception in thread "main" java.lang.NoClassDefFoundError: WspomaganieReklamacji/jar
Caused by: java.lang.ClassNotFoundException: WspomaganieReklamacji.jar
	at java.net.URLClassLoader$1.run(URLClassLoader.java:200)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:306)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:276)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:319)


Is there any system compatibility problem? Or maybe i am doing something wrong? Thanks in advance.

---

### Post by screech on 2008-07-05
did you try 'java -jar ***.jar' ?

---

### Post by tinny on 2008-07-06
> **e-nDrju said:**
> hi
maybe i put this thread into wrong section but I couldn`t find any better. I have a program written in java, which I use in Windows, but I wich I could use it on linux.
when i type    java xxxxx.jar i have error message:


Exception in thread "main" java.lang.NoClassDefFoundError: WspomaganieReklamacji/jar
Caused by: java.lang.ClassNotFoundException: WspomaganieReklamacji.jar
	at java.net.URLClassLoader$1.run(URLClassLoader.java:200)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:306)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:276)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:319)


Is there any system compatibility problem? Or maybe i am doing something wrong? Thanks in advance.

It wont be a Linux problem.

Have you copied over all the jar files from where you have this application running in windows? Looks to me like you are missing a jar file that your application is dependant on (a jar file that contains a class you need, a class that should be on your class path).

Also the real stack trace would be helpful.

---

### Post by tinny on 2008-07-07
BTW, this question would be better off being in the programming section.

[http://ubuntuforums.org/forumdisplay.php?f=39]("http://ubuntuforums.org/forumdisplay.php?f=39")

---

### Post by e-nDrju on 2008-07-07
> **screech said:**
> did you try 'java -jar ***.jar' ?

easy solutions are the best :)
thank You - problem solved

---

