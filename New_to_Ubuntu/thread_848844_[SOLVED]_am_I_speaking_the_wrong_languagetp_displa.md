---
title: "[SOLVED] am I speaking the wrong languagetp display disk performance?"
date: 2008-07-03
forum: New to Ubuntu
---

### Post by adamogardner on 2008-07-03
root@CRONUS:/home/adamogardner# hdparm -t /dev/hda
/dev/hda: No such file or directory
root@CRONUS:/home/adamogardner# 
root@CRONUS:/home/adamogardner# # hdparm -t /dev/hda
root@CRONUS:/home/adamogardner# 
root@CRONUS:/home/adamogardner# # hdparm -t /dev/hda
root@CRONUS:/home/adamogardner#

---

### Post by shad0w_walker on 2008-07-03
Try:

```
sudo hdparm -t /dev/sda
```

---

### Post by Rocket2DMn on 2008-07-03
You can check your drives and partitions with
```
sudo fdisk -l
```

---

