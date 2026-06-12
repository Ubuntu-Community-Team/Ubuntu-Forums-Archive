---
title: "Install ubuntu over an existing Windows XP in C drive without disturbing other drives"
date: 2012-09-29
forum: New to Ubuntu
---

### Post by gviswanath18 on 2012-09-29
Hi,

I have been using Windows XP SP3 for quite a long time. But recently I have been getting quite a lot of BSODs.:(

So I have decided to change my OS to Ubuntu. I have downloaded the 12.04_Live distro and have prepared my USB stick with the ISO using Unetbootin.

I have 4 partitions as described below.

1. C:\ 50 GB - Windows XP is installed in this drive
2. D:\ 100 GB
3. E: \ 150 GB
4. F:\ 200 GB

My intention is to completely format the C drive and install Ubuntu in that partition. I do not want to disturb my other partitions as they the backup of all my files.

How do I proceed with this? I am apprehensive that my data in other drives may get formatted and lost. Any help on the instructions would be greatly appreciated.

Thanks,
Viswa

---

### Post by kc1di on 2012-09-29
hi gviswanath18 & Welcome to Ubuntu,


you can go ahead with the install when it get to the disk partitioning part you want to select do something else the tell it to use the c/ drive which in Linux will should be sda1 from what you've listed in your e-mail. 

Good luck it should be no problem once your sure of what you are doing you may want more that the 50 Gb for Linux though.

---

### Post by DogMatix on 2012-09-29
If any of the data in the partitions D: E: and F: is that important I would make an external backup, ie. to a different HDD or DVD or USB. A backup on paritions of the same drive is never that secure. If the drive failed data on all partitions would be lost.

---

### Post by kc1di on 2012-09-29
Very good advice DogMatix

---

