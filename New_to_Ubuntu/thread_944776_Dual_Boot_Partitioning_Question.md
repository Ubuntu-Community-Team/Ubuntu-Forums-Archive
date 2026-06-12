---
title: "Dual Boot Partitioning Question"
date: 2008-10-11
forum: New to Ubuntu
---

### Post by locbart5 on 2008-10-11
I'm new to Ubuntu and preparing to set up a laptop with a newly installed harddrive as a dual boot Ubuntu/XP machine.  I would like to set up a partition that can be used by both OS's, where I would store most files.  My initial thought is to set up a FAT32 parition when I install Ubunutu.  Here are my questions:

1. I currently have a 7 GB recovery parition (which I'd like to keep) and the XP NTFS root parition. Ubuntu will need its own parition as well as a swap parition.  If I add a FAT32 file parition, that's 5 total.  I read on the Ubuntu install documentation that one drive can only have 4 paritions.  Will I need to use a logical partition to subdivide between the swap partition and the FAT32 partition?  Or, is there a better way to go?
2. Do I necessarily need to use the FAT32 format for the shared file parition? I have read that Ubuntu cannot write to the NTFS.

I'm new to Linux but very excited about it.
Thanks

---

### Post by jbrown96 on 2008-10-11
The nice thing about Linux is that it is compatible with almost everything, given enough time. Linux does support NTFS through the NTFS-3g project. I believe this is normally installed, but you can always manually install it with ```
sudo apt-get install ntfs-3g
```. I have a question about your computer and how you will use it in Ubuntu: how much RAM does it have, do you want to suspend/hibernate with it, and what kind of applications do you plan to run? Depending on your answers you may not need swap at all. 

There's no need to have a dedicated sharing partition. Just set up Ubuntu to mount your windows partition. Here are some steps on how to do that. All of this will be done in Ubuntu in a terminal.

1. Get your partition map. ```
sudo fdisk -l
``` This will show you all partitions. Figure out which is your Windows partition. It should be labled HPFS/NTFS (I believe). Remember the partition number; it will be of the type /dev/sda2 but "a" and "2" will probably be different.

2. Do an experimental mount to make sure everything works.
Create a directory ```
sudo mkdir /media/windows
```
mount the partition ```
sudo mount -t auto /dev/sda2 /media/windows
```
You should be able to navigate to /media/windows and find your files. If that worked ok, then we want to make it permanent.

3. edit your fstab. I like vi, but you should probably use gedit/kate when you're beginning. Make a backup ```
sudo cp /etc/fstab /etc/fstab.back
``` (If something gets messed up, do this command again but reverse the two files).
Read this article and post back with questions. [http://www.tuxfiles.org/linuxhelp/fstab.html]("http://www.tuxfiles.org/linuxhelp/fstab.html")

A note on errors: If you don't properly unmount NTFS, it will be marked as dirty. Ubuntu won't mount it unless you force it. If you ever get errors about not being able to mount, it is advisable to start windows and restart properly, but you can also append "-o force" (without the quotes) to the end of the mount command

---

### Post by locbart5 on 2008-10-11
Thanks for the reply - most helpful.  Keep it coming. I am using a Dell Inspiron 8200 laptop. 256 MB RAM and 160 GB harddrive. It will definitely need to hybernate.  I plan to use it for internet, email, home office, file sharing, and limited engineering applications - no gaming or programming. I use an internal wireless card for networking, and the nvidea geforce video card. It's possible that I could add RAM in the future, so I'd thought of using a 1 or 2 GB swap partition.

---

### Post by Papa-san on 2008-10-11
I have a Dell with a 180 gig hard drive. I currently have my Vista partition, a swap partition, root, and home partitions. It also contains my recovery partition, but this is designated as it's own drive (D). All 5 are on the one piece of hardware, so the 'rule' of a max of 4 doesn't really apply... You just have to make the recovery partition read as it's own drive... (How, I don't know, but it can be done!)

---

### Post by fidamehran on 2008-10-12
256 MB RAM, I think, could be a little deficient, if you would be running Windows XP, and of course also Ubuntu. I would recommend addition of some more memory if that is possible. If you manage to add up 1 GB of RAM, things should go pretty much more smoothly.
Of course, the matter is off-topic. but just felt like saying something.

---

### Post by Papa-san on 2008-10-12
I agree with the thoughts about 256 megs of RAM being a bit light. I ran an older Dell C-610 with 256, but once I progressed to Hardy, I required the alternate install image to do it. (Much less memory intensive. If you are currently unable to increase your memory, I would suggest installing an older version. Just make sure that you get one that is designated 'LTS'(Means you will be able to get help for four years after it's release date). My fav was Dapper Drake.

Just remember that you will want to set up a separate '/home' partition. This way, no matter which version you use, your personal info will be retained through future installs. (I learned this the hard way after I lost about 110 pages of a manuscript I was working on...)

---

### Post by bumanie on 2008-10-12
You do not need FAT32 as ubuntu can natively read/write to ntfs and it does so very well, and the process is stable. 256mb ram is not enough for ubuntu - offical Canonical documentation says the minimum for 8.04 is 384mb ram, although xubuntu will run fine on 256mb ram (the last ubuntu that could run on 256mb ram was 7.04).

---

### Post by locbart5 on 2008-10-13
Thanks for all the tips. I've got 2 512 MB modules on the way.  Hopefully I'll be in business by the end of the week.

---

### Post by jbrown96 on 2008-10-13
> **locbart5 said:**
> Thanks for all the tips. I've got 2 512 MB modules on the way.  Hopefully I'll be in business by the end of the week.
You should probably go with 1.1GB swap. Hibernating dumps the contents of RAM to your swap partition, so it should be at least the same size (for worst-case scenario). I like the .1 cushion because partitions can be a little different than you specify (rounding to blocks/cylinders).

---

### Post by REDace0 on 2008-10-13
Don't forget to thank the people that helped (click the star button at the bottom right of the helpful post).

---

### Post by locbart5 on 2008-10-15
Thanks for all the help and advice provided on this thread. My RAM modules arrived today.  With my upgraded memory I installed Hardy Heron successfully, and had no problem with partitioning for dual boot thanks to the slick installation program and this forum. Both OS's are running and my XP partition is mounted in my Linux environment. Connecting to the wireless network is my next challenge.  Thanks again.

---

