---
title: "Need to Restore or Expand WinXP ASAP"
date: 2008-09-17
forum: New to Ubuntu
---

### Post by A2JC4life on 2008-09-17
I had an XP machine, and added Ubuntu to it as a dual-boot machine.  So far, so good.  Problem is, Ubuntu's built-in partition manager during installation did not give me any real options, so it used ALL the free space for the Ubuntu installation, where I had been hoping to create an extra partition for both Windows and Linux to read/write dats from/to.

Anyway, so here's my situation.  I am moving in 2 days, and I need for my laptop to have more than a few MB of writeable space accessible to Windows. And in these same 2 days, I have to pack up my house.  Any changes I make to my PC have to be done NOW, while I still have my hubby's (desktop) computer available for backing up my data.  I can either A. shrink the Ubuntu partition and expand the Windows one, or B. remove Ubuntu, but I need a method that is relatively low-risk as far as wiping out all ability to get into my HDD altogether, because I can't be without a computer for the next month (and the desktop will not be available, due to the move).  I have no XP disk from which to boot, as one did not come with my computer.  My husband's computer didn't come with one, either, although he does have some huge set of "recovery" disks for his computer.  

What options do I have?  I understand that I can restore the Windows boot loader if I have an XP setup disk, but I don't.  And if I delete the Ubuntu partitions and then try to reboot, my understanding is that GRUB will lock up.  But I HAVE to have more space.  I am seriously down to only a few MB of free space, and that is just not going to work.

Thank you for any insight you might have.

---

### Post by waspbr on 2008-09-17
hmmm... 
I don't really see how the partition editor could not allow you to make a partition unless you have already 4 partitions partitions.

No matter, does your laptop have a recovery partition? Laptops generally come with a 8-9Gb partittion which can generally be burned into recovery disks just in case. 
 
you can change the size of you current partitions, just pop in the ubuntu live cd at boot, go to System>administration>Partition manager (gparted)

there it will give you an overview of your HDD, your harddrive may be mounted so right click in them and unmount if necessary, When unmounted you can just resize your partitions.

---

### Post by OffAxis on 2008-09-17
The easiest thing (after backing up all your important data) would be to boot off your ubuntu liveCD and use gparted to resize the partitions.
There's not really a need to have a partition for data exchange; ubuntu can read and write ntfs, so if you have a folder for data exchange on your windows partition ubuntu can access it.

---

### Post by Tatty on 2008-09-17
Dont panic!  This is easily solvable, all we need to do is alter your partitions.

First go into windows, run chkdsk to check for and fix disk errors, then defrag 3 times.  This is important as windows filesystems can get messy, so tidying them helps to prevent corruption

Next back up any valuable data you cant afford to lose - it is unlikely things will go wrong if you have run chkdsk and defragged properly, but computers do sometimes make mistakes.

Boot into a Ubuntu LiveCD then go to "System->Administration->Gnome Partition Editor"

This will load gparted which will allow you to edit your partitions.  You can either simply change the size of your partitions or add another data partition.  Its up to you.



In terms of the Ubuntu installer, it gives several options for partitioning your hard drive:

* It can automatically shrink your windows partition and put ubuntu in the free space
* It can wipe your entire disk and then install ubuntu
* It can find the largest block of non-partitioned space and install ubuntu into that
* Or you can manually set your partitions how you want them to be

You should probably have chosen the last option for the configuration you origionally wanted.

---

### Post by kansasnoob on 2008-09-17
You can boot your Ubuntu live CD, just be sure to choose: Try Ubuntu without any changes to your computer, then when you're booted into the live desktop go to System > Administration > Partition Editor (aka: Gparted).

From there you'll see a screen similar to this:

[ATTACH]85552[/ATTACH]

Of course your partitions are going to be quite different.

Perhaps it would be best for you to post a screenshot of yours so we could give more detailed instruction. You could do that before even booting the live CD, just go to Applications > Accessories > Terminal and in terminal:

```
sudo apt-get install gparted
```

It'll then be available following the above scrip, just don't try to make any changes while there .............. it won't work properly unless you're in the Live CD desktop mode!

---

### Post by A2JC4life on 2008-09-17
I wasn't smart enough to figure out how to work the manual partition editor. ;)  I've used one before, but this was very much not intuitive.  And it took me - literally - fourteen hours to get Ubuntu to install (I lost count of how many times I reran the installation process), so by the time it finally worked, I didn't want to mess with it!  

It didn't occur to me I could create another partition *after* the Ubuntu one (duh!).  I will try that and see if I still need help. Thanks!

---

### Post by kansasnoob on 2008-09-17
> **A2JC4life said:**
> I wasn't smart enough to figure out how to work the manual partition editor. ;)  I've used one before, but this was very much not intuitive.  And it took me - literally - fourteen hours to get Ubuntu to install (I lost count of how many times I reran the installation process), so by the time it finally worked, I didn't want to mess with it!  

It didn't occur to me I could create another partition *after* the Ubuntu one (duh!).  I will try that and see if I still need help. Thanks!

One thing. If you in fact have only a few mg's of space left on the windows partition you will sooner or later run into trouble, such as windows creating new restore points, adding new programs, etc.

I rather panic anytime I see windows using more than 75% of it's partition!

A screenshot of your drive would tell us a whole lot!

---

### Post by waspbr on 2008-09-17
you can take a screenshot by pressing the  alt + "prt scr" buttons

---

### Post by Tatty on 2008-09-17
> **A2JC4life said:**
> I wasn't smart enough to figure out how to work the manual partition editor. ;)  I've used one before, but this was very much not intuitive.

Yes i know what you mean, it took me a few installs before i understood enough to feel comfortable with the manual partition editor.

---

### Post by A2JC4life on 2008-09-18
Using the partition editor from the Ubuntu Live CD worked beautifully; thank you!!  It would not allow me to expand the Windows partition.  (I seem to recall having had the same problem with the Windows partition editor.  Stupid Windows.)  But I was able to create a shared data partition, and shift my documents and such to that, so I think I'm good to go. :)  Thank you again!

---

