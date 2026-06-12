---
title: "How to undo (or remount) the unmount of my Windows OS partition"
date: 2013-04-28
forum: New to Ubuntu
---

### Post by yixiaxian on 2013-04-28
Background: I install Ubuntu 12.04LTS alongside with my Win 7 on a same disk drive. There are 3 primary partitions and 1 external partition. The Win 7 is on /dev/sda1, /dev/sda2, /dev/sda3, and Ubuntu is on /dev/sda5, /dev/sda6. After installation I see there is a disk in the left panel called /OS and all my files in Win 7 disk C: are there so I'm very happy. I right click the disk and see this "unmount" option. I thought it means to "unpin" (like what win7 do, I'm sorry I should get to know what it means before I make any stupid action) but after I unmount it, I can't find it anymore in the filesystem.

Problem want to be solved: How can I mount the disk C: back to my filesystem so that I can still access those files from Ubuntu?

---

### Post by yixiaxian on 2013-04-28
I searched on the board and see some similar mistakes so I try to put in the code as others suggested. Below is the result. Could anyone tell me what I should do next? Thank you so much!

```
chong@chong-Ubuntu:~$ sudo fdisk -ls
[sudo] password for chong: 

Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders, total 488281250 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x50000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63      240974      120456   de  Dell Utility
/dev/sda2   *      241664    21831679    10795008    7  HPFS/NTFS/exFAT
/dev/sda3        21831680   433240063   205704192    7  HPFS/NTFS/exFAT
/dev/sda4       433242110   488280063    27518977    5  Extended
/dev/sda5       484433920   488280063     1923072   82  Linux swap / Solaris
/dev/sda6       433242112   484433919    25595904   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x18337581

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63  1953523119   976761528+  42  SFS



```

The /dev/sdb is a secondary hard drive which I assume has nothing to do with this problem. (But it'll be great if I could also mount that one, too!)

```

chong@chong-Ubuntu:~$ sudo sfdisk -d
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size=   240912, Id=de
/dev/sda2 : start=   241664, size= 21590016, Id= 7, bootable
/dev/sda3 : start= 21831680, size=411408384, Id= 7
/dev/sda4 : start=433242110, size= 55037954, Id= 5
/dev/sda5 : start=484433920, size=  3846144, Id=82
/dev/sda6 : start=433242112, size= 51191808, Id=83
# partition table of /dev/sdb
unit: sectors

/dev/sdb1 : start=       63, size=1953523057, Id=42
/dev/sdb2 : start=        0, size=        0, Id= 0
/dev/sdb3 : start=        0, size=        0, Id= 0
/dev/sdb4 : start=        0, size=        0, Id= 0



```


> **yixiaxian said:**
> Background: I install Ubuntu 12.04LTS alongside with my Win 7 on a same disk drive. There are 3 primary partitions and 1 external partition. The Win 7 is on /dev/sda1, /dev/sda2, /dev/sda3, and Ubuntu is on /dev/sda5, /dev/sda6. After installation I see there is a disk in the left panel called /OS and all my files in Win 7 disk C: are there so I'm very happy. I right click the disk and see this "unmount" option. I thought it means to "unpin" (like what win7 do, I'm sorry I should get to know what it means before I make any stupid action) but after I unmount it, I can't find it anymore in the filesystem.

Problem want to be solved: How can I mount the disk C: back to my filesystem so that I can still access those files from Ubuntu?

---

### Post by Impavidus on 2013-04-28
The best way to mount windows file systems in my opinion is putting them in /etc/fstab, so they will automatically mount when you boot. Read this: [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
There is an example on ntfs partitions, which is what you'll need.

Mounting your windows C partition is not always save. Writing to the C partition of win7 may corrupt windows. You can savely mount it read-only. Most people who dual-boot use a separate shared ntfs partition just for data.

Your /dev/sdb1 is an SFS partition. This is a dynamic windows partition. Ubuntu cannot read it, so you won't be able to mount it.

---

### Post by fantab on 2013-04-28
Did you remove the Windows partition from the Launcher? Open "FILES" the ubuntu file manager and it should list all the partitions under 'Devices'. Tell us what you see...

---

### Post by Mark Phelps on 2013-04-28
When you unmount a filesystem you will not be able to see it anymore -- that's normal behaviour.  So, you didn't do anything bad to it when you unmounted it.

As to converting your "sdb" drive from Dynamic Disk to Basic Disk -- you will have to do this in Windows, as Linux can't understand Dynamic Disks.  There are Windows tools that can do this like: Minitool Partition Wizard and Easus Partition Master.

---

### Post by Mopar1973Man on 2013-04-28
> I right click the disk and see this "unmount" option. I thought it means  to "unpin" (like what win7 do, I'm sorry I should get to know what it  means before I make any stupid action) but after I unmount it, I can't  find it anymore in the filesystem.

Sounds normal. When you typically unmount a drive it like unplugging it logically.

> Problem want to be solved: How can I mount the disk C: back to my filesystem so that I can still access those files from Ubuntu?                 

Fstab would be the option to forcably mount the drives and keep them mounted. 
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

I personally use Webmin ([www.webmin.com]("http://www.webmin.com")) for my control panel funtion of Ubuntu. Much easier for a Noobie. But if you want you can still edit the fstab file yourself too.

---

### Post by yixiaxian on 2013-04-28
Thank you! So from what I understand, it's actually good to unmount the C drive, but in order to exchange data between two systems, I'd better have another ntfs partition and mount that one. Is that right?

---

### Post by yixiaxian on 2013-04-28
Yes I think I "remove" the Windows partition from the Launcher. I open the "FILES" and I see "Home" and "File System" on the left panel, before I unmount there is another one called "OS"...

---

### Post by yixiaxian on 2013-04-28
> **Mark Phelps said:**
> When you unmount a filesystem you will not be able to see it anymore -- that's normal behaviour.  So, you didn't do anything bad to it when you unmounted it.

As to converting your "sdb" drive from Dynamic Disk to Basic Disk -- you will have to do this in Windows, as Linux can't understand Dynamic Disks.  There are Windows tools that can do this like: Minitool Partition Wizard and Easus Partition Master.

Thank you for your suggestion! I'll try them.

---

### Post by fantab on 2013-04-28
> **yixiaxian said:**
> Yes I think I "remove" the Windows partition from the Launcher. I open the "FILES" and I see "Home" and "File System" on the left panel, before I unmount there is another one called "OS"...

What happens when you click the "OS" in "Files"? Does it open that folder? 
If it opens that folder, and if you are able to boot Windows then you are OK. There is nothing to worry. Its normal. We can mount and unmount partitions from "Files" Left Panel by CLICKING on it.

It not adviseable to use Windows c: partition from Linux/Ubuntu. However I use it with WINE to play certain games on Ubuntu. If you have a need to share files/DATA between Ubuntu and Windows then you can use any NTFS partition to do so, except c:

---

