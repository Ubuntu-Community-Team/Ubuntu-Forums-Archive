---
title: "Couple GTK Questions"
date: 2011-09-26
forum: Programming Talk
---

### Post by nickos on 2011-09-26
I got some gtk questions,some links for the functions are more than enough instead of an example.

1)How can i make a toolbar draggable?(libreoffice has that as well as other programs)
2)How can i make the width of a notebook tab bigger and place the text at the left of it with some gap on the right if the text is small
3)On the menu, eg(File), how can i make it look like (_File)? that whiteline under the first letter of a menu item thing.
4)How can i make two text entries draggable?(eg they can be dragged horizontally to change their sizes


thanks!

---

### Post by SledgeHammer_999 on 2011-09-27
2) Create a gtk_label with appropriate text orientation and space and then embed in the tab in place of the default one with [gtk_notebook_set_tab_label()](http://developer.gnome.org/gtk/stable/GtkNotebook.html#gtk-notebook-set-tab-label)

3)Are you constructing the menus with gtk_uimanager(and an xml def) or totally manually from gtk_menubar/gtk_menu/gtk_gtkmenuitem? I'll describe for the second one and similarly you can do it in the xml definition too. Use mnemonics [gtk_menu_item_new_with_mnemonic()](http://developer.gnome.org/gtk/stable/GtkMenuItem.html#gtk-menu-item-new-with-mnemonic). Furthermore, some standard Menuitems are called "stock items" and have pre-associated mnemonics/icons/translations with them. It is recommended to use the stock items wherever possible instead of managing them manually. Eg for the "open" action this is the stock item [http://developer.gnome.org/gtk/stable/gtk-Stock-Items.html#GTK-STOCK-OPEN:CAPS](http://developer.gnome.org/gtk/stable/gtk-Stock-Items.html#GTK-STOCK-OPEN:CAPS)

---

### Post by nickos on 2011-09-27
> **SledgeHammer_999 said:**
> 2) Create a gtk_label with appropriate text orientation and space and then embed in the tab in place of the default one with [gtk_notebook_set_tab_label()]("http://developer.gnome.org/gtk/stable/GtkNotebook.html#gtk-notebook-set-tab-label")

3)Are you constructing the menus with gtk_uimanager(and an xml def) or totally manually from gtk_menubar/gtk_menu/gtk_gtkmenuitem? I'll describe for the second one and similarly you can do it in the xml definition too. Use mnemonics [gtk_menu_item_new_with_mnemonic()]("http://developer.gnome.org/gtk/stable/GtkMenuItem.html#gtk-menu-item-new-with-mnemonic"). Furthermore, some standard Menuitems are called "stock items" and have pre-associated mnemonics/icons/translations with them. It is recommended to use the stock items wherever possible instead of managing them manually. Eg for the "open" action this is the stock item [http://developer.gnome.org/gtk/stable/gtk-Stock-Items.html#GTK-STOCK-OPEN:CAPS](http://developer.gnome.org/gtk/stable/gtk-Stock-Items.html#GTK-STOCK-OPEN:CAPS)

Thanks for the answer :)

How can i modify the text orientation?

Yes i am using menu,menuitem etc.

---

### Post by nickos on 2011-09-27
alright,so i stil lhave a problem with the menu mnemonics :

```

#include <gtk/gtk.h> #include <gdk/gdkkeysyms.h>   int main( int argc, char *argv[]) {    GtkWidget *window;   GtkWidget *vbox;    GtkWidget *menubar;   GtkWidget *filemenu;   GtkWidget *file;   GtkWidget *new;   GtkWidget *open;   GtkWidget *quit;    GtkWidget *sep;    GtkAccelGroup *accel_group = NULL;    gtk_init(&argc, &argv);    window = gtk_window_new(GTK_WINDOW_TOPLEVEL);   gtk_window_set_position(GTK_WINDOW(window), GTK_WIN_POS_CENTER);   gtk_window_set_default_size(GTK_WINDOW(window), 250, 200);   gtk_window_set_title(GTK_WINDOW(window), "menu");    vbox = gtk_vbox_new(FALSE, 0);   gtk_container_add(GTK_CONTAINER(window), vbox);    menubar = gtk_menu_bar_new();   filemenu = gtk_menu_new();    accel_group = gtk_accel_group_new();   gtk_window_add_accel_group(GTK_WINDOW(window), accel_group);    file = gtk_menu_item_new_with_mnemonic("_File");   new = gtk_image_menu_item_new_from_stock(GTK_STOCK_NEW, NULL);   open = gtk_image_menu_item_new_from_stock(GTK_STOCK_OPEN, NULL);   sep = gtk_separator_menu_item_new();   quit = gtk_image_menu_item_new_from_stock(GTK_STOCK_QUIT, accel_group);    gtk_widget_add_accelerator(quit, "activate", accel_group,        GDK_q, GDK_CONTROL_MASK, GTK_ACCEL_VISIBLE);      gtk_menu_item_set_submenu(GTK_MENU_ITEM(file), filemenu);   gtk_menu_shell_append(GTK_MENU_SHELL(filemenu), new);   gtk_menu_shell_append(GTK_MENU_SHELL(filemenu), open);   gtk_menu_shell_append(GTK_MENU_SHELL(filemenu), sep);   gtk_menu_shell_append(GTK_MENU_SHELL(filemenu), quit);   gtk_menu_shell_append(GTK_MENU_SHELL(menubar), file);   gtk_box_pack_start(GTK_BOX(vbox), menubar, FALSE, FALSE, 3);    g_signal_connect_swapped(G_OBJECT(window), "destroy",       G_CALLBACK(gtk_main_quit), NULL);    g_signal_connect(G_OBJECT(quit), "activate",       G_CALLBACK(gtk_main_quit), NULL);    gtk_widget_show_all(window);    gtk_main();    return 0; } 
```

that is a simple code i found at zetcode.com and it wont display any mnemonics though :(

---

### Post by crdlb on 2011-09-27
By default, the mnemonics are only shown when you press Alt.

---

### Post by nickos on 2011-09-28
doest show anything even if i press alt..............

---

