---
title: "SEC_TYPE=&quot;ext2&quot;"
date: 2008-09-09
forum: New to Ubuntu
---

### Post by expatCM on 2008-09-09
I have all my drives formatted to ext3.  If I run blkid I get a listing of the UUID and other information.  On some of the drives this includes the following string - 

 SEC_TYPE="ext2" TYPE="ext3" 


Does anyone know what the reference to SEC_TYPE=”ext2” means?

---

### Post by Pro-reason on 2008-09-09
It means secondary type.  Ext3 partitions can always also be mounted at ext2, because ext3 is just ext2 with a [journal]("http://en.wikipedia.org/wiki/Journalling_file_system").

---

### Post by expatCM on 2008-09-09
Thanks for the reply and the link.

What I guess I don't understand now is why some drives / partitions include this and some do not.  Since drives are set up in fundamentally the same manner I would have expected this entry on all of the drives (or the other view, none of the drives).  Do you happen to know why there are differences?

---

### Post by Pro-reason on 2008-09-09
Are you saying that you have some drives with *SEC_TYPE="ext2" TYPE="ext3"* and some with just *TYPE="ext3"*?

---

### Post by Pro-reason on 2008-09-09
Looking at my own machine, I see that my big data partition has the *SEC_TYPE="ext2"* property, but my USB thumb drive only has *TYPE="ext3"*.

My iRiver E100 audio player just has *TYPE="vfat"*, yet I notice that other people online seem to have *SEC_TYPE="msdos" TYPE="vfat"* for their FAT-formatted drives.

Curious.

Maybe it is to do with size?   I don't think it affects anything.

---

### Post by expatCM on 2008-09-09
Exactly, the following is what I see from sudo blkid

What puzzles me is - 

1. sda1 is in the format TYPE= and then SEC_TYPE= whereas sdb1 is the other way round.

2.  sdc1 does not mention SEC_TYPE but sdc3 does .....

sda1 and sdb1 are the same make and 200GB size hdd each as a single partition.  sdc is a partitioned 500GB drive.


```
/dev/sda1: UUID="5da58b53-3947-43fc-9628-a4f6d5354afd" TYPE="ext3" SEC_TYPE="ext2" 
/dev/sdb1: UUID="6988b9fe-7c81-4061-a8ae-b5682330a3df" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc1: UUID="e2c4e39b-f3ed-44e6-b63c-e436c7dfb8b8" TYPE="ext3" 
/dev/sdc2: TYPE="swap" UUID="a5e9b86e-ac97-4aa8-801b-798e7c079620" 
/dev/sdc3: UUID="ea718670-885a-46a7-96f5-2e681a85445b" SEC_TYPE="ext2" TYPE="ext3" 
```

---

### Post by spaceballl on 2009-11-18
I know this is an old thread, but i'm pretty curious about this myself... can anyone shed some light?

---

