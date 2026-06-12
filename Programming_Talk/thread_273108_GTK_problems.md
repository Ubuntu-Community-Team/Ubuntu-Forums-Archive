---
title: "GTK problems"
date: 2006-10-07
forum: Programming Talk
---

### Post by anti-net on 2006-10-07
I am quite new to programming and was going thru a C++ tutorial with GTK 2, I installed all the GTK stuff (Glib and Pango) but I can't find the GTK dev files. When I try and compile this: 
```
#include <gtk/gtk.h>

int main( int   argc,
          char *argv[] )
{
    GtkWidget *window;
    
    gtk_init (&argc, &argv);
    
    window = gtk_window_new (GTK_WINDOW_TOPLEVEL);
    gtk_widget_show  (window);
    
    gtk_main ();
    
    return 0;
}


```
the compile error I get is that it can't find "gtk.h" as I have some bits installed Im not sure what I should install to obtain gtk.h.

---

### Post by po0f on 2006-10-07
[Click](http://packages.ubuntu.com/dapper/libdevel/libgtk2.0-dev) or [click](http://packages.ubuntu.com/dapper/libdevel/libgtk1.2-dev).

---

