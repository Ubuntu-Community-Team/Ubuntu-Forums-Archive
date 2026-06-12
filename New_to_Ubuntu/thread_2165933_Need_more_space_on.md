---
title: "Need more space on /"
date: 2013-08-07
forum: New to Ubuntu
---

### Post by schmitta on 2013-08-07
I need to get more space on / . /home is just below it with some free space. I have GParted. How do I release space above /home and incorporate it into root? Why does not ubuntu come with a root space requirement?

---

### Post by kevdog on 2013-08-07
If home is your last partition, you could delete it and add it to /.  Do you know the order your disk is partitioned?

---

### Post by deadflowr on 2013-08-07
It does come with a root space requirement.
When you install it states you need X amount of space to install Ubuntu.
That space is minimum requirement to run Ubuntu, that space is the minimum space needed for root.
Everything else is what you do.

Anyhoo, how much space is in root anyway?

---

### Post by Cheesemill on 2013-08-07
Can you fire up gparted and post a screenshot so we can see hpw your partitions are laid out.

---

### Post by schmitta on 2013-08-08
According to GParted my disk is partitioned as follows:
                 TYPE  NAME  SIZE     UNUSED
/dev/sda1/    EXT4 /BOOT  1.95GB  1.55GB
/DEV/SDA3/ EXT4 /          10.25GB  913.64 MB
/DEV/SDA4/ EXTENDED  128.91GB
/DEV/SDA5/ EXT4 /HOME 128.91GB 85.44GB
UNALLOCATED                5.01GB
/DEV/SDA2/ LINUX-SWAP 2.93GB

i HAVE A LOT OF STUFF ON /HOME SO I DON'T THINK i WANT TO ERASE IT.

---

### Post by sandyd on 2013-08-08
> **schmitta said:**
> According to GParted my disk is partitioned as follows:
                 TYPE  NAME  SIZE     UNUSED
/dev/sda1/    EXT4 /BOOT  1.95GB  1.55GB
/DEV/SDA3/ EXT4 /          10.25GB  913.64 MB
/DEV/SDA4/ EXTENDED  128.91GB
/DEV/SDA5/ EXT4 /HOME 128.91GB 85.44GB
UNALLOCATED                5.01GB
/DEV/SDA2/ LINUX-SWAP 2.93GB

i HAVE A LOT OF STUFF ON /HOME SO I DON'T THINK i WANT TO ERASE IT.

This looks a little complicated/dangerous to resize tbh
You would have to shrink the /home partition at the top, hope you dont lose any data, shrink the extended partition at the top too, just to get some extra space for the root partition.

Do you have another HDD you can store data on temperorily? If so, you can just copy the data from /home to that drive, remove the extended partition, expand the root partition, and put the extended partition back.

There are other options such as converting to a LVM available, but be sure you backup before you touch anything

Edit [8/13/2013]: I should probably mention that that will cause you to have to rewrite your fstab to have the new UUIDs for the new disks

---

### Post by schmitta on 2013-08-12
Thanks Sandy. I think I will do that. I will have to get a USB HDD. Should be interesting. If you are a girl I think you are cute!

---

### Post by mastablasta on 2013-08-12
you could also try somethign like ocmputer janitor or belachbit. it could be that old kernels or old updates took up the space. well that is unless you installed plenty new programes. 

i have 8 GB total (/ + /swap) on virtualbox install. of which about 6.5 GB is ooccupied (Xubuntu). i don't have GIMP installed but i do have lamp and a few other programes (e.g geany, bluefish and such). i remember once after some updates disk was full. i cleaned the old stuff (i htink with computer janitor) and there was *plenty* of space again for my tests.

---

