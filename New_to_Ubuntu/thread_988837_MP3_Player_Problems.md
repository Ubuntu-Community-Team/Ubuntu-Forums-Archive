---
title: "MP3 Player Problems"
date: 2008-11-20
forum: New to Ubuntu
---

### Post by waldo_phill on 2008-11-20
I have a 4GB RCA Lyra H100A that is almost full. When plugged in the music files do not show (just the system files). Amarok and Rythmbox do not recognize it. Any help getting this set up would be appreciated.

---

### Post by keplerspeed on 2008-11-20
Can you access the mp3 files for a windows machine? Is this a linux specific issue or a hardware issue? Unlikely they are hidden.. but try pressing ctrl-h when navagating the volume, and see what appears.

---

### Post by michande03 on 2008-11-20
what filesystem is the player, have you tried mounting it as sudo.

---

### Post by waldo_phill on 2008-11-21
> **keplerspeed said:**
> Can you access the mp3 files for a windows machine? Is this a linux specific issue or a hardware issue? Unlikely they are hidden.. but try pressing ctrl-h when navagating the volume, and see what appears.

I can access the files on a windows machine so it is a linux issue. Unfortunately they are not hidden.

> **michande03 said:**
> what filesystem is the player, have you tried mounting it as sudo.

As far as mounting is concerned I am still rather new at this...the file system is vfat. I may have mounted it wrong...if there is a thread on this or if someone can walk me through it I would appreciate it.

---

### Post by michande03 on 2008-11-21
as far as for me, and my kernel and ubuntu intrepid it mounts per auto with usb sticks and such through hal userwise and should do so for you aswell. have you tried to unmount it when its inserted. That you should be able to do through filebrowser, and rightclick disk and unmount, as kinda secure remove of usb disk. or maybe give rights to the disk via sudo chmod <whatyawant> /path/to/mountpnt

oh and sorry... to see what is mounted and how, just open terminal and type mount, or sudo mount, then all mounts should be vicible for you

---

