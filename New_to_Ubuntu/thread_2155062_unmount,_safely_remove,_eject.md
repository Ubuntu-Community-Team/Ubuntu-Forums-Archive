---
title: "unmount, safely remove, eject"
date: 2013-06-17
forum: New to Ubuntu
---

### Post by monkeybrain2012 on 2013-06-17
Ok I am on Ubuntu 13.04 and got a bit confused. 

If I plug in a usb flash drive (no bigger than 8G), it gets mounted on the desktop (I enable it from gnome-tweak-tool) and the Unity launcher, if I right click the desktop icon, it shows only the option "eject", if I click that the desktop icon disappears but the drive is still shown on the Unity bar and the left pane in Nautilus, so it is actually still attached though not mounted. Click the icon on the Unity bar a second time and "eject" then it is detached. So it seems like the first "eject" is actually "unmount" and the second "eject" is the same as "safely removed".

If instead of a usb flash drive I plug in an external hard drive, then again the drive is mounted on the desktop and the Unity bar, but this time the right click menu show only the option "safely remove", and if I click that the drive is detached (not on unity launcher and not in Nautilus's side pane), so there is no way to simply unmount it with a click. In order to unmount the drive or the partitions and yet keep it attached (I am doing a system backup)  I need to either use the command or gparted.

I am wondering if these are expected behaviours, a bug, or is there a setting for it? I was searching google a bit and there was a bug in 12.10 or something that says safely remove is missing and there is only "unmount", but It seems that I can't find the "unmount" option anywhere, only safely remove or eject??

---

### Post by monkeybrain2012 on 2013-06-17
OK, it seems that the first observation (with usb flash drive) only happens when the flash drive is a live usb with a 64-bit Linux in it. With a 32 bit it doesn't happen. This machine is 32 bit.

---

### Post by monkeybrain2012 on 2013-06-17
So it appears that "unmount" is only an option in the right click menu for partitions in the same hard drive as the OS, but not for partitions on a different hard drive.

---

### Post by Buntu Bunny on 2013-06-18
I was wondering about this myself. [This article]("http://ubuntutalk.tumblr.com/post/346018554/the-unmount-eject-and-safely-remove-drive-dilemma") at *Talking About Ubuntu* explains the difference.

---

### Post by mc4man on 2013-06-18
13.04 brought back 'safely remove', but only on **hot-plugged** devices, not those connected at boot

As far as flash drives I've found that it doesn't matter what's on the drive, it's the drive itself. Some get the usb flash icon & can only be ejected, some get the 'dual device icon' & can be safely removed or ejected.
screen show 1 of each, both are formatted the same & just contain similar files. The hp only gets eject, the sandisk gets full set of options like usb hdd's

---

