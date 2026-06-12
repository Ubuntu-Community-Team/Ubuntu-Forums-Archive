---
title: "[SOLVED] shared folder doesn't appear under &amp;quot;Network&amp;quot;"
date: 2008-08-23
forum: New to Ubuntu
---

### Post by stoppage on 2008-08-23
I'm trying to share folders between WINXP and Feisty. Samba and Samba common are both installed. Internet connection is o.k. I've got a shared folder in Feisty, and set up a static ip address. Under „Places/Network“ I've got „Windows Network“ (empty)! Still relatively new to Ubuntu, does anybody know of a fairly simple (GUI-based) tutorial or can anybody help me out here please?

---

### Post by halitech on 2008-08-24
if you open Nautilus and type in the IP address can you see the share?

```
smb://192.168.1.100/(name of shared folder)
```

---

### Post by stoppage on 2008-08-24
In your code, is...192.168.1.100 standard smb address? I tried both this address and actual static address of Feisty in Nautilus and both have the same result..&#8222;couldn't find.....&#8220;smb.... I think the problem may be in &#8222;Interfaces&#8220; file,,,,,,

auto lo

iface lo inet loopback



auto eth0

iface eth0 inet static

address 192.168.1.102

netmask 255.255.255.0

gateway 192.168.1.1



auto eth1

iface eth1 inet dhcp



auto eth2

iface eth2 inet dhcp



auto ath0

iface ath0 inet dhcp



auto wlan0

iface wlan0 inet dhcp





auto dsl-provider

iface dsl-provider inet ppp

pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf

provider dsl-provider




:~$ ifconfig

eth0      Link encap:Ethernet  HWaddr 00:16:17:13:A2:C0  

          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0

          inet6 addr: fe80::216:17ff:fe13:a2c0/64 Scope:Link

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          RX packets:542 errors:0 dropped:0 overruns:0 frame:0

          TX packets:440 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:548162 (535.3 KiB)  TX bytes:45763 (44.6 KiB)

          Interrupt:19 



lo        Link encap:Local Loopback  

          inet addr:127.0.0.1  Mask:255.0.0.0

          inet6 addr: ::1/128 Scope:Host

          UP LOOPBACK RUNNING  MTU:16436  Metric:1

          RX packets:110 errors:0 dropped:0 overruns:0 frame:0

          TX packets:110 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0 

          RX bytes:8602 (8.4 KiB)  TX bytes:8602 (8.4 KiB)



ppp0      Link encap:Point-to-Point Protocol  

          inet addr:85.180.147.163  P-t-P:213.191.89.20  Mask:255.255.255.255

          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1

          RX packets:478 errors:0 dropped:0 overruns:0 frame:0

          TX packets:361 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:3 

          RX bytes:532947 (520.4 KiB)  TX bytes:31010 (30.2 KiB)


This is turning into a marathon, thank you for your patience

---

### Post by bab1 on 2008-08-24
I am assuming you are trying to browse a windows XP share.  The client used for browsing windows shares from Linux (Ubuntu) is "smbfs"  Install: ```
sudo apt-get install smbfs
```
Then use Places>>Network to browse.

---

### Post by stoppage on 2008-08-24
Sorry, smb://192.168.1.102/(name of shared folder) now shows content, Windows Network is still empty and ping brings nothing, even to router although internet functions!

---

### Post by halitech on 2008-08-24
yes, I should have said to replace the IP address with your actual IP address. If using smb://192.168.1.102/(name of shared folder) works, just bookmark it and use that method to connect as Places - Network - windows shares doesn't seem to work properly for some reason

---

### Post by Iowan on 2008-08-24
In versions prior to Hardy (I still use Gutsy), I frequently had better luck using Places>Connect to Server.

---

### Post by stoppage on 2008-08-26
I can see all shared Windows folders when I just connect both computers with cross-over cable.
When I try to ping router I get "ping: sendmsg: Operation not permitted"
Windows sharing (XP to XP)  works no problem,so I don't have a router issue. Installing smbfs didn't help. This is really frustrating, on WINXP it's childs play! Anybody?

