---
title: "C Programming - GtkStatusIcon problem !"
date: 2012-05-19
forum: Programming Talk
---

### Post by etdsbastar on 2012-05-19
Hello friends,

I am creating a project with GtkStatusIcon but there is some problem with the code which I am unable to catch please help anyone. Actually, the status icon is not coming in the tray menu.

```
    gtk_status_icon_set_from_pixbuf(status_icon, create_pixbuf(PATH_IMG_PACKAGE));
    gtk_status_icon_set_tooltip_text(status_icon, MSG_PKG_NAME);
    gtk_status_icon_set_visible(status_icon, TRUE);
```

---

### Post by hakermania on 2012-05-19
This is some code I used to create an indicator a long time ago.
I don't understand it completely, so I just leave it here, in case it helps you"
```


#include <gtk/gtk.h>
#include <libappindicator/app-indicator.h>
#include <QDebug>


void print_a(GtkWidget *wid)
{
    qDebug() << "A";

}

void print_b(GtkWidget *wid)
{
    qDebug() << "B";
    //gtk_widget_hide(wid);
}

void quit_from_indicator(){
    exit(0);
}

GtkWidget* make_menu(AppIndicator* indicator)
{
        GtkWidget* menu = gtk_menu_new();
        GtkWidget* item = gtk_menu_item_new_with_label("Wallch main menu");
        gtk_menu_item_set_submenu(GTK_MENU_ITEM(item), menu);
        GtkWidget* subitem1 = gtk_menu_item_new_with_label("print A");
        g_signal_connect(subitem1, "activate", G_CALLBACK(print_a), indicator);
        gtk_menu_shell_append(GTK_MENU_SHELL(menu), subitem1);
        GtkWidget* subitem2 = gtk_menu_item_new_with_label("print B");
        g_signal_connect(subitem2, "activate", G_CALLBACK(print_b), indicator);
        gtk_menu_shell_append(GTK_MENU_SHELL(menu), subitem2);
        GtkWidget* subitem3 = gtk_menu_item_new_with_label("Quit");
        g_signal_connect(subitem3, "activate", G_CALLBACK(quit_from_indicator), indicator);
        gtk_menu_shell_append(GTK_MENU_SHELL(menu), subitem3);
        gtk_widget_show_all(menu);
        return menu;
}


int
main(int argc, char** argv)
{
        gtk_init (&argc, &argv);

        AppIndicator* indicator = app_indicator_new("Wallch Indicator", "wallch", APP_INDICATOR_CATEGORY_APPLICATION_STATUS);

        GtkWidget* indicatormenu = make_menu(indicator);

        app_indicator_set_status(indicator, APP_INDICATOR_STATUS_ACTIVE);
        app_indicator_set_attention_icon(indicator, "dialog-warning");

        app_indicator_set_menu(indicator, GTK_MENU (indicatormenu));

        gtk_main ();

        return 0;
}

```
QDebug is a Qt lib, from which I use the qDebug() function to write to output

---

### Post by etdsbastar on 2012-05-19
> **hakermania said:**
> This is some code I used to create an indicator a long time ago.
I don't understand it completely, so I just leave it here, in case it helps you"
...
QDebug is a Qt lib, from which I use the qDebug() function to write to output

Dear,

My program is using libgtk+-3.0 so I request you please to provide some code with GTK3+

---

### Post by lisati on 2012-05-20
*Thread moved to **Programming Talk**.*

---

### Post by MG&amp;TL on 2012-05-20
> **etdsbastar said:**
> Dear,

My program is using libgtk+-3.0 so I request you please to provide some code with GTK3+

That code looks like it should work. Just remove qDebug() from it.

---

