---
title: "Cannot load AWT toolkit ??"
date: 2007-03-19
forum: Programming Talk
---

### Post by derby007 on 2007-03-19
I'm getting the following error when i try and run my Java Application from the command line. Does anybody know how i might fix it ?

I tried setting different LooknFeel's but I still get the same error....
Is the libgcj.so.7 library/file causing me a problem?
Note: its a simple application, with just a few buttons, with standard layouts, & no fancy outside libraries/jars.

:confused: 


>>>java -jar SBWithMain.jar
Exception in thread "main" java.awt.AWTError: Cannot load AWT toolkit: gnu.java.awt.peer.gtk.GtkToolkit
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.7)
   at java.awt.EventQueue.invokeLater(libgcj.so.7)
   at smallbyteswithmain.Main.main(Main.java:35)
Caused by: java.lang.ClassNotFoundException: gnu.java.awt.peer.gtk.GtkToolkit
   at java.lang.Class.forName(libgcj.so.7)
   at java.lang.Class.forName(libgcj.so.7)
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.7)
   ...2 more

---

### Post by Ragazzo on 2007-03-19
GCJ doesn't support AWT or Swing. You need to use Sun's Java.

---

### Post by derby007 on 2007-03-19
em..........I don't understand......can I not run my file using a different Look&Feel ??

And I'm using Sun Java Studio Enterprise 8 !!

Please elaborate, as I try to understand my problems....

---

### Post by laxmanb on 2007-03-19
You don't have Sun's Java set up properly... for eg. type java -version and youll notice that you're not using the Sun's Hotspot JRE. You're using the GNU Compiler for Java... (something like that)

use **update-alternatives** @ the terminal... I think you can choose Sun's Java as the default JRE using that program...

---

### Post by derby007 on 2007-03-19
Cheers....:)

---

### Post by derby007 on 2007-03-20
Bump:
New problem: i tried to run it on a WinXP machine but got this error:

>>java -jar smallb1.jar

Exception in thread "main" java.lang.UnsupportedClassVersionError: smallb1/mainGUI (Unsupported major.minor version 49.0)
        at java.lang.ClassLoader.defineClass0(Native Method)
        at java.lang.ClassLoader.defineClass(Unknown Source)
        at java.security.SecureClassLoader.defineClass(Unknown Source)
        at java.net.URLClassLoader.defineClass(Unknown Source)
        at java.net.URLClassLoader.access$100(Unknown Source)
        at java.net.URLClassLoader$1.run(Unknown Source)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.net.URLClassLoader.findClass(Unknown Source)
        at java.lang.ClassLoader.loadClass(Unknown Source)
        at sun.misc.Launcher$AppClassLoader.loadClass(Unknown Source)
        at java.lang.ClassLoader.loadClass(Unknown Source)
        at java.lang.ClassLoader.loadClassInternal(Unknown Source)

where Java Version is:
>>java -version
java version "1.4.2_03"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.4.2_03-b02)
Java HotSpot(TM) Client VM (build 1.4.2_03-b02, mixed mode)

Any ideas, pls? 
note: this PC has JRE 1.4 & JDK 1.5.....

---

