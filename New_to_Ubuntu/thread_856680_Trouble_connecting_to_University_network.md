---
title: "Trouble connecting to University network"
date: 2008-07-11
forum: New to Ubuntu
---

### Post by nikhil.nikki on 2008-07-11
When I did used Ubuntu 7.10, I was able to connect to my University Network with the following settings:

Wireless Security: WPA2 Enterprise
EAP Type: PEAP
Key Type: Dynamic WEP
Phase2 Type: MSCHAPv2

But after I did installed Ubuntu 8.04 Hardy, I am able to connect to all the other networks except my University network with the above settings. I searched the forums but could not find the exact solution. Can anyone help me out connecting to my University network? 

My Ubuntu 8.04 is using Broadcom B43 wireless driver.

Thanks for any help in advance.

---

### Post by bab1 on 2008-07-11
Is this connected to a wireless router?  Can you contact the university via pinging?  Are you in a dorm on campus that filters by MAC addresses?  And finally...Have you contacted the University Data Center or Help Desk?

---

### Post by nikhil.nikki on 2008-07-12
My University help desk has support for windows only. They provide a limited support to Linux. They only provided the following settings:

Wireless Security: WPA2 Enterprise
EAP Type: PEAP
Key Type: Dynamic WEP
Phase2 Type: MSCHAPv2

along with a CA certificate file. 

It is connected to a wireless router. My University uses 802.1x authentication.

I was successful in connecting to the network while I worked on Ubuntu 7.10 but not in Ubuntu 8.04

Thanks for any help in advance.

---

### Post by bumanie on 2008-07-12
Know of someone disabling ipv6 which enabled connection to a university network. Not sure if it will work but here's the procedure, which is reversible.
In Firefox address bar type about:config. In the filter type ipv6 --> enter. In the line that appears, right click on it and then left click toggle in the drop down box that appears. This changes the value from true to false. If you want to reverse it, same procedure, except you change the toggle from false to true. Hope it works. ipv6 was an issue in 7.10 for a number of users.

---

### Post by bab1 on 2008-07-12
Nihil,

The configuration needed appears to be the IP addressing.  

We will need some information from the terminal before we can get you online.

We need the results of:```
ifconfig -a
```

and he results of:```
ping 192.168.1.1
```

and 

```
ping 192.168.1.1
```

---

### Post by nikhil.nikki on 2008-07-13
Results of 
       ifconfig -a 

eth0      Link encap:Ethernet  HWaddr 00:16:36:ad:02:48  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:158 errors:0 dropped:0 overruns:0 frame:0
          TX packets:158 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7900 (7.7 KB)  TX bytes:7900 (7.7 KB)

