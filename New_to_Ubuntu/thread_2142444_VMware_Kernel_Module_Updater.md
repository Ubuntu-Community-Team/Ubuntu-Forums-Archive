---
title: "VMware Kernel Module Updater"
date: 2013-05-05
forum: New to Ubuntu
---

### Post by Liffxng on 2013-05-05
I have a problem while install VMware. It's pop up the messages " Kernel headers for version 3.8.0-19-generic were not found "; and when I clicked on install it said C header file matching your kernel were not found. 

What should I do ?
Thanks xD

---

### Post by Cheesemill on 2013-05-05
Try installing the headers for your kernel...
```
sudo apt-get install linux-headers-$(uname -r)
```

---

### Post by Liffxng on 2013-05-05
it's download 2 files into /usr/src/ linux  headers 3.8.0-19-generic and linux headers 3.8.0-19.
but it doesn't do anything.

---

### Post by Cheesemill on 2013-05-05
VMware should work properly now you have the kernel header files. Is is still giving you an error?

---

### Post by Liffxng on 2013-05-06
it doesn't give any error at all. It's just pop up the box with kernel header missing and when i clicked on install it say missing C header files.

---

