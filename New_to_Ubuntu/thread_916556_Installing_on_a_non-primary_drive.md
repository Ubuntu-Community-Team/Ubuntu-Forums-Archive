---
title: "Installing on a non-primary drive"
date: 2008-09-11
forum: New to Ubuntu
---

### Post by Pocket Universe on 2008-09-11
Hello.

I've grown sick and tired of Windoze's constant hiccups and crashes, therefore I am thinking of using Ubuntu as well.

My problem is that since my primary drive, or C: if you will, doesn't have any unpartitioned space left and that got me thinking, would it be possible for me to buy an additional HDD and just slap Ubuntu on it or will I be forced to redo my whole Windows installation just to resize its partition?

Some specs that may be useful:
- WinXP Home SP3
- Intel Core2 Quad 2.4 GHz
- All SATA HDDs
- 4GB RAM

Any help would be greatly appreciated.

---

### Post by Infinity-al on 2008-09-11
It's not required to reinstall windows just to partition the space. It can be done automatically by the ubuntu live cd without you losing any data at all.

---

### Post by Pocket Universe on 2008-09-11
> **Infinity-al said:**
> It's not required to reinstall windows just to partition the space. It can be done automatically by the ubuntu live cd without you losing any data at all.

I thought that since the NTFS file system is a non-free standard, all applications using it were just guesstimations and therefore you'd risk your data by performing writes to such a disk (partitioning in particular). Has anyone else heard something different?

---

### Post by bumanie on 2008-09-11
If you get a new hard drive, just install ubuntu on it - unlike windows, ubuntu easily boots from non-primary drives and can even boot from within logical partitions. During the installation, grub will get installed to the windows MBR so you will have a choice of which OS to boot into.

---

### Post by Pocket Universe on 2008-09-11
> **bumanie said:**
> If you get a new hard drive, just install ubuntu on it - unlike windows, ubuntu easily boots from non-primary drives and can even boot from within logical partitions. During the installation, grub will get installed to the windows MBR so you will have a choice of which OS to boot into.

You're a hero, thank you so much.

---

