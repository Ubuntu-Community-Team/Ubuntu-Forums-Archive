---
title: "[SOLVED] Disks won't unmount"
date: 2008-08-30
forum: New to Ubuntu
---

### Post by intense.ego on 2008-08-30
I am currently using Gparted through a live CD to do a complete overhaul of my partitions, but the hard drive won't unmount. If I right-click and select unmount, it acts as if it is unmounting, but then opens up the directory (thus the partition must still be mounted). Is there a way to force the drives to unmount? A command perhaps?

---

### Post by intense.ego on 2008-08-30
Actually, nevermind, I found out the command. In case someone else needs to know, it is:

```
 sudo umount /path/to/partition 
```

---

