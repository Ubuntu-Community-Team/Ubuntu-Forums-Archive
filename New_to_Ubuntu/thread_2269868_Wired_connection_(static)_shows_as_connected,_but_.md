---
title: "Wired connection (static) shows as connected, but no internet and can't ping router"
date: 2015-03-18
forum: New to Ubuntu
---

### Post by keiko2 on 2015-03-18
Hi heros,

I've recently installed Lubuntu 14.10 on an old hp pavillion ze4400 laptop completely replacing XP.  During the installation, the wired network was not automatically recognized.  I've since tried both dhcp and static settings.  Dhcp never connects.  Static connects (network managers shows a happy connection and my router shows the machine), but won't go to the internet and the router can't be pinged (Destination Host Unreachable).  I've searched all over the place for a solution to no avail.

Below is my current situation first for dhcp, then for static.  Hope you can help.

/etc/network/interfaces when set to DHCP:
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
# primary connection
auto eth0
iface eth0 inet dhcp

ifconfig:
eth0      Link encap:Ethernet  HWaddr 00:0b:cd:a6:d0:94  
          inet6 addr: fe80::20b:cdff:fea6:d094/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:124 dropped:0 overruns:0 frame:559
          TX packets:211 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:45562 (45.5 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1200 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1200 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:95520 (95.5 KB)  TX bytes:95520 (95.5 KB)

/etc/network/interfaces when set to STATIC:
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
# primary connection
auto eth0
iface eth0 inet static
address 192.168.1.105
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1
dns-nameservers 192.168.1.1

ifconfig:
eth0      Link encap:Ethernet  HWaddr 00:0b:cd:a6:d0:94  
          inet addr:192.168.1.105  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20b:cdff:fea6:d094/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:15 dropped:0 overruns:0 frame:60
          TX packets:85 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:4166 (4.1 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:156 errors:0 dropped:0 overruns:0 frame:0
          TX packets:156 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:13412 (13.4 KB)  TX bytes:13412 (13.4 KB)

lspci:
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD/ATI] RS200 Host Bridge (rev 02)
00:01.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RS200/RS250 AGP Bridge
00:02.0 USB controller: ULi Electronics Inc. USB 1.1 Controller (rev 03)
00:06.0 Multimedia audio controller: ULi Electronics Inc. M5451 PCI AC-Link Controller Audio Device (rev 02)
00:07.0 ISA bridge: ULi Electronics Inc. M1533/M1535/M1543 PCI to ISA Bridge [Aladdin IV/V/V+]
00:08.0 Modem: ULi Electronics Inc. M5457 AC'97 Modem Controller
00:0a.0 CardBus bridge: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller
00:0c.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
00:10.0 IDE interface: ULi Electronics Inc. M5229 IDE (rev c4)
00:11.0 Bridge: ULi Electronics Inc. M7101 Power Management Controller [PMU]
00:12.0 Ethernet controller: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller
01:05.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RS200M [Radeon IGP 330M/340M/345M/350M]

lshw -C network:
  *-network
       description: Ethernet interface
       product: DP83815 (MacPhyter) Ethernet Controller
       vendor: National Semiconductor Corporation
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 00
       serial: 00:0b:cd:a6:d0:94
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii fibre 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=natsemi driverversion=2.1 duplex=full ip=192.168.1.105 latency=90 link=yes maxlatency=52 mingnt=11 multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:10 ioport:2400(size=256) memory:d0009000-d0009fff memory:2c000000-2c00ffff

---

### Post by nerdtron on 2015-03-18
If you have a GUI, don't manually edit /etc/network/interfaces file. This conflicts with the GUI network manager.

First remove the DHCP and Static entries on your /etc/network/interfaces file. Leave if on the default.
```

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

```

What we need to troubleshoot is the GUI network manager. Post the screenshot of your setting here, for both the DHCP and Static settings that your choose. And if the ping on the gateway says "Destination host unreachable", post the output of the following commands:
```
ifconfig
route -n

```

And try to ping other computers on the network just to see that you are successfully connected to the network.

---

### Post by keiko2 on 2015-03-18
Nerdtron, Thanks for the reply.  I returned "interfaces" file to default as you instructed, then edited using gui.  Sadly, the screen capture doesn't work, so photos are attached.  Same outcome:  dhcp, no connection, nothing pingable; static, appears connected, nothing pingable.

dhcp:
[ATTACH=CONFIG]260727[/ATTACH]
eth0      Link encap:Ethernet  HWaddr 00:0b:cd:a6:d0:94  
          inet6 addr: fe80::20b:cdff:fea6:d094/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:24 dropped:0 overruns:0 frame:107
          TX packets:56 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:10284 (10.2 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:480 errors:0 dropped:0 overruns:0 frame:0
          TX packets:480 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:38208 (38.2 KB)  TX bytes:38208 (38.2 KB)

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

static (only captured changed tabs):
[ATTACH=CONFIG]260728[/ATTACH]
eth0      Link encap:Ethernet  HWaddr 00:0b:cd:a6:d0:94  
          inet addr:192.168.1.105  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20b:cdff:fea6:d094/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:216 dropped:0 overruns:0 frame:984
          TX packets:524 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:30528 (30.5 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1301 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1301 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:103840 (103.8 KB)  TX bytes:103840 (103.8 KB)

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

---

### Post by nerdtron on 2015-03-19
DHCP is weird since it can't get any IP from the router.

Static IP looks good, and route is good too.

BTW, I can't view your DHCP shots, the pic have been resized.


Anyway, need to check the obvious solutions here. Is your network cable connected to the switch/router? No matter settings you do, if you can't ping any other PC on your network you probably not connected.
Things to check next:
1. Try a different computer and used the same LAN cable, see if it is able to get an IP. If not, then it is not a problem on the OS.
2. Does the router still have DHCP leases available? Is your static IP not conflict with other PC? Is your network IP correct?
3. Is you MAC Address registered to the network? probably a network policy disables unauthorized MAC addresses to get any IP from the network.

---

### Post by keiko2 on 2015-03-19
I found that print screen does work, I just didn't know where the files were going. I've attached a new bunch of dhcp screenshots.  Since yesterday, I've reinstalled Lubuntu to be sure I have a clean start.
[ATTACH=CONFIG]260752[/ATTACH]

1. Tried my Windows LT on the same LAN cable and it got an IP address.
2. The router has plenty of leases available. The new static IP (192.168.1.120) isn't in conflict with other machines. My network IP is correct.
3. At the router, I can manually assign IPs to specific MAC addresses, which I've done.  All other machines have obtained IPs with no such specific assigments (albeit over wireless).
The attached router shots show a windows lt connected via dhcp using the same ethernet wire; the lubuntu lt connected via static.
[ATTACH=CONFIG]260775[/ATTACH][ATTACH=CONFIG]260776[/ATTACH]

Here's ipconfig from the windows lt while on ethernet connection:

Ethernet adapter Ethernet 2:

   Connection-specific DNS Suffix  . : 
   Description . . . . . . . . . . . : ASIX AX88179 USB 3.0 to Gigabit Ethernet Adapter
   Physical Address. . . . . . . . . : 00-23-55-1C-06-34
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes
   Link-local IPv6 Address . . . . . : fe80::59f0:7f5c:8342:4bb5%11(Preferred) 
   IPv4 Address. . . . . . . . . . . : 192.168.1.100(Preferred) 
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Lease Obtained. . . . . . . . . . : Friday, March 20, 2015 2:23:22 PM
   Lease Expires . . . . . . . . . . : Saturday, March 21, 2015 2:23:22 PM
   Default Gateway . . . . . . . . . : 192.168.1.1
   DHCP Server . . . . . . . . . . . : 192.168.1.1
   DHCPv6 IAID . . . . . . . . . . . : 335553365
   DHCPv6 Client DUID. . . . . . . . : 00-01-00-01-1A-2D-88-B0-00-80-8A-8E-1F-1E
   DNS Servers . . . . . . . . . . . : 192.168.1.1
   NetBIOS over Tcpip. . . . . . . . : Enabled

---

### Post by nerdtron on 2015-03-20
Really weird situation. I'm not sure of any further steps. :(

Have you tried booting into the Live mode of another Ubuntu version and see if it gets an IP address?

---

### Post by keiko2 on 2015-03-20
I haven't tried live, but have previously tried installations of Lubuntu(alternate), Puppy, and Precise Puppy.  Sigh.  I guess I could try one of the Puppies live.  Sigh.  Again.

---

### Post by nerdtron on 2015-03-20
Have you tired Linux Mint?

Oh... I remember another problem before..

Try deleting the persistent udev file. (first, use the GUI network tool and set it to DHCP mode).
Then from the terminal:
```
 sudo rm /etc/udev/rule.d/70-persistent-net.rules 
```

Reboot and see it there is an improvement.

That's my last resort. running out of ideas here.

---

### Post by keiko2 on 2015-03-20
Removing the file didn't help.  Today I tried installing Linux Mint.  The install sat like a lump after "automatic boot in 10, 9, 8, 7, 6, 5, 4, 3, 2, 1 seconds."  So sad.  Thanks for the effort, Nerdtron.  Maybe someone else will run across my pitious situation and offer something up.

---

