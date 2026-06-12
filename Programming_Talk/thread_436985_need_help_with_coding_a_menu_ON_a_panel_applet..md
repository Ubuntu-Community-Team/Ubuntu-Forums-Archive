---
title: "need help with coding a menu ON a panel applet."
date: 2007-05-08
forum: Programming Talk
---

### Post by SkiesOfAzel on 2007-05-08
Hi and thx in advance. I am relatively new to linux and i wanted to learn some gtk so i tried to  modify an applet to include a menubar as an exercise of sorts. I build my menu add an item, add the menu as a submenu to another item , add the item to a menubar and add the menubar to my box. The result is that the menu is displayed not on but under the panel .
Here is the relevant code :
```
GtkWidget *menu_bar;
  GtkWidget *file_menu;
  GtkWidget *file_item;
  GtkWidget *open_item;
  file_menu = gtk_menu_new ();
  menu_bar = gtk_menu_bar_new ();
  open_item = gtk_menu_item_new_with_label ("Open");
  file_item = gtk_menu_item_new_with_label ("File");
 
  gtk_signal_connect_object (GTK_OBJECT (open_item), "activate",
                               GTK_SIGNAL_FUNC (GTK_STOCK_OPEN),
                               (gpointer) "file.open");
 
  
  gtk_menu_append (GTK_MENU (file_menu), open_item);
  gtk_menu_item_set_submenu (GTK_MENU_ITEM (file_item), file_menu);
  gtk_menu_shell_append (GTK_MENU_SHELL (menu_bar), file_item);
  gtk_box_pack_start(mmb->basebox,menu_bar, FALSE, FALSE, 0);
  //gtk_menu_shell_append (GTK_MENU_SHELL (mmb->basebox),file_item);
  gtk_widget_show (open_item);
  gtk_widget_show (file_item);

```
I've also tried to add the menu item to the box directly on a desperate attempt as you can see but it just behaved as a label (clicking it didn't show the submenu). 
What am i doing wrong?

After looking at the panel menubar code, i tried using some premade functions to generate menus like create_applications_menu() but gcc insisted on giving an undefined reference error. The thing is ,i'd included the ubuntu include and lib paths on the compile string as well as the path to the gnome-panel source (i couldn't find the gnome-panel menu.h file on my computer). Help would be greatly appreciated.

---

