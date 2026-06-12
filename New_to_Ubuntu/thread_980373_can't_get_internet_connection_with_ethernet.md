---
title: "can't get internet connection with ethernet"
date: 2008-11-12
forum: New to Ubuntu
---

### Post by jadu on 2008-11-12
Hello all,
I can't get my internet to connect with Ethernet. Maybe some one can give me some advice? I'll try to answer all the recomended questions from this post:
[http://ubuntuforums.org/showpost.php?p=5024425&postcount=1](http://ubuntuforums.org/showpost.php?p=5024425&postcount=1)

I used ubuntu for a few months with wireless and it mostly worked fine. But now I'm at a different house, in the United States, using a wired connection. I'm using an ethernet cable connected to an adsl modem (I think that's what it is).  The modem says "RCA" and "digital/broadband". It's through Comcast. My Ubuntu is 8.04 (hardy), with Gnome 2.22.3. The computer is a Compaq Presario laptop. 
The internet works fine with the other computer in this house. The comcast help line said all I would need to do is just plug in the ethernet and it would work.
Before I plug in the ethernet cable, it shows the two computers with an exclamation mark on the top. When I plug it in, it shows the swirling colors, like "thinking", for about a minute. In that time, I can get some internet pages. Then it goes to the two computers with no exclamation mark on the top, and internet stops working. If I click on that icon, it shows "wired connection" as checked. 

If I run lspci, lsusb, and lshw -classnetwork, I get these responses:

eric@eric-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
06:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
08:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

eric@eric-laptop:~$ lsusb
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

eric@eric-laptop:~$ lshw -classnetwork
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

If I look at the system log, it shows me this:
Nov 12 19:21:48 eric-laptop kernel: [  123.425680] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Nov 12 19:21:48 eric-laptop kernel: [  123.426154] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Nov 12 19:21:48 eric-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Nov 12 19:21:51 eric-laptop kernel: [  124.706735] NET: Registered protocol family 17
Nov 12 19:22:32 eric-laptop dhcdbd: Unrequested down ?:3


I double boot with windows, but it isn't working in windows either. And I can't figure out why unfortunately, because my windows is in Korean, and I don't read Korean very well.

Any advice would be appreciated. I posted in the absolute beginner secion because I am a beginner, with ubuntu and computers in general. So please, if you write an explanation, assume that I have no knowledge!
thanks

---

### Post by jadu on 2008-11-12
I thought I'd add, in Microsoft windows, it shows the connection as working, but then mozilla doesn't work with it.

---

### Post by dsurge on 2008-11-12
do you get an ip return with ifconfig?

---

### Post by louieb on 2008-11-12
Try to get an IP address from the modem.```
sudo dhclient
```
If you get one take a look at how long the lease is.

---

### Post by jadu on 2008-11-13
thanks for your responses. I don't know what an IP return is, but when I type "ipconfig" in a terminal it gives me:


eric@eric-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:d4:9e:77:62  
          inet6 addr: fe80::216:d4ff:fe9e:7762/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1440 errors:0 dropped:0 overruns:0 frame:0
          TX packets:117 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:91338 (89.1 KB)  TX bytes:13717 (13.3 KB)
          Interrupt:17 Base address:0x2000 

eth0:avahi Link encap:Ethernet  HWaddr 00:16:d4:9e:77:62  
          inet addr:169.254.7.95  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:17 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:27 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2411 (2.3 KB)  TX bytes:2411 (2.3 KB)

wlan0     Link encap:Ethernet  HWaddr 00:14:a5:df:cc:84  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0:avahi Link encap:Ethernet  HWaddr 00:14:a5:df:cc:84  
          inet addr:169.254.9.192  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

wmaster0  Link encap:UNSPEC  HWaddr 00-14-A5-DF-CC-84-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


**
and if I type sudo dhclient, it gives me this. I don't know how long the lease is, it says "no working lease". Any ideas?


eric@eric-laptop:~$ sudo dhclient
There is already a pid file /var/run/dhclient.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:14:a5:df:cc:84
Sending on   LPF/wlan0/00:14:a5:df:cc:84
Listening on LPF/wmaster0/
Sending on   LPF/wmaster0/
Listening on LPF/eth0/00:16:d4:9e:77:62
Sending on   LPF/eth0/00:16:d4:9e:77:62
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 7
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

### Post by louieb on 2008-11-13
looks like dhclient is trying to get and IP address from a wireless card wlan0 and a NIC eth0 if either had been successful you would have seen something like this
> DHCPACK of 10.0.0.7 from 10.0.0.1
bound to 10.0.0.7 -- renewal in 920860631 seconds.
also looks like Ubuntu see your NIC. but for some reason the NIC is not getting a response from the modem. 

I supect the NIC has gone bad. Had that happen on my laptop. ( cat got mad and pissed on it, cats are evil:evil: ) I have to use a pcmcia network card when I need to use a wired network.  

Guess your looking at getting a network card or maybe get a wireless router. 

BTW ifconfig displays the IP address on the second line and looks something like ths.

> eth1      Link encap:Ethernet  HWaddr 00:07:e9:78:b3:80  
          [COLOR=Red]inet addr:10.0.0.7 [/COLOR] Bcast:10.0.0.255  Mask:255.255.255.0
....

---

### Post by newbee70 on 2008-11-13
Hello all,
I can't get my internet to connect with Ethernet. Maybe some one can give me some advice? I'll try to answer all the recomended questions from this post:

Question: what does it say if you left click on your network manager "the computer icon" in the upper toolbar?

---

### Post by jadu on 2008-11-14
Hello, 

If I left click on the "computer icon" in the upper toolbar, it shows me this:

"
[checked] wired network 

wireless network
[another in the neighborhood, not mine]

connect to other wireless network
create new wireless network

connect to 802.1X  protected wired network
manual configuration
"

If  I click on "manual configuration", it brings me to the "network settings" dialog box. 

If I click on "connect to 802.1X protected wired network", it opens a dialog box that asks me for network name, EAP method (I don't know what that is), phase2 Type (ditto), identity (ditto) , etc.  Would I have to find this information from my ISP and connect in this way?
----
And about louieb's suggesstion, thank you. But could it also be that windows is turning off the network card before shutting down, like it describes in the below post? Or is that something different? (It's hard for me to check it myself, because my windows is in a language I don't speak very well...)

"
8. Do you dual-boot with Windows? If yes - read this:
From: [http://support.microsoft.com/kb/910389](http://support.microsoft.com/kb/910389)
Quote:
If the network adapter supports a power management option, the following check box may be selected:

Allow the computer to turn off this device to save power
If the network adapter supports this option, it is available on the Power Management tab of the network adapter properties dialog box. To resolve this issue, disable this option on the Power Management tab. For more information about how to disable this power management option, click the following article number to view the article in the Microsoft Knowledge Base:

If you have this power-save function on in Windows, it will turn the network card off before shutting down, leaving it unavailable to Ubuntu. So check that in Windows, and make sure you don't have power-save on.
"

---

### Post by jadu on 2008-11-16
bump!
thanks for the earlier great response. but maybe someone could answer this last question I have on this? thanks!

---

