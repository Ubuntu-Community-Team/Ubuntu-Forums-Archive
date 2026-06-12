---
title: "purple screen with mouse after  updating gtk libs"
date: 2012-04-16
forum: New to Ubuntu
---

### Post by linnewbe on 2012-04-16
I have Ubuntu 10.0.4 LTS and everything was working fine, till i decided to become a bit adventerous and try installing the latest GTK/Glib. I initially tried downloading the latest Glib-2.32.1. Because of dependencies, i installed zlib-1.2.6, libffi-3.0.10 and gettext-0.18.1.1. 
 
Since there were still too many dependencies, i decided to just go ahead with the glib using the apt-get install libgtk*.
 
After reboot, all that comes now is the purple screen with the mouse. The GDM / Gnome startup screen is not that.
 
In /var/log/gdm/ (attached) i see a bunch of error messages like:
 
GLib-GObject-WARNING **: /build/buildd/glib2.0-2.24.1/gobject/gsignal.c:2273: signal `proxy-status' is invalid for instance `0x8963f18'
** (gnome-power-manager:1288): WARNING **: Either HAL or DBUS are not working!
 
Appreciate if the experts could shed some light on how i can get past the purple screen
 
Also, JFYI, i had installed some packages for Ubuntu to detect my Intel Sandy Bridge Graphics card. However, after that i had rebooted a couple of times without any issue.
 
Thanks!
 
-Ubuntu newbee

---

