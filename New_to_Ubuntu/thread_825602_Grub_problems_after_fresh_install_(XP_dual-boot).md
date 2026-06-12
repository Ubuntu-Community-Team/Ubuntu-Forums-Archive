---
title: "Grub problems after fresh install (XP dual-boot)"
date: 2008-06-11
forum: New to Ubuntu
---

### Post by raghothams on 2008-06-11
hi
I had dual booting -winXP n ubuntu 7.
When  installing Ubunut 8 a had to create a new partition and install.
after installing hardy, i deleted the old partition which had ubuntu7.
now GRUB error 17 is occuring. i cant use my system. :(

How to re-install ubuntu 8 on the existing partition of ubuntu 8?
Pl help me. repky fassssssst!!!!!!!

---

### Post by ugm6hr on 2008-06-11
Boot from the Hardy LiveCD.

Use GParted (Partition Editor) and format the Ubuntu partition (ext3).

Click on the Install icon.

Select manual partitioning.

"Mount" the Ubuntu partition as "/" and select the format button.

Mount the swap partition as swap.

Follow the rest of the prompts.

Consider creating a separate /home partition at this stage too.

---

