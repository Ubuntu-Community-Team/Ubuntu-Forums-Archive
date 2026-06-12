---
title: "[SOLVED] Swap partition"
date: 2008-11-27
forum: New to Ubuntu
---

### Post by bcd87 on 2008-11-27
Hi there.

I intend to install another distro tonight on my second harddrive. I was wondering if I can use the swap partition I made while installing Ubuntu for the other Linux distro too?

So:
Ubuntu partitions (including swap) are on sda. Can I install another distro on sdb but use the swap on sda?
If I config my fstab correctly this should be no problem right?

---

### Post by Bucky Ball on 2008-11-27
No expert, but don't see why not. You can do it on one drive/2 OSs, so why not 2 drives/2 OSs? As long as the swap is the correct format for both OSs.

---

### Post by Kobalt on 2008-11-27
Yes, you can use the same swap partition with multiple Linux distributions.

---

### Post by Bucky Ball on 2008-11-27
> **Kobalt said:**
> Yes, you can use the same swap partition with multiple Linux distributions.

With one OS on another physical drive from the swap is the question ...

---

### Post by handydan918 on 2008-11-27
Buckyball is correct. Multiple installs can share swap. If the installer you use doesn't allow you to point it at the existing swap partition, you can do it afterward with the swapon command.

---

### Post by bcd87 on 2008-11-27
Great :) Thanks for the quick replies.

---

