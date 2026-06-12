---
title: "No Internet Connection in Ubuntu v8.10"
date: 2008-11-02
forum: New to Ubuntu
---

### Post by dvarsam on 2008-11-02
Hello.

My DSL Internet was working fine in Ubuntu v8.04.
With Ubuntu v8.10 installed, I have no Internet connection!

Any ideas how to fix this?

All I did was just copy the settings from the Ubuntu v8.04 wired connection to the Ubuntu v8.10 wired connection, but nothing works...

DSL Settings are saved in the Router (so I don't need to enter them in my Ubuntu).

Any ideas?

Thanks.

---

### Post by diablo75 on 2008-11-02
Try opening a terminal window and typing **ifconfig** and then press enter.  Copy and paste the output here please.  I like your signature, by the way ;)

---

### Post by dvarsam on 2008-11-02
Here it goes:

```
tony@tony-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:07:e9:64:97:73  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::207:e9ff:fe64:9773/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:196 errors:0 dropped:0 overruns:0 frame:0
          TX packets:209 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:20553 (20.5 KB)  TX bytes:20805 (20.8 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:242 errors:0 dropped:0 overruns:0 frame:0
          TX packets:242 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15132 (15.1 KB)  TX bytes:15132 (15.1 KB)

```

Thanks.

---

### Post by diablo75 on 2008-11-02
You appear to be getting an network connection.

First, ping your router:

```
ping 192.168.1.1
```

Hit CTRL-C to cancel the pings after a few have gone (they should be successful).

Now try to ping google.com

```
ping www.google.com
```

Hopefully that works (but it probably won't).  If it doesn't, the problem probably has something to do with your DNS settings (which someone else here will have to help you with).

---

### Post by dvarsam on 2008-11-02
Here it goes:

By the way, my Router's IP address is "192.168.1.100" (not the one you suggested) 

```
tony@tony-desktop:~$ ping 192.168.1.100
PING 192.168.1.100 (192.168.1.100) 56(84) bytes of data.
64 bytes from 192.168.1.100: icmp_seq=1 ttl=255 time=3.60 ms
64 bytes from 192.168.1.100: icmp_seq=2 ttl=255 time=0.626 ms
64 bytes from 192.168.1.100: icmp_seq=3 ttl=255 time=0.578 ms
64 bytes from 192.168.1.100: icmp_seq=4 ttl=255 time=0.585 ms
64 bytes from 192.168.1.100: icmp_seq=5 ttl=255 time=0.609 ms
64 bytes from 192.168.1.100: icmp_seq=6 ttl=255 time=0.561 ms
64 bytes from 192.168.1.100: icmp_seq=7 ttl=255 time=0.581 ms
64 bytes from 192.168.1.100: icmp_seq=8 ttl=255 time=0.588 ms
64 bytes from 192.168.1.100: icmp_seq=9 ttl=255 time=0.593 ms
64 bytes from 192.168.1.100: icmp_seq=10 ttl=255 time=0.612 ms

^C
--- 192.168.1.100 ping statistics ---
10 packets transmitted, 10 received, 0% packet loss, time 14005ms
rtt min/avg/max/mdev = 0.546/0.792/3.603/0.751 ms

```

The above seems to work fine.
Now pinging [www.google.com](www.google.com)

```
tony@tony-desktop:~$ ping www.google.com
ping: unknown host www.google.com
tony@tony-desktop:~$ 

```

I guess it is DNS as you suggested.

BTW I have 2 DNS addresses setup in WinXP and they work fine, so I copied them in my Ubuntu - i.e.:
```
193.92.150.3;194.219.227.2
```

Any ideas?

Thanks.

---

