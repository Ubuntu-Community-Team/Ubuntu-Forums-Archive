---
title: "Live CD deletes Window's Partition"
date: 2008-10-15
forum: New to Ubuntu
---

### Post by Sugi on 2008-10-15
A couple of nights ago I was installing Ubuntu Hardy Heron on my laptop.  It already had a Window's partition on it.  I wanted to dual boot with the Windows partition and a Ubuntu partition.  When I was promoted to the partition section of the Live-CD. I selected the manual partition, but when I clicked on the 80 gb partition of Windows. (NOTE: I wanted to take the whole 80 gb HDD worth and resize and used the free space for linux.)  I click on edit partition and create a new partition 40 gbs worth, but when it was computing the partition, it gave me an error.  I tried again and still the same error.

So I went back to the auto-partition section and let the LiveCD split it up.  It worked, but when I got to the Desktop of my brand new partition of Linux I found something else that I didn't want.  Instead of taking the free space from Window's partition and making a new partition for Linux.  It took the whole HDD, cut it in half and gave one partition for Linux and reformat the other (Window's partition) and made it into 40 gb ext3 partition.  I lost everything on the Window's partition.

So, what happen?

Sugi

(I did back up everything, but there is a lot of programs I lost from the laptop on Windows.)

---

### Post by SpenceMakesSense on 2008-10-15
I would suggest just using the partitoin editor next time then installing
this happened to me with the fedora install it completely formatted my windows drive without me knowing.

---

### Post by SeanBlader on 2008-10-15
Free space on a windows partition isn't free space on the hard drive, it's reserved space on the hard drive. It's like the driveway of your neighbor's house, when they're not home, it's not free space. 

What you needed to do was decrease the windows partition size, ideally from windows, then use the unpartitioned space to create your ubuntu partition from the manual partition editor of the live CD.

---

### Post by bumanie on 2008-10-15
If you have not written over the disk too much, you could try to recover the windows partition (which would get rid of your new ubuntu installation in the process). You could try testdisk form [here]("http://www.cgsecurity.org/wiki/TestDisk"). Read the documentation on that site and look [here also]("http://www.users.bigpond.net.au/hermanzone/p21.html")

---

### Post by LowSky on 2008-10-15
Windows likes to use any and all of the space of the partition it has been given. What I mean is that windows will use space at the start of the partition and one toward the end and maybe some in the middle. The way to correct this is to defragment the partition from windows. Once that is done it is safer to resize a partititon without harming anything. What you did probably messed that up.

---

### Post by Keen101 on 2008-10-15
I think the latest ubuntu disks may have a bug in the partition editor. But, i can't confirm, and you might have messed up yourself. in any case i find the **Gparted Live-CD** is much better at partitioning, that the one on the ubuntu live-cd. even though many people claim they are practically the same. I don't agree with them.

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by Electron on 2008-10-15
I had a similar problem with my Ubuntu, so later on when a tried again I used Partition Magic (you can download it from distrowatch) to make my partitions and ... woola! everything work.

---

