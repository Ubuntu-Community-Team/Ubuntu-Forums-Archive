---
title: "I can't connect to wireless internet on Lubuntu 11.04"
date: 2012-08-13
forum: New to Ubuntu
---

### Post by andrews2166 on 2012-08-13
Okay, my laptop is Sony Vaio PCG-VX71P that started out life with XP, it now runs on Linux Lubuntu 11.04 and I cannot connect to my wireless internet.

It does recognise the connection is there and it attempts to connect however after around 30 seconds I am presented with a box saying:

[B]Wireless Network
Disconnected- You are now offline[/B]

I've been looking for a solution for some time now and nothing seems to work, please help....thanks

---

### Post by jemadux on 2012-08-13
open  jockey-gtk and install non-free drivers to work

---

### Post by andrews2166 on 2012-08-13
Tried to open jockey-gtk, doesn't work

---

### Post by NikTh on 2012-08-13
Hi , 
please open a terminal and give the results of below commands . One line=one command. 

```
cat /etc/lsb-release && uname -r
lspci -nnk | grep -iA2 net 
nm-tool 
lsusb 
iwconfig 
rfkill list all 
lsmod
```Put the results inside [CODE] tags , by highlighting the text and click the # symbol on top of message pane. 
Thanks

---

### Post by mr-woof on 2012-08-13
out of interest, try this command:

iwlist wlan0 scan

do you see your wireless network listed? It'll be under ESSID:"XXX"

Edit: this is a good link with some commands to try

