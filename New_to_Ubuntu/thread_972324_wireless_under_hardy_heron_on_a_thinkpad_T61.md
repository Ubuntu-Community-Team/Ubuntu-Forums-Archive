---
title: "wireless under hardy heron on a thinkpad T61"
date: 2008-11-05
forum: New to Ubuntu
---

### Post by cincinnatus on 2008-11-05
Okay, I tried searching for information, but whenever anything looked promising, I didn't really know what it was talking about.

I just installed hardy on my Thinkpad T61, and I can't connect to my wireless internet. Ubuntu detects the network, and asks for the WEP key, looks like it's trying to connect, then asks for the key again. My adapter is a "Intel 82566mm gigabit network connection". I have a dual boot with XP, and wireless works perfectly fine on XP.

Here's the output for the commands suggested [here]("http://ubuntuforums.org/showthread.php?p=5024425#post5024425"):

$ lspci 
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c) 
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c) 
00:19.0 Ethernet controller: Intel Corporation 82566MM Gigabit Network Connection (rev 03) 
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03) 
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03) 
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03) 
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03) 
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03) 
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03) 
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03) 
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03) 
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03) 
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03) 
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03) 
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03) 
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03) 
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3) 
00:1f.0 ISA bridge: Intel Corporation 82801HBM (ICH8M-E) LPC Interface Controller (rev 03) 
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03) 
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03) 
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03) 
01:00.0 VGA compatible controller: nVidia Corporation Quadro NVS 140M (rev a1) 
03:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61) 
15:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ba) 
15:00.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 04) 

$ lsusb 
Bus 007 Device 001: ID 0000:0000   
Bus 006 Device 001: ID 0000:0000   
Bus 005 Device 001: ID 0000:0000   
Bus 003 Device 001: ID 0000:0000   
Bus 002 Device 001: ID 0000:0000   
Bus 001 Device 003: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader 
Bus 001 Device 001: ID 0000:0000   
Bus 004 Device 001: ID 0000:0000   

$ lshw -class network 
WARNING: you should run this program as super-user. 
  *-network                
       description: Ethernet interface 
       product: 82566MM Gigabit Network Connection 
       vendor: Intel Corporation 
       physical id: 19 
       bus info: pci@0000:00:19.0 
       logical name: eth0 
       version: 03 
       serial: 00:1e:37:d4:12:be 
       width: 32 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list ethernet physical 
       configuration: broadcast=yes driver=e1000 driverversion=7.3.20-k2-NAPI firmware=0.3-0 latency=0 module=e1000 multicast=yes 
  *-network 
       description: Wireless interface 
       product: PRO/Wireless 4965 AG or AGN Network Connection 
       vendor: Intel Corporation 
       physical id: 0 
       bus info: pci@0000:03:00.0 
       logical name: wmaster0 
       version: 61 
       serial: 00:1f:3b:52:5f:0f 
       width: 64 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list logical ethernet physical wireless 
       configuration: broadcast=yes driver=iwl4965 latency=0 module=iwl4965 multicast=yes wireless=IEEE 802.11g

---

### Post by james_vanb on 2008-11-05
Had a similar problem.  Installed Wifi-radar.  Combination of Network Manager and Wifi-radar seemed to correct problem.

Edit:  Turn of security at router first and confirm that you can connect, then try Wifi-radar.

---

### Post by cincinnatus on 2008-11-06
Wifi radar didn't help any. I've been working with ndiswrapper for the past few hours now, but I keep running into a dead end. I've tried reinstalling ndiswrapper and reinstalling the driver but it doesn't help.

I tried the command suggested [in pytheas22's wonderful troubleshooting guide]("http://ubuntuforums.org/showthread.php?t=885847&highlight=ndiswrapper+troubleshooting"):

```
$ dmesg | grep -e ndis -e wlan
[   20.420493] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   20.856816] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'KeBugCheck'
[   20.856991] ndiswrapper (load_sys_files:210): couldn't prepare driver 'netw5x32'
[   20.857367] ndiswrapper (load_wrap_driver:112): couldn't load driver netw5x32; check system log for messages from 'loadndisdriver'
[   20.883799] usbcore: registered new interface driver ndiswrapper
[ 1387.517855] usbcore: deregistering interface driver ndiswrapper
[ 1387.517938] ndiswrapper (ntoskernel_exit:2708): object f71e8520(2) was not freed, freeing it now
[ 1387.529306] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[ 1387.540852] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'KeBugCheck'
[ 1387.541039] ndiswrapper (load_sys_files:210): couldn't prepare driver 'netw5x32'
[ 1387.541679] ndiswrapper (load_wrap_driver:112): couldn't load driver netw5x32; check system log for messages from 'loadndisdriver'
[ 1387.543323] usbcore: registered new interface driver ndiswrapper


```
Could somebody move this thread to the "Networking and Wireless" forum? I think I might get more help there. Otherwise I'll have to repost...

---

