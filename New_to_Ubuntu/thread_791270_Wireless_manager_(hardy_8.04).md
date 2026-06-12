---
title: "Wireless manager (hardy 8.04)"
date: 2008-05-12
forum: New to Ubuntu
---

### Post by Dissident85 on 2008-05-12
Hi all, i have just installed ubuntu 8.04 on my dell m1330 laptop and i cant find the wireless manager? do i have to install one? or has it moved?

cheers

---

### Post by wolfen69 on 2008-05-12
if your wifi card is installed correctly, just single click the network icon on the taskbar. available networks should show up. you can also go to system>admin>network to configure. (remember to unlock)

---

### Post by subzero316 on 2008-05-12
> **Dissident85 said:**
> Hi all, i have just installed ubuntu 8.04 on my dell m1330 laptop and i cant find the wireless manager? do i have to install one? or has it moved?

cheers

i guess you are saying network manager if so


Frist try running the command
```
network-manager
```
for it from termial if It will pop up if installed if not it will ask you to install

Incase it asks you to install then i suggest you install wicd i find it better

```
sudo apt-get install wicd
```

---

### Post by Dissident85 on 2008-05-12
> **subzero316 said:**
> i guess you are saying network manager if so


Frist try running the command
```
network-manager
```
for it from termial if It will pop up if installed if not it will ask you to install

Incase it asks you to install then i suggest you install wicd i find it better

```
sudo apt-get install wicd
```

when i type in "network-manager" it get "bash: network-manager: command not found"

---

### Post by Dissident85 on 2008-05-12
> **wolfen69 said:**
> if your wifi card is installed correctly, just single click the network icon on the taskbar. available networks should show up. you can also go to system>admin>network to configure. (remember to unlock)

when i click on the network icon, i just get "wired network" & "connect to a 802.1x protected wired network" & "manual configuration"

---

### Post by wolfen69 on 2008-05-12
.

---

### Post by wolfen69 on 2008-05-12
is the proper driver installed?

---

### Post by Dissident85 on 2008-05-12
> **wolfen69 said:**
> ```
**sudo** network-manager
```

same thing 

```
sudo: network-manager: command not found
```

---

### Post by Dissident85 on 2008-05-12
> **wolfen69 said:**
> is the proper driver installed?

im not sure, i think so, how do i check? 

i know when i ran "Hardware Testing" it detected it and said it was ok...

---

### Post by subzero316 on 2008-05-12
well try
```
networkmanager
```

---

### Post by wolfen69 on 2008-05-12
check system>admin>hardware drivers

---

### Post by Dissident85 on 2008-05-12
> **subzero316 said:**
> well try
```
networkmanager
```

same thing again, command not found...

---

### Post by zenwalker on 2008-05-12
modprobe cmd will list the drivers loaded. Also issue lspci cmd to list all the devices present on pci slots. lsusb for usb based devices.

---

### Post by Dissident85 on 2008-05-12
> **wolfen69 said:**
> check system>admin>hardware drivers

all that is listed there is my graphics driver..

---

### Post by subzero316 on 2008-05-12
ok first 
post the output of ```
ifconfig -a
```

---

### Post by Dissident85 on 2008-05-12
> **subzero316 said:**
> ok first 
post the output of ```
ifconfig -a
```

```
eth0      Link encap:Ethernet  HWaddr 00:1d:09:3d:88:1e  
          inet addr:10.0.0.103  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:9ff:fe3d:881e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14010799 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14380499 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1121235250 (1.0 GB)  TX bytes:3248997445 (3.0 GB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4578 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4578 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:228900 (223.5 KB)  TX bytes:228900 (223.5 KB)
```

---

### Post by subzero316 on 2008-05-12
You haven`t installed your wifi driver...first u`ll have to do that...Post the output of ```
lspci
``` so we`ll know what is you wifi card

---

### Post by Dissident85 on 2008-05-12
```
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8400M GS (rev a1)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
09:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)
```

---

### Post by subzero316 on 2008-05-12
**Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection **  >>Thats your wifi card
Install it,

```
 

sudo aptitude install firmware-iwlwifi
sudo modprobe iwl4965


```

---

### Post by Dissident85 on 2008-05-12
> **subzero316 said:**
> **Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection **  >>Thats your wifi card
Install it,

```
 

sudo aptitude install firmware-iwlwifi
sudo modprobe iwl4965


```

```
Couldn't find any package whose name or description matched "firmware-iwlwifi"
Couldn't find any package whose name or description matched "firmware-iwlwifi"
No packages will be installed, upgraded, or removed.

``` 

:( it didnt work

---

### Post by subzero316 on 2008-05-12
**Install ndiswrapper** from the repositories and now you can install windows wireless drivers and get the 4965AGN wifi module working.
- Get the suitable windows driver [here]("http://downloadcenter.intel.com/download.aspx?url=/13000/eng/V11.1.1.0_XP_DRIVERS.ZIP&agr=N&ProductID=2753&DwnldId=13000&strOSs=All&OSFullName=All+Operating+Systems&lang=eng") and unpack it
get into that driver directory then

```
sudo ndiswrapper -i netw4965.inf
sudo ndiswrapper -m
```
```
ndiswrapper -l 
```terminal should now show the driver installed
```
sudo gedit /etc/modules 
```
and add line "ndiswrapper" in the end save and close.
After reboot you should be able to use you're wlan.

---

### Post by HotShotDJ on 2008-05-12
> **Dissident85 said:**
> ```
Couldn't find any package whose name or description matched "firmware-iwlwifi"
Couldn't find any package whose name or description matched "firmware-iwlwifi"
No packages will be installed, upgraded, or removed.

``` 

:( it didnt work

No, it wouldn't have worked.  The required module is included by default in Hardy.  If it isn't already loaded (verify with lsmod at the command line) then load it with "modprobe iwl4965"

---

### Post by HotShotDJ on 2008-05-12
> **subzero316 said:**
> **Install ndiswrapper**I'm quite sure that the iwl4965 driver has no need of ndiswrapper.

---

### Post by subzero316 on 2008-05-12
> **HotShotDJ said:**
> I'm quite sure that the iwl4965 driver has no need of ndiswrapper.

Yea it is installed by default...:)..jus checked

this will do
```
sudo modprobe iwl4965
```

---

