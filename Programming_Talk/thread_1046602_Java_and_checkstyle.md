---
title: "Java and checkstyle"
date: 2009-01-21
forum: Programming Talk
---

### Post by robz0rz on 2009-01-21
Hey all

I installed checkstyle in Ubuntu 8.04 through apt-get install checkstyle

However, I'm having trouble using it. According to the [checkstyle website]("http://checkstyle.sourceforge.net/cmdline.html"), using the command **java com.puppycrawl.tools.checkstyle.Main -c my_checks.xml MyClass.java** should run checkstyle.. However, I'm facing an error:

```
Exception in thread "main" java.lang.NoClassDefFoundError: com/puppycrawl/tools/checkstyle/Main
Caused by: java.lang.ClassNotFoundException: com.puppycrawl.tools.checkstyle.Main
	at java.net.URLClassLoader$1.run(URLClassLoader.java:217)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:323)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:268)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:336)
Could not find the main class: com.puppycrawl.tools.checkstyle.Main. Program will exit.
```

How come? I thought I installed checstyle using apt-get? Can someone please tell me how to fix this? Google wasn't too helpful...

---

### Post by myrtle1908 on 2009-01-21
You need to ensure the checkstyle library is in your classpath.  Do you know where the checkstyle JAR file is?  If so, try the following:-

```
java -cp /path/to/checkstyle-all-4.4.jar com.puppycrawl.tools.checkstyle.Main -c my_checks.xml MyClass.java
```

---

### Post by robz0rz on 2009-01-22
I couldn't find out where it installed, I used apt-get to install it. I ended up downloading a jar archive from the official website and I called checkstyle directly from there. I don't know the details, but to me it looks like the installation of checkstyle through apt-get is broken, if it doesn't automatically add checkstyle to my classpath.

---

