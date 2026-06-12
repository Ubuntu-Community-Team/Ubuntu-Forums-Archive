---
title: "wireless networks device not ready firmware missing"
date: 2011-10-03
forum: New to Ubuntu
---

### Post by mcgarrysean91 on 2011-10-03
I have a Dell Latitude x300 and I have Ubuntu 11.04 installed but it won't pick up any wireless networks and it says "wireless networks device not ready firmware missing". I am a beginner on Ubuntu and would love to be able to continue using it but I would like to have it working properly so any help?

---

### Post by westie457 on 2011-10-03
Hello and welcome

Chances are you have a Broadcom wireless chip. Just to make sure open a terminal Ctrl+Alt+t and type in ```
lspci -vnn
``` Copy the output and in a New reply click on the # at the top of the pane and paste between the ```

``` tags

Thank you.

---

### Post by anewguy on 2011-10-03
If you can, hard wire a connection between your PC and the router - this could even be at a friends house as it is not specific to "where" you are.

Next, go to System/Administration/Additional Hardware Drivers (you're title may look slightly different).  This will connect to the net (hence the need for the hard-wired connection) and try to download drivers for your device.  If it is successful, you may have to click on it to install the driver and/or activate it.  Then, remove the hard-wire and reboot.

Let us know if your wireless works then or not.

Dave ;)

---

### Post by mcgarrysean91 on 2011-10-03
ok

---

### Post by mcgarrysean91 on 2011-10-03
ok so anewguy i did that but there were No Proprietary Drivers so well yeah and westie457 i did that and it said all this

```
00:00.0 Host bridge [0600]: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller [8086:3580] (rev 02)
Subsystem: Dell Latitude X300 [1028:014f]
Flags: bus master, fast devsel, latency 0
Memory at <unassigned> (32-bit, prefetchable)
Capabilities: <access denied>
Kernel driver in use: agpgart-intel

00:00.1 System peripheral [0880]: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller [8086:3584] (rev 02)
Subsystem: Dell Latitude X300 [1028:014f]
Flags: bus master, fast devsel, latency 0

00:00.3 System peripheral [0880]: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller [8086:3585] (rev 02)
Subsystem: Dell Latitude X300 [1028:014f]
Flags: bus master, fast devsel, latency 0

00:02.0 VGA compatible controller [0300]: Intel Corporation 82852/855GM Integrated Graphics Device [8086:3582] (rev 02) (prog-if 00 [VGA controller])
Subsystem: Dell Latitude X300 [1028:014f]
Flags: bus master, fast devsel, latency 0, IRQ 10
Memory at e8000000 (32-bit, prefetchable) [size=128M]
Memory at e0000000 (32-bit, non-prefetchable) [size=512K]
I/O ports at 1800 [size=8]
Expansion ROM at <unassigned> [disabled]
Capabilities: <access denied>
Kernel driver in use: i915
Kernel modules: intelfb, i915

00:02.1 Display controller [0380]: Intel Corporation 82852/855GM Integrated Graphics Device [8086:3582] (rev 02)
Subsystem: Dell Latitude X300 [1028:014f]
Flags: fast devsel
Memory at f0000000 (32-bit, prefetchable) [size=128M]
Memory at e0080000 (32-bit, non-prefetchable) [size=512K]
Capabilities: <access denied>
Kernel modules: i915

00:1d.0 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 [8086:24c2] (rev 01) (prog-if 00 [UHCI])
Subsystem: Dell Device [1028:014f]
Flags: bus master, medium devsel, latency 0, IRQ 10
I/O ports at 1820 [size=32]
Kernel driver in use: uhci_hcd

00:1d.1 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 [8086:24c4] (rev 01) (prog-if 00 [UHCI])
Subsystem: Dell Device [1028:014f]
Flags: bus master, medium devsel, latency 0, IRQ 11
I/O ports at 1840 [size=32]
Kernel driver in use: uhci_hcd

00:1d.2 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 [8086:24c7] (rev 01) (prog-if 00 [UHCI])
Subsystem: Dell Device [1028:014f]
Flags: bus master, medium devsel, latency 0, IRQ 11
I/O ports at 1860 [size=32]
Kernel driver in use: uhci_hcd

