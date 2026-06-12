---
title: "wireless issues"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by bmann11 on 2008-04-26
with  7.10 I activated my wireless card through what is the hardware drivers program, only now no with Hardy no my wireless driver doesn't show up.  Any ideas?

---

### Post by richardd2137 on 2008-04-26
you would prolly. have to install it (your wifi driver) through ndiswrapper to get it to work

---

### Post by jlandaw on 2008-04-26
I'm having the same problem.

In gusty it at least showed my wireless driver in the restricted drivers menu... I still had to set it up manually thou, using ndiswrapper. In Hardy it does not work at all...

I did switch to 64 bit tho, so i don't know if that is the problem...

If anyone knows how to get the hardware driver menu to acknowledge our hardware, please help!!!!

---

### Post by sam_delta on 2008-04-26
whats your wireless card model / manufacturer,?  you may not need to install ndiswrapper

sam

---

### Post by Teoman on 2008-04-26
Hi,
i am new ubuntu user, and my desktop has Atheros Communications Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor (rev 01) pci card.when i tried to connect wireless network ,i click on the icon and see my wifi connection after i type my wap key wap psk key it tries to connect but cannot. so please help me.
Teoman
i tried to install madwifi and i used some codes and took these results:

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
phyxius@quadcore:~$ lsmod | grep ath
ath_rate_sample        14336  1 
ath_pci               101024  0 
wlan                  207728  4 wlan_scan_sta,ath_rate_sample,ath_pci
ath_hal               192592  3 ath_rate_sample,ath_pci
phyxius@quadcore:~$ sudo ifconfig eth0 down
[sudo] password for phyxius: 
phyxius@quadcore:~$ sudo ifconfig eth0 down
phyxius@quadcore:~$ sudo ifconfig ath0 up
phyxius@quadcore:~$ ifconfig ath0 up
SIOCSIFFLAGS: Permission denied
phyxius@quadcore:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

wifi0     Interface doesn't support scanning.

ath0      Scan completed :
          Cell 01 - Address: 00:14:C1:20:64:F3
                    ESSID:"Magen Malikanesi"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=45/70  Signal level=-50 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: 00:1C:A8:1C:C8:87
                    ESSID:"AIRTIES_RT-211"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=1/70  Signal level=-94 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:bcn_int=200
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK

---

### Post by sam_delta on 2008-04-26
have you tried wired? or to another network, or yours but without a password?

sam

---

### Post by bmann11 on 2008-04-26
my wireless card is:

dell truemobile 1300 wlan mini pci card

by the way, I was able to install in 7.10 w/out ndiswrapper, although I installed that as well.

---

### Post by Teoman on 2008-04-26
i only tried to connect my network. now i will try to connect another network and without password.


