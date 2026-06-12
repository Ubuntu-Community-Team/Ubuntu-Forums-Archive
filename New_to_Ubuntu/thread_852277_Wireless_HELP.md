---
title: "Wireless HELP"
date: 2008-07-07
forum: New to Ubuntu
---

### Post by utfan2012 on 2008-07-07
okay i've had my Laptop for awhile now and I can't get the wireless working i've searched like every forum but can't seem to find what the problem is...
I have a Compaq Presario with a broadcom wireless card (i know some broadcom cards aren't supported) but i have gotten online ONCE and have never been able to get on wireless again.

Thank you for helping

---

### Post by stats on 2008-07-07
have a look at [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by utfan2012 on 2008-07-07
* Wi...er
    * Ndiswrapper

This page does not exist yet. You can create a new empty page, or use one of the page templates.

Thats what i got when i went to it

---

### Post by Car60n on 2008-07-07
try this--
 1> install build-essential
```
sudo apt-get install build-essential
``` 
 2> install b43-fwcutter
```
sudo apt-get install b43-fwcutter
```
 3> point to the firmware directory
```
export FIRMWARE_INSTALL_DIR=/lib/firmware
```
 4>download and install firmware
```
wget http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2
tar xjf broadcom-wl-4.80.53.0.tar.bz2
cd broadcom-wl-4.80.53.0/kmod
../../b43-fwcutter-011/b43-fwcutter -w “$FIRMWARE_INSTALL_DIR” wl_ap
```
5>reboot
```
sudo shutdown -r 00
```

hope it works...

---

