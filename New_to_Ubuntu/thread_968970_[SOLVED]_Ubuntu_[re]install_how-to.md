---
title: "[SOLVED] Ubuntu [re]install how-to?"
date: 2008-11-03
forum: New to Ubuntu
---

### Post by rrcs on 2008-11-03
I have been running Ubuntu 8.04 dualboot with Vista on my laptop, and have been very happy with it.

When 8.10 came out, I decided to do a clean/fresh (whichever is the correct term) install in order to learn how to do that in case I ever needed it.

At the same time, I wanted to resize my partition, taking space from my Vista/Recover partitions for Ubuntu.

I've been having a ridiculous amount of trouble with it, and can't seem to find relevant tutorials - all tutorials seem to be for installing Ubuntu dualboot with Vista. Not for reinstalling or installing a second Linux OS in addition to a Linux/Windows dualboot.

I have attached a screenshot of my harddrive partitions as they are right now. What I would like to do:

1. Add the second unallocated space (5.68 GB) to the Ubuntu 8.04 partition (sda6 77.11 GB) - can I do that by moving the linux-swap, or is moving a swap partition complicated?

2a. Either: Install Ubuntu 8.10 in the first unallocated space (13.95 GB), so I can try it out without overwriting the 8.04 just yet.

2b. Or: Install 8.10 in (first unallocated + 8.04 + second unallocated) space.

3. If not too complicated with the other things I'm trying to do, create a separate partition for /home for the 8.10 installation, since I hear it's the thing to do.

---

### Post by Paqman on 2008-11-03
What might be stumping you is that the LiveCD is trying to be too clever. To run faster it has automatically mounted your swap partition. Since you swap is inside your extended partition, it's locked it.

You need to swapoff (believe you can do this from a right click in Gparted?) which should unlock your extended partition (notice the little keys icon) and allow you to make your changes.

---

### Post by mike555 on 2008-11-03
easiest would be to install in the first (13.95 )....

---

### Post by rrcs on 2008-11-03
@Paqman: I found out how to swapoff yesterday, which allowed me to move the unallocated space I had freed from the BOOT (Vista) partition to sda1, as well as shrink the Recover partition.

But is it possible to move the swap partition, and will I need to make changes in Ubuntu 8.04 so that I knows where it's gone to :o) ?

@mike555: I found a tutorial the other day (I thought at psychocats, but I can't find it again) which said to reinstall you just needed to "destroy" (which I assume is the same as delete?) the partition, then restart installation, and the installation program would automatically suggest to install in the empty space.

But the installation program does not suggest to install in the 13.95 GB unallocated space (it suggest shrinking the 8.04 partition to make room for it), and when I choose manual and point at the unallocated space, I get a message about no rootfilesystem being defined (message is in Danish) - I then tried formatting the unallocated space as ext3, but that didn't seem to make any difference.

---

### Post by Liviu-Theodor on 2008-11-03
This is no easy task what you want to do, but it is possible. When you defined manually the partitions, have you declared also the mount points? Maybe you have forgotten this, as doing something manualy implies also the partition editor does not mount the partitions for you, but you must define them.

---

### Post by rrcs on 2008-11-03
I definitely have not gotten as far as declaring any mount points, as I don't know how to do this :)

Would it be easier, then, to delete sda6 (8.04) and sda7 (linux-swap), and make everything between BOOT and RECOVER one big unallocated space, and install 8.10 there? (And will I need mount points for that, too?)

---

### Post by Paqman on 2008-11-03
> **rrcs said:**
> 
But is it possible to move the swap partition, and will I need to make changes in Ubuntu 8.04 so that I knows where it's gone to :o) ?


No, you can move it about, no problem. The only time your current install might get confused is if you deleted it and recreated it, but that's also fixable by editing /etc/fstab.

All you need to do for your installation is to make an ext3 partition for / and one for /home. Then pick manual partitioning, specify the mount points (/, /home and swap) to the right partitions and you're in business.

---

### Post by rrcs on 2008-11-04
Incorporated both free spaces into Ubuntu 8.04, which is now not quite stable (weird at start-up and shut-down). But I assume I can figure out how install Ubuntu 8.10 over it, so will try that at some point.

---

### Post by Liviu-Theodor on 2008-11-04
> **rrcs said:**
> I definitely have not gotten as far as declaring any mount points, as I don't know how to do this :)

Would it be easier, then, to delete sda6 (8.04) and sda7 (linux-swap), and make everything between BOOT and RECOVER one big unallocated space, and install 8.10 there? (And will I need mount points for that, too?)

Maybe this will help you:
[http://ubuntuforums.org/showthread.php?p=6062800#post6062800]("http://ubuntuforums.org/showthread.php?p=6062800#post6062800")
[http://ubuntuforums.org/showthread.php?p=5963236#post5963236]("http://ubuntuforums.org/showthread.php?p=5963236#post5963236")

---

