---
title: "Xgraphics?"
date: 2007-01-31
forum: Programming Talk
---

### Post by rich.bradshaw on 2007-01-31
[http://theorie.physik.uni-wuerzburg.de/Xgraphics/](http://theorie.physik.uni-wuerzburg.de/Xgraphics/)

Is the link. These Xgraphics libraries work fine on a Unix machine, and apparently in Suse too, but not on Ubuntu. The error thrown when compiling is from Xgraphics.h, at the point where:

#include <X11/Xlib.h>
#include <X11/Xutil.h>

These files aren't on my PC, but are on the Unix machine. Does anyone know how to get this working?

Thanks - any suggestions are welcome!

Rich

---

### Post by lnostdal on 2007-01-31
let's see now ..

```
aptitude search xlib
```

..xlibs-dev shows up; have you tried installing that?

```

lars@ibmr52:~/programming/c$ locate Xlib.h
/usr/include/X11/Xlib.h

```

edit:
the stuff you're working with seems very old/deprecated; you do know things like gtk+ and cairo exists? just a note

---

### Post by rich.bradshaw on 2007-01-31
Well, at university I have written a lot of code using it, so that's why i'm interested. That did get past the first problem, but didn't fix it totally. Think I will continue to produce version without graphics for home/processor intensive version, and pretty graphical version to use at Uni to see what's going on in my simulation.

How easy is it to use GTK etc? All I want to do is draw dots,circles and lines on the screen to represent movements of ants.

---

### Post by lnostdal on 2007-01-31
```

/*
  gcc -Wall -g `pkg-config --cflags --libs gtk+-2.0` `pkg-config --cflags --libs cairo` cairo2.c -o cairo2
*/

#include <stdio.h>
#include <gtk/gtk.h>
#include <cairo/cairo.h>


void hello(GtkWidget* drawable, gpointer data)
{
  // Width and height so you can scale the drawing as the user resizes the window.
  printf("width: %d, height: %d\n", drawable->allocation.width, drawable->allocation.height);
  cairo_t* cr = gdk_cairo_create(drawable->window); // drawing context
  cairo_arc(cr, 50, 50, 45, 0, 2);
  cairo_stroke(cr);    
  cairo_destroy(cr); // done with drawing context
}


void destroy(GtkWidget* widget, gpointer data)
{
  gtk_main_quit ();
}



int main(int argc, char** argv)
{
  gtk_init(&argc, &argv);
  
  GtkWidget* window = gtk_window_new(GTK_WINDOW_TOPLEVEL);
  GtkWidget* drawable = gtk_drawing_area_new();
  gtk_container_add((GtkContainer*)window, drawable);
  g_signal_connect(drawable, "expose-event", G_CALLBACK(hello), NULL);
  g_signal_connect(window, "delete_event", G_CALLBACK(destroy), NULL);
  gtk_widget_show_all(window);
  
  gtk_main();
  return 0;
}

```

(you need the *-dev libraries for gtk and cairo for this to compile; just search using aptitude like i did above)

cairo is easy to use and has good documentation: [http://www.cairographics.org/manual/](http://www.cairographics.org/manual/) .. edit: oh, and it produces beautiful results :)

---

