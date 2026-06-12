---
title: "Wireless Help - Broadcom BCM4318"
date: 2008-05-22
forum: New to Ubuntu
---

### Post by chaserboy on 2008-05-22
I've trawled though dozens of how tos and previous threads on the subject and I'm still no closer to getting my wifi working. Please help!

I'm using an acer travelmate 2420 which has a broadcom 4318 card. Whilst wired LAN worked out the box the wifi is being most stubborn!

- Started off trying bcm43xx-fwcutter. Followed the instructions at a how-to somewhere in the community docs. Didn't work obviously.

- found a reference in the community docs for my specific laptap that said fwcutter didn't work and had to use the ndiswrapper approach. I've followed the guide here [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper) and downloaded an exe from here [http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_b/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_b/).

"tail /var/log/messages" gives me this (username removed).


May 22 22:30:49 -laptop kernel: [  253.734740] input: b43-phy0 as /devices/virtual/input/input96
May 22 22:30:51 -laptop kernel: [  254.305246] input: b43-phy0 as /devices/virtual/input/input97
May 22 22:30:53 -laptop kernel: [  254.968836] input: b43-phy0 as /devices/virtual/input/input98
May 22 22:30:59 -laptop kernel: [  256.074979] input: b43-phy0 as /devices/virtual/input/input99
May 22 22:32:47 -laptop kernel: [  274.314319] input: b43-phy0 as /devices/virtual/input/input100
May 22 22:32:49 -laptop kernel: [  274.525840] input: b43-phy0 as /devices/virtual/input/input101
May 22 22:32:51 -laptop kernel: [  274.998648] input: b43-phy0 as /devices/virtual/input/input102
May 22 22:32:53 -laptop kernel: [  275.811633] input: b43-phy0 as /devices/virtual/input/input103
May 22 22:32:55 -laptop kernel: [  277.251864] input: b43-phy0 as /devices/virtual/input/input104
May 22 22:33:01 -laptop kernel: [  279.466900] input: b43-phy0 as /devices/virtual/input/input105

What does this mean? Should i try another driver?

Help!!! This is definitely going to be death of ubuntu for me if i can't get wireless.

Realise you probably need more info, wasn't sure what to post,just tell what you need.

Any help appreciated.

---

### Post by shifty_powers on 2008-05-22
have you tried just suing the gui for ndiswrapper?

```
sudo apt-get install ndisgtk
```

then look at system>admin>windows wireless drivers.

plus, when you download the windows driver for that card, don't forget it is the actual *.inf file that ndis needs...

---

### Post by chaserboy on 2008-05-22
> **shifty_powers said:**
> have you tried just suing the gui for ndiswrapper?

```
sudo apt-get install ndisgtk
```

then look at system>admin>windows wireless drivers.

plus, when you download the windows driver for that card, don't forget it is the actual *.inf file that ndis needs...

Yup, done that.It shows bcmwl5 Hardware present:Yes. I just started looking at the terminal when config didn't work through the gui.

---

### Post by shifty_powers on 2008-05-22
might be a silly question, and i'm sure someone has asked this, but wehat actually happens when you try and join a network?

and what is the output of:

```
sudo iwlist scan
```

---

### Post by spiderbatdad on 2008-05-22
Run: ```
sudo dhclient
```

and ```
ifconfig
```
Post results...assuming you have enabled driver via ndis...

---

### Post by chaserboy on 2008-05-22
> **shifty_powers said:**
> might be a silly question, and i'm sure someone has asked this, but wehat actually happens when you try and join a network?

and what is the output of:

```
sudo iwlist scan
```

If i try to manually config a network it applies the changes then i get the little signal strength indicator top right with 0%. There are no networks listed for me to just click on (although there are several in my location that i know i shoud be able to see).

iwlist scan returns:

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

---

### Post by chaserboy on 2008-05-22
> **spiderbatdad said:**
> Run: ```
sudo dhclient
```

and ```
ifconfig
```
Post results...assuming you have enabled driver via ndis...

dhclient:

Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
SIOCSIFFLAGS: No such file or directory
SIOCSIFFLAGS: No such file or directory
SIOCSIFFLAGS: Operation not supported
SIOCSIFFLAGS: Operation not supported
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:16:ce:21:fe:04
Sending on   LPF/wlan0/00:16:ce:21:fe:04
Listening on LPF/wmaster0/
Sending on   LPF/wmaster0/
Listening on LPF/eth0/00:0a:e4:f7:75:67
Sending on   LPF/eth0/00:0a:e4:f7:75:67
Sending on   Socket/fallback
receive_packet failed on wlan0: Network is down
receive_packet failed on wmaster0: Network is down
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
send_packet: Network is down
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 6
send_packet: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPOFFER of 192.168.1.138 from 192.168.1.1
DHCPREQUEST of 192.168.1.138 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.138 from 192.168.1.1
bound to 192.168.1.138 -- renewal in 37596 seconds.

ifconfig:

eth0      Link encap:Ethernet  HWaddr 00:0a:e4:f7:75:67  
          inet addr:192.168.1.138  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20a:e4ff:fef7:7567/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7252 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7443 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4002424 (3.8 MB)  TX bytes:1046256 (1021.7 KB)
          Interrupt:22 Base address:0x3000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1360 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1360 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:68000 (66.4 KB)  TX bytes:68000 (66.4 KB)

Thanks for responses so far folks.

---

### Post by shifty_powers on 2008-05-22
well your wirelss card is definitely not working with ndiswrapper, though i know that probably isn't a useful statement.

will have to leave it at that for now, working on a very important aessay that has to be finished in a few hours ;)

hopefully someone else can keep helping...

---

### Post by Steve413z on 2008-05-22
I had a problem similar to yours, and I didn't want to use NDISwrapper
here was my solution:
[http://ubuntuforums.org/showthread.php?t=803986](http://ubuntuforums.org/showthread.php?t=803986)

---

