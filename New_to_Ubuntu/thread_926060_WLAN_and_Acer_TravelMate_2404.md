---
title: "WLAN and Acer TravelMate 2404"
date: 2008-09-21
forum: New to Ubuntu
---

### Post by fi_sammy on 2008-09-21
I am trying to enable WLAN in my Acer TravelMate. I have several issues:
- Pressing the "WLAN" button in front panel of computer does not help, maybe the button works only with Windows?
- I do not know what drivers and/or SW to install to get WLAN working
- When I try to open System - Preferences - Hardware Information, the "Device Manager" starts for a second and the window immediatelly disappears. Therefore I can not check what WLAN chip my laptop has

How to proceed? What is needed (in general) to get WLAN working? How can I fix my "Device Manager"?

---

### Post by willca on 2008-09-23
can you post this please...

$ lspci | grep -i ethernet

If your wireless card happen to be Broadcom...then just try this.

$ sudo apt-get install b43-fwcutter

follow the prompts...

---

### Post by fi_sammy on 2008-09-24
OK, done that. Result was 
$ lspci | grep -i ethernet
05:01.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)

Then I run sudo install b43-fwcutter .. and nothing happened. What could I do next?

---

