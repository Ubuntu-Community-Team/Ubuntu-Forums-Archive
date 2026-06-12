---
title: "Wireless problems"
date: 2008-07-22
forum: New to Ubuntu
---

### Post by dragonboss on 2008-07-22
I've installed ndiswrapper on the system but it isn't detecting the signal, but in windows it detects the signal (but the signal strenght is very low anyway)

---

### Post by spiderbatdad on 2008-07-22
what wireless card?

---

### Post by northern lights on 2008-07-22
Can you post the output of ```
sudo lshw -C network
```

---

### Post by RequinB4 on 2008-07-22
What is the output of
```

lspci

```

Also, what are the exact steps you used with ndiswrapper?

---

### Post by dragonboss on 2008-07-22
> **spiderbatdad said:**
> what wireless card?
broadcom 4318

---

### Post by northern lights on 2008-07-22
You could try using the old "bcm43xx-fwcutter" driver, yet that is said to be even less likely to work with the 4318 than "ndiswrapper".

You might want to follow [this documentation]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4318_%5BAirForce_One_54g%5D").

---

### Post by Xardes on 2008-07-22
hi!
do you have a "special" hotkey or switch for your wireless lan? do you have a Led, which should turn on if your wireless lan works? does this led shine? 
you have this "special" switch and your led doesn't shine...
in this case, your problem is a quiet common problem with acer laptops. your wirkless card doesn't turn on.
you can see it if you use the command "iwconfig" in ther terminal. (first switch the card on :) )
if you get the message "radio off", your wireless card does not send anything.
perhaps you can find some threads about acerhk.

i fixed it so: (you need root-terminal for the following steps)
1. you have to aktivate acerhk. so we have to open /etc/modules with write permission.
```
gksudo gedit /etc/modules
```
here insert
```
acerhk
```
anywere.

2. and we want that your wireless card turn on/off if you use the switch.
so write into the terminal
```
gksudo gedit /etc/rc.local
```
and here insert between the comment and "exit 0"
```
echo 1 > /proc/driver/acerhk/wirelessed
```

3. restart your stystem

i hope i didn't make a mistake... perhaps you really can find some other threads too.
Good luck :)

EDIT: i found another [thread]("http://wiki.ubuntuusers.de/Acer_Hotkeys?highlight=(acerhk)")... for example (german thread)

---

### Post by Otto-C on 2008-07-22
Give this a try. It worked on my dell w the 4318 card first time.

[http://ubuntuforums.org/showthread.php?t=766560](http://ubuntuforums.org/showthread.php?t=766560)

otto-c

---

### Post by dragonboss on 2008-07-22
> **RequinB4 said:**
> What is the output of
```

lspci

```

Also, what are the exact steps you used with ndiswrapper?
the lspci output is as follows:
jeremy@jeremy's-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
06:01.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
06:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
06:04.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
06:04.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
06:04.2 SD Host controller: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01)
06:04.3 FLASH memory: ENE Technology Inc FLASH memory: ENE Technology Inc: (rev 01)
06:04.4 FLASH memory: ENE Technology Inc SD/MMC Card Reader Controller (rev 01)

and for the steps i cant remember exact;y but i extracted it and ran a command to install it

---

### Post by dragonboss on 2008-07-22
> **northern lights said:**
> Can you post the output of ```
sudo lshw -C network
```

jeremy@jeremy's-laptop:~$ sudo lshw -C network
[sudo] password for jeremy: 
  *-network:0             
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:06:01.0
       logical name: eth0
       version: 02
       serial: 00:16:d4:5e:1b:85
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=64 link=no module=ssb multicast=yes port=twisted pair speed=10MB/s
  *-network:1
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:06:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:16:cf:b5:4e:61
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

---

### Post by northern lights on 2008-07-22
I might repeat myself, but for "Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)", you wanna follow [https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4318_%5BAirForce_One_54g%5D]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4318_%5BAirForce_One_54g%5D")

---

### Post by dragonboss on 2008-07-22
> **northern lights said:**
> You could try using the old "bcm43xx-fwcutter" driver, yet that is said to be even less likely to work with the 4318 than "ndiswrapper".

You might want to follow [this documentation]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4318_%5BAirForce_One_54g%5D").

I've used the bcm43xx-fwcutter driver before and its range is horrible, you have to be in the same room as the wireless router

Thanks, I'll follow the documentation

---

### Post by Xardes on 2008-07-23
sry... made a mistake :)

in the file "/etc/rc.local" you have to insert
```
echo 1 >/proc/driver/acerhk/**wirelessled**
```
i forgot the second l ... sry ;)

---

