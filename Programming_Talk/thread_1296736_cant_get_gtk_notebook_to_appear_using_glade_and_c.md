---
title: "cant get gtk notebook to appear using glade and c"
date: 2009-10-21
forum: Programming Talk
---

### Post by CRAY-4 on 2009-10-21
i am using glade with c and i cannot get a notebook widget to show

```
#include <gtk/gtk.h>
 
void 
on_window_destroy (GtkObject *object, gpointer user_data)
{
        gtk_main_quit();
}
 
int main (int argc, char *argv[])
{
        GtkBuilder              *builder;
        GtkWidget               *window;
        GtkWidget               *notebook1;
        
        gtk_init (&argc, &argv);
        
        builder = gtk_builder_new ();
        gtk_builder_add_from_file (builder, "gameshackgui.glade", NULL);
 
        window = GTK_WIDGET (gtk_builder_get_object (builder, "window"));
        notebook1 = GTK_CONTAINER (gtk_builder_get_object (builder, "notebook1"));
        gtk_builder_connect_signals (builder, NULL);          
        g_object_unref (G_OBJECT (builder));
        
	 gtk_container_add (GTK_CONTAINER (window), notebook1);
	gtk_widget_show_all (notebook1);

        gtk_widget_show_all (window); 	    
        gtk_main ();
        
        return 0;
}
```

---

### Post by CRAY-4 on 2009-10-21
bump

---

