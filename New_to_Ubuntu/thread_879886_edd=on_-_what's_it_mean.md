---
title: "edd=on - what's it mean?"
date: 2008-08-04
forum: New to Ubuntu
---

### Post by Temporary Saint on 2008-08-04
The only way I can get the Kubuntu 8.04 CD to load succesfully on my computer is by selecting Safe Graphic Mode and, most importantly, by selecting edd=on from the F6 menu.  No other option on this menu results in a successful load.  All I would get is the empty desktop and the task bar with no mouse or keyboard control.  What does the edd parameter indicate?  Also, the two fixed disks in the system do not diplay in Dolphin until the OS has been running for about 10 minutes.

My PC is an old HP Vectra VEi8.  Pentium III 450 Mhz w/384MB RAM (system max) and planty of free disk space.  Windows XP SP2 is currently loaded on the system.  My Award BIOS is dated Oct. 1999 (it's the latest I was able to find on HP's web site) so I get the acpi=force message at boot.  There is no single option in the BIOS menus enable ACPI however there are three separate options regarding power mgmt such auto power-on from LAN activty, etc.  Should they all be enabled?

Steve
8{I

---

### Post by AdamWood on 2008-08-04
Someone with more kernel knowledge than me may wish to correct me but...

Edd is way for very old BIOS to boot from disks that are larger than 32Gb.

384Mb of ram is the minimum you really need for a KDE desktop (Xfce might be a better choice) so that could be why you're dropping into safe graphics mode. It could also be a strange video card and there's not much you can do about that.

As for your power options in the BIOS it sounds like they are the standard "Turn my PC on if this happens" setting not a configuration option to change how your computer manages it's power usage. Basically I think they're not relevant to you.

I would suggest you try Xubuntu on this machine of yours and I think it will run better.

---

### Post by Temporary Saint on 2008-08-04
Regarding the 'edd' issue, you've probably hit the nail on the head.  I was considering Xubuntu, but I really liked Kubuntu.  I'll try Xubuntu and see how it goes.

Thanks!

Steve
8{I

---

