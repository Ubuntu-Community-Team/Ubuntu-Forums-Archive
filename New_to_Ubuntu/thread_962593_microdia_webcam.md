---
title: "microdia webcam"
date: 2008-10-29
forum: New to Ubuntu
---

### Post by djallalnamri on 2008-10-29
*hello
*can anyone help with installing this webcam:
  Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 004: ID 0c45:627b Microdia 
Bus 002 Device 003: ID 03eb:0902 Atmel Corp. 
Bus 002 Device 002: ID 04fc:0005 Sunplus Technology Co., Ltd 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
*thanks in advance
*p.s.: i have turned to asking questions just because everything i have tried did not work:confused:

---

### Post by rashaan salaam on 2008-12-05
I'm having a similar problem. i've tried a number of fixes from various threads but so far only have gotten ekiga to recognize webcam and the picture is very fuzzy. in skype i get this weird green screen.  cheese gives me nothing and camorama gives me an error message that it cant capture image.  heres the lsusb result

patrick@patrick-laptop:~$ lsusb
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 0c45:6128 Microdia 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by rashaan salaam on 2008-12-05
maybe i should mention that i'm running ibex 8.10.  i tried downloading a microdia driver but as of yet i cant figure out how to get it running. anyway, i'm not sure that that's the issue anyway since the camera works in ekiga; its just extremely blurry.  any ideas or a really basic step by step howto for getting a microdia driver running.

---

### Post by NDUFB11 on 2009-01-03
Hi to everybody ! I'm a new entry with ....old commons problem 
Could someone help me? My webcam doesen't function and I have just intalled several package or progranms uselessly
Thanks and happy new year : )

patrizio@ubuntu:~$ lsusb
Bus 003 Device 002: ID 0425:f102 Motorola Semiconductors HK, Ltd 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 001 Device 004: ID 0c45:613c Microdia PC Camera (SN9C120)
Bus 001 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

I'm not an PC expert ,but with this action "lsusb" I had this answers
ehmm...finally I'm sorry for my english

---

