---
title: "Libnotify warning messages - quite weird situation"
date: 2011-07-13
forum: Programming Talk
---

### Post by hakermania on 2011-07-13
Hello ubuntu geeks :D!
Well, I have this code:
```

#include "libnotify/notify.h"

void closed_handler (NotifyNotification* notification,        gpointer            data){
g_print ("LOL\n");
}

int main ()
{
    NotifyNotification* notification;
    gboolean            success;
    GError*             error = NULL;

    if (!notify_init ("icon-summary"))
        return 1;

    /* try the icon-summary case */
    notification = notify_notification_new ("WiFi connection lost", NULL, "notification-network-wireless-disconnected", NULL);
    error = NULL;
    success = notify_notification_show (notification, &error);
    if (!success)
    {
        g_print ("That did not work ... \"%s\".\n", error->message);
        g_error_free (error);
    }

    g_signal_connect (G_OBJECT (notification),
              "closed",
              G_CALLBACK(closed_handler),
              NULL);

    notify_uninit ();

    return 0;
}

```

And it runs OK in my system, the notification is shown, but when I sent this code to my co-developer the program run, but he couldn't see the notification at all, while I could.
Both of us are using Ubuntu 11.04 (he's in classic mode while I'm in Unity, does this really matter?) and both of us take this _small_ warning while running the program:
```

** (process:13622): CRITICAL **: dbus_g_proxy_disconnect_signal: assertion `!DBUS_G_PROXY_DESTROYED (proxy)' failed

** (process:13622): CRITICAL **: dbus_g_proxy_disconnect_signal: assertion `!DBUS_G_PROXY_DESTROYED (proxy)' failed

```

Our uname -a's:
Mine:
```

Linux MaD-pc 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686 i686 i386 GNU/Linux

```

His:
```

Linux CityBong-PC 2.6.38-8-generic-pae #42-Ubuntu SMP Mon Apr 11 05:17:09 UTC 2011 i686 i686 i386 GNU/Linux

```
(no differences at all)

So, I assume that this small warning avoids the notification from being shown, but I really don't know how to get rid of it...
Google search revealed to use init() somewhere before creating the notification (but it was from a guy who was using python so im not sure at all)

Thanks in advance for any answer :):)

---

### Post by hakermania on 2011-07-13
He just told me that the example's working if he logs in into UNITY ??? Omg! That means that in Unity it works but in classic mode it doesn't!
what's going on?

---

