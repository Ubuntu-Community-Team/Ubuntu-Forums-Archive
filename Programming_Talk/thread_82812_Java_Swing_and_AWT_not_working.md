---
title: "Java Swing and AWT not working"
date: 2005-10-27
forum: Programming Talk
---

### Post by tribopablo on 2005-10-27
Hi everyone!

Hope someone can help me out. I'm currently running Ubuntu 5.10 at home and tried setting up J2SDK to start writing some java.

I tested the installation with a simple " java HelloWorldApp ", and it worked fine. However, when attempting to run some GUI with " java HelloWorldSwing " which basically is just the file from the Java Swing tutorial, I get the following error:

Exception in thread "main" java.awt.AWTError: Cannot load AWT toolkit: gnu.java.awt.peer.gtk.GtkToolkit
   at java.awt.Toolkit.getDefaultToolkit() (/usr/lib/libgcj.so.6.0.0)
   at java.awt.EventQueue.invokeLater(java.lang.Runnable) (/usr/lib/libgcj.so.6.0.0)
   at javax.swing.SwingUtilities.invokeLater(java.lang.Runnable) (/usr/lib/libgcj.so.6.0.0)
   at HelloWorldSwing.main(java.lang.String[]) (Unknown Source)
   at gnu.java.lang.MainThread.call_main() (/usr/lib/libgcj.so.6.0.0)
   at gnu.java.lang.MainThread.run() (/usr/lib/libgcj.so.6.0.0)
Caused by: java.lang.ClassNotFoundException: gnu.java.awt.peer.gtk.GtkToolkit not found in gnu.gcj.runtime.SystemClassLoader{urls=[file:./,file:./], parent=gnu.gcj.runtime.ExtensionClassLoader{urls=[], parent=null}}
   at java.net.URLClassLoader.findClass(java.lang.String) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.ClassLoader.loadClass(java.lang.String, boolean) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.ClassLoader.loadClass(java.lang.String) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.Class.forName(java.lang.String, boolean, java.lang.ClassLoader) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.Class.forName(java.lang.String) (/usr/lib/libgcj.so.6.0.0)
   at java.awt.Toolkit.getDefaultToolkit() (/usr/lib/libgcj.so.6.0.0)
   ...5 more

I've been reading the current forums and articles from the web but still no luck. 

Thanks in advance for you help :)

---

### Post by mostwanted on 2005-10-27
Maybe it would help if you had the Java runtime instead of GCJ? I don't think GCJ is very favorable for GUI apps.

---

### Post by ngms27 on 2005-10-27
You need to run Suns Java as the default rather the the one supplied with Ubuntu.

If you put in java -version in a terminal it will tell you which java is being used first.

You can either uninstall the one shipped with Ubuntu else modify the PATH in your .bashrc file such as:

PATH=/home/ngms27/SunJava/bin:./:$PATH

i.e. put the path to the SunJava ahead in the pecking order.

HTH

JonnyT

---

### Post by tribopablo on 2005-10-28
Great! Thanks so much for both your replies. Let me give it a shot and see what happens. Get back to you guys soon. :)

---

### Post by tribopablo on 2005-10-29
It works! 

I just added the following code to $PATH

PATH=/usr/lib/j2sdk1.5-sun/bin:/$PATH

and the Swing is swingin! Thanks again guys :)

---

