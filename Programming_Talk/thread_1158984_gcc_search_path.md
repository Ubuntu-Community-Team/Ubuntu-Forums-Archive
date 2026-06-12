---
title: "gcc search path"
date: 2009-05-14
forum: Programming Talk
---

### Post by adit on 2009-05-14
When I tried to compile an example GTK program I get the following error:
gtk.h: No such file or directory
I have installed libgtk2.0-dev package.  gtk.h is in /usr/include/gtk-2.0/gtk.
How can I make gcc to search /usr/include and **all of its subdirectories?**

---

### Post by dwhitney67 on 2009-05-14
When compiling with gcc, specify the location of the GTK header files using the -I (eye) option.
```

gcc -I/usr/include/gtk-2.0 ...

```

---

### Post by adit on 2009-05-14
I tried your code.  Now gcc found out gtk.h, but it couldn't find a lot of other header files.  (See my attachments).  Even if I ask gcc to look into /usr/include/gtk-2.0/gtk by typing the following code
```
~$ gcc -I /usr/include/gtk-2.0/gtk helloworld.c
```
it looks only into /usr/include/gtk-2.0/gtk subdirectory. Many header files are in other subdirectories under /usr/include/gtk-2.0. GCC does not look into any other subdirectories.  The **libgtk2.0-dev** package installation creates header files in various subdirectories under /usr/include/gtk-2.0
```
~$ ls /usr/include/gtk-2.0
[COLOR="Blue"]gdk
gdk-pixbuf
gdk-pixbuf-xlib
gtk[/COLOR]
```
All the header files are in the above four subdirectories.

So I gave the parent directory /usr/include/gtk-2.0 as an option.  What GCC does is, it sees only the names of these 4 subdirectories.  It does not look into the contents of these subdirectories.  How can I make GCC to look into all subdirectories under /usr/include/gtk-2.0?

---

### Post by dwhitney67 on 2009-05-14
Refer to the GTK documentation with regards to including their header files.  On my system, I only have four subdirs below /usr/include/gtk-2.0.  These are:
[LIST]
[*]gdk
[*]gdk-pixbuf
[*]gdk-pixbuf-xlib
[*]gtk
[/LIST]

Your source code (which I have not had the opportunity to review), should preface the GTK header  file with one of these paths.  For example, <gtk/gtk.h>.

If you require a header in one of the other directories, then follow the same style, and augment your gcc header files include path list as needed.

You may want to consider developing a Makefile at some point.

---

