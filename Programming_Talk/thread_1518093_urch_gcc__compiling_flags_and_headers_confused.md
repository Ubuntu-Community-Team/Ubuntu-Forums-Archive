---
title: "urch gcc / compiling flags and headers *confused*"
date: 2010-06-26
forum: Programming Talk
---

### Post by Søren on 2010-06-26
hi people ..
im attempting to compile the following code which writes cairo graphics onto a GTK window ...

(file is named hello.c)

```
#include <cairo.h> 
#include <gtk/gtk.h>
#include <cairo-deprecated.h>  
#include <cairo-svg.h> 
#include <cairo-xlib-xrender.h>
#include <cairo-features.h>  
#include <cairo-pdf.h> 
#include <cairo-version.h>
#include <cairo-ps.h>
#include <cairo-xlib.h>


static gboolean
on_expose_event(GtkWidget      *widget,
         GdkEventExpose *event,
         gpointer        data)
{
  cairo_t *cr;

  cr = gdk_cairo_create(widget->window);

  cairo_set_source_rgb(cr, 0, 0, 0);
  cairo_select_font_face(cr, "Sans", CAIRO_FONT_SLANT_NORMAL,
      CAIRO_FONT_WEIGHT_NORMAL);
  cairo_set_font_size(cr, 40.0);

  cairo_move_to(cr, 10.0, 50.0);
  cairo_show_text(cr, "Disziplin ist Macht.");

  cairo_destroy(cr);

  return FALSE;
}


int
main (int argc, char *argv[])
{

  GtkWidget *window;

  gtk_init(&argc, &argv);

  window = gtk_window_new(GTK_WINDOW_TOPLEVEL);

  g_signal_connect(window, "expose-event",
            G_CALLBACK (on_expose_event), NULL);
  g_signal_connect(window, "destroy",
            G_CALLBACK (gtk_main_quit), NULL);

  gtk_window_set_position(GTK_WINDOW(window), GTK_WIN_POS_CENTER);
  gtk_window_set_default_size(GTK_WINDOW(window), 400, 90); 
  gtk_widget_set_app_paintable(window, TRUE);

  gtk_widget_show_all(window);

  gtk_main();

  return 0;
}

```

i seem to writing the compile instruction wrong in the terminal ..
this is what im writing:

```
 cc -o hello $(pkg-config --cflags --libs cairo gtk+-2.0) hello.c
```

cant find any of the gtk stuff ... 

```
Package gtk was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk' found
hello.c:1:19: error: cairo.h: No such file or directory
hello.c:2:21: error: gtk/gtk.h: No such file or directory
hello.c:5: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘on_expose_event’
hello.c: In function ‘main’:
hello.c:31: error: ‘GtkWidget’ undeclared (first use in this function)
hello.c:31: error: (Each undeclared identifier is reported only once
hello.c:31: error: for each function it appears in.)
hello.c:31: error: ‘window’ undeclared (first use in this function)
hello.c:35: error: ‘GTK_WINDOW_TOPLEVEL’ undeclared (first use in this function)
hello.c:38: error: ‘on_expose_event’ undeclared (first use in this function)
hello.c:38: error: ‘NULL’ undeclared (first use in this function)
hello.c:40: error: ‘gtk_main_quit’ undeclared (first use in this function)
hello.c:42: error: ‘GTK_WIN_POS_CENTER’ undeclared (first use in this function)
hello.c:44: error: ‘TRUE’ undeclared (first use in this function)


```

is this the wrong instruction?

---

### Post by dwhitney67 on 2010-06-26
The instruction is (probably) correct.

Look at these pics... please make sure you have these packages installed on your system.

---

### Post by MadCow108 on 2010-06-26
> Package gtk was not found in the pkg-config search path.
this is indicates pkg-config is searching for gtk and not gtk+-2.0
maybe you should escape the "+":
pkg-config --cflags --libs cairo gtk\+-2.0

what shell are you using? as I cannot reproduce that problem with bash 4.1.5

---

### Post by gmargo on 2010-06-26
Here's your main clue:
> hello.c:1:19: error: cairo.h: No such file or directory
hello.c:2:21: error: gtk/gtk.h: No such file or directoryYou don't have the development packages installed.  Just install the **libgtk2.0-dev** package and it will pull in the **libcairo2-dev** and a bunch of other packages.  After that, your code compiles fine and works (tested on 10.04 Lucid.)

---

