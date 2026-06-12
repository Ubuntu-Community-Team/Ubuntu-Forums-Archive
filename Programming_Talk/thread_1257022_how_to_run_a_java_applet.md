---
title: "how to run a java applet?"
date: 2009-09-03
forum: Programming Talk
---

### Post by abhilashm86 on 2009-09-03
should i always embed java applet in html and run or can i run in terminal/ eclipse? usually i get this error ```
import javax.swing.JApplet;
import java.awt.Graphics;

public class j18 extends JApplet {
    public void paint(Graphics g) {
	g.drawRect(0, 0, 
		   getSize().width - 1,
		   getSize().height - 1);
        g.drawString("Hello world!", 5, 15);
    }
}

```
error is, ```
abhilash@abhilash:~$ javac j18.java 
abhilash@abhilash:~$ java j18
Exception in thread "main" java.lang.NoSuchMethodError: main

```

---

### Post by credobyte on 2009-09-03
Eclipse in-built applet viewer.

---

### Post by abhilashm86 on 2009-09-03
i just now tried using <html>, din't understand the error.....
here's html code, ```
<html>
<body bgcolor="red">
<applet code="/home/abhilash/j18.class" width="300" height="300">

</applet>
</body>
</html>

```
when i try running on firefox.......
```
abhilash@abhilash:~$ firefox pgm21.html 

```
i'll get a error ```
Java Plug-in 1.6.0_16
Using JRE version 1.6.0_16-b01 Java HotSpot(TM) Client VM
User home directory = /home/abhilash
java.lang.NoClassDefFoundError: /home/abhilash/j18 (wrong name: j18)
	at java.lang.ClassLoader.defineClass1(Native Method)
	at java.lang.ClassLoader.defineClass(ClassLoader.java:621)
	at java.security.SecureClassLoader.defineClass(SecureClassLoader.java:124)
	at sun.plugin2.applet.Applet2ClassLoader.findClass(Applet2ClassLoader.java:141)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:307)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:252)
	at sun.plugin2.applet.Plugin2ClassLoader.loadCode(Plugin2ClassLoader.java:433)
	at sun.plugin2.applet.Plugin2Manager.createApplet(Plugin2Manager.java:2880)
	at sun.plugin2.applet.Plugin2Manager$AppletExecutionRunnable.run(Plugin2Manager.java:1397)
	at java.lang.Thread.run(Thread.java:619)
Exception: java.lang.NoClassDefFoundError: /home/abhilash/j18 (wrong name: j18)
java.lang.NoClassDefFoundError: /home/abhilash/j18 (wrong name: j18)
	at java.lang.ClassLoader.defineClass1(Native Method)
	at java.lang.ClassLoader.defineClass(ClassLoader.java:621)
	at java.security.SecureClassLoader.defineClass(SecureClassLoader.java:124)
	at sun.plugin2.applet.Applet2ClassLoader.findClass(Applet2ClassLoader.java:141)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:307)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:252)
	at sun.plugin2.applet.Plugin2ClassLoader.loadCode(Plugin2ClassLoader.java:433)
	at sun.plugin2.applet.Plugin2Manager.createApplet(Plugin2Manager.java:2880)
	at sun.plugin2.applet.Plugin2Manager$AppletExecutionRunnable.run(Plugin2Manager.java:1397)
	at java.lang.Thread.run(Thread.java:619)
Exception: java.lang.NoClassDefFoundError: /home/abhilash/j18 (wrong name: j18)
java.lang.NoClassDefFoundError: /home/abhilash/j18 (wrong name: j18)
	at java.lang.ClassLoader.defineClass1(Native Method)
	at java.lang.ClassLoader.defineClass(ClassLoader.java:621)
	at java.security.SecureClassLoader.defineClass(SecureClassLoader.java:124)
	at sun.plugin2.applet.Applet2ClassLoader.findClass(Applet2ClassLoader.java:141)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:307)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:252)
	at sun.plugin2.applet.Plugin2ClassLoader.loadCode(Plugin2ClassLoader.java:433)
	at sun.plugin2.applet.Plugin2Manager.createApplet(Plugin2Manager.java:2880)
	at sun.plugin2.applet.Plugin2Manager$AppletExecutionRunnable.run(Plugin2Manager.java:1397)
	at java.lang.Thread.run(Thread.java:619)
Exception: java.lang.NoClassDefFoundError: /home/abhilash/j18 (wrong name: j18)

```
how exactly i need to run?

---

### Post by abhilashm86 on 2009-09-03
> **credobyte said:**
> Eclipse in-built applet viewer.

should i need to run on terminal for applet viewer? i don't see option of it in eclipse, now i'll google about how running it.....

---

### Post by Zugzwang on 2009-09-03
Use the codebase attibute to fix your program. See here:

[http://java.sun.com/docs/books/tutorial/deployment/applet/html.html](http://java.sun.com/docs/books/tutorial/deployment/applet/html.html)

---

