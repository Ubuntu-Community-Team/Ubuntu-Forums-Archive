---
title: "Can't connect to my internet"
date: 2012-10-20
forum: New to Ubuntu
---

### Post by southland on 2012-10-20
I put Ubuntu on my old laptop (HP Inspiron 1521). My other laptops (Macbook and Dell) show all existing internet connections (wireless) and I simply choose the one I want to hook up to. I have looked under the Network Connections (Wireless and DSL) and nothing is showing up. 

What must I do to find my internet connection at the house? It is DSL but we have a router in the house so we can use it wirelessly. Thanks for any help.

---

### Post by donkyhotay on 2012-10-20
> **southland said:**
> I put Ubuntu on my old laptop (HP Inspiron 1521). My other laptops (Macbook and Dell) show all existing internet connections (wireless) and I simply choose the one I want to hook up to. I have looked under the Network Connections (Wireless and DSL) and nothing is showing up. 

What must I do to find my internet connection at the house? It is DSL but we have a router in the house so we can use it wirelessly. Thanks for any help.

More information required, first of all are you trying to connect this laptop to the internet wirelessly? How is ubuntu installed, WuBi, dual-boot, standalone? Assuming that you are connecting to the internet wirelessly what kind of wireless card are you using? From the limited info you gave I'm going to assume this is a wireless connection and not using a wubi install which means the most likely cause of problem is lack of wireless drivers. First of all I would connect the computer using an ethernet cable and running the update manager to make certain you have the latest programs/drivers available. That might work however we are probably going to need to know what kind of wireless card you have for help with identifying and installing the specific wireless card driver you will need.

---

### Post by southland on 2012-10-20
> More information required, first of all are you trying to connect this laptop to the internet wirelessly? How is ubuntu installed, WuBi, dual-boot, standalone? Assuming that you are connecting to the internet wirelessly what kind of wireless card are you using? From the limited info you gave I'm going to assume this is a wireless connection and not using a wubi install which means the most likely cause of problem is lack of wireless drivers. First of all I would connect the computer using an ethernet cable and running the update manager to make certain you have the latest programs/drivers available. That might work however we are probably going to need to know what kind of wireless card you have for help with identifying and installing the specific wireless card driver you will need.

Thank you for your reply. I will attempt to answer your questions to the best of my ability. 

Yes, I am trying to connect wirelessly. We have DSL but I use a Cisco Linksys E1500 to make it wireless for our computers. My Dell PC, which runs Windows, and my MacbookPro automatically picked up the wireless connection and I simply clicked on it. My Inspiron 1521 is what I recently put Ubuntu on and the computer usually has a blue and lit up wi-fi symbol which is not working now, post Ubuntu. As far as parts, this computer has everything factory as I have added nothing new but the Ubuntu OS.

I installed Ubuntu and removed Windows (standalone?). 

I would love to hook it up some other way, I tried putting the wire directly into it, but it still doesn't work. 

Thanks for any additional information and thanks so much for your time.

---

### Post by newb85 on 2012-10-20
You can't rely on your wifi indicator light to behave the same way under Ubuntu as it did under Windows.  Maybe it will, maybe it won't.  On my old laptop for Windows, blue meant "enabled" and orange meant "disabled", while for Ubuntu, blue meant "activity" and orange meant "no activity".  On my current laptop for Windows, light-on means "enabled" and light-off means "disabled", while for Ubuntu, the light never comes on.

When you click the networking menu (next to the sound menu in the top-right corner of your screen), what options do you see?  Does it show a list of wireless networks?  Does it say something like "Wireless disabled by hardware switch"?

---

### Post by southland on 2012-10-20
> When you click the networking menu (next to the sound menu in the top-right corner of your screen), what options do you see? Does it show a list of wireless networks? Does it say something like "Wireless disabled by hardware switch"?

The only available options (in white) as opposed to the options that are grey (not available) are VPN Connections, Enable Networking (which has  a check besides it), and Edit connections. 

