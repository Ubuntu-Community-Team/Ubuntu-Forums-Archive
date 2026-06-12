---
title: "Wifi worked during install but not after reboot"
date: 2014-05-09
forum: New to Ubuntu
---

### Post by makaha2 on 2014-05-09
I've just installed Xubuntu14.04 on my old desktop. It has a d-link dwa-510A PCI wireless adaptor. While testing xubuntu and installing from the LiveCD/DVD the wifi worked perfectly, downloading updates etc as part of the install. However once the install finished, and the PC was rebooted, the wifi simply doesn't work, even though it still had the wifi connections settings. How can this be? The card works ok in some other distros, such as linux mint maya mate.

---

### Post by stalkingwolf on 2014-05-09
try checking additional driver to see if a driver needs installing.  you will or should find it under system > preferences

---

### Post by rburkartjo on 2014-05-10
mak try this turn off your router. reboot your computer. then turn on your router again and see if you can access. i had to do this. worth a try and easy.

---

### Post by makaha2 on 2014-06-08
Strange one this. Same thing stated to happen in Linux Mint 13 Mate I was also testing. Wifi was working very well for weeks, but after a kernel update the wifi stopped. In both it, and in Xubuntu 14.04 I could manually get the wifi working by running "modprobe rt61pci" within Terminal, but had to do this after every boot.

In the interim I've also installed Lubuntu 14.04, and the wifi is working perfectly! Not only that, but my old PC is runung much faster under Lubuntu than any other distro I've tried, so I've settled on it and blown all others away.

Thanks for the assistance :p

---

