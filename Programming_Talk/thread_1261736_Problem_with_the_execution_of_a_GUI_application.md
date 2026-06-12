---
title: "Problem with the execution of a GUI application"
date: 2009-09-09
forum: Programming Talk
---

### Post by MrSebastian on 2009-09-09
Hello, 
I have the following problem: I have developed an application (to be exact a graphical user interface) using NetBeans 6.7. 
When I build and execute the application in the platform, it's all right. 
But, when I try to execute the .jar corresponding to the app, launching it by 

java -jar DrawGUI.jar 

I obtain this error:

```

Exception in thread "main" java.lang.NoClassDefFoundError: org/jdesktop/application/SingleFrameApplication
    at java.lang.ClassLoader.defineClass1(Native Method)
    at java.lang.ClassLoader.defineClass(ClassLoader.java:621)
    at java.security.SecureClassLoader.defineClass(SecureClassLoader.java:124)
    at java.net.URLClassLoader.defineClass(URLClassLoader.java:260)
    at java.net.URLClassLoader.access$000(URLClassLoader.java:56)
    at java.net.URLClassLoader$1.run(URLClassLoader.java:195)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:307)
    at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:301)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:252)
    at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:320)
Caused by: java.lang.ClassNotFoundException: org.jdesktop.application.SingleFrameApplication
    at java.net.URLClassLoader$1.run(URLClassLoader.java:200)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:307)
    at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:301)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:252)
    at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:320)
    ... 12 more
Could not find the main class: drawgui.DrawGUIApp. Program will exit.


```It's a problem of missing package? How can I fix this error? :confused:

Thanks to all in advance 
MrSebastian

---

### Post by bogdan.veringioiu on 2009-09-09
Hi.
Your application needs the dependencies (.jar files where org/jdesktop/application/SingleFrameApplication class resides).

You have to run the jar something like this:
java -classpath mylib1.jar:mylib2.jar -jar DrawGUI.jar
You have to see which are the libraries that your netbeans project use, and pass them all to the command line when running your app.

Try to see in the netbeans console (I use different ide) the command used to run your jar...

Cheers

---

### Post by MrSebastian on 2009-09-09
Thanks, bogdan.veringioiu ;)
Actually I thinked this too, just after posting this message.
My approach was to put the jar files needed into the external libraries folder (lib/ext) of
my Java Virtual Machine, so that they were available for all applications.

Thanks again,
MrSebastian.

---

