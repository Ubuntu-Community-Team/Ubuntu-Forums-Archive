---
title: "Having some trouble"
date: 2008-11-03
forum: New to Ubuntu
---

### Post by TriloByte on 2008-11-03
Hey there.

I am having some troulbe with the wireless internet when I am trying to run Ubuntu. As my drivers are for Windows, that is the problem. Is there a place a can get Ubuntu drivers for it? I have a : D'Link DWL-G132

Any Ideas?

---

### Post by renzokuken on 2008-11-03
you can use the windows drivers through **ndiswrapper** to get your wireless working.

a bit of searching in the forums or on google will show you how to do this........i havent used ndiswrapper for while so i forget

---

### Post by Yellow Pasque on 2008-11-03
The native madwifi drivers don't work with USB devices. You'll have to use the Windows driver with ndiswrapper:
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by Fass on 2008-11-03
[http://ubuntuforums.org/showthread.php?t=584014](http://ubuntuforums.org/showthread.php?t=584014)

I assume you are running Ibex, so you shouldn't need to do the compiling of ndiswrapper. What you will need is an internet connection, so hook your comp up to a wired connection meanwhile. Run the following in a terminal:

```
sudo aptitude install ndiswrapper-common
wget ftp://ftp.dlink.com/Wireless/dwlg132/Driver/dwlg132_drivers_121.zip
unzip dwlg132_drivers_121.zip
cd D-Link\ AirPlus\ Xtreme\ G\ DWL-G132\ Utility\ \(V1.21\ Build\ 60629\ S0008\)/Drivers/
sudo ndiswrapper -i NetA5AGU.inf
sudo depmod -a
sudo modprobe ndiswrapper
```

Follow the rest of the instructions in the link.

---

