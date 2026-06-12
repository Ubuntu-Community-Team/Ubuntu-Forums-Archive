---
title: "Need Help With Internet !!!\"
date: 2008-06-11
forum: New to Ubuntu
---

### Post by Roeyfreak10 on 2008-06-11
just got linux on my computer. im now dual-booting xp and linux 8.04. i have a wireless network adapter, it is a linksys wireless usb network adapter (wusb11 version 2.6). When i go to the top and click the networks button it shows my internet so i click it and it says im connected and it has a 45% connection but when i go to any website it doesnt work. please help i really need to be able to go on the internet.


ok for cat /etc/resolv.conf 
i get...

search chn.comcast.net
nameserver 192.168.0.1

and for iwconfig
iget...

lo no wireless extension
eth0 no wireless extension
wlan0 ieee 802.11b essid:wireless internetz nickname:
mode:managed frquency:2.437GHz access point:00:0F:66:65:E0:13
bit rate:11/mbs tx power=15 dbm
retry limit=8
rts thr=1536 b
fragment thr=1536 b 
power managment = off
link quality = 30/100
signal level = 30/100

---

### Post by gr4nf on 2008-06-11
Do you have another computer running ubuntu, or can you get a package online any other way?

if so, try getting "dhcpcd" online and putting it on your computer. Then run the command "dhcpcd". Remember to get the .deb package.

---

### Post by Roeyfreak10 on 2008-06-11
i can get via flash drive but what do i do once i have it

?

---

### Post by natirips on 2008-06-11
Double-click it.

---

