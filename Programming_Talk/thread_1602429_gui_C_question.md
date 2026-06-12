---
title: "gui C question"
date: 2010-10-21
forum: Programming Talk
---

### Post by pythonsyntax on 2010-10-21
What would be good GUI tool in C to use for ubuntu?

---

### Post by Simian Man on 2010-10-21
If you're set on using C, GTK+ is your best option.  I'd really not recommend C for GUI applications though.

---

### Post by pythonsyntax on 2010-10-21
is there a guide how to use it?

---

### Post by Simian Man on 2010-10-21
> **pythonsyntax said:**
> is there a guide how to use it?

[Here ya go.]("http://library.gnome.org/devel/gtk-tutorial/stable/")

---

### Post by pythonsyntax on 2010-10-21
What tool kit do i need to download?I do got gtk+ install but i don't see the header i need.

---

### Post by worseisworser on 2010-10-21
```

sudo aptitude search libgtk | grep dev
...
sudo aptitude install libgtk2.0-dev

```

use google

---

### Post by pythonsyntax on 2010-10-21
that what i have installed but can't find the headers.

---

### Post by worseisworser on 2010-10-21
[http://library.gnome.org/devel/gtk-tutorial/stable/x111.html](http://library.gnome.org/devel/gtk-tutorial/stable/x111.html)

..what?


```

lnostdal@blackbox:~/programming/sbcl-git$ pkg-config --cflags gtk+-2.0
-pthread -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/gdk-pixbuf-2.0 -I/usr/include/pango-1.0 -I/usr/include/gio-unix-2.0/ -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12  
lnostdal@blackbox:~/programming/sbcl-git$ pkg-config --cflags gtk+-2.0
-pthread -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/gdk-pixbuf-2.0 -I/usr/include/pango-1.0 -I/usr/include/gio-unix-2.0/ -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12  
lnostdal@blackbox:~/programming/sbcl-git$ pkg-config --cflags gtk+-2.0
-pthread -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/gdk-pixbuf-2.0 -I/usr/include/pango-1.0 -I/usr/include/gio-unix-2.0/ -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12  
lnostdal@blackbox:~/programming/sbcl-git$ pkg-config --cflags gtk+-2.0
-pthread -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/gdk-pixbuf-2.0 -I/usr/include/pango-1.0 -I/usr/include/gio-unix-2.0/ -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12  
lnostdal@blackbox:~/programming/sbcl-git$ pkg-config --cflags gtk+-2.0
-pthread -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/gdk-pixbuf-2.0 -I/usr/include/pango-1.0 -I/usr/include/gio-unix-2.0/ -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12  
lnostdal@blackbox:~/programming/sbcl-git$ pkg-config --cflags gtk+-2.0
-pthread -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/gdk-pixbuf-2.0 -I/usr/include/pango-1.0 -I/usr/include/gio-unix-2.0/ -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12  
lnostdal@blackbox:~/programming/sbcl-git$ pkg-config --cflags gtk+-2.0
-pthread -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/gdk-pixbuf-2.0 -I/usr/include/pango-1.0 -I/usr/include/gio-unix-2.0/ -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12  
lnostdal@blackbox:~/programming/sbcl-git$ pkg-config --cflags gtk+-2.0
-pthread -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/gdk-pixbuf-2.0 -I/usr/include/pango-1.0 -I/usr/include/gio-unix-2.0/ -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12  
lnostdal@blackbox:~/programming/sbcl-git$ pkg-config --cflags gtk+-2.0
-pthread -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/gdk-pixbuf-2.0 -I/usr/include/pango-1.0 -I/usr/include/gio-unix-2.0/ -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12  
lnostdal@blackbox:~/programming/sbcl-git$ 
..
..

```

---

### Post by pythonsyntax on 2010-10-21
i said i can't find the headers when i try to compile in gtk+

---

### Post by Barrucadu on 2010-10-22
How are you compiling?

---

### Post by MadCow108 on 2010-10-22
don't write gui's in C, especially when you are unfamiliar with the C compilation process.
Your just making everything more complicated for no gain.

use a higher level language like python, perl, ruby or even c++ for the gui and the performance critical backend can still be C.

For your problem read the links provided by others here and the forum stickies...

---

### Post by pythonsyntax on 2010-10-22
gcc -Wall -g helloworld.c -o helloworld `pkg-config --cflags gtk+-2.0` \
    `pkg-config --libs gtk+-2.0`




and how do you run the file after you compile it?

---

### Post by Simian Man on 2010-10-22
> **madcow108 said:**
> don't write gui's in c, especially when you are unfamiliar with the c compilation process.
Your just making everything more complicated for no gain.

+1

---

