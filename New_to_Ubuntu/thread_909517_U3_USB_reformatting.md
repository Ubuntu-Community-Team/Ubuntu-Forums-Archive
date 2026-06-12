---
title: "U3 USB reformatting"
date: 2008-09-03
forum: New to Ubuntu
---

### Post by flyingsolo on 2008-09-03
I just purchased one of these but didn't pay attention to the fact it was a U3 drive.  I just want to use it as a regular USB stick with Ubuntu, OSX and sometimes Windows too.  How do I erase the volumes created on it by Sandisk and reformat it for general use?
Thanks.

---

### Post by bhadotia on 2008-09-03
Whats U3? Never heard of it. 

For formatting tasks you can use Gparted or the good old command line tools such as mkfs (type 'man mkfs' in terminal for more info on this).

---

### Post by mike555 on 2008-09-03
You can download the U3 uninstaller from the Sandisk (or whatever make) website and use it (on a windows machine)to completely remove it ......

---

### Post by flyingsolo on 2008-09-03
Thanks--the Sandisk removal tool did the trick and left the USB with FAT32 formatting in place.  Incidentally, gparted could see the disk but not format it; the device seemed to be 'locked'.

---

