---
title: "hfs+ externald drive read and write"
date: 2012-03-19
forum: New to Ubuntu
---

### Post by klqd on 2012-03-19
:popcorn:


i got this working via google a while back but i can't remember which walk through worked.
thanks :guitar:

---

### Post by mike555 on 2012-03-20
I think You need to have "   hfsprogs , hfsutils , hfsplus " installed.

---

### Post by Lars Noodén on 2012-03-20
Also, the target drive can't be using journaling.  That's not supported yet.  You can turn it off in OS X before trying to read/write in Ubuntu.

---

### Post by klqd on 2012-03-20
thanks. i assume that's safe ^^


do i need to edit etc/fstab?

---

### Post by Lars Noodén on 2012-03-20
AFAIK it's quite safe, I use HFS+ all the time with Ubuntu.

You only need to edit /etc/fstab if you will keep mounting the same drive and want to automate some of the mount options.  

But your regular desktop environment should detect it and mount it when you plug it in, just like it would for regular EXT partitions.

---

### Post by klqd on 2012-03-22
i remember before the drive seemed to keep rejournaling itself? anyway it's working now - thanks guys :D !

---

