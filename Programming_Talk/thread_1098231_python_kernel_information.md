---
title: "python kernel information"
date: 2009-03-16
forum: Programming Talk
---

### Post by mustafa-linux on 2009-03-16
Hi ,,
I am wondering how to get device info like if the firmware is loaded or a usb device is pluged unpluged from the system, I did some search and find out that it could be done via hotplug and netlink socket but is there is any way else like HAL or something that is more information specific than filtering a text string.
thanks in advance

---

### Post by imdano on 2009-03-16
You can listen for the "DeviceAdded" signal from HAL's DBus interface to find out if a usb device is plugged and the "DeviceRemoved" signal to see if it's unplugged.  There may be a way to listen for firmware loading/unloading, too.

---

### Post by unutbu on 2009-03-16
See [http://redclay.altervista.org/wiki/doku.php?id=projects:hal-automount](http://redclay.altervista.org/wiki/doku.php?id=projects:hal-automount) for example python code which does which imdano described.

The code may throw some errors if you run this on Ubuntu, but I think enough of it works to still be a useful example.

---

