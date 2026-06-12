---
title: "format and partitions"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by akkad on 2008-05-11
i created 3 partitions, one for root / with ext3 file system(primary), one for my data where the mount point is "/Data" also ext3 file system(logical), the last one is the swap(logical), now i can see that the Data partition appears under the root (as it is mounted there), does this means if later i wanted to format the root it will affect the Data partition ??

---

### Post by bumanie on 2008-05-11
If I understand your post correctly, you want a '/' a '/data' and a 'swap' So as not to affect your /data partition, / and /data need to be on separate partitions. I hope this answers your question - if they are together, you won't be able to reinstall / without affecting your data.

---

### Post by prcm311 on 2008-05-11
No.  The folder /Data is more like a shortcut to the physical drive.  When you format a drive you are not formatting "/" or "/Data" you are formatting the physical drive (e.g. /dev/sda1 or /dev/hda1).

---

### Post by akkad on 2008-05-11
prcm311, u got my point, thnx ...

---

