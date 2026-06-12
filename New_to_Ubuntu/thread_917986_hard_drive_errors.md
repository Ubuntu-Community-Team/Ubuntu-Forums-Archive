---
title: "hard drive errors?"
date: 2008-09-12
forum: New to Ubuntu
---

### Post by theproc64 on 2008-09-12
for some reason, when I booted up once my hdd failed the disk check and I ended up in a root prompt.  this error hasn't been repeated since on any boot ups.  Also, when I try to access certain files, the computer seems to freeze up and the hard disk keeps clicking and a constant rate with the light blinking at the same time.  Is their any way to scan the hdd from linux and maybe fix the errors?

---

### Post by spydon on 2008-09-12
Try this from a live cd, your harddrive may be defect:
```
sudo badblocks hda
```
hda can also be sda or hdb or something like that, you can check it with:
```
sudo fdisk -l
```

---

### Post by perlluver on 2008-09-12
> **theproc64 said:**
> for some reason, when I booted up once my hdd failed the disk check and I ended up in a root prompt.  this error hasn't been repeated since on any boot ups.  Also, when I try to access certain files, the computer seems to freeze up and the hard disk keeps clicking and a constant rate with the light blinking at the same time.  Is their any way to scan the hdd from linux and maybe fix the errors?

Sounds like the hard drive is failing, not sure that it can be repaired, via a scan.  If it failed during a scan, then most likely it is slowly dying, I would recommend backing up your data.

---

### Post by theproc64 on 2008-09-13
I did some tests using the dell diagnostics and it kept returning errors so I called them up and they're sending me a new hard drive.

---

