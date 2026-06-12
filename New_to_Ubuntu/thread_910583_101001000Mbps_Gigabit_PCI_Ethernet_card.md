---
title: "10/100/1000Mbps Gigabit PCI Ethernet card"
date: 2008-09-04
forum: New to Ubuntu
---

### Post by rockerphil on 2008-09-04
ok,this is a bit mind boggling to me, but the other night after logging off i was unable to get online the next morning, so i rebooted my box and found that my Ubuntu sysytem was no longer detecting my D-Link PCI ethernet card which had worked for me in Linux for almost a year so i replaced it with a $15 10/100/1000Mbps Gigabit PCI ethernet card which still wouldn't be detected by my Ubuntu system, so i attempted to install the Linux driver provided by the manufactorer of the card (i know, surprising that they supplied one) to no avail. well here's the mind boggling part.after doing some searching through the clutter i found my Damn Small Linux Live CD to see if it would pick up the card, and that's what i'm writing this post from right now. now, here's where the great people of te Ubuntu community come in, i'd like to be able to get online from my Ubuntu install without having to reinstall my OS since it was built over some time from a CLI, any suggestions would be greatly appreciated,

Phil

---

### Post by paul_mcl on 2008-09-04
First of all, try
```
lspci
```
and see if your card is present.

---

### Post by rockerphil on 2008-09-04
thank you for the speedy response, and no, my Ubuntu install doesn't list either of my ethernet cards when i run that command, yet i can get online when running from a live CD

---

### Post by paul_mcl on 2008-09-04
> my Ubuntu install doesn't list either of my ethernet cards when i run that command
Well, you'll need to compile a kernel module for your card. Try to google "<card model> linux driver".

---

### Post by rockerphil on 2008-09-04
but that's what's mind boggling to me, the card i replaced the old one with is what i'm using to get online from my DSL Live CD, so obviously it works fine in Linux, and the old one worked fine for almost a year, yet Ubuntu detects neither

---

### Post by paul_mcl on 2008-09-04
> the card i replaced the old one with is what i'm using to get online from my DSL Live CD
Okay, please deliver outputs from
```
uname -r
```
from both of your linuxes.

---

