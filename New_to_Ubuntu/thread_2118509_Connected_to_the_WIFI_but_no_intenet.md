---
title: "Connected to the WIFI but no intenet"
date: 2013-02-21
forum: New to Ubuntu
---

### Post by talib on 2013-02-21
Hello every one, 

I am facing a problem, 
according to the Network Manager I am connected to the Wifi, but I am not able to login to the modem nor I have a access to the net, 
I am pasting the output result of IFCONFIG and IWCONFIG,

me@ubuntu:~# ifconfig
eth0      Link encap:Ethernet  HWaddr e8:03:9a:b7:38:fa  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 root@bt:~# ifconfig
eth0      Link encap:Ethernet  HWaddr e8:03:9a:b7:38:fa  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:41 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:96 errors:0 dropped:0 overruns:0 frame:0
          TX packets:96 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6997 (6.9 KB)  TX bytes:6997 (6.9 KB)

wlan0     Link encap:Ethernet  HWaddr e8:03:9a:c5:9c:82  
          inet addr:192.168.1.65  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::ea03:9aff:fec5:9c82/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15983 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11086 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:21214884 (21.2 MB)  TX bytes:1149093 (1.1 MB)

me@ubuntu:~# iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"HG655D-858325"  
          Mode:Managed  Frequency:2.422 GHz  Access Point: 72:B6:86:85:83:24   
          Bit Rate=65 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:on
          Link Quality=58/70  Signal level=-52 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:3   Missed beacon:0

eth0      no wireless extensions.

me@ubuntu:~# ping [www.google.com](www.google.com)
ping: unknown host [www.google.com](www.google.com)

---

### Post by steeldriver on 2013-02-21
Can you ping external hosts by IP instead of name? e.g.

```
ping -c4 8.8.4.4
```If so it could be a DNS configuration issue

---

### Post by grahammechanical on 2013-02-21
According to this

> UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1You are connected to the wireless access point/router/hub/modem. The key word is RUNNING. If that was not there then we would know that the wireless adapter in the computer was not connected to the wireless access point in the router/modem.

And according to this

> wlan0     IEEE 802.11bgn  ESSID: "HG655D-858325"  
          Mode:Managed  Frequency:2.422 GHz  Access Point:  72:B6:86:85:83:24   That is the access point. I am writing this from a Live Session and I am connected by ethernet so if I run iwconfig I get this

> wlan0     IEEE 802.11bg  ESSID:  off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:  off   Fragment thr:  off
          Power Management: offDo you see the difference? If you cannot connect to the Internet then the problem is between the modem and the ISP. Is the modem connected to the Internet, to the ISP? Is the telephone connection working? Are you connected to your wireless access point (HG655D-858325) or to a neighbor's access point that is not connected to an ISP?

Regards.

---

### Post by talib on 2013-02-23
Thanx for your reply, 
HG655D-858325 is my own router 

if I am connected to the router, then why I cant access the router configuration page, 

I am connected to the same modem via my phone and its working fine there,

---

