---
title: "Gnome /GTK menu bar creation"
date: 2009-12-12
forum: Programming Talk
---

### Post by bluedalmatian on 2009-12-12
Ive got a gnome app called mainwindow which is declared like this:

GtkWidget* mainwindow = gnome_app_new("Name","Name");

This window loads up fine and has been part of a working application for a few weeks.  Im now trying to add a menubar accross the top which will contain one menu (Help) with one item (About).  The code Im using is as follows:

GtkWidget* menubar;
GtkWidget* helpitem;
GtkWidget* helpmenu;
GtkWidget* aboutitem;


menubar=gtk_menu_bar_new();
helpitem=gtk_menu_item_new_with_label("Help");
aboutitem=gtk_menu_item_new_with_label("About");
helpmenu=gtk_menu_new();
		gtk_menu_item_set_submenu(GTK_MENU_ITEM(helpitem),helpmenu);
gtk_menu_shell_append(GTK_MENU_SHELL(helpmenu),aboutitem);
gtk_menu_shell_append(GTK_MENU_SHELL(menubar),helpitem);
		gnome_app_set_menus(GNOME_APP(mainwindow),GTK_MENU_BAR(menubar));
gtk_widget_show_all(menubar);

This compiles fine and the app runs but the menu bar doesnt show up.

Can anybody see what Ive done wrong as as far as I can see it matches the examples Ive looked at?

Thanks

---

### Post by PmDematagoda on 2009-12-12
Could you post the complete source code of the application? Also, please enclose the posted code in code tags so that it would be easier to read.

---

### Post by bluedalmatian on 2009-12-12
Ive fixed it.

strange thing it appears the two arguments to 

mainwindow = gnome_app_new("Name","Name");

MUST be the same. In my app they werent. It was only when I copied and pasted the relevent bits of code out into a tiny dummy app that I could post here that I realised.

so thanks for the suggestion :)

---

