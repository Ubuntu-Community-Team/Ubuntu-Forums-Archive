---
title: "gpart does not recognize my windows partition"
date: 2014-04-24
forum: New to Ubuntu
---

### Post by pritesh4 on 2014-04-24
when i boot ubuntu 12.04.4 from live usb it shows my whole hdd as unallocated.
i run the command "sudo fdisk -lu"in terminals the following ouput shows.

```
ubuntu@ubuntu:~$ sudo fdisk -lu

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.




Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x5c672921


   Device             Boot        Start           End               Blocks            Id      System
/dev/sda1                        63             2047               992+            42        SFS
Partition 1 does not start on physical sector boundary.
/dev/sda2           *         2048          206847            102400           42        SFS
/dev/sda3                    206848      307202047       153497600         42        SFS
/dev/sda4                 307202048    1953523119      823160536         42         SFS


Disk /dev/sdb: 1983 MB, 1983905792 bytes
64 heads, 36 sectors/track, 1681 cylinders, total 3874816 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


   Device            Boot     Start          End       Blocks           Id      System
/dev/sdb1         *          37       3874724   1937344           6       FAT16           "
```

but in windows device manager it shows ntfs files

---

### Post by tomearp on 2014-04-24
fdisk will not work with hard disks that contain a [GPT style of partition table]("http://en.wikipedia.org/wiki/GUID_Partition_Table"). Hence the message:
```
WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.
```
You can use parted by issuing the command:
```
sudo parted
```
I would recommend using gparted though as it provides quite a good interface to parted.
```
sudo apt-get install gparted
sudo gparted &
```

---

### Post by pritesh4 on 2014-04-24
invalid command

---

### Post by coffeecat on 2014-04-24
You have Windows dynamic volumes which are a Microsoft proprietary way of creating partitions. Your screenshot shows that this is so and the "SFS" in your fdisk output means this. You cannot use Linux partitioning tools with dynamic disks. The only way around this is to convert the dynamic disk back to a basic one, or to completely reformat your hard drive and reinstall Windows to conventional partitions before installing Ubuntu. This thread is a little old, but see oldfred's comments in post #2:

[http://ubuntuforums.org/showthread.php?t=1705481](http://ubuntuforums.org/showthread.php?t=1705481)

**Edit**: a more recent post by oldfred on this issue:

[http://ubuntuforums.org/showthread.php?t=2213124&p=12967497&viewfull=1#post12967497](http://ubuntuforums.org/showthread.php?t=2213124&p=12967497&viewfull=1#post12967497)

---

### Post by lisati on 2014-04-24
> **pritesh4 said:**
> invalid command

Which one?

---

### Post by pritesh4 on 2014-04-24
sudo apt-get install gparted
sudo gparted &

---

### Post by pritesh4 on 2014-04-24
can anybody please explain me that in linux after executing the command "sudo fdisk -lu" it shows sfs" partition but in windows it shows ntfs partition why?

---

### Post by coffeecat on 2014-04-24
> **pritesh4 said:**
> can anybody please explain me that in linux after executing the command "sudo fdisk -lu" it shows sfs" partition but in windows it shows ntfs partition why?

@pritesh4, will you **please** read my post at #4. The links to oldfred's posts give you all you need to know in this situation. But to answer your question, SFS in fdisk output = dynamic disk and since dynamic disk is a Windows only thing, you can assume the filesystem is NTFS. Your screenshot shows type = dynamic, so both fdisk and the Windows Disk utility are saying the same thing in different ways.

---

### Post by pritesh4 on 2014-04-24
> **coffeecat said:**
> @pritesh4, will you **please** read my post at #4. The links to oldfred's posts give you all you need to know in this situation. But to answer your question, SFS in fdisk output = dynamic disk and since dynamic disk is a Windows only thing, you can assume the filesystem is NTFS. Your screenshot shows type = dynamic, so both fdisk and the Windows Disk utility are saying the same thing in different ways.
thank you :P:P:KS

---

### Post by Impavidus on 2014-04-24
Also note that the ntfs partitions shown by Windows have different sizes than the sfs partitions shown by fdisk. Windows assembles the sfs partitions into some kind of virtual disk and then repartitions it into dynamic partitions of different sizes. Ubuntu can't do anything with that drive.

---

