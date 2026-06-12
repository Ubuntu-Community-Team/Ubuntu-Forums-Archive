---
title: "Partition Issue and more."
date: 2008-11-05
forum: New to Ubuntu
---

### Post by Inapprope on 2008-11-05
Recently I tried to do a dual boot situation with Vista and Ubuntu on my Dell XPS M1330. I was having some problems with the ubuntu version after installing it (major system slowdown after a few a few minutes of rebooting). I wrote it off to the fact that I probably installed it wrong. Whatevs. 

The problem I am having now is that my hard drive is partitioned like crazy. I can't seem to merge all these rogue partitions. Right now in GParted it looks like this...

[IMG]http://i33.tinypic.com/2uqhb3p.jpg[/IMG]

Is there any way I could merge the "unallocated" and "new volume" partitions with the main "OS" partition?

Also, how would you recommend I go about installing ubuntu as the main OS with Vista already installed? I don't know how this works with Dell's, drivers, and warranty's...

---

### Post by bscbrit on 2008-11-05
I'm not an expert in this area, but have you tried simply resizing the NEW VOLUME into the unallocated space?  If you have, what happened?

For the time being, ignore the 'lost' 4.02MB - its not worth chasing!

---

### Post by haylun98 on 2008-11-05
I'm no expert but I can see the multple barriers preventing you to merge them. The sda3 is a Primary NTFS but sda5 and sda6 are FAT32 logical paritions reside within sda4, which is an extended partition.
I would boot into the NTFS OS sda3, manually copy/move those data from sda5/6 into sda3. Then use a windows partitioning tool, e.g. Easeus Partitioning (free for personal use), to delete sda5&6, then remove the empty extended partition. you can stop here if you're parparing empty space to instal ubuntu or extend your sda3 to take up the rest of the space.

---

### Post by haylun98 on 2008-11-05
just notice you already have maximum of 3 primary partitions: sda1,2&3. If you're planing to install ubuntu you need to keep and may be resize the extended partition because ubuntu need a mininum of 2 partition to install

---

### Post by mapes12 on 2008-11-05
Was the HDD setup like this when you got it?

I would delete all partitions and start again.

Advantages:
- All those nasty fat16/32 areas would be done away with, particularly the fairly useless fat16 area.
- The HDD could then be partitioned and sized to match your expected useage.
- Separate partitions could be allocated for Ubuntu /(root) and /home making any Ubuntu upgrades nice and easy in preserving files, personal settings and the like in the /home partition

Disadvatages:
- If you do not have a Windoze installation disc you're stuck.
- If windoze was activated in the last 120days (I think it's that long) on your machine then MS will not allow another activation.
- If the manufacturer of your machine setup the HDD in this way and you change it, particularly the recovery files, this may void your warranty.

---

### Post by Inapprope on 2008-11-05
I've tried deleting certain partitions and expanding the OS partition, but it wouldn't allow me to (I was using the built in Vista partitioner).

The way my HDD came was with the main OS partition, Recovery partition and Media Direct partition. I tried to make a 30gb partition to install ubuntu on, but as I said once it was installed it bogged down after a couple minutes on it every time I entered it.

Ideally I'd want ubuntu to be my one and only OS, but I don't know how to get there from where I am now. Not to mention potential compatibility issues with hardware and such.

As I said, this is a Dell laptop. I have a vista disk and a driver disk, and I've had this laptop since February.

---

### Post by bscbrit on 2008-11-05
Let me see if I understand what you want:

You have a Vista recovery disk and a driver disk, so you don't need anything that is currently on your hard drive?

You have an installation disk for Ubuntu?

SO you could install Ubuntu and tell it to use the entire disk.  It will automatically delete all the existing partitions and create the partitions it needs.

BUT this method will overwrite EVERYTHING on your hard drive.

OR install Ubuntu and tell it to use the free space.  You will then have a working Ubuntu system and it should leave your Vista intact and working also.  It will also leave any data intact.  Once you have Ubuntu working, you can research your problem in slow time and reorganise your hard disk when you know exactly how you want it organised.

Of course, I might have misunderstood what you meant by 'Ideally I'd want ubuntu to be my one and only OS', in which case can you please restate it in terms that an idiot such as myself can understand. :-)

---