---

### Post by halitech on 2008-08-26
with the linux box connected to the router, open a terminal and do
```
ifconfig
``` and post the info back here

also, what is the ip addresses of the windows boxes?

---

### Post by stoppage on 2008-08-26
$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:16:17:13:A2:C0  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0 
          inet6 addr: fe80::216:17ff:fe13:a2c0/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:1052 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:738 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:1197436 (1.1 MiB)  TX bytes:69314 (67.6 KiB) 
          Interrupt:20 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:70 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:70 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:5272 (5.1 KiB)  TX bytes:5272 (5.1 KiB) 

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:85.180.157.7  P-t-P:213.191.89.20  Mask:255.255.255.255 
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1 
          RX packets:965 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:644 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:3 
          RX bytes:1169963 (1.1 MiB)  TX bytes:47796 (46.6 KiB) 


**ip addresses windows**

Microsoft Windows XP [Version 5.1.2600]
(C) Copyright 1985-2001 Microsoft Corp.

>ipconfig /all

Windows-IP-Konfiguration

        Hostname. . . . . . . . . . . . . : henry
        Primäres DNS-Suffix . . . . . . . :
        Knotentyp . . . . . . . . . . . . : Unbekannt
        IP-Routing aktiviert. . . . . . . : Ja
        WINS-Proxy aktiviert. . . . . . . : Ja

Ethernetadapter LAN-Verbindung:

        Verbindungsspezifisches DNS-Suffix:
        Beschreibung. . . . . . . . . . . : Realtek RTL8139-Familie-PCI-Fast Eth
ernet-NIC
        Physikalische Adresse . . . . . . : 00-50-22-E3-A1-26
        DHCP aktiviert. . . . . . . . . . : Nein
        IP-Adresse. . . . . . . . . . . . : 192.168.1.100
        Subnetzmaske. . . . . . . . . . . : 255.255.255.0
        Standardgateway . . . . . . . . . : 192.168.1.1
        DNS-Server. . . . . . . . . . . . : 192.168.1.1

PPP-Adapter Breitbandverbindung:

        Verbindungsspezifisches DNS-Suffix:
        Beschreibung. . . . . . . . . . . : WAN (PPP/SLIP) Interface
        Physikalische Adresse . . . . . . : 00-53-45-00-00-00
        DHCP aktiviert. . . . . . . . . . : Nein
        IP-Adresse. . . . . . . . . . . . : 85.180.143.6
        Subnetzmaske. . . . . . . . . . . : 255.255.255.255
        Standardgateway . . . . . . . . . : 85.180.143.6
        DNS-Server. . . . . . . . . . . . : 62.109.123.197
                                            213.191.74.19
        NetBIOS über TCP/IP . . . . . . . : Deaktiviert

---

### Post by halitech on 2008-08-26
ok, I'm not sure but I *think* I see where the problem is. You are using PPPoE (I think) and the windows computer is showing the PPPoE IP address as 85.180.143.6 while the Ubuntu computer is showing the PPP0 IP address as 85.180.157.7. Since the first 3 sets of numbers are not the same you can't talk and I *think* that is the connection everything is looking on.

---

### Post by stoppage on 2008-08-27
O.k., but does this explain why I can't ping the router? Also, internet functions o.k.

---

### Post by halitech on 2008-08-28
if the active connection is being seen as the PPPoE connection it may not be accessing the internal address at all so you wouldn't be able to ping it but internet would work fine as you have a live address from the internet.

as I said, I'm taking a guess here, haven't really had any dealings with computers having an internal address and an external address with PPPoE

---

### Post by stoppage on 2008-08-28
Went back to using crossover -cable to tranfer some folders from Windows to Ubuntu. Reconnected router and modem, changed absolutely no settings and all shared folders suddenly apppeared under Places/Network and appropriately in Windows. Oh, Feisty, Feisty.....obliged to all for your help and patience

---

### Post by halitech on 2008-08-28
strange, unless it just needed to be told to use the internal address I'm not sure why it would suddenly work but I'm not going to look a gift horse in the mouth ~L~

---

