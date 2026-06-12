---
title: "[SOLVED] partition help"
date: 2008-09-04
forum: New to Ubuntu
---

### Post by PatrickMoore on 2008-09-04
so i had 2 partitions on my hard drive one with ubuntu and one with xubuntu. i erased the xubuntu partition which was in front of my ubuntu partition. i want to expand my ubuntu partition but gparted will not let me extend the size. i am running a live disk with my hard drive unmounted. any help would be appreciated

---

### Post by Elfy on 2008-09-04
Need to see whether extended partitions are involved to give a clear answer - can you run this and post result

```
sudo fdisk -l
```

Also is swap mounted - the livecd will use it.

---

### Post by kansasnoob on 2008-09-04
If the partition is "inside" an extended partition the extended partition must be expanded first.

Also if the swap partition is still in "swapon" mode there'll be a "keyring" to the left side of it .......... just select "swapoff".

Watch for the "keyring" somewhat to the left in the partition list.

Something I should note is the possibility that you may lose the ability to keep swap in "swapon" mode and/or losing the quiet Usplash boot when you're all done.

If that happens it's easy to fix, it'll be a uuid problem, just start a new thread titled something like "uuid problem after partition resizing".

---

### Post by PatrickMoore on 2008-09-04
> **kansasnoob said:**
> If the partition is "inside" an extended partition the extended partition must be expanded first.

Also if the swap partition is still in "swapon" mode there'll be a "keyring" to the left side of it .......... just select "swapoff".

Watch for the "keyring" somewhat to the left in the partition list.

Something I should note is the possibility that you may lose the ability to keep swap in "swapon" mode and/or losing the quiet Usplash boot when you're all done.

If that happens it's easy to fix, it'll be a uuid problem, just start a new thread titled something like "uuid problem after partition resizing".

it was showing up as two hard drives so i had to delet one of the tables. i fixed it now it just took some time to expand so i just got back on thanks anyways

---

