---
title: "time and date locked?"
date: 2011-09-15
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by arpanaut on 2011-09-15
tzdata just updated and it has changed my location and time and the time & date settings app. is locked.
 I cannot unlock to reset my location or adjust time.

Any Clues?

---

### Post by mc4man on 2011-09-15
It's the new lightdm, apparently it is ignoring a default .pkla - I thought it was just a .pkla I use, seems it goes a bit further
(this .pkla allows admin time & date, updating existing packages in update manager and some more

Downgrade to lightdm_0.9.5-0ubuntu2, do restart how ever you can and see if fixed

---

### Post by arpanaut on 2011-09-15
Interesting...
I'll give it a shot, 

thanks

---

### Post by mc4man on 2011-09-15
bug I filed a little while ago - have adjusted to inc the default .pkla
[https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/851135](https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/851135)

Here's the .pkla - all the uncommented ones may be affected by this
```
[Mounting, checking, etc. of internal drives]
Identity=unix-group:admin
Action=org.freedesktop.udisks.filesystem-*;org.freedesktop.udisks.drive-ata-smart*
ResultActive=yes

[Change CPU Frequency scaling]
Identity=unix-group:admin
Action=org.gnome.cpufreqselector
ResultActive=yes

[Setting the clock]
Identity=unix-group:admin
Action=org.gnome.clockapplet.mechanism.*;org.gnome.settingsdaemon.datetimemechanism.*;org.kde.kcontrol.kcmclock.save
ResultActive=yes

[Adding or changing system-wide NetworkManager connections]
Identity=unix-group:admin
Action=org.freedesktop.NetworkManager.settings.modify.system
ResultActive=yes

[Update already installed software]
Identity=unix-group:admin
Action=org.debian.apt.upgrade-packages
ResultActive=yes

[usb-creator]
Identity=unix-group:admin
Action=com.ubuntu.usbcreator.mount;com.ubuntu.usbcreator.image
ResultActive=yes

#[Disable hibernate by default]
#Identity=unix-user:*
#Action=org.freedesktop.upower.hibernate
#ResultActive=no
```

---

### Post by chrisccoulson on 2011-09-15
This is actually [https://launchpad.net/bugs/851055]("https://launchpad.net/bugs/851055"), and we've just uploaded a fix for it

---

### Post by alexvy13 on 2011-09-15
i did apt-get update and nothing is showing up

---

### Post by mc4man on 2011-09-15
> **alexvy13 said:**
> i did apt-get update and nothing is showing up

Give it a little while

---

### Post by arpanaut on 2011-09-15
thanks chris,
saved me some hacking.

Issue seems to be resolved.

---

