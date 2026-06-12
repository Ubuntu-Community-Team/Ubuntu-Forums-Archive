---
title: "where is /dev/hda8"
date: 2008-05-12
forum: New to Ubuntu
---

### Post by pppaaarrrkkk on 2008-05-12
I can't do mount /dev/hda8 /mnt/hda8 because /dev/hda8 doesn't exist.

/dev/hda8 does exist if using other distros

Can any one say what I should do please ?

---

### Post by Cypher on 2008-05-12
"/dev/hda8" has little to no bearing on the distro you are using, but has everything to do with your HD partitioning scheme.

So start with the following command
```

sudo fdisk -l

```
This will list the current partitions and their numbering. Once you have that information you can then try to mount the partition you want using the correct name.

---

### Post by pppaaarrrkkk on 2008-05-12
Okay, thanks. That works.

---

### Post by BDNiner on 2008-05-12
I agree with Cypher. If you have less than 8 partitions on your disk then /dev/hda8 will not exist.

---

