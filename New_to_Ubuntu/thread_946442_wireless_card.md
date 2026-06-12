---
title: "wireless card?"
date: 2008-10-13
forum: New to Ubuntu
---

### Post by resiarlleh_on_eredar on 2008-10-13
ok i had another post and i posted in it about this but ill ask here lol

my laptop is now running ubuntu 8.04, and i cannot connect to the internet, (had xp) how do i make it work?

---

### Post by Idefix82 on 2008-10-13
Please open the terminal and type in
```
lshw -C network
```
then paste the output here. Please also post the output from
```
lspci
```
here.

---

### Post by resiarlleh_on_eredar on 2008-10-13
[sudo] password for hellraiser: 
  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5751 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:12:3f:e3:62:c2
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.86 firmware=5751-v3.29a latency=0 link=no module=tg3 multicast=yes port=twisted pair
  *-network
       description: Wireless interface
       product: PRO/Wireless 2200BG Network Connection
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:03:03.0
       logical name: eth1
       version: 05
       serial: 00:13:ce:2e:dd:08
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) latency=64 link=no maxlatency=24 mingnt=3 module=ipw2200 multicast=yes wireless=unassociated










 lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc M24 1P [Radeon Mobility X600]
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express (rev 01)
03:01.0 CardBus bridge: Texas Instruments PCI6515 Cardbus Controller
03:01.5 Communication controller: Texas Instruments PCI6515 SmartCard Controller
03:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)



this is what i get when i do both commands

---

### Post by Idefix82 on 2008-10-13
Your wireless card should work out of the box. Can you post the output from
```
iwconfig
```

---

### Post by resiarlleh_on_eredar on 2008-10-13
iwconfig

lo        no wireless extensions

eth0      no wireless extensions

eth1      IEE 802.11g  ESSID:"ittcampus"
          Mode:Managed Frequency:2.437 GHz   Access Point: 00:0B:0E:18:50:00
          Bit Rate:54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0
          Retry limit:7   RTS thr:off  Fragment thr:off
          Power Management:off
          Link Quality=70/100 Signal level=-58 dBm Noise level=-86 dBm
          Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
          Tx excessive retries:0 Invalid misc:1 Missed beacon:12

---

### Post by Idefix82 on 2008-10-13
It looks to me like you are connected to a wireless network.
Just to be sure try
```
ifconfig eth1 up
dhclient eth1
```

---

### Post by resiarlleh_on_eredar on 2008-10-13
k i ran them now what?

---

### Post by Idefix82 on 2008-10-13
Are you connected? Can you see the available networks in the network manager (left click the icon the top right corner)? Have you connected to one of them, provided a pass phrase if it's required by your router...

---

### Post by resiarlleh_on_eredar on 2008-10-13
no but while i was messing around with options i just got connected... so i dunno lol but thx for all ur help <3

---

