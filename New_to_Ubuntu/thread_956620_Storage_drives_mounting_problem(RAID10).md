---
title: "Storage drives mounting problem(RAID10)"
date: 2008-10-23
forum: New to Ubuntu
---

### Post by CenturionKenshin on 2008-10-23
Installed Ubuntu 8.04 to Compaq Prolliant server ML370

Have 4 SCSI 18.6 Gb drives installed in array RAID 5. Actually the system is setuped on them, no problems.

Other 2 drives  36.4 Gb are setuped into array RAID10 otherwords it is one drive and the other is mirror.

I can not mount this array. Partitioned it with cfdisk, no problems, but when I try to mount it with ext3 (Linux file system 83) it says that it is not right fs and etc.. pretty long.

Did anyone have such a problem?

---

### Post by CenturionKenshin on 2008-10-28
No one replied... :(

But I found a problem...it is hmm my head...
I forgot to setup file system to a partition. silly.

---

