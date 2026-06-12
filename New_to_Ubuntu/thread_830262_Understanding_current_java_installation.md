---
title: "Understanding current java installation"
date: 2008-06-15
forum: New to Ubuntu
---

### Post by japhyr on 2008-06-15
Hello, I am having trouble understanding my current java installation.  Here is the result of java -version:
```
java version "1.5.0"
gij (GNU libgcj) version 4.2.3 (Ubuntu 4.2.3-2ubuntu6)

Copyright (C) 2007 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
```

I am trying to run Jin, a chess interface program.  When I go to the jin folder and run it with ./jin, this is what I get:
```
You seem to be running GNU's Java implementation, which is incomplete.
Jin requires Sun's Java (or a fully compatible version) 1.4 or later.
If you can't install it with your distribution's package manager, you
can obtain and install it manually from http://www.java.com
```

If I try to run it from the jin directory with java -jar jin.jar, I get a huge list of errors:
```
java.awt.AWTError: Cannot load AWT toolkit: gnu.java.awt.peer.gtk.GtkToolkit
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.81)
   at javax.swing.plaf.basic.BasicLookAndFeel.initialize(libgcj.so.81)
   at javax.swing.UIManager.setLookAndFeel(libgcj.so.81)
   at javax.swing.UIManager.<clinit>(libgcj.so.81)
   at java.lang.Class.initializeClass(libgcj.so.81)
   at free.jin.Jin.restoreLookAndFeel(Unknown Source)
   at free.jin.Jin.<init>(Unknown Source)
   at free.jin.Jin.createInstance(Unknown Source)
   at free.jin.JinApplication.main(Unknown Source)
Caused by: java.lang.UnsatisfiedLinkError: libgtkpeer: libgtkpeer.so: cannot open shared object file: No such file or directory
   at java.lang.Runtime._load(libgcj.so.81)
   at java.lang.Runtime.loadLibrary(libgcj.so.81)
   at java.lang.System.loadLibrary(libgcj.so.81)
   at gnu.java.awt.peer.gtk.GtkToolkit.<clinit>(libgcj.so.81)
   at java.lang.Class.initializeClass(libgcj.so.81)
   at java.lang.Class.forName(libgcj.so.81)
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.81)
   ...8 more
Exception in thread "main" java.awt.AWTError: Cannot load AWT toolkit: gnu.java.awt.peer.gtk.GtkToolkit
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.81)
   at java.awt.GraphicsEnvironment.getLocalGraphicsEnvironment(libgcj.so.81)
   at java.awt.Window.<init>(libgcj.so.81)
   at java.awt.Frame.<init>(libgcj.so.81)
   at java.awt.Frame.<init>(libgcj.so.81)
   at javax.swing.SwingUtilities$OwnerFrame.<init>(libgcj.so.81)
   at javax.swing.SwingUtilities$OwnerFrame.<init>(libgcj.so.81)
   at javax.swing.SwingUtilities.getOwnerFrame(libgcj.so.81)
   at javax.swing.JOptionPane.<clinit>(libgcj.so.81)
   at java.lang.Class.initializeClass(libgcj.so.81)
   at free.jin.JinApplication.main(Unknown Source)
Caused by: java.lang.NoClassDefFoundError: gnu.java.awt.peer.gtk.GtkToolkit
   at java.lang.Class.initializeClass(libgcj.so.81)
   at java.lang.Class.forName(libgcj.so.81)
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.81)
   ...10 more

```

I can't tell if the problem is with the way I downloaded Jin, or the java installation I currently have.  Can someone point me in the right direction?

---

### Post by y-lee on 2008-06-15
You need suns version of java. Type the following code in the terminal to see if it is installed on your machine:

```
sudo update-alternatives --config java
```

If it is installed you should see it in the list, change your java version to it. if not open synaptic and search for java, to get Sun Java under Ubuntu 7.04 or later running on Intel or PowerPC platform, you should enable the Universe repository in Add/Remove programs, and install  the sun-java6-bin package. ( I think this will work at least, note I always compile sun's java from source code downloaded from Suns web site)

---

