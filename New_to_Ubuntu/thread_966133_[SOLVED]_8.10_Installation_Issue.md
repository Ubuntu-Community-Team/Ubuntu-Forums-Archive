---
title: "[SOLVED] 8.10 Installation Issue"
date: 2008-11-01
forum: New to Ubuntu
---

### Post by Abu_Dayya on 2008-11-01
I had ubuntu 7.10 on my laptop with three partitions (root, swap, home), and I decided to upgrade to 8.10. after booting from the cd and starting the partitioner, I selected manual installation (not guided). Then selected the previous root partition to install ubuntu on it, so my old home folder and data wouldn't be lost. But now after the installation is complete, my ubuntu installation is on one partition only (with new home folder), and I can see my older partition present, but I don't know how to mount it on the new home folder.

So, how can I mount it over the new home folder, and have it mounted on every boot up?

---

### Post by Abu_Dayya on 2008-11-01
Bump

---

### Post by Abu_Dayya on 2008-11-01
Another bump

---

### Post by reg4c on 2008-11-01
Am not sure, but you should've selected your old home partition during the installation and said that it should be your /home.

As for mounting:

```
sudo mkdir /mount/home
sudo mount /dev/sdX /mount/home
```
where X is your harddrive and the partition number.

Cheers

---

### Post by Abu_Dayya on 2008-11-01
So, I'll try another clean installation and specify the old /home partition to be /home/myname?

---

### Post by reg4c on 2008-11-01
No.

When you get to the partitioning part then you have to select your current partition, the one that you are using for home now, and set it to mount as /home and do not mark it for format.

Cheers

---

### Post by ugm6hr on 2008-11-01
> **reg4c said:**
> When you get to the partitioning part then you have to select your current partition, the one that you are using for home now, and set it to mount as /home and **do not mark it for format**.

Also - use the same swap partition.

And mark the / partition to be formatted.

---

### Post by CatKiller on 2008-11-01
> **Abu_Dayya said:**
> So, how can I mount it over the new home folder, and have it mounted on every boot up?

You do this by changing the FileSystem Table (fstab). Make a backup copy first (so it's easy to restore should something go wrong) with ```
sudo cp /etc/fstab /etc/fstab.backup
``` You can open the file as root (so that you can save the changes) with ```
gksudo gedit /etc/fstab
```

The structure of this file is fairly simple, and you should be able to see roughly what you need to put there based on what's there already. You need to put in a line that says which partition you want to mount, where it should be mounted, what filesystem that partition is formatted in, and some options. So the line that you put in might be something like ```
/dev/sd*XN*     /home     ext3     defaults     0     2
``` where the *X* and the *N* depend on which partition is your /home partition. *X* might be *a*, *b*, *c* or *d*, depending on which physical hard drive it is, but is probably a for the first hard drive on the first channel. *N* would be the partition number on that drive, which would be 1-4 for a Primary Partition, or 5 or more for a logical drive in an extended partition. You probably know which partition you're interested in already, but if you don't someone might be able to tell you an easy way to find out.

EDIT: You might potentially have permissions problems for the folders in the /home partition, depending on which order you added new users in for your new install. If there's only one user, then it shouldn't be a problem. If you do have problems, post again and someone should be able to talk you through it.

---

