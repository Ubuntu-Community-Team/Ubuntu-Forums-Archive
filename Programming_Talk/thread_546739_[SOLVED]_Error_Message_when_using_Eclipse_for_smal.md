---
title: "[SOLVED] Error Message when using Eclipse for small graphics"
date: 2007-09-09
forum: Programming Talk
---

### Post by chr on 2007-09-09
hello,

i'm on an academic course learning java. the lecturer said we should use eclipse for the programming.

when i started to program small apps, which were just runing on the console, everything was ok.   

bus as soon as i start to work with graphical apllications i get an error mesage when i want to run it:

Exception in thread "main" java.awt.AWTError: Cannot load AWT toolkit: gnu.java.awt.peer.gtk.GtkToolkit
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.70)
   at java.awt.GraphicsEnvironment.getLocalGraphicsEnvironment(libgcj.so.70)
   at java.awt.Window.<init>(libgcj.so.70)
   at java.awt.Frame.<init>(libgcj.so.70)
   at javax.swing.JFrame.<init>(libgcj.so.70)
   at EmptyFrameViewer.main(EmptyFrameViewer.java:11)
Caused by: java.lang.UnsatisfiedLinkError: libgtkpeer: libgtkpeer.so: cannot open shared object file: No such file or directory
   at java.lang.Runtime._load(libgcj.so.70)
   at java.lang.Runtime.loadLibrary(libgcj.so.70)
   at java.lang.System.loadLibrary(libgcj.so.70)
   at gnu.java.awt.peer.gtk.GtkToolkit.<clinit>(libgcj.so.70)
   at java.lang.Class.initializeClass(libgcj.so.70)
   at java.lang.Class.forName(libgcj.so.70)
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.70)
   ...5 more

when i use another IDE(NetBeans) everything works fine.

i hope there is someone who can help me.

Best regards

christoph

---

### Post by chr on 2007-09-09
i solved the problem. there is a very good description in the community.

see the following link.

[http://ubuntuforums.org/showthread.php?t=427887&highlight=Eclipse+Error](http://ubuntuforums.org/showthread.php?t=427887&highlight=Eclipse+Error)

best regards

christoph

---

