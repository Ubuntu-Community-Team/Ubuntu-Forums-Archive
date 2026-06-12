---
title: "Combining Qt with GTK-only one problem!"
date: 2012-06-28
forum: Programming Talk
---

### Post by hakermania on 2012-06-28
I am using this code:
```
g_signal_connect(showapp_option, "activate", G_CALLBACK(&MainWindow::show_app), appindicator);
```
so as to connect my indicator menu item to the function show_app(), and it works just fine, irregardless the fact that I get the following warning:

```
warning: converting from 'void (MainWindow::*)()' to 'GCallback {aka void (*)()}' [-Wpmf-conversions]

```
I don't understand the warning as I've never worked with the gtk libs before... Anyway, this isn't the real reason I'm posting here, but it is maybe related to it.

The problem is that I cannot use 'this' (which stands for the MainWindow's call) from inside show_app() function, because the program crashes!

Why I cannot use 'this' inside the function? And, more importantly, how do I make it work?

---

### Post by SledgeHammer_999 on 2012-06-28
As far as I can tell this is a problem relating to C not mixing well with C++.

What type is "showapp_option"?

---

### Post by hakermania on 2012-06-30
> **SledgeHammer_999 said:**
> As far as I can tell this is a problem relating to C not mixing well with C++.

What type is "showapp_option"?

After some inspection, that's my full updated code(which still doesn't work though):
```

void [COLOR="Orange"]show_app[/COLOR](MainWindow *[COLOR="Red"]data[/COLOR])
{
    //crashes here
    [COLOR="Red"]data[/COLOR]->show();
}


void MainWindow::make_indicator()
{
    if(appindicator){
        //appindicator has already been created
        return;
    }
    appindicator = app_indicator_new("Format Junkie Indicator", "formatjunkie", APP_INDICATOR_CATEGORY_APPLICATION_STATUS);
    GtkWidget* showapp_option;
    GtkWidget* indicatormenu = gtk_menu_new();
    GtkWidget* item = gtk_menu_item_new_with_label("Format Junkie main menu");
    gtk_menu_item_set_submenu(GTK_MENU_ITEM(item), indicatormenu);

    showapp_option = gtk_menu_item_new_with_label("Show App!");
    g_signal_connect(showapp_option, "activate", G_CALLBACK([COLOR="Orange"]show_app[/COLOR]), [COLOR="Red"]this[/COLOR]);
    gtk_menu_shell_append(GTK_MENU_SHELL(indicatormenu), showapp_option);

    gtk_widget_show_all(indicatormenu);
    app_indicator_set_status(appindicator, APP_INDICATOR_STATUS_ACTIVE);
    app_indicator_set_attention_icon(appindicator, "dialog-warning");

    app_indicator_set_menu(appindicator, GTK_MENU (indicatormenu));
}
```

I think that now things are more clear for you :)

---

### Post by hakermania on 2012-07-01
bump

---

