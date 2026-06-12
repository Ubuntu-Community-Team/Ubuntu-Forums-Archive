---
title: "[SOLVED] Internet stopped working suddenly"
date: 2008-07-20
forum: New to Ubuntu
---

### Post by AnonUK on 2008-07-20
Hi i have wired internet with sagem router, and my interner just suddenly stopped working yesterday and i don't know why. I've tried to change network settings to fix the problem but it hasn't worked.

Does anybody have any ideas please ?

---

### Post by TSS on 2008-07-20
First, is this for both wireless and wired?  Second, do you have another computer on your network that can connect to the internet?  Third, post the output of:
```
ifconfig
```

---

### Post by AnonUK on 2008-07-20
edit: it doesn't work now

---

### Post by TSS on 2008-07-20
Looks like you are good to go for now :-p...

Feel free to mark this thread SOLVED using Thread Tools at the top.

---

### Post by AnonUK on 2008-07-21
bump

the internet now doesn't work on ubuntu  (it works on vista)

i did ipconfig and it said -

eth0      Link encap:Ethernet  HWaddr 00:19:db:43:22:de  
          inet6 addr: fe80::219:dbff:fe43:22de/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:600 (600.0 B)  TX bytes:608 (608.0 B)
          Interrupt:19 Base address:0xe000 

eth0:avahi Link encap:Ethernet  HWaddr 00:19:db:43:22:de  
          inet addr:169.254.7.119  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:19 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2224 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2224 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:111200 (108.5 KB)  TX bytes:111200 (108.5 KB)

Also, could it not working have anything to do with my lokkit firewall ?

- yeh it's just a home machine

---

### Post by dracayr on 2008-07-21
You said you did 'ipconfig'. I trust you meant 'ifconfig'. 'ipconfig' is the command for windows

please also  post the output of

```
ipconfig /all
```

in vista

and

```
route
```
in ubuntu

EDIT: If you only want to use your machine as a home computer, you probably won't need a firewall

dracayr

---

### Post by AnonUK on 2008-07-21
Windows IP Configuration

   Host Name . . . . . . . . . . . . : louis-vitton-don
   Primary Dns Suffix  . . . . . . . :
   Node Type . . . . . . . . . . . . : Hybrid
   IP Routing Enabled. . . . . . . . : No
   WINS Proxy Enabled. . . . . . . . : No
   DNS Suffix Search List. . . . . . : home

Ethernet adapter Local Area Connection:

   Connection-specific DNS Suffix  . : home
   Description . . . . . . . . . . . : VIA Rhine II Compatible Fast Ethernet Ada
pter
   Physical Address. . . . . . . . . : 00-19-DB-43-22-DE
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes
   Link-local IPv6 Address . . . . . : fe80::908c:e299:9623:2440%8(Preferred)
   IPv4 Address. . . . . . . . . . . : 192.168.0.2(Preferred)
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Lease Obtained. . . . . . . . . . : 21 July 2008 16:41:19
   Lease Expires . . . . . . . . . . : 22 July 2008 16:41:19
   Default Gateway . . . . . . . . . : 192.168.0.1
   DHCP Server . . . . . . . . . . . : 192.168.0.1
   DHCPv6 IAID . . . . . . . . . . . : 201333211
   DNS Servers . . . . . . . . . . . : 192.168.0.1
   NetBIOS over Tcpip. . . . . . . . : Enabled

Tunnel adapter Local Area Connection* 6:

   Connection-specific DNS Suffix  . : home
   Description . . . . . . . . . . . : isatap.home
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes
   Link-local IPv6 Address . . . . . : fe80::5efe:192.168.0.2%16(Preferred)
   Default Gateway . . . . . . . . . :
   DNS Servers . . . . . . . . . . . : 192.168.0.1
   NetBIOS over Tcpip. . . . . . . . : Disabled

Tunnel adapter Local Area Connection* 9:

   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Teredo Tunneling Pseudo-Interface
   Physical Address. . . . . . . . . : 02-00-54-55-4E-01
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes
   IPv6 Address. . . . . . . . . . . : 2001:0:d5c7:a2ca:103d:182f:a53c:5b72(Pref
erred)
   Link-local IPv6 Address . . . . . : fe80::103d:182f:a53c:5b72%9(Preferred)
   Default Gateway . . . . . . . . . : ::
   NetBIOS over Tcpip. . . . . . . . : Disabled

Tunnel adapter Local Area Connection* 10:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : 6TO4 Adapter
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes

Tunnel adapter Local Area Connection* 11:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : 6TO4 Adapter
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes

Tunnel adapter Local Area Connection* 12:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : 6TO4 Adapter
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes

Tunnel adapter Local Area Connection* 7:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : 6TO4 Adapter
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes



-- ok it will take me a few mins until my next post because i have to now restart into ubuntu

---

### Post by AnonUK on 2008-07-21
Kernel IP routing table 
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface 
192.168.0.0     *               255.255.255.0   U     0      0        0 eth0 
link-local      *               255.255.0.0     U     1000   0        0 eth0 
default         myrouter.home   0.0.0.0         UG    100    0        0 eth0

---

### Post by Xerp on 2008-07-21
> Link-local IPv6 Address . . . . . : fe80::908c:e299:9623:2440%8(Preferred)
IPv4 Address. . . . . . . . . . . : 192.168.0.2(Preferred)
Subnet Mask . . . . . . . . . . . : 255.255.255.0
Lease Obtained. . . . . . . . . . : 21 July 2008 16:41:19
Lease Expires . . . . . . . . . . : 22 July 2008 16:41:19
Default Gateway . . . . . . . . . : 192.168.0.1
DHCP Server . . . . . . . . . . . : 192.168.0.1
DHCPv6 IAID . . . . . . . . . . . : 201333211
DNS Servers . . . . . . . . . . . : 192.168.0.1

Thats your info right there - you're getting your network settings via DHCP from 192.168.0.1. Ensure your NIC is set to "roaming" mode in Ubuntu. If your router is causing problems and can't assign DHCP information correctly, then you can bypass this by using a static setup.

---

### Post by dracayr on 2008-07-21
OK, run

```
sudo ifconfig eth0 192.168.0.2
```If it still doesn't work, also run
```
sudo route add default gw 192.168.0.1
```

dracayr

---

### Post by AnonUK on 2008-07-21
> **dracayr said:**
> OK, run

```
sudo ifconfig eth0 192.168.0.2
```If it still doesn't work, also run
```
sudo route add default gw 192.168.0.1
```

dracayr

:) Thanks it worked !

---

