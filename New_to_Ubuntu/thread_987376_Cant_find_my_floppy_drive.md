---
title: "Cant find my floppy drive"
date: 2008-11-19
forum: New to Ubuntu
---

### Post by Swerve1000 on 2008-11-19
Hi,

I have Ubuntu 8.10 installed on one machine, and Xubuntu 8.10 on another, both Desktop versions.. 

I'm tying to access my floppy drive on both machines, but they don't seem to be there, where the CD-ROM's are for example.

The disk is in the drive, the writeable tab on the floppies is set to write, but it's as if the OSs don't see the floppy drive.

I've never tried to use the floppy drive before with Linux, so I'm probably making a newbie error, or not looking for he right icon, but I can't find it, that is for sure!

I tried:

mount /media/floppy0

But it says can find it OR something, unable to remember exactly.

Can anyone help?

Many thanks!!!

---

### Post by MasterSander on 2008-11-19
you have to find it in /dev, then you have to make a directory like /media/floppy and then type mount /dev/deviceyoufoundasfloppy /media/floppy

---

### Post by rbc on 2008-11-19
[http://ubuntuforums.org/showthread.php?p=6185315&highlight=floppy#post6185315](http://ubuntuforums.org/showthread.php?p=6185315&highlight=floppy#post6185315)

See glennric's solution (third from the bottom)

---

