---
title: "cant partition free space"
date: 2008-09-14
forum: New to Ubuntu
---

### Post by jason10 on 2008-09-14
hello.  i have a toshiba laptop here that came with vista.  i now have it set up as a dual boot with ubuntu, and im having some issues with partitions..  what i WANT to do is have a reasonable vista partition, a resonable ubuntu partition and then have the rest of my free space in some 3rd partitioin that both ubuntu and win can read and write to.

the problem is that toshiba put a primary (recovery i assume) partition in the front + vista and ubuntu are primary and then my ubuntu swap came out as primary also..  when i set up ubuntu i told it to make the swap logical, but i dont think thats what happened..  i also seem to have random free space between all my partitions.  when i try to make a partition with my remaining free space i get "youcan only have 4"


to get what i have so far i used vista to shrink itself, then i used the ubuntu install to make the 50gb ubuntu and the 3gb swap.  what can i do with this free space?  do i want ntfs?  or fat32?  or what.  im pretty noob with partitions.  can i convert my swap from primary to logical?  do i really need a swap at all when i have 3gb of ram?

any help would be awesome!  thanks



[INDENT]
jason@silversat:~$ sudo fdisk -l

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7a8ba399

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         192     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         192        6719    52429056    7  HPFS/NTFS
/dev/sda3            6720       12943    49994280   83  Linux
/dev/sda4           23948       24321     3004155    5  Extended
/dev/sda5           23949       24321     2996122+  82  Linux swap / Solaris
jason@silversat:~$
[/INDENT]

---

### Post by Tatty on 2008-09-14
You cant have any more than 4 primary partitions on a hard drive.  So you probably want to create an extended partition and put your swap space and your third storage partition as logical partitions under that.

I would say ntfs would be fine for your storage partition as ntfs support is very mature in linux now, however there will be a lot of people who will recommend fat32.  Thats something you may want to do a bit of research into yourself, but its not a huge issue these days.

---

### Post by jason10 on 2008-09-14
You cant have any more than 4 primary partitions on a hard drive. So you probably want to create an extended partition and put your swap space and your third storage partition as logical partitions under that.


create an extended partition..  so that means destroy the primary swap partition i have at the end, and then make a big 88gb partition that starts at the end of my ubuntu, and put the ubuntu swap inside of that?  would that extended partition be ..a primary partition?  can i have a swap partition inside of a ntfs or fat32 partition?  

also, if i have to recreate my swap partition, does that mean i cant do it from ubuntu?  ..would ubuntu instantly die if i use ubuntu to kill its swap space?  

also, i have no idea what that sda4 thing is.  i dont remember making that..

sorry for being so noob

---

### Post by Victormd on 2008-09-14
From your screenshot, your swap is already an extended partition. You can have severl partitions inside your extended partition, but the extended partition itself counts as a primary partition. Resize your extended partition to take up the entire free space and create your 3rd partition in the extended partition. As for NTFS or FAT, I prefer NTFS, blocks are smaller and it's faster than FAT, but as Tatty mentioned, that's up to you.

It should be noted that, to resize your extended, you'll need to use Gparted from the Live CD because it contains your swap. Also, you'll need to turn off your swap partition (after booting the Live CD and running Gparted, right click on the swap partition and click on the SWAPOFF option. Furthermore, you will need to edit your fstab to match your new swap ID, you can do this from the live CD as well.

As for the 4MB free space between partitions, unfortunately that's lost space (not that 4MB matter these days) because of the block allocation on your HD.

---

### Post by Tatty on 2008-09-15
Ah! i just looked at your attached image again and realised that you already have an extended partition, that makes things much easier.

A very brief explanation:
 * you can only have up to 4 primary partitions on a drive
 * one of your primary partitions can be an Extended partition
 * an extended partition can have "sub-partitions" under it
 * you can have as many "sub-partitions" as you want in an Extended partition


If you look at your partitions, /dev/sda4 is an Extended partition, and under that you have your swap partition as a "sub-partition".

What you need to do is to expand /dev/sda4 to take up all your free space, then under that you can create a new "sub-partition" which can be your storage drive.

---

### Post by Victormd on 2008-09-15
> **jason10 said:**
> also, if i have to recreate my swap partition, does that mean i cant do it from ubuntu?  ..would ubuntu instantly die if i use ubuntu to kill its swap space?
You will have to do this from the Live CD...

> also, i have no idea what that sda4 thing is.  i dont remember making that..
That's your extended partition, you created it during your install...

---

