---
title: "What is gvfs-fuse-daemon?"
date: 2008-07-31
forum: New to Ubuntu
---

### Post by words1 on 2008-07-31
In "System Monitor," File Systems tab, I have a listing for my primary HD, then below it a listing for gvfs-fuse-daemon with exactly the same stats, mounted at home/[me]/gvfs.

fdisk for this disk produces:

```
Disk /dev/sdb: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6fbe2ab7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9324    74894998+  83  Linux
/dev/sdb2            9325        9726     3229065    5  Extended
/dev/sdb5            9325        9726     3229033+  82  Linux swap / Solaris



```

I don't remember seeing "gvfs=fuse-daemon" in previous versions.  What is it, and why is it there?

---

### Post by philinux on 2008-07-31
[http://en.wikipedia.org/wiki/GVFS](http://en.wikipedia.org/wiki/GVFS)

---

### Post by dietkinnie on 2008-07-31
This is new to me also , you might want to check this out 

[http://en.wikipedia.org/wiki/GVFS]("http://en.wikipedia.org/wiki/GVFS")

---

### Post by billgoldberg on 2008-07-31
Aren't those things used for nautilus to be able to handle ssh?

On fluxbox gvfs wasn't used and nautilus couldn't use ssh.

Fuse is used to mount virtual filesystems. I used it in the past to [mount an upnp share]("http://linuxowns.wordpress.com/2008/06/05/accessing-upnp-server-from-ubuntu/") in ubuntu.

---

### Post by words1 on 2008-07-31
Thanks, but that's a bit over my head.  As long as it belongs there and isn't eating up space, that's all I care about.

---

### Post by words1 on 2008-07-31
Huh -- well, I do use SSH quite a bit.

---

