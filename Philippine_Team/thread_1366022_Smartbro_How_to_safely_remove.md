---
title: "Smartbro: How to safely remove???"
date: 2009-12-27
forum: Philippine Team
---

### Post by pepe machine on 2009-12-27
hello pinoys!!

whenever i plug my smartbro usb, ubuntu detect two usb devices

1 - a storage device that contains the installer for windows 
2 - and a device named ZTE MMC Storage (i think this one is the modem)

i can safely remove the 1st storage device.
but i cant do it with the ZTE MMC storage, is displays an error saying "device unable to remove and blah blah"

how do you guys safely remove your smartbro usb??

---

### Post by loell on 2009-12-28
removing it should be fine (i mean, just ignore those messages),  you may need to set your system to identify it as a usb modem.

---

### Post by pepe machine on 2009-12-28
> **loell said:**
> removing it should be fine (i mean, just ignore those messages),  you may need to set your system to identify it as a usb modem.

how sir?? kasi kada saksak ko ng smartbro kelangan ko pa type sa terminal ito

sudo /usr/sbin/usb_modeswitch

para lumabas ung ZTE MMC storage sa una kasi eh, smartbro storage lang sya.
tsaka lang saya madedetect na usb modem sya.

pwede bang permanent na sya na madetect as ZTE MMC device??
ok lang po ba un na tanggalin na lang ung usb modem??

---

### Post by loell on 2009-12-28
by using  **udev-extras** to detect the modem during plug in like killer_d76 did,  

[http://ubuntuforums.org/showthread.php?t=1307277]("http://ubuntuforums.org/showthread.php?t=1307277")

---

