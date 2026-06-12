---
title: "Installing hardy heron please help"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by siretfel on 2008-05-02
hi all,

i've recently formated my laptop
i want to install hardy heron now on it
i have windows installed allready

so i'm in partitioning stage at the moment

Windows is on had1 with 20gb ntfs
i have another 20gb for ubuntu
what is the best way to partition the 20gb of disk for ubuntu?
also i don't know what to choose, meaning, i know i have to make a swap partition of about 2gb as my ram is. but i dont know if it has to be first or last and also what is the partition name for ubuntu installation: xt3 jouraling? ext2 file system? what?

thanks in advance

---

### Post by turezky on 2008-05-02
Hey,
If I had 20 spare Gb i would split it in the following way
1. 8Gb - with mount point "/"
2. 10Gb - with mount poing "/home"
3. 2Gb - with swap.
The file system is of your own personal choice.. you can use either ext3, ext2, reierFS or whatsoever. Just check what are the pros and contras for each type. I personally use ext3.
I don't think it actually matters now where do place your partitions in order. I had everything completely randomly mixed: NTFS, swap, ext3, and everything ran OK.

---

### Post by siretfel on 2008-05-02
I understand the 10GB and 2GB, what's the 8GB for?

---

### Post by avtolle on 2008-05-02
> **siretfel said:**
> I understand the 10GB and 2GB, what's the 8GB for?
For root; that is where the system will be installed.

---

### Post by siretfel on 2008-05-02
many thanks for your help.
i will go with your suggestion
thanks a lot!!!

---

### Post by Gwador on 2008-05-02
Ok.
That was my layout for the laptop's 120 Gb HDD (before I've completely dumped WinXP last month):
sda1 - ntfs 45 Gb (Windows XP) # cause the beginning of the disk is the only place it would ever install to
sda2 - linux swap 2 Gb # Theoretically swap partion goes as close to the beginning of the disk as possible, considering perfomance. It was NEVER used in last 9 months though, so it could be even smaller with my 1 Gb RAM
sda3 - ext3 45 Gb mounted as "/" # that's where my ubuntu lives
sda4 - FAT32 30 Gb # that was a cross-platform backup storage, you probably won't need one

In my case, partitioning was done by Acronis Disk Director. Ubuntu installer does everything alright without any third-party tools, though.

Good luck.

---

