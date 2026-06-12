---
title: "Workaround for Floppy Oddities?"
date: 2008-09-10
forum: New to Ubuntu
---

### Post by Kellemora on 2008-09-10
Hi Gang

Should there be a FILE in /dev/fd0 for the different floppy disk sizes?

The reason I'm asking is:
The ONLY option Ubuntu seems to accept is the default 1.44Mb.

Here is what I mean.  The proper way to format a floppy from Root is to use the commmand:  fdformat /dev/fd0H1440 but if you do this, Ubuntu reports, file or directory not found.

Another quirk:  To format into ext2 you must first format as MSDOS.
The command for Low Level format don't seem to work.  But then fdformat IS the low level.  If you make the floppy an ext2 floppy Ubuntu does NOT recognize the floppy but it does recognize DOS floppies with ease.

I do HAVE ext2 in my fstab!

I also have about 100 2Mb floppies with no way to use them on Ubuntu.
It also did not see 720 floppies either.

FWIW: Same computer but under Red Hat, allows me to format and use the 2Mb floppies in the same drive.  It also formats them using H2000.
But neither Debian based platform I have allows anything but 1.44Mb disks.

WHAT am I missing here?????

Thanks

TTUL
Gary

---

### Post by Kellemora on 2008-09-11
Just bumping it up, looking for an answer to my question.

fdformat /dev/hd0H1440 does not work, shows file or directory not found.

Does Ubuntu have it's OWN command for formatting floppies?

TTUL
Gary

---

### Post by Kellemora on 2008-09-23
Been a whole week, bumping again, still looking for the answer!

TTUL
Gary

---

### Post by lukjad on 2008-09-23
Honestly, I rarely use floppies. I have only formatted them using DOS. I'll have to look it up. If you find out, drop me a line.

---

### Post by kansasnoob on 2008-09-23
Sorry, I'm clueless! The last thing I used my floppy for was creating a Super Grub Disk that's seldom used.

---

### Post by Kellemora on 2009-01-09
Bump

---

