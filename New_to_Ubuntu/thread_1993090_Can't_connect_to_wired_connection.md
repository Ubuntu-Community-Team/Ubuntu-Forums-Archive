---
title: "Can't connect to wired connection"
date: 2012-06-01
forum: New to Ubuntu
---

### Post by KeithandStacie on 2012-06-01
Alright, So I downloaded Ubuntu 12.04 and everything is great except I can't connect to a wired connection via my Ethernet switch.
When I connect my computer to the cable modem directly it works fine, I just can't go modem-switch-computer. My other windows machine on the switch is running fine. The box says it supports linux. The computer does know something is plugged in though, as when I plug it in it tries to connect for a few minutes then gives up. Any help would be greatly appreciated, Thanks!

---

### Post by roton on 2012-06-01
Type ifconfig in the terminal and paste what it says (when the lan cable is connected).

Also, you can try going to network connections and setting a static ip for your computer... just in case the waiting before it fails is because it can't negotiate an ip address.

---

### Post by KeithandStacie on 2012-06-01
> **roton said:**
> Type ifconfig in the terminal and paste what it says (when the lan cable is connected).

Also, you can try going to network connections and setting a static ip for your computer... just in case the waiting before it fails is because it can't negotiate an ip address.

Thanks for the quick response, After a reboot its actually telling me it's connected. BUT It still wont do anything internet related. But this is what I got:

ifcokeith@keith-T3604:~$ ifconfig  
 eth0      Link encap:Ethernet  HWaddr 00:19:d1:48:a8:92   
           inet6 addr: fe80::219:d1ff:fe48:a892/64 Scope:Link  
           inet6 addr: 2001:558:6033:f3:581c:a232:47a3:cc09/64 Scope:Global  
           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1  
           RX packets:2424 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:88 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:1000  
           RX bytes:153792 (153.7 KB)  TX bytes:13124 (13.1 KB)  
 

 lo        Link encap:Local Loopback   
           inet addr:127.0.0.1  Mask:255.0.0.0  
           inet6 addr: ::1/128 Scope:Host  
           UP LOOPBACK RUNNING  MTU:16436  Metric:1  
           RX packets:160 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:160 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:0  
           RX bytes:13335 (13.3 KB)  TX bytes:13335 (13.3 KB)

---

### Post by roton on 2012-06-01
So no ipv4 address. Did you try manually setting an ip address?

Do "cat /etc/network/interfaces" in terminal and paste please :p

---

### Post by KeithandStacie on 2012-06-01
> **roton said:**
> So no ipv4 address. Did you try manually setting an ip address?

Do "cat /etc/network/interfaces" in terminal and paste please :p

I haven't tried to set an IP manually yet, I got:
keith@keith-T3604:~$ cat /etc/network/interfaces  
 auto lo  
 iface lo inet loopback

---

### Post by roton on 2012-06-01
type 'sudo gedit /etc/network/interfaces'

Change what's there to this:

```
auto eth0
iface eth0 inet dhcp
```

Save and close.

Then type 'sudo /etc/init.d/networking restart'

Try the wired connection. If it doesn't work change the text back again.

---

### Post by KeithandStacie on 2012-06-01
> **roton said:**
> type 'sudo gedit /etc/network/interfaces'

Change what's there to this:

```
auto eth0
iface eth0 inet dhcp
```Save and close.

Then type 'sudo /etc/init.d/networking restart'

Try the wired connection. If it doesn't work change the text back again.
 
It doesn't work, and I made a mistake... I forgot what it originally was...

---

### Post by steeldriver on 2012-06-01
what it originally was is right there in your post from when you did "cat /etc/network/interfaces", i.e.

```
auto lo  
iface lo inet loopback     

```imho you should be careful about messing with /etc/network/interfaces and/or /etc/init.d/networking in 12.04

the new way of doing things is for everything except the loopback (lo) interface to be handled by the NetworkManager service and configured via /etc/NetworkManager/NetworkManager.conf (and any non-default connection defs in /etc/NetworkManager/system-connections)

NetworkManager *should* be capable of configuring the default wired interface out of the box - and if it doesn't, there's likely something else (drivers, firmware etc.) that needs to be fixed

---

### Post by roton on 2012-06-01
> **KeithandStacie said:**
> It doesn't work, and I made a mistake... I forgot what it originally was...

