---
title: "Drawing Fonts"
date: 2007-09-21
forum: Programming Talk
---

### Post by Earthwormzim on 2007-09-21
Hello, everyone...I'm just trying to get into GTK programming, and such, and I would like to know how to draw a font on a window.  

Here is the code for the simplest window in GTK
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

So, my question is...what do I add, and where do I add it?  From what I've been able to gather, I'll be using either Pango or Cairo (or both)...but, how exactly do I do that?  I'm confident that I'll be able to figure the rest out if I can get just one example.

---

### Post by Awalton on 2007-09-22
Curious as to what you mean by "draw a font"; do you wish to put some text in the window?
```

//add me after your gtk_init line
GtkWidget* mylabel = gtk_label_new("I has text");
gtk_widget_show(mylabel);

```
Or something like: 
[http://library.gnome.org/devel/pango/unstable/pango-Cairo-Rendering.html](http://library.gnome.org/devel/pango/unstable/pango-Cairo-Rendering.html) 

A bit more in the way of context or details would help.

---

