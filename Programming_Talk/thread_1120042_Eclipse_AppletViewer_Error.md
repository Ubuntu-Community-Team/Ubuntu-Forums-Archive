---
title: "Eclipse AppletViewer Error"
date: 2009-04-08
forum: Programming Talk
---

### Post by MasterAchilles on 2009-04-08
I get this error when I try to run an applet on Ubuntu 8.10 in Eclipse:

```
Exception in thread "main" java.lang.NoClassDefFoundError: sun.applet.AppletViewer
   at gnu.java.lang.MainThread.run(libgcj.so.90)
Caused by: java.lang.ClassNotFoundException: sun.applet.AppletViewer not found in gnu.gcj.runtime.SystemClassLoader{urls=[file:/home/oswald/workspace/Tutorials/], parent=gnu.gcj.runtime.ExtensionClassLoader{urls=[], parent=null}}
   at java.net.URLClassLoader.findClass(libgcj.so.90)
   at java.lang.ClassLoader.loadClass(libgcj.so.90)
   at java.lang.ClassLoader.loadClass(libgcj.so.90)
   at gnu.java.lang.MainThread.run(libgcj.so.90)
```

I read this other forum post about downloading another JRE and then The solution - Click Run > Run then click on JRE and select the required JRE.

There is a search button and an add button when you do that. When I press the search button it displays all the directories I have so where do look for JRE's I have downloaded from the Synaptic Package manager?

When I do that I have no idea where to look in order to find where the JRE was downloaded to.

Right now the JRE setting is set to java-1.5.0-gcj-4.3-1.5.0.0

---

### Post by Froodolt on 2009-04-21
Same here.8-[

Done the [[COLOR="Navy"]instructions in the sticky[/COLOR]]("http://ubuntuforums.org/showthread.php?t=713622"), but didn't work for me.

> 0.b. Make sure the sun-java6-jdk package is installed

This package installs the essential tools needed to write and run Java programs.
```
sudo aptitude install sun-java6-jdk
```
Also run this to set the Sun Java as the default.
```
sudo update-java-alternatives --set java-6-sun
```

Whats wrong??... Am I missing something here??...:-s

---

### Post by Froodolt on 2009-04-22
PROBLEM SOLVED (for me anyway)
After I've installed the sun-java stuff (above post), I did the:
> I read this other forum post about downloading another JRE and then The solution - Click Run > Run then click on JRE and select the required JRE.

There is a search button and an add button when you do that. When I press the search button it displays all the directories I have so where do look for JRE's I have downloaded from the Synaptic Package manager?
After I pressed the search button, I started filling in the directorie where the default package was located. (for me /usr/lib/jvm) and than started the search. 
Then it found:
```
Java-1.5.0-gcj-4.3-1.5.0.0
java-6-sun
java-6-sun-1.6.0.10
java-gcj
``` 
 Selected java-6-sun, and now it runs!

_EDIT:_
Everything runs better now. 
Not only applets, but other applications that I run in eclipse run much smoother.

---

