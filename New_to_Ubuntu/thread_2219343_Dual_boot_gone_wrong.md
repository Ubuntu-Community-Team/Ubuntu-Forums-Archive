---
title: "Dual boot gone wrong"
date: 2014-04-23
forum: New to Ubuntu
---

### Post by Mueez_Aizaz on 2014-04-23
I was running Windows / on my laptop and decided to create  dual boot with ubuntu 14.04 LTS. I created the bootable usb and ran  ubuntu and when I started installing it i did nt understand the  partitioning part. I guess i made some serious mistakes there as now my  windows will not boot. Every time i restart ubuntu starts automatically.  I ran boot repair but it didnt do anything. It gave me this link [http://paste.ubuntu.com/7317775/](http://paste.ubuntu.com/7317775/)  and said this might help on forums. Can anyone help me with this. I  really want my Windows back even if I lose ubuntu that is no issue.

---

### Post by suprleg on 2014-04-23
So when you restart the laptop you're not presented with any kind of boot manager such as grub? Do you remember creating a linux partition or the installer warning that _all_ the disk's data would be lost?
Do you have a recovery CD or DVD, recovery partition within the disk? 
Open a terminal, ctrl-atl-t, and try running: "sudo fdisk -l","sudo blkid" or "df -Th" and see if the windows partition is still present.

Looking at: [http://paste.ubuntu.com/7317775/](http://paste.ubuntu.com/7317775/) it would seem you hopefully didn't re-partition the entire 500g..

---

### Post by oldfred on 2014-04-24
You are only showing Linux partitions, no NTFS partitions for Windows.
Or it looks like you totally erased Windows.

Do you have a full image backup of Windows? 
Do you have a image reinstall set of DVDs? 
Vendors do not ship DVDs set to install anymore. They expect you to make your own set and it is not a full installer, but just an image of hard drive as purchased.
Some vendors will ship a DVD set for a nominal charge. Others will not. But worth checking.
Or you can purchase a new full Windows install DVD set.

---

### Post by Impavidus on 2014-04-24
You have a 20GB /boot partition (which is very large), a 5GB / partition (tiny) and 475GB unallocated space. Windows is gone. Most Windows files are probably still present in the unallocated space, so if you didn't have good backups may still be able to recover much of it. Windows itself has to be recovered from a backup/disk image or reinstalled.

---

