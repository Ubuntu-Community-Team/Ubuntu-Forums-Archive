---
title: "ethernet recognition"
date: 2008-09-19
forum: New to Ubuntu
---

### Post by m-i on 2008-09-19
Hi, 

I'm having problems with ubuntu recognizing ethernet connections. When I go to manual configuration network settings window only the point-to-point connection option pops-up.  I have a dell inspiron 4000 laptop that had a great wireless connection  when using Windows. It's now hooked to a router with a ethernet cord and Ubuntu's not accessing it. 

I've read and tried some of the suggestions given to other people who listed similar problems on the forum, but I'm still stuck. 

please help!!
[email]izbeing@yahoo.com[/email]



Here are the things I tried and the results: 

system > admin > network


**[COLOR="DarkOliveGreen"]ifconfig[/COLOR]**

lo        Link encap:Local Loopback  

          inet addr:127.0.0.1  Mask:255.0.0.0

          inet6 addr: ::1/128 Scope:Host

          UP LOOPBACK RUNNING  MTU:16436  Metric:1

          RX packets:2686 errors:0 dropped:0 overruns:0 frame:0

          TX packets:2686 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0 

          RX bytes:136580 (133.3 KB)  TX bytes:136580 (133.3 KB)

**[COLOR="DarkOliveGreen"]ifconfig eth1[/COLOR]**[COLOR="DarkOliveGreen"]ifconfig eth1[/COLOR]

**[COLOR="DarkOliveGreen"]ifconfig eth2[/COLOR]****ifconfig eth0**

eth0: error fetching interface information: Device not found

marie-isabelle@marie-isabelle-laptop:~$ ifconfig eth1

eth1: error fetching interface information: Device not found


**[COLOR="DarkOliveGreen"]lspci[/COLOR]**
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)

00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)

00:03.0 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller

00:03.1 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller

00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)

00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)

00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)

00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 03)

00:08.0 Multimedia audio controller: ESS Technology ES1983S Maestro-3i PCI Audio Accelerator (rev 10)

00:10.0 Communication controller: Agere Systems WinModem 56k (rev 01)

01:00.0 VGA compatible controller: ATI Technologies Inc Rage Mobility M3 AGP 2x (rev 02)


**[COLOR="DarkOliveGreen"]sudo ifconfig[/COLOR]**
lo        Link encap:Local Loopback  

          inet addr:127.0.0.1  Mask:255.0.0.0

          inet6 addr: ::1/128 Scope:Host

          UP LOOPBACK RUNNING  MTU:16436  Metric:1

          RX packets:2686 errors:0 dropped:0 overruns:0 frame:0

          TX packets:2686 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0 

          RX bytes:136580 (133.3 KB)  TX bytes:136580 (133.3 KB)



**[COLOR="DarkOliveGreen"]sudo apt-get install dhcp3 server[/COLOR]**
Reading package lists... Done

Building dependency tree       

Reading state information... Done

E: Couldn't find package dhcp3


**[COLOR="DarkOliveGreen"]sudo lshew &#8211; C network[/COLOR]**
sudo: lshew: command not found


**[COLOR="DarkOliveGreen"]sudo dhclient eth0[/COLOR]**
Internet Systems Consortium DHCP Client V3.0.6

Copyright 2004-2007 Internet Systems Consortium.

All rights reserved.

For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)



SIOCSIFADDR: No such device

eth0: ERROR while getting interface flags: No such device

eth0: ERROR while getting interface flags: No such device

Bind socket to interface: No such device




**[COLOR="DarkOliveGreen"]gksugedit/etc/network/interfaces[/COLOR]**
bash: gksugedit/etc/network/interfaces: No such file or directory



**[COLOR="DarkOliveGreen"]ping 192.168.0.0[/COLOR]**
 the address cannot be found please enter a valid network address and try again


**[COLOR="DarkOliveGreen"]ping 192.168.0.1[/COLOR]**
Bytes	Source	Seq	Time	Units

Time minimum:	0.00 ms

Time average:	0.00 ms

Time maximum:	0.00 ms

Packets transmitted:	0

Packets received:	0

Successful packets:	0%


**[COLOR="DarkOliveGreen"]lshw &#8211; C network[/COLOR]**
Hardware Lister (lshw) - B.02.12.01

usage: lshw [-format] [-options ...]

       lshw -version



	-version        print program version (B.02.12.01)



format can be

	-html           output hardware tree as HTML

	-xml            output hardware tree as XML

	-short          output hardware paths

	-businfo        output bus information



