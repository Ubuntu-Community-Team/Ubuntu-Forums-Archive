---
title: "updated nvidia drivers, monitor won't work"
date: 2012-08-20
forum: New to Ubuntu
---

### Post by dwivnoob on 2012-08-20
Hi, I recently installed Ubuntu 11.10 on my HP dv6 laptop. I activated the Nvidia drivers and my system froze. Alt+Sysrq+REISUB didn't work so I switched off the machine via the power button. When I started it up again the monitor doesn't work. No display. Since its not a dual boot I basically cannot use my laptop now. Please help!

---

### Post by PhantomTurtle on 2012-08-20
Read this thread on how to use nomodeset - [http://ubuntuforums.org/showthread.php?t=1613132]("http://ubuntuforums.org/showthread.php?t=1613132"). > How to temporarily set kernel boot options on an installed OS (not wubi)

To set kernel boot options, you must edit your grub configuration. You can do this temporarily for a single boot by entering the grub menu. If you do not get to see the grub boot menu after the bios automatically, you may have to press SHIFT key after the bios logo to get in to grub:



Select the default ubuntu kernel (usually the top one), and rather than pressing enter, press E to edit.

Press DOWN ARROW until you get to the line that starts with

Code:
linux /boot
and press END keys to position your cursor at the end of the that line usually ending with “quiet splash”. 

Now you can type in additional kernel options like nomodeset (please dont make the same typing error I made for this screenshot  ):



press control+X to boot the modified grub entry.

Basically add nomodeset after quiet splash. Once you get into Ubuntu just remove the Nvidia drivers you installed.

---

