---
title: "dood how do u configure web cam"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by viswanathan on 2008-04-29
[FONT="Arial Black"][/FONT] doods i tried using camorama but it didnt work it gave eroor as cant dtect dev/video0 ???????/ ny help m is creative live web cam :KS

---

### Post by Vermind on 2008-04-29
Hello,
Please post the output of running ```
lsusb
``` in terminal.
You could also google with the ID number given by lsusb to Your webcam. This way You find which driver goes with Your webcam, if the driver is not included with Ubuntu. We can then help in installing the driver.

Also, the package linux-backports-modules-2.6.24-16-generic has some extra modules. I'm not sure if it contains any webcam stuff, but You could try installing it.

---

