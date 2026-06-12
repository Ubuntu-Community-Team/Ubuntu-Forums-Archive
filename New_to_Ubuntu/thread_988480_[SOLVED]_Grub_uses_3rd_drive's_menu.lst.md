---
title: "[SOLVED] Grub uses 3rd drive's menu.lst"
date: 2008-11-20
forum: New to Ubuntu
---

### Post by Xyro on 2008-11-20
I have a system set up with 3 (nearly) identical installs of Ubuntu 8.04 server 64bit, each on a different physical drive (sda1, sdb1, sdc1). I've varied a few things on each trying to find an optimal set-up for disk write speed. The problem I am having (a bit nit-picky) is that the menu.lst located on sda1 is not being used, but Grub is using the menu.lst on sdc1. Really, it doesn't matter, but I am interested in knowing why, since I would prefer it use the one from sda1 (a bit OCD). In a quick search I see you can redirect it from sdc1 to sda1, but why not go directly to sda1? Where/when is grub being told to look on sdc1 for menu.lst?

---

### Post by caljohnsmith on 2008-11-20
Probably Ubuntu on sdc1 was the last Ubuntu you installed, and it put Grub into the MBR of your sda drive by default; thus the Grub in sda's MBR would point to your sdc1 drive for the menu.lst. You can easily correct it with:
```
sudo grub
grub> root (hd0,0)
grub> setup (hd0)
grub> quit
```
And that will reinstall Grub to the MBR of the sda drive, but it will point to sda1 for its boot files. Give that a shot and let me know how it goes. :)

---

### Post by Xyro on 2008-11-20
Success! Thanks very much! :)

---

