---
title: "Ubuntu 11.04 on Lenovo G475"
date: 2011-10-09
forum: New to Ubuntu
---

### Post by demeter on 2011-10-09
hi there, I've been trying to install the 11.04 on a lenovo G475. First i tried the x86 desktop edition but it wont install, so i downloaded the ubuntu-11.04-desktop-amd64 version and i was able to install it and was very happy that I have been able to until I rebooted the machine. It freezes when in comes to the log in screen. One thing I noticed though that, whenever I disable the wireless LAN on the bios, it would boot normally but then I cannot use the wireless capability of my laptop. Any help would be greatly appreciated. Thanks...

just an update: I do have this machine on dual boot with windows 7 ultimate x64, I just found out that if I boot it on win 7 first then using the function keys to turn off the wifi, I could boot into ubuntu with no problem(well except that i have no wifi,would be handy if the function keys works on natty,but it does'nt). Then when I again reboot and log on to win 7, turn on the wifi,reboot again and to my surprise I could boot on the natty.

Found a solution(if you can call it as one) for the freezing problem,  its a bit funny though, as I figured out that the problem seems to be  connected with the ethernet hardware, I made a loopback cable and  inserted it on the ethernet port of the G475, and it booted normally and  with wifi capability. well, its funny to look at and I myself could'nt  consider this as a proper slotion that addresses to the said problem but  it works and I can now use natty with no problems whatsoever....for  now... just hope that there would be other solution for this...

---

### Post by demeter on 2011-10-10
Found a solution(if you can call it as one) for the freezing problem,  its a bit funny though, as I figured out that the problem seems to be  connected with the ethernet hardware, I made a loopback cable and  inserted it on the ethernet port of the G475, and it booted normally and  with wifi capability. well, its funny to look at and I myself could'nt  consider this as a proper solution that addresses to the said problem but  it works and I can now use natty with no problems whatsoever....for  now... just hope that there would be other solution for this...

---

### Post by mörgæs on 2011-10-10
Posts merged.

---

### Post by Idefix82 on 2011-10-10
What's the wifi card in your machine? You can type in the terminal
```

lspci
lshw -C network

```
and paste the output here (ideally enclosed in [CODE] tags).

---

### Post by demeter on 2011-10-10
thanks for the reply, heres the output when i did the lspci:
noyski@noyski-Lenovo-G475:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] Pavilion DM1Z-3000 Host bridge
00:01.0 VGA compatible controller: ATI Technologies Inc Device 9802
00:04.0 PCI bridge: Advanced Micro Devices [AMD] Device 1512
00:11.0 SATA controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 42)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
00:14.3 ISA bridge: ATI Technologies Inc SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (rev 40)
00:15.0 PCI bridge: ATI Technologies Inc Device 43a0
00:15.1 PCI bridge: ATI Technologies Inc Device 43a1
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 0 (rev 43)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 6
00:18.6 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 5
00:18.7 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 7
03:00.0 Ethernet controller: Atheros Communications AR8152 v2.0 Fast Ethernet (rev c1)
04:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)

 lshw -C network output:

noyski@noyski-Lenovo-G475:~$ sudo lshw -C network
[sudo] password for noyski: 
  *-network               
       description: Ethernet interface
       product: AR8152 v2.0 Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: c1
       serial: 1c:75:08:69:21:67
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI duplex=full firmware=N/A latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:40 memory:f0100000-f013ffff ioport:2000(size=128)
  *-network
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlan0
       version: 01
       serial: 68:a3:c4:10:da:13
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=2.6.38-11-generic firmware=N/A ip=192.168.0.109 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:f0000000-f000ffff
noyski@noyski-Lenovo-G475:~$ 

thanks...

---

### Post by demeter on 2011-10-11
[SIZE=3]finally found a fix on the problem here: [http://ubuntuforums.org/showthread.php?p=11330488&posted=1#post11330488:D](http://ubuntuforums.org/showthread.php?p=11330488&posted=1#post11330488:D)

[/SIZE]

---

