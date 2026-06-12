---
title: "Eclipse Problem"
date: 2006-03-30
forum: Programming Talk
---

### Post by EvilToad on 2006-03-30
Hi, i am using eclipse, i have j2sdk1.5-sun installed, i am getting the following error when running an applet in eclipse and i am not sure how to resolve problem.

> java.lang.ClassNotFoundException: sun.applet.AppletViewer not found in java.lang.ClassLoader$1{urls=[file:/home/evilmonkey/workspace/LayoutManagerCWK/], parent=null}
   at java.net.URLClassLoader.findClass (URLClassLoader.java:841)
   at java.lang.ClassLoader.loadClass (ClassLoader.java:360)
   at java.lang.ClassLoader$1.loadClass (ClassLoader.java:1285)
   at java.lang.ClassLoader.loadClass (ClassLoader.java:304)
   at java.lang.VirtualMachine.main (VirtualMachine.java:99)


any help would be most appreciated

---

### Post by gtoddv on 2006-04-09
Try this in the terminal and see if it helps:

echo JAVA_HOME=/usr/lib/j2re1.5-sun > ~/.eclipse/eclipserc

---

