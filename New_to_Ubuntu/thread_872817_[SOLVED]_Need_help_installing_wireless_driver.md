---
title: "[SOLVED] Need help installing wireless driver"
date: 2008-07-28
forum: New to Ubuntu
---

### Post by Haioko on 2008-07-28
Hi there. I need some help to understand the basic fundamentals of Ubuntu. I don't understand ANY of the terminal stuff and I'm totally confused. All I want to do is install a driver for my wireless adapter but I have no clue how to go about it.

Please help.

---

### Post by halitech on 2008-07-28
is it an internal wireless card or an external USB devide?

open a terminal (Applications - accessories - terminal) and type in
```
lsusb
```
and
```
lspci
```
then copy and paste the info back here

---

### Post by dew5 on 2008-07-28
hey mate

try the solution on [https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT73](https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT73) it may help.

dew

---

### Post by dew5 on 2008-07-28
oh to open terminal is easy

go
Application>accessories>Terminal

go hard

dew

---

### Post by halitech on 2008-07-28
> **dew5 said:**
> hey mate

try the solution on [https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT73](https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT73) it may help.

dew

just out of curiousity, why direct him to a site about a specific card without knowing what card he has? might just end up causing more issues then he already has

---

### Post by Haioko on 2008-07-28
It's an external USB device.

It's a Netgear WG111 v2

scott@scott-desktop:~$ lsusb
Bus 002 Device 006: ID 0781:7100 SanDisk Corp. 
Bus 002 Device 004: ID 0846:6a00 NetGear, Inc. WG111 WiFi (v2)
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 04f3:02f0 Elan Microelectronics Corp. 
Bus 001 Device 001: ID 0000:0000  

scott@scott-desktop:~$ lspci
00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev a2)
00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev a3)
00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev a3)
00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2)
00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
05:00.0 VGA compatible controller: ATI Technologies Inc Unknown device 95c5
05:00.1 Audio device: ATI Technologies Inc Unknown device aa28

---

### Post by halitech on 2008-07-28
looks like this one
[color=red]Bus 002 Device 004: ID 0846:6a00 NetGear, Inc. WG111 WiFi (v2)[/color]

is your USB wireless device. Good sign that Ubuntu is seeing it.

Did a search and it looks like it should work out of the box without doing anything special. in the terminal, do
```
ifconfig
``` and see what that tells us

---

### Post by Haioko on 2008-07-28
scott@scott-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:01:6C:CF:24:82  
          inet6 addr: fe80::201:6cff:fecf:2482/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:131 errors:0 dropped:0 overruns:0 frame:0
          TX packets:57 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:33122 (32.3 KB)  TX bytes:7269 (7.0 KB)
          Interrupt:19 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:96 errors:0 dropped:0 overruns:0 frame:0
          TX packets:96 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8288 (8.0 KB)  TX bytes:8288 (8.0 KB)

wlan0     Link encap:Ethernet  HWaddr 00:14:6C:B2:6B:88  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0:ava Link encap:Ethernet  HWaddr 00:14:6C:B2:6B:88  
          inet addr:169.254.7.87  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

wmaster0  Link encap:UNSPEC  HWaddr 00-14-6C-B2-6B-88-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

---

### Post by dew5 on 2008-07-28
ok thanks for the heads up.

dew

---

### Post by Haioko on 2008-07-28
Sorry about taking my time. I'm having to switch between two computers. THis one and the one with ubuntu installed and I need to copy and paste the data onto my flash drive.

---

### Post by halitech on 2008-07-28
ok, good sign, network manager is seeing the connection

```
wlan0:ava Link encap:Ethernet HWaddr 00:14:6C:B2:6B:88
inet addr:169.254.7.87 Bcast:169.254.255.255 Mask:255.255.0.0
UP BROADCAST MULTICAST MTU:1500 Metric:1

```
but its not giving you an IP address. Do you have any kind of encryption on your router?

---

### Post by Haioko on 2008-07-28
Yeah I have WEP.

---

### Post by halitech on 2008-07-28
ok, if you click on your network manager, do you see your wireless connection?

---

### Post by Haioko on 2008-07-28
I'm lost, sorry.

---

### Post by halitech on 2008-07-28
ok, go to System - Administration - Network

that should list your connections and (cross your fingers) allow you to change the settings on the wireless connection

---

### Post by Haioko on 2008-07-28
I see three connections. A wireless one, a wired one and a modem one. I just clicked on Network in the admin bar

Yeah I can change the settings.

---

### Post by halitech on 2008-07-28
ok, I don't have a wireless connection on my desktop but there should be an option about security when you go to configure the wireless connection, select WEP and put in your passcode. Then it should connect and if you do an ifconfig again, it should give you a new IP address

---

### Post by Haioko on 2008-07-28
When I do ifconfig it gives me an address. But it's still not connecting to the net. When I run firefox it just tells me that it can't find the web address.

I've added the IP and gatenet address manually from the router admin panel. But it's still not working

---

### Post by halitech on 2008-07-28
try this
```
sudo dhclient wlan0
``` and then ```
ifconfig
``` and check the IP address.

was the IP address still 169.x.x.x?

---

### Post by Haioko on 2008-07-28
No. It's 77.97.39.10

---

### Post by halitech on 2008-07-28
I thought you were using a router? 77.97.39.10 is usually an IP assigned to the outside world

---

### Post by halitech on 2008-07-28
if you assigned the IP from the router that the router is getting, that won't work as your computer is behind the router and not connected to the internet directly. You need your computer to have an IP of 192.168.x.x which should be assigned by your router

---

### Post by Haioko on 2008-07-28
Ahhh. Yes. It's 192.168.1.1

---

