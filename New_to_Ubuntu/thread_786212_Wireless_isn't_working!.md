---
title: "Wireless isn't working!"
date: 2008-05-07
forum: New to Ubuntu
---

### Post by Axis on 2008-05-07
Ok I am using version 8.04 (i love the new wallpaper by the way) and on a Compaq Presario F500. You guys have no clue the amount of work I have done to try and get this thing on the wireless networks with no success. I have read every article and tried everything but nothing works. From what I have understood the best way to do it with this version is ndiswrapper. I installed the driver and its working and it even says hardware is present (through the gui for ndiswrapper) but no success whatsoever! I would really appreciate some help on this matter I have loved ubuntu for so long and I would die to get it on this laptop (with my wireless working!!!)

Thanks a lot guys,
Axis

---

### Post by jlandaw on 2008-05-07
It would help to know what kind of card your wireless is...
Run this in a Terminal 
```
sudo lspci
```
and if you get something like this as the network controller:
03:00.0 Network controller [0280]: Broadcom Corporation BCM94311MCG wlan mini-PCI [14e4:4311] (rev 02)

then go [here]("http://ubuntuforums.org/showthread.php?t=769990")

---

### Post by Axis on 2008-05-07
I glanced over your thread (about to go to bed) but it looks to be exactly what I was looking for. Thanks a lot if it works I will be sure to update and let you know. If anyone else has any suggestions please let me know.

---

