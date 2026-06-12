---
title: "gparted"
date: 2012-03-08
forum: New to Ubuntu
---

### Post by maheshtatva on 2012-03-08
gparted live cd works fine but cannot access the extended partition button only primary partition is available

one thing i found that got one extended partition (linux swap)as it was partitioned during installing the ubuntu 11.10

there any thing to fix problem

---

### Post by plucky on 2012-03-08
> **maheshtatva said:**
> gparted live cd works fine but cannot access the extended partition button only primary partition is available

one thing i found that got one extended partition (linux swap)as it was partitioned during installing the ubuntu 11.10

there any thing to fix problem

Post a screenshot.

I think you are allowed only  one extended partition,just increase the size of the one you have and then put your logical partitions inside the extended partition.

You may need to turn swap off to increase the size of the extended partition,even on the Live CD.

Good Luck

---

### Post by maheshtatva on 2012-03-08
after swapoff there will be any problems in RAM.

---

### Post by plucky on 2012-03-08
> **maheshtatva said:**
> after swapoff there will be any problems in RAM.

There shouldn't be, as the swap is only used if you run out of memory.You will probably need to use gparted on the Live CD to alter partitions.

Please post a screenshot of your gparted picture.

Good Luck

---

