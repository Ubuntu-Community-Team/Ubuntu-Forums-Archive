---
title: "Cannot SSH into Beaglebone Blue via USB cable"
date: 2018-01-19
forum: New to Ubuntu
---

### Post by k3nden on 2018-01-19
From Ubuntu host:  i am logged into Beaglebone using minicom. The results of ifconfig show below
Trying to connect using ssh to either of the inet addr's results in connection timed out.
ping results: PING 192.168.6.2 (192.168.6.2) 56(84) bytes of data. From 96.120.19.33 icmp_seq=123 Packet filtered -- not sure what this means.

The image on the beaglebone was installed based on info  from: [https://elinux.org/BeagleBoardUbuntu](https://elinux.org/BeagleBoardUbuntu)  and is "[COLOR=black][FONT=monospace]bone-ubuntu-16.04.3-console-armhf-2018-01-05-2gb.img.xz"
[/FONT][/COLOR]
I am stumped as what to try next or how to correctly set up network addresses. Suggestions are appreciated as I have not been able to find anything via searches that i can understand that help.


```
lo        Link encap:Local Loopback            inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1760 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1760 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:130240 (130.2 KB)  TX bytes:130240 (130.2 KB)


usb0      Link encap:Ethernet  HWaddr f4:5e:ab:50:31:4e  
          inet addr:192.168.7.2  Bcast:192.168.7.3  Mask:255.255.255.252
          inet6 addr: fe80::f65e:abff:fe50:314e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:133 errors:0 dropped:0 overruns:0 frame:0
          TX packets:33 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:21632 (21.6 KB)  TX bytes:5639 (5.6 KB)


usb1      Link encap:Ethernet  HWaddr f4:5e:ab:50:31:51  
          inet addr:192.168.6.2  Bcast:192.168.6.3  Mask:255.255.255.252
          inet6 addr: fe80::f65e:abff:fe50:3151/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:136 errors:0 dropped:0 overruns:0 frame:0
          TX packets:31 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:22616 (22.6 KB)  TX bytes:4034 (4.0 KB)
 
```

---

