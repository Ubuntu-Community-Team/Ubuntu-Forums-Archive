---
title: "NTFSFIX will not work.  What should I do?"
date: 2008-08-19
forum: New to Ubuntu
---

### Post by curiousnoob on 2008-08-19
Whenever I try to run the ntfsfix command I get the following message: 
sudo ntfsfix /dev/sda2/disk
sudo: ntfsfix: command not found

I read I might need the build-essential pack so I installed it with this command:
sudo apt-get install build-essential 

but it still gives the same error.  How can I make this work?

---

### Post by halitech on 2008-08-19
are you sure that /dev/sda2/disk is the right path?

open a terminal and do ```
fdisk -l
``` just to confirm it is correct

---

### Post by curiousnoob on 2008-08-19
> **halitech said:**
> are you sure that /dev/sda2/disk is the right path?

open a terminal and do ```
fdisk -l
``` just to confirm it is correct

 Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           4       32098+  de  Dell Utility
/dev/sda2   *           5        1383    11076817+   7  HPFS/NTFS
/dev/sda3            1384        3645    18169515   83  Linux
/dev/sda4            3646        3738      747022+   5  Extended
/dev/sda5            3646        3738      746991   82  Linux swap / Solaris

---

### Post by halitech on 2008-08-19
the drive would actually be /dev/sda2

did you install ntfsprogs?

```
sudo apt-get install ntfsprogs
```

---

### Post by curiousnoob on 2008-08-19
I think that did it but now I have a new error message: 
sudo ntfsfix /dev/sda2/disk
Failed to determine whether /dev/sda2/disk is mounted: Not a directory.
Mounting volume... Error opening partition device: Not a directory.
Failed to startup volume: Not a directory.
FAILED
Attempting to correct errors... Error opening partition device: Not a directory.
FAILED
Failed to startup volume: Not a directory.
Volume is corrupt. You should run chkdsk.

Any ideas?

---

### Post by halitech on 2008-08-19
try running```
ntfsfix /dev/sda2
```

---

### Post by curiousnoob on 2008-08-19
> **halitech said:**
> try running```
ntfsfix /dev/sda2
```

I get this:
sudo ntfsfix /dev/sda2
Refusing to operate on read-write mounted device /dev/sda2.

---

### Post by halitech on 2008-08-19
getting closer :)

do you have an icon for the drive on your desktop? Ubuntu seems to think it is mounted so will need to unmount it first. If you have an icon for it, right click - unmount. if not, open a terminal and type```
sudo unmount /dev/sda2
```

---

### Post by curiousnoob on 2008-08-19
> **halitech said:**
> getting closer :)

do you have an icon for the drive on your desktop? Ubuntu seems to think it is mounted so will need to unmount it first. If you have an icon for it, right click - unmount. if not, open a terminal and type```
sudo unmount /dev/sda2
```

I think that might have done it.  I'm going to attempt to boot up Windows now.

---

### Post by halitech on 2008-08-19
ok, will cross my fingers for you :)

---