wlan0     Link encap:Ethernet  HWaddr 00:14:a5:d3:7e:6b  
          inet addr:192.168.1.111  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::214:a5ff:fed3:7e6b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2024 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1597 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1969332 (1.8 MB)  TX bytes:259976 (253.8 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-14-A5-D3-7E-6B-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

=========================================================================

Results of
       ping 192.168.1.1

PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=127 time=2.36 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=127 time=8.26 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=127 time=1.31 ms
64 bytes from 192.168.1.1: icmp_seq=4 ttl=127 time=9.66 ms
64 bytes from 192.168.1.1: icmp_seq=5 ttl=127 time=7.67 ms
64 bytes from 192.168.1.1: icmp_seq=6 ttl=127 time=4.53 ms
64 bytes from 192.168.1.1: icmp_seq=7 ttl=127 time=20.8 ms
64 bytes from 192.168.1.1: icmp_seq=8 ttl=127 time=14.9 ms
64 bytes from 192.168.1.1: icmp_seq=9 ttl=127 time=29.8 ms
64 bytes from 192.168.1.1: icmp_seq=10 ttl=127 time=8.74 ms
64 bytes from 192.168.1.1: icmp_seq=11 ttl=127 time=14.0 ms
64 bytes from 192.168.1.1: icmp_seq=12 ttl=127 time=4.89 ms
64 bytes from 192.168.1.1: icmp_seq=13 ttl=127 time=10.0 ms
64 bytes from 192.168.1.1: icmp_seq=14 ttl=127 time=5.73 ms
64 bytes from 192.168.1.1: icmp_seq=15 ttl=127 time=22.1 ms
64 bytes from 192.168.1.1: icmp_seq=16 ttl=127 time=6.14 ms
64 bytes from 192.168.1.1: icmp_seq=17 ttl=127 time=8.96 ms
64 bytes from 192.168.1.1: icmp_seq=18 ttl=127 time=7.73 ms
64 bytes from 192.168.1.1: icmp_seq=19 ttl=127 time=2.39 ms
64 bytes from 192.168.1.1: icmp_seq=20 ttl=127 time=7.39 ms
64 bytes from 192.168.1.1: icmp_seq=21 ttl=127 time=10.7 ms
64 bytes from 192.168.1.1: icmp_seq=22 ttl=127 time=32.7 ms
64 bytes from 192.168.1.1: icmp_seq=23 ttl=127 time=5.31 ms
64 bytes from 192.168.1.1: icmp_seq=24 ttl=127 time=29.8 ms
64 bytes from 192.168.1.1: icmp_seq=25 ttl=127 time=9.34 ms
64 bytes from 192.168.1.1: icmp_seq=26 ttl=127 time=2.80 ms
64 bytes from 192.168.1.1: icmp_seq=27 ttl=127 time=9.66 ms
64 bytes from 192.168.1.1: icmp_seq=28 ttl=127 time=2.83 ms
64 bytes from 192.168.1.1: icmp_seq=29 ttl=127 time=3.27 ms
64 bytes from 192.168.1.1: icmp_seq=30 ttl=127 time=2.88 ms
64 bytes from 192.168.1.1: icmp_seq=31 ttl=127 time=13.7 ms
64 bytes from 192.168.1.1: icmp_seq=32 ttl=127 time=3.04 ms
64 bytes from 192.168.1.1: icmp_seq=33 ttl=127 time=13.6 ms
64 bytes from 192.168.1.1: icmp_seq=34 ttl=127 time=41.6 ms
64 bytes from 192.168.1.1: icmp_seq=35 ttl=127 time=4.06 ms
64 bytes from 192.168.1.1: icmp_seq=36 ttl=127 time=21.7 ms
64 bytes from 192.168.1.1: icmp_seq=37 ttl=127 time=6.94 ms
64 bytes from 192.168.1.1: icmp_seq=38 ttl=127 time=9.10 ms
64 bytes from 192.168.1.1: icmp_seq=39 ttl=127 time=7.52 ms
64 bytes from 192.168.1.1: icmp_seq=40 ttl=127 time=7.43 ms
64 bytes from 192.168.1.1: icmp_seq=41 ttl=127 time=15.4 ms
64 bytes from 192.168.1.1: icmp_seq=42 ttl=127 time=3.52 ms
64 bytes from 192.168.1.1: icmp_seq=43 ttl=127 time=6.35 ms
64 bytes from 192.168.1.1: icmp_seq=44 ttl=127 time=10.2 ms
64 bytes from 192.168.1.1: icmp_seq=45 ttl=127 time=18.3 ms
64 bytes from 192.168.1.1: icmp_seq=46 ttl=127 time=2.69 ms
64 bytes from 192.168.1.1: icmp_seq=47 ttl=127 time=3.76 ms

//did a Ctrl+c here

--- 192.168.1.1 ping statistics ---
47 packets transmitted, 47 received, 0% packet loss, time 46080ms
rtt min/avg/max/mdev = 1.316/10.564/41.632/8.801 ms
=================================================================================

---

### Post by nikhil.nikki on 2008-07-13
> **bumanie said:**
> Know of someone disabling ipv6 which enabled connection to a university network. Not sure if it will work but here's the procedure, which is reversible.
In Firefox address bar type about:config. In the filter type ipv6 --> enter. In the line that appears, right click on it and then left click toggle in the drop down box that appears. This changes the value from true to false. If you want to reverse it, same procedure, except you change the toggle from false to true. Hope it works. ipv6 was an issue in 7.10 for a number of users.

I typed about:config in the Firefox address bar and found out
under Preference Name: network.dns.disableIPv6 is already set to false.

Could u plz help me out. Thank You.

---

### Post by bab1 on 2008-07-13
Nikhil,

It appears you are connected; at least to the wireless router.

The results of ifconfig show your wifi card spec's to be> wlan0 Link encap:Ethernet HWaddr 00:14:a5:d3:7e:6b
[COLOR="Red"]inet addr:192.168.1.111[/COLOR] Bcast:192.168.1.255 Mask:255.255.255.0
inet6 addr: fe80::214:a5ff:fed3:7e6b/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:2024 errors:0 dropped:0 overruns:0 frame:0
TX packets:1597 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:1969332 (1.8 MB) TX bytes:259976 (253.8 KB)

Your ping of 192.168.1.1 shows that you are sending and receiving IP packets.   You are 192.168.1.111 and you are pinging 192.168.1.1. > PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
[COLOR="Green"]64 bytes from 192.168.1.1[/COLOR]: icmp_seq=1 ttl=127 time=2.36 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=127 time=8.26 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=127 time=1.31 ms 

Try try this:```
ping ubuntuforums.org
```

If this is successful you have DNS service.

To confirm send the results of:```
cat /etc/network/interfaces
```

and ```
cat /etc/resolv.conf
```

Can you surf the web?  How are you trying to connect to the University?

---

### Post by nikhil.nikki on 2008-07-13
Results of
       ping ubuntuforums.org


PING ubuntuforums.org (91.189.94.12) 56(84) bytes of data.
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_seq=1 ttl=46 time=142 ms
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_seq=2 ttl=46 time=158 ms
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_seq=3 ttl=46 time=144 ms
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_seq=4 ttl=46 time=151 ms
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_seq=5 ttl=46 time=143 ms
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_seq=6 ttl=46 time=146 ms
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_seq=7 ttl=46 time=150 ms
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_seq=8 ttl=46 time=147 ms
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_seq=9 ttl=46 time=144 ms
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_seq=10 ttl=46 time=148 ms
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_seq=11 ttl=46 time=181 ms
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_seq=12 ttl=46 time=148 ms
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_seq=13 ttl=46 time=158 ms
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_seq=14 ttl=46 time=141 ms
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_seq=15 ttl=46 time=151 ms
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_seq=16 ttl=46 time=147 ms
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_seq=17 ttl=46 time=147 ms
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_seq=18 ttl=46 time=155 ms
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_seq=19 ttl=46 time=149 ms
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_seq=20 ttl=46 time=150 ms
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_seq=21 ttl=46 time=147 ms
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_seq=22 ttl=46 time=140 ms
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_seq=23 ttl=46 time=149 ms
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_seq=24 ttl=46 time=140 ms

--- ubuntuforums.org ping statistics ---
24 packets transmitted, 24 received, 0% packet loss, time 23070ms
rtt min/avg/max/mdev = 140.389/149.512/181.295/8.183 ms
====================================================================================

Results of
        cat /etc/network/interfaces


auto lo
iface lo inet loopback
================================================================================

Results of
        cat /etc/resolv.conf

### BEGIN INFO
#
# Modified_by:  NetworkManager
# Process:      /usr/bin/NetworkManager
# Process_id:   5066
#
### END INFO

search tx.rr.com


nameserver 192.168.1.1
==============================================================================
I am able to surf the web with my home network. I am trying to connect to my
University network using network manager and with the following settings:

Wireless Security: WPA2 Enterprise
EAP Type: PEAP
Key Type: Dynamic WEP
Phase2 Type: MSCHAPv2

along with a CA certificate file.

Thanks for ur help.

---

### Post by bab1 on 2008-07-13
Nikhil,

The settings> Wireless Security: WPA2 Enterprise
EAP Type: PEAP
Key Type: Dynamic WEP
Phase2 Type: MSCHAPv2

along with a CA certificate file

are for encryption and authorization.  They don't really have anything to do with "connecting".

Your settings for the wlan0 interface connect you.  What specifically are you trying to connect to?  Is it a ssh connection to a host inside the university?  Is it a Terminal Server at the university?  I need to understand [COLOR="Blue"]what[/COLOR] you want to do, not [COLOR="Orange"]how[/COLOR] you want to do it.

---

### Post by nikhil.nikki on 2008-07-13
Hello bab1

Am just trying to connect to my University wireless network inorder to surf the net when i am at my University.  While i am trying to connect with the network manager, it seems as though it is half way to get connected by showing one green light, but it does not get connected.

---

### Post by bab1 on 2008-07-13
Ahhhhh.  The quick answer is to use dhcp to supply the address on the wlan0 interface for both home and school.  Do you know how to set that up?

---

### Post by nikhil.nikki on 2008-07-13
I don't know how to set up that. I would be very thankful if u give a detailed setup. 

Thank You so much for ur help.

---

