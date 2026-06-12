---
title: "[SOLVED] How can I tell the name of my Windows partition?"
date: 2008-08-19
forum: New to Ubuntu
---

### Post by curiousnoob on 2008-08-19
I can find my Windows partition and see all the files but I need to know if it is SDA1, SDA2, etc.  
How can I find this out?

---

### Post by Vivaldi Gloria on 2008-08-19
```
sudo fdisk -l
```

---

### Post by curiousnoob on 2008-08-19
Thanks.

---

### Post by Sorivenul on 2008-08-19
A little more explanation:
sudo fdisk -l will output a list of your current partitions.  Your Windows partition is the one with filesystem type NTFS most likely.

---