As steeldriver says, the original text was what you pasted in your reply.
I still think you should go right click on your wired connection (at the top) and then click 'edit connection' so you can define an ipv4 address manually.

---

### Post by KeithandStacie on 2012-06-01
> **steeldriver said:**
> what it originally was is right there in your post from when you did "cat /etc/network/interfaces", i.e.

```
auto lo  
iface lo inet loopback     

```imho you should be careful about messing with /etc/network/interfaces and/or /etc/init.d/networking in 12.04

the new way of doing things is for everything except the loopback (lo) interface to be handled by the NetworkManager service and configured via /etc/NetworkManager/NetworkManager.conf (and any non-default connection defs in /etc/NetworkManager/system-connections)

NetworkManager *should* be capable of configuring the default wired interface out of the box - and if it doesn't, there's likely something else (drivers, firmware etc.) that needs to be fixed

I set it back to what it was. Where would I find the firmware or drivers that I need?

> As steeldriver says, the original text was what you pasted in your reply.
I still think you should go right click on your wired connection (at the  top) and then click 'edit connection' so you can define an ipv4 address  manually.     I have tried to manually configure a connection but I'm unsure where I find my IP, Netmask or Gateway. I have looked at several tutorial but none show where those are found. I'm guessing ifconfig but even then I'm not sure which numbers are what.

Sorry for the trouble, I'm just trying to get this working, Thanks

EDIT: Can I use the Subnet Mask, Default Gateway, and IPv4 Address my Windows Machine is giving me if I'm running on a network switch? I think the IP would be slightly different, Correct?

---

### Post by steeldriver on 2012-06-01
sorry - I missed the part about it working fine direct to the modem - that suggests there is no problem with the firmware or drivers

first thing I would do is

```
sudo service networking stop

```then plug it into the switch again and

```
sudo service network-manager restart

```let it try to connect, and then do

```
nm-tool

```this should spit out its current config which we can look through for obvious red flags

---

### Post by roton on 2012-06-01
> **KeithandStacie said:**
> I have tried to manually configure a connection but I'm unsure where I find my IP, Netmask or Gateway. I have looked at several tutorial but none show where those are found. I'm guessing ifconfig but even then I'm not sure which numbers are what.

Sorry for the trouble, I'm just trying to get this working, Thanks

EDIT: Can I use the Subnet Mask, Default Gateway, and IPv4 Address my Windows Machine is giving me if I'm running on a network switch? I think the IP would be slightly different, Correct?


If you look up near your clock and volume there should be some arrows showing your network status. If you right click there and then go to 'edit connections' you should see a "wired tab". In there you can click on your wired connection and edit the ip etc. It will be added under 'ipv4'.
Yes it will be the same as your Windows machine but change the last digit. So if Windows machine is 192.168.0.2 then use something like 192.168.0.20 (if you have no other devices with that ip). Subnet mask should be 24 and gateway is your router address normally.
No trouble. I just hope you get your answer soon ;)

---

### Post by KeithandStacie on 2012-06-01
> **steeldriver said:**
> sorry - I missed the part about it working fine direct to the modem - that suggests there is no problem with the firmware or drivers

first thing I would do is

```
sudo service networking stop

```then plug it into the switch again and

```
sudo network-manager restart

```let it try to connect, and then do

```
nm-tool

```this should spit out its current config which we can look through for obvious red flags

keith@keith-T3604:~$ sudo service networking stop  
 [sudo] password for keith:  
 stop: Unknown instance:  
 keith@keith-T3604:~$ sudo network-manager restart  
 sudo: network-manager: command not found  
 keith@keith-T3604:~$ nm-tool  
 


 NetworkManager Tool  
 


 State: connected (global)  
 


 - Device: eth0  [Auto Ethernet] ------------------------------------------------  
   Type:              Wired  
   Driver:            e100  
   State:             connected  
   Default:           no  
   HW Address:        00:19:D1:48:A8:92  
 


   Capabilities:  
     Carrier Detect:  yes  
     Speed:           100 Mb/s  
 


   Wired Properties  
     Carrier:         on  
 


   IPv6 Settings: 
     Address:         2001:558:6033:f3:581c:a232:47a3:cc09  
     Prefix:          64  
     Gateway:         fe80::201:5cff:fe22:be41  
 


     Address:         fe80::219:d1ff:fe48:a892  
     Prefix:          64  
     Gateway:         fe80::201:5cff:fe22:be41  
   
     Address:         2001:558:6033:f3:581c:a232:47a3:cc09  
     Prefix:          64  
     Gateway:         ::  
 


     DNS:             2001:558:feed::1  
     DNS:             2001:558:feed::2  
 

