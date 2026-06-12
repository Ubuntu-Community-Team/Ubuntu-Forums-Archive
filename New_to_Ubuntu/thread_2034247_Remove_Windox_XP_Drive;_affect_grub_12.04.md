---
title: "Remove Windox XP Drive; affect grub? 12.04"
date: 2012-07-28
forum: New to Ubuntu
---

### Post by omac on 2012-07-28
Hi all, I wanted to ask advice before proceeding, as Grub has wrecked an old hard drive of mine.

I have a 2 hard drive system, the 1st is ubuntu 12.04 (on a SATA 1TB), and the 2nd is Windows XP (on an old IDE 500gb).  All is fine, and initial grub screen lets me choose which to boot, ubuntu 12.04 is default.  In the Bios, the Ubuntu SATA 1TB is the first drive.

I plan to remove the Windows XP Hard Drive.

Will this cause problems when I reboot, as there will no longer be a Windows XP Hard Drive?

I'm asking because when I was using the Ubuntu Maverick version in one drive, and Windows XP on the other, it somehow wrecked the Maverick hard drive little by little (not sure how) until it could no longer function, and it wasn't even a year old.  Fortunately, I was able to get a free replacement.

Currently, Ubuntu recognizes the Ubuntu 12.04 1TB Drive as SDB, and it recognizes the Windows XP 500GB Drive as SDA.

I'm hoping Grub will just automatically recognize the Windows XP disk missing and remove the option.

Can I remove the Windows XP Hard Drive without any need for concern?

Thanks.  :)

---

### Post by Laiquendi on 2012-07-28
If grub boot loader is on the drive you wish to keep, then there should be no problem. But I'm not 100% sure though.
You can test it by unplugging the second drive, and then booting the computer.

---

### Post by NikTh on 2012-07-28
Hi, 
take a look at here --> [https://help.ubuntu.com/community/OS-Uninstaller](https://help.ubuntu.com/community/OS-Uninstaller)

Thanks

---

### Post by kc1di on 2012-07-28
Normally grub is installed on sda MBR so if you remove SDA you may have to reinstall grub on the 1 TB HD.  

Grub can not distory an HD by the way there must be other factors at work there. 

Before you remove the SDA HD go to this [page]("https://help.ubuntu.com/community/Boot-Repair") and download and burn a copy of boot repair to a cd to have on hand it will make reinstalling grub easier.
Cheers!

---

### Post by omac on 2012-07-28
Laiquendi, NikTh, & kc1di,

Thank you for your replies, much appreciated.

I will read through those links very carefully before proceeding, just in case, and it can't hurt to burn a copy of the boot repair.  :)

---

### Post by omac on 2012-07-29
Just an update.

I downloaded the boot rescue disk from the link and burned it on a DVD, just in case.

I turned off the PC, removed the Wndows XP hard drive, then turned on the computer.

No problems.

Grub still gives Windows XP as one of the boot options, even though the drive isn't there, but it hasn't seemed to affect the computer in any way.

Guys, thanks for all the help, and I'll try to change the status of this to solved.  :)

---

