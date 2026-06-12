---
title: "No Ethernet, Help"
date: 2014-03-14
forum: New to Ubuntu
---

### Post by Halfe on 2014-03-14
Hi. Just started to use Ubuntu on my server. 
The Version i'm running is Ubuntu 13.04 within a Jail in FreeNAS/BSD 

everything works well with VLAN from BSD to the Jail. But i cant Ping or get any thing out of the UBUNTU.
what i found out is that the network on ubuntu isnt configured and that is what i need help with cause i'm really new with this and Ubuntu. And googlin' it has been a hassel when you dont understand what you are doing.

Is there anyone who can help me seting this up.

This is the VLAN created by FreeBSD
> epair1b: flags=8842<BROADCAST,RUNNING,SIMPLEX,MULTICAST> metric 0 mtu 1500        options=8<VLAN_MTU>
        ether 02:16:bb:00:0c:0b
        nd6 options=9<PERFORMNUD,IFDISABLED>
        media: Ethernet 10Gbase-T (10Gbase-T <full-duplex>)
        status: active



This is the ifconfig on the ubuntu jail
> root@Ubuntu:/# ifconfig
eth0      Link encap:Ethernet  HWaddr 02:16:bb:00:0c:0b
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:116856 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0
          RX bytes:30411343 (30.4 MB)  TX bytes:0 (0.0 B)


lo0       Link encap:Local Loopback
          UP LOOPBACK RUNNING MULTICAST  MTU:16384  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


If i try to ping out i cannot reach anything.
> root@Ubuntu:/# ping 10.0.2.1
connect: Network is unreachable


root@Ubuntu:/# ping [www.google.com](www.google.com)
ping: unknown host [www.google.com](www.google.com)

root@Ubuntu:/# ping 173.194.71.104
connect: Network is unreachable

if i ping from network to IP

> ping 10.0.2.12


Pinging 10.0.2.12 with 32 bytes of data:
Reply from 10.0.2.101: Destination host unreachable.


Ping statistics for 10.0.2.12:
    Packets: Sent = 1, Received = 1, Lost = 0 (0% loss),

ping 10.0.2.12
PING 10.0.2.12 (10.0.2.12): 56 data bytes
^C
--- 10.0.2.12 ping statistics ---
29 packets transmitted, 0 packets received, 100.0% packet loss


---

