---
title: "Help on making custom partition before installation"
date: 2012-03-12
forum: New to Ubuntu
---

### Post by ds95 on 2012-03-12
I have got Ubuntu 10.10 and tried it on Live CD.Now I am thinking of installing it .My hard drive is of 500GB and windows 7 home basic installed.I want to make a windows 7 partition(maybe around 40GB) , a Ubuntu partition (around15GB) and the rest space as data partition.Do I have to shrink the existing partition in disk management utility? Or go straight to Ubuntu and edit the partitions manually ? Please give me step by step instruction for I am a little confused what to do exactly.I am kind of a beginner.Also tell me if I have to make more necessary partitions like swap .

---

### Post by Frogs Hair on 2012-03-12
You can use Windows disk management to shrink the volume or partition from the Ubuntu installation disc.
 _10.10 reaches end of life in two months_, so consider a newer version. 12.04 will be released in late April.

---

### Post by oldfred on 2012-03-12
With MBR you can only have 4 primary partitions but one can be an extended that holds many logical partitions. Data & Linux boot partitions can be in logical partitions, but Windows wants primary partitions as boot (active) partition.

How many primary partitions have you used?
Are you thinking of installing a second copy of Windows?

Post this from liveCD to see partitions:

```
sudo fdisk -lu
```

Best to use Windows to shrink NTFS partitions, but do not create new partitions as it may convert to dynamic not extended/logical. Linux does not work with dynamic partitions.

---

