---
title: "Cannot get libnotify to work :/"
date: 2011-06-09
forum: Programming Talk
---

### Post by hakermania on 2011-06-09
Well, that's the code that SHOULD display a notification and then delete at once, but it just shows the notification, nothing more or less....

Can anyone help me out?
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
//IF YOU RUN THE CODE CHANGE THE BELOW PATH WITH A VALID IMAGE PATH
    icon = gdk_pixbuf_new_from_file("/home/alex/Pictures/fatality.png", &error); 
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
    GError** err = NULL;
    sleep(1);
    notify_notification_close(n,err); // <-- this doesn't work :'(
    g_object_unref(G_OBJECT(n));

    return 0;
}

```

Any help appreciated!

---

### Post by hakermania on 2011-06-10
bumpino

---

### Post by hakermania on 2011-06-12
BUMPINOOO

I start to think that this is a bug....

---

### Post by kostkon on 2011-06-12
You can't manually set the timeout or close a notification in ubuntu, because it has its own notification server, notify-osd. For more info and code samples, check [here]("https://wiki.ubuntu.com/NotificationDevelopmentGuidelines").

---

### Post by hakermania on 2011-06-12
thanks a lot

---