### Post by halitech on 2008-07-28
> **Haioko said:**
> Ahhh. Yes. It's 192.168.1.1

this is your routers IP address?

---

### Post by Haioko on 2008-07-28
I assume so.

LAN IP Setup
 
LAN TCP/IP Setup
IP Address 	192.168.1.1
IP Subnet Mask 	255.255.255.0 

Thats what it says on my router's admin panel.

---

### Post by Haioko on 2008-07-28
It's either 192.168.1.0, 192.168.1.1 or 192.168.1.2.

I'm assuming that 192.168.1.0 Is the router. 192.168.1.1 is this computer and 192.168.1.2 is the ubuntu computer?

---

### Post by halitech on 2008-07-28
ok, so 192.168.1.1 is your router and you would use that for the gateway but you need to figure out what IP address to use for the wireless. It will probably be something like 192.168.1.105 (105 could be anything, will depend on how the router is set up)

if you go back into the network and click on properties, under the Connection settings section, where it says Configuration, do you have that on Automatic configuration (DHCP)?

---

### Post by Haioko on 2008-07-28
No I have it on Static IP address.

---

### Post by halitech on 2008-07-28
change it to Auto (DHCP) and see if it will get a connection

---

### Post by Haioko on 2008-07-28
Nope. When I had it on static address with the Ip address in it seemed as if it was looking for the site. But with automatic on it just come up server cannot be found, straight away.

---

### Post by halitech on 2008-07-28
ok, when it was on DHCP, did you do the ```
sudo dhclient wlan0
``` to see if it was giving you an IP address?

---

### Post by Haioko on 2008-07-28
scott@scott-desktop:~$ sudo dhclient wlan0
[sudo] password for scott:
There is already a pid file /var/run/dhclient.pid with pid 7443
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:14:6c:b2:6b:88
Sending on   LPF/wlan0/00:14:6c:b2:6b:88
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

Thats what I got

---

### Post by halitech on 2008-07-28
did you disable the wired connection? it may be interferring with the wireless

---

### Post by Haioko on 2008-07-28
I set it to roaming. Is thats what you mean.

---

### Post by halitech on 2008-07-28
no, if you uncheck it, that will disable the connection. Just keep the wireless connection running

---

### Post by Haioko on 2008-07-28
Ok. Done. But the internet still isn't working...

---

### Post by halitech on 2008-07-28
ok, post the results of```
iwconfig
```

---

### Post by Haioko on 2008-07-28
scott@scott-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"NETGEAR"  
          Mode:Managed  Frequency:2.447 GHz  Access Point: 00:90:4C:7E:00:6E   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by halitech on 2008-07-28
ok, so we have a connection to the router, now we need to get an IP address from it

run this again
```
sudo dhclient wlan0
```

---

### Post by halitech on 2008-07-28
wait a minute, I see a problem

> Link Quality:0 Signal level:0 Noise level:0

its not getting a signal from the router, the link quality should be higher then 0

---

### Post by Haioko on 2008-07-28
scott@scott-desktop:~$ sudo dhclient wlan0
[sudo] password for scott:
There is already a pid file /var/run/dhclient.pid with pid 11137
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:14:6c:b2:6b:88
Sending on   LPF/wlan0/00:14:6c:b2:6b:88
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

Pretty much the same as before.

---

### Post by Haioko on 2008-07-28
But the router is working fine.

I had another computer attatched to the router with that USB device and it worked fine. (Mind you It was a windows OS and the driver was installed)

---

### Post by halitech on 2008-07-28
ok, lets try something else. lets do a reboot on the computer. Also, can we disable the WEP on the router for now? see if it is a WEP issue or connection issue?

---

### Post by Haioko on 2008-07-28
Ok, computer had been rebooted and WEP has been disabled.

---

### Post by halitech on 2008-07-28
ok, do the ```
ifconfig
``` now and ```
sudo dhclient wlan0
```

---

### Post by Haioko on 2008-07-28
scott@scott-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:01:6C:CF:24:82  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:16 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:19 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1679 (1.6 KB)  TX bytes:1679 (1.6 KB)

wlan0     Link encap:Ethernet  HWaddr 00:14:6C:B2:6B:88  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0:ava Link encap:Ethernet  HWaddr 00:14:6C:B2:6B:88  
          inet addr:169.254.7.87  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

wmaster0  Link encap:UNSPEC  HWaddr 00-14-6C-B2-6B-88-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

scott@scott-desktop:~$ sudo dhclient wlan0
[sudo] password for scott:
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:14:6c:b2:6b:88
Sending on   LPF/wlan0/00:14:6c:b2:6b:88
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
scott@scott-desktop:~$

---

### Post by halitech on 2008-07-28
I'm at a loss here. from what I can see this should be working so for it not to be working it's 1 of a few things.

1. router has the wireless turned off
2. driver for the wireless isn't installed properly
3. the MAC address has been assigned to a deny state in the router preventing it from getting an IP

---

### Post by Haioko on 2008-07-28
What about trying to install the driver for the wireless USB device? Can I do that on ubuntu?

---

### Post by halitech on 2008-07-28
we are working on the wireless and it shouldn't need the windows drivers to get it to work

try this
```
sudo iwlist wlan0 scan
``` and post the info back here

---

### Post by Haioko on 2008-07-28
It's working now. I'm actually posting this from the computer.

I changed the wireless setting to static ip and put in 192.168.1.2 as this computer's ip and the gateway to 192.168.1.1 and I changed the security from WEP to WPA. And entered the passcode and it now works... Thanks for your help. I really appreciate it.

---

### Post by halitech on 2008-07-28
glad we finally got it working :)

I would almost say it was a combination of the wrong security setting and your router isn't set up to give out IP addresses. 

Since it is working, mark this thread solved so others will know its fixed :)

---

