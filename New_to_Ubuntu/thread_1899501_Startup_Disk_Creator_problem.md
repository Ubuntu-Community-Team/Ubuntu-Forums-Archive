---
title: "Startup Disk Creator problem"
date: 2011-12-23
forum: New to Ubuntu
---

### Post by kaloasd on 2011-12-23
I'm trying to create a bootable flash drive but when the installing process reaches the finishing stage it freezes. I see some files in the drive but I don't know if they are complete or error free. can anyone suggest some ways of checking perhaps with the md5sum file in the drive itself.also I was wondering if some files on the flash (autorun and some adds) would cause any problem

---

### Post by elgordodude on 2011-12-23
First, make sure the drive is at least 1 GB in size.

Second, I would reformat the drive as FAT32.

If the installation is still giving you trouble I would try to redownload the ubuntu .iso or try a slightly different flavor such as lubuntu

"some files" can be a lot of different things, but when I build livedrives I always start with a fresh clean drive, and then build within the persistent file system, you'll find it much easier than trying to install on top of whatever is there.

---