I have clicked on VPN connections--Configure VPN-- and there are no connections listed under any of the tabs, from wired to DSL. 

I don't know if I am supposed to 'set up' a connection. If so, I would like to know how. Also, The "connection" symbol (beside the sound function) has no lines on it, which I assume it does, like a cell phone, when it has some type of connection.

Is there a type of command that I can type in my terminal to help you out? Thanks. 
Thanks for any help.

---

### Post by newb85 on 2012-10-21
Please give the output of 
```
sudo lshw -c network
```

Put the output in code tags, like this:

[noparse]```
Output
Here
```[/noparse]

---

### Post by southland on 2012-10-21
> **newb85 said:**
> Please give the output of 
```
sudo lshw -c network
```

Put the output in code tags, like this:

[noparse]```
Output
Here
```[/noparse]



Here is my Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)

I cannot access the internet with the computer under discussion and thus cannot give you all the info with a simple copy and paste. However, I would really like to get this fixed and don't mind manually typing any relevant information from the results of that command. What specific lines would help you? (description, product, logical name, capacity, capabilities, configuration, etc.)? 

driver version: 2.0
broadcast=yes
autonegotiation= on

THIS ALSO MAY HELP. I just noticed that nm-tool shows up that I am:
State: disconnected
Type: Wired
Driver: b44
Wired Properties Carrier: off
Thanks for your help!

EDIT: I am about to put the code on a flash drive and upload it. Thanks.

---

### Post by southland on 2012-10-21
```
 *-network 
       description: Ethernet interface 
       product: BCM4401-B0 100Base-TX 
       vendor: Broadcom Corporation 
       physical id: 0 
       bus info: pci@0000:03:00.0 
       logical name: eth1 
       version: 02 
       serial: 00:1c:23:82:fb:4b 
       size: 10Mbit/s 
       capacity: 100Mbit/s 
       width: 32 bits 
       clock: 33MHz 
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=64 link=no multicast=yes port=twisted pair speed=10Mbit/s 
       resources: irq:21 memory:fe5fe000-fe5fffff 
```

---

### Post by southland on 2012-10-21
**UPDATE:** I can get on the internet if I hook the cable directly up to my computer, however, while that is good, it still doesn't solve my problem. I need to be able to use the computer wirelessly. Thanks for any help. I will let you know if I get it to working now.

---

### Post by NikTh on 2012-10-21
> **southland said:**
> **UPDATE:** I can get on the internet if I hook the cable directly up to my computer, however, while that is good, it still doesn't solve my problem. I need to be able to use the computer wirelessly. Thanks for any help. I will let you know if I get it to working now.

Hi , 

Hook the cable directly to your computer (to have Internet connection) and then open a terminal and copy-paste bellow commands with order, one by one.

```
wget "http://ubuntuone.com/1kKCgeRTZHszxUdsSEekYz" -O ~/wirelessinfo
chmod +x wirelessinfo 
./wirelessinfo 
gedit netinfo.txt
``` 

Last command will open the gedit editor with a lot of informations about your problem. Copy-paste those informations back here **but please put the results** between the brackets **[noparse]```
here
```[/noparse]** so can be readable. 

Thanks.

---

### Post by southland on 2012-10-21
> **NikTh said:**
> Hi , 

Hook the cable directly to your computer (to have Internet connection) and then open a terminal and copy-paste bellow commands with order, one by one.

```
wget "http://ubuntuone.com/1kKCgeRTZHszxUdsSEekYz" -O ~/wirelessinfo
chmod +x wirelessinfo 
./wirelessinfo 
gedit netinfo.txt
```Last command will open the gedit editor with a lot of informations about your problem. Copy-paste those informations back here **but please put the results** between the brackets **[noparse]```
here
```[/noparse]** so can be readable. 

Thanks.

