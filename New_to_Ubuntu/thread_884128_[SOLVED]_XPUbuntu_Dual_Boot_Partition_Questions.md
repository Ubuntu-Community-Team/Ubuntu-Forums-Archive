---
title: "[SOLVED] XP/Ubuntu Dual Boot Partition Questions"
date: 2008-08-08
forum: New to Ubuntu
---

### Post by intrusion on 2008-08-08
Hello!

I am trying to get my laptop to dual boot XP and Ubuntu with a FAT32 shared partition and a separate /home partition.

I installed windows on the first partition, and set up the other partitions in GParted from the liveCD as follows:

primary: NTFS   XP             -30gigs
primary: FAT32  shared data    -174gigs
extended:
         EXT3   for home       -2gigs
         EXT3   for root       -30gigs
         SWAP                  -4gigs (2gigs RAM)

Now I am at the stage of installing Ubuntu.

1) Should I mount the first (XP) partition as /windows?
2) Should I mount the shared partition at all?  (It said if I didn't, it wouldn't be used).
3) Is there anything I need to do special for the dual boot (Grub I assume?) to work with this setup?  Something like manually setting root partition to bootable or something to do with the boot loader in the advanced tab at the end of the install?

Thanks very much for your time and assistance.

---

### Post by WRDN on 2008-08-08
You don't need to mount the Windows or shared partition.
During installation at the Partitioning stage, select Manual. Now, select the partitions for home and root. For the home partition you created, set the mount point as "/home". Similarly, for the root partition, set the mount point as "/".

---

### Post by Enternald on 2008-08-08
I can answer in your question:
1) yes if you need, but only It will be mounted if there was clean shutdown. Of course you shouldn't delete system files while in linux.
2) Yes you can. As far as I use ubuntu there were no problem at all (even with ntfs partitions, except few atributes not working as root and users privilegies bug, but everything is OK.
3) Nothing special except if you want automaticaly mount some partitions which were not alocated when you installed linux(for automatic choose config something in config file which is named fstab, but I'm not sure.) normaly you need only double click disk icons in places menu. Grub will work automaticly, so don't worry.
Of course if you are security fanatic, you'd better not do the first thing, but nothing should hapened only througt the stupidity! :) 
One more thing you can use linux partitions in windows if you in example ext2fsd (works with both ext2 and ext3). So good luck

---

