---
title: "[SOLVED] CD ROM Mount / Copy Problem"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by jethin on 2008-04-30
Hi Y'all, total newb making my first post here.

I'm having problems with my CD-Rom drives. When I put a cd into one, they seem to mount OK (I get an icon on the desktop and can open/read files) but I get the following error:

**Failed to mount "MY CD NAME".**

mount: block device /dev/scd1 is write-protected, mounting read-only
mount: /dev/scd1 already mounted or /media/cdrom1 busy
mount: according to mtab, /dev/scd1 is already mounted on /media/cdrom1.

I also get "permission denied" errors when I try to copy some of the files from the cd drives. I'm also getting a similar error with an external hard drive.

Looking forward to becoming a Ubuntu evangelist and maybe even lending a hand to a poor confused soul such as myself someday. Thanks.

---

### Post by scragar on 2008-04-30
try forcing it to be unmounted:
```
sudo umount /media/cdrom1
```
then try to open it from the places menu, if that doesn't work you may need to edit mtab and remove the reference, see if it mounts then```
gksudo /etc/mtab
```and remove the line with it in, but be warned, if you corrupt mtab you can cause some very strange effects, although the actual damage it can cause is minimal(since a restart would undo any edits :P).

---

### Post by jethin on 2008-04-30
I tried your first suggestion Scragar, but it didn't seem to help as far as the recurring error message is concerned. Before I go messing with mtab, can someone confirm that this would indeed be the way to go about fixing a cd drive that *does* mount (I can at least read the disc) but that throws afailure alert (see above) whenever a disc is inserted into it and inexplicably locks some of the files on the disc? Thanks, Jeremy

---

### Post by jethin on 2008-07-16
I'm pretty sure that my permissions problem was somehow related to the way Totem was accessing my cd drive. I uninstalled Totem and installed Grip, which seems to read my cd drives properly.

---

