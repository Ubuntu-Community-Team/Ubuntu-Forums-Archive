---
title: "Installed Ubuntu on MircoSD, now can't format it or anything"
date: 2013-02-24
forum: New to Ubuntu
---

### Post by pdub110 on 2013-02-24
I have a 64GB microSD for my Surface Pro, created a bootable USB drive for Ubuntu 12.10, got my Surface to boot to Ubuntu via USB and then ran the installer on the 64GB microSD but couldn't get my Surface Pro to boot off of it. 

So now i'm trying to create a bootable microSD card but the microSD card only see's 200MB of the 64GB card no matter what OS I put it on, including Ubuntu.  Is there a way to re-format the microSD card?  not sure what happened but I want to re-format it, and create a bootable Ubuntu via mircoSD.

Any advice is greatly appreciate.

---

### Post by leclerc65 on 2013-02-24
You can download Parted Magic then use its Partition Editor (Gparted) to fix your microSD.

---

### Post by pdub110 on 2013-02-24
> **leclerc65 said:**
> You can download Parted Magic then use its Partition Editor (Gparted) to fix your microSD.

thank you for the quick reply, i'll give it a try.

---

### Post by pdub110 on 2013-02-24
> **leclerc65 said:**
> You can download Parted Magic then use its Partition Editor (Gparted) to fix your microSD.
 
Do I do this in Ubuntu?  or can i do this from windows?  I downloaded it but it's an iso file.

---

### Post by leclerc65 on 2013-02-24
You burn it as a bootable CD. If your computer doesn't have a CD/DVD drive , try to burn it on a USB (my favorite program to do that is YUMI (Windows 7, also free).

---

### Post by mastablasta on 2013-02-25
> **pdub110 said:**
> Do I do this in Ubuntu? or can i do this from windows? I downloaded it but it's an iso file.
 
 
gparted is included in Ubutnu. if not you can install it from software center.

---

### Post by debodas on 2013-02-25
> **pdub110 said:**
> Do I do this in Ubuntu?  or can i do this from windows?  I downloaded it but it's an iso file.
Download Gparted from the software center, then you can run it as a program from within Ubuntu.

Note - to format the Micro SD card, you will need to unmount the SD card, which you can do easily from the file manager, by right clicking on the usb drive icon and selecting unmount.

---

### Post by audiomick on 2013-02-25
> **mastablasta said:**
> gparted is included in Ubutnu. if not you can install it from software center.

It is not there by default on an Ubuntu install, but is included by default on the installer CD / USB. And yes, it can be installed easily from the software centre.

---

### Post by oldfred on 2013-02-25
Is this Windows 8 or Windows RT?

If RT and maybe all Surface versions of Windows 8 have locked UEFI that will not boot anything else.

       [http://linux.slashdot.org/story/12/12/30/2340208/why-linux-on-microsoft-surface-is-a-tough-challenge](http://linux.slashdot.org/story/12/12/30/2340208/why-linux-on-microsoft-surface-is-a-tough-challenge)

---

