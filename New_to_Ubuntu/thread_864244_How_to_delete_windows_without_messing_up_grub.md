---
title: "How to delete windows without messing up grub"
date: 2008-07-19
forum: New to Ubuntu
---

### Post by appi2012 on 2008-07-19
What should I do if I have ubuntu on the 3rd partiton of my hard drive, and I want to delete the first two? Wouldn't deleting them make my ubuntu be the 1st partition? How could I set up grub again? 

I have a lot of questions, but I just want to make sure I know what I'm doing before I do it.

Also, when I installed ubuntu, I gave it only 15GB of space. Now I would like to expand my ubuntu partition. Can I just use GParted on the live cd to shrink my windows partition and expand my ubuntu partition? Would that mess anything up?

Thanks in advance!

---

### Post by pavel989 on 2008-07-19
typically no, the name it got it should stick with. deleting windows (xp i assume) would only cause problems if ud tried to boot back into it from the grub menu, but that can be taken off. just be sure to keep the ubuntu partition flagged as boot and you shouldn't have problems.

On the other hand, yes you can just shorten and expand without problems.

Look at it this way, if a person grows, does their name change?

---

### Post by phidia on 2008-07-19
When you delete partitions without editing your fstab you will have some error messages during a reboot/boot up. That happens because during boot the existing partitions are compared to /etc/fstab and if there's a mismatch the shell lets you know. 

So I think it's best to edit your fstab and comment out the partitions you are going to delete.I recommend commenting out (which is the placing of "#" that number symbol without the quote marks in front of the partition line in fstab) because if you make a mistake correcting a commented out line is easier than replacing a deleted one. 

You can use cfdisk (in terminal) to edit your hard drive partitions too-but gparted can work. I don't think it will change the partition # of the the partition you leave but your partition table will be a little strange.

---

### Post by houbysoft.xf.cz on 2008-07-19
By the way, you don't need the liveCD for gparted. Just run "sudo apt-get install gparted" in your ubuntu installation, it will be lots faster than the CD :)

---

### Post by appi2012 on 2008-07-19
So can I just boot into my Gutsy live CD and delete the partitions? What would happen if I wanted to reinstall windows. Also, can I delete windows and my recovery partition, and then move my ubuntu partition to the front of the disk? Will that cause problems?

---

### Post by pavel989 on 2008-07-19
> **houbysoft.xf.cz said:**
> By the way, you don't need the liveCD for gparted. Just run "sudo apt-get install gparted" in your ubuntu installation, it will be lots faster than the CD :)

they want to edit their ubuntu partition too, and you can't unmount that while using it.

---

### Post by appi2012 on 2008-07-19
Say something did happen during the deleting. Could I use super grub disk to boot if that happened?

(When I say "something happened", I mean that I wasn't able to boot, not that I deleted my ubuntu partition)

---

### Post by pavel989 on 2008-07-19
yep. or u can fix grub from the super grub disk, or fix it from a live cd.

---

### Post by Victormd on 2008-07-19
Yes, supergrub would solve your problem...
If you need tips on editing your fstab, take a look at my signature, even though it's for automount, it shows how to edit fstab and how to determine what should be done...

---

### Post by richardjennings on 2008-07-19
Are you looking for a "ubuntu only system using all available diskspace"?

if so, you are probably best off doing a clean install. It depends how large your disk(s) are. If you have space to leave your current Ubuntu installation alone, and still have ample for a new installation, I would:

delete the windows partition after backing up anything you want to back up to what ever medium(s) you have available.

from the ubuntu Install disk partitioner:

If your current swap partition is not at the start of your drive, set a swap partition at the start of the drive & delete the old swap partition.

set a root partition after the swap partition. This partition need only be 20 to 30GB. Make it larger if you want. Remember to ensure the boot flag is on.

set a home partition after the the root partition to use all remaining space. (ensuring that the old ubuntu install partition is not deleted.)


Once the install is finished, you will have a system booting a clean install from the fastest part of the drive. Boot into the new install, you will have access to the files in the old Ubuntu partition. Copy accross any config files you need, drivers you compiled etc...

Once you have set up your new install how you want it and you are sure you dont want the old install for any reason. Boot into the livecd, delete the ubuntu partition and expand your new home partition to use up the rest of the space.

The advantage of doing it this way is:

moving partitions is not an easy task.

your home partition (your media files etc..) will be seperate from the Ubuntu root partition. Flexibility!

You are not likely to have any problems other than those associated with setting up an Ubuntu install, i.e wireless drivers etc...

You will have a clean install.


The disadvantages:

might take you a while to get everything the way you want it.

---

### Post by phoenix_abhi on 2008-07-19
Firstly the Grub is not installed in Windows partition. By deleting the windows partition, GRUB loads normally and u can boot to Ubuntu from there.

Secondly - Do u want to get rid off from the windows permanently, then do a fresh installation of the Ubuntu by backing up all the data.

thirdly for Backing up all the upgrades and new apps installations use [COLOR="SandyBrown"]APTonCD[/COLOR]which makes a ISO of the all those. After re installation u can re apply that image on Ubuntu

---

### Post by proevofanatik on 2009-05-29
im sorry for bringing back an old post. but i had windows xp home installed then i dual booted ubuntu 9.04. the problem is i must have installed windows on my other hard drive at one point, i keep getting 2 windows xp options in grub when i try to dual boot windows and ubuntu. one of the windows in grub is dead but for some reason it keeps appearing when i dual boot. how do i get rid of this entry on grub?

thanks

---