00:1d.7 USB Controller [0c03]: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller [8086:24cd] (rev 01) (prog-if 20 [EHCI])
Subsystem: Dell Device [1028:014f]
Flags: bus master, medium devsel, latency 0, IRQ 10
Memory at e0100000 (32-bit, non-prefetchable) [size=1K]
Capabilities: <access denied>
Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 81) (prog-if 00 [Normal decode])
Flags: bus master, fast devsel, latency 0
Bus: primary=00, secondary=02, subordinate=0a, sec-latency=64
I/O behind bridge: 00003000-00003fff
Memory behind bridge: e0200000-e02fffff
Prefetchable memory behind bridge: 28000000-2fffffff
Kernel modules: shpchp

00:1f.0 ISA bridge [0601]: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge [8086:24cc] (rev 01)
Flags: bus master, medium devsel, latency 0
Kernel modules: iTCO_wdt, intel-rng

00:1f.1 IDE interface [0101]: Intel Corporation 82801DBM (ICH4-M) IDE Controller [8086:24ca] (rev 01) (prog-if 8a [Master SecP PriP])
Subsystem: Dell Latitude X300 [1028:014f]
Flags: bus master, medium devsel, latency 0, IRQ 11
I/O ports at 01f0 [size=8]
I/O ports at 03f4 [size=1]
I/O ports at 0170 [size=8]
I/O ports at 0374 [size=1]
I/O ports at 1810 [size=16]
Memory at 30000000 (32-bit, non-prefetchable) [size=1K]
Kernel driver in use: ata_piix

00:1f.3 SMBus [0c05]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller [8086:24c3] (rev 01)
Subsystem: Dell Latitude X300 [1028:014f]
Flags: medium devsel, IRQ 10
I/O ports at 1880 [size=32]
Kernel modules: i2c-i801

00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller [8086:24c5] (rev 01)
Subsystem: Dell Latitude X300 [1028:014f]
Flags: bus master, medium devsel, latency 0, IRQ 10
I/O ports at 1c00 [size=256]
I/O ports at 18c0 [size=64]
Memory at e0100c00 (32-bit, non-prefetchable) [size=512]
Memory at e0100800 (32-bit, non-prefetchable) [size=256]
Capabilities: <access denied>
Kernel driver in use: Intel ICH
Kernel modules: snd-intel8x0

00:1f.6 Modem [0703]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller [8086:24c6] (rev 01) (prog-if 00 [Generic])
Subsystem: Conexant Systems, Inc. D480 MDC V.9x Modem [14f1:5422]
Flags: medium devsel, IRQ 10
I/O ports at 2400 [size=256]
I/O ports at 2000 [size=128]
Capabilities: <access denied>
Kernel modules: snd-intel8x0m

02:03.0 CardBus bridge [0607]: Ricoh Co Ltd RL5c476 II [1180:0476] (rev ac)
Subsystem: Dell Latitude X300 laptop [1028:014f]
Flags: bus master, medium devsel, latency 168, IRQ 10
Memory at e0213000 (32-bit, non-prefetchable) [size=4K]
Bus: primary=02, secondary=03, subordinate=06, sec-latency=176
Memory window 0: 28000000-2bfff000 (prefetchable)
Memory window 1: 34000000-37fff000
I/O window 0: 00003000-000030ff
I/O window 1: 00003400-000034ff
16-bit legacy interface ports at 0001
Kernel driver in use: yenta_cardbus
Kernel modules: yenta_socket

02:03.1 CardBus bridge [0607]: Ricoh Co Ltd RL5c476 II [1180:0476] (rev ac)
Subsystem: Dell Latitude X300 laptop [1028:014f]
Flags: bus master, medium devsel, latency 168, IRQ 10
Memory at e0214000 (32-bit, non-prefetchable) [size=4K]
Bus: primary=02, secondary=07, subordinate=0a, sec-latency=176
Memory window 0: 2c000000-2ffff000 (prefetchable)
Memory window 1: 38000000-3bfff000
I/O window 0: 00003800-000038ff
I/O window 1: 00003c00-00003cff
16-bit legacy interface ports at 0001
Kernel driver in use: yenta_cardbus
Kernel modules: yenta_socket

02:03.2 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C552 IEEE 1394 Controller [1180:0552] (rev 04) (prog-if 10 [OHCI])
Subsystem: Dell Latitude X300 laptop [1028:014f]
Flags: bus master, medium devsel, latency 64, IRQ 11
Memory at e0212000 (32-bit, non-prefetchable) [size=2K]
Capabilities: <access denied>
Kernel driver in use: firewire_ohci
Kernel modules: firewire-ohci

