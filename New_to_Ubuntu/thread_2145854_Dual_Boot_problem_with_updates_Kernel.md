---
title: "Dual Boot problem with updates Kernel"
date: 2013-05-16
forum: New to Ubuntu
---

### Post by zzmax on 2013-05-16
I have Ubuntu 12.04 and dual boot Zorin6 with Ubuntu being default OS, I  have new kernel today and forgot to Update Zorin first and now Zorin  does not have the new Kernel after updates installed, do I have to do a  grub update and how? Thanks zzmax

---

### Post by ajgreeny on 2013-05-16
Which OS updated the kernel; I'm confused!

If the Zorin kernel was updated, you now simply need to run ```
sudo update-grub
``` in your ubuntu OS and your ubuntu grub will find the zorin new kernel and add it to the grub menu.

---

