---
title: "Connected on Network but no internet connection"
date: 2012-12-26
forum: New to Ubuntu
---

### Post by OnTwoLegs on 2012-12-26
Running 12.04

I am connected on a wireless network but

ping [www.ubuntu.com](www.ubuntu.com)

dosen't return anything. 
All other devices in the house can browse the net on this very same network (including mobile phones and laptop running windows 7). 
I have no clue what I'm doing.
Been reading similar posts for the last couple hours.
Here are some info you might need:


```

route -n

Destination   Gateway        Genmask         Flags   Metric  Ref   Use  Iface
0.0.0.0       192.168.2.1    0.0.0.0         UG      0       0     0    wlan0
169.254.0.0   0.0.0.0        255.255.0.0     U       1000    0     0    wlan0
192.168.2.0   0.0.0.0        255.255.255.0   U       2       0     0    wlan0

```

```

ifconfig

eth0   Link encap:Ethernet HWaddr 00:26:6c:6f:e8:3e
       UP BROADCAST MULTICAST MTU:1500 Metric:1
       RX packets:0 errors:0 dropped:0 overruns:0 frame:0
       TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
       collisions:0 txqeuelen:1000
       RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
       Interrupted:43

lo     Link encap:Local Loopback
       inet addr:127.0.0.1 Mask:255.0.0.0
       inet6 addr: ::1/128 Scope:Host
       UP LOOPBACK RUNNING MTU:16436 Metric:1
       RX packets:4 errors:0 dropped:0 overruns:0 frame:0
       TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
       collisions:0 txqueuelen:0
       RX bytes:240 (240.0 B) TX bytes:240 (240.0 B)

wlan0  Link encap:Ethernet  HWaddr 00:16:44:61:ad:8d
       inet addr:192.168.2.12 Bcast:192.168.2.255 Mask:255.255.255.0
       inet6 addr: fe80::216:44ff:fe61:ad8d/64 Scope:Link
       UP BROADCAST RUNNING MULTICAST  MTU:1500 Metric:1
       RX packets:832 errors:0 dropped:0 overruns:0 frame:0
       Tx packets:1240 errors:0 dropped:0 overruns:0 carrier:0
       collisions:0 txqueuelen:1000
       RX bytes 227899 (227.8 KB)  TX bytes:126326 (126.3 KB)

```

```

iwconfig

lo     no wireless extensions.

wlan0  IEEE 802.11bgn  ESSID:''Lucien''
       Mode:Managed  Frequency:2.462 GHz Access Point: 00:13:A3:38:13:21
       Bit Rate=54 Mb/s    Tx-Power=15 dBm
       Retry  long limit:7   RTS thr:off   Fragment thr:off
       Power Management:off
       Link Quality=70/70  Signal level=-40 dBm
       Rx invalid nwid:0  Rx invalid crypt:0 Rx invalid frag:0
       Tx excessive retries:0  Invalid miscs:123   Missed beacon:0

eth0   no wireless extensions.

```

please help!

P.S. First time post, not sure about formatting...

---

### Post by papibe on 2012-12-26
Hi OnTwoLegs. Welcome to the forums ):P

Could you post the result of these commands?
```
cat /etc/resolv.conf 

grep dns /etc/NetworkManager/NetworkManager.conf 

cat /var/run/nm-dns-dnsmasq.conf 

nslookup ubuntu.com

dig google.com

```
Merry Christmas.

---

### Post by OnTwoLegs on 2012-12-26
```

cat /etc/resolv.conf

search umontreal.ca
nameserver 10.120.31.31
nameserver 10.120.184.31


```

```

grep dns /etc/NetworkManager/NetworkManager.conf

dns=dnsmasq


```

```

cat /var/run/nm-dns-dnsmasq.conf

server=192.168.2.1


```

```

nslookup ubuntu.com

;; connection timed out; no servers could be reached

```

```

dig google.com

; <<>> Dig 9.8.1-P1 <<>> google.com
;; global options: +cmd
;; connection timed out; no servers could be reached


```

---

### Post by OnTwoLegs on 2012-12-26
Thanks for the welcome :) (and quick reply!!)

---

### Post by papibe on 2012-12-26
It seems that your nameserver are not quite correct. You have to edit your /etc/resolv.conf and change the lines 'nameserver'.

Try this 2 options:
[LIST]
[*]If your router provide DNS services:
```
nameserver 127.0.0.1
```
That would point to use your router, which is set on /var/run/nm-dns-dnsmasq.conf

[*]Use Google public DNS:
```
nameserver 8.8.8.8
nameserver 8.8.4.4
```
[/LIST]
Let us know how it goes.
Regards.

---

### Post by OnTwoLegs on 2012-12-26
It worked! Thanks so much! :D

Why do you think resolv.conf changed all of a sudden? I have been using this connection for month with no problems..

---

### Post by papibe on 2012-12-26
Glad is working OK now.

It's hard to say why stop working, but let me make a couple of educated guesses:

If you change the modem or your router on your network lately, that settings may be reflecting the old configuration.

If your computer is a laptop, may be IT personnel or friend set your machine for another network while on another network.

In any case, check the application 'Network Connections', since there you should be able to set all network setting using an easier to use GUI tool.

Regards.

---

### Post by sandyd on 2012-12-26
> **OnTwoLegs said:**
> It worked! Thanks so much! :D

Why do you think resolv.conf changed all of a sudden? I have been using this connection for month with no problems..

If you use DHCP, it is the router's job to send the DNS nameservers, and the dhcp client (dhclient)'s job to paste it in resolv.conf

---

### Post by KermitTensmeyer on 2012-12-26
The system was set up to use localhost as DNS (and in reality it was using dnsmasq)  NetworkManager should have written the information from dhcp into nm-dns-dnsmasq.conf.

  Bypassing his local dnsmasq to use Googles public DNS server will get connected to the outside, but he still has a broken dnsmasq configuration.

 If you are going to bypass dnsmasq on a long-term basis, you should also going into the NetworkManager.conf and change the *dnsmasq* reference to *dns*


  side-note:   _nm-tool_ will report the current state of what NetworkManager understands

---

### Post by teejabar on 2012-12-27
i also have the same problem, but am connected through lan can anyone help

---

