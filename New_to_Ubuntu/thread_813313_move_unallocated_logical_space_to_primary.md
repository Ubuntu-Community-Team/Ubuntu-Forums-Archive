---
title: "move unallocated logical space to primary"
date: 2008-05-30
forum: New to Ubuntu
---

### Post by akkad on 2008-05-30
is it possible to resize the primary partition to use unallocated space in extended partition ???  am using gparted from the live cd.

---

### Post by housam on 2008-05-30
Yes , shrink the extended partition first to leave the unallocated space out of it . then resize the primary partition to have that space.

---

### Post by akkad on 2008-05-30
i already deleted one logical partition so there is unallocated space, but i dont have the option to resize extended and primary partitions !!!!

---

### Post by akkad on 2008-05-30
ok i found it here : [http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)
first remove the swap then it will let u resize the extended partition.

---

### Post by housam on 2008-05-30
use the Gparted live CD or ubuntu live cd but after unmounting the partition you want to resize.

---

