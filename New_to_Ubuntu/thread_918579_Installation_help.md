---
title: "Installation help"
date: 2008-09-13
forum: New to Ubuntu
---

### Post by esmailgad on 2008-09-13
Hi everyone. I'll install ubuntu for the first time on my computer. I have no experience with linux. My acer notebook has a hard disk with three paritions. One with windows (I want to keep), one with my data (sure I want to keep) and the third parition is free of data. I was told to delete the third parition and ubuntu will use it. is it true?? and what I must do if this is not the situation?

---

### Post by WRDN on 2008-09-13
If you have 1 partition left, boot from the LiveCD, delete this one in GParted (under System > Administration) and then you can create new primary partitions (max of 4) or an extended partition in this space.
Alternatively, during the installer, select "Use largest free continuous space" and it will use the unallocated space that appeared when you deleted the 3rd partition.
Out of interest, how old is the laptop? Most new(ish) computers also have a recovery partition now.

---

### Post by Elfy on 2008-09-13
Use largest free continuous space and it will create the necessary partitions in an extended partition for you.

This assumes that the partition you have deleted is unformatted - you should be able to point the installer at it if necessary.

---

### Post by crazypenguin2008 on 2008-09-13
smart thinking to ask. when i upgraded from gusty to hardy it added a second partition and kept gusty and installed hardy in a new partition. i didnt have the resources(IE too hardheaded to ask lol)  and i tried to delete the gusty partition and totaly muffed it up. i had to do a fresh install and lost everything.

---

### Post by esmailgad on 2008-09-13
my laptop is one year old. I make regular ghost image of my window and data partitions on an external hard disk, so I deleted the recovery partition

---

### Post by esmailgad on 2008-09-13
Hi again
I installed ubuntu as you told me. It went smoothly and I had no problem.
I'll discover it and I'll come back
Thank you for your help

---

