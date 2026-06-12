---
title: "help with partitions"
date: 2008-06-18
forum: New to Ubuntu
---

### Post by winsall on 2008-06-18
hey all,

i have 57.98gb of unallocated HDD space that i wish to just merge into the filesystem. but gparted wont let me!!! i followed a walkthrough a while back that put it onto /mnt/disk, however it told me i didnt have the permission to read/write. please help!!! :):):)

---

### Post by aquavitae on 2008-06-18
Can you give more information?  What were the instructions you were following, and where do you get stuck?

---

### Post by hyper_ch on 2008-06-18
What partition do you want to add to which one?

---

### Post by winsall on 2008-06-18
just assume that i have two things: a partition (the one ubuntu is running) and a giant free space on my HDD.

i want them to become one. any idea?

---

### Post by rxtx on 2008-06-18
Have you tried running gparted from the Ubuntu live CD then resizing your existing partition to use the free space?

Also, you could also always mount your free space as /home or /usr :)

---

### Post by indytim on 2008-06-18
If you are trying to use GParted on your active partition... can't do it.  Either boot to the Ubuntu LiveCD or, better yet, download, burn and use the GParted Live CD (great thing to have in your "toolkit").

IndyTim

---

### Post by aquavitae on 2008-06-18
You should be able to just resize your ubuntu partition in gparted.  If you can't, then what errors do you get?

---

### Post by rxtx on 2008-06-18
> **indytim said:**
> If you are trying to use GParted on your active partition... can't do it.  Either boot to the Ubuntu LiveCD or, better yet, download, burn and use the GParted Live CD (great thing to have in your "toolkit").

IndyTim

Yes, forgot about that! The gparted live CD is very useful indeed 8-)

---

### Post by winsall on 2008-06-18
sweet will give it a go, thanks all

---

