---
title: "Please help me with my atheros wifi card!"
date: 2008-09-12
forum: New to Ubuntu
---

### Post by holliday74 on 2008-09-12
To start off i have Ubuntu 7.10 64bit on an amd machine. My wifi card is Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter. I get this in the terminal when i type lspci. I also have two restricted drivers for this card and it still dosen't work. And if i type iwconfig i get lo no wireless extensions eth0 no wireless extensions. I have tryed the ndiswrap approach but it didnt work. but I'm not to sure if i done it right so please help me i need wifi for this comp. thanks alot. 
Travis Holliday

---

### Post by LowSky on 2008-09-12
install ndiswrapper and then use the Windows drivers, should work

sudo apt-get install ndiswrapper

---

