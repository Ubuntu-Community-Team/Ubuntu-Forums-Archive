---
title: "Fujitsu Tablet problems"
date: 2012-01-14
forum: New to Ubuntu
---

### Post by Darkrising on 2012-01-14
After some fiddling I finally Installed Ubuntu 1.1 on my tablet.
The pen works, but the display will not. I currently have it hooked via VGA to my tv so that i can work on it. The tablet screen works until the Ubuntu logo appears on the screen, It then turns into a bunch of white lines and soon goes completely white. The TV screen is flashing erratically. I Know little or nothing about Linux.
I have heard that it is a Driver problem, "i810" or something like that. 

Fujitsu st4110

---

### Post by Favux on 2012-01-15
Hi Darkrising,

Welcome to Ubuntu forums!

Not sure I remember the Fujitsu ST4110's having a video problem.  Are those convertible tablet PCs or slates?  I forget.

Are you maybe talking about an integrated Intel video chipset?  If you know how to open a terminal, to determine your video chipset, run in the terminal this command:
```
lspci | grep VGA
```

---

