---
title: "qhow to quad boot a system"
date: 2008-09-13
forum: New to Ubuntu
---

### Post by stunningman on 2008-09-13
i am running windows xp and ubuntu 8.04 and fedora 9.i want to add more operating system on my pc.how to do it.

anybody give step by step procedure.

---

### Post by C.S.Cameron on 2008-09-13
You can only have 4 partitions on a given drive.
Search grub.

---

### Post by cariboo on 2008-09-13
Just a bit of a correction, you can only have 4 primary partitions, you can have as many logical partitions as you want.

Jim

---

### Post by lswb on 2008-09-13
Here's a website with lots of info on this:

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

What works best for me is to have a small (I use 100MB, yes that is 1/10 of a gigabyte) partiton where grub is installed. This partiton will be used to boot the computer. In the grub menu.lst in this partition, there are chainloader statements that transfer boot to other partitions where the different OS are installed. These other partitions can have their own grub or other bootloader installed.

The benefit of this is that when a particular linux distribution has a kernel upgrade and modifies it's grub menu or other bootloader configuration, the startup grub menu will not be changed. The web site link explains much better than I can.

---

### Post by unutbu on 2008-09-13
Having a separate grub partition as lswb suggested is a very good idea. You may also find this guide helpful:
[http://ubuntuforums.org/showthread.php?t=724817](http://ubuntuforums.org/showthread.php?t=724817)

---

### Post by egalvan on 2008-09-13
> **cariboo907 said:**
> Just a bit of a correction, you can only have 4 primary partitions, you can have as many logical partitions as you want.

Jim

further notes on limits...

clip:
[I]Most MS systems are designed to reside in a primary partition and there can be a maximum of four of 4 primaries in each hard disk. To get more partition a user “must” give up one primary to turn it into an extended partition. In Linux a PATA (or IDE) disk can have 63 partitions maximum and the limit of a SATA or SCSI disk is 15.

The number of partition plus the whole disk itself make up 64 and 16 devices respectively.

Updated note: PATA disk names and the 63 partitions limit is no longer supported. Please read Post #21 for further explanation
Since Feb 2007 Linux kernel 2.6.20 and later have incorporated the PATA disk names into the SCSI/SATA/USB disk family and so in the future PATA disks will all be called sda, sdb, sdc... etc. This makes a PATA disk incapable of having more than 15 partitions.[/I]



See more at:

**How to install and boot 145 operating systems in a PC**

[http://www.justlinux.com/forum/showthread.php?t=147959&page=2](http://www.justlinux.com/forum/showthread.php?t=147959&page=2)

---

### Post by stunningman on 2008-09-19
i want to add ubuntu partition along with my my last installed linux i have two linux already installed(i.e.fedora 9 and opensuse 11.0)both of them are working fine but whenever i try to install ubuntu 8.04 after that my last linux partition do not boot .have to edit grub evertime.

somebody give permanent solution.

---

