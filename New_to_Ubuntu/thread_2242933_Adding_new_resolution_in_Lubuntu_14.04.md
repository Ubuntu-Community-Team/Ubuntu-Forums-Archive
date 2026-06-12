---
title: "Adding new resolution in Lubuntu 14.04"
date: 2014-09-05
forum: New to Ubuntu
---

### Post by dietwo on 2014-09-05
The supported resolution on monitor is 1366x768 but I don't know why its undetected in almost all Linux distributions that I have tried. I have rechecked monitor settings too on the monitor side.

I can successfully modify the screen resolution using the following method:

$ sudo xrandr --newmode "1344x768_60.00"   84.00  1344 1416 1552 1760  768 771 781 798 -hsync +vsync
$ sudo xrandr --addmode VGA1 1344x768_60.00
$ sudo xrandr --output VGA1 --mode 1344x768_60.00

Following some other threads to make the setting persistent, I am using the following method:

$ sudo vim /etc/xdg/lxsession/Lubuntu/autostart

@xscreensaver -no-splash
@lxpanel --profile Lubuntu
@pcmanfm --desktop --profile lubuntu
@/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1
@xrandr --auto --output VGA1 --primary --mode 1344x768

But, I am not getting the desired resolution. Any hint will be greatly appreciated.

---

### Post by JeQhdMD on 2014-09-07
What are your gpu specs?  Nvidia, ATI, Intel.  If not Intel, did you install the proprietary drivers?

---

### Post by dietwo on 2014-09-07
Its HP Z210 Machine with intel graphics. Yes, I have installed the drivers.

---

### Post by Vladlenin5000 on 2014-09-07
> **dietwo said:**
> Its HP Z210 Machine with intel graphics. Yes, I have installed the drivers.

There's no proprietary drivers for Intel so... Which ones have you installed exactly?

---

### Post by dietwo on 2014-09-07
mesa-utils and xserver-xorg-video-intel. But I believe, its not drivers issue. Monitor is not propagating its general information so I need to set the resolution explicitly.

---

### Post by JeQhdMD on 2014-09-08
Perhaps this guide is worth a try - just slightly different from your previous method:

[http://www.vxbus.com/software/linux/148-how-to-change-monitor-resolution-in-ubuntu-1204.html](http://www.vxbus.com/software/linux/148-how-to-change-monitor-resolution-in-ubuntu-1204.html)

---

### Post by Moni_Sinha on 2014-09-08
software supported Without Drivers.

---

