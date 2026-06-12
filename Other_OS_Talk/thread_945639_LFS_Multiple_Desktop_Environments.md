---
title: "LFS: Multiple Desktop Environments"
date: 2008-10-12
forum: Other OS Talk
---

### Post by JupiterV2 on 2008-10-12
I have installed LFS 6.3 and KDE 3.5.9 as a desktop environment. I would also like to install Xfce 4.4.2 by way of comparison. What are my options for choosing between the two environments at bootup? Maybe from Grub?

---

### Post by smartboyathome on 2008-10-12
You wouldn't choose between them at bootup. You need to install a display manager like GDM or KDM, and then you can choose which one you want to start up. Grub doesn't do this kind of stuff, since it simply boots the kernel.

---

### Post by JupiterV2 on 2008-10-13
Great, thanks!

Rob

---

### Post by Tux Aubrey on 2008-10-14
An alternative that I really like, is to use [bodhi.zazzen's "VirtualX" script ]("http://ubuntuforums.org/showthread.php?t=271674")and have different WM's running side-by-side in the same session.

---

