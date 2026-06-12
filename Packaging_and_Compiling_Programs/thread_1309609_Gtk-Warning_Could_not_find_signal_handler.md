---
title: "Gtk-Warning: Could not find signal handler"
date: 2009-11-01
forum: Packaging and Compiling Programs
---

### Post by evilbios on 2009-11-01
Hello,
I'm hopefull to get an answer to this problem I've been having for the past few days. I'm trying to load a simple gui I made in Glade. The form loads property but in terminal I get the error:

 GtK-WARNING: Could not find signal handler 'on_window1_destroy'

Its the signal I have setup on the main window. 

This is my code:

#include <gtk/gtk.h>
#include "sqldbconnection.h"
#include <stdio.h>

G_MODULE_EXPORT void on_window1_destroy (GtkObject *object, gpointer user_data)
{
    gtk_main_quit();
}

int main (int argc, char *argv[])
{
    GtkBuilder      *builder;
    GtkWidget       *window;
    GError          *error = 0;

    gtk_init(&argc, &argv);

    builder = gtk_builder_new();
    if (!gtk_builder_add_from_file(builder, "Frost.glade", &error))
    {
        g_warning("%s", error->message);
        g_free(error);
        return(1);
    }
    window = GTK_WIDGET(gtk_builder_get_object(builder, "window1"));
    gtk_builder_connect_signals(builder, NULL);
    g_object_unref(G_OBJECT(builder));

    gtk_widget_show(window);
    gtk_main();

    return 0;
}

and the compile line I'm using is: 
`--export-dynamic` `pkg-config --cflags --libs gtk+-2.0 gmodule-export-2.0`

I'm using Code::Blocks IDE.
Any help is appreciated, Ive been searching forums for days with no answers. Thank you.

---

