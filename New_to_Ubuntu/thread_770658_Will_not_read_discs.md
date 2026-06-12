---
title: "Will not read discs"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by OKnotOK on 2008-04-27
Ok, I've just recently installed 7.10 on my PC, and I'm having a few problems.  Primarily, the CD/DVD drive won't read anything (audio, data, movies, nothing).  When i put in a data CD, the error i get is: 
Cannot Mount Volume:
invalid mount option when attempting to mount the volume 'UDF volume'
Audio CDs just show up on the desktop as a 'CD ROM' icon

When i was installing, I couldn't get online, so maybe it missed some part of the installation.
Any help is greatly appreciated.  Thanks!

---

### Post by OKnotOK on 2008-04-27
Bump.
Wow, these boards move fast.   Any ideas on my problem above?

---

### Post by OKnotOK on 2008-04-27
*Bump*Bump*

Any help here?

---

### Post by DezSP on 2008-04-27
Hi there,

This could be an installation problem. Have you checked the CD you used? Simply boot from it, and choose "Check CD for defects" from the menu. It'll run through and check there's no errors.

You could also try mounting manually via the terminal:

sudo mount /dev/cdrom /media/cdrom0
cd /media/cdrom0
ls

---

