---
title: "Fix For jEdit Problem When Upgrading to Sun Java 1.6.07"
date: 2008-10-17
forum: Programming Talk
---

### Post by david64 on 2008-10-17
Hi. I have just upgraded Ubuntu and part of the upgrade was an update to Sun Java.

After doing so and a restart, my fav. text editor jEdit was dead. I was getting this error:

> Exception in thread "main" java.lang.NoClassDefFoundError: .usr.bin.jedit
   at gnu.java.lang.MainThread.run(libgcj.so.81)
Caused by: java.lang.ClassNotFoundException: .usr.bin.jedit not found in gnu.gcj.runtime.SystemClassLoader{urls=[file:./], parent=gnu.gcj.runtime.ExtensionClassLoader{urls=[], parent=null}}
   at java.net.URLClassLoader.findClass(libgcj.so.81)
   at gnu.gcj.runtime.SystemClassLoader.findClass(libgcj.so.81)
   at java.lang.ClassLoader.loadClass(libgcj.so.81)
   at java.lang.ClassLoader.loadClass(libgcj.so.81)
   at gnu.java.lang.MainThread.run(libgcj.so.81)


I tried re-installing jEdit, but it still didn't work. I tred setting an env. var. but still didn't work.

However, I manage to fix the problem by toggeling my Java I am using. You can do this by:

sudo update-java-alternatives -s java-6-sun

I set mine to some other Java and then back to java-6-sun and was back in business :)

You can get more info on the Java toggeling here:

[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)


Hope this helps some bloody Linux noobs like me.

---

