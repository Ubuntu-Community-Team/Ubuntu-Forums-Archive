---
title: "Disable Certain Updates"
date: 2008-06-12
forum: New to Ubuntu
---

### Post by bren21 on 2008-06-12
There are a few updates I do not want to install, like the new kernel update since I am too lazy to get it working with my graphics card. Is there any way for me to stop the kernel updates and other updates from showing up on the list?

---

### Post by johnl on 2008-06-12
If you go into synaptic and find the package you want to prevent from being upgraded,  you can click on it, go the the 'package' menu, and choose 'lock version'.  This will prevent newer versions of that package from being installed.

I suspect to keep the kernel from updating you will need to lock the linux-image-generic and possibly linux-restricted-modules-generic packages, though I could be wrong.

Hope this helps!

---

### Post by drs305 on 2008-06-12
You can also set grub's menu.lst to keep the current kernel as default.
[HOWTO: Grub Menu Kernel Display Options]("http://ubuntuforums.org/showthread.php?t=818177")

Startup-Manager, Advanced, Automatically update default boot option = unticked.

---

### Post by bren21 on 2008-06-12
Worked great! Thanks for the info.

---

