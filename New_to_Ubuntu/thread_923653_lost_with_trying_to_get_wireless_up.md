---
title: "lost with trying to get wireless up"
date: 2008-09-18
forum: New to Ubuntu
---

### Post by iwannalearn on 2008-09-18
Hi all, need some help please. Acer 3003

not long ago i went wireless got my m$ up ok in no time, then had trouble getting my laptop which has ubuntu on it, i got so pissed that i just put m$ on it and was ok, but then thought wtf, pulled out my ubuntu cd and put it back on.

system>preferences>hardware info
BCM4318 [Airforce One 54g] 802.11g Wireless LAN Controller
Unknow Device
WLAN Interface
Networking Wireless Control Interface

Also when i go in Network Settings, i edit the wireless connection it is ticked and i have checked it a million times the settings

System>admin>Hardware divers

Device driver
Broadcom B43 wireless driver  enabled ticked  on satus green tick in use

When i put the mouse over i get the following

While this driver itself is free software, it relies on proprietary firmware which cannot be legally shipped with the operating system. Your hardware will not work without the firmware.

Thanks

---

### Post by Tatty on 2008-09-18
So according to the Hardware Drivers manager, the driver should be installed.  Lets test out whether it can see any networks... can you post the results of

```
sudo iwlist scan
```

---

### Post by iwannalearn on 2008-09-18
> **Tatty said:**
> So according to the Hardware Drivers manager, the driver should be installed.  Lets test out whether it can see any networks... can you post the results of

```
sudo iwlist scan
```

lo        Interface doesn't support scanning

eth1      Interface doesn't support scanning

wmaster0  Interface doesn't support scanning

eth0      No scan results

does this help you mate?

---

### Post by Tatty on 2008-09-18
Did you definately preface the command with "sudo"?

Also, should it be detecting a network where you are? I assume it should, but just checking.

can you also post the results of:
```

lspci
lsusb
```

---

### Post by Crafty Kisses on 2008-09-18
First you need to install this package:
```
sudo apt-get install ndisgtk
```
After you've done that we need to do is make it so that the pre-installed driver, bcm43xx, doesn't attach to the hardware on bootup. The way we do this is by blacklisting it. Run the following in Terminal:
```
sudo gedit /etc/modprobe.d/blacklist
```
You can get the driver right [**here**]("http://dlsvr03.asus.com/pub/ASUS/wireless/WL-100g-03/Driverv3100640.zip") for that card. Once you've downloaded that file, run this command:
```
sudo ndiswrapper -i bcmwl5.inf
```
Once you've done that, try installing the .inf file using ndisgtk, and lets see if that Wireless card springs to life. :)

---

### Post by iwannalearn on 2008-09-18
> **Tatty said:**
> Did you definately preface the command with "sudo"?

Also, should it be detecting a network where you are? I assume it should, but just checking.

can you also post the results of:
```

lspci
lsusb
```

xxxxxxx@xxxxxxx-laptop:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

eth0      No scan results


xxxxxx@xxxxxxx-laptop:~$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 760/M760 Host (rev 03)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
00:06.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
00:0b.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

xxxxx@xxxxx-laptop:~$ lsusb
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

Yes i have the laptop just a couple of feet away from router.

i have to leave now will check and report back tomorrow

Many thanks for your time

---

### Post by Tatty on 2008-09-18
You should probably follow the guide in Codename's post above.  I dont have any experience with ndiswrapper, and it sounds like he knows it well :)

---

### Post by iwannalearn on 2008-09-19
@Tatty & Codename

At work at the moment will give it a go as soon as i get home and let you guys know

Thanks for now

---

### Post by iwannalearn on 2008-09-19
> **Codename said:**
> First you need to install this package:
```
sudo apt-get install ndisgtk
```
After you've done that we need to do is make it so that the pre-installed driver, bcm43xx, doesn't attach to the hardware on bootup. The way we do this is by blacklisting it. Run the following in Terminal:
```
sudo gedit /etc/modprobe.d/blacklist
```
You can get the driver right [**here**]("http://dlsvr03.asus.com/pub/ASUS/wireless/WL-100g-03/Driverv3100640.zip") for that card. Once you've downloaded that file, run this command:
```
sudo ndiswrapper -i bcmwl5.inf
```
Once you've done that, try installing the .inf file using ndisgtk, and lets see if that Wireless card springs to life. :)

Codename mate i need some help please.

i downloaded the file and have extracted it to my working directory. when i do 
sudo ndiswrapper -i bcmwl5.inf

i get couldn't open bcmw15.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 219

i have looking and it is there

how do i install the drivers?

please help

---

### Post by iwannalearn on 2008-09-19
OK guys just go it up for the time being till i f**k it up:lolflag:

Thanks for the help

Cheers

---

