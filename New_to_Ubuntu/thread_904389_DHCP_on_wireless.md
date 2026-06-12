---
title: "DHCP on wireless"
date: 2008-08-29
forum: New to Ubuntu
---

### Post by Bölvaður on 2008-08-29
Hi. I had wireless set up on this laptop and could connect to my university's router yesterday. Well today is different from yesterday, now my dhclient doesn't give me an IP.

I have tried to follow how-tos from this forum but it just doesn't give me a positive ending. All I get is the Network Manager agreeing with me that I have connected, but also claiming not having any IP and wireless quality is 0% (It is 99% and I am very close to it.. it was working yesterday ffs)

Also at home I was able to connect before upgrating to 8.04, and it seems to work on Vista on a different laptop.


```

sudo ifconfig wlan0 down
[COLOR="Silver"]sudo: unable to resolve host TwistedTiger[/COLOR]
[sudo] password for gummi:

sudo dhclient -r wlan0
[COLOR="Silver"]sudo: unable to resolve host TwistedTiger[/COLOR]
Internet Systems Consortium DHCP Client V3.06
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:04:3d:55:76:32
Sending on  LPF/wlan0/00:04:3d:55:76:32
**Sending on Socket/fallback**

sudo ifconfig wlan0 up
[COLOR="Silver"]sudo: unable to resolve host TwistedTiger[/COLOR]

sudo iwconfig wlan0 essid "My_Wireless"
[COLOR="Silver"]sudo: unable to resolve host TwistedTiger[/COLOR]

sudo iwconfig wlan0 key 123456789A
[COLOR="Silver"]sudo: unable to resolve host TwistedTiger[/COLOR]

sudo iwconfig wlan0 mode Managed
[COLOR="Silver"]sudo: unable to resolve host TwistedTiger[/COLOR]

sudo dhclient wlan0
[COLOR="Silver"]sudo: unable to resolve host TwistedTiger[/COLOR]
There is already a pid file /var/run/dhclient.pid with pid 134519077
Internet Systems Consortium DHCPClient V3.06
Copyright 2004-2007 Internet Systems ...............

Listening on LPF/wlan0/01:48:32:48:64:21
Sending on LPF/wlan0/01:48:32:48:64:21
Sending on Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6[B]
No DHCPOFFERS received.
No working leases in persistent database - sleeping.[/B]

```

---

### Post by Sam Lars on 2008-08-29
What's with this
```
sudo: unable to resolve host TwistedTiger
```
That has me worried.
And
```
There is already a pid file /var/run/dhclient.pid with pid 134519077
```
Seems to mean that dhclient is already working, or it thinks it is.
Could you do
```
ifconfig wlan0
```
before and after the dhclient -r and dhclient, and
```
iwconfig
```
before and after your iwconfig commands, to see how your changes are affecting the card.

---

### Post by Bölvaður on 2008-08-29
> **Sam Lars said:**
> What's with this
```
sudo: unable to resolve host TwistedTiger
```
That has me worried.
I do not know. It started coming after 8.04 on both my computers, doesn't seem to affect anything at all, but yes, it looks very strange and as if there is something wrong (probably is)




My ifconfig wlan0 gives me the same results through out the process.
Here are the highlights

wlan0 Link encap:Ethernet
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX and TX all give 0
collisions: 0 txqueuelen:1000
RX bytes: 0 TX bytes:0
Interrupt:10


iwconfig

wlan0 IEEE 802.11b ESSID: off/any
Mode;managed Frequency:2.412 GHz Access Point: Not-Associated
TRS thr=1600 B Fragment thr=2344 B
Power Management: off
Link Quality: 0 Signal level:0 Noise level:0
Rx and Tx give 0 in all

---

### Post by Bölvaður on 2008-08-29
bump

---

### Post by Sam Lars on 2008-08-29
It doesn't appear that your wireless is being configured correctly.
So you can do a iwlist scanning and see the wireless networks, and network manager claims to connect, but it doesn't?
Do you get the same output from those commands when network manager claims to be connected.

---

