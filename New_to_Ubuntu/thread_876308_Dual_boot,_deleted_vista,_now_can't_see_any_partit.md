---
title: "Dual boot, deleted vista, now can't see any partitions"
date: 2008-07-31
forum: New to Ubuntu
---

### Post by Onay on 2008-07-31
Here was my setup: Vista on an ntfs partition, using the vista bootloader and EasyBCD used to boot ubuntu.

I deleted the vista partition cuz it sucked and I was planning on installing xp. After I deleted it, Gparted, ubuntu live cd... all partition editors show my hard drive as one big unallocated space. I know that something along the line got corrupt... any ideas?

---

### Post by bobnutfield on 2008-07-31
It sounds as though you have somehow wiped the whole drive.  If you run the live cd you can verify that by opening a terminal and typing:

> fdisk -l

---

### Post by BGFG on 2008-07-31
Are you still getting into Ubuntu then ?

Remember, you would have installed Ubuntu's bootloader to the native Ubuntu's partition and used EasyBCD to add grub to the vista bootloader. Now that you've fragged vista the BIOS probably isn't seeing any bootloader. You can try to set the ubuntu partition as the default boot drive in the BIOS.

---

