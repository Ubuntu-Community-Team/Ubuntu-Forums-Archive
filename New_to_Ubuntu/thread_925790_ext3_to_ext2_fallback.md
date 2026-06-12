---
title: "ext3 to ext2 fallback :"
date: 2008-09-21
forum: New to Ubuntu
---

### Post by sandylovesgnr on 2008-09-21
I have ubuntu installed in ext3 filesystem. I m doing some access read/write latency check. I need to do that for both ext3/ext2. How can i mount ext3 to ext2 just for testing purpose and move back? I have no idea about mounting and all..
pls help

---

### Post by nowshining on 2008-09-21
internal or external drive??

---

### Post by sandylovesgnr on 2008-09-21
its an internal hard drive.

---

### Post by nowshining on 2008-09-21
ah: hmmm you'll need to mount the drive with writeback to get close to ext3 performance, or u can try manually mounting the drive 

example: in /media/ create a folder

then issue

mount /dev/sd__ /media/drive name u chose/ -t ext2

---

