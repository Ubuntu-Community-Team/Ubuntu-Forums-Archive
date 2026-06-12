---
title: "increasing a partition with gparted"
date: 2008-09-22
forum: New to Ubuntu
---

### Post by conedash on 2008-09-22
i am trying to increase the size of my hda1 partition with gparted. unfortunately it only lets me decrease the partition size and i find no way to add the 25gb of free space to this partition. any hints on what i have to do to increase a partition?

---

### Post by Najmudin on 2008-09-22
If i remember you should move the swap partition to the end of the empty space in order to extend the hda1 partition.

---

### Post by adamogardner on 2008-09-22
yes if I remember correctly also, you can only work expand to the left, and since you are at the left you can't pull your partition out.  I never did this I just remember reading it.

---

### Post by timcredible on 2008-09-22
the free space has to be contiguous with the partition you want to add that space to.  which means you have to delete the swap partition, apply that change, then delete the extended partition, apply that, then expand your hda1 partition, but leave room at the end, because you have to put the swap partition back at the end.

---

