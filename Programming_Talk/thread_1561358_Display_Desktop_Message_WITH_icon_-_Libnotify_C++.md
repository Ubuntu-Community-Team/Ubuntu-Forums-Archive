---
title: "Display Desktop Message WITH icon - Libnotify C++"
date: 2010-08-26
forum: Programming Talk
---

### Post by hakermania on 2010-08-26
Well, actually this code is nowhere else at the net (as Google says) and I think that a lot of people want to do something like that...So the code is:
```
#include <libnotify/notify.h>
#include <stdio.h>
#include <unistd.h>

int main()
{
    GError *error = NULL;
    NotifyNotification *n;
    GdkPixbuf *icon;
        g_type_init();
    icon = gdk_pixbuf_new_from_file("/home/alex/Pictures/terminal/alien.png", &error);
    notify_init("Basics");
    n = notify_notification_new ("Summary",
                                 "\nThis is the message that we want to display",
                                  NULL, NULL);
    notify_notification_set_icon_from_pixbuf
                                                            (n,
                                                              icon);
    notify_notification_set_timeout (n, 5000); // 5 seconds
    if (!notify_notification_show (n, NULL))
    {
        return 1;
    }
    g_object_unref(G_OBJECT(n));
    return 0;
}

```If you get errors like libnotify.h [Not Found] or something similar you have to add this into the makefile (into the .pro file in QtCreator):
```

CONFIG += link_pkgconfig
PKGCONFIG += libnotify
```Thx to guys from IRC channel ##c++ at irc.ubuntu.com :))))))

---

### Post by StephenF on 2010-08-26
Looks like plain old C to me.

---

### Post by hakermania on 2010-08-27
Well, I compiled it wiith Qt4 - C++ compiler :)

---

