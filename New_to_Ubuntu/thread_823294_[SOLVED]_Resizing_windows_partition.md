---
title: "[SOLVED] Resizing windows partition"
date: 2008-06-09
forum: New to Ubuntu
---

### Post by tysonh on 2008-06-09
I have a option to set my resized windows partition not do be used.  Should I do this?

Also, It has a option for bootable flag on or off?  If I choose off will I not be able to boot into windows? 

Should I make both my windows partition and my / partition bootable flag on?

---

### Post by Rocket2DMn on 2008-06-10
Using your windows partition is up to you - the ntfs-3g driver allows linux machines to safely read/write ntfs partitions, so it is safe to do so.

You should keep the bootable flag on for your Windows partition.  You do not need your linux root partition to have the boot flag (and perhaps you shouldn't even try).

---

### Post by wolfen69 on 2008-06-10
if windows is the first partition, you will want to make it bootable.

---

### Post by tysonh on 2008-06-10
Thanks for the input.  I got it all figured out last night and left the boot flag on xp just in case.  Everything worked just fine.

---

### Post by wolfen69 on 2008-06-10
glad everything worked out.

---

