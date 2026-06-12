---
title: "stuck in emergency mode"
date: 2018-05-12
forum: New to Ubuntu
---

### Post by sn0m on 2018-05-12
Hi guys, got stuck in emergency mode. Not sure how to fix it. have posted some pictures, could someone pls have a look and advice.
Thanks
sn0m

---

### Post by Bashing-om on 2018-05-12
sn0m; Hello;

Let's prepare to run that file system check from a liveDVD/USB.
Boot a live environment and post back the output of terminal command - Between Code Tags :
```

sudo parted -l

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
to identify the target - images are difficult to work with and many people do not have the bandwidth to deal with images.

see here what we can do.

---

### Post by sn0m on 2018-05-13
Hi, thanks for your reply.
Output as follow:

ubuntu@ubuntu:~$ sudo parted -l
Model: ATA TOSHIBA A100 (scsi)
Disk /dev/sda: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system     Flags
 1      1049kB  16.8GB  16.8GB  primary  linux-swap(v1)
 2      16.8GB  77.7GB  60.9GB  primary  ntfs            boot
 3      77.7GB  99.5GB  21.8GB  primary  ext4
 4      99.5GB  120GB   20.6GB  primary  ext4


Model: ATA WDC WD10JPCX-24U (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name                 Flags
 1      1049kB  66.0GB  66.0GB  ntfs         spare_drive_windows  msftdata
 4      66.0GB  1000GB  934GB   ext4


Warning: The driver descriptor says the physical block size is 2048 bytes, but
Linux says it is 512 bytes.
Ignore/Cancel? I                                                          
Model: USB Flash Disk (scsi)
Disk /dev/sdc: 32.7GB
Sector size (logical/physical): 2048B/512B
Partition Table: mac
Disk Flags: 

Number  Start   End     Size    File system  Name   Flags
 1      2048B   6143B   4096B                Apple

---

### Post by Bashing-om on 2018-05-13
sn0m; Well -

In the 1st drive sda, you have 2 partitions devoted to linux, and on the 2nd - sdb - you have one other.
Do you know what is what ? ( or we can go ahunt'n and find out) .
Operating systems installed on both drives ? What results if you change the boot drive priority in your bios ?

[INDENT][INDENT]sometimes I wonder
[/INDENT][/INDENT]

---

### Post by sn0m on 2018-05-13
Hi
Thanks for your reply. The first drive(SSD) is for os only, it has 1 windows 7 and two ubuntu, a 18.04 qne 16.04
Second drive is for home directory. Ie sdb4 is /home for both linux OS and the sdb1 is an ntfs partition that can be accessed by windows 7 OS as well as ubuntu ones, when I need to transfer files and so on.
Thanks
Koli

---

### Post by Bashing-om on 2018-05-13
sn0m; Ho Kay :)

We focus on sda then.

1st up is to insure that the file system(s) are intact,
Boot up a liveDVD/USB in "try ubuntu" mode and activate a terminal/
here run:
```

sudo e2fsck -C0 -p -f -v /dev/sda3
sudo e2fsck -C0 -p -f -v /dev/sda4

```
If these run clean we try and boot up from grub and see what the system has to say .

[INDENT][INDENT]we can do that
[/INDENT][/INDENT]

---

