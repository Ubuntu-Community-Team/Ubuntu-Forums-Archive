---
title: "Problem:kubuntu 12.4 Desktop Effects not available"
date: 2012-05-11
forum: New to Ubuntu
---

### Post by Bumpalot on 2012-05-11
p, li { white-space: pre-wrap; }  Desktop effects are not available on this system due to the following technical issues:
  kubuntu 12.4

Required X extensions (XComposite and XDamage) are not available.
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GTX 550 Ti"
    "TwinViewXinerama
Section "Extensions"
    Option         "Composite" "Disable"
unable to change permissions on etc/X11/xorg.conf
bump@BUMPYKDEPUTER:/etc/X11$ sudo chmod -v a+rw xorg.conf
[sudo] password for bump: 
mode of `xorg.conf' changed from 0744 (rwxr--r--) to 0766 (rwxrw-rw-)
How can I enable Composite?

---

### Post by wildmanne39 on 2012-05-22
Hi, click on the link in my signature and follow the guide for setting up compiz in 12.04 but is workingis al dependent on your video card and driver.
Thanks

---

