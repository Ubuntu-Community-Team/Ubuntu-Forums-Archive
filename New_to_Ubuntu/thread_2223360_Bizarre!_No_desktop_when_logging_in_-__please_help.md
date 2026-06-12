---
title: "Bizarre! No desktop when logging in -  please help!"
date: 2014-05-10
forum: New to Ubuntu
---

### Post by dcunn2002 on 2014-05-10
running 14.04.  Up till now had just one (administrator) account.

Everythig fine till this evening, but now when I log in I just see a blank ubuntu screen.

Right clicking the mouse brings up a small menu, through which I was able to access system settings and then create a new administrator account  - which works but I'd like to know why this has happened and how to restore dektop and settings  for my original account.

Any ideas?

Thanks

---

### Post by grahammechanical on 2014-05-10
If you can login then I suggest that it is not a problem with your user account. Unless you removed that user account. If you did then re-create it. May I suggest that you login to the normal user account. Then one with the blank screen and open a terminal - Ctrl+Alt+T or a tty Ctrl+Alt+F and run either or both of these commands.

```
sudo dconf reset -f /org/compiz/
sudo setsid unity
```

The first will reset Compiz, the compositing/window manager. The second will reset Unity, the user interface. Everything happens for a reason. Can you think of anything that you changed that might just have caused this problem? Have you changed some settings?

Regards.

---

### Post by dcunn2002 on 2014-05-10
Before i try that just wanted to clarify that using my original sole account I can log in but see no desktop jsut a black orange Ubuntu screen and can only access one small menu on right click.  I can't access terminal via ctrl alt t in that account.

One option on that small menu was screen settings and via this I got to all settings and then user accounts and was able to create a new administrator account which works but obviously all settings have to be started from scratch.

---

### Post by dcunn2002 on 2014-05-10
unfortunately I lost it but when i did the command to reset unity I got a heap of error messages

---

### Post by dcunn2002 on 2014-05-10
This is what I got when to resetting Unity:

tion, waiting for it...
ERROR 2014-05-10 21:02:33 unityo (appinfo2) <unknown>:0 g_dbus_proxy_new_for_bus: assertion 'g_variant_is_object_path (object_path)' failed
WARN  2014-05-10 21:02:33 unity.glib.dbus.server GLibDBusServer.cpp:579 Can't register object 'com.canonical.Unity.Session' yet as we don't have a connection, waiting for it...
WARN  2014-05-10 21:02:33 unity.glib.dbus.server GLibDBusServer.cpp:579 Can't register object 'org.gnome.ScreenSaver' yet as we don't have a connection, waiting for it...
WARN  2014-05-10 21:02:33 unityo (appinfo2) <unknown>:0 g_settings_set_value: value for key 'visual-bell-type' in schema 'org.gnome.desktop.wm.preferences' is outside of valid range
ERROR 2014-05-10 21:02:33 unity.glib.dbus.server GLibDBusServer.cpp:524 DBus name lost 'org.gnome.Shell'
ERROR 2014-05-10 21:02:33 unity.glib.dbus.server GLibDBusServer.cpp:524 DBus name lost 'com.canonical.Unity'
WARN  2014-05-10 21:02:33 unity.glib.dbus.proxy GLibDBusProxy.cpp:417 Calling method "CanShutdown" on object path: "/org/gnome/SessionManager" failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files
ERROR 2014-05-10 21:02:33 unity.session.gnome GnomeSessionManager.cpp:340 Gnome Session call failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files

---

### Post by dcunn2002 on 2014-05-10
> **grahammechanical said:**
> If you can login then I suggest that it is not a problem with your user account. Unless you removed that user account. If you did then re-create it. May I suggest that you login to the normal user account. Then one with the blank screen and open a terminal - Ctrl+Alt+T or a tty Ctrl+Alt+F and run either or both of these commands.

```
sudo dconf reset -f /org/compiz/
sudo setsid unity
```

The first will reset Compiz, the compositing/window manager. The second will reset Unity, the user interface. Everything happens for a reason. Can you think of anything that you changed that might just have caused this problem? Have you changed some settings?

Regards.

this doesn't work - from the first command I get error message: "error: cannot autolaunch D-Bus without X11 $display"

---

