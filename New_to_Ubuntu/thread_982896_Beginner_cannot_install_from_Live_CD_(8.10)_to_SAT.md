---
title: "Beginner cannot install from Live CD (8.10) to SATA (only drive, dual w/ WinXP)"
date: 2008-11-15
forum: New to Ubuntu
---

### Post by MissouriKnight on 2008-11-15
I am trying to install 8.10 onto my SATA drive, which already contains WinXP. I previously used Partition Magic in Windows to set up some partitions for Linux. When I try to install Ubuntu 8.10 from within the Live CD, within Linux, not Windows, I get to the screen that shows partitions, and no partitions show up.

Can anyone help me? :confused:

MissouriKnight ](*,)

---

### Post by MissouriKnight on 2008-11-15
Bump

---

### Post by shifty_powers on 2008-11-15
i had the same problem. rather than going through the livecd, when you boot up and it goes to the intitial menu, use the install option rather than boot the cd.

iirc, it is something to do with not being able to detect mounted partitions, or something along those lines.

anyways, the abpve solved the probelm for me...

---

### Post by oilchangeguy on 2008-11-15
> **MissouriKnight said:**
> I am trying to install 8.10 onto my SATA drive, which already contains WinXP. I previously used Partition Magic in Windows to set up some partitions for Linux. When I try to install Ubuntu 8.10 from within the Live CD, within Linux, not Windows, I get to the screen that shows partitions, and no partitions show up.

Can anyone help me? :confused:

MissouriKnight ](*,)

your post does not make much sense. first you don't need to use third party partition apps. the ubuntu cd has a partition manager included. now for the not making sense part, you're trying to install 8.10 from within the live cd, from within linux?????????????????????? and you get to the screen that shows partitions, and there are none???????????????????? read this:
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by MissouriKnight on 2008-11-15
Shifty_Powers, thanks for the advice.

I will try that. :D

MissouriKnight

---

### Post by shifty_powers on 2008-11-15
cool, np's.

if all else fails, download the alternate cd, it is not a livecd and has a text based installer. it is intended as a failsafe in these sitatuions...

---

### Post by ugm6hr on 2008-11-15
> **MissouriKnight said:**
> I am trying to install 8.10 onto my SATA drive, which already contains WinXP. I previously used Partition Magic in Windows to set up some partitions for Linux. When I try to install Ubuntu 8.10 from within the Live CD, within Linux, not Windows, I get to the screen that shows partitions, and no partitions show up.

Delete those partitions you created to leave "unallocated / empty space"

Then try again.

If you don't understand Linux partitions, best to use the "Use largest free space" guided install option.

If you do understand partitions - Ubuntu requires at least 1 ext3 & 1 linux swap partition.

---

### Post by Duck2006 on 2008-11-15
[http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm)

---

