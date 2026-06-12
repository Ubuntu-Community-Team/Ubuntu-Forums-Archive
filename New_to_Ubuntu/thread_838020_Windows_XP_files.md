---
title: "Windows XP files"
date: 2008-06-23
forum: New to Ubuntu
---

### Post by eris2305 on 2008-06-23
I set up ubuntu as a dual boot leaving Windows XP on the C: drive.  I'm very new to linux and would like to know why I can't see all the Windows files when I look in folders on the Window drive when I'm running under linux.  I can see a lot of them, but definitely not all.  They aren't 'hidden' files either.

---

### Post by bumanie on 2008-06-23
Not sure about that as all the files should be visible as far as I know. However, I would install ntfs-3g and ntfsconfig, the former allows read/write to ntfs and the latter is a gui that mounts the ntfs partition and records it in /etc/fstab. > sudo apt-get install ntfs-3g then > sudo apt-get install ntfsconfig then go to Applications --> System Tools --> ntfsconfig and make a mount point for the ntfs drive/partition, hopefully you will be able to see all the files in windows after that.

---

