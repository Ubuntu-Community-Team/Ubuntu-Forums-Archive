---
title: "mp3/mp4 device won't mount"
date: 2008-06-19
forum: New to Ubuntu
---

### Post by XSindy on 2008-06-19
mounted it once, now it won't mount
there used to be a thread some time ago with a command for this but I can't find it, any ideas?

---

### Post by KingTermite on 2008-06-19
do a "man mount" to get details.

First find out the device name by:
**sudo fdisk -l**
after you've inserted it.

To manually mount you can create a directory for it, say "/media/thumb" and then I think (at work and going by memory) its something like:
**sudo mount /sdbX /media/thumb**

sdbX would be the name you discovered earlier with the fdisk -l command.

---

