---
title: "[SOLVED] Swap partition not mounted automatically"
date: 2008-10-22
forum: New to Ubuntu
---

### Post by Liviu-Theodor on 2008-10-22
I did not had anything better to do, and I redimensioned the swap partition. Now it is still formatted as swap, but it is not automounted at system boot. Still, it can be used, if I open GParted and I say it to swapon (or I use the command swapon in a terminal). What can I do to automount it at startup?

---

### Post by Elfy on 2008-10-22
The UUID has changed I would expect, open aterminal and run

```
sudo blkid
sudo cp /etc/fstab /etc/fstab.2210
gksudo gedit /etc/fstab
```

Look for the swap line in your fstab it will look similar to

> UUID=cbd99e21-9789-4ea0-ba9a-09d365321c1d none            swap    sw 

chekc the UUID, if it has changed then replace it with the corresponding one form blkid

save file and close gedit

---

