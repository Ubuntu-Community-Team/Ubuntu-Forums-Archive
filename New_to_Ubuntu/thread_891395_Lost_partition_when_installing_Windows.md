---
title: "Lost partition when installing Windows"
date: 2008-08-16
forum: New to Ubuntu
---

### Post by sidzoo on 2008-08-16
I had three working primary partitions - one for / , one for my laptop recovery stuff, and one extended partition that housed my swap and two logical partitions, one for Media and one for Personal files. I had about 12 gB unallocated at the start of the disk. These logical partitions were NTFS, created by Ubuntu.

I installed XP on the unallocated area. It installed perfectly, but my Multimedia partition now shows up as unallocated on GParted.
Also, when I tried to reinstall grub, and I rebooted, I got an [Error 5: File not found]. I can now boot from nothing but the live cd.

I need to fix two things:
1) Installation of Grub
2) Recover (if possible) the data on the drive that now shows up as Unallocated.

Is this possible?

---

### Post by Pro-reason on 2008-08-16
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

I think that you have lost your data for ever.  Windows ate it.

---

### Post by sidzoo on 2008-08-16
> **Pro-reason said:**
> [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

I think that you have lost your data for ever.  Windows ate it.


I managed to find a fix for the grub problem.
Is my other problem known to happen? Install Windows on one partition, and just completely LOSE another partition? The partition I lost now shows up as "unpartitioned space".

---

### Post by nicedude on 2008-08-16
Give us some info

sudo fdisk -l

would show us all your partition tables. I am trying to understand your situation and know this would help others to do so as well.

---

### Post by sidzoo on 2008-08-16
omitting empty partition (5)

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcccdcccd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              34        1408    11044687+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2            1409        3608    17671500   83  Linux
Partition 2 does not end on cylinder boundary.
/dev/sda3   *        3609        4257     5213092+   c  W95 FAT32 (LBA)
Partition 3 does not end on cylinder boundary.
/dev/sda4            4258        9729    43953840    5  Extended
Partition 4 does not end on cylinder boundary.
/dev/sda5            4258        4507     2008062   82  Linux swap / Solaris
/dev/sda6            8143        9729    12747546    7  HPFS/NTFS

---

### Post by Dill on 2008-08-16
Boot from the Live CD, open up a Terminal, and try this:

```
cd /mnt
sudo mkdir sda2
sudo mount /dev/sda2 sda2
cd sda2
ls
```

Check around here and see if you see any of the data that was on your Linux partition. I think you should be fine, since your partition table seems to show everything that you mention as still there.

Cheers, 
Dylan

---

### Post by l4c on 2008-09-01
Hello. I have a similar problem. I've tried to install Windows XP Pro in a partition that i created. The Windows XP cd was corrupted and all the instalation became corrupted. So cleaned the windows xp partition. When i logged in on ubuntu i found out that my hard drive containing my backups, movies, images, musics etc... had been erased. When i open up Gparted and select the second hard drive where all that stuff used to be, it says 230gb of unallocated space. I don't know why but windows erased all that. You have to help me. All my precious stuff like family vacations photos were there. That partition was formated in NTFS.

Sudo fdisk-l shows this:

Disk /dev/sda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa9bea9be

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       12316    98928238+  83  Linux

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
86 heads, 15 sectors/track, 378602 cylinders
Units = cylinders of 1290 * 512 = 660480 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1      208090   134217727+   4  FAT16 <32M

Disk /dev/sdb1: 137.4 GB, 137438952960 bytes
86 heads, 15 sectors/track, 208089 cylinders
Units = cylinders of 1290 * 512 = 660480 bytes
Disk identifier: 0x00000001

     Device Boot      Start         End      Blocks   Id  System
/dev/sdb1p1   *           1      208090   134217727+   4  FAT16 <32M

Some one help me please!

Thanks

---

### Post by bumanie on 2008-09-01
Grub error five indicates that the partition table on the hard drive has been corrupted. The only way of trying to retrieve it by using testdisk to re-write the partition table. You can use a ubuntu live cd > sudo apt-get install testdisk Then to start testdisk > sudo testdiskThen follow the simple gui. You can also go to [this site]("http://www.cgsecurity.org/wiki/TestDisk") and download a testdisk live cd and read the tutorial. I recently re-wrote a partition table showing grub error 5 with testdisk - worked like a charm.

---

### Post by l4c on 2008-09-01
Can't i do that in my desktop? Without using the ubuntu live cd?

Thanks

---

### Post by pmlxuser on 2008-09-01
when you boot into ubuntu the system loads the Disk and sometimes it is locked for changes I guess thats why they constalty refer you to use Lice CD so that you can be able to apply necessary changes to your disks or partition

---

### Post by l4c on 2008-09-01
Ok thank you. I am going to try it.

---

### Post by bumanie on 2008-09-01
I believe it needs to be done via a live cd as any partition you are using at the time will also need to be accounted for in the partition table. If the partition is 'active' it may send some unreliable data. Any retrieval programs I know off run from live cd's - all the 'rescue-type' disks do, so I think it would only be safe to use a live cd - basically it is safest to work on unmounted partitions. 
l4c in your case, A) You should've started a new thread and B) Testdisk may work, your other option would be photorec (which recovers more than photos) from the same site linked to before. There is also a linux program called ntfsundelete. In fact your problem is quite different - it would be good if you started a new thread. Read up on how to use any of these before attempting anything, if you have problems, start a new thread.

---

### Post by l4c on 2008-09-01
Thanks for all the help. TestDisk worked like a charm. I've got all of my stuff back, and it only took half-hour. Thank you.

Cheers!

---

