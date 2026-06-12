---
title: "Can't boot Ubuntu after adding 8600GTS card"
date: 2008-06-25
forum: New to Ubuntu
---

### Post by Samurai Penguin on 2008-06-25
I just added a 8600GTS card and when I powered up the puter it will not boot to the desktop (it hangs up while the script is still on the monitor - I forget what it says). Had the same problem after installing Ubuntu and trying to boot for the first time with the built-in 7025 GeForce graphics. Had to do with the graphics not being recognized. How can I boot an already installed Ubuntu using safe graphics mode so I can download the restricted drivers?

---

### Post by cprofitt on 2008-06-25
> **Samurai Penguin said:**
> I just added a 8600GTS card and when I powered up the puter it will not boot to the desktop (it hangs up while the script is still on the monitor - I forget what it says). Had the same problem after installing Ubuntu and trying to boot for the first time with the built-in 7025 GeForce graphics. Had to do with the graphics not being recognized. How can I boot an already installed Ubuntu using safe graphics mode so I can download the restricted drivers?

You should have an option for recovery mode when you go through GRUB at boot up... select that. Then you can select a root session and edit your /etc/X11/xorg.conf file.

Just out of curiosity what card did you switch from?

---

