---
title: "Hosed"
date: 2008-11-10
forum: New to Ubuntu
---

### Post by whaledawg on 2008-11-10
My machine had XP installed on it and I used partition magic to make a 2 gig partition to put Ubuntu on. I used the "install another operating system right away option" since, well, I was planning on installing another operating system right away.

Unfortunately I found out afterward that Ubuntu requires at least 2.5 gigs. Because I can't get a full install into that partition XP won't boot either so I can't adjust the partition size.

So I ask:

[LIST=1]
[*]What can I do?(besides just repartitioning everything with Ubuntu and reinstalling XP)
[*]How the hell does a 690mb CD install 2.5 gigs of stuff?
[/LIST]

---

### Post by beercz on 2008-11-10
Have you booted from an ubuntu live CD?

Try running gparted from that CD and repartition your disk.

At least you will be able to access you XP data and back it up, thus preventing it from being lost.

---

### Post by oilchangeguy on 2008-11-10
> **whaledawg said:**
> My machine had XP installed on it and I used partition magic to make a 2 gig partition to put Ubuntu on. I used the "install another operating system right away option" since, well, I was planning on installing another operating system right away.

Unfortunately I found out afterward that Ubuntu requires at least 2.5 gigs. Because I can't get a full install into that partition XP won't boot either so I can't adjust the partition size.

So I ask:

[LIST=1]
[*]What can I do?(besides just repartitioning everything with Ubuntu and reinstalling XP)
[*]How the hell does a 690mb CD install 2.5 gigs of stuff?
[/LIST]

first if all you can give to the operating system is less than 3gb of space, you're wasting your time. second boot from your windows cd, enter the recovery console. and enter the admin password, if none simply press enter to bypass the prompt. now type fixboot and press enter, type fixmbr and press enter, and type exit and press enter. and lastly, have you heard of compressed data?

---

### Post by jpoRS on 2008-11-10
oops.

---

### Post by dhtseany on 2008-11-10
A) Get to a DOS prompt and do a 
```
C:\> fdisk /mbr
```
B) Use the LiveCD to explore the contents of that partition and backup your data. 
C) As recommended above, use the liveCD to boot UB and use gparted to realign your partition tables.
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

Try those out and see where you get,

Peace
Sean

---

### Post by oilchangeguy on 2008-11-10
> **dhtseany said:**
> A) Get to a DOS prompt and do a 
```
C:\> fdisk /mbr
```
B) Use the LiveCD to explore the contents of that partition and backup your data. 
C) As recommended above, use the liveCD to boot UB and use gparted to realign your partition tables.
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

Try those out and see where you get,

Peace
Sean

fdisk /mbr works in windows 95, 98, & ME. not sure it will work with 2000 or xp. the best way is to follow the directions i outlined in post #3.

---

### Post by whaledawg on 2008-11-11
Thanks for the help guys, unfortunately it didn't work. Nor did the Symantec restore disk :(

See, the board checks the **first** partition for the OS to boot. Because my first partition was the hosed Ubuntu install nothing could fix that. 

So I'm nuking the drive and starting over. For a duel boot system, which should I install first; XP or Ubuntu?

Thanks.

---

### Post by beercz on 2008-11-11
> **whaledawg said:**
> Thanks for the help guys, unfortunately it didn't work. Nor did the Symantec restore disk :(

See, the board checks the **first** partition for the OS to boot. Because my first partition was the hosed Ubuntu install nothing could fix that. 

So I'm nuking the drive and starting over. For a duel boot system, which should I install first; XP or Ubuntu?

Thanks.
I think I would do XP first, but set it up so you leave a reasonable partition for ubuntu, including it's swap file.

Good luck.

---

### Post by billgoldberg on 2008-11-11
1. Take a look at "super grub disk".

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

It (it's a live cd) will allow you to boot into windows.

If you make the partition bigger and install Ubuntu on it, the grub will give you the choice to boot either Ubuntu or XP.

2. Compression

*(A windows XP cd is also around 700mb but when installed it will be around 4 gigs)*

---

### Post by psusi on 2008-11-11
Just use gparted on the livecd to resize the partitions, then reinstall Ubuntu and you should be set.

Oh, and NEVER use partition magic.  I have seen it munch way too many hard disks.

---

### Post by dhtseany on 2008-11-12
> **oilchangeguy said:**
> fdisk /mbr works in windows 95, 98, & ME. not sure it will work with 2000 or xp. the best way is to follow the directions i outlined in post #3.

Actually, I've had it work using the Recovery Console. However, just like years past it's still not 100% reliable.

Peace
Sean

---

### Post by psusi on 2008-11-12
> **dhtseany said:**
> Actually, I've had it work using the Recovery Console. However, just like years past it's still not 100% reliable.

Peace
Sean

fdisk is an msdos utility so it does not exist in the recovery console.  That's why they made the fixmbr command: to do what you used to use fdisk /mbr for.

---

### Post by Keen101 on 2008-11-12
Super grub Disk can usually fix the MBR.

I'd try a live-cd first to try and see if you can backup your data.

If you are reinstalling, then install xp first. And leave 5-8 gigs or more for ubuntu.

And for future partitioning stuff... use this instead...
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by Asem on 2008-11-12
to fix the mbr enter the recovery console by the windows xp cd and type 

fixmbr

---

### Post by The Cog on 2008-11-12
Don't try to create a partition for Ubuntu to install on. Instead, create an empty unpartitioned space and tell the installer to install into the unused disk space. It will create 2 partitions, a root system partition and a swap partition, and possibly also an extended partition to house logical partitions.

---

### Post by dhtseany on 2008-11-12
> **psusi said:**
> fdisk is an msdos utility so it does not exist in the recovery console.  That's why they made the fixmbr command: to do what you used to use fdisk /mbr for.

Oh wow, I can't believe I switched those 2 :)

Yes, you're correct. Try the fixmbr command from the recovery console and see if that can get you into XP.

Peace
Sean

---

