---
title: "GTK customize UI"
date: 2012-06-19
forum: Programming Talk
---

### Post by chuchi on 2012-06-19
Hi all!! I am developing an application using GTK. I need to know how to change the font size. But it is more important if you could tell me some tutorial about styles in GTK, because the GTK+ documentations does not say anything about it.   

 I am getting in too much trouble trying to customize my UI application.
 

 Thank you very much!!

---

### Post by satsujinka on 2012-06-19
Here's a good place to start: [http://developer.gnome.org/gtk3/3.4/GtkWidget.html#gtk-widget-override-font](http://developer.gnome.org/gtk3/3.4/GtkWidget.html#gtk-widget-override-font)

You'll need to create a pango font description, the function has a link to them. You should be able to create a new one and then set the various properties for it.

---

### Post by chuchi on 2012-06-19
Hi satsujinka! thanks for reply. I knew this reference. Do you know about some tutorial, examples?? 
The reference is good, but is quite difficult to understand and to put it on practice.

---

### Post by satsujinka on 2012-06-19
I don't have access to a compiler at the moment, but this should work:
```
#include <gtk/gtk.h>
/*modified version of the gtk example @ http://en.wikipedia.org/wiki/GTK%2B*/
int main (int argc, char *argv[])
{
    GtkWidget *window;
    GtkWidget *label;
    PangoFontDescription *font;
 
    gtk_init(&argc, &argv);
    window = gtk_window_new(GTK_WINDOW_TOPLEVEL);
    gtk_window_set_title(GTK_WINDOW(window), "Hello, world!");
    g_signal_connect(window, "destroy", G_CALLBACK(gtk_main_quit), NULL);
    label = gtk_label_new("Hello, world!");
    
    /* replace the string below with a string matching your desired font */
    font = pango_font_description_from_string("Monospace Regular 12");
    
    /*now override your chosen widget's font, here a label is used as an example*/
    gtk_widget_override_font(label, font);
    
    gtk_container_add(GTK_CONTAINER(window), label);
    gtk_widget_show_all(window);
    gtk_main();
    pango_font_description_free(font);
    return 0;
}
```
UPDATE:
This tutorial seems to have some similar information:[http://zetcode.com/tutorials/gtktutorial/gtkdialogs/](http://zetcode.com/tutorials/gtktutorial/gtkdialogs/)

---

### Post by alexfish on 2012-06-19
don't know if this will help

if have
```
#include <gtk/gtk.h>
```and problems compiling

can try compiling like this "example.c"  using  gtk3 .

```
gcc -Wall -g `pkg-config --cflags --libs gtk+-3.0` -o example example.c
```this is what some times helps in a .c file

```
/*modified version of the gtk example @ http://en.wikipedia.org/wiki/GTK%2B*/
/* gcc -Wall -g `pkg-config --cflags --libs gtk+-3.0` -o example example.c */ 
#include <gtk/gtk.h>
```

---

