---
title: "swap file: to shrink or delete with gparted"
date: 2008-08-26
forum: New to Ubuntu
---

### Post by aspergerian on 2008-08-26
I have an asus 901 with 8.04.1, w/o XP. While loading 8.04.1 I made too large a swap file and would like to shrink it. Gparted offers the option of deleting the swap file, which uses virtually all of a 9.44gig partition on sdb. Would deleting the swap file be a safe next step?

---

### Post by kpatz on 2008-08-26
Yes, delete the swap, and then recreate it with a smaller size.  Then you can create another partition in the space you freed up.

To prevent issues with the swap being in use while it's being resized, boot from a Live CD and then run gparted from that, rather than running it while booted from the hard drive.

---

### Post by bodhi.zazen on 2008-08-26
Shrink (resize) you swap file.

If you delete it and then make a new, smaller one you will then need to update fstab.

List your partitions with

```
sudo blkid
```

that will show your UUID

Then :

```
gksu gedit /etc/fstab
``` and update your swap UUID.

FYI: swap should be RAM X 2 , Max 1 Gb, unless you use hibernation, in which case swap = ram.

---

