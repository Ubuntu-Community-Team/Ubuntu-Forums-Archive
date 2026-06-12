---
title: "Help installing ubuntu on LV"
date: 2011-11-04
forum: New to Ubuntu
---

### Post by cap10Ibraim on 2011-11-04
can I install ubuntu on "Unused Space" in a Logical Volume ?

---

### Post by Mark Phelps on 2011-11-04
You can't install INSIDE an existing partition.  If the unused space is, as you state INSIDE an existing logical volume, you would first have to shrink the logical volume to free up some space outside of it.

If the unused space is outside a logical volume but inside an Extended partition, you can create another partition inside that space.  The installer will let you do that.

---

### Post by cap10Ibraim on 2011-11-04
are you familiar with system-config-lvm ? 
I'm using it resize a partition , now I have 10 GB Unused how to make those unpartitioned outside of the lv ?

---

