---
title: "Problem understanding partitions and device files"
date: 2018-09-12
forum: New to Ubuntu
---

### Post by hirno93 on 2018-09-12
So as i understand it you can list the partitions with fdisk -l in /dev and i have sda1 as my main partition. 

But how i can view which device file connects to this partition? google tells me that that the device files are listed under /dev but how do i know which one belongs to sda1?

---

### Post by The Cog on 2018-09-12
In /dev you will find sda with represents the entire disk, sda1 which represents the first partition, sda2, 3, 4 the second third and fourth partitions (if they exist in the partition table). 
For msdos partition tables, sda5 will represent the first logical partition and so on. 

Actually, the command **lsblk** gives a nice representation of the disks and partitions.

---

### Post by hirno93 on 2018-09-12
so sda is the device file for sda2? or am i missunderstanding?

---

### Post by oldfred on 2018-09-12
You should not have to worry about it.
But if you want to know, run these two commands to see details, like mine:

```
fred@bionic-z97:~$ ls -l /dev/sda*
brw-rw---- 1 root disk 8, 0 Sep 11 11:14 /dev/sda
brw-rw---- 1 root disk 8, 1 Sep 11 11:14 /dev/sda1
brw-rw---- 1 root disk 8, 2 Sep 11 11:14 /dev/sda2
brw-rw---- 1 root disk 8, 3 Sep 11 11:14 /dev/sda3
brw-rw---- 1 root disk 8, 4 Sep 11 11:14 /dev/sda4
```


```
fred@bionic-z97:~$ lsblk -f
NAME    FSTYPE LABEL    UUID                                 MOUNTPOINT
sda                                                          
&#9500;&#9472;sda1  vfat   EFI      FD76-E33D                            /boot/efi
&#9500;&#9472;sda2                                                       
&#9500;&#9472;sda3  ext4   trusty   45de38c8-6748-4634-b207-628d9aa8b42b 
&#9500;&#9472;sda4  swap            3af6a910-59f8-4719-b58c-2e7484d435f0 
&#9500;&#9472;sda5  ext4   iso_ssd  695d18b5-16f8-4e9c-bf66-675a12da5a26 
&#9500;&#9472;sda6  ext4   xenial   255a2800-b871-4fdf-a809-16987e64b8b3 
&#9492;&#9472;sda7  ext4   bionic   8c92557f-cc60-438b-b1ea-ffea0adf0a1a /
```

---

### Post by The Cog on 2018-09-12
> **hirno93 said:**
> so sda is the device file for sda2? or am i missunderstanding?
Both /dev/sda and /dev/sda2 are device files. /dev/sda is a window into the entire disk and at the front of that you would be able to read the partition table, and further along you would be able to read the contents of the partitions (and any gaps between them). But /dev/sda2 is a window into just the second partition on /dev/sda, so reading/writing /dev/sda2 cannot accidentally overstep the bounds of that partition.

---

### Post by ajgreeny on 2018-09-12
You will also probably hear or read the sentence somewhere that "everything in Linux is a file", meaning all disks, partitions, usb drives and their partitions, etc etc; all are represented in the filesystem somewhere as files.

The command ```
mount
``` will show you all the mounted devices, including all the partitions, whether hard disk or usb, and that list will show you where each partition fits within the filesystem, ie, its mountpoint, and will also show many other mounted parts of the filesystem; expand that command to ```
mount | grep /dev
``` and you will see only those that are "files" in the /dev folder, including, of course the / (root) partition, and if you have one, as separate /home partition.

I'm not sure how well this helps answer your question, but I hope it is useful information for you.

---

