---
title: "Help With Internet!!!"
date: 2008-06-11
forum: New to Ubuntu
---

### Post by Roeyfreak10 on 2008-06-11
i just got linux on my computer. im now dual-booting xp and linux 8.04. i have a wireless network adapter, it is a linksys wireless usb network adapter (wusb11 version 2.6). When i go to the top and click the networks button it shows my internet so i click it and it says im connected and it has a 45% connection but when i go to any website it doesnt work. please help i really need to be able to go on the internet.

---

### Post by wolfen69 on 2008-06-11
did you enter the SSID and password?

---

### Post by Roeyfreak10 on 2008-06-11
ya. i put that all in and when i did that it would just keep asking for the wep key and i would keep checking that i had the right one but it didnt work like that. so then i just decided to take of the encryption and once i did that it said i was connected and had 45% signal but internet still didnt work.

---

### Post by prshah on 2008-06-11
> **Roeyfreak10 said:**
> 
click the networks button it shows my internet so i click it and it says im connected and it has a 45% connection 

Open a terminal (Applications-Accessories-Terminal), then give the following commands and post the output here. ```

cat /etc/resolv.conf
iwconfig

```

---

### Post by Roeyfreak10 on 2008-06-11
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

### Post by prshah on 2008-06-11
> **Roeyfreak10 said:**
> ok for cat /etc/resolv.conf 
nameserver 192.168.0.1

and for iwconfig
wlan0 ieee 802.11b essid:wireless internetz nickname:


A little more information```
ping -c 5 192.168.0.1
ifconfig wlan0
```

If you don't have Internet access in Ubuntu right now (Looks like you typed the previous outputs) you can copy and paste the output to a text file, save it in your windows partition and then use that when posting back here.

---

