---
title: "D-Link System DWA-160 Xtreme N Dual Band USB Adapter"
date: 2011-11-21
forum: New to Ubuntu
---

### Post by Glkanter on 2011-11-21
Hi everyone!

This is "resumption" of my earlier thread regarding cheap usb wi-fi adapter purchase recommendations. That thread has been closed as 'solved'. Thanks to all!

Now I'm going in a whole different direction.

I'll be brief: I was given a Dell 8400 PC with this adapter as per lsusb: D-Link System DWA-160 Xtreme N Dual Band USB Adapter(rev.B) [Ralink RT2870]

But it works like crap, very much like this older thread I found:

[http://ubuntuforums.org/showthread.php?t=1640053&highlight=D-Link+System+DWA-160](http://ubuntuforums.org/showthread.php?t=1640053&highlight=D-Link+System+DWA-160)

Here's what I have:
```
disposable@disposable-Dimension-8400:~$ **iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"GK"  
          Mode:Managed  Frequency:2.457 GHz  Access Point: 00:40:36:3C:2F:86   
          Bit Rate=60 Mb/s   Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=67/70  Signal level=-43 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:23  Invalid misc:2   Missed beacon:0

disposable@disposable-Dimension-8400:~$ 



disposable@disposable-Dimension-8400:~$** ifconfig**
eth0      Link encap:Ethernet  HWaddr 00:11:11:c4:a0:b1  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:412 errors:0 dropped:0 overruns:0 frame:0
          TX packets:412 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:31464 (31.4 KB)  TX bytes:31464 (31.4 KB)

wlan0     Link encap:Ethernet  HWaddr 00:21:91:81:ab:00  
          inet addr:192.168.2.7  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::221:91ff:fe81:ab00/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1259 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1316 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1236922 (1.2 MB)  TX bytes:310823 (310.8 KB)

disposable@disposable-Dimension-8400:~$ 


disposable@disposable-Dimension-8400:~$** lshw -C network**
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5751 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:11:11:c4:a0:b1
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.116 firmware=5751-v3.23a latency=0 multicast=yes port=twisted pair
       resources: irq:16 memory:dfcf0000-dfcfffff
  *-network
       description: Wireless interface
       physical id: 3
       bus info: usb@1:3
       logical name: wlan0
       serial: 00:21:91:81:ab:00
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rt2800usb driverversion=2.6.38-12-generic firmware=0.12 ip=192.168.2.7 multicast=yes wireless=IEEE 802.11abgn
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.

disposable@disposable-Dimension-8400:~$ **sudo lshw -C network**
[sudo] password for disposable: 
  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5751 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:11:11:c4:a0:b1
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.116 firmware=5751-v3.23a latency=0 link=no multicast=yes port=twisted pair
       resources: irq:16 memory:dfcf0000-dfcfffff
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:3
       logical name: wlan0
       serial: 00:21:91:81:ab:00
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rt2800usb driverversion=2.6.38-12-generic firmware=0.12 ip=192.168.2.7 link=yes multicast=yes wireless=IEEE 802.11abgn
disposable@disposable-Dimension-8400:~$ 

```Can somebody help me understand what I need to do? Is this adapter worth the trouble? I have another 802.11n that I can tell you about. Or I can go to Micro Center.

Thanks!!

Garry

---

### Post by anewguy on 2011-11-21
The information you provided shows that the wireless appears to be working - it even shows an session id.  So, with that in mind, have you checked in network manager to see if wireless networks show?

If you could, please restate what isn't working with your existing adapter.

Thanks!
Dave ;)

---

### Post by Glkanter on 2011-11-21
[SIZE=2]So you're suggesting that [/SIZE]> [SIZE=2]*But it works like crap...*[/SIZE]
[SIZE=2] is not quite descriptive enough?

Very well, then. It's slow, it hangs, it requires re-boots...

The link I included is all over it, but I would benefit from all that info being distilled into the best and the simplest. Or more simply, 'right'.

Thanks!

Garry
[/SIZE]

---

### Post by OnkyC on 2012-02-26
I had been looking for a solution for this adapter for quite a while, stumbled on this site of instructions which sorted it for me. 

Good luck with it.

> [https://www.thinkpenguin.com/gnu-linux/penguin-80211n-usb-upgrading-carl9170-ubuntu-lts-lucid-1004-and-maverick-1010](https://www.thinkpenguin.com/gnu-linux/penguin-80211n-usb-upgrading-carl9170-ubuntu-lts-lucid-1004-and-maverick-1010)

---

