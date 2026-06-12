---
title: "executable jar not executing"
date: 2008-09-06
forum: Programming Talk
---

### Post by shadylookin on 2008-09-06
I've tried exporting a java project that I wrote in eclipse. It uses slick libraries. I developed it on linux and vista because it uses native libraries. 

When i exported it on the linux machine I get this error when i try and run the jar file

```

java -jar ./test.jar
Exception in thread "main" java.lang.NoClassDefFoundError: org/newdawn/slick/BasicGame
	at java.lang.ClassLoader.defineClass1(Native Method)
	at java.lang.ClassLoader.defineClass(ClassLoader.java:620)
	at java.security.SecureClassLoader.defineClass(SecureClassLoader.java:124)
	at java.net.URLClassLoader.defineClass(URLClassLoader.java:260)
	at java.net.URLClassLoader.access$000(URLClassLoader.java:56)
	at java.net.URLClassLoader$1.run(URLClassLoader.java:195)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:306)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:276)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:319)
Caused by: java.lang.ClassNotFoundException: org.newdawn.slick.BasicGame
	at java.net.URLClassLoader$1.run(URLClassLoader.java:200)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:306)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:276)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:319)
	... 12 more

```

when I exported the project it works fine on the vista machine I originally made it on, but when I try and run it on other windows machines it refuses to run and I get this error.

```
java -jar Game.jar
Exception in thread "main" java.lang.UnsatisfiedLinkError: no lwjgl in java.library.path 
 
```

and then it lists a whole bunch of places where it comes up.

I'm guessing there is something wrong with the libraries not getting packaged because when I use just the standard java api I don't have a problem with exporting executable jars. How do I go about fixing this?

Thanks for the help.

---

### Post by Reiger on 2008-09-07
Check your manifest file, specifically the Classpath entries. Essentially it complains about **missing** files.

---

### Post by shadylookin on 2008-09-07
I think I have figured out the problem. When I export using eclipse it doesn't sign the jars. Since I'm using native libraries the jars have to be signed apparently. So I guess the real question is how do I sign the jar files?

---

### Post by shadylookin on 2008-09-07
more specifically when I go into eclipse and click export, runable jar, then select the main class and click finish I get this warning message

> 
This operation repacks referenced libraries.

please review the licenses associated with libraries you wish to reference to make sure you are able to repack them using this application. Note also that this operation does not copy signature files from original libraries to the generated jar file.


however when I did the tutorial shown here [http://java.sun.com/docs/books/tutorial/security/toolfilex/step2.html](http://java.sun.com/docs/books/tutorial/security/toolfilex/step2.html)

it said it was signed and that the certificate would expire in 6 months. when i tried to run it I still get the same error. 

```
java -jar ./stest.jar
Exception in thread "main" java.lang.UnsatisfiedLinkError: no lwjgl in java.library.path
	at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1682)
	at java.lang.Runtime.loadLibrary0(Runtime.java:823)
	at java.lang.System.loadLibrary(System.java:1030)
	at org.lwjgl.Sys$1.run(Sys.java:75)
	at java.security.AccessController.doPrivileged(Native Method)
	at org.lwjgl.Sys.doLoadLibrary(Sys.java:68)
	at org.lwjgl.Sys.loadLibrary(Sys.java:84)
	at org.lwjgl.Sys.<clinit>(Sys.java:101)
	at org.lwjgl.opengl.Display.<clinit>(Display.java:128)
	at org.newdawn.slick.AppGameContainer$1.run(AppGameContainer.java:38)
	at java.security.AccessController.doPrivileged(Native Method)
	at org.newdawn.slick.AppGameContainer.<clinit>(AppGameContainer.java:35)
	at cs.GameSample.main(GameSample.java:134)

```

---

