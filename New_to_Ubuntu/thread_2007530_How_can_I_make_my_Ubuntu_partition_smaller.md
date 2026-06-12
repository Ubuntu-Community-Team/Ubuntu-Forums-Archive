---
title: "How can I make my Ubuntu partition smaller?"
date: 2012-06-20
forum: New to Ubuntu
---

### Post by greenelf on 2012-06-20
I accidentally installed Ubuntu with a very large partition size. How can I shrink it to something like 50GB, and add that space back to Windows?

---

### Post by click4851 on 2012-06-20
I've always had good luck with a LiveCD of Gparted.

---

### Post by Mark Phelps on 2012-06-21
First of all, you can't make changes to partitions while they are in use, so to make any changes to the Linux filesystem partitions, you have to boot from a CD or USB.

If you boot from an Ubuntu CD (or USB), you then run the GParted app (Gnome Partition Editor) to shrink down the size of the Ubuntu partition.

However, if you are also running Win7, it does not work well with GParted, so you should then boot into Win7 and use its Disk Management utility to increase the size of the Win7 OS partition.

---

