---
title: "installing Ubuntu 8.0.4 using Mac from firewire"
date: 2008-07-13
forum: New to Ubuntu
---

### Post by corinhorn on 2008-07-13
I'm attempting to install Ubuntu onto a firewire drive and boot using an intel iMac.  I am a newbie at this stuff and have done some searching and have followed instructions as well as I can.  I'm not sure if I've done everything properly.

When I'm installing Ubuntu, I do the manual installation/partition setup.  I separate the firewire drive into 2 partitions:

Main partition with ext3 file system and mount point /
Swap partition with 1GB

It installs fine, but when i turn the Mac on and choose (using rEFIt) the system to boot in to, the new Linux system does not appear as an option.  What am I missing?  Do I need to create an EFI partition on the firewire drive as well?  Thanks!

~Corin

---

### Post by aysiu on 2008-07-15
I don't think it can be done, based on the Googling I've just done.

You can read more [here](http://tennessee.ubuntuforums.com/showthread.php?t=510030).

---

### Post by misterlister on 2008-11-04
While I'm also inclined to agree with you aysiu, based on my attempts to install on a firewire disk, your link is NOT compelling evidence against it, as it deals with booting from USB. Booting from USB is a relatively new thing for Macs, only being enabled since the advent of Intel based Macs. Firewire, on the other hand, has been an option for booting Macs for many years, from the introduction of FW 400, iirc.

FWIW, YMMV, etc.

Good luck corinhorn, and keep us updated.

---

