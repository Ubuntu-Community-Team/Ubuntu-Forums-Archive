---
title: "Ubuntu 12.04  How do you build wifi driver for Xmedia NE-WN3500D for linux?"
date: 2013-06-10
forum: New to Ubuntu
---

### Post by primitive1 on 2013-06-10
I have an install of 12.04 on a single hard drive to itself and i need to build the driver to let ubuntu see my wifi connection.  I am very much a novice to linux and need help as i was trying to learn linux to fix this problem as well as make the computer available for the give computers to the needy ubuntu initiative.

I am trying to make it work on a wifi PCI card on my HP Pavillion 533W that has 2Ghz processor speed and 1G RAM installed. i don't even know what the file extension is for linux driver for wifi if someone can explain that as well.  Thank you much and have a great day!

---

### Post by squakie on 2013-06-10
Let's start with something easy, and workout from there. 

Open a terminal window (cntrl-alt-f1) and type:

Lspci > dwetest.txt  - BT,that should be a lower case "L" at the beginning (can't seem to get it to lower case here)

This will list all the devices that Ubuntu sees on the PCI bus and output it to the file dwetest.txt.

Now reply here attaching (via the paperclip icon) ~/dwetest.txt

---

