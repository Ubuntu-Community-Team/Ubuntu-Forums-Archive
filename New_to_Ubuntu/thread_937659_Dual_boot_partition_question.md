---
title: "Dual boot partition question"
date: 2008-10-04
forum: New to Ubuntu
---

### Post by Antwon87 on 2008-10-04
I've got a system with Vista installed and I'd like to be able to dual boot in order to try out Ubuntu. I've read that I need to shrink Vista's partition and then install Ubuntu in the unpartitioned space. The different partitions needed for Ubuntu seem to make sense but what I can't find anywhere is where to put all of my files. Can I create a partition for personal files that both Vista and Ubuntu will be able to read? Or... what?

---

### Post by Elfy on 2008-10-04
USe vista to resize it's partition.

Yes - you can use a shared data or as it's likely that all the current data is on the vista partition you can access that from within ubuntu.

> different partitions needed for UbuntuYou don't need anymore than 2 - especially if you use a shared data area. You would only need 2 - one for the install and one for swap.

---

### Post by Orange_and_Green on 2008-10-04
Dear Antwon,

Welcome to the Ubuntu forums and the Ubuntu world!

While windows can only read ntfs and fat partitions, Linux has drivers that can read ntfs partitions (other than its own file system types). Which means, you can leave your files right where they are on the vista partition and read/write them from Ubuntu. Of course, it's also possible to create a separate partition (ntfs or fat) that both linux and windows can access, but frankly, why bother ;)

Do you only have one big partition on your hard drive? Most PCs nowadays come with one big first partition where windows and all the programs reside, but also with a second, maybe smaller, partition for the data. If this is your case, you might want to copy all the data from the second partition onto the vista main one, and then remove the (now empty) partition to make space for
1) a partition for the ubuntu root (mount point /), minimum 4GB, I would recommend at least 8 GB if you can spare the place
2) a swap partition (around 1GB should be plenty enough)
3) although optional, it is advisable to take all the space that is left (should be at least 1-2 GB to be safe) and partition it with a /home mount point. /home is where all the data&config files reside, so if you decide to format the root partition one day, having /home on a separate one will allow you to keep all your settings.

If, on the other hand, you only have the main Vista partition, follow forestpixie's advice and let Vista resize it first. 4-8MB for /, 1GB for swap and at least 1-2 GB for /home means it's optimal to shrink the partition by at least 6-11GB. 

With this setup, the installer will set Ubuntu to mount the vista partition automatically, you will see a nice icon that points to it on your new Ubuntu desktop.

I hope this helps. Have fun with Ubuntu, it's really great!! Good luck:KS

---

