---
title: "java-gnome dont work"
date: 2005-05-18
forum: Programming Talk
---

### Post by nmarmol on 2005-05-18
I'm installing java-gnome 2.10. But I've an error.
The program compile fine.  
   javac First.java
But when i run the program "java First" I've the following error

Exception in thread "main" java.lang.UnsatisfiedLinkError: no gtkjni-2.6 in java.library.path
        at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1682)
        at java.lang.Runtime.loadLibrary0(Runtime.java:822)
        at java.lang.System.loadLibrary(System.java:992)
        at org.gnu.gtk.Gtk.<clinit>(Gtk.java:187)
        at First.main(First.java:22)

Can anyone help me?

Regards
Nelson

---

### Post by GoLo on 2005-11-04
take a look here:
[http://java-gnome.sourceforge.net/cgi-bin/bin/view/Main/EclipseDevelopment]("http://java-gnome.sourceforge.net/cgi-bin/bin/view/Main/EclipseDevelopment")

---

