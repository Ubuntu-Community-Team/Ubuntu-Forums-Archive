---
title: "Help!!!!low resolution after reboot and ubunto refused to recognise my 8800gt card"
date: 2008-07-28
forum: New to Ubuntu
---

### Post by SandyM on 2008-07-28
HI!! I am New to Ubuntu andfacing a proplem from the time i checked proposed repositories in synaptic and thereby enabling Pre-released Updates (Hardy Proposed). This installed a newer Kernel 2.6.24.20 in my grub menu.Before this I was using 2.6.24.19 Kernel which was absolutely OK but due to some other problems I had to reinstall ubuntu (with formatting my ubuntu drive)
With new installation I decided to go for proposed updates and I  downloaded certain other packages and files as per my understanding of them through the details provided by synaptic
After installing all the updates I installed the latest Nvidia drivers (I am using 8800gt) which I downloaded from Nvidia website.Then I restarted my PC but when I entered ubuntu I saw my PC goinginti low resolution state (800*600 I presume as against my resolution of 1440*900) .I tried every possibility includig installing older Nvidia drivers proposed by ubuntu hardware driver manager but to no help.
PLEASE ADVISE WHERE THE TRUE PROBLEM LIES . IS IT WITH MY NEW NVIDIA DRIVERS or THE PROPOSED KERNEL 2.6.24.20 or WITH ANY OTHER PACKAGES WHICH I DON'T REALLY REMEMBER. 
The new Nvidia driver were perfectly fine before  I formatted my drive and din't installed all those packages of ubuntu and other optional repositories (you can't realy diffentiate between the two after enabling all the repositories):(

---

### Post by Neo0351 on 2008-07-28
you should you envy to install your drivers for your card, evny supports 8000 series cards
```
sudo apt-get install envyng-gtk 
```

---

