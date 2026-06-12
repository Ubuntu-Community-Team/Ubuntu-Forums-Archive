---
title: "[SOLVED] disable the screensaver? (java?)"
date: 2007-05-12
forum: Programming Talk
---

### Post by stinkinrich88 on 2007-05-12
Hello!

Basically, I want to disable the screensaver (and screen power saver) when my java application is active. Is there a way to do this in java? If not, what command would I use to disable the screensaver from the terminal?

thanksss!!!!!!!

---

### Post by ssam on 2007-05-12
i think its best to do it with dbus.

have a look at these

[http://live.gnome.org/GnomePowerManager/DbusInterface](http://live.gnome.org/GnomePowerManager/DbusInterface)
[http://www.freedesktop.org/wiki/Software/DBusBindings](http://www.freedesktop.org/wiki/Software/DBusBindings)
[http://www.freedesktop.org/wiki/Software/dbus](http://www.freedesktop.org/wiki/Software/dbus)
[http://www.vitavonni.de/projekte/dbus-inspector.html.en](http://www.vitavonni.de/projekte/dbus-inspector.html.en)

in the gnome-screensaver source there is a docbook file /doc/dbus-interface.xml

---

### Post by stinkinrich88 on 2007-05-13
If anyone's interested, I used the Robot class to move the curser a pixel and back every second (using a timer). Works a treat, and cross platform!

---

