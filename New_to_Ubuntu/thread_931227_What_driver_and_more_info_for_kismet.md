---
title: "What driver and more info for kismet?"
date: 2008-09-27
forum: New to Ubuntu
---

### Post by disappearedng on 2008-09-27
Hi everyone,
right now I am trying to configure kismet and under source I have defined:
22 source = iwl4965, wlan0, Atheros

I use a T61 from Lenovo.
my ifconfig
```

eth0      Link encap:Ethernet  HWaddr 00:1c:25:70:55:ce  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Base address:0x1840 Memory:fe000000-fe020000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:117 errors:0 dropped:0 overruns:0 frame:0
          TX packets:117 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:12816 (12.5 KB)  TX bytes:12816 (12.5 KB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:c0:00:01  
          inet addr:192.168.17.1  Bcast:192.168.17.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:c0:00:08  
          inet addr:192.168.10.1  Bcast:192.168.10.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:1d:e0:34:51:9f  
          inet addr:192.168.0.165  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:e0ff:fe34:519f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:42917 errors:0 dropped:0 overruns:0 frame:0
          TX packets:31620 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:54417473 (51.8 MB)  TX bytes:4355946 (4.1 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1D-E0-34-51-9F-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

and iwconfig
```

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"dlink"  Nickname:""
          Mode:Managed  Frequency:2.427 GHz  Access Point: 00:1E:58:40:EF:F3   
          Bit Rate=54 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Power Management:off
          Link Quality=85/100  Signal level=-57 dBm  Noise level=-91 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

vmnet1    no wireless extensions.

vmnet8    no wireless extensions.

```

My question is, How do I know that I am using Atheros but not Prism? How do I know if iwl4965 is the right choice?

```

disappearedng@disappearedng-ubuntu-client:~$ sudo kismet
Launching kismet_server: //usr/bin/kismet_server
Suid priv-dropping disabled.  This may not be secure.
No specific sources given to be enabled, all will be enabled.
Non-RFMon VAPs will be destroyed on multi-vap interfaces (ie, madwifi-ng)
Enabling channel hopping.
Enabling channel splitting.
Source 0 ( Atheros): Enabling monitor mode for iwl4965 source interface  wlan0 channel 6...
FATAL: GetIFFlags: interface  wlan0: No such device
Done.

```
this is my error from starting kismet. Weird
I guess my iwl4965 is wrong?

---

### Post by disappearedng on 2008-09-27
any1?

---

