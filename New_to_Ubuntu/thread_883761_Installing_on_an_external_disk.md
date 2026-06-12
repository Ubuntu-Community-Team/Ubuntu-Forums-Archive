---
title: "Installing on an external disk"
date: 2008-08-08
forum: New to Ubuntu
---

### Post by timbim on 2008-08-08
Is it possible to install ubuntu onto an external HDD, so that it can boot on any computer and take all its sensitive data with it?

---

### Post by caljohnsmith on 2008-08-08
Yes, just make sure that when you get to the part about installing Grub, you install Grub to (hd1) and not (hd0), assuming that you still have your internal HDD connected when installing Ubuntu to your external HDD. When the Live CD installer gets to the part about installing Grub, just click on the advanced button, and it will give you an option of where you want to put Grub; that's where you should specify (hd1).

---

