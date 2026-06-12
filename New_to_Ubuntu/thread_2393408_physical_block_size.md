---
title: "physical block size"
date: 2018-06-03
forum: New to Ubuntu
---

### Post by ilabordus on 2018-06-03
Yesterday I posted a question under the title: Backup&redo does not see systemdisk?
The problem being about Backup&redo not functioning as expected.
Now -in using GPart in order to inspect my partitions (curiousity, nothing more at this time)- I got this warning: driver descriptor says the fysical blocksize is 2048 bytes, but Linux says it is 512 bytes.
This raises two questions:
- might this be related to the yesterday-problem?
- do I have to do something about this (and if so: what)?

---

### Post by TheFu on 2018-06-03
As long as the partitions are aligned, it doesn't matter.  Usually during install the first partition begins 2KB in from the start of the disk to ensure alignment.
If you run **sudo fdisk -l** and see any message about "alignment", then you should worry. A misaligned disk/partitions can suck 30+% of performance from spinning HDDs.  On a fresh install, that won't happen, but if you've upgraded and moved disk from older storage to new storage over the years, it could.

  s/fysical/physical/

---

