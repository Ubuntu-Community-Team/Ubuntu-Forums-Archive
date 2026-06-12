---
title: "cant delete files from flash drive"
date: 2012-01-07
forum: New to Ubuntu
---

### Post by 007casper on 2012-01-07
> 
user@puter: cd /media/flashdrive

user@puter: /media/flashdrive$ ls
red-documents 

user@puter: /media/flashdrive$ rm -r red-documents

rm: cannot remove `red-documents': Read-only file system

how can I delete the files?

---

### Post by kimda on 2012-01-07
You have to mount the filesystem as writable. Its mounted as read only.

ex. sudo mount -o remount,rw /dev/sdb1 /media/flashdrive

---

### Post by MARP1961 on 2012-01-07
One of the quickest ways to completely clear your USB of files is to let 'Startup Disk Creator' delete all files from your USB Flashdrive. Just make sure you really do want to empty it!

---

### Post by 007casper on 2012-01-07
that worked - thanks

---

