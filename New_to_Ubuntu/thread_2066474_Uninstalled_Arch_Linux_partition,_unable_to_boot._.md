---
title: "Uninstalled Arch Linux partition, unable to boot. Have Crunchbang LiveCD. GRUB err 22"
date: 2012-10-04
forum: New to Ubuntu
---

### Post by duodecillian on 2012-10-04
Hello, it appears Ive messed up royally. I'll attempt to keep this as concise as possible.


[LIST]
[*]Had windows7/Arch Linux installed
[*]Wanted to switch from Arch over to Ubuntu
[*]Deleted all arch linux partitions and am left with unallocated space
[*]Rebooted computer and encounted syslinux errors(No configuration UI directive found)
[*]If I try to boot USB-HDD I get GRUB error 22
[*]I can boot from my CrunchBang LiveCD (On it now)
[*]Fairly unfamiliar with linux, so if you could explain things to me as such. It would mean a ton.
[/LIST]
In other threads I was looking at, it was asked to post the results of **fdisc -l** so here they are:
```
Disk /dev/sda: 1000 GB, 1000202273280 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System 
/dev/sda1   *           1          13      104391    7  HPFS/NTFS
Warning: Partition 1 does not end on cylinder boundary.
/dev/sda2              13      102020   819371227    7  HPFS/NTFS
Warning: Partition 2 does not end on cylinder boundary.
/dev/sda3          102020      121602   157292415    5  Extended
Warning: Partition 3 does not end on cylinder boundary.

Disk /dev/sdb: 500 GB, 500105249280 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System 
/dev/sdb1   *           1       60800   488375968    7  HPFS/NTFS

Disk /dev/sdc: 1 GB, 1998743040 bytes
255 heads, 63 sectors/track, 243 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System 
/dev/sdc1   *           1         244     1959898    c  FAT32 LBA
Warning: Partition 1 does not end on cylinder boundary.
Warning: Unable to open /dev/fd0 read-write (Read-only file system).  /dev/fd0 has been opened read-only.
Error: /dev/fd0: unrecognised disk label
Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0 has been opened read-only.
Error: Invalid partition table - recursive partition on /dev/sr0.
root@crunchbang:/home/crunchbang# 

```


Anything that could help means a ton, also. If you could please be patient with me, as I may not understand things resulting in what seems to be many stupid questions.

Thank you in advance.

---

### Post by NikTh on 2012-10-04
Hi , 

I did not look the results of commands you provided , I just looked in this 
> **duodecillian said:**
> 

[LIST]
[*]Had windows7/Arch Linux installed
[*]Wanted to switch from Arch over to Ubuntu
[*]**Deleted all arch linux partitions and am left with unallocated space**
[*]Rebooted computer and encounted syslinux errors(No configuration UI directive found)
[*]If I try to boot USB-HDD I get GRUB error 22
[*]I can boot from my CrunchBang LiveCD (On it now)
[*]Fairly unfamiliar with linux, so if you could explain things to me as such. It would mean a ton.
[/LIST]
You deleted Arch linux = you deleted bootloader. So no bootloader is installed in your HDD right now. 



What I suggest. 



Boot from the DVD of windows and fix mbr. How you can do that ? 



See here : [http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)


When you get in **5th step** (with command prompt) **STOP** , do not continue with this guide. 


Just give these 2 commands 

```
bootrec /fixmbr
```and
```
bootrec /fixboot
```DONE. 



Reboot your system (remove the CD/DVD)  and it will load Windows directly. 



Then you can do anything you want. 


Thanks

---

### Post by robgraves on 2012-10-04
You stated you wanted to install ubuntu in lieu of Arch Linux.  So I'm assuming ultimately you are going to be doing an Ubuntu installation on this PC.  

If you happen to already have an Ubuntu Live CD, you can just simply install Ubuntu and when it installs GRUB, it will recognize windows and add it.

---

### Post by puntigamer on 2012-10-05
This live tool used to fix my grub problems: [http://www.supergrubdisk.org/rescatux/](http://www.supergrubdisk.org/rescatux/) Just boot it from a pendrive and follow the instructions ;)

Good luck with Ubuntu!

---

