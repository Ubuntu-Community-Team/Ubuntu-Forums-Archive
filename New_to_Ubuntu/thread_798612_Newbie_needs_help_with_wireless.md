---
title: "Newbie needs help with wireless"
date: 2008-05-18
forum: New to Ubuntu
---

### Post by huntis619 on 2008-05-18
Hi I have a hpzv5410us laptop. I had ubuntu 7.10 which worked very well and I liked it as an alternative to windows or spending money on a new mac. Then I updated to ubuntu 8.04 and now I'm having problems with my wireless internet access. The drivers are updated and it says there in use but I still can't get on the internet with a wireless connection. Please can anyone help me.

---

### Post by shifty_powers on 2008-05-18
try downloading a live-cd and booting from it, to see if something went wrong with the upgrade, and a fresh install might help.

---

### Post by FuturePilot on 2008-05-18
What wireless card do you have? 
Post the output of
```
lspci
```

---

### Post by drs305 on 2008-05-18
Do you know the type of wireless card?
You can check with:
```
lshw
```
For an html output:
```
sudo lshw -html > ~/Desktop/hardware.html
```

If it's a broadcom card, here's the possible solution:
[http://ubuntuforums.org/showthread.php?t=766560](http://ubuntuforums.org/showthread.php?t=766560)

---

### Post by huntis619 on 2008-05-18
lspci
00:00.0 Host bridge: nVidia Corporation nForce3 Host Bridge (rev a4)
00:01.0 ISA bridge: nVidia Corporation nForce3 LPC Bridge (rev a6)
00:01.1 SMBus: nVidia Corporation nForce3 SMBus (rev a4)
00:02.0 USB Controller: nVidia Corporation nForce3 USB 1.1 (rev a5)
00:02.1 USB Controller: nVidia Corporation nForce3 USB 1.1 (rev a5)
00:02.2 USB Controller: nVidia Corporation nForce3 USB 2.0 (rev a2)
00:06.0 Multimedia audio controller: nVidia Corporation nForce3 Audio (rev a2)
00:06.1 Modem: nVidia Corporation nForce3 Audio (rev a2)
00:08.0 IDE interface: nVidia Corporation nForce3 IDE (rev a5)
00:0a.0 PCI bridge: nVidia Corporation nForce3 PCI Bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation nForce3 AGP Bridge (rev a4)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 440 Go 64M] (rev a3)
02:00.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
02:04.0 CardBus bridge: Texas Instruments PCI1620 PC Card Controller (rev 01)
02:04.1 CardBus bridge: Texas Instruments PCI1620 PC Card Controller (rev 01)
02:04.2 System peripheral: Texas Instruments PCI1620 Firmware Loading Function (rev 01)

---

### Post by FuturePilot on 2008-05-18
Possibly check the link in the post above yours.
```
02:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
```

---

### Post by shifty_powers on 2008-05-18
have a look

[http://davidwatson.org/2007/05/broadcom-4306-on-feisty-fawn.html](http://davidwatson.org/2007/05/broadcom-4306-on-feisty-fawn.html)

and broadcom chipsets are ntoriously a pain in the *** with ubuntu ;)

---

### Post by huntis619 on 2008-05-18
steven@steven-laptop:~$ echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
sudo: unable to resolve host steven-laptop
steven@steven-laptop:~$ sudo apt-get install ndiswrapper-utils-1.9
sudo: unable to resolve host steven-laptop
steven@steven-laptop:~$ mkdir ~/bcm43xx; cd ~/bcm43xxwget [http://myspamb8.googlepages.com/WPC54Gv2_40826-pruned.zip](http://myspamb8.googlepages.com/WPC54Gv2_40826-pruned.zip)
mkdir: cannot create directory `/home/steven/bcm43xx': File exists
bash: cd: /home/steven/bcm43xxwget: No such file or directory
steven@steven-laptop:~$ unzip WPC54Gv2_40826-pruned.zip
unzip:  cannot find or open WPC54Gv2_40826-pruned.zip, WPC54Gv2_40826-pruned.zip.zip or WPC54Gv2_40826-pruned.zip.ZIP.
steven@steven-laptop:~$ sudo ndiswrapper -i bcmwl5.inf
sudo: unable to resolve host steven-laptop
steven@steven-laptop:~$ ndiswrapper -l
bcmwl5 : driver installed
	device (14E4:4320) present (alternate driver: bcm43xx)
steven@steven-laptop:~$ sudo depmod -a
sudo: unable to resolve host steven-laptop
steven@steven-laptop:~$ sudo modprobe ndiswrapper
sudo: unable to resolve host steven-laptop
steven@steven-laptop:~$ sudo cp /etc/network/interfaces /etc/network/interfaces.orig
sudo: unable to resolve host steven-laptop
steven@steven-laptop:~$ echo -e 'auto lo\niface lo inet loopback\n' | sudo tee /etc/network/interfaces
sudo: unable to resolve host steven-laptop
steven@steven-laptop:~$ sudo ndiswrapper -m
sudo: unable to resolve host steven-laptop
steven@steven-laptop:~$ echo 'ndiswrapper' | sudo tee -a /etc/modules
sudo: unable to resolve host steven-laptop
steven@steven-laptop:~$ echo 'ENABLED=0' | sudo tee -a /etc/default/wpasupplicant
sudo: unable to resolve host steven-laptop
steven@steven-laptop:~$ sudo aptitude remove b43-fwcuttersudo gedit /etc/init.d/wirelessfix.sh#!/bin/bash
bash: !/bin/bash: event not found
steven@steven-laptop:~$ modprobe -r b44
steven@steven-laptop:~$ modprobe -r b43
FATAL: Error removing b43 (/lib/modules/2.6.24-16-generic/kernel/drivers/net/wireless/b43/b43.ko): Operation not permitted
steven@steven-laptop:~$ modprobe -r b43legacy
steven@steven-laptop:~$ modprobe -r ssb
FATAL: Module ssb is in use.
steven@steven-laptop:~$ modprobe -r ndiswrapper
FATAL: Error removing ndiswrapper (/lib/modules/2.6.24-16-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko): Operation not permitted
steven@steven-laptop:~$ modprobe ndiswrapper
steven@steven-laptop:~$ modprobe b44
FATAL: Error inserting b44 (/lib/modules/2.6.24-16-generic/kernel/drivers/net/b44.ko): Operation not permitted
steven@steven-laptop:~$ cd /etc/init.d/ && sudo chmod 755 wirelessfix.sh
sudo: unable to resolve host steven-laptop
steven@steven-laptop:/etc/init.d$ sudo update-rc.d wirelessfix.sh defaults

---

### Post by drs305 on 2008-05-18
Since it can't resolve the host steven-laptop, see if you have an /etc/hosts file:
```
find /etc/hosts
```

If you don't have one, create it:
```
gksudo gedit /etc/hosts
```

Add these lines:

```

127.0.0.1 localhost
127.0.1.1 steven-laptop

```

Save the file. You may have to reboot.

If you have an /etc/hosts, check to see if these two are the same:
```

cat /etc/hosts
cat /etc/hostname

```

You should see steven-laptop in both.

---

