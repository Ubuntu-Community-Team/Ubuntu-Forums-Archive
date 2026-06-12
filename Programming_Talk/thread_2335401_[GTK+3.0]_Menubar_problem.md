---
title: "[GTK+3.0] Menubar problem"
date: 2016-08-28
forum: Programming Talk
---

### Post by mefimess on 2016-08-28
Hello friends ! I have a problem with menubar in GTK3.0. I would like to create GUI application with drop down menu but ...

I've installed Ubuntu 14.04 and later 16.04 on VirtualBox Machine. I've created file test.c with example of menubar in GTK. After compilation (it runs without errors) the window is opened but without menu ...

```
#include <gtk/gtk.h>

static void open_activated(GtkWidget *f)
{
    g_print("File -> Open activated.\n");
}

static void quit_activated(GtkWidget *f)
{
    g_print("File -> Quit activated...bye.\n");
    gtk_main_quit();
}

static void another_activated(GtkWidget *widget, gpointer data)
{
    g_print("%s clicked.\n", (gchar*)data);
}

int main( int argc, char *argv[])
{
    GtkWidget *window;
    GtkWidget *box;
    GtkWidget *menubar;
    GtkWidget *filemenu;
    GtkWidget *file;
    GtkWidget *open;
    GtkWidget *quit;

    GtkWidget *anothermenu;
    GtkWidget *another;
    GtkWidget *anothermenuitem;

    gtk_init(&argc, &argv);
    window = gtk_window_new(GTK_WINDOW_TOPLEVEL);
    //gtk_window_set_position(GTK_WINDOW(window), GTK_WIN_POS_CENTER);
    gtk_window_set_default_size(GTK_WINDOW(window), 400, 250);
    gtk_window_set_title(GTK_WINDOW(window), "Linux-buddy.blogspot.com");

    menubar = gtk_menu_bar_new();

    filemenu = gtk_menu_new();
    file = gtk_menu_item_new_with_label("File");
    open = gtk_menu_item_new_with_label("Open");
    quit = gtk_menu_item_new_with_label("Quit");
    gtk_menu_item_set_submenu(GTK_MENU_ITEM(file), filemenu);
    gtk_menu_shell_append(GTK_MENU_SHELL(filemenu), open);
    gtk_menu_shell_append(GTK_MENU_SHELL(filemenu), quit);
    gtk_menu_shell_append(GTK_MENU_SHELL(menubar), file);
    //Connects GCallback function open_activated to "activate" signal for "open" menu item
    g_signal_connect(G_OBJECT(open), "activate", G_CALLBACK(open_activated), NULL);
    //Connects GCallback function quit_activated to "activate" signal for "quit" menu item
    g_signal_connect(G_OBJECT(quit), "activate", G_CALLBACK(quit_activated), NULL);

    anothermenu = gtk_menu_new();
    another = gtk_menu_item_new_with_label("Another");
    anothermenuitem = gtk_menu_item_new_with_label("Another Menu Item");
    gtk_menu_item_set_submenu(GTK_MENU_ITEM(another), anothermenu);
    gtk_menu_shell_append(GTK_MENU_SHELL(anothermenu), anothermenuitem);
    gtk_menu_shell_append(GTK_MENU_SHELL(menubar), another);
    //Connects GCallback function another_activated to "activate" signal for another
    g_signal_connect(G_OBJECT(anothermenuitem), "activate", G_CALLBACK(another_activated), "anothermenuitem");
    g_signal_connect(G_OBJECT(another), "activate", G_CALLBACK(another_activated), "another");

    box = gtk_box_new(GTK_ORIENTATION_VERTICAL, 5);
    gtk_box_pack_start(GTK_BOX(box), menubar, FALSE, FALSE, 3);
    gtk_container_add(GTK_CONTAINER(window), box);

    //Connects GCallback function gtk_main_quit to "destroy" signal for "window"
    g_signal_connect(G_OBJECT(window), "destroy", G_CALLBACK(gtk_main_quit), NULL);

    gtk_widget_show_all(window);
    gtk_main();

    return 0;
}
```

The compilation command is :

```
 gcc test.c -export-dynamic `pkg-config --cflags --libs gtk+-3.0` -o test 
```

Moreover I installed packages

```
sudo apt-get install libgtk-3-dev
```.

The example is compiled without errors but menu is still not working and I dont know why ...

Greetings !

---

### Post by spjackson on 2016-08-30
Your example works for me,  complete with menu. Are you by any chance running this on Unity and is the menu at the top of the display rather than inside the window?

---