options can be

	-class CLASS    only show a certain class of hardware

	-C CLASS        same as '-class CLASS'

	-disable TEST   disable a test (like pci, isapnp, cpuid, etc. )

	-enable TEST    enable a test (like pci, isapnp, cpuid, etc. )

	-quiet          don't display status

	-sanitize       sanitize output (remove sensitive information like serial numbers, etc.)



**[COLOR="DarkOliveGreen"]C: \ >ipconfig/all[/COLOR]**
bash: ipconfig/all: No such file or directory


try assigning the eth0 an ip one highter than the highest XP box, with the same DNS and Gatewa y address to see if you have internet
have no idea how to do this

system > network settings > devices
Network device:	lo

Hardware address:	Loopback

IP address:	127.0.0.1

Netmask:	255.0.0.0

Broadcast:	 

Multicast:	Disabled

MTU:	16436

Link speed:	 

State:	Active

Transmitted packets:	2766

Transmission errors:	0

Received packets:	2766

Reception errors:	0

Collisions:	0

---

### Post by zvacet on 2008-09-19
I don´t use wireless,so I´m not an expert but it look like you need driver for your wierless card.Look [here]("https://help.ubuntu.com/community/WifiDocs/WiFiHowTo") for more information.

---

### Post by El Conquistador on 2008-09-19
have you tried

ifconfig eth0 up

this will "initilize" your device.

---

### Post by m-i on 2008-09-22
Thanks for replying!

I tried ifconfig eth0 up and ifconfig eth1 up and got the "device not found" answer. 

I also tried the following today.... 


[COLOR="DarkOliveGreen"]**[SIZE="5"] ifconfig inet addr [/SIZE]**[/COLOR]
addr: Unknown host 
ifconfig: `--help' gives usage information.


[SIZE="5"]**[COLOR="DarkOliveGreen"]ifconfig --help[/COLOR]**[/SIZE] 
Usage: 
  ifconfig [-a] [-v] [-s] <interface> [[<AF>] <address>] 
  [add <address>[/<prefixlen>]] 
  [del <address>[/<prefixlen>]] 
  [[-]broadcast [<address>]]  [[-]pointopoint [<address>]] 
  [netmask <address>]  [dstaddr <address>]  [tunnel <address>] 
  [outfill <NN>] [keepalive <NN>] 
  [hw <HW> <address>]  [metric <NN>]  [mtu <NN>] 
  [[-]trailers]  [[-]arp]  [[-]allmulti] 
  [multicast]  [[-]promisc] 
  [mem_start <NN>]  [io_addr <NN>]  [irq <NN>]  [media <type>] 
  [txqueuelen <NN>] 
  [[-]dynamic] 
  [up|down] ... 
 
  <HW>=Hardware Type. 
  List of possible hardware types: 
    loop (Local Loopback) slip (Serial Line IP) cslip (VJ Serial Line IP)  
    slip6 (6-bit Serial Line IP) cslip6 (VJ 6-bit Serial Line IP) adaptive (Adaptive Serial Line IP)  
    strip (Metricom Starmode IP) ash (Ash) ether (Ethernet)  
    tr (16/4 Mbps Token Ring) tr (16/4 Mbps Token Ring (New)) ax25 (AMPR AX.25)  
    netrom (AMPR NET/ROM) rose (AMPR ROSE) tunnel (IPIP Tunnel)  
    ppp (Point-to-Point Protocol) hdlc ((Cisco)-HDLC) lapb (LAPB)  
    arcnet (ARCnet) dlci (Frame Relay DLCI) frad (Frame Relay Access Device)  
    sit (IPv6-in-IPv4) fddi (Fiber Distributed Data Interface) hippi (HIPPI)  
    irda (IrLAP) ec (Econet) x25 (generic X.25)  
    eui64 (Generic EUI-64)  
  <AF>=Address family. Default: inet 
  List of possible address families: 
    unix (UNIX Domain) inet (DARPA Internet) inet6 (IPv6)  
    ax25 (AMPR AX.25) netrom (AMPR NET/ROM) rose (AMPR ROSE)  
    ipx (Novell IPX) ddp (Appletalk DDP) ec (Econet)  
    ash (Ash) x25 (CCITT X.25)

---

### Post by jemate18 on 2008-09-22
Is your ethernet built in on board? or discrete?

If on-board, your ubuntu is having problem on recognizing it..  what model is your ethernet card. or board?

---

### Post by m-i on 2008-09-29
I have no idea what model or type of ethernet card I have... 

should I just try to change the hardware and see if that works? is that someone i would likely be able to figure out how to do myself?

also, i had previously tried buying a wireless notebook adapter and the software wasn't compatable with ubuntu. is there some type of wireless adapter that's software works with the ubuntu os? (I tried the third-party software input window and it wouldn't work). 

thanks!!!!!!

---

