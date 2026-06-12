---
title: "[C] Pointers: incompatible type?"
date: 2008-05-06
forum: Programming Talk
---

### Post by microfi on 2008-05-06
Hi! I'm new to C and I'm developing a simple application using Cairo. I followed the tutorial on [http://cairographics.org/tutorial/](http://cairographics.org/tutorial/) and I'm stuck in this piece of code:
```
cairo_surface_t *surface;
cairo_t *cr;
surface = cairo_image_surface_create (CAIRO_FORMAT_ARGB32, 120, 120);
cr = cairo_create (surface);
```
The command I use to compile is:
```
gcc `pkg-config --cflags --libs gtk+-2.0 libglade-2.0` foo.c -o foo
```
But, after running it, I get the following log:
```
foo.c: In function ‘func_cairo_draw’:
foo.c:34: warning: passing argument 1 of ‘gdk_cairo_create’ from incompatible pointer type
Compilation finished successfully.
```
As the compilation seems to have worked successfully, I run the program and, after crashing, I get this:
```
(foo:7320): Gdk-CRITICAL **: gdk_cairo_create: assertion `GDK_IS_DRAWABLE (drawable)' failed
Segmentation fault

```

After changing a window title with **gtk_window_set_title** I get the same warning (passing argument 1 of ‘gtk_window_set_title’ from incompatible pointer type). The odd thing is that I can show the same window by **gtk_widget_show** with no warnings or errors. The title of the window changes normally at runtime, though.
The window pointer is initialized with:
```
GtkWidget *wndmain;
wndmain = glade_xml_get_widget (xml, "wndmain");
```

Any suggestions of what it can be?
Thanks, Filipe.

---

### Post by microfi on 2008-05-06
I got it solved!..
You can call me dumb... I was using **gtk_cairo_create** instead of **cairo_create**! Everything went OK now!
And the window issue is due to the fact that it's declared as GtkWidget, not GtkWindow.
Thanks.

---

