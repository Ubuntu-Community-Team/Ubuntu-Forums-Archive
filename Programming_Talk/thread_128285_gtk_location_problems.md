---
title: "gtk location problems"
date: 2006-02-11
forum: Programming Talk
---

### Post by rockyredhead on 2006-02-11
I have installed gtk 2.0 by synaptic but when I went to compile the first example program from the gtk website I got the following (I have ubuntu 5.10)

james@xenutha:~/pgmg/gtktutorial$ gcc base.c -o base `pkg-config --cflags --libs gtk+-2.0`
Package gtk+-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+-2.0' found
base.c:1:21: error: gtk/gtk.h: No such file or directory
base.c: In function ‘main’:
base.c:6: error: ‘GtkWidget’ undeclared (first use in this function)
base.c:6: error: (Each undeclared identifier is reported only once
base.c:6: error: for each function it appears in.)
base.c:6: error: ‘window’ undeclared (first use in this function)
base.c:10: error: ‘GTK_WINDOW_TOPLEVEL’ undeclared (first use in this function)

gtk-2.0 seems to be in /usr/lib/ but I am unsure of what to do to resolve this

any help appreciated

---

### Post by nagilum on 2006-02-12
Looks like you don't have the libgtk2.0-dev package installed, it contains the missing pkg-config file for gtk+-2.0 (/usr/lib/pkgconfig/gtk+-2.0.pc).

---

### Post by rockyredhead on 2006-02-16
Thanks to nagilum.

sudo apt-get install libgtk2.0-dev
fixed the problem. When running apt get it suggested some
docs which I also used apt get on.  There was a bonus in that the tutorial I was using online is now availble offline.  I have compiled the first code and also the hello window button example and ran them successfully.  Great!

---

