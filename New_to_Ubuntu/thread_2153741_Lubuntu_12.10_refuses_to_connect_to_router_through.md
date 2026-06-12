---
title: "Lubuntu 12.10 refuses to connect to router through WLAN"
date: 2013-06-12
forum: New to Ubuntu
---

### Post by Werne on 2013-06-12
First of all, I feel stupid for asking this, seeing as how I'm not a beginner but the problem is dumb and seems simple. Anyway...

Recently I got Lubuntu 12.10 (i686) for my wife, she finds Ubuntu sluggish and slow while Debian is too complicated for her. So I installed it, refused to connect to WLAN while in live session but I though that's normal, I have Ubuntu 12.04.2 (i686) that refuses to connect to WLAN when live but works fine after I install it. But this didn't work, as in at all.

The problem is, it finds the router, the signal is good (it has to be, the WLAN receiver is 30cm from the router), there is no password to it so it's not an authentification problem, I try to connect to it and it fails no matter how much I try. It's a router from a Croatian Vip mobile network, has a sim card in it (or so it says), not sure which model since the tag thingy that was glued to the bottom fell off a long time ago.

Here's the output of some commands you might find helful:

lsusb:
```

Bus 001 Device 005: ID 148f:3070 Ralink Technology, Corp. RT2870/RT3070 Wireless Adapter

```

ifconfig:
```

wlan0     Link encap:Ethernet  HWaddr 00:a1:b0:21:e1:7d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

iwconfig:
```

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on

```

lshw -C network:
```

  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:8
       logical name: wlan0
       serial: 00:a1:b0:21:e1:7d
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rt2800usb driverversion=3.5.0-17-generic firmware=0.29 link=no multicast=yes wireless=IEEE 802.11bgn

```

nmap -O 192.168.1.1 (executed on Ubuntu 12.04):
```

Starting Nmap 5.21 ( http://nmap.org ) at 2013-06-12 11:48 CEST
Nmap scan report for e.home (192.168.1.1)
Host is up (0.0076s latency).
Not shown: 997 closed ports
PORT   STATE SERVICE
23/tcp open  telnet
53/tcp open  domain
80/tcp open  http
MAC Address: 4C:54:99:11:3D:63 (Unknown)
Device type: general purpose
Running: Linux 2.4.X
OS details: Linux 2.4.18 - 2.4.35 (likely embedded)
Network Distance: 1 hop

OS detection performed. Please report any incorrect results at http://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 4.97 seconds

```

Unrelated to this thread - Interesting, even my router is running on Linux. :D

---

### Post by gordintoronto on 2013-06-12
Can you connect to the router as admin? There are several possibilities which might account for the problem. For example, the router might be blocking all but a list of known MAC addresses. Do you have a manual for the router?

Running an open network is dangerous unless you live in the woods, and your nearest neighbour lives 20 km away. If your neighbour uses the Internet through your router, and distributes child porn, you might find the police come and take your computers away -- and that's only the beginning of your troubles.

---

### Post by Werne on 2013-06-15
Hmm, I solved it. I ran dmesg and it said that the connection timed out after 3 times. Fiddling with iwconfig didn't help, not even compiling ralink drivers. But after I compiled the drivers, I checked lsmod and I found something interesting.

I ran the following command to check on Ralink 2870 module I compiled:
```
sudo lsmod|grep rt2
```
And it showed a bunch of them, one was even for a PCI card. So then I blacklisted all except those who seemed relevant to the USB dongle I have, these are the ones I didn't blacklist:
```
rt2800usb
rt2800lib
rt2x00usb
rt2x00lib
```
And now WLAN works like a charm, no timing out at all.:D Though I can't believe I didn't try to check that before I created this thread, now I feel dumb.:(

Also, out of curiosity, I tried running the same command on Ubuntu 12.04 and it only showed the above modules along with 3 more that are used by them (crc_ccitt, mac80211 and cfg80211). Don't know why Lubuntu 12.10 has other rt2* modules active, they didn't seem to be used by any of the above and they were the problem.:-s



Oh yeah, the reason I don't have WLAN encription is because the router doesn't support it. It's a piece of cheap junk I got for 5$ which will be replaced today with a D-Link router with WPA2 encription. And having an open network any poor guy can connect to is actually useful in a way, at least I got to try out Kali.:wink:

Anyway, the problem is solved now.

---

