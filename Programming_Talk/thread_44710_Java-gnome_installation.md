---
title: "Java-gnome installation"
date: 2005-06-27
forum: Programming Talk
---

### Post by thom_kbbc on 2005-06-27
Hello everybody,
I'm trying to use java-gnome,and I have some problems.

I've install : libgtk2-java, libgnome2-java, libglade2-java 
but I can't find : libgconf-java

When I try to lunch a small application, I've this error : ```
Exception in thread "main" java.lang.UnsatisfiedLinkError: no gtkjava2.4 in java.library.path
	at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1682)
	at java.lang.Runtime.loadLibrary0(Runtime.java:822)
	at java.lang.System.loadLibrary(System.java:992)
	at org.gnu.gtk.Gtk.<clinit>(Gtk.java:104)
	at HelloWorld.main(HelloWorld.java:13)
``` 
The problem as a solution, as said on 
[http://java-gnome.sourceforge.net/cgi-bin/bin/view/Main/UsingAMakefile](http://java-gnome.sourceforge.net/cgi-bin/bin/view/Main/UsingAMakefile)
but I cant find the libs that must been in this part of the code :```
LIBS=-lgtkjar2.4 -lgnomejar2.8
LIBPATH=/usr/lib
``` 

Tanks for your help

---

