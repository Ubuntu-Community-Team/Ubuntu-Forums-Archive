---
title: "Wrecked NTFS partition"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by ~chinook~ on 2008-04-27
During my resize of the NTFS partition it got wrecked. Now I can't seem to mount. Is there any way to force mount the drive. I just want to be able to get some emails and documents off of the disk. Any help will be appreciated.

---

### Post by hums07 on 2008-04-27
After being resized, an NTFS partition may become "dirty". In this situation, I would run Windows then do chkdsk and restart to Ubuntu again. Hope then it would mount ntfs partition automatically.

To force mount:
```
sudo mount -t ntfs-3g -o force /dev/sda1 /media/sda1
```

---

### Post by Drate on 2008-04-27
How were you resizing it?  GParted?  Fdisk and NTFSRESIZE?  It would help to know at what point the resize fouled up.  Also, always remember that running chkdsk and most definitely defrag are great ideas before resizing windows partitions.

---