That's what I got

> If you look up near your clock and volume there should be some arrows  showing your network status. If you right click there and then go to  'edit connections' you should see a "wired tab". In there you can click  on your wired connection and edit the ip etc. It will be added under  'ipv4'.
Yes it will be the same as your Windows machine but change the last  digit. So if Windows machine is 192.168.0.2 then use something like  192.168.0.20 (if you have no other devices with that ip). Subnet mask  should be 24 and gateway is your router address normally.
No trouble. I just hope you get your answer soonI will try this if the above cannot help solve my problem, Thanks ;)

EDIT: I tried booting Ubuntu straight from a CD to see if it work, Same problem. Don't think it will help but I though I'd post it

---

### Post by steeldriver on 2012-06-01
oops my apologies that restart command should have been

```
sudo **service** network-manager restart
```

regardless, the nm-tool output seems to show you have a non-default (i.e. user defined) connection,  as roton suggests you will need to fix that manually to whatever settings are correct for your subnet - or delete it and let network-manager try to configure it automatically via DHCP

---

### Post by KeithandStacie on 2012-06-01
> **steeldriver said:**
> oops my apologies that restart command should have been

```
sudo **service** network-manager restart
```regardless, the nm-tool output seems to show you have a non-default (i.e. user defined) connection,  as roton suggests you will need to fix that manually to whatever settings are correct for your subnet - or delete it and let network-manager try to configure it automatically via DHCP

It's fine, Sorry about that, I was trying to do what roton suggested but stopped and forgot to reset it, Here is what I got this time:

keith@keith-T3604:~$ sudo service networking stop  
 [sudo] password for keith:  
 stop: Unknown instance:  
 keith@keith-T3604:~$ sudo service network-manager restart  
 network-manager stop/waiting  
 network-manager start/running, process 2551  
 keith@keith-T3604:~$ nm-tool  
 


 NetworkManager Tool  
 


 State: connected (global)  
 


 - Device: eth0  [Wired connection 1] -------------------------------------------  
   Type:              Wired  
   Driver:            e100  
   State:             connected  
   Default:           yes  
   HW Address:        00:19:D1:48:A8:92  
 


   Capabilities:  
     Carrier Detect:  yes  
     Speed:           100 Mb/s  
 


   Wired Properties  
     Carrier:         on  
   
   IPv4 Settings:  
     Address:         192.168.100.11  
     Prefix:          24 (255.255.255.0)  
     Gateway:         192.168.100.1  
 


 


   IPv6 Settings:  
     Address:         fe80::219:d1ff:fe48:a892  
     Prefix:          64  
     Gateway:         fe80::201:5cff:fe22:be41

---

### Post by steeldriver on 2012-06-01
OK so now you have a pretty sensible IPv4 setup - how does that compare to what you see on the windows machine? in particular do they show the same gateway IP (192.168.100.1  )?

the obvious thing missing seems to be nm-tool is not showing any DNS server, that would mean at best you will be able to connect by IP but not by name

you can see if you have basic IP connectivity by

```
ping 8.8.8.8
```

(this is a google DNS server) - if that works we will just need to figure out where your DNS setup has gone wrong

---

### Post by KeithandStacie on 2012-06-01
> **steeldriver said:**
> OK so now you have a pretty sensible IPv4 setup - how does that compare to what you see on the windows machine? in particular do they show the same gateway IP (192.168.100.1  )?

the obvious thing missing seems to be nm-tool is not showing any DNS server, that would mean at best you will be able to connect by IP but not by name

you can see if you have basic IP connectivity by

```
ping 8.8.8.8
```(this is a google DNS server) - if that works we will just need to figure out where your DNS setup has gone wrong

I got:
keith@keith-T3604:~$ ping 8.8.8.8  
 connect: Network is unreachable  
 keith@keith-T3604:~$  
 
Actually, I checked my Windows Machine and I got a completely different IP 68.57.231.51

---

