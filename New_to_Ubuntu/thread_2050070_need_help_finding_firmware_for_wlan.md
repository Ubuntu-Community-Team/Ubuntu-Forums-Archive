---
title: "need help finding firmware for wlan"
date: 2012-08-30
forum: New to Ubuntu
---

### Post by jcheung94 on 2012-08-30
i have a broadcom corporation bcm4318 [airforce one 54g] 802.11g wireless lan controller (rev 2). if someone could help me with finding and installing the firmware from a separate computer via USB, it would be much appreciated...

ubuntu version 12.04.1
laptop model inspiron b130

:popcorn:

---

### Post by fractalman on 2012-08-30
Don't know about doing it over a usb, hopefully someone will be along who can answer that, thought these links might help you

[http://linuxwireless.org/](http://linuxwireless.org/)

[http://wireless.kernel.org/en/users/Devices/USB](http://wireless.kernel.org/en/users/Devices/USB)

[http://www.aircrack-ng.org/doku.php?id=install_drivers](http://www.aircrack-ng.org/doku.php?id=install_drivers)

[http://aircrack-ng.org/doku.php?id=compatibility_drivers](http://aircrack-ng.org/doku.php?id=compatibility_drivers)

---

### Post by Cheesehead on 2012-08-30
Step 1: Check linuxwireless.org.
bcm4318, according to [http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43) , is supported by the b43 driver.

Step 2: Check if your driver is already installed.
```
$ dpkg -S b43.ko
linux-image-2.6.38-11-generic: /lib/modules/2.6.38-11-generic/kernel/drivers/net/wireless/b43/b43.ko
linux-image-3.0.0-12-generic: /lib/modules/3.0.0-12-generic/kernel/drivers/net/wireless/b43/b43.ko
```
That driver is included with the normal Ubuntu kernel image, and is probably already installed on your system.

If it were in a different package, you could search [http://packages.ubuntu.com](http://packages.ubuntu.com) for the package it's in, then USB-stick that package to your desktop, then double-click on it to install.

Since the kernel module is likely already installed, what seems to be the problem? Not recognized? Not working? Working poorly?

---

### Post by jcheung94 on 2012-08-30
either i'm doing something wrong, or something is just wrong....

[IMG]http://i1247.photobucket.com/albums/gg635/jcheung19/CAM00143.jpg[/IMG]


and then

[IMG]http://i1247.photobucket.com/albums/gg635/jcheung19/CAM00144.jpg[/IMG]

---

### Post by jcheung94 on 2012-08-30
did some more digging and i finally got a fix from post #8 on [http://ubuntuforums.org/showthread.php?t=1269683](http://ubuntuforums.org/showthread.php?t=1269683)

thank you all for your time.

---

