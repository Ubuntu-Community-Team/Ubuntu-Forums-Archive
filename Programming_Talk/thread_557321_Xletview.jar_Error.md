---
title: "Xletview.jar Error"
date: 2007-09-22
forum: Programming Talk
---

### Post by Black Mage on 2007-09-22
I get this error when I try to run xletview.jar and I don't know if its an error in Java or an error in linux. When I use java -jar xletview.jar, it starts up but then says, 

```

********************************************************
XleTView, Copyright (C) 2003 - 2004 Martin Sveden 
XleTView comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to redistribute 
it under certain conditions; 
see license document for details.
********************************************************
java.lang.reflect.InvocationTargetException
   at java.lang.reflect.Constructor.newInstance(libgcj.so.70)
   at net.beiker.xletview.Main.main(Unknown Source)
Caused by: java.awt.AWTError: Cannot load AWT toolkit: gnu.java.awt.peer.gtk.GtkToolkit
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.70)
   at java.awt.Font.tk(libgcj.so.70)
   at java.awt.Font.getPeerFromToolkit(libgcj.so.70)
   at java.awt.Font.<init>(libgcj.so.70)
   at javax.swing.plaf.FontUIResource.<init>(libgcj.so.70)
   at javax.swing.plaf.metal.DefaultMetalTheme.<clinit>(libgcj.so.70)
   at java.lang.Class.initializeClass(libgcj.so.70)
   at java.lang.Class.initializeClass(libgcj.so.70)
   at net.sourceforge.mlf.metouia.MetouiaLookAndFeel.createDefaultTheme(MetouiaLookAndFeel.java:196)
   at javax.swing.plaf.metal.MetalLookAndFeel.<init>(libgcj.so.70)
   at net.sourceforge.mlf.metouia.MetouiaLookAndFeel.<init>(MetouiaLookAndFeel.java:79)
   at net.beiker.xletview.Startup.<init>(Unknown Source)
   at java.lang.reflect.Constructor.newInstance(libgcj.so.70)
   ...1 more
Caused by: java.lang.UnsatisfiedLinkError: libgtkpeer: libgtkpeer.so: cannot open shared object file: No such file or directory
   at java.lang.Runtime._load(libgcj.so.70)
   at java.lang.Runtime.loadLibrary(libgcj.so.70)
   at java.lang.System.loadLibrary(libgcj.so.70)
   at gnu.java.awt.peer.gtk.GtkToolkit.<clinit>(libgcj.so.70)
   at java.lang.Class.initializeClass(libgcj.so.70)
   at java.lang.Class.forName(libgcj.so.70)
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.70)
   ...13 more


```

Can anyone anyone help?
Xletview is availabe at [http://xletview.sourceforge.net/](http://xletview.sourceforge.net/)
If anyone knows of a way to comple Xlets, that would be very much appreciated.

---

### Post by luisromangz on 2007-09-22
It seems that you are using the gnu java implementation (as your log mentions libgcj.so in many places). You might try using Sun's JRE, you will be able to find how easily in the forums.

---

### Post by Black Mage on 2007-09-22
Thnx, a sudo update-java-alternatives -s java-1.6.0-sun did the trick.

---

