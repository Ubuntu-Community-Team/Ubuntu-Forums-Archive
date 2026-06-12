---
title: "Unrecognized Partition Table GParted"
date: 2013-06-02
forum: New to Ubuntu
---

### Post by Dabo Ross on 2013-06-02
I was just doing some partitioning work on a live USB system, and when I just booted back up into my install GParted won't recognize the partition table.

The device still boots up fine, but this is the output I get from running GParted:
```
daboross: ~\ $ sudo gparted
[sudo] password for daboross: 
======================
libparted : 2.3
======================
Unable to satisfy all constraints on the partition.
```

Here is fdisk output:
```
daboross: ~\ $ sudo fdisk -l

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xe2a07366

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63       80324       40131   de  Dell Utility
Partition 1 does not start on physical sector boundary.
/dev/sda2   *       81920    42485759    21201920    7  HPFS/NTFS/exFAT
/dev/sda3        42487808   252203007   104857600    7  HPFS/NTFS/exFAT
/dev/sda4       252203008  1465147391   606472192    f  W95 Ext'd (LBA)
/dev/sda5       252205056   262688767     5241856   83  Linux
/dev/sda6       262688768   294146047    15728640   83  Linux
/dev/sda7       294148096   325605375    15728640   83  Linux
/dev/sda8       503865344  1087657983   291896320   83  Linux
/dev/sda9      1087660032  1221875711    67107840   83  Linux
/dev/sda10     1221877760  1431592959   104857600   83  Linux
/dev/sda11     1431595008  1465147391    16776192   82  Linux swap / Solaris

```

This is what GParted looks like graphically:
[IMG]http://i44.tinypic.com/jpg8ev.png[/IMG]

This is what my understanding of my current partition layout is:
/dev/sda1 through /dev/sda3 are windows partitions.
/dev/sda4 is an extended partition containing all of my linux partitions.
/dev/sda5 is a 5gb partition that I am planning on making a shared /boot partitions
/dev/sda6 is a 15gb partition mounted at / in Ubuntu 13.04
/dev/sda7 is a 15gb partition mounted at / in UbuntuGNOME 13.04
/dev/sda8 is a partition over 300gb that is mounted on /home in Ubuntu 13.04
/dev/sda9 is a 60gb partition mounted at /opt in Ubuntu 13.04
/dev/sda10 is an around 100gb backup partition
/dev/sda11 is an around 16gb swap partition
All of the non-windows partitions besides the SWAP are ext4.
The system is 64bit, just in case that has any significance.
This was working before I created /dev/sda5 (Which started out as /dev/sda11).

And also I used fdisk to re-order the partitions after I created /dev/sda5 like this:
```
sudo fdisk /dev/sda
x
f
w
```

The system works fine as far as I can tell, GParted is just 'Unable to satisfy all constraints on the partition.'

I was in the middle of creating a shared /boot partition when this happened, and I would like to be able to finish that with GParted.

I found a few post about GParted not recognizing the partition, but I don't think they are the same issue.
[http://ubuntuforums.org/showthread.php?t=1835762](http://ubuntuforums.org/showthread.php?t=1835762) - Not sure about this
[http://gparted.sourceforge.net/h2-fix-msdos-pt.php](http://gparted.sourceforge.net/h2-fix-msdos-pt.php) - Is this what I want?
[http://www.pclinuxos.com/forum/index.php?topic=79547.0](http://www.pclinuxos.com/forum/index.php?topic=79547.0) - Don't think this is the problem
[http://linux.bigresource.com/Ubuntu-Partition-Table-not-recognized-in-Gparted--1NrmYL4Or.html](http://linux.bigresource.com/Ubuntu-Partition-Table-not-recognized-in-Gparted--1NrmYL4Or.html) - Not sure?

Basically I would like to know if it is safe to keep booting this system, and if there is any way to get GParted to recognize this.
Does GParted not like there being 11 partitions?

---

### Post by sandyd on 2013-06-02
Follow the instructions at
[http://gparted.sourceforge.net/faq.php#faq-23](http://gparted.sourceforge.net/faq.php#faq-23) - which shows you how to check why gparted is showing it as unallocated

---

### Post by Dabo Ross on 2013-06-02
The problem I have is 'Unable to Satisfy All Constraints'.

Do you think this is caused by there only being one sector in between the end of /dev/sda5 and /dev/sda6 instead of 2?

I don't have anything I care about on /dev/sda5, would it be safe to delete it with fdisk, and do you think this might solve it?

This is what The GParted help page ([http://gparted.sourceforge.net/h2-fix-msdos-pt.php#unable-satisfy-constraints](http://gparted.sourceforge.net/h2-fix-msdos-pt.php#unable-satisfy-constraints)) says about this:
> How-to Fix Unable to Satisfy All Constraints

We plan to outline how to approach this problem. In the meantime you can seek help in the GParted forum.
Because this probably isn't really a problem with GParted, I would rather not bug them on their forum, but do you think I should?

EDIT:

I deleted /dev/sda5 using fdisk from a live usb and that fixed it!

---

