---
title: "New Disk pre install diskpart dual boot"
date: 2008-11-18
forum: New to Ubuntu
---

### Post by gmgj on 2008-11-18
I have an XP machine that I am making into a dual boot.  I am adding a 500 gig hard drive today and I would like to partition it into 2 XP logical drives (one to build Firefox under windows) and another partition for ubuntu.  After seeing a few posts that mention FAT32 etc, I thought I would ask, Is this okay?

Use Diskpart to create 3 partitions on my new hard drive.

format 2 of these partitions for ntfs and use them with XP

Leave the 3 partition alone and use the LiveCD to install ubuntu into this partition.

---

### Post by nhasian on 2008-11-18
actually linux needs two partitions.  one for / (usually EXT3) and one for SWAP.  a lot of people recommend having a third partition for /home.  Since you can only have 4 primary paritions, you can make one of them be an Extended parition.  This partition may then be subdivided into multiple logical partitions.

---

### Post by gmgj on 2008-11-18
If I create an extended partition , with logical partitions , can that extended partition , and its logical partitions be used for the Linux partitions?

For example I am getting a new 500 gb drive

200 gig XP Primary Parition - for miscellaneous Content and Source files
50   gig XP Primary Partiton - for for building Firefox, source control and tmp downloads and jic
25   gig XP Primary Partition - converting filenames from codepage 1252 to utf-8 
the rest (200 gig)  Extended Parition - for Ubuntu

create partiton logical  1 - for / EXT3 - size XX 
create partition logical 2 - for swap   - size YY
create parition logical 3 for /home  - the rest ?

I will be swapping out a few packages, but for the most part, for the foreseeable future, I will be learning Open Office and the standard stuff found on the Live CD.
I will need 20 gig of space for a Firefox extension

Grub is the boot loader, so where does that live?

---

### Post by gmgj on 2008-11-19
I have found this as guide to partitioning:

[http://www.faqs.org/docs/Linux-mini/Partition.htm](http://www.faqs.org/docs/Linux-mini/Partition.htm).

It looks good ; however, it (as perhaps with most documentation, its almost obsolete the day its written) appears dated.

...

Boot Partition:

    Your boot partition ought to be a primary partition, not a logical partition. This will ease recovery in case of disaster, but it is not technically necessary. ...

-----------------------------------------------------------

From 
[http://www.bglug.ca/articles/linux_boot_process.html](http://www.bglug.ca/articles/linux_boot_process.html)  Linux Boot Process

It is also possible for extended partitions to hold a boot sector, but this must be supported by the boot manager....

  Does Grub support extended partitions as a boot sector ?

Seems to be a few issues that I am trying to avoid
see  convincing-grub-dual-boot-winxp-extended-partition at
[http://www.linuxforums.org/forum/ubuntu-help/60947-convincing-grub-dual-boot-winxp-extended-partition-2.html](http://www.linuxforums.org/forum/ubuntu-help/60947-convincing-grub-dual-boot-winxp-extended-partition-2.html)

Okay, the path of least resistance is:

It looks as if it was indeed partitioned as 4 primaries ... unlike the more usual practice (in old established distributions) of making the 
**boot one a primary,** then giving **the rest allowed for Linux to an extended one**.

==========================================================

So its back to sizing, ordering and mapping

500 gig

200 gig XP Primary Partition 
75  gig XP Primary Partition 
??   gig Linux Boor Partition  (is this  EXT3  ?)  
the rest (200 gig)  Extended Partition - for ubuntu

logical 1 - for / EXT3 - size XX see above 
logical 2 - for swap   - size YY
logical 3 for /home  - the rest ?

---

### Post by nhasian on 2008-11-20
yep, thats a lot of partitions, but it looks like everything's in order now.  :)

---

### Post by caljohnsmith on 2008-11-20
> **gmgj said:**
> 
> Boot Partition:

    Your boot partition ought to be a primary partition, not a logical partition. This will ease recovery in case of disaster, but it is not technically necessary. ...
I don't think there is any special advantage to having the boot partition as a primary partition; it can be primary or logical with no problems. 

> **gmgj said:**
> 
> 
It is also possible for extended partitions to hold a boot sector, but this must be supported by the boot manager....

  Does Grub support extended partitions as a boot sector ?

Absolutely. :)
> **gmgj said:**
> 
500 gig

200 gig XP Primary Partition 
75  gig XP Primary Partition 
??   gig Linux Boor Partition  (is this  EXT3  ?)  
the rest (200 gig)  Extended Partition - for ubuntu

logical 1 - for / EXT3 - size XX see above 
logical 2 - for swap   - size YY
logical 3 for /home  - the rest ?
If you are going to make a /boot partition, it would be best to put it at the very beginning of the drive if you can, because there are some BIOSes that can't access anything on a drive past either 8.5 GB or 137 GB; your BIOS might not have that limitation, but if it does, it's not fun finding out the hard way after you've gone through the trouble of setting all your partitions up and installing everything. Anyway, good luck and let us know how it goes. :)

---

### Post by gmgj on 2008-11-21
Thanks again.  I did not think you could make an extended partition, the first partition!  

I did the above partitioning.  I did a custom install of ubuntu to my new disk.  I changed the boot order of the disks in my BIOS.  I am writing from ubuntu, on my new disk!  As soon as I figure out how to tell where my boot partition is, my swap partition and  home, I can declare victory.

---

