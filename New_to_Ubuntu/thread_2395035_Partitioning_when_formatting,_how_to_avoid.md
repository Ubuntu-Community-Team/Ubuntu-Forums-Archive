---
title: "Partitioning when formatting, how to avoid?"
date: 2018-06-25
forum: New to Ubuntu
---

### Post by jasdeep24 on 2018-06-25
Hi there,

I've recently bought a Samsung SSD and i'm trying g to format it Ext4 in ubuntu 14.04, but whenever i  try to format it partitions automatically how can i avoid this happening?

---

### Post by ajgreeny on 2018-06-25
Assuming this SSD is already installed in a machine with *ubuntu already installed please run command ```
sudo parted -l
``` and show us the output here.  That will show us the current partitioning of all disks present and should help us to figure out your difficulty.

Please use **Code-Tags** for terminal output. See my signature below for a **How-to**

---

### Post by Dennis N on 2018-06-25
To avoid the automatic creation of partitions, select the "Something Else" option from the installer's installation type screen. Then you get the disk partitioning screen where you can specify what you want.

---

