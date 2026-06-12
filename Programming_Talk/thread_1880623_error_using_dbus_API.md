---
title: "error using dbus API"
date: 2011-11-14
forum: Programming Talk
---

### Post by avee137 on 2011-11-14
Hello ,
I am a newbie to dbus programming . I tried executing the following sample code on ubuntu-11.04:
```
#include <dbus/dbus.h>
#include <stdio.h>


int main(){


DBusError error;
DBusConnection *conn;

dbus_error_init (&error);
conn = dbus_bus_get (DBUS_BUS_SYSTEM, &error);
if (!conn) {
    fprintf (stderr, "%s: %s\n",
             err.name, err.message);
    return 1;
}
}

```


it gives me following error
```
dbusDemo.c:1:23: fatal error: dbus/dbus.h: No such file or directory
compilation terminated.

```
Do i need to install any development libraries or some similar sort of thing? 
Any relevant help would be greatly appreciated.

---

### Post by crdlb on 2011-11-14
Yes, you need libdbus-1-dev. You also need to use pkg-config to provide the correct include and library paths. How exactly are you compiling the code?

Also, what are you doing with dbus? You may want to consider another api, such as GLib's [GDBus]("http://developer.gnome.org/gio/2.30/gdbus-convenience.html"). (Edit: the high-level part of that API is only in GLib 2.30 in Ubuntu 11.10, [the rest]("http://developer.gnome.org/gio/2.30/gdbus-lowlevel.html") is in 2.26 in Ubuntu 10.10)

---

