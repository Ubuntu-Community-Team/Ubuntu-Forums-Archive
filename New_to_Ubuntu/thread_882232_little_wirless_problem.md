---
title: "little wirless problem"
date: 2008-08-06
forum: New to Ubuntu
---

### Post by trigsenior on 2008-08-06
hello , 

I recently installed vmware which involved messing around with drivers and also i updated my kernel which messed up wireless so now im on 
2.6.24-18-generic ( the one up is messed up). I am able to connect to wireless
on this kernel  even though though wlan0 when normally eth0.

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"Livebox-5000"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: something  
          Bit Rate=54 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality=63/100  Signal level=-40 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

hope you can help me fix this mess =)

---

### Post by Ryadt on 2008-08-06
I think you will have to reinstall the 2.6.24-19-generic. In synaptic search for linux-image-2.6.24-19-generic and mark it for reinstallation.

---

### Post by trigsenior on 2008-08-08
thanxs so much,

I re-installed it and it worked like a charm.

---

### Post by trigsenior on 2008-08-10
the problem is back , im not using wireless but wlan and every couple hours it dies and i need to re-connect. 

any ideas what is causing this error ? 

eth0      Link encap:Ethernet  HWaddr 00:1b:fc:5e:5d:d9  
          inet addr: XXXXX Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:fcff:fe5e:5dd9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16126 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22903 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7013407 (6.6 MB)  TX bytes:18948839 (18.0 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2877 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2877 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:162908 (159.0 KB)  TX bytes:162908 (159.0 KB)

wlan0     Link encap:Ethernet  HWaddr 00:c0:a8:ee:e0:e5  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:109 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:15581 (15.2 KB)  TX bytes:3747 (3.6 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-C0-A8-EE-E0-E5-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

