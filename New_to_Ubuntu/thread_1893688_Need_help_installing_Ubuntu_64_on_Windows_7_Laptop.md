---
title: "Need help installing Ubuntu 64 on Windows 7 Laptop"
date: 2011-12-10
forum: New to Ubuntu
---

### Post by EndemicTruth on 2011-12-10
Hey guys, 

       I am new here so be kind to me.[-o< I am trying to find out the best way to install Ubuntu 64 on my Windows 7 laptop. I made a 100 GB partition, and installed Ubuntu on it, but when I restart the laptop I get no option to choose which partition I boot from; it just goes straight into Windows desktop. I searched for this question on the forums but to no avail. Anyone got any tips? :confused:


Thanks

---

### Post by lechien73 on 2011-12-10
Hi and welcome to the forums,

To help us solve your issue, could you please boot from a LiveCD or LiveUSB.

Then download the boot info script from here: [http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

Follow the instructions at that link to create a RESULTS.txt file, and post the contents of the file here between CODE tags (the **#** icon on the toolbar).

That will help us to see your hard drive layout and if grub (the bootloader) is installed anywhere.

---

### Post by Chaz46 on 2011-12-10
When you say you installed into your 100GB partition how did you install it? From a LIveUSB?

---

### Post by ilikelinuxitisthebest on 2011-12-10
what was your method of installation?

---

### Post by Bucky Ball on 2011-12-10
Boot from the Ubuntu CD again and 'Try Ubuntu'. Open Synaptic Package Manager and search for and install boot-repair. Run it. When it tells you grub fixed, reboot. Should be that easy. I'm presuming you are using 11.10? This seems to happen a bit and this fixes it (generally) without much fuss at all.

Other thing, when you boot, try hitting escape (or could be shift) and see if that brings up the grub instead of booting Win.

---

### Post by lolpenguin on 2011-12-10
Enter your BIOS' boot menu and select the partition GRUB is installed. GRUB should load with and Ubuntu with Linux x.x.x-x option.

---

### Post by EndemicTruth on 2011-12-11
Thanks for all the tips guys. Haven't installed grub yet (not familiar with what that is) but will double check my procedures. I burned the ubuntu 64 ISO to a DVD using IMGburn and just went straight through the install. If I install this 'grub' then will it allow me to pick which partition (Win7 or Ubuntu) I can boot? :P

---

### Post by EndemicTruth on 2011-12-11
I rebooted and selected "Try Ubuntu" but can't find Synaptic Packet Manager in the search... any ideas?

---

### Post by Jagoly on 2011-12-11
synaptic is no longer included, since 11.10.

Ubuntu software center can serve the same purpose.

---

### Post by linuxman94 on 2011-12-11
Synaptic isn't on the cd because it has been removed from the default installation.  

You noted that you haven't installed grub.  The ubuntu installer should have installed grub by itself, unless you told it not to.  On the live CD, can you run this script

[Boot Info Script]("http://dl.dropbox.com/u/7800678/boot_info_script.sh")

Save it on the desktop.  Open a terminal (search for it in the dash) and put in:

```
sudo bash ~/Desktop/boot_info_script.sh
```Post the contents of results.txt (it'll be on the desktop) in code tags (# sign in editor).

---

### Post by EndemicTruth on 2011-12-11
> **Jagoly said:**
> synaptic is no longer included, since 11.10.

Ubuntu software center can serve the same purpose.

No "Boot-Repair" available there... still can't get this figured out :(

---

### Post by linuxman94 on 2011-12-11
Please see my post.

---

### Post by mastablasta on 2011-12-11
> **EndemicTruth said:**
> No "Boot-Repair" available there... still can't get this figured out :(

following instructions blindly can make things worse. 

please post the results.txt of boot info script so that people can help you. it's the only way we can know what the configuration of boot is like (what boots first, what is where etc).

---

### Post by EndemicTruth on 2011-12-11
> **mastablasta said:**
> following instructions blindly can make things worse. 

please post the results.txt of boot info script so that people can help you. it's the only way we can know what the configuration of boot is like (what boots first, what is where etc).

Gotcha, here are mein results: 


                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda5 starts 
                       at sector 2048.
    Operating System:  
    Boot files:        

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048    31,459,327    31,457,280  27 Hidden NTFS (Recovery Environment)
/dev/sda2          31,664,128   241,379,327   209,715,200   f W95 Extended (LBA)
/dev/sda5          31,666,176   241,379,327   209,713,152   7 NTFS / exFAT / HPFS
/dev/sda3    *    241,379,328   976,769,023   735,389,696   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        04BEBDE1BEBDCC04                       ntfs       
/dev/sda3        7EB4B5ABB4B56675                       ntfs       
/dev/sda5        0E9EB5A09EB5812F                       ntfs       Energon Reserves

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


___________ 

Edit: I think I may have solved it... will report back!

---

### Post by linuxman94 on 2011-12-11
Looks like you either didn't install Ubuntu or you forced it to install on an NTFS partition.  You shouldn't use an NTFS partition for the install because it is not the file system native to Ubuntu.  Boot from the live cd/usb and install again, but tell it to replace what is on the 100 GB partition.  That will get you up and running.

Let us know if you have any questions.

---

### Post by Bucky Ball on 2011-12-11
No Ubuntu installed there. Not aware that you can install Ubuntu (or any other Linux OS) on an NTFS partition, Linuxman94. News to me. ;)

---

### Post by oldos2er on 2011-12-11
> **EndemicTruth said:**
> Thanks for all the tips guys. Haven't installed grub yet (not familiar with what that is) but will double check my procedures. I burned the ubuntu 64 ISO to a DVD using IMGburn and just went straight through the install. If I install this 'grub' then will it allow me to pick which partition (Win7 or Ubuntu) I can boot? :P

If you didn't boot the CD after burning but ran it from inside Windows, you have a Wubi install. [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
At that URL, look under the heading Wubi Support Forum for grub help.

---

