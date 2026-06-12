---
title: "Partition"
date: 2008-04-23
forum: New to Ubuntu
---

### Post by grannyw on 2008-04-23
Hi everybody!
i have just got hardy 8.04 and i want to install at my notebook.
I have two harddrives 120G,how should i make my partitions.i mean:":Logical/extended" and all this stuff.

thanx in advance

---

### Post by markjensen on 2008-04-23
My advice is to **not** "make" the partitions, unless you know what you need for your partitioning scheme.

Just shrink an existing partition (or use an extra drive, since you mentioned you have two drives) and let Ubuntu set up your partitions for you.

---

### Post by grannyw on 2008-04-23
**markjensen**
it sounds good but,what should i do to use all my harddrives,even though i dont really need it right now?

---

### Post by wannadumpwindows on 2008-04-23
Use the second hard drive for your home partition. That way you'll always have your data no matter what happens, and you can even move it between computers if you ever have the need. And you can use the first drive for the O/S itself.

---

### Post by markjensen on 2008-04-23
Do you not want any other OS to remain on that computer?   Ubuntu can "take over" the entire drive and install.

If there is another OS on there (XP or Vista, most likely) that you want to keep, then we need to make sure we don't tell Ubuntu to be greedy and use the entire drive...

---

### Post by SnakeHips on 2008-04-23
I'd suggest the following if you are comfortable around setting up partitions

disk1

/            - ext3 -   say 10gig
/swap        -      -   twice your ram
/home        - ext3 -   whatever is left on drive

disk2

format in FAT32 and use as a Backup drive

---

### Post by markjensen on 2008-04-23
I am not certain if the notebook really has two separate 120GB hard drives in it.  Or a large drive divided into two Windows "drives" that are really partitions.

---

### Post by SnakeHips on 2008-04-25
Post the output from terminal...

```
sudo fdisk -l
```

---

