---
title: "partition Help"
date: 2008-07-12
forum: New to Ubuntu
---

### Post by trikster_x on 2008-07-12
I took a 34 GB chunk off my windows partition to add to my 15 GB ubuntu partition.  Everything worked great until gparted tried to move and resize my ubuntu partition.  It ran into an error when it was finishing moving the filesystem, but there were no details.  Now gparted says that my Ubuntu partition is 49 GB, which is what I wanted, but now it says that 46 GB is being used, and I only had about 10 GB used before extending the partition.  I need to know if there is any way to fix this problem without having to reinstall Ubuntu.  If I have to, I can back up all the files I need and do a completely fresh install, but I really don't want to.

---

### Post by drs305 on 2008-07-12
If you are in ubuntu at the moment, run this to see what the system thinks you have regarding disk space:
```
df -Th	

```

---

### Post by trikster_x on 2008-07-13
Here's what I get:

[ATTACH]77625[/ATTACH]

It looks like there is still only 11 GB being used, but I don't know where my 34 GB went.  The unused memory matches what gparted tells me I have.  Here is a screenshot of gparted:

[ATTACH]77629[/ATTACH]

---

### Post by trikster_x on 2008-07-15
bump

---

### Post by trikster_x on 2008-07-18
bump.

---

### Post by jamewill on 2008-07-18
can you run
gparted and help/about to see which version you are using

---

### Post by trikster_x on 2008-07-18
0.3.5

---

