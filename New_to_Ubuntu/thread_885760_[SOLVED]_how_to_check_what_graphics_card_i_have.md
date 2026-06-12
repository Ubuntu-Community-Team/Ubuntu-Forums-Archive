---
title: "[SOLVED] how to check what graphics card i have"
date: 2008-08-10
forum: New to Ubuntu
---

### Post by cgkades on 2008-08-10
According to Toshiba I have either an Intell display driver or Nvidia. how do i tell? i have a tosihba satellite p105-S6024

---

### Post by Diabolis on 2008-08-10
Execute this in a terminal:
```
lspci | grep VGA
```

---

### Post by cgkades on 2008-08-10
bah, it's intell. Thanks for the info!

---

### Post by cdtech on 2008-08-10
lshw

This will give a list of all the hardware in your PC.

---

