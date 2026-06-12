---
title: "Dual Booting Windows 7 x64 and Ubuntu - using the same Data"
date: 2014-01-29
forum: New to Ubuntu
---

### Post by David_Hall on 2014-01-29
Please do tell me if I did this right...

I did a fresh install of windows, partitioned my hard drive before the install with Gpart...

Did I do the partitions right? And is there anyway I can access my windows Data with Ubuntu so I can make changes to doc files, pictures, etc without going all the way into the data disk. etc
Basically I'm asking, how do I make my Documents, Pictures, Videos etc point to my data partition?

[ATTACH=CONFIG]249908[/ATTACH]

---

### Post by Habitual on 2014-01-29
Have a look at //help.ubuntu.com/community/MountingWindowsPartitions

partitioning looks fine.

---

### Post by David_Hall on 2014-01-29
Perfect, that's what I thought. However, I was wondering what a swap partition was... I didn't believe I needed it because I have plenty of room on my 700 gb Hitachi sshd

---

### Post by Bucky Ball on 2014-01-30
Ubuntu can read/write to NTFS, FAT and others so not an issue. Easiest to delete the (empty) directories in /home directory in / and create symlinks to existing data folders, which in the best of all possible worlds would exist on the /dev/sda4 partition. Say you mount /dev/sda4 in /mnt/data in Ubuntu. Then:

```
ln -s /mnt/data/Documents /home/username/Documents
```

... will create a symbolic link in your /home directory to the 'Documents' folder on your /dev/sda data drive. Create links in Windows also and no matter what OS you are booted into you will ALWAYS be using the same data, no redundancy or duplication.

You have to keep your personal data off the / partition in this install as you've created a partition for that situation (only 25Gb; if you're storing your data elsewhere you probably don't need more than 15).

The /swap partition has nothing to do with the size of your hard drive or the CPU specs. It is ALL about RAM, and should be 2Gb or the same size as your installed RAM if you intend to hibernate.

---

