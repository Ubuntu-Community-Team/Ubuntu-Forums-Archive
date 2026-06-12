---
title: "New to Linux and fresh 11.10"
date: 2012-03-03
forum: New to Ubuntu
---

### Post by v0x0r on 2012-03-03
Hi,

As the title states, I am new to linux and coming from both Windows and Apple after years of use. I got a hold of a pretty old laptop that I found in a box today, turned it on and it was running slower than snail. It came preloaded with Windows XP and i decided to install the Ubuntu 11.10. 

The laptop is a a Compaq Presario V2555US. I got it installed perfectly and all, but for some reason when I hit enable on the wifi in the OS, it won't turn on the wifi. Is there anything i can do to try and get the wifi to work on it? Oh and it came with a built in wifi just in case anyone would like to know.

Any help would be appreciated to get this old laptop up and running! 

Thanks!

---

### Post by TeoBigusGeekus on 2012-03-04
Post us the output of
```
lshw -C network
```
to see if a wifi card is recognized by your system.

---

### Post by Palmstroem on 2012-03-04
Hi,

first thing I would do is to open a terminal, type the command "lspci" to see if the wifi is recognized by Linux. If not it can sometimes help to change BIOS settings so that the operating system may access the hardware.

---