### Post by steeldriver on 2012-06-01
OK then we need to take a step back here - your Ubuntu box seems to be getting a regular private class C address (192.168.xxx.xxx) like you are behind a router with DHCP and NAT, but the Windows box has a public WAN (Comcast?) IP

You could go look at the Windows Network Connections -> Local Area Connection then scroll down to 'Internet Protocol (TCP/IP)' and see if it's set to use static IP and/or specific DNS servers (or Start -> Run -> cmd.exe -> ipconfig /all)

Does your ISP actually provide you with multiple IPs? Have you had more than one connection before or is the switch setup new?

---

### Post by KeithandStacie on 2012-06-01
> **steeldriver said:**
> OK then we need to take a step back here - your Ubuntu box seems to be getting a regular private class C address (192.168.xxx.xxx) like you are behind a router with DHCP and NAT, but the Windows box has a public WAN (Comcast?) IP

You could go look at the Windows Network Connections -> Local Area Connection then scroll down to 'Internet Protocol (TCP/IP)' and see if it's set to use static IP and/or specific DNS servers (or Start -> Run -> cmd.exe -> ipconfig /all)

Does your ISP actually provide you with multiple IPs? Have you had more than one connection before or is the switch setup new?
 
It would be Comcast. The Windows Machine is the only one I had for a long time until recently so I'm not sure if they would provide me with another. The Ubuntu Machine and the switch are both new (Well, I bought the computer used... It originally had Windows Vista and I installed Ubuntu myself). The switch was purchased from an online store earlier this week.


Copyright (c) 2006 Microsoft Corporation.  All rights reserved.

C:\Users\glen>ipconfig/all

Windows IP Configuration

   Host Name . . . . . . . . . . . . : glen-PC
   Primary Dns Suffix  . . . . . . . :
   Node Type . . . . . . . . . . . . : Hybrid
   IP Routing Enabled. . . . . . . . : No
   WINS Proxy Enabled. . . . . . . . : No
   DNS Suffix Search List. . . . . . : hsd1.il.comcast.net.

Ethernet adapter Local Area Connection:

   Connection-specific DNS Suffix  . : hsd1.il.comcast.net.
   Description . . . . . . . . . . . : NVIDIA nForce Networking Controller
   Physical Address. . . . . . . . . : 00-25-11-54-88-9B
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes
   IPv6 Address. . . . . . . . . . . : 2001:558:6033:f3:3d68:3f0a:4cf8:198d(Pref
erred)
   Lease Obtained. . . . . . . . . . : Friday, June 01, 2012 12:03:23 PM
   Lease Expires . . . . . . . . . . : Sunday, June 03, 2012 8:55:59 PM
   Link-local IPv6 Address . . . . . : fe80::bc7a:6cbc:508e:ed84%8(Preferred)
   IPv4 Address. . . . . . . . . . . : 68.57.231.51(Preferred)
   Subnet Mask . . . . . . . . . . . : 255.255.254.0
   Lease Obtained. . . . . . . . . . : Friday, June 01, 2012 7:20:38 AM
   Lease Expires . . . . . . . . . . : Monday, June 04, 2012 6:38:55 AM
   Default Gateway . . . . . . . . . : fe80::201:5cff:fe22:be41%8
                                       68.57.230.1
   DHCP Server . . . . . . . . . . . : 69.252.202.8
   DHCPv6 IAID . . . . . . . . . . . : 201336081
   DHCPv6 Client DUID. . . . . . . . : 00-01-00-01-14-82-2C-48-00-25-11-54-88-9B

   DNS Servers . . . . . . . . . . . : 2001:558:feed::1
                                       2001:558:feed::2
                                       75.75.75.75
                                       75.75.76.76
   NetBIOS over Tcpip. . . . . . . . : Enabled

Tunnel adapter Local Area Connection* 6:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : isatap.hsd1.il.comcast.net.
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes

Tunnel adapter Local Area Connection* 7:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Teredo Tunneling Pseudo-Interface
   Physical Address. . . . . . . . . : 02-00-54-55-4E-01
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes

Tunnel adapter Local Area Connection* 9:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : 6TO4 Adapter
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes

Tunnel adapter Local Area Connection* 10:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . : hsd1.il.comcast.net.
   Description . . . . . . . . . . . : isatap.hsd1.il.comcast.net.
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes

C:\Users\glen>\



EDIT: The switch set-up is new

