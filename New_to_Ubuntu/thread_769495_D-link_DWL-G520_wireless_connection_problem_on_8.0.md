---
title: "D-link DWL-G520 wireless connection problem on 8.04"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by Teoman on 2008-04-26
Hi,
I am new and begginer user. i have some wireless connection problems about  my desktop. There is results about my wireless card. i can see my wireless network but i cannot connect it.

Teoman


phyxius@quadcore:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 01
       serial: 00:1a:4d:55:09:07
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.2LK latency=0 module=r8169 multicast=yes
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth1
       version: 01
       serial: 00:1a:4d:55:09:05
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.2LK ip=192.168.1.2 latency=0 module=r8169 multicast=yes
  *-network
       description: Wireless interface
       product: AR5212/AR5213 Multiprotocol MAC/baseband processor
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wifi0
       version: 01
       serial: 00:1b:11:1e:01:f1
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci latency=168 maxlatency=28 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11g



phyxius@quadcore:~$ lspci
00:00.0 Host bridge: Intel Corporation 82X38/X48 Express DRAM Controller (rev 01)
00:01.0 PCI bridge: Intel Corporation 82X38/X48 Express Host-Primary PCI Express Bridge (rev 01)
00:06.0 PCI bridge: Intel Corporation 82X38/X48 Express Host-Secondary PCI Express Bridge (rev 01)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8800 GT (rev a2)
04:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
04:00.1 IDE interface: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
07:00.0 Ethernet controller: Atheros Communications Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor (rev 01)
07:06.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)

---

### Post by sam_delta on 2008-04-26
another thing, are you sure you have a Dlink wireless card? i thought it was a Atheros

do you found your windows drivers?,   XXXXx.inf and XXXXX.sys?
if have em, well do the ndiswrapper thing from the other thread
post# 18  from  [http://ubuntuforums.org/showthread.php?t=769333&page=2](http://ubuntuforums.org/showthread.php?t=769333&page=2)

---

### Post by Teoman on 2008-04-26
Yeah,
it is D-Link DWL-G520 with atheros chipset
i can see my wireless connection but i cannot connect it. i type password after it seems connecting but not. it wants password again and again.

i did steps as you said. but i couldnt connect.

---

### Post by sam_delta on 2008-04-26
have you tried on another network, try removing your network password and see it you can connect?

you already did ndiswrapper thing?
what does this returns?
```
 ndiswrapper -l
```

---

### Post by urk_nono on 2008-04-26
[http://ubuntuforums.org/showthread.php?t=766887](http://ubuntuforums.org/showthread.php?t=766887)

Check it out. Made my day

---

### Post by Teoman on 2008-04-26
i did. and seem like that.

phyxius@quadcore:~$ ndiswrapper -l
oem10 : driver installed
	device (168C:0013) present (alternate driver: ath_pci)

---

### Post by Teoman on 2008-04-26
Thanks urk_nono

:)

---

### Post by Teoman on 2008-04-26
Sam

What do you think? what should be problem about my connection?

Teoman

---

### Post by urk_nono on 2008-04-26
I'm no pro myself, but do you get a wireless icon in your network-manager? 
(When using wired connection there are two black screens appearing) 


System -> Administration -> Network
Ususally there should be a wireless icon, a wired icon and a modem icon. Do you have them all?

And post the ouput of iwconfig

---

### Post by Teoman on 2008-04-26
yes, i have them all. when i click window appear and i choose my connection and password it seems connect but after it needs password again and again.  

i tried your  advice "http://ubuntuforums.org/showthread.php?t=766887" 

but it seems same. problem goes on.

---

### Post by urk_nono on 2008-04-26
Aha! Perhaps the problem lies within the encryption.

What encryption did you choose when setting up your router?

---

### Post by Teoman on 2008-04-26
i think i can read your answer tomorrow. i must sleep. ;)
Thanks a lot.

---

### Post by Teoman on 2008-04-26
upps.
i was reading" http://ubuntuforums.org/showthread.php?t=571188&highlight=AR5212%2FAR5213" and [http://ubuntuforums.org/showthread.php?t=202834&highlight=dwl-g520](http://ubuntuforums.org/showthread.php?t=202834&highlight=dwl-g520)

:)
my modems encryption is like that

Method:	        WPA2 and WPA
Encryption:	AES and TKIP

what do you think and what should i do? i have to change my encryption method? it means less security? WEP?

---

### Post by sam_delta on 2008-04-27
try WEP, or just no encryption at all, just to make sure thats actually the problem. if thats the problem, we can figure something out

sam

---

