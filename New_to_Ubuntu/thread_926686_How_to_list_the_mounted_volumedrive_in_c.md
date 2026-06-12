---
title: "How to list the mounted volume/drive in c"
date: 2008-09-22
forum: New to Ubuntu
---

### Post by yogish on 2008-09-22
How to list the mounted volume/drive in c?

---

### Post by aeiah on 2008-09-22
first you need to find out what the name of the partition is. i find it easiest to run gparted (it may not be installed yet. get it from synaptic if not). gparted is a partition editing tool. you dont need to edit any partitions, but if you're unclear about what the device is called under linux then this will probably give you the clearest idea. once found, you can manually mount it if you like, or you could permanently mount it by editing fstab. here's how to mount it temporarily. in terminal do:

```

sudo mkdir /media/windows
sudo mount /dev/sda1 /media/windows

```

windows is the directory it will be mounted to (mkdir made the directory first) and sda1 is the name of the partition/device. it probably wont be sda1 in real life. you'll have to find that out first.

to permanently mount it like any other partition, refer to the HOWTO tutorials and such on this forum or google regarding editing fstab and mounting an ntfs windows partition. its just a matter of editing a text file really.

---

### Post by prasaanth on 2008-09-22
Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x62fc62fc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2503    20105316    c  W95 FAT32 (LBA)
/dev/sda2            2504       10011    60308010    f  W95 Ext'd (LBA)
/dev/sda5            2504        5006    20105316    b  W95 FAT32
/dev/sda6            5007        7509    20105316    b  W95 FAT32
/dev/sda7            7510       10011    20097283+   b  W95 FAT32

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe1d284c9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30216   242709988+  83  Linux
/dev/sdb2           30217       30401     1486012+   5  Extended
/dev/sdb5           30217       30401     1485981   82  Linux swap / Solaris


THIS IS WHAT I GET WHEN I ENTER THE sudo fdisk -l COMMAND IN MY TERMINAL, I'M USING DUAL HARDISK -- IN WHICH THE SECOND ONE (250GB) IS COMPLETELY OCCUPIED BY UBUNTU, HOWEVER IT IS NOT MOUNTING ALL THE WINDOWS DRIVES, PLEASE BRIEF ME ON HOW TO DO THAT, I'M A NEWBIE

---

### Post by aeiah on 2008-09-22
see here: [http://ubuntuforums.org/showthread.php?t=912345](http://ubuntuforums.org/showthread.php?t=912345)

your drives that need mounting are /dev/sda1, sda2, sda5, sda6 and sda7

---

### Post by prasaanth on 2008-09-22
Thanks a lot!!!
It worked just perfect... now as i said i have installed my ubuntu in the second harddisk --250gb, but the thing is it is as a SINGLE PARTITION, when tried to resize/move thro Gparted i got errors, so i installed it on the complete disk without partitioning and after installation i tried again but this time some other error occured and the process occured, please help.

Thanks in advance, 

PRaNdo

---

