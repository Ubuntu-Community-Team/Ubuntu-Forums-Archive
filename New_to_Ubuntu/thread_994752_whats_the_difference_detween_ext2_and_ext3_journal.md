---
title: "whats the difference detween ext2 and ext3 journaling?"
date: 2008-11-27
forum: New to Ubuntu
---

### Post by faraz_k86 on 2008-11-27
???

---

### Post by ggaaron on 2008-11-27
ext2 just doesn't have journalling. ext3 saves additional information about file system and is more likely to recover it and not loose any information for example after an unclean shutdown.

---

### Post by Xiong Chiamiov on 2008-11-27
Ext3 is journaled, while ext2 is not.  Other than that, they are the same, so you can mount an ext3 drive as ext2 if you wish.

---

### Post by vanadium on 2008-11-27
You can easily find this information on Wikipedia. Briefly, ext3 keeps a report (journal) on all transactions on the disk. If something goes wrong, that can immediately be seen on the next reboot, and the report can be used to restore the disk to its previous healthy condition.

With ext2, there is no such check and the only way to know that the disk is "healthy" is to run the long disk check each time at boot time. With ext3, we only need to do this thorough check every 30 days or so.

---

