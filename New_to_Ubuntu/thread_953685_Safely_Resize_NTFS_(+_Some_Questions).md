---
title: "Safely Resize NTFS (+ Some Questions)"
date: 2008-10-20
forum: New to Ubuntu
---

### Post by tenghoward on 2008-10-20
Hi there,

I have been using Ubuntu for sometime. I recently got a new Desktop (HP Pavilion Slimline s3600z). I wise to install Xubuntu x64 on it. Problem is with my currrent Disk partition:

250GB hardrive partition table:

210GB for C (Where Vista x64 is) - NTFS
13.5GB for D (Factory Image) - NTFS

Since both partition is NTFS, how can I safely resize Drive C? I wish to allocate 25GB from Drive C for Xubuntu (24GB for Xubuntu and 1GB for swap). Did I need some special software to resize partition without corrupting my data? Also what defragment software would you recommand to defarg my drive before resize? Is 1GB of swap enough for me (I have 3GB of RAM)?

Final Question, did Xubuntu support Nvidia 9300? I have not try it but I will tonight.

Many thanks! :lolflag:

---

### Post by aeiah on 2008-10-20
you should be able to resize it no problems. kinda. do a degrag first just using windows, although i doubt there's any fragmentation if its new. the tricky choice you have is whether you should resize your vista partition, move your factory partition and place ubuntu at the end (because the factory image may get confused if it isnt the 2nd partition) or whether you should keep the factory partition at the end of the disk, and put the ubuntu partitions in the middle after vista. you're best seeing if people have had problems with factory resets after messing with the partition table, or whether its possible to create dvds for the factory reset instead of relying on the partition.

you could probably ask the manufacturer whether the position of the factory image on the hard drive has any special significance

oh, and as for swap. if you want to hibernate your computer, you will need at least the 3GB as it dumps everything from ram into the swap during this process.

---

### Post by bumanie on 2008-10-20
Vista has its own partitioning utility. Right click 'my computer', choose 'manage' and then choose 'manage disks'. Right click on the partition you want to alter and you will be given the choices, one of which is to shrink the partition. Prior to doing this it is a good idea to defrag vista at least twice. Ubuntu and its derivatives has its own partitioner that partions/writes the ext3filesystem during the installation process. When installing xubuntu, ensure you set the xubuntu partitioner up on the unallocated space vacated by vista. Ensure you format to ext3 filesystem.

---

### Post by jerome1232 on 2008-10-20
I would advise using vista's partition editor as there has been changes to the nt file system in vista and gparted in rare cases can destroy the ntfs partition while resizing.

---

### Post by tenghoward on 2008-10-20
Okay, I will allocate 3GB for swap even though I won't use hibernation. I will use Vista partition editor to edit my partition. Will **Auslogic Defrag Software do good work**? Or I need other defrag software? 

aeiah: How do I re-arrange the order of the partition?

---

### Post by ajgreeny on 2008-10-20
Having shrunk your vista partition with vista's own utility you can then use gparted to move the Factory Image partition to the left and leave the empty space for xubuntu at the end of the disk.  I don't know if you can move partitions with vista's own utility, but have a look at that as well.

---

### Post by tenghoward on 2008-10-20
Okay, I now have another question. What is the benefit of installing Ubuntu traditionaly vs using Wubi? Pros and Cons?

---

### Post by Duck2006 on 2008-10-20
> **tenghoward said:**
> Okay, I now have another question. What is the benefit of installing Ubuntu traditionaly vs using Wubi? Pros and Cons?

Installing ubuntu using wubi is just making a file from within windoze as install to HDD is in it's own partition. I find the install to a partition, the system runs faster.

[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)

---

### Post by Paqman on 2008-10-20
> **tenghoward said:**
> Will **Auslogic Defrag Software do good work**? Or I need other defrag software? 


Go for it, Auslogics is the best NTFS defrag tool i've found. Certainly the fastest, anyway.

As for Wubi, it has two main drawbacks:
[list]
[*] No hibernation
[*] It really, really doesn't like having it's power supply cut. So don't use it on a desktop if you live somewhere that's prone to power cuts unless you have an uninteruptable power supply.
[/list]

Otherwise, it's an excellent way of setting up a dual-boot. You've also got the option of migrating your Wubi-installed Ubuntu to a dedicated partition later if you want. So there's nothing to lose, really.

---

### Post by tenghoward on 2008-10-21
Okay, I think I'll stick with full installation.

One last question. Can I use Vista's Boot Manager to boot Xubuntu Linux? Considering that I install Linux after Vista, I really don't want to install Grub on MBR. This is for that if I want to remove Linux few years later I can do it easily. :confused:

Many Thanks!

---

### Post by Duck2006 on 2008-10-21
Yes you can or use EasyBCD as the boot loader.

[http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)

---

