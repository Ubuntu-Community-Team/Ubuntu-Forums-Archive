---
title: "Wireless connection problems"
date: 2012-07-16
forum: New to Ubuntu
---

### Post by sooners95 on 2012-07-16
I just acquired this Ubuntu netbook from my Dad.  It is version 8.04.  I know updates need to be made but I need to get a wireless connection going here.  I can connect via Ethernet cable but not through my wireless. 

I did lspci, lsusb & ifconfig (below) before posting.  I could not be more clueless about this so any help is appreciated.

Katie

carl@C7:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. CX700 Host Bridge (rev 10)
00:00.1 Host bridge: VIA Technologies, Inc. CX700 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. CX700 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. CX700 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. CX700 Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. CX700 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:0f.0 IDE interface: VIA Technologies, Inc. CX700M2 IDE
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 90)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 90)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 90)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 90)
00:11.0 ISA bridge: VIA Technologies, Inc. CX700 PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. CX700 Internal Module Bus
00:13.0 PCI bridge: VIA Technologies, Inc. CX700 Host Bridge
01:00.0 VGA compatible controller: VIA Technologies, Inc. CX700M2 UniChrome PRO II Graphics (rev 03)
02:01.0 Audio device: VIA Technologies, Inc. VIA High Definition Audio Controller (rev 10)
carl@C7:~$ lsusb
Bus 004 Device 004: ID 13d3:5094 IMC Networks 
Bus 004 Device 003: ID 0bda:0156 Realtek Semiconductor Corp. 
Bus 004 Device 002: ID 0bda:8189 Realtek Semiconductor Corp. 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
carl@C7:~$ ifconfig
eth1      Link encap:Ethernet  HWaddr 00:d0:35:08:04:76  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 Base address:0xe800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2307 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2307 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:115434 (112.7 KB)  TX bytes:115434 (112.7 KB)

wlan0     Link encap:Ethernet  HWaddr 00:22:43:8a:71:cd  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:4 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:1008 (1008.0 B)

wlan0:avahi Link encap:Ethernet  HWaddr 00:22:43:8a:71:cd  
          inet addr:169.254.8.12  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

---

### Post by Sealbhach on 2012-07-16
Thanks for pasting in that info. Can you do this one as well please?

```
sudo lshw -C network
```

---

### Post by sooners95 on 2012-07-16
here it is:

PCI (sysfs)  
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@0000:00:07.0
       logical name: eth1
       version: 10
       serial: 00:d0:35:08:04:76
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:22:43:8a:71:cd
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=802.11b/g

---

### Post by NikTh on 2012-07-16
Hi , 
can you check please if something like switch ON/OFF from keys like Fn+F! exists ? 
I think maybe your wireless is OFF and you can turn it ON by Fn+F! compilation keys.

Also you can check you Bios configuration page and see if wireless card (pci) its Off or disabled. 
Thanks

---

### Post by sooners95 on 2012-07-17
How do I access the BIOS configuration page?  I can't seem to get there.
I tried Fn+F1 and it does enable/disable but still nothing.

---

### Post by sooners95 on 2012-07-17
Got into the BIOS but didn't see anything about a PCI card.

---

### Post by NikTh on 2012-07-17
Hi , 
can you download 12.04 Ubuntu release and burn it to a Usb or CD to test if your wireless work there? 
I cannot see any wireless card , from the results of** lspci **and **lsusb** , it seems that Kernel which accompanies Ubuntu 8.04 its incapable to recognize your wireless card
or
something is wrong with hardware.
Thanks

---

### Post by anewguy on 2012-07-17
Tghe USB device with manufacturer/product id's of 0bda:8189 should be the wireless.  Realtek RTL8187 of some version.  That should help those of you try to find a driver for the user.

---

### Post by anewguy on 2012-07-18
I might also add, since this in an old release, you might be better off just using ndiswrapper and installing the Windows XP (32-bit) driver - it would probably be the easiest.  If you need help in doing that just post back.

---

### Post by NikTh on 2012-07-18
Hi , 
yes indeed. @Anewguy has right. Your wireless its ```
0bda:8189 Realtek Semiconductor Corp.
``` , i search the forums and found this 
[http://ubuntuforums.org/showthread.php?t=898054](http://ubuntuforums.org/showthread.php?t=898054) (look at the 6th post) .
It seems need a patch of something for Ubuntu 8.04 , so be capable to connect with  your wireless card.
Try it and post back results. 
Ndiswrapper of course its another (maybe easier) solution . Try it too.
Thanks

---

### Post by anewguy on 2012-07-18
Since you are new, and if I'm assuming correctly you want to try a newer version of Ubuntu, ndiswrapper would probably be the easiest way to go for that adapter back in 8.xx.

However, it might also be worthwhile to see if your hardware will support the newer versions.

We know what the wireless is.  In addition, we can that the video chipset is a unichrome pro.  I haven't had to deal with one of those for many years, so I don't know if things are any better now or not.  The unichrome will probably require the drivers from OpenChrome.  On addition, I would be doubtful of the ability to run desktop effects, etc..

We should also look at a couple of other things:

- what is the model and speed of the CPU?
- how much memory does the system have?
- how large is the hard drive?
- does the system contain anything other than ubuntu, say perhaps a dual boot with Windows?

Those are the best questions I can think of for now to see if the system might be able to run an updated OS.

If you can post the specs back, we can make sure things are good enough to at least try.  At that point, we can walk you through ndiswrapper to get the wireless going.

---

