---
title: "XOSL or GRUB setup for multiple OSes"
date: 2009-02-04
forum: Other OS Talk
---

### Post by dbsoundman on 2009-02-04
I'm having a bit of a problem with a multi-OS system I'm building. Eventually, it will have DOS 6.21, Windows 95, Windows 2000, and Ubuntu 8.04 (in that order). I initially decided to use XOSL, and install it on the DOS partition (first one, FAT16 formatted). I installed XOSL fine (no errors), but when I reboot to start with XOSL, the computer just continuously reboots as soon as it gets to the point where it would boot XOSL (or whatever OS it finds). I uninstalled it, and restored the default boot loader, so now my system boots into DOS only, unless I use my super grub disk. Basically, I want to be able to use either XOSL or GRUB to  boot my OSes. I don't particularly care which one, I just want one of them to work. I can't find a simple set of instructions to reconfigure GRUB (which is currently with the Ubuntu installation on the last, extended partition). Can someone help me out here?

Thanks,
Dan

---

### Post by pelle.k on 2009-02-05
What i do is install grub to MBR for my primary linux installation. Then i just install grub too the system root (/) for the rest of the linux distros and point to that menu.lst like this:
> root (hd0,X)
configfile /boot/grub/menu.lst
But you could also copy a stanza from that particular menu.lst and boot the other distro directly from your primary (grub) menu.lst. (And/or chainloaders to boot windows).

The problem as you probably already know is that you have to install windows last of all, and if you cant do that you have to use a live cd and restore grub on the MBR (after windows wipes the MBR). This is pretty easy. (from a live distro) run "grub", then;
```
root(hd0,X)
setup(hd0)
```
Where "root" is your primary distro root (to restore grub again), and "setup" is where it gets installed again (in this case hd0 wich is MBR).

There's a third solution wich is pretty nifty too. Install windows, and all of your linux distros, but be sure to *always* install grub to the system root (/) on *all* distros, and let GAG ( [http://gag.sourceforge.net/](http://gag.sourceforge.net/) ) install to the MBR using a live cd. This last solution is probably the easiest, and best solution. Too bad GAG looks like crap though! :D

---

### Post by djhyland on 2009-02-05
Take a look at [COLOR="Blue"][this]("http://www.dedoimedo.com/computers/grub.html#mozTocId288068")[/COLOR] page.  It's a comprehensive guide to grub, and it has a link to an [COLOR="Blue"][example grub configuration]("http://www.justlinux.com/forum/showthread.php?threadid=143973")[/COLOR] that has around a hundred OS entries, your OSes among them.  I figure that you should be able to find what you want in that.

---

### Post by dbsoundman on 2009-02-06
Thanks, I figured out how to add entries to GRUB from those pages, and I used the super grub disk to restore it, so now everything is hunky-dorey!

-Dan

---

### Post by djhyland on 2009-02-06
Glad you figured things out, then.

---

