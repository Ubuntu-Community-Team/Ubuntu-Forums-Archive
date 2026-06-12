---
title: "I have HFS+!  But Gparted says I don't"
date: 2008-07-05
forum: New to Ubuntu
---

### Post by revun096 on 2008-07-05
Well, I installed:

hfsplus
libhfsp0
libhfsp-dev

But, in gparted, it still doesn't let me create hfs+ partitions!  Help!

---

### Post by shirilover on 2008-07-05
According to this -> [http://gparted.sourceforge.net/features.php](http://gparted.sourceforge.net/features.php)
you cannot create an HFS+ partition with gparted.

---

### Post by revun096 on 2008-07-05
Well, in that case, can I create mac os x with hfs instead of hfs+?

---

### Post by avtolle on 2008-07-05
From what I recall, cannot create hfs+ partitions with Gparted; and, from reading threads on the Apple Users Forum (and their ancestors), to do anything with hfs+ partitions, the journaling must be turned off.

---

### Post by revun096 on 2008-07-05
Well then....  Could I install mac os x in a hfs partiton?

---

### Post by avtolle on 2008-07-05
I don't know the answer to your question. Perhaps a post to the Apple Users Forum might bring a response which is more informative.

---

### Post by shirilover on 2008-07-05
You can create a FAT32 partition and then before installing OS X, use Disk Utility to format the partition as HFS+.

---

### Post by revun096 on 2008-07-06
ThanKS!

---

