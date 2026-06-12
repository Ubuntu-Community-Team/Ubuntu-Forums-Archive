---
title: "[SOLVED] ath9k/dhclient connect problems"
date: 2008-10-11
forum: New to Ubuntu
---

### Post by Sava8420 on 2008-10-11
So I have gotten ath9k installed and setup the wireless connection through iwconfig, have even sucessfully obtained connection though only one time.  If I run:
sudo iwlist wlan0 scan
I can see the network in the scan but then turn around and run:
sudo dhclient wlan0
And it won't find any offers.  When running scan though link only shows up at 23% signal strength.  Now that may seem low but I have connected once and connection wasn't lagging speed compared to connecting to link with vista.  Was mainly wondering if there is any certain codes that are helpful to run prior to dhclient that would help it obtain connection?  By the way it's a WEP 128-bit encrypted but I always run:
sudo iwconfig wlan0 
prior to scan and all settings are correct.

---

### Post by Sava8420 on 2008-10-12
Updated to 8.10 and no more problems.

---