02:04.0 Network controller [0280]: Broadcom Corporation BCM4309 802.11a/b/g [14e4:4324] (rev 03)
Subsystem: Dell Truemobile 1450 MiniPCI [1028:0003]
Flags: bus master, fast devsel, latency 64, IRQ 5
Memory at e0210000 (32-bit, non-prefetchable) [size=8K]
Kernel driver in use: b43-pci-bridge
Kernel modules: ssb

02:05.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5705M Gigabit Ethernet [14e4:165d] (rev 01)
Subsystem: Dell Device [1028:2003]
Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 11
Memory at e0200000 (64-bit, non-prefetchable) [size=64K]
Expansion ROM at <ignored> [disabled]
Capabilities: <access denied>
Kernel driver in use: tg3
Kernel modules: tg3
```

---

### Post by westie457 on 2011-10-03
Aah a challenge, you have a Broadcom chip I've not heard of, however the numbers thrown up by the command you ran (Broadcom Corporation BCM4309 802.11a/b/g [[COLOR="Red"]14e4:4324[/COLOR]] (rev 03)) suggest you need to use the legacy driver. In your Software Sources ensure that the top 4 boxes have a 'x' in.
Then open a terminal and run ```
sudo apt-get update

sudo apt-get install b43-fwcutter

sudo apt-get firmware-b43legacy-installer
```

unplug the wired connection and reboot. You should then be able to see local wireless networks. If you cannot see yours click the radar icon and select 'Connect to Hidden Network'. Enter the details as necessary and away you go.

---

### Post by mcgarrysean91 on 2011-10-03
And how do I go to software sources?

---

### Post by westie457 on 2011-10-03
> **mcgarrysean91 said:**
> And how do I go to software sources?

Sorry about that. Go to Software Centre find a button marked Software Sources. If not visible go to the Edit menu and select that way.

---

### Post by mcgarrysean91 on 2011-10-03
ok i put in ```
sudo apt-get firmware-b43legacy-installer
``` and it says 

```
E: Invalid operation firmware-b43legacy-installer

```

any ideas?

---

### Post by westie457 on 2011-10-03
Strange, we will try through Synaptic Package Manager now. If not already installed type synaptic into the search bar of Software Centre.
I presume you are using the Unity interface. Click the button top-left start to type synaptic then open it. In the quick search box type in bcm, you should see something similar to this screenshot. Check the box matching the package I said earlier and click apply.


                 =====================================================================

Huge apologies, missed an important word out of the command.
It should have been ```
 sudo apt-get install firmware-b43legacy-installer
```

---

### Post by anewguy on 2011-10-03
I had a 4309 instead of your 4306 but they use the same driver.  You will probably need to install the "all" firmware package as well.

Dave ;)

---

### Post by mcgarrysean91 on 2011-10-03
so now for some reason when i click the network spot on the top right it doesnt even say wireless, only wired. so i mustve done something very wrong. Is there anyway to do the remote desktop viewer so you can control my screen? or anything of that nature?

---

### Post by mcgarrysean91 on 2011-10-03
ok after i put in the third code westie457 i got this message ```
sudo apt-get install firmware-b43legacy-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  firmware-b43legacy-installer
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/3,478 B of archives.
After this operation, 49.2 kB of additional disk space will be used.
Selecting previously deselected package firmware-b43legacy-installer.
(Reading database ... 157183 files and directories currently installed.)
Unpacking firmware-b43legacy-installer (from .../firmware-b43legacy-installer_4.178.10.4-5_all.deb) ...
Setting up firmware-b43legacy-installer (4.178.10.4-5) ...
Not supported card here (PCI id 14e4:4324
14e4:165)!
Use b43 firmware. This is just for the b43legacy driver.
Aborting.
dpkg: error processing firmware-b43legacy-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 firmware-b43legacy-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by mcgarrysean91 on 2011-10-04
and anewguy how do i install the "all" firmware package?

---

### Post by anewguy on 2011-10-04
First try the following:

- disable the b43-legacy stuff  - you may have to blacklist the b43 and b43-legacy

- hard-wire again, go to synaptic package manager and look for and install the STA driver and remove the firmware cutter (essentially we want to reverse everything you have done so far so we are starting at a clean slate again).

