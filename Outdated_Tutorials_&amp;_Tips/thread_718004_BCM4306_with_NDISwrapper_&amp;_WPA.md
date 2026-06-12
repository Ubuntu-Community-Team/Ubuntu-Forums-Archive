---
title: "BCM4306 with NDISwrapper &amp; WPA"
date: 2008-03-07
forum: Outdated Tutorials &amp; Tips
---

### Post by DapperMe17 on 2008-03-07
[B]This a simple solution to enabling your BCM4306, with NDISwrapper, Windows driver & WPA encryption in Gutsy Gibbon 7.10.
[/B]
*Prerequisites in router settings...*
WPA1 (TKIP)
Hidden ssid 

This worked for me, so I hope that it helps in your situation. 

Many thanks to ubunturules, fireant & weiman01, as this tutorial includes valuable information from their tutorials, in order to get my connection active. I've just combined their processes into a simple numerical order, but which leaves out much of the thorough explanation. All credit goes to the above authors, who's research enabled me to write up a "quick guide". See their tutorials at...

[http://ubuntuforums.org/showthread.php?t=201902&highlight=bcm4306+wpa&page=75](http://ubuntuforums.org/showthread.php?t=201902&highlight=bcm4306+wpa&page=75)  
[http://ubuntuforums.org/showthread.php?t=201902&highlight=bcm4306+wpa&page=75](http://ubuntuforums.org/showthread.php?t=201902&highlight=bcm4306+wpa&page=75)


Ok, by following this order, you should get your connection up & running.


*1) Download the 32 or 64 bit Windows drivers*

*2) lspci | grep Broadcom\ Corporation*

*3) sudo rmmod bcm43xx*

*4) echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist*

*5) Place Ubuntu Gutsy Gibbon 7.10 disk in your DVD/CD tray*

*6) sudo aptitude install build-essential*

*7) uname -r*

*8) sudo ln -s /usr/src/linux-2.6.22-14-generic /lib/modules/2.6.22-14-generic/build*

*9) sudo apt-get install ndiswrapper-utils-1.9*

*10) sudo ndiswrapper -i /folder where driver is/bcmwl5.inf    		*....for 32-bit drivers
*    sudo ndiswrapper -i /folder where driver is/bcmwl564.inf  		*....for 64-bit drivers

*11) ndiswrapper -l*

*12) sudo ndiswrapper -m*

*13) sudo modprobe ndiswrapper*

*14) echo 'ndiswrapper' | sudo tee -a /etc/modules*

*15) sudo gedit /etc/udev/rules.d/70-persistent-net.rules*

(Replace the "eth1" entry for (bcm43xx) with "wlan0" as the following example shows...

# PCI device 0x14e4:0x4306 (bcm43xx)
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:04:c2:65:3b:b4", NAME="wlan0")

*16)  echo 'ENABLED=0' | sudo tee -a /etc/default/wpasupplicant*

*17)  sudo /etc/init.d/dbus restart*

*18) wpa_passphrase "your_essid" "your_ascii_key"   *
(....replace your_essid & your_ascii_key with your respective info &  copy the outcome scrambled line after "psk=")

*19) sudo gedit /etc/network/interfaces             *
(....keep any auto lines & replace all wlan0 lines with the following & replace <your_essid> with your ssid name & replace <your_hex_key> with the scrambled code you previously copied...)

auto wlan0
iface wlan0 inet dhcp
wpa-driver wext
wpa-ssid <your_essid>
wpa-ap-scan 2
wpa-proto WPA
wpa-pairwise TKIP
wpa-group TKIP
wpa-key-mgmt WPA-PSK
wpa-psk <your_hex_key> 

*20)sudo /etc/init.d/networking restart*


This "should" get you to an active internet connection with 54MB/s, WPA1 encryption & Hidden SSID.

Please feel free to add additional comments as needed.

---

