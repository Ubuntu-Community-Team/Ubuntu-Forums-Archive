---
title: "Eclipse freezes"
date: 2008-11-20
forum: Programming Talk
---

### Post by Axel-P on 2008-11-20
Unhappy  Cant make Eclipse 3.2 work correctly
Hi!

I have a very big problem with Eclipse 3.2, each time i ask him to run one of my .java programs it freezes, i mean the little window created by Eclipse not Eclipse itself. Eclipse works fine its only that the little window (lets say a .showInputDialog kind of window) that freezes and i can only close it by closing Eclipse. I have tried many thing arround the forum and it stills not working.

This is my Java version:

java version "1.6.0_10"
Java(TM) SE Runtime Environment (build 1.6.0_10-b33)
Java HotSpot(TM) Server VM (build 11.0-b15, mixed mode)

And I modified /etc/eclipse/java_home so now it points to /usr/lib/jvm/java-6-sun

Thanks

---

### Post by Wolki on 2008-11-20
Do you really need 3.2? I had problems with that version, 3.3 worked much better, and even 3.4 seems stable enough to be used by now - I started running it a few weeks ago with no problems so far.

---

### Post by Axel-P on 2008-11-20
I'll try to redownload, but apt-get got me the 3,2 ant the update always tell me that i have the latest version, i though i couldn't get the latest one.

---

### Post by DirtDawg on 2008-11-20
Try running Eclipse via the terminal. When it crashes, you will probably get an error message that may tell you what the problem is, or maybe you can post here for someone else to look at.

---

### Post by Axel-P on 2008-11-20
Well it doesnt really prompt any error message at all, probrably beacuse eclipse doesnt freezes only the window eclipse prompts. By now im trying to installa 3.4 to see if the problem stills there

---

### Post by slavik on 2008-11-20
I would also suggest trying sun's 1.6 jvm ... I've had issues using gcj. Please remember about update-alternatives.

---

### Post by Axel-P on 2008-11-20
I did update alternatives and it didn't really help. By now i have eclipse 3.4 but the problem is that when i ran my .java this is prompted:

Exception in thread "main" java.lang.NoClassDefFoundError: 
   at gnu.java.lang.MainThread.run(libgcj.so.90)
Caused by: java.lang.ClassNotFoundException:  not found in gnu.gcj.runtime.SystemClassLoader{urls=[file:./], parent=gnu.gcj.runtime.ExtensionClassLoader{urls=[], parent=null}}
   at java.net.URLClassLoader.findClass(libgcj.so.90)
   at gnu.gcj.runtime.SystemClassLoader.findClass(libgcj.so.90)
   at java.lang.ClassLoader.loadClass(libgcj.so.90)
   at java.lang.ClassLoader.loadClass(libgcj.so.90)
   at gnu.java.lang.MainThread.run(libgcj.so.90)

I'm not used to Eclipse, so i don't know if its the same error than before or if its something wrong with my .java

---

### Post by DirtDawg on 2008-11-21
> **Axel-P said:**
> I did update alternatives and it didn't really help. By now i have eclipse 3.4 but the problem is that when i ran my .java this is prompted:

Exception in thread "main" java.lang.NoClassDefFoundError: 
   at gnu.java.lang.MainThread.run(libgcj.so.90)
Caused by: java.lang.ClassNotFoundException:  not found in gnu.gcj.runtime.SystemClassLoader{urls=[file:./], parent=gnu.gcj.runtime.ExtensionClassLoader{urls=[], parent=null}}
   at java.net.URLClassLoader.findClass(libgcj.so.90)
   at gnu.gcj.runtime.SystemClassLoader.findClass(libgcj.so.90)
   at java.lang.ClassLoader.loadClass(libgcj.so.90)
   at java.lang.ClassLoader.loadClass(libgcj.so.90)
   at gnu.java.lang.MainThread.run(libgcj.so.90)

I'm not used to Eclipse, so i don't know if its the same error than before or if its something wrong with my .java
There is a package called 'eclipse-gcj' in the repositories. Maybe you need to install that (if you haven't already)?

---

### Post by jespdj on 2008-11-21
> **Axel-P said:**
> I did update alternatives and it didn't really help. By now i have eclipse 3.4 but the problem is that when i ran my .java this is prompted:

Exception in thread "main" java.lang.NoClassDefFoundError: 
   at gnu.java.lang.MainThread.run(libgcj.so.90)
Caused by: java.lang.ClassNotFoundException:  not found in gnu.gcj.runtime.SystemClassLoader{urls=[file:./],
...
You said you did update-alternatives, but you are still using GNU Java (so you didn't to that correctly). Install Sun Java 6:
```
sudo apt-get install sun-java6-jdk
```
And then do this to make it the default Java used on your system:
```
sudo update-java-alternatives -s java-6-sun
```

---

