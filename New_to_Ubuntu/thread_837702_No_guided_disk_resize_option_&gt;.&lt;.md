---
title: "No guided disk resize option &gt;.&lt;"
date: 2008-06-22
forum: New to Ubuntu
---

### Post by Ericthegreat on 2008-06-22
Well got onto the live cd for Ubuntu (posting from in it) but when i go through the install process when i get to the step where you make a partition i only have the option to make a partition i only have the option to use entire disk or manual, What should i do? I only want to make a 10 gb ubuntu partition (and w/e extra for swap or w/e i need?) for now and i really dont want to lose my windows data. Ubuntu 8.04 and trying to Dual Boot.

---

### Post by jimv on 2008-06-22
Do it manually and create a 10 gb ext3 partition and a 1 gb swap partitition.

---

### Post by Ericthegreat on 2008-06-22
ty but how do i do that safely without overwriting the windows partitions?

---

### Post by Ericthegreat on 2008-06-22
I also heard i need to defrag my windows partition first or it might overwrite some of my data? is that true?

---

### Post by Ericthegreat on 2008-06-22
could anyone please help?

---

### Post by biohypnotix on 2008-06-22
I've never used Manual by itself for Ubuntu or other operating systems. I always had my disk pre-partitioned using [[color=blue]GParted LiveCD[/color]](http://gparted.sourceforge.net/) first. Just know which partition you have Windows on as to not delete nor shrink it below say 10GB (personally I kept the Windows partition around 20GB). I would create three new partitions for Linux. My personal and popular scheme was one for root, swap, and home. I give root about 5-10GB, swap 1GB, and all remaining space for my home directory partition. Once I have the hard drive partitioned using GParted LiveCD, I would just reboot, pop the Ubuntu LiveCD back in and install using the partitions I just created with GParted LiveCD. I picked the "Manual" option in Ubuntu LiveCD and went from there.

And backin up all your important files you have on your Windows partition (music, work, bookmarks, e-mail/IM contacts, logs, etc) before doing anything wouldn't hurt.

Also check out: [[color=blue]https://help.ubuntu.com/community/WindowsDualBoot[/color]](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by Biggy on 2008-06-22
Download and burn [PartedMagic]("http://exo.enarel.eu/mirror/partedmagic/pmagic-2.2.iso")

boot from partedmagic live cd
 open gparted and create new partition
don't worry for all files,folders in hdd xp 
windows work after new partition resized.

for more info how to use PartedMagic go [Here]("http://partedmagic.com/wiki/PartedMagic.php?n=PartedMagic.UsingGParted")

---

### Post by Kronie on 2008-06-22
zomg.. dude, heres the way out. go to livecd, system->admin->partition manager. THATS IT! you dont need to download anything, its already there! then when u open it, slice off a chunk from the biggest partition you have(if there;s windows on it, defrag it) and then format the new partition to EXT3

---

### Post by tysonh on 2008-06-22
I just got my laptop dual booted with xp and ubuntu.  All I did is once I got to the partition set up in the ubuntu install I resize the windows(ntfs partition).  All ya gotta do is shrink the windows down to whatever you want. make a ext3 partition for ubuntu and a swap partition.  I usually make my swap partition double the max memory I can have in any given machine depending on how new the hardware is.

To dual boot all you need is 3 partitions. 1 windows partition, 1 Ext3 partition and a Swap partition.  If it asks you leave the bootable flag on windows and I marked do not use on my windows partition so ubuntu wouldn't mess with it.

After all that you can pick your OS at boot.  Good luck.

---

### Post by jimv on 2008-06-23
Don't delete your Windows partition then.  When you use manual mode, it's not going to do anything that you don't tell it to do.  It should be intuitive enough for you to figure out pretty easily.

---

### Post by Stefanie on 2008-06-23
> **Ericthegreat said:**
> Well got onto the live cd for Ubuntu (posting from in it) but when i go through the install process when i get to the step where you make a partition i only have the option to make a partition i only have the option to use entire disk or manual, What should i do? I only want to make a 10 gb ubuntu partition (and w/e extra for swap or w/e i need?) for now and i really dont want to lose my windows data. Ubuntu 8.04 and trying to Dual Boot.

i had the same problem when i installed gutsy. you probably need to run chkdsk before you can resize your partition. if you're using windows xp, just go to my computer, right-click your c-drive and select the option "check drive for errors" or something like that, i think it's on one of the tabs right above the defragmentation option. when you reboot windows should start checking your disk for errors and when that's done the "resize partition" option will show up when you install ubuntu.

---

### Post by avtolle on 2008-06-23
If the OP is running Vista and not XP, (s)he should use the Vista resize utility to resize the Windows partition. On either Vista or XP, before resizing (or attempting to resize) the Windows partition one should definitely defrag the HHD, at least twice IMHO.

---

