---
title: "How to make a vertical toolbar in GTK?"
date: 2009-06-29
forum: Programming Talk
---

### Post by resander on 2009-06-29
I am new to GTK and have difficulties in placing a vertical toolbar. I want it to occupy about 20% of the window on the left-hand side, but each toolbar item spans most of the window horizontally and is centered with a lot of blank space on either side.
I want the width of vertical toolbar to be the width of an icon plus a few pixels of margin around it.  

Here is the problem as a minimal example:

```

   window = gtk_window_new ( GTK_WINDOW_TOPLEVEL ) ;
   gtk_window_set_title (GTK_WINDOW (window), "Vertical Toolbar" ) ;
   gtk_widget_set_size_request (window, 450,300 ) ; // works

   GtkWidget * box = gtk_hbox_new (TRUE, 0);

   GtkWidget * toolbar = gtk_toolbar_new ();
   gtk_widget_set_size_request (toolbar, 50,300 ) ; // doesn't work

   gtk_toolbar_set_orientation( (GtkToolbar *)toolbar ,
                                 GTK_ORIENTATION_VERTICAL ) ;
   gtk_toolbar_set_icon_size ( (GtkToolbar *)toolbar , GTK_ICON_SIZE_SMALL_TOOLBAR ) ;
   gtk_toolbar_set_style ( (GtkToolbar *)toolbar , GTK_TOOLBAR_ICONS ) ;

   GtkToolItem * gtkimg = gtk_tool_button_new_from_stock ( GTK_STOCK_CUT ) ;
   gtk_toolbar_insert( GTK_TOOLBAR(toolbar) , gtkimg , -1 ) ;

   gtkimg = gtk_tool_button_new_from_stock ( GTK_STOCK_COPY ) ;
   gtk_toolbar_insert( GTK_TOOLBAR(toolbar) , gtkimg , -1 ) ;

   gtkimg = gtk_tool_button_new_from_stock ( GTK_STOCK_PASTE ) ;
   gtk_toolbar_insert( GTK_TOOLBAR(toolbar) , gtkimg , -1 ) ;

   gtk_box_pack_start_defaults (GTK_BOX (box), toolbar ) ;

   gtk_container_add (GTK_CONTAINER (window), box);

   gtk_widget_show_all (window);
   gtk_main ();

```

It seems the size request gtk_widget_set_size_request (toolbar, 50,300 ) is ignored. My intent was to reserve 50 pixels for the the toolbar leaving 400 pixels for the neighbour(s) on the right-hand side, but it didn't work out like that. 

How to modify the code above so the vertical toolbar comes out looking right?

---

### Post by PmDematagoda on 2009-06-29
I managed to get what I think is what you want, using this code:-
```
#include <gtk/gtk.h> 

int main (int argc, char *argv[]){

  GtkWidget *window;

  gtk_init (&argc, &argv);

  window = gtk_window_new ( GTK_WINDOW_TOPLEVEL ) ;
   gtk_window_set_title (GTK_WINDOW (window), "Vertical Toolbar" ) ;
   gtk_widget_set_size_request (window, 450,300 ) ; // works

   GtkWidget * box = gtk_hbox_new (FALSE, 0);
   GtkWidget *n_box = gtk_hbox_new (TRUE, 0);

   GtkWidget * toolbar = gtk_toolbar_new ();
   gtk_widget_set_size_request (box, 30,30 ) ; // doesn't work

   gtk_toolbar_set_orientation( (GtkToolbar *)toolbar ,
                                 GTK_ORIENTATION_VERTICAL ) ;
   gtk_toolbar_set_icon_size ( (GtkToolbar *)toolbar , GTK_ICON_SIZE_SMALL_TOOLBAR ) ;
   gtk_toolbar_set_style ( (GtkToolbar *)toolbar , GTK_TOOLBAR_ICONS ) ;

   GtkToolItem * gtkimg = gtk_tool_button_new_from_stock ( GTK_STOCK_CUT ) ;
   gtk_toolbar_insert( GTK_TOOLBAR(toolbar) , gtkimg , -1 ) ;

   gtkimg = gtk_tool_button_new_from_stock ( GTK_STOCK_COPY ) ;
   gtk_toolbar_insert( GTK_TOOLBAR(toolbar) , gtkimg , -1 ) ;

   gtkimg = gtk_tool_button_new_from_stock ( GTK_STOCK_PASTE ) ;
   gtk_toolbar_insert( GTK_TOOLBAR(toolbar) , gtkimg , -1 ) ;

   gtk_box_pack_start (GTK_BOX (box), toolbar, FALSE,FALSE,4 ) ;
   gtk_box_pack_start_defaults (GTK_BOX (box), n_box ) ;

   gtk_container_add (GTK_CONTAINER (window), box);

   gtk_widget_show_all (window);
   gtk_main ();

return 0;

}
```
please note that gtk_box_pack_start_defaults() is deprecated and should not be used in the future.

---

### Post by resander on 2009-06-30
Many thanks!

I understand how it works now. Wouldn't have guessed it in a hundred years.

I am still thinking in terms of explicit positioning of graphical elements after more than 10 years of conditioning with the Windows GUI, HTML and SVG. Need to have my brain refurbished.

---

