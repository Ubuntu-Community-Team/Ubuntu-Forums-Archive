---
title: "[SOLVED] GParted live CD running, now what?"
date: 2008-07-23
forum: New to Ubuntu
---

### Post by germanix on 2008-07-23
As I have explained in a previous post, I would like to format the HHD on my laptop, there by removing XP and installing Ubuntu. To do this I downloaded the GParted live CD. I have started this and I see that there are various partitions on this drive.
/dev/hda1 file sysrem ntfs
/dev/ hda3  extended
/dev/ hda5 ntfs
/dev/hda7 Linux-swap
I have never used Gparted before and have no idea how to proceed to format this whole drive. I only need one partition in the end, so I want to remove all.
Please could anyone tell me how do I get Gpard to format this drive?
much appreciated

---

### Post by Potatoj316 on 2008-07-23
If you want to clear the HD to install Ubuntu and you want nothing but Ubuntu on it you can just use the ubuntu install disk and tell it to use the entire disk.  

If you want to use gparted I would sugest deleting all the partitions and then creating new partitions to match what you want your disk to look like after you install ubuntu.  You will need an ext3 for all your files and a linux-swap for the swap space (about double what you have in physical RAM)

---

### Post by northern lights on 2008-07-23
Delete all existing partitons and create a new one. All necessary steps can be taken via the icons in the gparted top menu.

Still, why do you want to do this in the first place?

Flip in the regular Ubuntu LiveCD, run setup and during the process, partiton the whole thing...

---

### Post by drs305 on 2008-07-23
Here are some general guidelines.

If you want to remove partitions and start over, any data on the partition will be destroyed. Make sure you have made copies of any files you wish to keep.

To perform any action with gparted, the partition must be unmounted. There is an option for that under the Partition option.

Before you can see and perform any partition action, the partition must be selected by clicking on it. When you do that, the partition will have a highlighted border around it. Then you can select the action you wish via the Partition menu.

In your case, if you want a completely fresh start, unmount each partition, select Delete, and then click on the apply button. When you are finished with that step, you will have no partitions listed.

You will want at least two, and perhaps more, partitions. The main partition should be formatted to ext3. You also need a linux-swap partition - it is one of the formatting options when you create a new partition. It should be twice as large as your RAM (e.g. 2GB RAM, 4GB swap).

Here is a general recommendation:
One partition 15GB formatted to ext3 - This will be your root partition for system files.
One partition 2-4GB (twice your RAM size) formatted to linux-swap. This is the linux swap partition.
One partition with all the rest of the space formatted to ext3. This will be your home/data partition on which you keep your data and which contains your individual ubuntu/linux configuration/customization files.

Or you can let the install CD to all of this automatically and it would be easier.

---

### Post by immerohnegott on 2008-07-23
Guten Tag.

I would proceed in German, but my ability to speak the language is a bit rusty.

There is a far easier way to do this than going through the GParted live CD. If you plan on installing Ubuntu, just put the Ubuntu Live CD in and boot up. When you get to the partition menu (which uses GParted), just select the option to "Erase entire disk". This will remove all of those partitions and create two new ones - one for your linux filesystem and one for swap.

If you're dead-set on using the GParted disc, load it up and right click on each partition - in that menu click delete. Do this to each one and write the changes to disk (the circle with a right-arrow in it under the toolbar). At this point you should have a clean drive. Partitioning for linux can be done when you install OS.

NOTE: If the option to delete a partition in Gparted is grayed-out (unusable), click "unmount volume" in the right-click menu. Gparted does not allow you to edit partitions that are currently mounted (i've never used the GParted CD, so i'm not sure how it treats volumes).

---

### Post by germanix on 2008-07-23
Thank you very much Potatoj316. This has solved my problem.

---

