---
title: "how to install windows without killing ubuntu"
date: 2012-01-10
forum: New to Ubuntu
---

### Post by ilikelinuxitisthebest on 2012-01-10
i have ubuntu.  i want to install windows on my computer in a seperate partition. how do i do that?

---

### Post by wildmanne39 on 2012-01-10
Hi, here is a link that will walk you through the process.
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
Thanks

---

### Post by Double.J on 2012-01-10
> **ilikelinuxitisthebest said:**
> i have ubuntu.  i want to install windows on my computer in a seperate partition. how do i do that?

Hi there!

1)back-up

2)boot the live cd and load gparted.

3) the goal here is to shink then move your partition(s) such that you create space of atleast 40GB to the far left(start) of the drive. If you're wanting to install windows/vista/7/8 you need to have 2 primary partitions available.

4) Create 1 40GB fat partition (sometimes windows and gparted disagree about ntfs)

5) Move grub off of the mbr to the root partition. Follow this [guide]("http://www.dangibbs.co.uk/journal/repair-restore-grub-2-with-ubuntu-10-04-live-cd") - making sure to install grub2 to the ubuntu partition as called in gparted - for example /dev/sda1 not /dev/sda

6)restart with the windows disk, install as usual, once completed install [easybcd]("http://neosmart.net/EasyBCD/") to manage the booting process and delete any entry it sets up for linux. Then add one - choose grub2 and call it ubuntu, then write mbr - that should be it!

---

### Post by Bucky Ball on 2012-01-10
Don't bother about making partitions (FAT or otherwise). Just leave about 40Gb free space at the beginning of the drive by shrinking and/or moving your Ubuntu partition(s). The Windows install will do the rest and create its own NTFS partitions (creating the FAT ones is superfluous).

---

### Post by Double.J on 2012-01-10
> **Bucky Ball said:**
> Don't bother about making partitions (FAT or otherwise). Just leave about 40Gb free space at the beginning of the drive by shrinking and/or moving your Ubuntu partition(s). The Windows install will do the rest and create its own NTFS partitions (creating the FAT ones is superfluous).

I agree it's not necessary, I only suggested as its a straight reference point on the windows installer - personal preference, I always like to have partitions defined before installing is all :)

---

### Post by ilikelinuxitisthebest on 2012-01-10
thank you all.

---

