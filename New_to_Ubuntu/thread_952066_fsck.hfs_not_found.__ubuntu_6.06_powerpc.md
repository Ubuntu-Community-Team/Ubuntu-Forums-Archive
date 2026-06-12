---
title: "fsck.hfs not found.  ubuntu 6.06 powerpc"
date: 2008-10-18
forum: New to Ubuntu
---

### Post by lapubell on 2008-10-18
anyone know how i can get fsck to run on the ibook hdd on an old ibook G3?

I can't figure out why fsck.hfs is missing.  apt-get says that hfsplus and hfsutils are installed.

any help would be wonderful.  I don't work on macs much and my roommates is dying...

---

### Post by lapubell on 2008-10-18
anyone?  know about macs?

---

### Post by lifeinnovative on 2008-10-29
I've found this, and it might be a good place to start:

[http://packages.ubuntu.com/hardy/otherosfs/hfsprogs](http://packages.ubuntu.com/hardy/otherosfs/hfsprogs)

Ironically, I don't think it's available for powerpc...

---

### Post by lifeinnovative on 2008-10-29
Okay, got your solution:

[http://ubuntuforums.org/showthread.php?t=392287](http://ubuntuforums.org/showthread.php?t=392287)

Make sure you have "build-essential" installed:
```
sudo apt-get install build-essential
```

---

