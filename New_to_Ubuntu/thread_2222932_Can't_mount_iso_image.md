---
title: "Can't mount iso image"
date: 2014-05-08
forum: New to Ubuntu
---

### Post by jotapbraga on 2014-05-08
I, i'm trying to mount a iso image under lubuntu 12.04 terminal and am having  this message:
mount: /dev/loop1: can't read superblock

```
root@pentium3:/home/joaobraga/virtualdrive# mount -o loop -t iso9660 image.iso /home/joaobraga/virtualdrive/Drive0
mount: block device /home/joaobraga/virtualdrive/image.iso is write-protected, mounting read-only
mount: /dev/loop1: can't read superblock
```

What am i doing wrong?

---

### Post by LastDino on 2014-05-08
Is it getting mounted in GUI program, lets say like Furious ISO?

---

### Post by caver12 on 2014-05-09
Use to be able to right click iso image and choose mount/unmount. Is that not an option?  You could try . AcetoneISO.  It's in synaptic and in Software Center or right click any ISO file and choose "Open With > Disk Image Mounter.

---

