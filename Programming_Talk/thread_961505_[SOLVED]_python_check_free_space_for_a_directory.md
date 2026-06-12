---
title: "[SOLVED] python check free space for a directory"
date: 2008-10-28
forum: Programming Talk
---

### Post by giuspen on 2008-10-28
hi i'm searching for a way to check the free disk space in a path in order to compare it to the dimension of an object that i want to write there.
i need to insert this into a python script.
thanks in advance to anybody suggest something.

---

### Post by ghostdog74 on 2008-10-28
you can parse the output of df

---

### Post by wmcbrine on 2008-10-28
How about os.statvfs()?

---

### Post by ghostdog74 on 2008-10-28
yes, definitely
```

import sys,os,statvfs

f = os.statvfs("/home")
print "preferred block size", "=>", f[statvfs.F_BSIZE]
print "fundamental block size", "=>", f[statvfs.F_FRSIZE]
print "total blocks", "=>", f[statvfs.F_BLOCKS]
print "total free blocks", "=>", f[statvfs.F_BFREE]
print "available blocks", "=>", f[statvfs.F_BAVAIL]
print "total file nodes", "=>", f[statvfs.F_FILES]
print "total free nodes", "=>", f[statvfs.F_FFREE]
print "available nodes", "=>", f[statvfs.F_FAVAIL]
print "max file name length", "=>", f[statvfs.F_NAMEMAX]

```

---

### Post by giuspen on 2008-10-29
yes, os.statvfs is exactely what I needed, thanks a lot.

for ghostdog74: I see that you import also "sys" (and not only "os" and "ststvfs"), is there a reason for it? I'm quite new to python and I saw in many examples people to do "import sys" even if not apparently used.

---

### Post by ghostdog74 on 2008-10-29
no, if you don't need sys, then don't import it.
I have copied and paste without removing it.

---

