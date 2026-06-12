---
title: "swap partition primary or extended?"
date: 2008-08-25
forum: New to Ubuntu
---

### Post by sheroxe on 2008-08-25
Ok so im editing partitions with gparted to install ubuntu for the first time. I rezised my ntfs partition, made it smaller.

Then i made a new ext3 partition as primary (is this right?) to install ubuntu, and left another 2gb for swap, im about to create the swap, should i make it primary or extended?

thanks in advance

---

### Post by Gone fishing on 2008-08-25
Mines on a primary partition. Although I don't think it matters.

You will have to edit fstab: sudo gedit /etc/fstab 

also have a look at this thread:

[http://ubuntuforums.org/showthread.php?t=810948&page=5](http://ubuntuforums.org/showthread.php?t=810948&page=5)

---

### Post by bumanie on 2008-08-25
With linux, it doesn't matter whether a partition is primary or extended. Personally I make them all primary, but that depends on how many partitions one has, as a hard drive can only have four primary partitions. If you need an extended partition, swap is probably as good a choice as any other partition. It is not a good idea to make / or /home in extended partitions unless room is left with in the extended partition to expand them. Have come across a number of posts were people are trying to expand a / or /home and can't because they are already at their maximum size with in an extended partition. An extended partition can't be removed without also removing that which is inside it.

---

