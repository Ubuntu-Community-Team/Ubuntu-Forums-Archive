---
title: "Partition layout strategies"
date: 2008-07-06
forum: Outdated Tutorials &amp; Tips
---

### Post by louieb on 2008-07-06
I've see a lot of post asking how should I partition my hard drive. Well theres no right or wrong way to layout partitions on a hard drive.   But there are layouts that make backing up, running several distributions or  making it easier to answer the question upgrade or not.    

These are just some layouts I have tried.  The pre-install page of the [Illustrated Dual Boot Site]("http://users.bigpond.net.au/hermanzone/")  contains the rules of partitioning and is a must read for anybody new to partitioning a hard drive. 

For another view point check out the plan partitions page of [Psychocats Ubuntu Linux Resources]("http://www.psychocats.net/ubuntu/index.php") 

Kiss (keep it simple stupid).  - dual boot.
The Ubuntu installer left on its own   partitions the drive something like this.
[IMG]http://louboldt.com/pimg/simple.jpg[/IMG]

The main advantage of this is its simple.

However if you keep your system up to date. Every 6 months Ubuntu put out a new version.  I want my data out of the way when those 300-400 MB start downloading. So my desktop is partitioned some thing like this.
[IMG]http://louboldt.com/pimg/Desktop2.jpg[/IMG]
Along with a / (root) and /home partition, I have a  test partition. During the Gutsy to Hardy upgrade xorg changed.  I found that out when I installed Hardy in the test partition. It came up with 600x800 resolution not the 1440x900 I enjoyed in Gutsy. I was able to take my time and search the forum to find I needed to run displayconfig-gtk.       


I used to think 31 was a lot of flavors of ice cream. There hundreds of Linux distributions out there. When I first stared using Linux I wanted to try a few. So I set up a hard drive like this.
[IMG]http://louboldt.com/pimg/MultiBoot.jpg[/IMG]The 1st partition is a dedicated boot loader partition the oly thing on it is GRUB. Its GRUB menu is what comes up when the PC is booted.  the grub menu looked like this 
```

title  Linux 1 chainload on (hd0,0)    
       root (hd0,0)  
       chainloader +1

title  Linux  1 configfile on (hd0,0)
       configfile (hd0,0)/boot/grub/menu.lst  

title  Linux 2 chainload on (hd0,5)    
       root (hd0,5)  
       chainloader +1

title  Linux  2 configfile on (hd0,5)    
       configfile (hd0,5)/boot/grub/menu.lst      

....

```it contained a configfile and chainloader  for each of the partitions. To add another linux it install on some partition. reboot and select the partition. 

The rest of the drive  was sliced up into 5 to 15GB partitions.  When I installed a distribution I had the install put its boot loader in the boot sector of its partition.

---

### Post by be4truth on 2008-07-07
I have a rather large /home partition and check out most new operating systems via VirtualBox. That saves a lot of trouble with partitioning. I recommend this method.

---

### Post by kcnnc on 2008-07-07
A neater and faster way to try out different distribution nowadays might be virtualization with xen, vmware, virtualbox etc.

A large data partition for the virtual files, a home partition and a / partition.

---

### Post by rolnics on 2008-07-08
> **be4truth said:**
> I have a rather large /home partition and check out most new operating systems via VirtualBox. That saves a lot of trouble with partitioning. I recommend this method.

> **kcnnc said:**
> A neater and faster way to try out different distribution nowadays might be virtualization with xen, vmware, virtualbox etc.

A large data partition for the virtual files, a home partition and a / partition.

Yeah, it might be a faster, cleaner, neater etc, but if like me when i started out with linux, i didn't know you could do such a thing! And also i had got experience of partitioning anyway, so i saw and still do see that the easier option, but there again i have installed one of the virtualisation programs, so i might give it a try. The other thing is my pc is feeling it's age, so that's another consideration, of my own, as running another os on top of your current one must add extra strain on a system? 

But anyway back to the subject louieb great layouts, i've been interested in having a seperate grub partition, i was trying it before my last install, but grub didn't want to play. So i gave up on it and just installed as a knew how.

louieb would you post your current config file(s) for grub, i'd be interested to see a working one, so i can learn for the next time?!

---

### Post by louieb on 2008-07-08
Thanks for the replies and feed back. Checking out distributions in a virtual machine is a good way to go I agree.  For one reason or another I never around to setting up a VM. When I first started using Linux I had a P2-400mHz w 384 MB ram. Not really a powerful enough PC to run a VM. By the time I got a PC powerful enough and with enough memory to run a VM I'd pretty   much settled on Ubuntu.

rolnics -  I'll attach my menu.lst for my GRUB partition. Pretty simple really this hard drive has

[LIST]
[*]Hardy's root on sda1
[*]and home on sda2 ,
[*]sda3 is my dedicated GRUB partition.
[*]sda5 swap
[*]sda6 test install partition
[*]sda7 data
[/LIST]
 ```

/home/lou%>sudo fdisk -l 

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6001c8de

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         914     7341673+  83  Linux
/dev/sda2             915        1436     4192965   83  Linux
/dev/sda3            1437        1438       16065   83  Linux
/dev/sda4            1439        4865    27527377+   5  Extended
/dev/sda5            1439        1503      522081   82  Linux swap / Solaris
/dev/sda6            1504        2417     7341673+  83  Linux
/dev/sda7            2418        4865    19663528+  83  Linux


```Because I have a Dedicated GRUB partition and two Linux installs I have 3 copies of GRUB and 3 menu.lst files on it. Two of the menu.lst files are just whatever the disrtro put it its /boot/grub/menu.lst. 

The MBR boots to the GRUB in sda3 and attached is its  menu.lst.  By the way check out what Herman has to say about making a dedicated GRUB partition.  [IDBS make a dedicated GRUB partition. ]("http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_Grub_Partition_")

Pretty simple really -  make a small 15-20mb partition and copy  all the files from your /boot/grub  directory to it.  Then setup the MBR. For example to set up the MBR on this PC to boot grub I would at a terminal enter ```
sudo grub 
```then at the grub> I would enter these commands
```
root (hd0,2)
setup (hd0)
quit
```

---

