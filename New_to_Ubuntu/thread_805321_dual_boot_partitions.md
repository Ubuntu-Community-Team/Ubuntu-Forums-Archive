---
title: "dual boot partitions"
date: 2008-05-23
forum: New to Ubuntu
---

### Post by keegs on 2008-05-23
I installed Hardy Heron and Vista on my system, which has a 250gb HDD, and I partitioned the hard drive to give Vista 16gb, Ubuntu 10gb, and the swap partition 512mb.  My question is, can these OS's both share and access the free space left over, or do I have to just increase the partitions they are already in.  I want to be able to access the same files from either OS.  Thanks.

---

### Post by JC Cheloven on 2008-05-23
You have to partition and format that remaining space if you want to use it!
If you plan to acces it from both (windows & ubuntu), format it as ntfs.

BTW, 512Mb of swap seems to be scarce. It should be at least as much as your ram.
Greetings

---

### Post by thisiam on 2008-05-23
format it ntfs and install ntfs-3g and your set.

---

