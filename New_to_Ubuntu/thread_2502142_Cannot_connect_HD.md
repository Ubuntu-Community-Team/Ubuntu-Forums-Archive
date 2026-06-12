---
title: "Cannot connect HD"
date: 2024-11-03
forum: New to Ubuntu
---

### Post by kap-franje on 2024-11-03
Hi, I run ubuntu server 24.04.1 LTS on my little Lenovo Thinkcentre M93p. It is used mainly for running ZoneMinder with 3 cameras. It runs perfectly well. However the internal 500 MByte SSD is small for storing camera captures so I decided to attach a 4TB WD purple through USB. The HD is put in a nice AXAGON box and connected to the USB 3 port on the server.

It connects seemingly nicely. However, something is not OK. The lsblk commands recognizes the new drive as sdb:
kapetan@serveronevallo:~$ lsblk
NAME                      MAJ:MIN RM   SIZE RO TYPE MOUNTPOINTS
sda                         8:0    0 465,8G  0 disk 
&#9500;&#9472;sda1                      8:1    0     1M  0 part 
&#9500;&#9472;sda2                      8:2    0     2G  0 part /boot
&#9492;&#9472;sda3                      8:3    0 463,8G  0 part 
  &#9492;&#9472;ubuntu--vg-ubuntu--lv 252:0    0 463,8G  0 lvm  /
sdb                         8:16   0     0B  0 disk 

But if I run fdisk -l, it won't see it.

And fdisk /dev/sdb gives a error message:


Welcome to fdisk (util-linux 2.39.3).
Changes will remain in memory only, until you decide to write them.
Be careful before using the write command.


fdisk: cannot open /dev/sdb: Invalid argument

What can be the problem?

By the way, dmesg seems to give the correct log:
[ 3221.340255] sd 5:0:0:0: Attached scsi generic sg1 type 0
[ 3221.340522] sd 5:0:0:0: [sdb] 0 512-byte logical blocks: (0 B/0 B)
[ 3221.398803] sd 5:0:0:0: [sdb] Write Protect is off
[ 3221.398820] sd 5:0:0:0: [sdb] Mode Sense: 43 00 00 00
[ 3221.399045] sd 5:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 3221.399244] sd 5:0:0:0: [sdb] Preferred minimum I/O size 512 bytes
[ 3221.399257] sd 5:0:0:0: [sdb] Optimal transfer size 33553920 bytes
[ 3221.399568] sd 5:0:0:0: [sdb] Attached SCSI disk

---

### Post by TheFu on 2024-11-03
Try **sudo fdisk /dev/sdb**.

Create a new GPT partition table, then create a Linux primary partition.
Now, you need to add a file system to the partition, unless you want to use LVM. Your install has LVM already on the other storage though you aren't really using the power that LVM provides.

If you have another workstation that is running an X/Server, you could use X11-forwarding to install gparted and do all of this remotely with a GUI. Also, gparted will handle the formatting of the file system AND you can add a LABEL to it so that mounting is easier through the /etc/fstab.

In case you don't know this, the order that storage devices are discovererd by the kernel can change, so we can't count on device file names like /dev/sdb remaining consistent.  This is why we use UUIDs and LABELs to mount specific file systems.  With LVM Logical Volumes, while we can use the UUID or LABEL, I like to use the /dev/{vgname}/[lvname} symbolic links because they provide more information just when I need it in the /etc/fstab file.

BTW, the **lsblk** command above isn't providing too mcuch information.  Use **lsblk -f** to get all of it.  Also, whenever posting terminal commands/output, please, please, please, use the advanced editor here and wrap that output in forum code tags so the columns line up.

---

