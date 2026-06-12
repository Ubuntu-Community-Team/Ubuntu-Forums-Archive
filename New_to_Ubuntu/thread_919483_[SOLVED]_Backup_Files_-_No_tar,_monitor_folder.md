---
title: "[SOLVED] Backup Files - No tar, monitor folder?"
date: 2008-09-14
forum: New to Ubuntu
---

### Post by dioltas on 2008-09-14
I am looking for an application or script to easily back up my music to a portable hard drive.

I would like something that I could run when I connected my hard drive, that would check if new files have been added to my Music folder, and copy them to /media/externalharddrive/Music/ or whatever. Also I need something that will just copy the files without compressing/archiving them. Any suggestions?

Thanks.

---

### Post by swisscow on 2008-09-14
Unison - it's in the repos. It will synchronise just nicely an mp3 player and an external drive

Only thing you may have to do is to tell it to ignore the permissions by adding the line

perms=0

to the profile file (hidden folder in home)

---

### Post by dioltas on 2008-09-14
Thanks, thats exactly what I was looking for. Trying it out now, seems perfect.

---

### Post by swisscow on 2008-09-14
My pleasure, good luck with it

---

