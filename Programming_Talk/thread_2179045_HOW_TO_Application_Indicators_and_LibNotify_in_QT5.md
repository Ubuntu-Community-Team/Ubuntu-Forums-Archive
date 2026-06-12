---
title: "HOW TO: Application Indicators and LibNotify in QT5"
date: 2013-10-06
forum: Programming Talk
---

### Post by Woody1987 on 2013-10-06
This is a how-to on implementing application indicators and libnotify in QT5.

With thanks to this post [http://stackoverflow.com/questions/17193307/qt-systray-icon-appears-next-to-launcher-on-ubuntu-instead-of-on-the-panel]("http://stackoverflow.com/questions/17193307/qt-systray-icon-appears-next-to-launcher-on-ubuntu-instead-of-on-the-panel")

My setup:
Ubuntu 13.10 64bit
QT Creator 2.7.1
QT 5.0.2

1. Install required libraries
```
sudo apt-get install libgtk2.0-dev libappindicator-dev libnotify-dev
```

2. Create a new Qt Gui Application in Qt Creator

3. Edit the .pro file, add:
```
INCLUDEPATH += /usr/include/libappindicator-0.1 \
        /usr/include/gtk-2.0 \
        /usr/lib/gtk-2.0/include \
        /usr/include/glib-2.0 \
        /usr/lib/glib-2.0/include \
        /usr/include/cairo \
        /usr/include/atk-1.0 \
        /usr/include/pango-1.0

LIBS += -L/usr/lib -lappindicator -lnotify

CONFIG += link_pkgconfig

PKGCONFIG = gtk+-2.0
```

4. In your mainwindow.cpp, add the headers
```
#undef signals
extern "C"
{
    #include <libappindicator/app-indicator.h>
    #include <libnotify/notify.h>
    #include <gtk/gtk.h>
}
#define signals public
```

5. Create the indicator. This example will create an indicator with two menu options, one to show/hide the application and another to quit it.
```
/*
 * Indicator call backs
 */
extern "C"
{
void onShow(GtkCheckMenuItem *, gpointer);
void onQuit(GtkMenu *, gpointer);
}

void onShow(GtkCheckMenuItem *menu, gpointer data)
{
    bool checked = gtk_check_menu_item_get_active(menu);
    QApplication *self = static_cast<QApplication *>(data);
    if(checked)
        self->allWindows().at(0)->show();
    else
        self->allWindows().at(0)->hide();
}

void onQuit(GtkMenu *menu, gpointer data)
{
    Q_UNUSED(menu);
    QApplication *self = static_cast<QApplication *>(data);
    self->quit();
}

/*
 * Create the indicator with two menu options, show/hide and quit application
 */
void MainWindow::createIndicator()
{
    QString desktop;
    bool isUnity;

    desktop = getenv("XDG_CURRENT_DESKTOP");
    isUnity = (desktop.toLower() == "unity");

    if(isUnity) //only use this in unity
    {
        AppIndicator *indicator;
        GtkWidget *menu;
        GtkWidget *showItem;
        GtkWidget *quitItem;

        menu = gtk_menu_new();

        //show Item
        showItem = gtk_check_menu_item_new_with_label("Show Application");
        gtk_check_menu_item_set_active((GtkCheckMenuItem*)showItem, true);
        gtk_menu_shell_append(GTK_MENU_SHELL(menu), showItem);
        g_signal_connect(showItem, "toggled", G_CALLBACK(onShow), qApp);
        gtk_widget_show(showItem);

        //quit item
        quitItem = gtk_menu_item_new_with_label("Quit");
        gtk_menu_shell_append(GTK_MENU_SHELL(menu), quitItem);
        g_signal_connect(quitItem, "activate", G_CALLBACK(onQuit), qApp);
        gtk_widget_show(quitItem);

        indicator = app_indicator_new("example", "indicator-messages", APP_INDICATOR_CATEGORY_OTHER);

        app_indicator_set_status(indicator, APP_INDICATOR_STATUS_ACTIVE);
        app_indicator_set_menu(indicator, GTK_MENU(menu));
    }
    else //other DE's and OS's
    {

    }
}
```

6. Create a notification
```
void MainWindow::createNotification()
{
    QString desktop;
    bool isUnity;

    desktop = getenv("XDG_CURRENT_DESKTOP");
    isUnity = (desktop.toLower() == "unity");

    if(isUnity) //only use this in unity
    {
        if(!notify_init("example"))
            return;

        NotifyNotification *notf;

        notf = notify_notification_new("test", "test", NULL);
        notify_notification_show(notf, NULL);

        notify_uninit();
    }
    else //other DE's and OS's
    {

    }
}
```

7. Run the application, a new message indicator will appear with two menu options. A notification should also appear.


**Example project**
[ATTACH]246781[/ATTACH]

---

### Post by SledgeHammer_999 on 2013-10-07
Why use libnotify directly?

For the notification area you can use QSystemTrayIcon which supports showing "messages" and other stuff. Also in qt5 there is QPlatformSystemTrayIcon, although I never used it yet.
[https://qt-project.org/doc/qt-5.1/qtwidgets/qsystemtrayicon.html](https://qt-project.org/doc/qt-5.1/qtwidgets/qsystemtrayicon.html)
[https://qt-project.org/doc/qt-5.1/qtgui/qplatformsystemtrayicon.html](https://qt-project.org/doc/qt-5.1/qtgui/qplatformsystemtrayicon.html)

---

### Post by Woody1987 on 2013-10-07
Ive found that QSystemTrayIcon doesnt currently work with Indicators, at least with qt5 in ubuntu 13.10. In regards to QPlatformSystemTrayIcon, I cant even find the header for it.

---

### Post by SledgeHammer_999 on 2013-10-07
I haven't worked with Unity. I assumed that Appindicators and systray are 2 separate things, ie you can have both at the same time. I guess I am wrong.

Moreover from the link above the include is:
[php]#include <QPlatformSystemTrayIcon>[/php]

---

### Post by xgarth on 2014-07-27
Woody1987's sample project, "Example Project.zip", worked great for me on my development environment:  Ubuntu 14.04.1 LTS with Qt Creator 3.0.1.  Thank you for sharing this thread and for creating the sample project.

---

### Post by fugu2 on 2015-03-31
It's the end of march, 2015, and Qt5 is still broken when it comes to QSystemTrayIcon. I love how cross platform Qt is becoming.

---

