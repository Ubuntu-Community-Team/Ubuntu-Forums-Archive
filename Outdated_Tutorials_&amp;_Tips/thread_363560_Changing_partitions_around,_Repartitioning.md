---
title: "Changing partitions around, Repartitioning"
date: 2007-02-17
forum: Outdated Tutorials &amp; Tips
---

### Post by ingo on 2007-02-17
[FONT=Verdana][SIZE=2]Hi,

what to do when you put your (K/X/Ed)Ubuntu onto a single partition but are now running out of space? Simple, export either your /home or /usr directories or both.

How you ask? Simple, just follow the steps below.[/SIZE][/FONT][LIST=1]
[*][FONT=Verdana][SIZE=2]**Partitioning** - Using gparted (either as a [live cd]("http://gparted.sourceforge.net/livecd.php") or the one you may have on your system already) you partition your hard disk the way you want to. I prefer the former, as you may be certain that nothing is mounted and you are not in any danger of ruining your data. Having said that, there is no reason why you should screw it up with the distro version if reasonable care is taken. In this example I will assume that you created two extra ext3 partitions, one for /home (say /dev/hda7) and one for /usr (say dev/hda8). If you used the live CD your system may complain that it cannot successfully run fsck while booting. Ignore its whinging and carry on - you are about to fix it.[/SIZE][/FONT]
[*][FONT=Verdana][SIZE=2]**Mount Points **- OK, you're up again. For you to be able to mount those newly created partitions you have to create mount points (directories) and include them into your fstab. Let's create the mount points first: ```
sudo mkdir /new_home
``` and ```
sudo mkdir /new_usr
```[/SIZE][/FONT]
[*][FONT=Verdana][SIZE=2]**fstab 1** - First we have to find out the relevant UUIDs for the newly created partitions hda7 and hda8. To do so, open a shell and type ```
sudo blkid
``` to get the new UUIDs. Now for the fstab. I like vim but you can use your favourite editor open your /etc/fstab in root mode (sudo). Add the following lines to your fstab ```
# /dev/hda7
UUID=the_code_you_got /new_home ext3 nouser,defaults,atime,auto,rw,dev,exec,suid 0 2
# /dev/hda8
UUID=the_code_you_got  /new_usr ext3 nouser,defaults,atime,auto,rw,dev,exec,suid 0 2
```Save your fstab and mount the new partitions ```
mount /dev/hda7
```and ```
mount /dev/hda8
```[/SIZE][/FONT]
[*][FONT=Verdana][SIZE=2]**Copying** - First we want to export your home folder (incl. all different users) to its new_home :) You should switch to your current home directory ```
cd /home
``` and copy everything across to your new home ```
sudo cp -a * /new_home
```.[/SIZE][/FONT]
[*][FONT=Verdana][SIZE=2]**Check **- OK, the hardest bit is done. It is not a bad idea before wiping your original home to check that what you have done is actually working. So let's tell the system that /dev/hda7 is going to be your /home partition. Again, you need to edit your fstab and adjust the following [/SIZE][/FONT][FONT=Verdana][SIZE=2]```
# /dev/hda7
UUID=the_code_you_got /new_home ext3 nouser,defaults,atime,auto,rw,dev,exec,suid 0 2
``` to read [/SIZE][/FONT]```
# /dev/hda7
UUID=the_code_you_got /home ext3 nouser,defaults,atime,auto,rw,dev,exec,suid 0 2
```[FONT=Verdana][SIZE=2]Now reboot and pray :) If your system boots up fine you should change your fstab back again to read [/SIZE][/FONT][FONT=Verdana][SIZE=2]```
# /dev/hda7
UUID=the_code_you_got /new_home ext3 nouser,defaults,atime,auto,rw,dev,exec,suid 0 2
``` and reboot again.[/SIZE][/FONT]
[*][FONT=Verdana][SIZE=2]**Delete **- OK, you're back to your old, clogged system. It is time to delete your old /home and create some space! To do so open a shell and [/SIZE][/FONT]```
cd /home
```followed by ```
sudo rm -R *
```. Once this is done change your fstab again to read ```
# /dev/hda7
UUID=the_code_you_got /home ext3 nouser,defaults,atime,auto,rw,dev,exec,suid 0 2
```and reboot.:guitar:
[*]Repeat steps 4 to 6 if you need to free up more space and export your /usr directory as well.[/LIST]

---

### Post by LeoSolaris on 2008-03-17
Ok, I have a question!

I currently have 3 (technically 5) partitions. First with XP, the second is an 'empty' partition with fat32 for swapping files back and forth between Linux and XP, then Ubuntu on the third. (Linux swap is taking up the fifth, and an extended partition, so it's technically two partitions all by itself)

I am thinking about dumping XP, making a 30 Gig Logical partition by extending the logical partition around the swap, and making a couple of paritions within that logical partitions few a few /root's for a couple of distros. I would like the rest of the 130 gigs to be a pair of partitions for /home and /usr for all of the programs and personal files, that way, I can get to all of my things from Distros like Arch that start themselves out as little more than the 'background' for the GUI 'foreground'

Maybe just making a giant /home space for the different distros to share, with the same user name and password for them all? That would let me have different programs on different distros...

Or if a different configuration would work better, please let me know. I am new at this part of Linux, and I would like to get things set the way I like before too much irreplaceible stuff gets put on my system. (Incase I royally screw up)

This summer I am going to by buying a USB harddrive to clone all of what I have on my system, so I can be a little more free with my partitioning set up. Less fear of data loss.

Thank you!
Leo

---

### Post by perixx on 2008-03-17
Hi LeoSolaris,

> First with XP, the second is an 'empty' partition with fat32 for swapping files back and forth between Linux and XP, then Ubuntu on the third. (Linux swap is taking up the fifth, and an extended partition, so it's technically two partitions all by itself)

I read that like you have 3 primary partitions (XP, FAT32 and extended - containing Ubuntu and swap and you've got some 30gig left in that extended partition?).

I don't know how many OS's you want to install there, but depending on the type, 8-10 gig is the minimun to be on the safe side, for each, I'd say. Unless you install some micro-distros like Puppy or DSL. Keep in mind though, that you can only create a maximum of 4 primary partitions per drive (an extended partition counts as primary), so you should install everything that's not necessarily in need of a primary partition (i.e. Windows) in a logical partition in your extended partition. There's only one possible extended partition, but I know of no limitations regarding the number of logical partitions it can contain...

Have a look at this great site - you'll find pretty much everything you need about dualbooting here... 
[http://users.bigpond.net.au/hermanzone/]("http://users.bigpond.net.au/hermanzone/")

regards,

perixx

---

### Post by impert on 2008-03-17
Hello Leosolaris,

> Maybe just making a giant /home space for the different distros to share, with the same user name and password for them all? That would let me have different programs on different distros...


Here are three links that might help:

[http://tldp.org/HOWTO/Partition/]("http://tldp.org/HOWTO/Partition/")

[http://http://www.overclock.net/linux-unix/11208-linux-partitioning-guide.html]("http://http://www.overclock.net/linux-unix/11208-linux-partitioning-guide.html")

and especially:
[http://http://linuxhelp.blogspot.com/2006/01/effective-partitioning-how-and-why-of.html]("http://http://linuxhelp.blogspot.com/2006/01/effective-partitioning-how-and-why-of.html")
Note the replies of BTrey and RavindranathY to this post - they seem to be pertinent to what you want to do. It seems there are pitfalls.

Cheers

---

### Post by ingo on 2008-03-17
Hi there,

in retrospect I should apologise for the apparently chaotic howto. I didn't bother even looking at it until I was alerted to the blkid command. Not sure that was a good idea ;)

However, your post raises some good questions about how to plan for a future proof systems and there are some things you need to take into account:

First off - you need one swap and one swap only. Different Linuxes share the same swap. In case of two disks it makes some sense to have a swap on each disk for faster access times.

Second off - each Linux has its own fairly similar directory structure. However, directories are not interchangeable. /usr or /etc for example simply have to stay under their root, sharing them is gonna leave you in all sorts of trouble with different kernels and different dependencies and everything not working. The only two you can sort of share are /home and /boot. 

Third off - 10GBs is ample for each root (i.e. Linux). I have never managed to exceed 7GB for root and I install and tinker with a decent amount of software...

Fourth off - Linux does not give a toss about primary or logical partitions. That is MS speak and MS limitations (i.e. you can have any number of Linux operating systems in logical partitions).

Finally, make a table of your proposed setup and post it here. We'll make it future proof :)

---

### Post by xzero1 on 2008-04-30
My disk (dual boot xp) has the following partition layout:
5G         ntfs primary
24G      ext3 Ubuntu
125G   unallocated
125G   extended
2.8G    unallocated ?!??
125G   ntfs primary (program files)

I would like to create partitions 3 partitions in the 125G unallocated space for linux but there seems to be the 3 primary + 1 extended rule preventing me from doing this. I don't have enough space to move the 5G and 125G ntfs partitions to another drive (move windows). Is there any way to accomplish this without losing xp access to the programs on the 125G ntfs partition?

---

### Post by ingo on 2008-05-01
Could you post the output of ```
sudo fdisk -l
```That way we avoid any potential misunderstandings...

---

### Post by xzero1 on 2008-05-01
Disk /dev/hda: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf13af13a

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         634     5092573+   7  HPFS/NTFS
/dev/hda2             635        3773    25214017+  83  Linux
/dev/hda3           20059       36484   131940410+   f  W95 Ext'd (LBA)
Partition 3 does not end on cylinder boundary.
/dev/hda5           20059       36484   131937088+   7  HPFS/NTFS

Disk /dev/hdb: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1b50c18d

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       12748   102398278+   7  HPFS/NTFS
/dev/hdb2           14754       14946     1550272+  82  Linux swap / Solaris
/dev/hdb3           12749       14753    16105162+  83  Linux

Partition table entries are not in disk order

---

### Post by ingo on 2008-05-01
OK, so 
hda1 = M$ - primary
hda2 = Linux - primary
SPACE
hda3 = extended
hda5 = M$ - logical 

hdb1 = M$ - primary
hdb2 = swap - primary
hdb3 = Linux - primary

So far so good. hdb appears to be full in any case, so you must be talking about the space between hda2 and hda3 - right?

As far as I can see there is absolutely no reason (apart from M$) to create however many _logical_ partitions you fancy in that space. 

I say "apart from M$" 'cos I am not sure whether they like you stuffing a partition in front (cylinders), yet behind (numbering) one of the partitions they access. Their letter system being extremely limited in its scope my guess is that you will have to tweak your M$ after having created the desired partitions.

As for the how? I haven't got a clue about M$ - think there is a T-shirt with the imprint "No, I won't fix your Windows" - should get that really ;)

Sorry I cannot be of more help. You can what you want to do quite easily under Linux, but M$ is a closed book as far as logic goes.

---

### Post by xzero1 on 2008-05-01
Thanks for your time. I guess I'm going to have to bit the bullet and create a pure Linux drive.

---

### Post by CPKS on 2008-09-19
There's no problem mounting /home on a new partition. Some advocate a separate partition for /var. I tried it - don't! /var is used during the boot process before /var gets mounted.

---

### Post by Shaoline on 2008-09-19
> **ingo said:**
> [FONT=Verdana][SIZE=2]
[*]**Check **- OK, the hardest bit is done. It is not a bad idea before wiping your original home to check that what you have done is actually working. So let's tell the system that /dev/hda7 is going to be your /home partition. Again, you need to edit your fstab and adjust the following [/SIZE][/FONT][FONT=Verdana][SIZE=2]```
# /dev/hda7
UUID=the_code_you_got /new_home ext3 nouser,defaults,atime,auto,rw,dev,exec,suid 0 2
``` to read [/SIZE][/FONT]```
# /dev/hda7
UUID=the_code_you_got /home ext3 nouser,defaults,atime,auto,rw,dev,exec,suid 0 2
```[FONT=Verdana][SIZE=2]Now reboot and pray :) If your system boots up fine you should change your fstab back again to read [/SIZE][/FONT][FONT=Verdana][SIZE=2]```
# /dev/hda7
UUID=the_code_you_got /new_home ext3 nouser,defaults,atime,auto,rw,dev,exec,suid 0 2
``` and reboot again.[/SIZE][/FONT]

Wouldn't these steps intervene with the original /home line in fstab?
Maybe you should mention to comment it out before reboot?

Thanks for nice tips! :)

---

### Post by zelhar on 2008-09-20
Hi guys, I read  here that a /HOME partitions can be 'sort off' shared between several distros, would you care to elaborate the pros/cons for that ?

* Bonus Q: How much space should I reserve to the /HOME partition if I keep all my docs and multimedia in a different location ?

---

