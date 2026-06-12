---
title: "Won't boot up after install ?"
date: 2013-12-23
forum: New to Ubuntu
---

### Post by aberganza1997 on 2013-12-23
I installed ubuntu 12.04 from USB to desktop when it rebooted it said press S to skip mounting or M for manual recovery but my keyboard turns off as soon as it gets to this screen ? And if I press f11 when my computer turns on all I get is the mouse icon with no way to select to boot from USB

---

### Post by vasple on 2013-12-23
Hi! In my case , this message appears when I've setup a system with encrypted home directory. It is normal since it takes some time for the encrypted partition to be mounted (usually around 3-5 sec) and after that, the system startup process continues. Is your computer stuck on that screen? have you waited a bit to see if it moves forward?

---

### Post by aberganza1997 on 2013-12-24
> **vasple said:**
> Hi! In my case , this message appears when I've setup a system with encrypted home directory. It is normal since it takes some time for the encrypted partition to be mounted (usually around 3-5 sec) and after that, the system startup process continues. Is your computer stuck on that screen? have you waited a bit to see if it moves forward?

I waited all night and it just keeps turning off and on and it doesn't get off that screen

---

### Post by Bashing-om on 2013-12-24
aberganza1997; Hi !

Tell us a bit about the machine you are installing onto. Dual booting ? .. is Windows8 involved in anyway ?

Might try:
Boot from a cold start, soon as the bios screen clears, depress and hold the shift key. Do you get the Grub boot screen ?

If so we can give further guidance to boot ubuntu.

[INDENT][INDENT]it is all in the process
[/INDENT][/INDENT]

---

### Post by whitesmith on 2013-12-24
> **aberganza1997 said:**
> I installed ubuntu 12.04 from USB to desktop when it rebooted it said press S to skip mounting or M for manual recoveryThis is a fairly common error that can be caused by a device not properly auto-mounting. Please hit S (if you can get that far) and then run```
sudo fdisk -l
```to see if all drives are accounted for. Also, you said nothing about your hardware or configuration. Just knowing if yours is dual-boot might help. Consider "trying" instead of installing. Your system's behavior might be revealing under these conditions. Cheers!

---

### Post by aberganza1997 on 2013-12-24
I have windows 8 on 1 hdd but I'm trying to install ubuntu on another hdd that had windows but on the option I put to erase everything on the hdd. Also  I can't press S because my keyboard turns off as soon as it loads in that screen.

---

### Post by whitesmith on 2013-12-24
Let me know if you can get to a virtual console (Ctrl+Alt+F2). If you can, attempt to login there and follow these instructions on the disk that originally had Windows: [http://ubuntuforums.org/showthread.php?t=267869](http://ubuntuforums.org/showthread.php?t=267869) **Be extremely careful!** This is a wipe routine that zaps everything on the HDD before creating a new filesystem, so the author's warnings should not be taken lightly. I think most likely something got left over from the previous install that is hosing this one. If these attempts fail, I'm afraid I'll have to refer you to someone with a higher pay grade than mine. Good luck!

---

### Post by aberganza1997 on 2013-12-24
Nope I can't get a virtual console is their any other way I can wipe the hard drive and install ubuntu again ?

---

### Post by whitesmith on 2013-12-24
I prefer the old fashioned way, as explained. You should be able to use gparted to eliminate and re-create the partition, and then create an ext4 (or 3) filesystem. Don't forget to edit /etc/fstab (preferably identifying the drive by UUID) to insure proper auto-mounting. I'm off to work for several days, so if this doesn't help someone else should be able to step in. Happy holidays to you and yours!

---

