---
title: "I'm stumped with Wifi adapter install"
date: 2022-12-30
forum: New to Ubuntu
---

### Post by ysottot on 2022-12-30
Hi all. I recently decided to go Ubuntu from Windows, on a older machine. It installs fine but the wifi adapter won't install.
I'm not Linux savvy at all just an old MCSE trying to learn new stuff. I'm just not getting it.
Tried to follow install sites but the language and process is foreign to me and I just keep ending up at the same web pages
without getting anything downloaded. Wifi adapter is USB Netgear AC1200 model A6150. Ubuntu is 5.15.0-56-generic. 22.04
I would have thought the OS would see the adapter. The Ethernet hard wire works. Just can't get or understand how to get the wifi to work.   
The machine see the adapter on Bus 002 Device 003.
 Any help would be appreciated. Thanks in advance.

tsuser@Music01:~$ lsusb
[COLOR=#ff0000]Bus 002 Device 003: ID 0846:9055 NetGear, Inc. A6150[/COLOR]
Bus 002 Device 002: ID 13fd:3940 Initio Corporation external DVD burner ECD819-SU3
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 003: ID 0461:4d20 Primax Electronics, Ltd HP Optical Mouse
Bus 005 Device 002: ID 04d9:1203 Holtek Semiconductor, Inc. Keyboard
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by grahammechanical on 2023-01-01
Please run this command in a terminal:

```
rfkill list
```

On my system I see this:

> graham@UbuntuDev:~$ rfkill list
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


If your Wireless LAN is Soft Blocked then you do not have a driver installed. If the wireless LAN is Hard Blocked then the adapter is turned off.

Have you checked the UEFI/BIOS settings to confirm that the WiFi adapter is enabled and not disabled? In the past if we were dual booting with Microsoft Windows and we turned off WiFi in Windows then it would remain off when we booted Ubuntu.

Some things for you to check to help us identify how we can help you.

Regards

---

### Post by VMC on 2023-01-01
Is that Netgear a "dongle"? If so read through this info:
[https://www.linuxquestions.org/questions/showthread.php?p=6358773#post6358773](https://www.linuxquestions.org/questions/showthread.php?p=6358773#post6358773)

---

### Post by electricmax on 2023-01-08
Hello, I read your tread and found similar issue like me. I was also having the same issue I failed to connect wifi adapter to ubuntu OS, finally I connected my desktop to internet via wired connection. I think you should install necessary drivers from Disk or official website(if available) and try to connect the wifi adapter again. I hope you find this helpful, have a good sunday (Greetings from India)

---

