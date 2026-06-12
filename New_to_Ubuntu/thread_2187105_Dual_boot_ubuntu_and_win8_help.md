---
title: "Dual boot ubuntu and win8 help?"
date: 2013-11-10
forum: New to Ubuntu
---

### Post by ianhoyle on 2013-11-10
I know this is a topic that gets brought up a lot but i am really having a hard time with this..

so on my laptop (Acer Aspire M5 Ultrabook) the UEFI has to be disabled for me to boot from the USB. furthermore the way my hard drives are partitioned isnt like I have seen in any tutorials i have found. im going to post a screenshot of my partitions. 

can I just shrink my C: volume and leave the others alone and still have it all boot and function correctly?

If I try to boot from USB with UEFI enabled it says something about the USB being blocked for security. I can boot from USB if i switch to legacy BIOS mode but I worry that if I install ubuntu like that it wont play well with the bootloader... any help please?

[ATTACH=CONFIG]247726[/ATTACH]

---

### Post by fantab on 2013-11-10
Boot with Ubuntu Live DVD/USB and 'Try Ubuntu without installing'. Open Terminal [Ctrl+Alt+T], run the following and post its output here:

```
sudo parted -l
sudo fdisk -l
```

Since you have more than One HDD/SSD you may not have to shrink anything...

---

### Post by oldfred on 2013-11-10
Ultrabooks have the small SSD and usually use Intel SRT which has RAID meta-data on the drive. The RAID then confuses the installer and/or grub and prevents a valid install. Users that are primarily Windows users then install Ubuntu to hard drive and reenable SRT. But some who use Ubuntu more use the small SSD as / (root) for Ubuntu to make it fast.

Be sure to create good backups before doing anything, including the efi partition and the main Windows install.

        Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)


 Ubuntu on hard drive, re-enable SRT post #19 details
[http://ubuntuforums.org/showthread.php?t=2129157](http://ubuntuforums.org/showthread.php?t=2129157)
> Disable the RAID, it was using the Intel rapid management thingy and telling it to disable the acceleration or the use of the SSD. If you have a different system, just disable the RAID system then install Ubuntu. Once installed you can then re-enable it.
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
> You will need to use the dmraid command prior to running the Ubuntu Installer so that it will be able to see the partitions on the drive because otherwise with the raid metadata in place it will see the drive as part of a raid set and ignore its partitions.

See lots more info in link in my signature.

---

### Post by efrilinux on 2013-11-11
> **fantab said:**
> Boot with Ubuntu Live DVD/USB and 'Try Ubuntu without installing'. Open Terminal [Ctrl+Alt+T], run the following and post its output here:

```
sudo parted -l
sudo fdisk -l
```

Since you have more than One HDD/SSD you may not have to shrink anything...

Yes, This is a good idea.

---

### Post by ianhoyle on 2013-11-11
thanks for your replys everyone! I was able to fix my machine using the steps listed in a post on another page. 
[http://superuser.com/questions/460762/how-can-i-repair-the-windows-8-efi-bootloader](http://superuser.com/questions/460762/how-can-i-repair-the-windows-8-efi-bootloader)

---

