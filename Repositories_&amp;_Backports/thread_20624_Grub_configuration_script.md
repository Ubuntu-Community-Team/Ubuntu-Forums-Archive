---
title: "Grub configuration script?"
date: 2005-03-17
forum: Repositories &amp; Backports
---

### Post by trigg on 2005-03-17
Okay here is my issue - I had ubuntu on one hard drive and decided that I wanted it on another.  I successfully copied the partition using partimage and knoppix - chrooted into the install, updated the grub/menu.lst and the etc/fstab and everything booted fine. The problem appeared when I updated the kernel - for some reason the grub update script still thinks my kernels are located on the original hard drive and partition. The original install was on (hd1,2) and now the install is located on (hd0,5).  No matter how many times I go in and change it, if I add a kernel or for some reason the update-grub (or is it grub-update) script is run - ubuntu "automagically" generates a completely incorrect - but totally consistent list of kernels.  The original hardrive partition no longer exists, so I know the script isn't "finding" other kernels on other partitions. . .

Anyone have a clue?

trigg

---

### Post by trigg on 2005-03-17
ok.  I just deleted menu.lst and then did an update-grub and all is well.  brain not firing on all cylinders today.

---

