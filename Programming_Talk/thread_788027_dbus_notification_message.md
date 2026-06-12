---
title: "dbus notification message"
date: 2008-05-09
forum: Programming Talk
---

### Post by uidzer0 on 2008-05-09
Hey everyone,

I'm new to dbus and I'd like to incorporate it into an applications I'm working on. I'd like to send a general notification message to the bus, what is the best method of doing this (using dbus-glib, dbus-glib-bindings)?

Here is what I currently have, although I don't think proxy_call is the right method for a general notification.

```

    DBusGConnection *connection;
    DBusGProxy *proxy;
    GError *error = NULL;

    connection = dbus_g_bus_get (DBUS_BUS_SESSION, NULL);
    if (connection == NULL) {
        return;
    }

    proxy = dbus_g_proxy_new_for_name (connection, 
                                       "org.gnome.XXX",
                                       "/org/gnome/XXX",
                                       "org.gnome.XXX");


    dbus_g_proxy_call_no_reply (proxy, "TEST",
                                G_TYPE_STRING, "TESTING",
                                G_TYPE_INVALID);

    g_object_unref (proxy);
    dbus_g_connection_unref (connection);


```

Thanks!

---

### Post by xelapond on 2008-05-09
What language are you doing it in?  It looks like C, but i'm not really sure.

---

### Post by uidzer0 on 2008-05-09
It's written in C - 

Here's what I currently have although I'm having some issues:

```

    #include <dbus/dbus.h>
    
    ...
    
    DBusConnection *connection;
    DBusMessage *message;
    DBusMessageIter iter;

    connection = dbus_bus_get (DBUS_BUS_SESSION, NULL);
    if (connection == NULL) {
        return;
    }

    message = dbus_message_new_signal ("/org/gnome/XXX",
                                       "org.gnome.XXX",
                                       "TEST");

    dbus_message_iter_init (message, &iter);
    dbus_message_iter_append_string (&iter, "TEST");

    dbus_connection_send (connection, message, NULL);

    dbus_message_unref (message);
    dbus_connection_unref (connection);


```

Compiling with -ldbus-1 however I'm getting
```

undefined reference to dbus_message_iter_append_string

```

Any thoughts?

---

### Post by uidzer0 on 2008-05-09
Doh, it's dbus_message_iter_append_basic - thats what I get for trusting the internet.

Anyway - more issues now =].

Current code:
```

    DBusConnection *connection;
    DBusMessage *message;
    DBusMessageIter iter;
    char *message_text = "TESTING!!!";

    connection = dbus_bus_get (DBUS_BUS_SESSION, NULL);
    if (connection == NULL) {
        return;
    }

    message = dbus_message_new_signal ("/org/gnome/XXX",
                                       "org.gnome.XXX",
                                       "TEST");

    dbus_message_iter_init (message, &iter);
    dbus_message_iter_append_basic (&iter, 
                                    DBUS_TYPE_STRING,
                                    &message_text);

    dbus_connection_send (connection, message, NULL);

    dbus_message_unref (message);
    dbus_connection_unref (connection);

```

When this is ran - I get a warning from dbus:
```

process 7226: arguments to dbus_message_iter_append_basic() were incorrect, assertion "real->iter_type == DBUS_MESSAGE_ITER_TYPE_WRITER" failed in file dbus-message.c line 2240.
This is normally a bug in some application using the D-Bus library.

```

So close! Any thoughts out there?

---

### Post by girishlc on 2011-12-09
hey could you please post the full code?

I want to get notification in my C code when any browser opens particular application and even when that application closes need a notification.

Please let me know how to do this?

---

