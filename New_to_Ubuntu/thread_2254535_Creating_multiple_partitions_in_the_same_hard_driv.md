---
title: "Creating multiple partitions in the same hard drive"
date: 2014-11-27
forum: New to Ubuntu
---

### Post by hunbalbabar on 2014-11-27
Hi guys. Just wanted some help. I just started using linuxand I wanted to create multiple partitions on the same hard drive just in case I wanted to switch to another linux distribution and still keep my data. But ubuntu installation only created one partition of the entire disk. After some searching on the net I found this article [https://help.ubuntu.com/community/UbuntuDesktopLVM](https://help.ubuntu.com/community/UbuntuDesktopLVM) and I followed all the given instructions except the last ```
sudo mkfs.ext4
``` commands. Now everything is working fine. But when I do the ```
sudo fdisk -l
``` this information shows up.

> Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ef39c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    14699473     7348713   83  Linux
/dev/sda2        14699474   625137344   305218935+  8e  Linux LVM

Disk /dev/mapper/sysvg-lvswap: 7516 MB, 7516192768 bytes
255 heads, 63 sectors/track, 913 cylinders, total 14680064 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/sysvg-lvswap doesn't contain a valid partition table

Disk /dev/mapper/sysvg-lvroot: 53.7 GB, 53687091200 bytes
255 heads, 63 sectors/track, 6527 cylinders, total 104857600 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/sysvg-lvroot doesn't contain a valid partition table

Disk /dev/mapper/sysvg-lvhome: 251.3 GB, 251339472896 bytes
255 heads, 63 sectors/track, 30556 cylinders, total 490897408 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/sysvg-lvhome doesn't contain a valid partition table



Apart from this everything else is working seemingly fine. Is this something I should be worried about ? If so how can I correct it ?

---

### Post by yancek on 2014-11-27
You used LVM, Logical Volume Management which is generally not used on a standard home computer installation although it can be.  Modifying LVM is much different than a standard partition installation.  Never used it myself but you might try googling modifyin LVM partitions.

---

### Post by ajgreeny on 2014-11-27
Personally I suggest you start again as you have not yet really used your system and presumably have few personal files on it.

If I am wrong about that, my apologies; that is the way I read your post.  However, LVM adds a lot of complications to your system and in my opinion is not worth it for a standard desktop machine.

Assuming you are not using UEFI and GPT partitions, start over and first make an extended partition of the whole disk.  This givers you the option to make as many logical partitions as you want within the extended partition, ignoring the limit of 4 primary partitions that you have when using a msdos (normal) partition table.

Linux will boot from a logical partition whereas Windows will not, or not without a lot of kerfuffle, so assuming you do not have, or need windows, the complete disk-sized extended partition will not matter to you.

---

### Post by kevdog on 2014-11-27
I honestly would download and run the Gparted live CD to create your partitions. This is a Linux distribution just made to handle partitioning. It's very easy and intuitive. If your going to be possibly using more than one linux distro, I recommend a separate home and swp partition that can be shared between the installation types. Always make swp partition your last partition.

---

### Post by fantab on 2014-11-28
> **ajgreeny said:**
> Personally I suggest you start again as you have not yet really used your system and presumably have few personal files on it.

+1

LVM has a learning curve, and I wouldn't recommend it to a Linux Beginner. However, LVM has its own pros and cons and cons are only related to LVM being very complicated to use.
As a linux beginner you start with the default Ext4 filesystem on normal partiions...

The ubuntu installer only does the basic parttioning job required for installation... to have more control over your partitions you need to do it yourself.
Preferably, partition your HDD before you install ubuntu... run Ubuntu Live and 'try ubuntu'. Open Gparted and partition your disk as you need.
Then Install ubuntu, however you must choose 'Something Else' option from the *Installation Type* dialog during install to manually direct your install to said partition.

If you want to multi boot or dual boot then, don't use separate /home. Only create '/' partition of about 20-30gb. For your personal data create a simple ext4 partition to store your data. Its what I do.
I would later mount the partiton at boot with 'fstab' file.

---

### Post by hunbalbabar on 2014-11-28
Thanks for the reply guys. I think I might just have to resínstall ubuntu again. Is there someway I can still keep my current files and settings after the installation ? Because I installed a lot of softwares and moved some data... and it would be a pain to do it all over again

---

### Post by fantab on 2014-11-28
Since you will be deleting/formating partitions, it is not possible to preserve your 'current' files.
Do you have a GPT or MBR (msdos) HDD? You can check with the following:
```
sudo parted -l
```

If you have a GPT disk, then you do NOT need an Extended partition. As there is no only 4 primary partition limit.

---

### Post by hunbalbabar on 2014-11-28
Its an msdos partition table. Actually I only need 2 partitions. One for the system files and one for my personal. I guess I need to reinstall ubuntu. But thanks a lot for all your help guys.

---

### Post by ajgreeny on 2014-11-28
> **hunbalbabar said:**
> Its an msdos partition table. Actually I only need 2 partitions. One for the system files and one for my personal. I guess I need to reinstall ubuntu. But thanks a lot for all your help guys.
Actually you should really have 3 partitions in that case:
[LIST=1]
[*]The root partition, ext4, with mountpoint /, and about 25GB 
[*]Your personal files partition, which can either be done with a separate /home partition, or you can leave /home within root and make a separate /data partition, the mounting of which we will have to leave until the OS is installed. This partition can be all the rest of the disk except for swap; see 3 below. 
[*]A swap partition, probably of 2 - 4GB, though the size depends on whether you want to hibernate, and how much physical ram you have. 
[/LIST]
If hibernation is important to you come back again, tell us how much ram you have, and we can tell you how to enable hibernation on your machine.  I find that Linux boots fast enough without worrying about hibernating my system; you may feel differently.

---

### Post by hunbalbabar on 2014-11-28
Dont need hibernation. but thanks :)

---