[http://www.cyberciti.biz/tips/linux-find-out-wireless-network-speed-signal-strength.html](http://www.cyberciti.biz/tips/linux-find-out-wireless-network-speed-signal-strength.html)

---

### Post by andrews2166 on 2012-08-13
okay here they are:

cat /etc/lsb-release && uname -r
```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.04
DISTRIB_CODENAME=natty
DISTRIB_DESCRIPTION="Ubuntu 11.04"
2.6.38-15-generic
```

lspci -nnk | grep -iA2 net 
```
01:08.0 Ethernet controller [0200]: Intel Corporation 82801BA/BAM/CA/CAM Ethernet Controller [8086:2449] (rev 03)
	Subsystem: Sony Corporation Device [104d:8111]
	Kernel driver in use: e100
```

nm-tool 
```
NetworkManager Tool

State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e100
  State:             unavailable
  Default:           no
  HW Address:        08:00:46:61:25:9B

  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Properties
    Carrier:         off


- Device: eth2 -----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            orinoco_cs
  State:             disconnected
  Default:           no
  HW Address:        00:02:2D:84:F1:EA

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes

  Wireless Access Points 
    NETGEAR:         Infra, 00:1E:2A:DB:94:3C, Freq 2437 MHz, Rate 11 Mb/s, Strength 68
```

lsusb 
```
Bus 002 Device 002: ID 054c:0069 Sony Corp. Memorystick MSC-U03 Reader
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 13fe:1d00 Kingston Technology Company Inc. DataTraveler 2.0 1GB/4GB Flash Drive / Patriot Xporter 4GB Flash Drive
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

iwconfig 
```
lo        no wireless extensions.

eth0      no wireless extensions.

eth2      IEEE 802.11b  ESSID:"NETGEAR"  
          Mode:Managed  Frequency:2.457 GHz  Access Point: None   
          Bit Rate:11 Mb/s   Sensitivity:1/0  
          Retry limit:8   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-122 dBm  Noise level=-122 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:68
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

rfkill list all 
```
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
```

lsmod
```
Module                  Size  Used by
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17335  1 
fat                    55505  1 vfat
parport_pc             32111  0 
ppdev                  12849  0 
dm_crypt               22463  0 
michael_mic            12540  4 
orinoco_cs             12898  1 
orinoco                69899  1 orinoco_cs
cfg80211              156212  1 orinoco
snd_intel8x0           33213  1 
snd_ac97_codec        105614  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80042  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
joydev                 17322  0 
snd_timer              28659  2 snd_pcm,snd_seq
pcmcia                 39671  1 orinoco_cs
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
yenta_socket           27230  0 
pcmcia_rsrc            18292  1 yenta_socket
snd                    55295  9 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i810                   22812  2 
psmouse                73312  0 
pcmcia_core            21505  4 orinoco_cs,pcmcia,yenta_socket,pcmcia_rsrc
i915                  451053  0 
drm_kms_helper         40971  1 i915
drm                   184164  5 i810,i915,drm_kms_helper
soundcore              12600  1 snd
i2c_algo_bit           13184  1 i915
sony_laptop            34432  0 
serio_raw              12990  0 
snd_page_alloc         14073  2 snd_intel8x0,snd_pcm
shpchp                 32345  0 
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
dm_raid45              88410  0 
xor                    21860  1 dm_raid45
btrfs                 527388  0 
zlib_deflate           26594  1 btrfs
libcrc32c              12543  1 btrfs
firewire_ohci          31504  0 
usb_storage            43946  1 
e100                   40108  0 
firewire_core          56138  1 firewire_ohci
video                  19112  1 i915
crc_itu_t              12627  1 firewire_core
```

thanks

---

### Post by andrews2166 on 2012-08-13
> **mr-woof said:**
> out of interest, try this command:

iwlist wlan0 scan

do you see your wireless network listed? It'll be under ESSID:"XXX" 

It replies: Interface doesn't support scanning

---

### Post by mr-woof on 2012-08-13
This is going to sound stupid, but is the wireless switched off? Button perhaps, possibly in the bios.

---

### Post by andrews2166 on 2012-08-13
> **mr-woof said:**
> This is going to sound stupid, but is the wireless switched off? Button perhaps, possibly in the bios.

Just checked both are on/enabled...

---

### Post by NikTh on 2012-08-13
Hi , 
please post the output of 
```
sudo hwinfo --netcard
``` 
Thanks

---

### Post by underdog512 on 2012-08-13
I have seen this issue quite a few times before and it has almost always been a driver issue.  So we need to install restricted drivers for you card.  You should see something in your settings/administration menu called "restricted drivers" or it may say "additional drivers."

---

### Post by andrews2166 on 2012-08-13
> **NikTh said:**
> Hi , 
please post the output of 
```
sudo hwinfo --netcard
``` 
Thanks

Replies with 

```
sudo: hwinfo: command not found
```

---

### Post by andrews2166 on 2012-08-13
> **underdog512 said:**
> I have seen this issue quite a few times before and it has almost always been a driver issue.  So we need to install restricted drivers for you card.  You should see something in your settings/administration menu called "restricted drivers" or it may say "additional drivers."

Okay, on the "Additional Drivers" it says 

No propriety drivers are in use on this system

and there is nothing in the box below

---

### Post by NikTh on 2012-08-13
Hi , 
give the results of ```
sudo lshw -C network
``` 
Thanks

---

### Post by andrews2166 on 2012-08-13
> **NikTh said:**
> Hi , 
give the results of ```
sudo lshw -C network
``` 
Thanks

Okay results for this are:

```
  *-network               
       description: Ethernet interface
       product: 82801BA/BAM/CA/CAM Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:01:08.0
       logical name: eth0
       version: 03
       serial: 08:00:46:61:25:9b
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=half firmware=N/A latency=66 link=no maxlatency=56 mingnt=8 multicast=yes port=MII speed=10Mbit/s
       resources: irq:9 memory:f4100000-f4100fff ioport:3000(size=64)
  *-network
       description: Wireless interface
       physical id: 1
       logical name: eth2
       serial: 00:02:2d:84:f1:ea
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=orinoco_cs driverversion=2.6.38-15-generic firmware=Lucent/Agere 9.48 link=no multicast=yes wireless=IEEE 802.11b

```

---

### Post by NikTh on 2012-08-13
Hi , 
I cannot understand why Ubuntu not recognize the Vendor or Product name.. of your wireless controller. 

Anyways , it seems a driver (orinoco) issue that you disconnected after a while . 
Try to install backport-modules for 11.04 (natty)  wireless , and see if something fixed . 

Open synaptic package manager and search for **linux-backports-modules** for wireless (or compact wireless , I don't remember exact name)
Install - reboot and see if wireless works properly.  
Thanks

---

### Post by andrews2166 on 2012-08-13
> **NikTh said:**
> Hi , 
I cannot understand why Ubuntu not recognize the Vendor or Product name.. of your wireless controller. 

Anyways , it seems a driver (orinoco) issue that you disconnected after a while . 
Try to install backport-modules for 11.04 (natty)  wireless , and see if something fixed . 

Open synaptic package manager and search for **linux-backports-modules** for wireless (or compact wireless , I don't remember exact name)
Install - reboot and see if wireless works properly.  
Thanks

Nope, problem still occurs...

---

### Post by marlow59 on 2012-08-13
I found a forum's entry where they talk about your card not being support, it might be helpful : [http://ubuntuforums.org/showthread.php?t=1919819](http://ubuntuforums.org/showthread.php?t=1919819)

---

### Post by marlow59 on 2012-08-13
The issue also seems to have been solved on the Launchpad : [https://answers.launchpad.net/ubuntu/+question/169150](https://answers.launchpad.net/ubuntu/+question/169150)

---

### Post by NikTh on 2012-08-13
> **marlow59 said:**
> I found a forum's entry where they talk about your card not being support, it might be helpful : [http://ubuntuforums.org/showthread.php?t=1919819](http://ubuntuforums.org/showthread.php?t=1919819)

Wireless here is functional , but one problem that occurs is disconnections after a while.

OP , can you access your router's configuration page ? Right click on network-manager icon and "Connection Information" . Read "Default Route" address and give this address to firefox. It will open router's config page. 
Try to find a report to channel and try to change the channel and see if wireless behaviors better. 
Thanks

---

### Post by andrews2166 on 2012-08-14
> **NikTh said:**
> Hi , 
please post the output of 
```
sudo hwinfo --netcard
``` 
Thanks

Okay, if this helps here are the results for that command

```
> hal.1: read hal dataprocess 1204: arguments to dbus_move_error() were incorrect, assertion "(dest) == NULL || !dbus_error_is_set ((dest))" failed in file dbus-errors.c line 280.
This is normally a bug in some application using the D-Bus library.
libhal.c 3483 : Error unsubscribing to signals, error=The name org.freedesktop.Hal was not provided by any .service files
21: PCI 108.0: 0200 Ethernet controller                         
  [Created at pci.318]
  Unique ID: rBUF.J3dGkOGuS_A
  Parent ID: 6NW+.1wYxkCEtAH5
  SysFS ID: /devices/pci0000:00/0000:00:1e.0/0000:01:08.0
  SysFS BusID: 0000:01:08.0
  Hardware Class: network
  Model: "Intel 82801BA/BAM/CA/CAM Ethernet Controller"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x2449 "82801BA/BAM/CA/CAM Ethernet Controller"
  SubVendor: pci 0x104d "Sony Corporation"
  SubDevice: pci 0x8111 
  Revision: 0x03
  Driver: "e100"
  Driver Modules: "e100"
  Device File: eth0
  Memory Range: 0xf4100000-0xf4100fff (rw,non-prefetchable)
  I/O Ports: 0x3000-0x3fff (rw)
  IRQ: 9 (921 events)
  HW Address: 08:00:46:61:25:9b
  Link detected: no
  Module Alias: "pci:v00008086d00002449sv0000104Dsd00008111bc02sc00i00"
  Driver Info #0:
    Driver Status: e100 is active
    Driver Activation Cmd: "modprobe e100"
  Driver Info #1:
    Driver Status: eepro100 is not active
    Driver Activation Cmd: "modprobe eepro100"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #10 (PCI bridge)

32: PCMCIA 01.0: 0282 WLAN controller
  [Created at pcmcia.84]
  Unique ID: BnC0.lG4e6KMEdl8
  Parent ID: ul7N.J5lSzbB0WR8
  SysFS ID: /devices/pci0000:00/0000:00:1e.0/0000:01:05.0/1.0
  SysFS BusID: 1.0
  Hardware Class: network
  Model: "Lucent WaveLAN/IEEE"
  Hotplug: CardBus
  Socket: 1
  Vendor: pcmcia 0x0156 "Lucent Technologies"
  Device: pcmcia 0x0002 "WaveLAN/IEEE"
  Driver: "orinoco_cs"
  Driver Modules: "orinoco_cs"
  Device File: eth2
  Features: WLAN
  HW Address: 00:02:2d:84:f1:ea
  Link detected: no
  WLAN channels: 1 2 3 4 5 6 7 8 9 10 11
  WLAN frequencies: 2.412 2.417 2.422 2.427 2.432 2.437 2.442 2.447 2.452 2.457 2.462
  WLAN encryption modes: WEP40 WEP104 TKIP
  WLAN authentication modes: open sharedkey wpa-psk wpa-eap
  Module Alias: "pcmcia:m0156c0002f06fn00pfn00pa23EB9949pbC562E72ApcD27DEB1Apd00000000"
  Driver Info #0:
    Driver Status: hostap_cs is not active
    Driver Activation Cmd: "modprobe hostap_cs"
  Driver Info #1:
    Driver Status: orinoco_cs is active
    Driver Activation Cmd: "modprobe orinoco_cs"
  Extra Info: Lucent Technologies, WaveLAN/IEEE, Version 01.01
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #20 (CardBus bridge)
```

---

### Post by NikTh on 2012-08-15
Hi , 
If disconnections is a problem with a mismatch of voltage between  card and socket then below commands will solve your problem.

```
sudo rmmod -vf orinoco_cs 
sudo modprobe orinoco_cs ignore_cis_vcc=1
```If above not goes well , then we can try to blacklist orinoco module , and modprobe hostap_cs and see if works better.
Thanks

---

### Post by andrews2166 on 2012-09-05
> **NikTh said:**
> Hi , 
If disconnections is a problem with a mismatch of voltage between  card and socket then below commands will solve your problem.

```
sudo rmmod -vf orinoco_cs 
sudo modprobe orinoco_cs ignore_cis_vcc=1
```If above not goes well , then we can try to blacklist orinoco module , and modprobe hostap_cs and see if works better.
Thanks

Okay, when I do ```
sudo rmmod -vf orinoco_cs
``` I get:

```
rmmod orinoco_cs, wait=no force
ERROR: Removing 'orinoco_cs': Resource temporarily unavailable
```

And when I do ```
sudo modprobe orinoco_cs ignore_cis_vcc=1

```

Nothing Happens

---

