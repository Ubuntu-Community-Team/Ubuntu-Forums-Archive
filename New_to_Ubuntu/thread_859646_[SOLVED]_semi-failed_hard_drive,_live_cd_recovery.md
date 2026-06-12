---
title: "[SOLVED] semi-failed hard drive, live cd recovery"
date: 2008-07-14
forum: New to Ubuntu
---

### Post by blampars on 2008-07-14
My hard drive has finally gone kaput (at least some what).  Ive booted from the ubuntu 8.04 live cd i have, and it auto mounts my hard drive. i can browse it no problem.
ive plugged in my 30gb ipod so i can copy my home directory on the hard drive to the ipod, but i'm not quite sure how to go about that. i dont have permissions needed to access all the directories or files in my home directory.

i've chrooted into my drive which is listed at /media/drive

i just dont know how to ```
cp /home/brad /to/ipod/location
```

using ```
sudo fdisk -l
``` does not yield any information from my chroot session.

some help pointing me in the right direction would be appreciated :)

thanks!

---

### Post by Xerp on 2008-07-14
So you can see your iPod, yes? You can copy your home thus:

```
sudo cp -r /media/sda1/home/brad /media/sdb1/ipod/directory
```

---

### Post by blampars on 2008-07-14
excellent, that seems to have worked beautifully.

thank you !

---

