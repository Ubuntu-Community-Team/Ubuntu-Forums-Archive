---
title: "[SOLVED] aMule configuration"
date: 2008-05-18
forum: New to Ubuntu
---

### Post by Daveg4otu on 2008-05-18
Just installed aMule P2p application

Thisis being used in conjuction with Ubuntu 8.04  and a Netgear DG834g router (with two PCs copnnected - this one and one on WinXP.

Trying to configure the router Firewall to get  a HighID connection.

I have followed the instructions in the Wiki - entering the IP as 192 168 0 1 as that is what shows as the IP in the router config page.

The best this gives is a lowID ( two yellow arrows ) with a warning that I am "behind a Firewall or Router"

How to get around this please

Edit - the" test port application " says
[I]
Error: TCP port 4662 is unavailable. Make sure your firewall or router is allowing/forwarding this TCP service port and your ED2K client is running (i.e. aMule, eMule).

Detailed Error Message
TCP Error 110 Connection refused

Explanation
The connection timed out, meaning the port is being blocked or incorrectly forwarded by a firewall or your computer is turned off :) [/I]

---

### Post by Monicker on 2008-05-18
The error about port 4663 pretty much tells it all.  How are you connected to the internet?

Computer -> Router -> Cable modem -> Internet

The above is a common setup where NAT would be in used at the router.  It would require port forwarding from the router the ip address of the specific computer. If your network connectivity is setup differently, please give us the details.

---

### Post by Daveg4otu on 2008-05-18
Hi - yes the setup is  2 PCs- both to the Netgear router(DG834G) -> internet

[COLOR="Blue"]require port forwarding from the router[/COLOR]

I had more or less figured out that was what was needed - can't work out how to do it 
]
This is what the Router  page shows

[COLOR="Blue"]Account Name  	
Firmware Version 	V4.01.06
 
ADSL Port
MAC Address 	00:18:4d:af:17:63
IP Address 	92.4.222.48
Network Type 	PPPoA
IP Subnet Mask 	255.255.255.255
Gateway IP Address 	92.4.192.1
Domain Name Server 	92.31.241.20
92.31.241.21
 
LAN Port
MAC Address 	00:18:4d:af:17:62
IP Address 	192.168.0.1
DHCP 	On
IP Subnet Mask 	255.255.255.0
 
Modem
ADSL Firmware Version 	6.01.00.12
Modem Status 	Connected
DownStream Connection Speed 	5088 kbps
UpStream Connection Speed 	448 kbps
VPI 	0
VCI 	38
 
Wireless Port
Name (SSID) 	NETGEAR
Region 	Europe
Channel 	11
Wireless AP 	Disabled
Broadcast Name 	Enabled
  [/COLOR]

And the INBOUND FW rules
[COLOR="Blue"]
 	1 	  	aMule3 	ALLOW always 	192.168.0.1 	Any 	Always
	2 		aMule2 	ALLOW always 	192.168.0.1 	Any 	Always
	3 		aMule1 	ALLOW always 	192.168.0.1 	Any 	Never[/COLOR]

---

### Post by Monicker on 2008-05-18
I think you just need to modify your rules slightly. 192.168.0.1 should be the ip address of the router.  Change that to the ip address of the computer which is running amule.

---

### Post by Daveg4otu on 2008-05-18
Have checked via ifconfig - this is what I get  so have set the IP to 192.168.0.3 ..Still same  lowID - best speed showing about 10 kb/s on a test download.

eth0      Link encap:Ethernet  HWaddr 00:0c:76:8c:1a:d6  
          inet addr:192.168.0.3  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:76ff:fe8c:1ad6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:67735 errors:0 dropped:0 overruns:0 frame:0
          TX packets:64927 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:45035538 (42.9 MB)  TX bytes:6234658 (5.9 MB)
          Interrupt:18 Base address:0x4d00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1134 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1134 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:56700 (55.3 KB)  TX bytes:56700 (55.3 KB)

---

### Post by Daveg4otu on 2008-05-18
Figured this one out in the end - problem related to the default port 4662- seemed it may be blocked on AOL ...added (totally at random )to 5050(services and FW )  and - wonder of wonders - everything started working.

---

