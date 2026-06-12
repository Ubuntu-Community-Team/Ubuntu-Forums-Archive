---
title: "Ubuntu 13.04 won't turn back on after closing laptop"
date: 2013-05-09
forum: New to Ubuntu
---

### Post by ElectroIgnition on 2013-05-09
I recently installed Ubuntu 13.04 alongside Windows 7 Home Premium on my Samsung NP305V5A laptop. Whenever I've booted into Ubuntu and I close the lid of my laptop, I can't get the computer to turn back on. When I press the power button, it lights up as normal but doesn't actually turn on the screen. I've tried "sudo apt-get install hibernate" to install a driver, but it didn't work and I am assuming it was the wrong driver? Has anybody else had a similar problem but found a fix? Thanks, guys.

---

### Post by 2F4U on 2013-05-09
Please provide more info about the hardware and graphics card/graphics driver you are using.

---

### Post by grahammechanical on 2013-05-09
Is the swap partition larger than the amount of RAM in the machine? The OS state has to be stored somewhere. I think that it is stored in Swap. Is there enough space in swap? Remember, when you close the lid all kinds of hardware get switched off to save battery power. Including RAM.

Regards.

---

