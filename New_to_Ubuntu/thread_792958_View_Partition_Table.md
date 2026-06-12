---
title: "View Partition Table"
date: 2008-05-13
forum: New to Ubuntu
---

### Post by silverjohnlong on 2008-05-13
Is there a way to view the partition table? I am running Ubuntu 8.04

---

### Post by cwgatling on 2008-05-13
Have you tried ```
sudo fdisk -l
```

---

### Post by Monicker on 2008-05-13
> **silverjohnlong said:**
> Is there a way to view the partition table? I am running Ubuntu 8.04

From a terminal:

```
sudo fdisk -l
```

---

### Post by silverjohnlong on 2008-05-13
Thanks guys!

---

### Post by jamyskis on 2008-05-13
If you're looking for a sweet looking GUI, give GParted a try. You can install it via Synaptic (and I think Add/Remove Applications as well) and it's got a menu entry under System/Administration

---

### Post by silverjohnlong on 2008-05-13
I have got the GParted "live" CD but unfortunately not a clue how to use it!

---

### Post by django0909 on 2008-05-13
I just did 

```
sudo apt-get install gparted
```

and ran it from there :)

---