i tried to connect without password to my network i couldnt :( now there is only my network. so i cannot try to connect others.

---

### Post by sam_delta on 2008-04-26
alright bmann11, ull need to reinstall fwcutter using aptitud NOT synaptic

make sure you have a wired conection

go into a terminal and type the following

to remove previous fw cutter

```
 sudo aptitude remove b43-fwcutter 
```

to update repos
```
 sudo aptitude update 
```

to install again
```
 sudo aptitude install b43-fwcutter 
```

restart pc, and u should be able to activate hardware drivers under system>administration>hardware driveres

tell  us how it goes'

sam

---

### Post by bmann11 on 2008-04-26
wired is working fine for me.  Wireless, whether roaming or manual set-up, is not working.

---

### Post by sam_delta on 2008-04-26
> **Teoman said:**
> i only tried to connect my network. now i will try to connect another network and without password.


i tried to connect without password to my network i couldnt :( now there is only my network. so i cannot try to connect others.

nvm, iduno whats going on, let me reserch on this one. for now, try to conect to another network, do you have working wired conection?

---

### Post by Teoman on 2008-04-26
Sam Delta,

could you help me solve this problem. i installed ubuntu 8.04 on my laptop and i didnt have any problem about wireless connection. but on my desktop i didnt connect.

you should show me the way step by step? just you say and i will apply these steps.

Teoman

---

### Post by bmann11 on 2008-04-26
tried it sam_delta but didn't work.  I'm still getting only a softward modem in the hardware drivers program that says its enabled and in use.  Thanks for your help, gotta put this down and take care of the kids for a while.  I'll check in later.

---

### Post by sam_delta on 2008-04-26
> **Teoman said:**
> Sam Delta,

could you help me solve this problem. i installed ubuntu 8.04 on my laptop and i didnt have any problem about wireless connection. but on my desktop i didnt connect.

you should show me the way step by step? just you say and i will apply these steps.

Teoman

teoman i will do my best to help you.
could you please tell me your desktop wirless card model/manufacturer plx?

you should also consider making a new thread
sam

---

### Post by Teoman on 2008-04-26
Thanks :)

i think i installed madwifi but who knows, he he. i am begginer :(

wireless card info:

product: AR5212/AR5213 Multiprotocol MAC/baseband processor
vendor: Atheros Communications Inc.

Teoman

---

### Post by sam_delta on 2008-04-26
> **bmann11 said:**
> tried it sam_delta but didn't work.  I'm still getting only a softward modem in the hardware drivers program that says its enabled and in use.  Thanks for your help, gotta put this down and take care of the kids for a while.  I'll check in later.

alright, did it ask to fetch any firmware when you did sudo aptitude install b43-fwcutter??

also, could you post the output of 

```
 lshw -C network 
```
and 
```
 lspci 
```

thx

---

### Post by Teoman on 2008-04-26
i dont think so. you know i am begginer and i try everything so i dont know what did i try. :D


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
> **Teoman said:**
> Thanks :)

i think i installed madwifi but who knows, he he. i am begginer :(

wireless card info:

product: AR5212/AR5213 Multiprotocol MAC/baseband processor
vendor: Atheros Communications Inc.

Teoman

@teoman
youll need to install ndiswrapper with the windows drivers

the first step is to install ndiswrapper, you can do this, by going into the system>administration>synaptic package manager, and serch for the package Ndiswrapper, and mark for installation, click apply

one ndiswrapper is intalled, well need to get the apropiate windows driveres for your wireless card, you can find those on your manufacturer website, if you cant find them, tell us, we can help you find them, once we have them, we go into the terminal go into the same directory as the windows drivers , for example, if you have windows drivers in your desktop type

```
cd Desktop
```

then, we install drivers by typing

Code:

 ```
sudo ndiswrapper -i driver.inf
```

then we make sure drivers installed correctly by typing

Code:

 ```
sudo ndiswrapper -l
```

something like "XXXXX : driver installed device (XXXX:XXXX) present" should appear

then we run the correspondint modules
[/code]
Code:

```
sudo ndiswrapper -m
```

and
Code:

```
sudo modprobe ndiswrapper
```

restart, check if works, if it dosnt work,

type this:
to remove other wireless modules
Code:

 ```
sudo modprobe -r b44
```

Code:

 ```
sudo modprobe -r b43
```

Code:

```
 sudo modprobe -r b43legacy
```

Code:

```
 sudo modprobe -r ssb
```

Code:

 ```
sudo modprobe -r ndiswrapper
```

then run ndiswrapper and b44 module again
Code:

 ```
sudo modprobe ndiswrapper
```

Code:

```
 sudo modprobe b44
```

check/restart and see if it works

tell us how it goes,
Sam

---

### Post by sam_delta on 2008-04-26
teoman, if you have further questions please start a new thread, this thread was made by bmann11 and his problem is not solved yet. we are getting confused with 2 cases in the same thread. we are still going to help you.

thanks

---

### Post by Teoman on 2008-04-26
Sam,
i installed Ndiswrapper. and i have my pc's drivers in my external hdd. so i copied on desktop "D-Link AirPlus DWL-G520 Wireless PCI Adapter(rev.B)"
so which should i follow steps.
Teoman

---

### Post by Teoman on 2008-04-26
Ok. i will go on another case.

---

