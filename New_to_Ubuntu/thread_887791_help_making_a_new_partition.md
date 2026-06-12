---
title: "help making a new partition??"
date: 2008-08-12
forum: New to Ubuntu
---

### Post by betterthanjordan79 on 2008-08-12
im trying to make a new partition in ubuntu but im not sure how to-i installed the partition editor but it let me select a new one. could someone please give me step by step instructions on how to make one!thanks in advance.

---

### Post by rbc on 2008-08-12
Need some additional information. Is Ubuntu the only OS on this hard drive? If so, is Ubuntu and the swap partition using the whole hard drive, and you trying to make the partition while that OS is active or are you running a Live CD?

---

### Post by betterthanjordan79 on 2008-08-12
yes ubuntu is the only os on it and there is 2 partitions-like u said the ubuntu 1 and the swap partition. i am not using a live cd to do it but i could if i have to. what would i hav to to in the ubuntu live cd??

---

### Post by bodhi.zazen on 2008-08-12
You have to manage your partitions from a live CD.

You can not work with a mounted partition, so that means booting a live cd to mange your root partition.

You will likely need to unmount your swap partition (this can be done manually or form gparted).

---

### Post by sandysandy on 2008-08-12
> **betterthanjordan79 said:**
> im trying to make a new partition in ubuntu but im not sure how to-i installed the partition editor but it let me select a new one. could someone please give me step by step instructions on how to make one!thanks in advance.

use gparted

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

here is a link to gparted tutorial

[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

regards

---

