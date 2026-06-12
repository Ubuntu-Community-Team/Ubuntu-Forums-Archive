---
title: "Ubuntu partitioning"
date: 2008-07-29
forum: New to Ubuntu
---

### Post by kkreck on 2008-07-29
i am using windows XP. this is loaded in C drive of hard disk. My hard disk already has c,d,e, and f partition. I made part e full blank for installing Ubuntu.. i do not know how to intall ubuntu in that drive only.  i want to use both XP and Ubuntu.

pls help

---

### Post by bodhi.zazen on 2008-07-30
> **kkreck said:**
> i am using windows XP. this is loaded in C drive of hard disk. My hard disk already has c,d,e, and f partition. I made part e full blank for installing Ubuntu.. i do not know how to intall ubuntu in that drive only.  i want to use both XP and Ubuntu.

pls help

A typical installation uses 2 partitions, one for the filesystem / or root and one for swap.

Linux partitions are different then windows. Best understand linux terminology:

[HowTo: Partitioning Basics - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=282018") 

Then fire up the Ubuntu CD

Start gparted, delete your "e" partition and make a new extended partition. Make 2 logical partitions , one for swap (size = RAM X 2 , max 1 Gb, size = RAM if you would like to use hibernation) and one (ext3) for ubuntu / (root)

Apply changes, close gparted, start the installer, assign the new partition to root.

---

