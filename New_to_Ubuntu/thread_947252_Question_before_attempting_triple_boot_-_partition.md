---
title: "Question before attempting triple boot - partitioning."
date: 2008-10-14
forum: New to Ubuntu
---

### Post by RavUn on 2008-10-14
I have Ubuntu and Vista and want to add OS X.  I plan on doing a fresh install of all 3.  I'm going to follow these instructions:
> 
- GPT (Guid Partition Table) triple boot -

- Change your partition table type to GPT (Guid Partition Table) and create 3 partitions by using Parted Magic Live CD or iATKOS Disk Utility. HFS+ format for OS X target, Fat32 (msdos) for the others.

- Boot iATKOS 4i DVD, install only bootloader to OS X target. ***

- Boot Vista DVD and install it to first Fat32 partition.
(Note: System marks first Fat32 partition for booting Foreign OS'. If you choose other than first Fat32 as target for Vista, then during installation, system will not continue install process at first Vista boot.)

- Boot Linux media and install the OS. Install the bootloader to linux root.
(Note: Some live linux cd stuff (knoppix, kanotix, parsix, etc.) has built-in installer applications and they use gparted for partitioning and formatting targets. At this point, formatting target to linux fs via Gparted is not a good choice, use unix fdisk just for changing the target partition type from ''c0'' to ''83'' which is linux partition type and then continue installation.)

- Boot iATKOS 4i DVD and install OS X as usual.

Now you have triple boot on GPT, thats all.

As you see, preparing multiboot system on GPT is more practical and easier.
Darwin on GPT will see other OS' as Foreign Boot.

*** For pro-users: You can re-install Darwin bootloader by booting the iATKOS DVD with -s. Boot with -s and enter darwin command, follow the instructions. For MBR HD, you can add boot flag via fdisk after darwin installation.


It seems pretty straight forward... but it recommends creating the HFS+ partition and two Fat32 partitions (one for linux and one for Vista).  Is this correct?  I thought linux needed ext3.

Also, how do I include a swap partition... and I'm pretty sure when it says to have the bootloader in the linux root partition that means have that partition setup with / and /boot.  Right?  Should I end up with 4 partitions (HFS+ => OS X, Fat32 => Vista, Ext3/Fat32 => Ubuntu, Ext3 swap)?  Also, when I reinstall Vista will it automatically do a recovery partition...?  I am pretty sure we can't have more than 4 primary partitions.

Thanks.

---

### Post by spiderbatdad on 2008-10-14
Hi. I'm no expert at partitions, but that guide doesn't look right to me either. I have had 3 oses on here in the past. I did by  having a linux installation and using gparted after to create the others. The linux partitioning tool create an **Extended** partition. The extended partition (imaginary kind of space) allows you to have more than four partitions on your disk. Personally, I would start with Ubuntu, creating a separate /home while i was at it. Then move on to OSX, and vista last...where you will have to fix the mbr after the installation...like I said, I'm no expert at multiple booting...Good luck.

---

### Post by aska786 on 2008-10-14
Earn money for clicking The Ads [sign up]("http://bux.to/?r=aska786") Here

---

### Post by bumanie on 2008-10-14
I have some idea of triple booting, but not with OSX. Really wonder why they suggest vista and linux be put on a FAT32 filesystem - very limiting with the size of files one can get these days - and very odd. The instructions may work, but I would be careful about doing it this way as recommending FAT32 for two OSes that normally would reside on different types of filesystems, seems a bit suspect to me. If I were you, I would look for a way of chainloading hfs with grub or try an independant bootloader like GAG.

---

