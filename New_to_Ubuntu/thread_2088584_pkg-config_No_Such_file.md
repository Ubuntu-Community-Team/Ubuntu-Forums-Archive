---
title: "pkg-config No Such file"
date: 2012-11-27
forum: New to Ubuntu
---

### Post by sawjam on 2012-11-27
Hi 

Ubuntu 64 bit
Kernel 3.2.0-33-generic



I've decided to dive into trying some programing, first off using eclipse, but could not compile my simple file using gtkmm-2.4 to draw a window.

I dropped to the terminal and tried

```
g++ gtkmm.cpp -o main 'pkg-config --libs --cflags gtkmm-2.4'
```
and get 
```
g++: error: pkg-config --libs --cflags gtkmm-2.4: No such file or directory
```

so after some digging did this:
```
pkg-config --list-all >pkglist.txt
```
and gtkmm-2.4 is in the list????

So tried this:
```
pkg-config --libs --cflags gtkmm-2.4-pthread -
```

and got this:
```
I/usr/include/gtkmm-2.4 -I/usr/lib/x86_64-linux-gnu/gtkmm-2.4/include -I/usr/include/atkmm-1.6 -I/usr/include/giomm-2.4 -I/usr/lib/x86_64-linux-gnu/giomm-2.4/include -I/usr/include/pangomm-1.4 -I/usr/lib/x86_64-linux-gnu/pangomm-1.4/include -I/usr/include/gtk-2.0 -I/usr/include/gtk-unix-print-2.0 -I/usr/include/gdkmm-2.4 -I/usr/lib/x86_64-linux-gnu/gdkmm-2.4/include -I/usr/include/atk-1.0 -I/usr/include/glibmm-2.4 -I/usr/lib/x86_64-linux-gnu/glibmm-2.4/include -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include -I/usr/include/sigc++-2.0 -I/usr/lib/x86_64-linux-gnu/sigc++-2.0/include -I/usr/include/cairomm-1.0 -I/usr/lib/x86_64-linux-gnu/cairomm-1.0/include -I/usr/include/pango-1.0 -I/usr/include/cairo -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/lib/x86_64-linux-gnu/gtk-2.0/include -I/usr/include/gdk-pixbuf-2.0 -I/usr/include/gio-unix-2.0/  -lgtkmm-2.4 -latkmm-1.6 -lgdkmm-2.4 -lgiomm-2.4 -lpangomm-1.4 -lgtk-x11-2.0 -lglibmm-2.4 -lcairomm-1.0 -lsigc-2.0 -lgdk-x11-2.0 -latk-1.0 -lgio-2.0 -lpangoft2-1.0 -lpangocairo-1.0 -lgdk_pixbuf-2.0 -lcairo -lpango-1.0 -lfreetype -lfontconfig -lgobject-2.0 -lglib-2.0  
```

Confused everything seems to be there but it can't find it:confused:

Any help appeciated

---

### Post by sawjam on 2012-11-27
Posted too soon,

used output of:

```
pkg-config --libs --cflags gtkmm-2.4
```

```
g++ gtkmm.cpp -o main -pthread -I/usr/include/gtkmm-2.4 -I/usr/lib/x86_64-linux-gnu/gtkmm-2.4/include -I/usr/include/atkmm-1.6 -I/usr/include/giomm-2.4 -I/usr/lib/x86_64-linux-gnu/giomm-2.4/include -I/usr/include/pangomm-1.4 -I/usr/lib/x86_64-linux-gnu/pangomm-1.4/include -I/usr/include/gtk-2.0 -I/usr/include/gtk-unix-print-2.0 -I/usr/include/gdkmm-2.4 -I/usr/lib/x86_64-linux-gnu/gdkmm-2.4/include -I/usr/include/atk-1.0 -I/usr/include/glibmm-2.4 -I/usr/lib/x86_64-linux-gnu/glibmm-2.4/include -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include -I/usr/include/sigc++-2.0 -I/usr/lib/x86_64-linux-gnu/sigc++-2.0/include -I/usr/include/cairomm-1.0 -I/usr/lib/x86_64-linux-gnu/cairomm-1.0/include -I/usr/include/pango-1.0 -I/usr/include/cairo -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/lib/x86_64-linux-gnu/gtk-2.0/include -I/usr/include/gdk-pixbuf-2.0 -I/usr/include/gio-unix-2.0/  -lgtkmm-2.4 -latkmm-1.6 -lgdkmm-2.4 -lgiomm-2.4 -lpangomm-1.4 -lgtk-x11-2.0 -lglibmm-2.4 -lcairomm-1.0 -lsigc-2.0 -lgdk-x11-2.0 -latk-1.0 -lgio-2.0 -lpangoft2-1.0 -lpangocairo-1.0 -lgdk_pixbuf-2.0 -lcairo -lpango-1.0 -lfreetype -lfontconfig -lgobject-2.0 -lglib-2.0  

```

and it worked!!!!

Long story short ' (Next to enter key) is the wrong one, needed to use `(Next to 1 key)

---

