---
title: "No space left on device?"
date: 2008-05-03
forum: New to Ubuntu
---

### Post by cardinals_fan on 2008-05-03
I attached a SanDisk MagicGate memory stick (through my printer), and began to copy files.  When the drive is only 23% full (according to df), I receive a "No space left on device" error in Thunar.  If I copy with cp, it also says: ```
cp: cannot create regular file `/media/disk/PC230045.JPG': No space left on device
``` Why is this happening?

---

### Post by dcast on 2008-05-03
Try clearing your trash bin. I find that helps when this happens, somehow the trash gets moved to the device on a hidden folder.

---

### Post by MockY on 2008-05-03
Something similar happened after I washed my memory stick. Does it work in another machine? Not saying yours is broken, but mine sure was. I would try doing what dcast suggested, show hidden folders on the device and empty the trash out.

---

### Post by cardinals_fan on 2008-05-03
Clearing the trash didn't work.

---

### Post by cardinals_fan on 2008-05-03
> **MockY said:**
> Something similar happened after I washed my memory stick. Does it work in another machine? Not saying yours is broken, but mine sure was.
I doubt it - the card is brand new.  I can't test on another machine because my printer has the only slot for MagicGate cards in my house, and it's too big to move.

---

### Post by cardinals_fan on 2008-05-03
I figured out most of the problem - I could only add a certain number of files to each directory on the drive.  Does anyone know how I might change this limit?

I've got it!  According to Wikipedia:> The number of root directory entries available is set at formatting time, and is stored in a 16-bit signed field setting an absolute limit of 32767 entries (32736, a multiple of 32, in practice). For historical reasons, FAT12 and FAT16 media generally use 512 root directory entries on non-floppy media, and other sizes may be incompatible with some software or devices (entries being file and/or folder names in the old 8.3 format).[9] Some third party tools like mkdosfs allow the user to set this parameter.[10]
Thus, my Fat-16 drive will only allow a little over 500 files in one directory.

---

