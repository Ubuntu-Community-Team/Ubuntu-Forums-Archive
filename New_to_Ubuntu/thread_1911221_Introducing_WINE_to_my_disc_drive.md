---
title: "Introducing WINE to my disc drive"
date: 2012-01-18
forum: New to Ubuntu
---

### Post by RFS-81 on 2012-01-18
Hi!  I installed Ubuntu 11.10 a few days ago and really like it!  I only have a little problem (or rather inconvenience) with WINE 1.2: Ubuntu automatically mounts the disc drive to /media/(disc name) (e.g. /media/Diablo II Disc 1), so everytime I change the CD/DVD I must change the configuration of WINE. Is there some way I can make WINE always find the drive without having to mount manually?

---

### Post by insane_alien on 2012-01-18
you could just point it to the device rather than the mount point 

for example, /dev/sr0 is your first CD/DVD drive (I think ubuntu still links this to /dev/cd and /dev/dvd so either of these will work too.)

---

### Post by RFS-81 on 2012-01-18
Thanks for your answer, but that didn't work. I tried running a game (Baldur's Gate) and when I gave WINE the mount point, it ran, but when I gave it /dev/sr0, I got an error telling me that no CD drive was detected. But for all I know that might as well have something to do with some copy protection stuff.

---

