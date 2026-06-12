---
title: "Where'd my grub go?"
date: 2008-09-07
forum: New to Ubuntu
---

### Post by childofstrings on 2008-09-07
Hey guys,
I've got a bit of a problem with my new 8.04 Ubuntu install. I've dual booted Ubuntu before with Windows XP on my old PC and never had a problem with it. For some reason, Im having problems dual booting it on my new custom built PC with Windows XP Pro.

My Programs/OS drive is a 160GB SATA drive. I've had Windows XP running smoothly on the drive for just over a week now. Using the partition editor in the live disc, I partitioned 20GB or so for Ubuntu then partitioned 2 GB for swap. I mounted the 20GB as / and all that good stuff. Had no problems selecting the correct drives to install Ubuntu to. Initiated the install...everything appeared to go smoothly...rebooted PC.

I expected to be greeted by the charming grub load but instead I got a blinking curser for a few seconds and my PC went straight into booting Windows. No sign of grub loader what so ever. Windows starts running CHKDSK on all my drives. I skip them. Boot into XP, and reboot the machine. Same thing, this time I let CHKDSK check my primary drive (no problems), boot into Windows. And here I am asking this forum humbly...

Where did my grub loader go?

Theoretically I've got Ubuntu installed...just no way to boot into it.

---

### Post by hyper_ch on 2008-09-07
grub needs in the first booting harddisk... very likely you changed that somehow. So reinstall grub.

---

### Post by Sef on 2008-09-07
Get [Super GRUB Disk]("http://supergrubdisk.org") to install GRUB.

>  partitioned 2 GB for swap

If you have at least 1 GB ram, then swap only needs to be 1 GB.

---

