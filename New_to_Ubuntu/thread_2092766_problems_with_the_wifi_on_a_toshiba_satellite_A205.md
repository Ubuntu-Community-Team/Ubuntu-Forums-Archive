---
title: "problems with the wifi on a toshiba satellite A205 12.10 install"
date: 2012-12-08
forum: New to Ubuntu
---

### Post by Seth12 on 2012-12-08
So I just did a fresh install of 12.10 on my laptop and for some reason the wifi isnt working I am thinking it is a driver problem but really I have no idea im still a noob when it comes to Ubuntu.  So I read a few other posts about this kinda thing and to check to see what card I had I entered this into the terminal

lspci -nn | grep 0280


and what it brought up was this

03:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02)

now according to the other posts ubuntu comes with drivers for a broadcom card and according to this it doesn't have a broadcom card but and intell 3945ABG anyone know what I should do? any help would be much appreciated thanks 

Seth

---

### Post by LADmaticCA on 2012-12-08
Have you tried looking in "Additional Drivers?" Press the Windows button and type "additional" and see if it finds it.

If not, press the windows button and type "software" click on Software Sources, inside there should be a "Additional drivers" tab. Hopefully, there will be a driver for your hardware.

---

### Post by Manodedios on 2012-12-08
this may help


[http://www.linlap.com/toshiba_satellite_a205](http://www.linlap.com/toshiba_satellite_a205)

---

### Post by Seth12 on 2012-12-10
I found the Additional Drivers but it doesn't have any drivers in it maybe I should just try re installing?

---

