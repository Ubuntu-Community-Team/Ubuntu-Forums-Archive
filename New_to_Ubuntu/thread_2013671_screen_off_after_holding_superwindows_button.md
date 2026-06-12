---
title: "screen off after holding super/windows button"
date: 2012-07-01
forum: New to Ubuntu
---

### Post by evil77 on 2012-07-01
hi all,
i just installed ubuntu 1204 on my computer (intel Q9550 on Asus P5G41T-M LX with nivida gforce 9600GT). btw i'm new to linux

installation was fine so far, but if i press and hold the windowsbutton i'll see an overlay of shortcuts for a splitsecond, and my display switches off immediately. no matter what i do, i cant get the display back.
after that i can only switch the system off with my powerbutton, an then reboot it.

i couldn't find anything related. (google an so on...)

it doesn't seem to be a feature. i assume it's a bug.



in system settings--hardware--additional drivers
i tried to change the display driver from "nividia accelerated graphics driver (version current)" to "nividia accelerated graphics driver (post-release updates)". but the bug is still there.

i read something about unity 2D, but it seems not to be present in ubuntu 1204


any tips or help for an ubuntu/linux newbie? (sorry for bad spelling, im not fluent in english)

---

### Post by evil77 on 2012-07-04
so far i could test following things:

- if i boot with ahci on, or in ide mode, doesn't make a difference, system crashes (at least the grafikpart).

- if i boot from usbstick (livelinux?) instead of my harddiskinstalation (Mushkin Chronos 2,5" SSD 120 GB), there is no problem! it works without any flaw. don't know what the difference between livelinux und installation on HD/SSD is. (that could help)

- if i boot from my old harddisk the same problem is there, so it shouldn't depend on HD vs SSD, or IDE vs AHCI.

anybody any ideas?

---

### Post by evil77 on 2012-07-06
so, i tried a sapphire radeon HD6450, and the problem is gone.

so it is problem with nividia geforce 9600GT.

are there any different drivers for this gpu?


am i doing something wrong? nobody is participating, or answering...

---

### Post by Krytarik on 2012-07-06
> **evil77 said:**
> are there any different drivers for this gpu?
One option would be to use the default "nouveau" driver, which seems to work fine:
> **evil77 said:**
> if i boot from usbstick (livelinux?) instead of my harddiskinstalation (Mushkin Chronos 2,5" SSD 120 GB), there is no problem!
For that, remove any proprietary Nvidia drivers via Additional Drivers, and modify/remove your "/etc/X11/xorg.conf":[INDENT][http://nouveau.freedesktop.org/wiki/UbuntuPackages](http://nouveau.freedesktop.org/wiki/UbuntuPackages)
[/INDENT]Another option would be to upgrade to the most recent version of the proprietary Nvidia driver provided by the Ubuntu X-Swat PPA, currently 302.17:[INDENT][http://www.tuxgarage.com/2011/07/upgrade-video-drivers-through-ppas.html](http://www.tuxgarage.com/2011/07/upgrade-video-drivers-through-ppas.html)[/INDENT]Regards.

---

### Post by codingman on 2012-07-06
Try reinstalling the drivers. That is usually the case for the older nVidia's. Quite odd if you ask me.

---

### Post by evil77 on 2012-07-14
> **Krytarik said:**
> 
Another option would be to upgrade to the most recent version of the proprietary Nvidia driver provided by the Ubuntu X-Swat PPA, currently 302.17:[INDENT][http://www.tuxgarage.com/2011/07/upgrade-video-drivers-through-ppas.html](http://www.tuxgarage.com/2011/07/upgrade-video-drivers-through-ppas.html)[/INDENT]Regards.

Big THX, that did it :D

---

