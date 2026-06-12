---
title: "Windows partition problem"
date: 2013-04-28
forum: New to Ubuntu
---

### Post by Marouane9099 on 2013-04-28
I installed Ubuntu on one of my hard drive's partitions, the other one has windows on it, I need to acces the other partitions since all my data is saved there, but Ubuntu keeps on telling me I don't have permission.
Is there a way to acces the other FAT32 drive without losing all my data ?

---

### Post by Mark Phelps on 2013-04-28
IF you installed Ubuntu into an existing NTFS partition, then you installed using Wubi -- and you access your Win 7 files and folders by looking under /host in the Ubuntu filesystem.

---