---

### Post by steeldriver on 2012-06-01
OK well I'm not too familiar with using a switch in that kind of setup 

However one possible issue is that the cable modem may not be accepting your new computer's MAC address (they are usually restricted to 2 or 3 devices via a 'CPE MAC list' - and that might not be getting updated right away). Your ISP may have specific instructions for adding a new device / MAC or it may just be a matter of power cycling the modem until it starts working. Sorry that's about the limit of my knowledge of these things. That's all assuming the ISP allows multiple clients on your service of course.

It's easier with a router instead of a switch - you only need one WAN-side IP / MAC combination and you can throw anything you like on the LAN side.

---

### Post by KeithandStacie on 2012-06-01
> **steeldriver said:**
> OK well I'm not too familiar with using a switch in that kind of setup 

However one possible issue is that the cable modem may not be accepting your new computer's MAC address (they are usually restricted to 2 or 3 devices via a 'CPE MAC list' - and that might not be getting updated right away). Your ISP may have specific instructions for adding a new device / MAC or it may just be a matter of power cycling the modem until it starts working. Sorry that's about the limit of my knowledge of these things. That's all assuming the ISP allows multiple clients on your service of course.

It's easier with a router instead of a switch - you only need one WAN-side IP / MAC combination and you can throw anything you like on the LAN side.
 
Thanks for all the help!:p I will give Comcast a call tomorrow, It seems this is not a problem with Ubuntu after all.

---

### Post by eode on 2012-06-01
I know I'm chiming in late on this, but yup.  You either need to pay comcast for another IP address (monthly fee, usually a few bucks) or buy a router (anywhere from $20 to $120 - [this Rosewill B/G/N router]("http://www.newegg.com/Product/Product.aspx?Item=N82E16833166072") is a pretty good deal, and you get wireless to boot (which you can disable if you don't want).

Good diagnosis, steeldriver.

---

### Post by LinGNUbie on 2012-06-01
Most ISPs are pushing a version of a config file to their modems that disables any devices from receiving an address via dhcp UNTIL the modem registration is complete. I would recommend unhooking the CAT5/6 cable from the ethernet port on the modem, do a power cycle on it, and when the device is fully registered reconnect your cable. This will allow the modem to reacquire the new machines MAC address also as it is cleared after a power cycle.

Also only one device may be connected to the modem at a time, so the proper connection scheme would be to have Modem > FIREWALLED PC w/sharing & DHCP enabled (2 NICs) > switch > other PCs.

---

### Post by steeldriver on 2012-06-01
> **eode said:**
> Good diagnosis, steeldriver.

Thanks eode - it took us a while to get there, when Keith said he was connecting via a switch I was initially imagining that as a secondary device (essentially a port multiplier in an already NATed LAN). I sometimes forget we're not all wired up the wazoo.

---

### Post by pfindan on 2012-06-01
I was wondering about this myself...

---

### Post by LinGNUbie on 2012-06-01
BTW most end-user available modems are only configured to accept a single IP from the ISP. A second separate dedicated RG-6 and modem would be required to have an additional IP delivered to the home. At that point the user would have to have a multi-wan router or other (Ubuntu PC/Router) device set up to load balance/separate the two lines.

---

### Post by KeithandStacie on 2012-06-02
> **eode said:**
> I know I'm chiming in late on this, but yup.  You either need to pay comcast for another IP address (monthly fee, usually a few bucks) or buy a router (anywhere from $20 to $120 - [this Rosewill B/G/N router]("http://www.newegg.com/Product/Product.aspx?Item=N82E16833166072") is a pretty good deal, and you get wireless to boot (which you can disable if you don't want).


Seems fairly cheap, Ill probably get this!

> 
Also only one device may be connected to the modem at a time, so the  proper connection scheme would be to have Modem > FIREWALLED PC  w/sharing & DHCP enabled (2 NICs) > switch > other PCs. 	

> BTW most end-user available modems are only configured to accept a  single IP from the ISP. A second separate dedicated RG-6 and modem would  be required to have an additional IP delivered to the home. At that  point the user would have to have a multi-wan router or other (Ubuntu  PC/Router) device set up to load balance/separate the two lines. 	

I didn't realize this, So it wouldn't even be worth it (For me) to have a second IP. This helped me COMPLETELY understand whats going on! Thanks

---

