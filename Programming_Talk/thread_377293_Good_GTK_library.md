---
title: "Good GTK library?"
date: 2007-03-05
forum: Programming Talk
---

### Post by CrazyTn on 2007-03-05
Hi, I am new to GTK programming. Trying to program a tetris game atm. 

Currently I am using this website as a reference
[http://developer.gnome.org/doc/API/2.0/gtk/ch01.html](http://developer.gnome.org/doc/API/2.0/gtk/ch01.html)

It is a lil hard to find what I need with it.

Trying to find something to draw on the frame or maybe move widgets around.

---

### Post by lnostdal on 2007-03-06
GDK contains drawing-functions: [http://developer.gnome.org/doc/API/2.0/gdk/](http://developer.gnome.org/doc/API/2.0/gdk/)

..but a very good (better than GDK) library for drawing stuff is Cairo: [http://cairographics.org/](http://cairographics.org/) .. it produces beautiful results (see the examples .. for instance: [http://macslow.thepimp.net/?page_id=23](http://macslow.thepimp.net/?page_id=23) )

GDK contains the functions needed to combine GDK/GTK and Cairo: [http://developer.gnome.org/doc/API/2.0/gdk/gdk-Cairo-Interaction.html](http://developer.gnome.org/doc/API/2.0/gdk/gdk-Cairo-Interaction.html)

..and here is a complete example:
[http://nostdal.org/~lars/programming/c/cairo.c](http://nostdal.org/~lars/programming/c/cairo.c)

---

