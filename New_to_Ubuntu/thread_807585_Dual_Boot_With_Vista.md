---
title: "Dual Boot With Vista"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by Etheredge on 2008-05-25
I have ubuntu on this laptop and would like to put vista on here

all i have to do is creat two partitions on the main HD right?

but the problem is how do i creat a second partition without unmounting it?

sorry for bein illiterate on this subject

---

### Post by damis648 on 2008-05-25
Either use gparted on the Ubuntu LiveCD or the visparted LiveCD so resize the Ubuntu Ext3 partition and then create a new NTFS partition. After installing vista, you will have to reinstall the linux grub, however.

EDIT: sorry the Visparted liveCD is actually PartedMagic, as mentioned by the poster below.

---

### Post by wolfen69 on 2008-05-25
i suggest [PartedMagic]("http://partedmagic.com/wiki/PartedMagic.php") to create a partition.

---

