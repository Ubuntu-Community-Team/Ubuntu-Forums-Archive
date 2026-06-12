---
title: "Partition Issues / 64bit 11.04"
date: 2011-10-09
forum: New to Ubuntu
---

### Post by letsrollusafa11 on 2011-10-09
First off, I apologize if this isn't in the correct area but I figured this was a newbie type question. My issue is this, I'm installing the latest ubuntu 64bit software and I had the issue of it saying I needed a minimum of 2.5gb for one of the partitions, I went into windows and deleted the linux partitions and tried reinstalling. I got the slider bars which allow you to choose the partition size, so this time I slid it to about 5gb (small I understand but definitely over 2.5gb) I continued on with the installation and the same error came up saying one of the partitions is below the 2.5gb threshold...so at this point I'm at a loss and have no idea what's going on. Any help would be awesome. Thanks!!

(And yes I have a 64bit processor)

Also, I've looked around and most people ask for the sudo fdisk -l readout so I've added that as well. Thank you so much.

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd9b3496e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1342    10775552   1c  Hidden W95 FAT32 (LBA)
/dev/sda2            1342        1912     4580353    5  Extended
/dev/sda3   *        1912       38914   297212248    7  HPFS/NTFS
/dev/sda5            1342        1525     1471488   83  Linux
/dev/sda6            1526        1552      210944   82  Linux swap / Solaris
/dev/sda7            1552        1912     2895872   83  Linux

Disk /dev/sdb: 16.0 GB, 16001269760 bytes
5 heads, 32 sectors/track, 195328 cylinders
Units = cylinders of 160 * 512 = 81920 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          51      195328    15622208    c  W95 FAT32 (LBA)

---

### Post by Quackers on 2011-10-09
Welcome to UF:-)

A couple of things first.
You don't say which version of Windows you are using.
It is not normally a good idea to change Linux partitions with Windows software.
It is not normally a good idea to change Windows partitions with the Ubuntu installer.
Use Windows tools to change Windows partitions and use Linux tools to change Linux partitions.

You are showing 2 Linux partitions (sda5 and sda7) and a swap partition (sda6). Do you know what is in the 2 Linux partitions?

For further clarification can you boot from the Ubuntu live cd/usb and select "try ubuntu" and when the desktop loads please open gparted and post a screenshot of its window.

---

### Post by letsrollusafa11 on 2011-10-09
A couple of things first.
You don't say which version of Windows you are using. **Windows 7 Personal 64 bit**
It is not normally a good idea to change Linux partitions with Windows software. **Gotcha thanks!**
It is not normally a good idea to change Windows partitions with the Ubuntu installer. **Gotcha thanks!**


You are showing 2 Linux partitions (sda5 and sda7) and a swap partition (sda6). Do you know what is in the 2 Linux partitions? - The only thing I can see is that I went through the installation process and sometimes it lets me use the slider and sometimes it didn't but it creates all these partitions in the installation process and thats where they come from, not sure. Sorry I'm not giving better info.

For further clarification can you boot from the Ubuntu live cd/usb and  select "try ubuntu" and when the desktop loads please open gparted and  post a screenshot of its window.





Thank you so much for your help!!!
-Chris

---

### Post by Quackers on 2011-10-09
Is the Ubuntu installer still running? If so, please quit the installation.

Do you know how your extended partition (sda2) got in between your recovery partition and your Windows partition?

sda2, which is your extended partition is not 5GB - it is 4.37GB
sda5, which is your first Linux partition and appears to be the installer's target partition (for installation) is only 1.40GB in size. This is not big enough and is your source for the error messages.
Your swap partition is very small.

My memory may be wrong, but doesn't Ubuntu 11.04 need 4GB to install in to? Maybe that's 11.10, not sure but I know my 11.04 installation takes up 4GB.

---

### Post by bob53124 on 2011-10-09
Try installing via wubi or wait untill the 13th and download 11.10 it would save you updating aswell (11.10 might work better) and also shrink the partitions in windows and then in ubuntu use the free space created

---

### Post by letsrollusafa11 on 2011-10-09
I'll be honest I'm not sure how that happened. I tried freeing up some space from the recovery partition ( prolly not smart) but what happens is mid-installation I get the "one of your partitions is not the minimum 2.5gb" and then soon after that the installation fails saying "not enough free space" . Im just confused because I never chose to have such small partitions ( for example the partition u said is giving me heartache)

---

