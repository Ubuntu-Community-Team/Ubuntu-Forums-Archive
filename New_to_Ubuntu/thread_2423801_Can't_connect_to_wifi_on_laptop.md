---
title: "Can't connect to wifi on laptop"
date: 2019-07-29
forum: New to Ubuntu
---

### Post by retsek2 on 2019-07-29
I'm using Ubuntu MATE version 18.04.2. And I cannot connect to the wifi. I have done sudo apt-get update, and I have installed proprietary drivers. I am on a HP 225 laptop. I have tried manually entering the SSID of the router and typing in the password to no avail. Are there wifi drivers that I need to install? This laptop connects the wifi fine on Windows 10 and connects to the wifi when plugged in with the ethernet cable.

---

### Post by oldrocker99 on 2019-07-30
The wireless chip, which is one of these,```
Intel Dual Band Wireless-AC 3165 802.11 ac (1x1) WiFi + Bluetooth 4.2 Combo
Realtek 802.11b/g/n (1x1) Wi-Fi + Bluetooth 4.0 Combo
Broadcom 802.11 b/g/n (1x1) Wi-Fi + Bluetooth 4.0 Combo
Realtek 802.11b/g/n (1x1) Wi-Fi
```should already have all drivers in the kernel.

Do you have a wireless icon in the upper left? If not, which has happened to me, right-click the upper bar, and add "Indicator Applet Complete." That will re-add the wireless icon, and then you'll be all set.

Good luck!

---

