---
title: "Screen going off during video"
date: 2014-02-01
forum: New to Ubuntu
---

### Post by d.mayfair on 2014-02-01
I'm back with another problem :)

About 10 minutes into watching a live stream or video the screen goes off.
I have all display options re power management and screen savers turned off.

Using the command xset q I see DPMS is enabled so I enter xset -dpms and xset s off.Now it shows as disabled but when I swtich off and restart the computer it resets to being enabled again.

How do I turn screen savers and DPMS off permanently ?
I'm using xubuntu 13.10

---

### Post by bug67 on 2014-02-01
I use an app called caffeine.  It allows you to turn off the screensaver during video viewing.  It's in the software center.

---

### Post by Dennis N on 2014-02-01
> **d.mayfair said:**
> I'm back with another problem :)
How do I turn screen savers and DPMS off permanently ?
I'm using xubuntu 13.10

The screen-blanking after 10 minutes is due to the Power Management. To stop this, there are two actions you can take:

1) **Settings > Power Manager**
General Tab: uncheck "Monitor power management control"

OR,

2) **Settings > Sessions and Startup > Application Autostart Tab**
uncheck "Power Manager" to prevent it from starting.

I also use xscreensaver, and set the "Blank after" time > the movie length or it will activate, and "Power management enabled" is unchecked in Screensaver Preferences > Advanced.

Reference System: Xubuntu 12.10

---

### Post by d.mayfair on 2014-02-01
seems there's been a bug in ubuntu for quite some time
[https://bugs.launchpad.net/ubuntu/+source/xfce4-power-manager/+bug/1193716](https://bugs.launchpad.net/ubuntu/+source/xfce4-power-manager/+bug/1193716)

It's possible to turn it off but it comes back on after a reboot.
I'll have a look into your second suggestion and see if that works,cheers

---

### Post by d.mayfair on 2014-02-01
Ok,well I unchecked power manager from the startup menu but when I rebooted it is showing as enabled in xset q

I have enabled xscreensaver and set it to 720 minutes.Let's see if that works

---

