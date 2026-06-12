---
title: "Oneiric installer won't recognise Windows 7 partition!!"
date: 2011-10-08
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by psychokilla on 2011-10-08
Hi, I'm trying to dual boot Ubuntu with Windows 7 (As I've done in the past with no problems).

I already have Windows 7 installed and it works fine.

I've shrunk the partition ready to install Ubuntu but when I try to install I get the following...

[[IMG]http://i56.tinypic.com/vqql1j.jpg[/IMG]](http://i56.tinypic.com/w0lru8.png)
[Click to Magnify]

As you can see neither the partition tool nor the installer will recognise the Windows 7 partition as being present but it's still shown in Ubuntu itself.

I had previously tried to install the iAtkos L1 distribution but then formatted the drive back to NTFS using an Ubuntu Live CD and then installed Windows 7.

Anyone have an idea why the Ubuntu installer won't recognise my Windows partition and what I can do to resolve this?

---

### Post by garvinrick4 on 2011-10-08
What does (open a terminal in Live cd and run)
```
sudo fdisk -l 
```(lower case L)
say. copy and paste to this thread.

---

### Post by psychokilla on 2011-10-08
[quote=Terminal]ubuntu@ubuntu:~$ sudo fdisk -l

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xff5a403f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848  1045460991   522627072    7  HPFS/NTFS/exFAT

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 4043 MB, 4043309056 bytes
255 heads, 63 sectors/track, 491 cylinders, total 7897088 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x4688b40f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *         128     7893119     3946496    b  W95 FAT32
ubuntu@ubuntu:~$ 
[/quote]

That's what I get.

Thanks for the reply

Seems like the iAtkos left the hard drive with a GUID partition table even though I reformatted using a Live CD to NTFS Is there any way to convert without losing all the data?

---

### Post by garvinrick4 on 2011-10-08
There are a lot of threads and links supplied when doing a Google search but I have
none handy. 
You now know why is not recognized you need to get back to "basic" disk.
Here is one on quick google. 
[http://www.dynamic-disk.com/convert-dynamic-disk-to-basic.html](http://www.dynamic-disk.com/convert-dynamic-disk-to-basic.html)

---

### Post by Quackers on 2011-10-08
If it's just stray GPT data it may be that Fixparts can get rid of it. If it's because an EFI boot partition was used then it won't, but it doesn't look like an EFI partition is present.
Have a look here
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

EDIT  If you do use Fixparts, make sure you download Fixparts and NOT gdisk! Just keep clicking until you find fixparts :-)

---

### Post by psychokilla on 2011-10-08
Genius!!!

Thanks so much man, that did the trick, used the Windows version, it said there was GPT stuff left, asked me if I wanted it removed, I said yes then chose "w" to write the MBR data and then rebooted onto the Ubuntu nightly on usb and it saw the Windows 7 partition and the new one I made straight away!!

Thanks again!!

---

### Post by Quackers on 2011-10-08
That's good news :-)
It's a very handy little programme is Fixparts (written by forum member srs5694).

---

