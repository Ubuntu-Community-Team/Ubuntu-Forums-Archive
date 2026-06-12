---
title: "[SOLVED] reinstall ubuntu"
date: 2008-06-17
forum: New to Ubuntu
---

### Post by xdarkday on 2008-06-17
I have a ubuntu install and also have a windows install. I have that set up where you can boot to either.

I was wondering if I can re-install ubuntu, but keep my windows partition intact. I have searched for help but gave up.

---

### Post by kool_kat_os on 2008-06-17
ya...iv done it a few times...but the last time it corrupted my windows partition and i had to reformat...so backup.backup.backup

---

### Post by xdarkday on 2008-06-17
I know to back up. I want to know the best way to start a fresh install of ubuntu while keeping my windows partition. I dont care for anything on my ubuntu install, just my XP.

---

### Post by geezerone on 2008-06-17
If you are to use the same partition you have to format the root (/) partition at the very least so should be a matter of doing an install with the custom settings for the partitioning tool.

---

### Post by avtolle on 2008-06-17
First, find out the linux name for the partition where you have the Windows. From terminal, sudo fdisk -l will give you the current partition set up (I suspect it will be on the first partition, but check it and write it down for reference).

Second, start the installation. When you get to the partitioning, select manual, delete the existing Ubuntu partitions (don't touch the Windows partition), then set up your partitioning scheme as you want it. Remember to designate at least two partitions, one as / for the mount point, one as /swap.  HTH.

---

### Post by lisati on 2008-06-17
One possibility for a fresh install is to boot from the Live CD, use the partition editor to delete the Ubuntu partition, and then re-install. When the install process gets to the question about partitions, choose the "Guided - use largest free space" option.

---

### Post by annda on 2008-06-17
> **kool_kat_os said:**
> ya...iv done it a few times...but the last time it corrupted my windows partition and i had to reformat...so backup.backup.backup

always backup the most important data! that said, in my 30+ install count experience on many machines, i have never managed to hurt windows (but no vista as yet). just be careful when you choose the partitioning and GRUB placement.

highly recommended:
> **geezerone said:**
> If you are to use the same partition you have to format the root (/) partition at the very least so should be a matter of doing an install with the custom settings for the partitioning tool.

use the custom partitioning option, and choose the old partitions (as / and swap, only / needs to be formatted)

---

### Post by kool_kat_os on 2008-06-17
Yes there is...when installing it..when installing it...when you get the the "Prepare Disk space" window...there should be a slider...just set it to the amount that you would like to give ubuntu...and your done....but all if this is if you want to install ubuntu on the same hd as your windows partition...

or just run virtualbox on windows...thats what i do

EDIT: i just realized that like 4 people posted ahead of me.

---

### Post by tim_wright on 2008-06-17
I know you've said that you do backup but here's what happens when you don't and you trust microsoft with your data...

... you lose 750gb 

So yea, my philosophy is to backup onto DVD / CD and also my 80gb removable HD :)

---

### Post by kool_kat_os on 2008-06-17
i lost 80GB:((dang it...you beat me:))

---

### Post by Zenze on 2008-06-17
I think that the best/easiest way for you to do this is from the LiveCD. Just run the cd and choose Install Ubuntu and go through the menues until you get to the partition editor. Choose manual and it will let you pick and choose what partitions you want to keep, delete, or even resize. If you want to keep XP safe all you have to do is not touch any of the NTFS partitions, those are all the windows partitions. The Ubuntu partions should be ext3 and swap. I find it easiest to just delete both the ext3 partition and the swap partition. Then you can remake both of them. Most people seem to recomend that you size the swap partition to be at least the same size of the amount of RAM that you have, but it can certainly go higher. Then the ext3 partition can take up the rest of the space. When making the partitions the default settings should be fine, just make sure the mount the ext3 partition to "/".

---

### Post by xdarkday on 2008-06-17
Sweet thanks for the quick responses. I will be back to let you know all how it goes!

---

### Post by kansasnoob on 2008-06-17
Assuming that both Windows and your old Ubuntu OS still work my preferred method is to "shrink" the old Ubuntu partition and allow at least 10GB (as little as 6GB will work but I'd recommend more) for my new install. 

Just leave the Windows partition(s) completely alone. (They're easily identified because Gparted will normally show them as either NTFS or FAT32).

This a great site for getting familiar with installation options:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by xdarkday on 2008-06-17
Well I have my new fresh install. Thank you EVERYONE who posted in this thread. All of the post here make sense, for anyone who looks at this in the future. Read them and choose which is best for you.

---

