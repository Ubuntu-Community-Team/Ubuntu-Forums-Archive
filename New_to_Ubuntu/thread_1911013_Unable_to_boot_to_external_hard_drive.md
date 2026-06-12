---
title: "Unable to boot to external hard drive"
date: 2012-01-18
forum: New to Ubuntu
---

### Post by Pannkakan on 2012-01-18
Heya!
I am quite new to Linux/UBuntu and has ran into a problem while installing/booting my newly installed Ubuntu 10.04.2.LTS.
Up til now I've used a 4 gb flashdrive with a mountable partition of Backtrack 5 as my source for using Linux, and I thought that it was time to take a step further and install the entire Backtrack to disk (Ubuntu 10.04 as I have understood it?).
I decided to rezise a partition of my external hard drive and install Backtrack there.
The hard drive is a TEAC HD-35PU, 250 gb, with an 12 V powersupply.

The installation went smooth, no problems what so ever. However, at the boot menu at startup, there is no external hard drive to be found. The only bootable devices listed is my internal hard drives with XP and the flash drive with Backtrack 5.
Is there anything I have done wrong during the installation?
I've read that there is a program called GRUB2 that might solve my problems, but how do I install that if I am unable to even boot the external hard drive in the first place?

I am most thankful for any help I can get. Kind regards :)

---

### Post by nipunshakya on 2012-01-18
Hi. Welcome to the forums. 
Grub is simply a boot loader package that gets installed on your MBR of machine. Without that, you won't be able to boot to linux!
I guess you didn't take care of where to install your GRUB when u were installing your Backtrack on your external hdd.

**You must install your grub2 in your external harddisk during the  installation of your backtrack so that next time you boot, your external harddisk is also seen on the menu list of grub.** 

That might be the main cause why your external harddisk isnt showing up in your grub menu.

---

### Post by Savio2010 on 2012-01-18
what was your source to install BT pen drive or DVD.

I recommend you just connect your external hdd and disconnect the other hdd and pen drive.
Do a fresh install of BT by repartitioning the external hdd from the DVD.

---

### Post by nipunshakya on 2012-01-18
> **Savio2010 said:**
> what was your source to install BT pen drive or DVD.

I recommend you just connect your external hdd and disconnect the other hdd and pen drive.
Do a fresh install of BT by repartitioning the external hdd from the DVD.

I guess there is no need to do a fresh installation. I guess there is just a need to install grub in his external harddisk drive so that next time he can see his external drive listed to grub menu too. Isn't it?

---

### Post by Savio2010 on 2012-01-18
> **Pannkakan said:**
> Heya!
..........................................................** However, at the boot menu at startup, there is no external hard drive to be found. The only bootable devices listed is my internal hard drives with XP and the flash drive with Backtrack 5.**...................................................................................

This sounded to me like he is talking about the BIOS boot menu. If it is the grub menu reinstalling grub will work for sure.

---

### Post by Pannkakan on 2012-01-18
As you said, it's in the boot menu I am unable to find the device (I am however able to find my internal hard drives (striped 500 gb WIndows XP) and the flash drive with Backtrack 5).
So a reinstall would be the proper way to do it?

EDIT: Also, I used my pen drive for the installation of Backtrack.

---

### Post by nipunshakya on 2012-01-19
Well, in that case, load your BIOS first and see if there is anything u can do anything with the BIOS settings so that u can view your external drive... Even if that won't work out, a reinstall might work.

I personally haven't installed ubuntu on an external drive, however, next time when u try to install on an external drive, [B]make sure to select your external drive when you will be managing your partition schemes. 
[/B]

Regards,WinuxUser

---

