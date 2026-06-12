---
title: "I want to install windows xp but i can't"
date: 2008-10-13
forum: New to Ubuntu
---

### Post by amazingjxq on 2008-10-13
I installed ubuntu on my entire hard disk, now i want to install windows xp. After i put the xp disk in my cd dirve, that normal setup screen didn't show up.What should i do?
I googled it and think maybe there're some problems with my mbr.

---

### Post by Elfy on 2008-10-13
If you want keep ubuntu - resize the disc from the from to allow room for xp in a new ntfs partition. Once xp is inatlled you will need to reinstall [grub]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

If you want lose ubuntu - format the whole disc to ntfs

You can use the livecd - there is a partition editor on it.

---

### Post by WWSmith36 on 2008-10-13
Windows can´t read or even see ext3 linux partitions.  Therefore when windows looks at your hard drive, it doesn´t see any free space.  You will have to boot to ubuntu liveCD and use gparted to resize you linux partition.  Then in the free space, create a primary partition and format it as ntfs.

After you install windows, you will have to reinstall grub to boot to ubuntu again.

Hope this helps.

---

### Post by ethoxyethaan on 2008-10-13
amazingjxq

you have to press a button ( F8, esc, F12) for the setup screen to appear,

i hope this helps.

---

### Post by billgoldberg on 2008-10-13
> **amazingjxq said:**
> I installed ubuntu on my entire hard disk, now i want to install windows xp. After i put the xp disk in my cd dirve, that normal setup screen didn't show up.What should i do?
I googled it and think maybe there're some problems with my mbr.

You don't have a mbr, so their can't be anything wrong with it :p .

--

Get yourself a copy of the the "gparted live cd" or the ubuntu live cd.

Boot it.

Open up gparted (gnome partition editor).

Either resize the partition and created a second ntfs partition to install Windows on, or format the entire drive as ntfs. The second will remove Ubuntu.

---

### Post by amazingjxq on 2008-10-13
Will it do some harm to resize the partition?
And what's the meaning of the three arguments(Free space preceding,New size,Free space following)?

---

### Post by dfreer on 2008-10-13
> **billgoldberg said:**
> You don't have a mbr, so their can't be anything wrong with it :p

Why wouldn't he have an MBR? That doesn't make much sense...

If the OP can boot Ubuntu, then your MBR is working just fine. If you can't load the Windows XP Disc, it shouldn't have anything to do with the hard drive's MBR (if BIOS gets to the point of loading the MBR of the hard drive, you've missed your opportunity to boot to the CD).

---

### Post by amazingjxq on 2008-10-13
OK,now i know it. I'm trying.

---

### Post by amazingjxq on 2008-10-13
I wonder how could this be possible. Does ubuntu use the hard disk continously?The data spreaded continuously?
How long would this operation take?

---

### Post by alwez_loner_TZ on 2008-10-13
Resizing you hard disk does not harm your PC it just checks for free space and then it partition from there. The best way to do it would be to format the hard disk and then Install windows then Ubuntu.

---

### Post by amazingjxq on 2008-10-13
I mean how could it possible to shrink a file system. Didn't ubuntu use the space yet ?

---

### Post by amazingjxq on 2008-10-13
Still can't do this. Just like before. I have shrinked the file system and created an ntfs partion.What's wrong?

---

### Post by rybaxs on 2008-10-13
Did you finish created a new space? (gparted/Partition Editor)

That space of the disk is where you can install your WinXP..
Its better to install WinXP before Ubuntu, because it is simple for Ubuntu to override Operating System than Winxp.

" i love the installation of Ubuntu than WinXP in means of touching other system"..

---

### Post by Orange_and_Green on 2008-10-13
Hello,

Are you by chance using a RAID or SATA controller? The original XP installer CD comes without support for most RAID or AHCI SATA controllers, so it won't see the disks. If you are using RAID or AHCI, either go to BIOS and disable RAID / set SATA to Legacy (aka compatibility) mode, or slipstream the controller drivers onto your XP CD with [NLite]("http://www.nliteos.com/")

If this applies to you and you want to slipstream, download the controller driver from your manufacturer's site and then you can follow this [tutorial]("http://komku.blogspot.com/2007/11/integrate-driver-into-windows.html").

Good luck :KS

---

### Post by amazingjxq on 2008-10-13
> **rybaxs said:**
> Did you finish created a new space? (gparted/Partition Editor)

That space of the disk is where you can install your WinXP..
Its better to install WinXP before Ubuntu, because it is simple for Ubuntu to override Operating System than Winxp.

" i love the installation of Ubuntu than WinXP in means of touching other system"..
How to completely uninstall ubuntu so that i can install winxp? Do i need to format my disk?

---

### Post by amazingjxq on 2008-10-13
> **Orange_and_Green said:**
> Hello,

Are you by chance using a RAID or SATA controller? The original XP installer CD comes without support for most RAID or AHCI SATA controllers, so it won't see the disks. If you are using RAID or AHCI, either go to BIOS and disable RAID / set SATA to Legacy (aka compatibility) mode, or slipstream the controller drivers onto your XP CD with [NLite]("http://www.nliteos.com/")

If this applies to you and you want to slipstream, download the controller driver from your manufacturer's site and then you can follow this [tutorial]("http://komku.blogspot.com/2007/11/integrate-driver-into-windows.html").

Good luck :KS
But I can install winxp using this cd before. That time i installed xp first.

---

### Post by alwez_loner_TZ on 2008-10-13
Yes you do need to format your hard disk. What you do is boot with an XP CD and then create a partition when installing. 

After you install XP, you then Boot with the Live CD for ubuntu. Follow the instructions and create the partitions as required. Ubuntu 8.04 is more user friendly with the Partitions part.

---

### Post by amazingjxq on 2008-10-13
> **alwez_loner_TZ said:**
> Yes you do need to format your hard disk. What you do is boot with an XP CD and then create a partition when installing. 

After you install XP, you then Boot with the Live CD for ubuntu. Follow the instructions and create the partitions as required. Ubuntu 8.04 is more user friendly with the Partitions part.
I can't boot from the xp cd.That's the problem.But i can boot from the live cd.

---

### Post by Elfy on 2008-10-13
You might be better creating an empty space at the beginning of the hdd with the livecd for it and leave it unformatted.

Windows does like partitions at the beginning of the drive, but will soemtimes deal with them in middle - it's obvioulsy not liking it for you.

What you want to end up with in gparted is

unallocated space |Linux drives

---

### Post by rybaxs on 2008-10-13
> **amazingjxq said:**
> I can't boot from the xp cd.That's the problem.But i can boot from the live cd.

I think when you have created an empty space, XP can find the new created empty space that you've created at the Gparted/Partition Editor. 
Thats the empty space where you need to install the XP. When you are finish installing the windows XP, Im my experience before i've encountered a problem before, that the GRUB will be gone, and you need to configure this so that you can boot both Ubuntu and WinXp.

What do you mean by XP CD can't boot? is your XP cd bootable disk?

---

### Post by alwez_loner_TZ on 2008-10-13
# I can't boot from the xp cd.That's the problem.But i can boot from the live cd.

You can install Partition magic in windows if you don't have a bootable winXP CD, after you partition you hard disk you can then boot with the LiveCD in Ubuntu.

---

### Post by stalkingwolf on 2008-10-13
are you getting any error messages when you try to boot XP?  also 
check to make sure you are still set to boot from CD and that your CD
is in the correct CD Rom if you have more than one.

---

