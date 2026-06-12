---
title: "Grub Boot not installing"
date: 2012-09-17
forum: New to Ubuntu
---

### Post by ritergal on 2012-09-17
I'm trying to install a freshly downloaded copy of Ubuntu 12.04.1 onto a four-year-old Acer Aspire One netbook that uses an 8GB flash card rather than a standard hard-drive. I had 11.10 installed, but forgot my passwword, so I'm starting over with a USB drive installation. 

Ubuntu runs fine from the USB drive, but when I go through the installation process, the final step tells me the Grub Boot didn't install. I tried telling it to install it on another device, but that didn't work. 

The Installation Type window offers me two choice: "Erase Ubuntu 12.04.1 LTS and reinstall" or "Something else." (Originally that was "Erase 11.10 ..."

After three tries with the first, even freshly installing on the USB drive, I switched to the "Something else" installation routine. I have three options for the device: 
1) /dev/sda (default option)
2) /dev/sda1 ext4   size: 7006 MB  used: 2624 MB
3) /dev/sda5 swap   size: 1060 MB  used: 0 MB

For devices, I have three choices:
A) /dev/sda  ATA SSDPAMM0008G1 (8.1 GB)
B) /dev/sda 1 Ubuntu 12.04.1 LST (12.04)
C) /dev/sdb

I have tried every combination of these and always get this message: "No root file system is defined. Please correct this from the partitioning menu. 

I'm stuck. Please help.

---

### Post by Elfy on 2012-09-17
*Thread moved to **Absolute Beginner Talk**.*

---

### Post by newb85 on 2012-09-17
> **ritergal said:**
> I'm trying to install a freshly downloaded copy of Ubuntu 12.04.1 onto a four-year-old Acer Aspire One netbook that uses an 8GB flash card rather than a standard hard-drive. I had 11.10 installed, but forgot my passwword, so I'm starting over with a USB drive installation. 

Ubuntu runs fine from the USB drive, but when I go through the installation process, the final step tells me the Grub Boot didn't install. I tried telling it to install it on another device, but that didn't work. 

The Installation Type window offers me two choice: "Erase Ubuntu 12.04.1 LTS and reinstall" or "Something else." (Originally that was "Erase 11.10 ..."

After three tries with the first, even freshly installing on the USB drive, I switched to the "Something else" installation routine. I have three options for the device: 
1) /dev/sda (default option)
2) /dev/sda1 ext4   size: 7006 MB  used: 2624 MB
3) /dev/sda5 swap   size: 1060 MB  used: 0 MB

For devices, I have three choices:
A) /dev/sda  ATA SSDPAMM0008G1 (8.1 GB)
B) /dev/sda 1 Ubuntu 12.04.1 LST (12.04)
C) /dev/sdb

I have tried every combination of these and always get this message: "No root file system is defined. Please correct this from the partitioning menu. 

I'm stuck. Please help.

Reverse order:

For devices, you should choose option "A", which is your 8GB SSD.

The first list you gave is not a list of options.  It's the list of existing partitions.  I assume you want to do a fresh install with nothing else on the SSD (practically your only option with 8GB limit).  

Try the following:

Select sda1 and hit "Change..."
Use as > Ext4 journaling file system
Mount point > /
OK

Select sda5 and hit "Delete"
(If it asks for confirmation, hit yes.)

Select the free space and hit "Add"
Use as > Swap
OK

Then hit "Install Now".

---

### Post by ritergal on 2012-09-17
I tried yet another install, overwriting what was there. Device A was the only one available, so I used it and let it do its thing -- no different from before. But this time it worked. Who knows? Thanks for the suggestion. I didn't see it before I tried again, but perhaps it will help someone else.

---

### Post by newb85 on 2012-09-17
> **ritergal said:**
> I tried yet another install, overwriting what was there. Device A was the only one available, so I used it and let it do its thing -- no different from before. But this time it worked. Who knows? Thanks for the suggestion. I didn't see it before I tried again, but perhaps it will help someone else.

Glad you got it working.  Please mark this thread as Solved.

---

### Post by Galdov on 2012-09-17
happened the same to me with Debian 6 Xfce+Lxde version, but besides he wont install the kernel, it says is not avaiable from repositories (wtf, it should be in the CD right?), and then says that couldnt install the grub or lilo, weird...

---

