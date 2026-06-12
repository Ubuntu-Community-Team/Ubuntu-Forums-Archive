---
title: "Eclipse - Cannot load AWT toolkit"
date: 2007-04-29
forum: Programming Talk
---

### Post by OMRebel on 2007-04-29
Hey guys, I'm taking a Java course, and am running into a problem.  Here's some info:
Ubuntu 7.04
Eclipse 3.2.2

brad@brad-desktop:~$ java -version
java version "1.6.0"
Java(TM) SE Runtime Environment (build 1.6.0-b105)
Java HotSpot(TM) Client VM (build 1.6.0-b105, mixed mode, sharing)


I've uploaded the simple Java file that I'm trying to run.  But, I get the following errors:
Exception in thread "main" java.awt.AWTError: Cannot load AWT toolkit: gnu.java.awt.peer.gtk.GtkToolkit
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.70)
   at java.awt.GraphicsEnvironment.getLocalGraphicsEnvironment(libgcj.so.70)
   at java.awt.Window.<init>(libgcj.so.70)
   at java.awt.Frame.<init>(libgcj.so.70)
   at ChatClient.launchFrame(ChatClient.java:26)
   at ChatClient.main(ChatClient.java:46)
Caused by: java.lang.UnsatisfiedLinkError: libgtkpeer: libgtkpeer.so: cannot open shared object file: No such file or directory
   at java.lang.Runtime._load(libgcj.so.70)
   at java.lang.Runtime.loadLibrary(libgcj.so.70)
   at java.lang.System.loadLibrary(libgcj.so.70)
   at gnu.java.awt.peer.gtk.GtkToolkit.<clinit>(libgcj.so.70)
   at java.lang.Class.initializeClass(libgcj.so.70)
   at java.lang.Class.forName(libgcj.so.70)
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.70)
   ...5 more

How do I get this straightened out?
Thanks!

---

### Post by OMRebel on 2007-04-29
Figured it out.  It was a setting in Eclipse that I had to change.  For those that might be having the same problem, whenever you run the application, go to the JRE tab, and make sure Sun is selected, and not the gcj.  For me, I had to add the Sun version to the list.   See screenshot for how I set it up.  But, it's working now. :o)

---

### Post by Maxamor on 2007-05-02
Thanks a BUNCH. This really helped me out and your screenshot was exceptional. My issues are solved now, too.

Thanks again!

---

### Post by mlago on 2007-05-06
Thanks a lot, helpful for me also

---

### Post by zuzuzzzip on 2007-07-26
nice one :)
Thanks!

---

### Post by muzzamo on 2007-08-08
For the record, I was getting this problem when trying to create a visual class in eclipse and using the drag and drop swing tools. The widgets in the preview were not showing, just with a little red cross. Hover over them to get the no class def found error on eclipse gnu.java.awt.peer.gtk.GtkToolkit .

sudo apt-get install sun-java6-jre 

will install the jre. 

Then had to follow the instructions here:

[http://wiki.liferay.com/index.php/Liferay_Development_Environment:_Ubuntu_Linux#Eclipse_IDE](http://wiki.liferay.com/index.php/Liferay_Development_Environment:_Ubuntu_Linux#Eclipse_IDE) 

To change the jvm.

---

### Post by rwales on 2007-09-12
Thanks a lot OMRebel & muzzamo. I've just run into the same problem using swing & your comments fixed it.

---

