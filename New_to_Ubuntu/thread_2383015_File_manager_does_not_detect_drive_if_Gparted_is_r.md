---
title: "File manager does not detect drive if Gparted is running"
date: 2018-01-19
forum: New to Ubuntu
---

### Post by wrongusername2 on 2018-01-19
I have 2nd internal disk. File manager will not detect the drive as long as GParted is running,  Once i close gparted, drive will show up in filemanager. Not a very important issue but would like to know why this behavior.
Ubuntu 16.04

Thanks

---

### Post by DuckHook on 2018-01-20
…because *gparted* is strong medicine. In order to do its partitioning work, it must unmount the drive. You can't read an unmounted drive. When you exit *gparted*, it has the grace to remount the drive before bowing out.

---

### Post by wrongusername2 on 2018-01-20
Thanks that makes sense :-)

---

