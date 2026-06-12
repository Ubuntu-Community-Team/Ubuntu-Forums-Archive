---
title: "Strange symbols on boot after clean install, MacBook model A1181"
date: 2016-02-28
forum: New to Ubuntu
---

### Post by nibudd on 2016-02-28
Just completed two clean installs of Xubuntu 14.04 and then 12.04. After both installs completed I removed the install disc and rebooted. The picture below is the screen I see.
[ATTACH=CONFIG]267576[/ATTACH]
Before this happened, this MacBook was running 15.10 and then 10.04 without any boot issues. I think my bootloader is the problem.
Ideas and suggestions are very welcome.

---

### Post by nibudd on 2016-03-04
My original problem is posted here: [ubuntuforums.org/showthread.php?t=2315426]("http://ubuntuforums.org/showthread.php?t=2315426")

Essentially, after going from OSX to Xubuntu 15.10 to Xubuntu 10.04 (which all worked fine), I tried 14.04 and 12.04, both of which I cannot boot into without the install disc in the drive. Without the disc, I see the image shown in my original post.

I've used Boot Repair to do the recommended repair, but this hasn't worked. It says the problem is that my boot files aren't close to the start of the disc and recommended i use gParted to create a new /boot partition at the disc start. However, gParted shows that my boot partition is the first partition on the disc, so I don't understand what to do.

Here's a link to the data from Boot Repair: [paste.ubuntu.com/15281164/]("http://paste.ubuntu.com/15281164/")

Your help is appreciated,

Nathan

---

### Post by oldos2er on 2016-03-04
Threads merged. Please don't open more than one thread for each problem or question.

---

### Post by nibudd on 2016-03-05
During one of my clean OS installs, the boot partition was created in the FAT32 format, rather than the EXT4 format. When I used gParted to reformat the boot partition to EXT4, my next clean install worked fine.

I'm not clear on why a clean install wouldn't properly format the partitions it creates (maybe someone can explain that to me), but my problem is resolved.

---

