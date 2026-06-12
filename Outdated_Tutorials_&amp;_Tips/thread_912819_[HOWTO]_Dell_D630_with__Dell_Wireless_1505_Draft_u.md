---
title: "[HOWTO] Dell D630 with  Dell Wireless 1505 Draft under Ubuntu 8.04 and ndiswrapper"
date: 2008-09-07
forum: Outdated Tutorials &amp; Tips
---

### Post by moresun on 2008-09-07
The wireless card is working perfect on my ubuntu. The only problem I had was that I used the ndiswarpper with a new windows dell driver at first and WPA did not work. After I used an old windows driver everthing worked perfect.

Currently I am using the  
ndiswrapper:
version 1.52
vermagic:       2.6.24-19-generic SMP mod_unload 586 

Windows driver:
Dell Wireless 1505 Draft 802.11n WLAN Mini-Card
Versionsdatum:	18.12.2007
Version:	4.170.25.12, A17
[http://ftp.us.dell.com/network/Dell_multi-device_A17_R174291.exe](http://ftp.us.dell.com/network/Dell_multi-device_A17_R174291.exe)

Installation:
1.) 
sudo apt-get install build-essential
2.)
# if you like you can skip the ndisgtk 
sudo apt-get ndiswrapper-common ndiswrapper-utils-1.9 ndisgtk 
3.)
sudo mdkir /opt/dell
cd /opt/dell
sudo wget [http://ftp.us.dell.com/network/Dell_multi-device_A17_R174291.exe](http://ftp.us.dell.com/network/Dell_multi-device_A17_R174291.exe)
sudo apt-get install unzip
sudo unzip Dell_multi-device_A17_R174291.exe
sudo ndiswrapper -i DRIVER_ROW/bcmwl5.inf
4.)
sudo vim /etc/modules
#add on the end
ndiswrapper
5.) 
#restart
sudo reboot

---

### Post by melenor on 2008-09-23
Does this use the new drivers, also i think there are a few misspellings in there.

---

