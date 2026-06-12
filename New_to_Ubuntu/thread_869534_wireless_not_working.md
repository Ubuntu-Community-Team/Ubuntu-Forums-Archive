---
title: "wireless not working"
date: 2008-07-24
forum: New to Ubuntu
---

### Post by bluzepher on 2008-07-24
HP Laptop
my wireless is not working, not sure what to do next.

thanks in advance for your help.

 iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4318"
          Mode:Managed  Frequency=2.472 GHz  Access Point: Invalid   
          Bit Rate=1 Mb/s   Tx-Power=18 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


 sudo lshw -C network
  *-network:0             
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:03:02.0
       logical name: eth1
       version: 02
       serial: 00:14:a5:23:13:4b
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.22-15-generic latency=64 link=no module=bcm43xx multicast=yes wireless=IEEE 802.11b/g
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 6
       bus info: pci@0000:03:06.0
       logical name: eth0
       version: 10
       serial: 00:0f:b0:79:3c:a0
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.3 latency=128 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s


 lsusb
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 045e:00b9 Microsoft Corp. Wireless Optical Mouse 3.0
Bus 001 Device 001: ID 0000:0000  


Thanks

---

### Post by bluzepher on 2008-07-24
lspci

00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 10)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 01)
00:14.6 Modem: ATI Technologies Inc SB400 AC'97 Modem Controller (rev 01)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)
03:00.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
03:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
03:04.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
03:04.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
03:04.4 Generic system peripheral [0805]: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller
03:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)


I noticed that this was also asked for.  Hope this helps.  The wireless does work in windows, not in Ubuntu  
thanks

---

### Post by Tim Sharitt on 2008-07-24
If you've got internet through ethernet cable, Enter this into a terminal:
```
 sudo apt-get install bcm43xx-fwcutter
```
and then reboot

---

### Post by bluzepher on 2008-07-24
sudo apt-get install bcm43xx-fwcutter

Reading package lists... Done
Building dependency tree       
Reading state information... Done
bcm43xx-fwcutter is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 7 not upgraded.

this is the response that I got.
did it work?

---

### Post by bluzepher on 2008-07-25
Looks like this did not fix the problem.  any other ideas why this laptop will not connect wireless?

thanks

---