[B]```
bobby@bobby-Inspiron-1521:~$ wget "http://ubuntuone.com/1kKCgeRTZHszxUdsSEekYz" -O ~/wirelessinfo
--2012-10-21 21:53:08--  http://ubuntuone.com/1kKCgeRTZHszxUdsSEekYz
Resolving ubuntuone.com (ubuntuone.com)... 91.189.89.205, 91.189.89.204
Connecting to ubuntuone.com (ubuntuone.com)|91.189.89.205|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1555 (1.5K) [application/octet-stream]
Saving to: `/home/bobby/wirelessinfo'

100%[======================================>] 1,555       --.-K/s   in 0.03s   

2012-10-21 21:53:09 (57.9 KB/s) - `/home/bobby/wirelessinfo' saved [1555/1555]
```[/B]

[B]```
n PCI device 0000:0b:00.0
[   19.965495] b44 0000:03:00.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   19.988970] ssb: Core 0 found: Fast Ethernet (cc 0x806, rev 0x07, vendor 0x4243)
[   19.989009] ssb: Core 1 found: V90 (cc 0x807, rev 0x03, vendor 0x4243)
[   19.989035] ssb: Core 2 found: PCI (cc 0x804, rev 0x0A, vendor 0x4243)
[   20.036509] ssb: Sonics Silicon Backplane found on PCI device 0000:03:00.0
[   20.036671] b44: Broadcom 44xx/47xx 10/100 PCI ethernet driver version 2.0
[   20.065718] b44 ssb1:0: eth0: Broadcom 44xx/47xx 10/100 PCI ethernet driver <MAC address removed>
[   22.334690] type=1400 audit(1350828169.341:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=841 comm="apparmor_parser"
[42409.988327] b44 ssb1:0: eth0: Link is up at 100 Mbps, full duplex
[42409.988359] b44 ssb1:0: eth0: Flow control is off for TX and off for RX


**************** done ********************

```[/B]

---

### Post by NikTh on 2012-10-22
I think this is not the complete output. 

Try again. 

```
gedit netinfo.txt
``` 

Copy-paste everything (edit -> select all -> edit -> copy) in here . 

Or

You can attach the netinfo.txt file here in your reply , by clicking the paperclip icon at the message toolbar. 

Thanks

---

### Post by southland on 2012-10-22
> **NikTh said:**
> I think this is not the complete output. 

Try again. 

```
gedit netinfo.txt
```Copy-paste everything (edit -> select all -> edit -> copy) in here . 

Or

You can attach the netinfo.txt file here in your reply , by clicking the paperclip icon at the message toolbar. 

Thanks

