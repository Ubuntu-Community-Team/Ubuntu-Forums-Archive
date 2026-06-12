---
title: "Could not get Epson L366 scanner to work in Ubuntu 14.04 x64"
date: 2018-02-16
forum: New to Ubuntu
---

### Post by ubunstar10 on 2018-02-16
Hello everyone, I have a problem with the Epson L366 scanner. I had Linux Mint 18.3 before and I installed the driver without any problems.
So, I installed the All-in-One scanner driver from Epson off.site with GDebi, but Image Scan doesn't detect it, nor the XSane does. I reinstalled the driver 3-4 times, but it didn't help too.
lsusb shows the following info:
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 04b8:08d2 Seiko Epson Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 004: ID 0bda:8179 Realtek Semiconductor Corp. RTL8188EUS 802.11n Wireless Network Adapter
Bus 004 Device 003: ID 0930:6544 Toshiba Corp. TransMemory-Mini / Kingston DataTraveler 2.0 Stick (2GB)
Bus 004 Device 002: ID 058f:9254 Alcor Micro Corp. Hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 0000:0538  
Bus 003 Device 002: ID 1a2c:2d43 China Resource Semico Co., Ltd 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

The printer itself works fine, the scanner is the problem.

In case you need it, my system specs are:
ASUS M4A77TD
AMD Athlon II X2 250
Palit GeForce GT 440 2 GB
4 GB DDR3 RAM
Windows 8.1 x64, Windows Vista SP2 x64, Ubuntu 14.04 x64 installed.

---

### Post by mörgæs on 2018-02-16
Hi, welcome to the fora.

Release 18.3 is the newest in the Mint family. If you want to try Ubuntu I suggest a fresh install of the newest one, that is 17.10.1.

---

### Post by ubunstar10 on 2018-02-24
I really don't like Ubuntu versions newer than 14.04. Also I don't have EFI bios. Thanks anyway.

---

### Post by Geoffrey_Arndt on 2018-02-24
Hmm, . . . new versions of the buntu family do not require EFI.    Legacy MBR is fine.   With the hardware you have, I think Xubuntu 16.04.3 will run very fast and you'll have a better chance the scanner is auto detected. 

Simple Scan should work.    Unlike standard Unity, Xubuntu's XFCE is more flexible regarding customizations (you may just love it . . )

---

### Post by mörgæs on 2018-02-25
Yes, the other buntus (K/X/Lubuntu and others) are good options if look and feel is important. You can see lots of demos on Youtube.

17.10.1 would be the safe bet but 16.04.3 might work, too.

---

