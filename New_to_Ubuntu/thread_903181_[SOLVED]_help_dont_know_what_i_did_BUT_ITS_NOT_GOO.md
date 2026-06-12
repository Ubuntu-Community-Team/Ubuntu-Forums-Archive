---
title: "[SOLVED] help dont know what i did BUT ITS NOT GOOD"
date: 2008-08-28
forum: New to Ubuntu
---

### Post by brandon333 on 2008-08-28
just installed ubuntu on new machine (imac) with refit had some issue but got it working and di updates downloaded some goodies, themes etc and then had to reboot, now this error:


/dev/sda3:  inodes that were part of a corrupted orphan link list found
/dev/sda3: unexpected inconsistency ; run fsck manually
                      (ie without -a or -p options)
fsck died with exit status 4
an automatic file check of root filesystem failed





HELP!!

---

### Post by brandon333 on 2008-08-28
fixed. disregard.

---

### Post by kpkeerthi on 2008-08-28
Boot with **Ubuntu Live CD**. Yes you should be in Live mode only so the disks are NOT MOUNTED. When you are at the desktop, open a terminal and run this command:
```

sudo fsck /dev/sda3

```
and follow prompts.

---

### Post by LTFC2020 on 2008-08-28
fixed?
please mark the thread as solved using the thread tools drop down menu

---

