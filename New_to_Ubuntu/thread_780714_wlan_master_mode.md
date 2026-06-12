---
title: "wlan master mode"
date: 2008-05-03
forum: New to Ubuntu
---

### Post by sefmars on 2008-05-03
I have a canyon cn-wf518 and a linux box, i want ot set the card in AP mode hodo i do it:

```
br0       Link encap:Ethernet  HWaddr 00:0C:46:17:DC:3D
          inet addr:10.10.0.1  Bcast:10.10.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:411482 errors:0 dropped:0 overruns:0 frame:0
          TX packets:207016 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:557783463 (531.9 MB)  TX bytes:13123080 (12.5 MB)

eth0      Link encap:Ethernet  HWaddr 00:50:DA:7B:43:3A
          inet addr:xxx.xxx.xxx.xxx  Bcast:xxx.xxx.xxx.xxx  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:219583 errors:0 dropped:0 overruns:0 frame:0
          TX packets:419661 errors:0 dropped:0 overruns:10 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:15324130 (14.6 MB)  TX bytes:564501110 (538.3 MB)
          Interrupt:10 Base address:0xef00

eth1      Link encap:Ethernet  HWaddr 00:14:78:05:6D:27
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Base address:0x8e00

eth2      Link encap:Ethernet  HWaddr 00:0C:46:17:D9:43
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:12 Base address:0x4d00

eth3      Link encap:Ethernet  HWaddr 00:0C:46:17:DC:3D
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:411748 errors:0 dropped:0 overruns:0 frame:0
          TX packets:207024 errors:0 dropped:0 overruns:1 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:563635485 (537.5 MB)  TX bytes:14029939 (13.3 MB)
          Interrupt:9 Base address:0x6c00

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:162 errors:0 dropped:0 overruns:0 frame:0
          TX packets:162 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:15630 (15.2 KB)  TX bytes:15630 (15.2 KB)

wlan0     Link encap:Ethernet  HWaddr 00:0E:2E:CA:83:BF
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wmaster0  Link encap:UNSPEC  HWaddr 00-0E-2E-CA-83-BF-00-00-00-00-00-00-00-00-00-00
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

```
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

eth2      no wireless extensions.

eth3      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""
          Mode:Ad-Hoc  Frequency:2.412 GHz  Cell: Not-Associated
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B
          Encryption key:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

br0       no wireless extensions.

```

---

### Post by sefmars on 2008-05-04
bump...
no one done this?

---

### Post by sefmars on 2008-05-04
i installed hardy .. no luck it has rt2x00 support in the kernel but it does not work for me , when it boots it says it can't load the module :(

I can't even use it in ad-hoc mode :(

root@mars:/proc/sys/net/ipv4# ifconfig wlan0 down
root@mars:/proc/sys/net/ipv4# iwconfig wlan0 mode ad-hoc
root@mars:/proc/sys/net/ipv4# iwconfig wlan0 essid home
root@mars:/proc/sys/net/ipv4# iwconfig wlan0 key 1234567890
root@mars:/proc/sys/net/ipv4# ifconfig wlan0 up
SIOCSIFFLAGS: Operation not supported

---

### Post by sefmars on 2008-05-04
can anyone help me?

---

### Post by sefmars on 2008-05-09
bump

---