```


*************** info trace ****************



**** uname -a ****


Linux bobby-Inspiron-1521 3.2.0-29-generic-pae #46-Ubuntu SMP Fri Jul 27 17:25:43 UTC 2012 i686 athlon i386 GNU/Linux


**** lsb-release ****


DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.1 LTS"


**** lspci ****


03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
    Subsystem: Dell Device [1028:01fc]
    Kernel driver in use: b44
--
0b:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
    Subsystem: Dell Wireless 1390 WLAN Mini-Card [1028:0007]
    Kernel driver in use: b43-pci-bridge


**** lsusb ****


Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


**** iwconfig ****




**** rfkill ****


0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no


**** lsmod ****


Module                  Size  Used by
joydev                 17393  0 
dell_wmi               12601  0 
sparse_keymap          13658  1 dell_wmi
snd_hda_codec_idt      60251  1 
snd_hda_intel          32765  3 
snd_hda_codec         109562  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
dell_laptop            17767  0 
dcdbas                 14098  1 dell_laptop
snd_pcm                80845  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
r852                   17901  0 
snd                    62064  15 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
sm_common              16737  1 r852
nand                   49667  2 r852,sm_common
nand_ids                8547  1 nand
mtd                    35584  2 sm_common,nand
r592                   17808  0 
nand_bch               13003  1 nand
bch                    21757  1 nand_bch
nand_ecc               13070  1 nand
memstick               15857  1 r592
b44                    31364  0 
psmouse                72919  0 
serio_raw              13027  0 
sp5100_tco             13495  0 
ssb                    50691  1 b44
k8temp                 12905  0 
i2c_piix4              13093  0 
soundcore              14635  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
wl                   2646601  0 
radeon                737789  3 
ttm                    65344  1 radeon
drm_kms_helper         45466  1 radeon
mac_hid                13077  0 
drm                   197692  5 radeon,ttm,drm_kms_helper
lib80211               14040  1 wl
i2c_algo_bit           13199  1 radeon
rfcomm                 38139  0 
bnep                   17830  2 
parport_pc             32114  0 
bluetooth             158438  10 rfcomm,bnep
ppdev                  12849  0 
wmi                    18744  1 dell_wmi
video                  19068  0 
ati_agp                13242  0 
shpchp                 32325  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
sdhci_pci              18324  0 
firewire_ohci          40172  0 
sdhci                  28241  1 sdhci_pci
firewire_core          56906  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
pata_atiixp            12999  0 


**** nm-tool ****



NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            b44
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         66.211.125.150
    Prefix:          20 (255.255.240.0)
    Gateway:         66.211.112.1

    DNS:             66.211.112.5
    DNS:             12.231.80.5




**** NetworkManager.state ****



[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


**** NetworkManager.conf ****



[main]
plugins=ifupdown,keyfile
dns=dnsmasq

no-auto-default=<MAC address removed>,

[ifupdown]
managed=false


**** NetworkManager.conf-10.04 ****




**** interfaces ****


auto lo
iface lo inet loopback



**** iwlist ****




**** resolv ****


# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.0.1
search nexband.com


**** blacklist.conf ****


# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac


**** dmesg ****


[   18.455630] wmi: Mapper loaded
[   19.625929] wl: module license 'MIXED/Proprietary' taints kernel.
[   19.779139] wl 0000:0b:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   19.779174] wl 0000:0b:00.0: setting latency timer to 64
[   19.882340] b43-pci-bridge 0000:0b:00.0: setting latency timer to 64
[   19.906448] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x11, vendor 0x4243)
[   19.906489] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x0A, vendor 0x4243)
[   19.906518] ssb: Core 2 found: USB 1.1 Host (cc 0x817, rev 0x03, vendor 0x4243)
[   19.906547] ssb: Core 3 found: PCI-E (cc 0x820, rev 0x01, vendor 0x4243)
[   19.960874] ssb: Sonics Silicon Backplane found on PCI device 0000:0b:00.0
[   19.965495] b44 0000:03:00.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   19.988970] ssb: Core 0 found: Fast Ethernet (cc 0x806, rev 0x07, vendor 0x4243)
[   19.989009] ssb: Core 1 found: V90 (cc 0x807, rev 0x03, vendor 0x4243)
[   19.989035] ssb: Core 2 found: PCI (cc 0x804, rev 0x0A, vendor 0x4243)
[   20.036509] ssb: Sonics Silicon Backplane found on PCI device 0000:03:00.0
[   20.036671] b44: Broadcom 44xx/47xx 10/100 PCI ethernet driver version 2.0
[   20.065718] b44 ssb1:0: eth0: Broadcom 44xx/47xx 10/100 PCI ethernet driver <MAC address removed>
[   22.334690] type=1400 audit(1350828169.341:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=841 comm="apparmor_parser"
[42409.988327] b44 ssb1:0: eth0: Link is up at 100 Mbps, full duplex
[42409.988359] b44 ssb1:0: eth0: Flow control is off for TX and off for RX


**************** done ********************



```

---

### Post by NikTh on 2012-10-23
Hi ,

**connect to Internet** via cable (Ethernet) and then open a terminal and execute bellow commands 

```
sudo apt-get remove --purge bcmwl-kernel-source 
sudo apt-get install linux-firmware-nonfree
```

Then reboot your system without the Ethernet cable and see if wireless arisen.

---

