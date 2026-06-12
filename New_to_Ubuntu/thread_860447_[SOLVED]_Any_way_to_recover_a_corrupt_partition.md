---
title: "[SOLVED] Any way to recover a corrupt partition?"
date: 2008-07-15
forum: New to Ubuntu
---

### Post by Brightbelt on 2008-07-15
Hi, I have a dual Vista/Ubuntu boot. (HP dv9000 laptop). I was trying to install PCLOS over Ubuntu using the same partition,...

Well I couldn't get PCLOS Gnome to format the partition for some reason, so I "tried" various things: deleting the partition, re-creating it etc. Nothing worked, so I thought 'forget it'.

But needless to say, when I rebooted, I got a grub 17 error.

I've encountered this before, so I ran the startup recovery on my Vista CD and that sometimes works. To my surprise, Vista "saw nothing wrong with the startup" and so it does nothing,

NOW, when I try to even reinstall Ubuntu from scratch over the same partition, the partition is now MISSING when I start up the partition editor during the install.

If I run the LiveCD and try to find the grub files, I get an error: no file found. If I try to run root (hd0,5) (since I think sd5 was the partition name), it says the partition is corrupt.

I know I could get out of this my choosing to write over my whole hard drive with a reinstall of either Vista or Ubuntu. But I really want to keep Vista, since MS is such an activation headache. 

I appreciate any help anyone could offer. 

Many Thanks, Frank B.

---

### Post by bumanie on 2008-07-15
Boot ubuntu live cd > sudo apt-get install gparted Then go to System --> Administration --> Partition editor. Start the partition editor and you should be able to delete or reformat the partition. As long as you only alter the former/corrupt ubuntu partition, vista will be safe. Deleting should leave 'unallocated' space, if you want ext3, format to that.

---

### Post by Brightbelt on 2008-07-15
Many Thanks Bumanie, This is one time G=parted really came through for me. 

I had to actually resize (shrink) the whole Vista partition again to get a partition set for Ubuntu.G-parted not only let me resize the Vista partition, it did so with no damage or disruption to my Vista desktop. It kept all the data and Vista install intact.

Things are back in order and I didn't lose Vista (I just don't want any re-activation headaches etc).

Again, Many Thanks, Frank B.

---

