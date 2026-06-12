---
title: "Inalid mount option"
date: 2008-09-05
forum: New to Ubuntu
---

### Post by thelasersailor on 2008-09-05
Whenever I insert and USB storage device it comes up with the error 'invalid mount option when attempting to mount the volume'. Please keep responses simple as I'm new to linux.

---

### Post by thelasersailor on 2008-09-05
Managed to sort it out myself by editing fstab.

---

### Post by Rocket2DMn on 2008-09-05
Not sure what you did in your fstab, but typically you don't want any entry enabled in fstab for a device that gets automounted.  This often happens when people have removable drives plugged in during the install process, then disconnect them and attempt to plug in different ones.  Your best bet is to disable the fstab entry by placing a # in front of it, then any device that gets plugged in and gets placed at the /dev location (ex: /dev/sdb1) will be automounted with the appropriate options, regardless of filesystem.  So if you simply edited fstab to change the filesystem (say from ntfs-3g to vfat), you will still run into problems later.

---

