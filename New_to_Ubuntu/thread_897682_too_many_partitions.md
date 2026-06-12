---
title: "too many partitions?"
date: 2008-08-22
forum: New to Ubuntu
---

### Post by sheroxe on 2008-08-22
Hi, im about to install ubuntu for the first time, i have never partitioned a disk before so im reading and i have a few doubts.

it says:

[I]You don't need a huge amount of space for Ubuntu. You will need enough space for the following:

Root partition - where Ubuntu is installed. This should be at least 4GB.

Home partition - where your files are kept.

Swap partition - this need only be twice the size of your memory.
 
A hard disk can only have 4 primary partitions.[/I]


Swap memory means the double of my RAM? so if i have 1024 i need to make it 2048 right?

About the warning, it says only 4 primary partitions, im looking at my disc and it's already partitioned, i have my hard drive ( C: ) and another named HP_RECOVERY ( D: )...how does this affect?

thanks in advance :D

---

### Post by insane_alien on 2008-08-22
right, i wouldn't make swap any bigger than 512MB unless you want to hibernate in which case it should be maybe 100MB greater than your RAM.

with ubuntu you can put all these partitions in a logical partition rather than a primary partition. its only windows that is eternally fussy about it.

with logical partitions you can get 16 on a disk.

---

### Post by Thelasko on 2008-08-22
You can make the root, home and swap partitions, extended partitions within one primary partition.
> Swap memory means the double of my RAM? so if i have 1024 i need to make it 2048 right?
That's old information, if you have 1024 make your swap 1024.

---

### Post by Paqman on 2008-08-22
You can break the four partitions rule by creating an extended partition and putting some/all of your others inside it. You can have as many partitions inside an extended partition as you like.

---

### Post by grEnAlEins on 2008-08-22
You do not need a home partition to my knowledge.  I installed ubuntu with only a "/" and "swap" partition.  A designated home partition is probably similar to using a second partition for user files in a windows install.  It is not needed, but can be preferred in some instances.


If you already have two partitions, then you can make two more.  Shrink down your windows partition and create "/" and "swap" partitions.

---

### Post by indytim on 2008-08-22
If you don't go the route of having a dedicated "/home" partition, you will be ok.  I strongly recommend that you do, in fact do this.  

To avoid a lot of headaches later on, I would suggest the following:
1.  De-frag your C-Drive a couple of times.
2.  Backup your critical data.
3.  Pre-partition your hard drive by:
a.  Shrinking your Windows partition down to something reasonable (will create new space).  **Do this from RIGHT TO LEFT**on the Windows partition.
b.  With the new space, create a new partition that is **Extended**
c.  Once the extended partition is created, create:
- a new ext3 partition of 4-6G
- a new swap partition of ~2G
- a new ext3 partition of whatever space you want to use for "/home" (will be used to store your "settings" and perhaps docs etc.
d.  Record the partition identifications on the 3 new partitions (i.e. sda1, sda2 etc.).
4.  Boot to your Live CD. 
5.  Choose the install and sail along until you get to the partition section. At that point, select the "manual partition" option.
6.  In the partition section identify the partitions you just set up with the corresponding function "/", "/home" & swap . Note put the "/" in the 4-6G partition.
7.  Don't forget to check the partition checkbox for the "/" partition.
8.  When prompted, take a good look at the layout of the partitions and make sure it is what you want.
9.  Proceed with the balance of the installation.

Hope this helps.

IndyTim

---

### Post by sandysandy on 2008-08-22
for creating new partitions u can use gparted

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

the gparted tutorial is here

[www.howtoforge.com/partitioning_with_gparted](www.howtoforge.com/partitioning_with_gparted)

regards

---

### Post by Thelasko on 2008-08-22
> **sandysandy said:**
> for creating new partitions u can use gparted

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

the gparted tutorial is here

[www.howtoforge.com/partitioning_with_gparted](www.howtoforge.com/partitioning_with_gparted)

regards

The LiveCD is very handy.  It's the only way I partition a drive.

---

### Post by Cypher on 2008-08-22
At a minimum you'll want to create 3 partitions, a /, /home and SWAP. You can take that a step further by breaking the / into /usr and /var as well. Having a seperate /home is crucial so that should you want to re-install Ubuntu or any other Linux distro from scratch, you can do so while leaving your /home directory intact and having the new installation just mount it, so all of your data is safe.

---

### Post by philinux on 2008-08-22
[http://ubuntuforums.org/showthread.php?t=897628](http://ubuntuforums.org/showthread.php?t=897628)

See post 10 re swap.

---

