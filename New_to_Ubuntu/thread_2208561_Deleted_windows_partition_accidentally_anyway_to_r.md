---
title: "Deleted windows partition accidentally? anyway to recover?"
date: 2014-03-01
forum: New to Ubuntu
---

### Post by oomalikoo on 2014-03-01
got a new notebook and installed ubuntu. Since I cant use netflix I wanted to go back to windows but apparently I deleted it :s

Anyways to get it back?

---

### Post by lisati on 2014-03-01
Did you make a recovery disk?

---

### Post by oomalikoo on 2014-03-01
> **lisati said:**
> Did you make a recovery disk?


no i did not sir :(

---

### Post by david98 on 2014-03-01
When you installed ubuntu did you use the full hdd or did you install alongside windows ?

---

### Post by Mark Phelps on 2014-03-01
If you completely overwrote Windows, while it may be possible to get the filesystem back, some of it will have been destroyed due to the overwrite; so I seriously doubt you can get it back in working order.

If you're not sure if Windows is still there, open a terminal and enter "sudo fdisk -lu" (lowercase L, not a one).  That will list out the partitions on the drive.

IF you can't restore it, an alternative is to contact the notebook supplier and see if they will sell you "full restore media". That will be a LOT cheaper than going out and buying a full retail copy of MS Windows.

---

