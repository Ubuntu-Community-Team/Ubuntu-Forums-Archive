---
title: "[SOLVED] What wireless driver am Im using?"
date: 2008-06-14
forum: New to Ubuntu
---

### Post by Sprogg2001 on 2008-06-14
Help! My wireless connection is working! :biggrin:

a little info...

Over the last two weeks I have followed a lot of guides, tutorials and how-twos to get my wireless connection to work consistently I have lost track of what I have actually done, I got it to work then a kernel update broke it again then it worked sometimes but was a really bad connection. All of this can be blamed on me using a cheap no name laptop with no hardware documentation of any sort :(

I finally removed ndis wrapper & network manager and installed WICD and now it works perfectly. 

In order to avoid this pain should I ever have to reinstall I wanted to know what type of wireless driver I'm using.

If you have a look below you will see my wireless interface has no listed driver. Can someone please tell me how I can go about identifying my wireless card and what driver I'm using?

```
sudo lshw -C network
[sudo] password for sprogg: 
  *-network               
       description: Ethernet interface
       product: 191 Gigabit Ethernet Adapter
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 02
       serial: 00:03:0d:88:dc:45
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sis190 driverversion=1.2 duplex=half latency=0 link=no module=sis190 multicast=yes port=MII speed=10MB/s
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:10:60:99:60:57
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.70 multicast=yes wireless=IEEE 802.11g
 
```

---

### Post by ajmorris on 2008-06-14
hi there,
to find out what card you are using, ```
sudo lspci
``` will tell you.

As for finding out what driver you are using... im sure there is another easy way to do it, but one way is using ```
sudo dmesg
```. if you type sudo dmesg in a terminal, you will get an output of lots of stuff, what you need to look for is something like this:
```
wlan0: ethernet device 00:1a:73:65:c0:dc using NDIS driver: bcmwl5, version: 0x4281300, WPA, WPA2, WPA2PSK
```That code there is what happens when my wireless adapter loads, so if you dont want to manually look for it, you could try variations of:
```
sudo dmesg | grep -i ethernet
sudo dmesg | grep -i wlan0
sudo dmesg | grep -i eth1
```AJ

---

### Post by Sprogg2001 on 2008-06-14
Thanks for replying 

here is my output. I was online at the time and the WLAN link was up, its not a PCIMA it is "internal onboard wifi" 

```
sudo dmesg | grep -i wlan0
[  262.776471] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  263.539419] wlan0: Initial auth_alg=0
[  263.539427] wlan0: authenticate with AP 00:90:d0:df:86:d6
[  263.540931] wlan0: RX authentication from 00:90:d0:df:86:d6 (alg=0 transaction=2 status=0)
[  263.540934] wlan0: authenticated
[  263.540936] wlan0: associate with AP 00:90:d0:df:86:d6
[  263.542643] wlan0: RX AssocResp from 00:90:d0:df:86:d6 (capab=0x431 status=0 aid=2)
[  263.542647] wlan0: associated
[  263.542650] wlan0: switched to short barker preamble (BSSID=00:90:d0:df:86:d6)
[  263.543641] wlan0: WMM queue=2 aci=0 acm=0 aifs=3 cWmin=15 cWmax=1023 burst=0
[  263.543645] wlan0: WMM queue=3 aci=1 acm=0 aifs=7 cWmin=15 cWmax=1023 burst=0
[  263.543647] wlan0: WMM queue=1 aci=2 acm=0 aifs=2 cWmin=7 cWmax=15 burst=30
[  263.543650] wlan0: WMM queue=0 aci=3 acm=0 aifs=2 cWmin=3 cWmax=7 burst=15
[  263.545274] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  271.094426] wlan0: no IPv6 routers present
```


also 

```
sprogg@sprogg-laptop:~$ sudo lspci -v -nn -m
Device:	00:00.0
Class:	Host bridge [0600]
Vendor:	Silicon Integrated Systems [SiS] [1039]
Device:	671MX [0671]
SVendor:	Elitegroup Computer Systems [1019]
SDevice:	Unknown device [5050]

Device:	00:01.0
Class:	PCI bridge [0604]
Vendor:	Silicon Integrated Systems [SiS] [1039]
Device:	SiS AGP Port (virtual PCI-to-PCI bridge) [0003]

Device:	00:02.0
Class:	ISA bridge [0601]
Vendor:	Silicon Integrated Systems [SiS] [1039]
Device:	SiS968 [MuTIOL Media IO] [0968]
SVendor:	Elitegroup Computer Systems [1019]
SDevice:	Unknown device [5a00]
Rev:	01

Device:	00:02.5
Class:	IDE interface [0101]
Vendor:	Silicon Integrated Systems [SiS] [1039]
Device:	5513 [IDE] [5513]
SVendor:	Elitegroup Computer Systems [1019]
SDevice:	Unknown device [5a00]
Rev:	01
ProgIf:	80

Device:	00:03.0
Class:	USB Controller [0c03]
Vendor:	Silicon Integrated Systems [SiS] [1039]
Device:	USB 1.1 Controller [7001]
SVendor:	Elitegroup Computer Systems [1019]
SDevice:	Unknown device [5a00]
Rev:	0f
ProgIf:	10

Device:	00:03.1
Class:	USB Controller [0c03]
Vendor:	Silicon Integrated Systems [SiS] [1039]
Device:	USB 1.1 Controller [7001]
SVendor:	Elitegroup Computer Systems [1019]
SDevice:	Unknown device [5a00]
Rev:	0f
ProgIf:	10

Device:	00:03.3
Class:	USB Controller [0c03]
Vendor:	Silicon Integrated Systems [SiS] [1039]
Device:	USB 2.0 Controller [7002]
SVendor:	Elitegroup Computer Systems [1019]
SDevice:	Unknown device [5a00]
ProgIf:	20

Device:	00:04.0
Class:	Ethernet controller [0200]
Vendor:	Silicon Integrated Systems [SiS] [1039]
Device:	191 Gigabit Ethernet Adapter [0191]
SVendor:	Elitegroup Computer Systems [1019]
SDevice:	Unknown device [5a00]
Rev:	02

Device:	00:05.0
Class:	IDE interface [0101]
Vendor:	Silicon Integrated Systems [SiS] [1039]
Device:	SATA Controller / IDE mode [1183]
SVendor:	Silicon Integrated Systems [SiS] [1039]
SDevice:	SATA Controller / IDE mode [1183]
Rev:	03
ProgIf:	8f

Device:	00:0f.0
Class:	Audio device [0403]
Vendor:	Silicon Integrated Systems [SiS] [1039]
Device:	Azalia Audio Controller [7502]
SVendor:	Elitegroup Computer Systems [1019]
SDevice:	Unknown device [5a00]

Device:	01:00.0
Class:	VGA compatible controller [0300]
Vendor:	Silicon Integrated Systems [SiS] [1039]
Device:	771/671 PCIE VGA Display Adapter [6351]
SVendor:	Elitegroup Computer Systems [1019]
SDevice:	Unknown device [5050]
Rev:	10

```


I would understand if it didn't work, but the fact that it does and without any identifiable drivers or device is just spooky!

Ok, so now I know its Device 2.0 by elite group computer systems in China with not a single mention of the word linux on their entire website? 

worse they make about 30 models of laptops and I don't even know what model mine is all the labels on the bottom are in Mandarin! Arrgh next time I'm really going to go all out and purchase a laptop with a manual. 

thanks for the help so far.

---

