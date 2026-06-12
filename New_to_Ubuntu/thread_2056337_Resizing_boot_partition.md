---
title: "Resizing boot partition"
date: 2012-09-11
forum: New to Ubuntu
---

### Post by Pr3sh4 on 2012-09-11
Hi all, and sorry for the boring question about to be asked... How do I resize my boot partition?
 
I've seen a similar thread posted but the answer doesn't quite fit my problem, so it seems.
So, if it's not too annoying, here we go again...

I've just installed Xubuntu on my machine, running really nice and all (though there are some issues with my graphics card, but we'll see to that later...), but I wasn't very careful with partitions when installing. So this is hat my mess currently looks like:

[[img]http://img4.hostingpics.net/thumbs/mini_725722Gparted.png[/img]](http://www.hostingpics.net/viewer.php?id=725722Gparted.png)
  
I would like to partition my hard drive so that I can have 2 or 3 extra partitions to get my stuff sorted, but can't seem, from Xubuntu, to be able to do anything.
 I already once mounted the install CD from which I launched Gparted and changed the size of the partitions but it all went to hell when I rebooted, since I seemed to have erased Xubuntu at the time.
 
Question: How do I not mess up? Ah, and if I could avoid reinstalling that would be absolutely fabulous.  
 
 Many thanks!
 Judith

---

### Post by roger_1960 on 2012-09-11
Hi

Backup anything you value.

Using gparted

You need to shrink your sda1 by moving the right edge to the left.

Then move your expanded partition sda2 so it is just right of sda1 ie into the empty space.  Then expand sda2 so that it contains empty space by dragging the right edge to the right.

Then you can create extra partitions, sda6, sda7 etc within the expanded partition.

All of this has to be done while the partitions are not mounted ie by booting to and using a live cd with gparted on it.

NB, once you have shrunk sda1 you could instead use the empty space for up to 2 more primary partitions, but using the expanded partition  would allow more...

Not sure why altering the boot partition would mess up xubuntu unless you tried to move the left edge of it.

---

### Post by oldfred on 2012-09-11
Welcome to the forums.

You should  be able to use gparted from your install or download a separate gparted liveCD to edit partitions. You cannot edit while in your system, and even the liveCD usually mounts the swap partition to speed things up. So if using gparted click on swap and right  click swap off.

You can only have 4 primary partitions. You should be able to shrink sda1 your / (root) to a much smaller size. Then you can create up to 2 more primary partitions. Or you can move the start of the extended partition into the unallocated space you create and then create any number of logical partitions.

Basics of partitions:
[http://en.wikipedia.org/wiki/Disk_partitioning](http://en.wikipedia.org/wiki/Disk_partitioning)
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)
Partitioning basics with some info on /data, older but still good bodhi.zazen
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)

Resizing an Ubuntu System Partition Use liveCD so everything is unmounted & swapoff if neccesary
[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)
[http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html)

Both are liveCDs with gparted:
[http://partedmagic.com/](http://partedmagic.com/)
[http://gparted.sourceforge.net/faq.php](http://gparted.sourceforge.net/faq.php)

---

### Post by Pr3sh4 on 2012-09-14
Wow!
Thank for all that Info!

I'll test that out as soon as I can, and tell you how it all went.

Many thanks again!

---

