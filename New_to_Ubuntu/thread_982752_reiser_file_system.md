---
title: "reiser file system"
date: 2008-11-15
forum: New to Ubuntu
---

### Post by stonecoldjha on 2008-11-15
i had reinstalled hardy on my PC that has 2 gigs of RAM,an intel core2duo processor and nvidia Geforce 6200.but,i found the system to be slow and inresponsive as compared to my earlier installations on the same computer.i decided to reinstall again.but,this time i decided to experiment with a few things.for the root partition,i chose Reiserfs as the file system and made it a logical partition instead of primary,and this time i saw a significant gain in system speed.my system simply flies now.i wanted to ask if the two choices really have any bearing on the much improved system sped.i also wanted to know if reiser4 is better than reiserfs?how can i use reiser4 for the root partition when i install ubuntu?thanks in advance.

---

### Post by nhasian on 2008-11-15
the logical parition vs primary partition doesnt affect the speed.  EXT3 is kinda dated... JFS, XFS, or Reiser are much faster.  we should have EXT4 for the next iteration of ubuntu in april.  its already in the latest stable linux kernel but not yet supported by the GRUB bootloader.

---

### Post by stonecoldjha on 2008-11-15
so ext4 ic good enough to beat reiser in terms of speed and performance?how can i implement reiser4 on my ubuntu system?i am ready for a fresh install,if i can choose reiser4.

---

### Post by nhasian on 2008-11-15
here's some more reading for you:

[http://www.linux.com/feature/119025](http://www.linux.com/feature/119025)
[http://www.dslreports.com/forum/r18916226-](http://www.dslreports.com/forum/r18916226-)
[http://wiki.archlinux.org/index.php/JFS](http://wiki.archlinux.org/index.php/JFS)

---

### Post by cariboo on 2008-11-15
See this atricle:

[http://en.wikipedia.org/wiki/Reiser4](http://en.wikipedia.org/wiki/Reiser4)

Check the Future of Reiser4

Jim

---

### Post by stonecoldjha on 2008-11-15
but,can the root partition in ubuntu be reiser4?

---

### Post by stonecoldjha on 2008-11-16
since the future of reiser is uncertain,i wanted to know if ext4 beats reiser4 or reiserfs in terms of speed and performance?

---

