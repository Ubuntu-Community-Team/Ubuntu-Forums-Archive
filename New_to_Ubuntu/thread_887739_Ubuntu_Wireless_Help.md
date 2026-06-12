---
title: "Ubuntu Wireless Help"
date: 2008-08-12
forum: New to Ubuntu
---

### Post by farrinux on 2008-08-12
Very new to Ubuntu and Linux for that matter.  I absolutely know nothing.  I have managed to install ubuntu 8.04 LTS with a dual boot of Win 98 SE. I've also managed to get my sound card working and the computer to shut off at shutdown.  :confused: But I am totally lost when it comes to setting up my Linksys WMP54G and getting it working. Not sure if I need to use the NDISWRAPPER and my cards drivers or bcm43xx-fwcutter or just what to use. I tried using 8.04 LTS troubleshooting guide.  But I hit a brick wall on the very first step, "Check for device recognition
Open Device Manager (System &#8594; Preferences &#8594; Hardware Information)." I do not have a choice for hardware info in my system/preference menu list.  Can anyone walk me through the steps to set this up? It's a linksys wmp54g with a broadcom 4306 chip I believe.  Thanks in advance.

Kevin

---

### Post by Ryadt on 2008-08-12
See if your wireless card is in System > Administration > Hardware Drivers. Enable it if it is.

---

### Post by farrinux on 2008-08-12
It's not listed there either.  I know if I run the "lspci -l" command it is listed.

---

### Post by wolfen69 on 2008-08-12
install the bcm43xx-fwcutter and see what happens. otherwise, you will have to use ndiswrapper.

---

### Post by farrinux on 2008-08-12
Just so I know, I can install bcm43xx-fwcutter from the live cd using one of the package managers, correct?

---

