---
title: "Unable to ping any public IP"
date: 2016-02-22
forum: New to Ubuntu
---

### Post by cpaoli17 on 2016-02-22
I just recently installed ubuntu 14.4 and while I was in the CLI trying some ping commands, I realized I am unable to ping any public IP address or DNS (google, 8.8.8.8, 4.2.2.2, yahoo, etc). I have internet access from the ubuntu machine in question and I can ping said IPs and DNS from another Windows 10 machine within the same LAN. I am able to ping the NIC and the gateway from ubuntu machine, but beyond that, nothing. Any suggestions?

Thanks!

---

### Post by newbie-user on 2016-02-22
Do you have a firewall that's blocking pings from your ubuntu machine?

---

### Post by cpaoli17 on 2016-02-22
I only have a comcast router and I don't think it's blocking it. 

I was looking at the route and noticed the following output. 

root@chris-K53U:/# route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         10.0.0.1        0.0.0.0         UG    0      0        0 wlan0
10.0.0.0        *               255.255.255.0   U     9      0        0 wlan0

Could one of those routes be messing me up?

I think the second route needs to be deleted but I can't enter the proper command.

---

### Post by newbie-user on 2016-02-22
The routes are fine. The second route is the route for your lan. That needs to be there.

Can you ping your Windows machine from Ubuntu?

---

### Post by cpaoli17 on 2016-02-22
Sure can:

chris@chris-K53U:~$ ping 10.0.0.6
PING 10.0.0.6 (10.0.0.6) 56(84) bytes of data.
64 bytes from 10.0.0.6: icmp_seq=1 ttl=128 time=7.72 ms
64 bytes from 10.0.0.6: icmp_seq=2 ttl=128 time=1.89 ms
64 bytes from 10.0.0.6: icmp_seq=3 ttl=128 time=4.28 ms
64 bytes from 10.0.0.6: icmp_seq=4 ttl=128 time=2.02 ms
64 bytes from 10.0.0.6: icmp_seq=5 ttl=128 time=4.54 ms
^C
--- 10.0.0.6 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4005ms
rtt min/avg/max/mdev = 1.895/4.094/7.724/2.124 ms

---

### Post by sandyd on 2016-02-22
Try installing MTR and see if it can tell us where your pings are dropping off.

Installation:
```

sudo apt-get install mtr-tiny

```

Run MTR:
```

mtr 8.8.8.8

```

Does the MTR show anything or does it only produce blank output? Or does it stop somewhere?

You can exit with Control+C

---

### Post by cpaoli17 on 2016-02-23
chris-K53U (0.0.0.0)                                                     Mon Feb 22 21:32:36 2016Keys:  Help   Display mode   Restart statistics   Order of fields   quit
                                                           Packets               Pings
 Host                                                    Loss% Drop   Rcv   Snt   Avg  Wrst StDev
 1. 10.0.0.1                                              0.0%    0    37    37   4.4  13.4   2.5
 2. ???

I also tried rebooting the comcast router, disabling the wifi on the laptop with ubuntu and connected with a cat5 directly to the router and got the same results. Still can't ping.

---

### Post by sandyd on 2016-02-23
Hmm.

Stop all pings, and then open a second tab.

In the first tab, run
```

ping 8.8.8.8

```

In the second, run
```

sudo tcpdump -i wlan0 -t icmp
```

If TCPDump is not installed, you can install it by running
```

sudo apt-get install tcpdump
```

Wait around 30s, and then post the output of the tcpdump window.

---

### Post by cpaoli17 on 2016-02-23
Here is the ping results:

root@chris-K53U:/# ping 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
^C
--- 8.8.8.8 ping statistics ---
120 packets transmitted, 0 received, 100% packet loss, time 118999ms


And here is the TCP dump:

```
IP 10.0.0.25 > google-public-dns-a.google.com: ICMP echo request, id 6458, seq 102, length 64
IP 10.0.0.25 > google-public-dns-a.google.com: ICMP echo request, id 6458, seq 103, length 64
IP 10.0.0.25 > google-public-dns-a.google.com: ICMP echo request, id 6458, seq 104, length 64
IP 10.0.0.25 > google-public-dns-a.google.com: ICMP echo request, id 6458, seq 105, length 64
IP 10.0.0.25 > google-public-dns-a.google.com: ICMP echo request, id 6458, seq 106, length 64
IP 10.0.0.25 > google-public-dns-a.google.com: ICMP echo request, id 6458, seq 107, length 64
IP 10.0.0.25 > google-public-dns-a.google.com: ICMP echo request, id 6458, seq 108, length 64
IP 10.0.0.25 > google-public-dns-a.google.com: ICMP echo request, id 6458, seq 109, length 64
IP 10.0.0.25 > google-public-dns-a.google.com: ICMP echo request, id 6458, seq 110, length 64
^C
17 packets captured
18 packets received by filter
0 packets dropped by kernel
```

I might have found something.  I wen't back to my windows desktop and ran another ping test and when I pinged the google DNS name I got :

```
Pinging google.com [2607:f8b0:4010:801::200e] with 32 bytes of data:
Reply from 2607:f8b0:4010:801::200e: time=14ms
Reply from 2607:f8b0:4010:801::200e: time=15ms
Reply from 2607:f8b0:4010:801::200e: time=14ms
Reply from 2607:f8b0:4010:801::200e: time=14ms


Ping statistics for 2607:f8b0:4010:801::200e:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 14ms, Maximum = 15ms, Average = 14ms

```
The results came back in IPV6, right?

But when I pinged the 8.8.8.8 from the windows PC, it failed:

```
Pinging 8.8.8.8 with 32 bytes of data:
Request timed out.
Request timed out.


Ping statistics for 8.8.8.8:
    Packets: Sent = 2, Received = 0, Lost = 2 (100% loss),
Control-C
^C
```

So the windows PC resolved the DNS name but the ubuntu laptop didn't.

i think the issue may be the xfinity arris TGG/CT modem/router. Comcast suggested it be replaced by taking it into the store, but we haven't seen any reason to do so. I'm not 100% sure that's where the problem lies....but I might be exchanging it tomorrow. 

Any other suggestions?

---

