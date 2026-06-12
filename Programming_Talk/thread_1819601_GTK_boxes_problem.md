---
title: "GTK boxes problem"
date: 2011-08-06
forum: Programming Talk
---

### Post by nickos on 2011-08-06
Hello.


i am having the following problem.I make some boxes as an interface for GTK+ and i get the following error:



Gtk-WARNING **: Attempting to add a widget with type GtkVBox to a GtkWindow, but as a GtkBin subclass a GtkWindow can only contain one widget at a time; it already contains a widget of type GtkVBox



my code is 


```
static GtkWidget*
create_window(void) { 
    GtkWidget *window;
    GtkWidget *help;
    GtkWidget *about;
    GtkWidget *menubar;
    GtkWidget *helpmenu;
    GtkWidget *vbox;
    GtkWidget *vboxtwo;
    GtkWidget *button;

    window = gtk_window_new(GTK_WINDOW_TOPLEVEL);
    gtk_window_set_default_size(GTK_WINDOW(window), 150, 150);
    gtk_window_set_title(GTK_WINDOW(window), "test");


    help = gtk_menu_item_new_with_label("Help");
    about = gtk_menu_item_new_with_label("About");

    menubar = gtk_menu_bar_new();
    helpmenu = gtk_menu_new();

    vbox = gtk_vbox_new(FALSE, 0);
    gtk_container_add(GTK_CONTAINER(window), vbox);
    
    gtk_menu_shell_append(GTK_MENU_SHELL(menubar), help);
    gtk_menu_item_set_submenu(GTK_MENU_ITEM(help), helpmenu);
    gtk_menu_shell_append(GTK_MENU_SHELL(helpmenu), about);

    gtk_box_pack_start(GTK_BOX(vbox), menubar, FALSE, FALSE, 3);

    vboxtwo = gtk_vbox_new(FALSE, 0);
    button =  gtk_button_new_with_label("test");
    gtk_container_add(GTK_CONTAINER(window), vboxtwo);
    gtk_box_pack_start(GTK_BOX(vboxtwo), button, FALSE, FALSE, 0);


    return window;
}
```

---

### Post by gusnan on 2011-08-06
Create another VBox which you put in the window, and then put the VBoxes that you already have created into that VBox - that should solve it.

---

### Post by nickos on 2011-08-06
clever idea man,it works perfectly :)

Many thanks from the bottom of my heart :D

---