- disconnect the hard-wire

- reboot


Dave ;)

Yeah, I know it's not marked for that chipset, but there seems to be a little problem with some of the chipset id's versus the driver recommended.  I ran into this same thing more than once.

If it doesn't work - no harm done and we'll continue on a different path.

---

### Post by mcgarrysean91 on 2011-10-04
ok now some how or another i was able to get it to scan for networks but it wont find any so i put all the information to connect to my router thru a "hidden" network but now it doesnt want to fully connect? any tests or anything i can run now?

---

### Post by wildmanne39 on 2011-10-04
Hi, a hidden network is hard for most wireless cards in ubuntu to connect to at first you should at least unhide it while you are trying to connect to it. 

Also a hidden network is not much more secure then one that is not, if a person wants to get in and has what it takes to crack your system it only takes a few seconds longer.
Thank you

---

### Post by mcgarrysean91 on 2011-10-04
see thats the thing its not actually hidden. i also have an iphone and connect to it wonderfully.

---

### Post by wildmanne39 on 2011-10-04
Hi, please post the results of these commands:
```
nm-tool
```
```
iwconfig
```
```
rfkill list all
```
```
sudo iwlist scan
```
```
lsmod | egrep -e b43 -e wl
```
```
dmesg | egrep 'b43|firm|wl|wlan0'
```
Thank you

---

### Post by mcgarrysean91 on 2011-10-04
ok first one ```
NetworkManager Tool

State: connected

- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             connected
  Default:           yes
  HW Address:        00:11:43:CC:40:DA

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.5
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ndiswrapper
  State:             disconnected
  Default:           no
  HW Address:        00:11:F5:09:A2:0C

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points
```
 
second one 
```
sean@sean-Latitude-X300:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management max timeout:0us  mode:All packets received
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sean@sean-Latitude-X300:~$ 

```

third one did absolutely nothing

fourth one 
```
sean@sean-Latitude-X300:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:18:01:F8:73:2C
                    ESSID:"6PXE4"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:10/100  Signal level:-89 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 02 - Address: 00:18:01:F8:89:38
                    ESSID:"NOEM4"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:1/100  Signal level:-95 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 03 - Address: 00:1F:90:DB:27:5C
                    ESSID:"Q4NU4"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:100/100  Signal level:-23 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 04 - Address: 00:1F:90:EC:26:5A
                    ESSID:"PLK22"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:10/100  Signal level:-89 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 05 - Address: 00:1F:90:D7:84:D8
                    ESSID:"ES3A4"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:15/100  Signal level:-86 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 06 - Address: 00:12:0E:7F:39:D8
                    ESSID:"sbrumbaugh"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:18/100  Signal level:-84 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

```

next one did nothing and finally 
```
sean@sean-Latitude-X300:~$ dmesg | egrep 'b43|firm|wl|wlan0'
[   27.993632] ndiswrapper: driver bcmwl5 (Broadcom,03/23/2006, 4.40.19.0) loaded
[   28.269507] wlan0: ethernet device 00:11:f5:09:a2:0c using NDIS driver: bcmwl5, version: 0x4281300, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 14E4:4324.5.conf
[   28.269590] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   28.362907] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   81.405873] ADDRCONF(NETDEV_UP): wlan0: link is not ready

```

---

### Post by wildmanne39 on 2011-10-04
Hi, you threw a curve ball you have ndiswrapper installed also.

You should delete the wireless connection you set up and let it scan and find the right connection when we get it working properly, also disconnect your wired connect before you run these commands.

Please run these commands one line at a time:
```
sudo modprobe -rf ndiswrapper
sudo apt-get remove --purge ndiswrapper-common ndiswrapper-utils-1.9 ndisgtk
sudo rm /etc/modprobe.d/ndiswrapper.conf
sudo rm -r /etc/ndiswrapper/* 
sudo depmod -a:
```
Then
```
sudo modprobe b43
```
if it does not connect please post the results of:
```
lsmod
```
Thank you

---

### Post by mcgarrysean91 on 2011-10-04
ok this is really weird but when i did those tests it just started working!?!?!?! its weird but ill take it lol thank you all so much

---

### Post by wildmanne39 on 2011-10-04
Hi, that is not weird, that is what I was hoping for, you may have to run this command to make it permanent.
```
sudo su 
echo b43 >> /etc/modules 
exit
```
Thank you

---

