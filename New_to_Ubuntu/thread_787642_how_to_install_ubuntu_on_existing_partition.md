---
title: "how to install ubuntu on existing partition?"
date: 2008-05-09
forum: New to Ubuntu
---

### Post by mabtifro2 on 2008-05-09
i have a small sata drive that i used to use as an external hard drive. it is formatted as fat 32 and i have some files on it, but no os. i installed the drive in my laptop and started it up with live cd 8.04. but i cant figure out which option to choose to install ubuntu on the same partition. i do not want to create a new partition. can i just simply install it without formatting or partitioning anything? if the answer is no, then ill just use the entire disk without adding a separate partition. but then can i do that without formatting it to ext3? i want to keep fat32

---

### Post by subzero316 on 2008-05-09
> **mabizeid said:**
> i have a small sata drive that i used to use as an external hard drive. it is formatted as fat 32 and i have some files on it, but no os. i installed the drive in my laptop and started it up with live cd 8.04. but i cant figure out which option to choose to install ubuntu on the same partition. i do not want to create a new partition. can i just simply install it without formatting or partitioning anything? if the answer is no, then ill just use the entire disk without adding a separate partition. but then can i do that without formatting it to ext3? i want to keep fat32


Linux will not install on fat type filesystem.
As for partitions you ll need em for home , swap , root.
All these will be created. Go through the installation Docs [here]("https://help.ubuntu.com/community/GraphicalInstall").

---

### Post by malathion on 2008-05-09
The answer is no you cannot install linux on fat32 (thank goodness). If you must have those files stored on a fat32 partition, then your best bet is to create a new partition for linux and leave those files on the fat32 partition.

---

