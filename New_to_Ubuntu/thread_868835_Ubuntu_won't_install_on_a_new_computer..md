---
title: "Ubuntu won't install on a new computer."
date: 2008-07-24
forum: New to Ubuntu
---

### Post by lzyeddie on 2008-07-24
Completely new build, can't get an Ubuntu 7.1 CD that I've used several times before to install.
First. Specs.

Motherboard: nVidia 680i SLI
CPU: Intel Core 2 Duo
HDD: 2x Hitachi SATA on separate lines, not RAID enabled
DVD-RW: 2x Lite-On on same line
Video Card: nVidia e-GeForce 8800 GTS
Monitor: Acer AL2016W 20" (1680x1050 res)

Ubuntu autorun leads to install screen. Selecting install/run and other options with the various suggested command lines all have same outcome. After the bar fills, it prompts to configure monitor and video card or run in safe graphics mode. If I configure, my monitor is not listed and is recognized as generic plug n play. If I test a generic LCD as a widescreen with near correct resolution, the test works and continues the config. When I test the video card with the nVidia driver, it exits the config tool and proceeds to try to start Ubuntu, stalling at the boot scripts step. Reversing the config order does not change either outcome. Choosing safe graphics mode at the install screen merely skips the config tool and goes straight to stalling at the boot scripts step.

There seems to be no rhyme or reason at this point, sometimes it completely freezes with the only indication being that NumLock and CapsLock on the keyboard flash, forcing me to cut power at the power supply. Sometimes it responds to keystrokes, displaying text but not responding to any command except Ctrl+Alt+Del, at which point it unmounts temporary filesystems, deactivates swap, unmounts local filesystems and displays

unmount2: Device or resource busy [ok]
unmount: /cdrom busy - remounted read-only [ok]
Segmentation fault
[fail]
* casper is resynching snapshots and caching reboot files...


Then I'm prompted to remove my disk and hit enter for a reboot.

After that prompt it gives further error messages.

usplash: Setting mode 640x480 failed
screen init failed

I don't know what to do. The only other operating system I have at my disposal is Server 2003, which I've successfully installed and thus installed all drivers on my computer before trying to install Ubuntu, except the video card and monitors because their drivers are only compatible with 64-bit OS's. I tried hunting down compatible drivers with no success.

Please help. I'm willing to try anything at this point.

---

### Post by Potatoj316 on 2008-07-24
Maybe if you tried 8.04 instead of 7.10, 8.04 is newer and may contain something to fix the proglem.
It could be that your disk is damaged in which case using a nes 8.04 disk would fix that problem as well.  You can check for this in the check disk for errors (or whatever its called) option when you first boot with the disk

---

### Post by phidia on 2008-07-24
Personally I would try a livecd at this point (knoppix, pclinuxos, nimblex are all good ones). You may need to use boot options on your hardware/motherboard for some reason.

***I just noticed that you have the 8800 gpu some people are having problems with that card. Either boot in safe graphic/recovery mode or use the livecd idea I mentioned above, and edit you /etc/X11/xorg.conf. You want to change the driver from "nvidia" to "nv". After you have a desktop you can read posts in the [multimedia & video]("http://ubuntuforums.org/forumdisplay.php?f=334") section on [your card]("http://ubuntuforums.org/search.php?searchid=45090455"). There are actually so many trouble reports on the 8800 that I just included the whole search in that last link.

---

