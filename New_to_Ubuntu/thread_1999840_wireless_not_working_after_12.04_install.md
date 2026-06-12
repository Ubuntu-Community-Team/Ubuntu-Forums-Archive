---
title: "wireless not working after 12.04 install?"
date: 2012-06-08
forum: New to Ubuntu
---

### Post by DaveCara on 2012-06-08
Hi folks, Ive had enough of windows vista crashing all the time and generally being crap, so as recommended by a friend I've installed 12.04lts.
Very happy so far, everything looks nice and runs quickly, but my wireless wont work?
Any help greatly appreciated! Ive finally got my laptop working the way I want it apart from a great long ethernet cable across my lounge!:)

---

### Post by mbzn01 on 2012-06-08
Hi, welcome to the forum.

We'll need more info on your system. What type of notebook do you have.
Also post the output of "lspci" and "ifconfig" to get us started. This can be typed into terminal, (ctrl+alt+t) should get you there. Text can be copy+pasted with your mouse.

---

### Post by DaveCara on 2012-06-08
Hi, I have a Packard Bell Easynote TJ65
lspci:

00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 09)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 09)
00:1a.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1d.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801IBM/IEM (ICH9M/ICH9M-E) 4 port SATA Controller [AHCI mode] (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe (rev 10)
04:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)


and ifconfig:
ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1f:16:b5:30:91  
          inet addr:192.168.0.7  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:16ff:feb5:3091/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:68329 errors:0 dropped:0 overruns:0 frame:0
          TX packets:37002 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:102035843 (102.0 MB)  TX bytes:2905170 (2.9 MB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:268 errors:0 dropped:0 overruns:0 frame:0
          TX packets:268 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:37519 (37.5 KB)  TX bytes:37519 (37.5 KB)

wlan0     Link encap:Ethernet  HWaddr 00:22:5f:d6:39:73  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by mbzn01 on 2012-06-08
Seems like your card is working fine but not yet set up(looking at the last line of lspci and wlan0), wlan0 has no ip set. How did you try to connect to your wireless, which app do you use(I'm not familiar with stock ubuntu). Do you have a network icon in the tray"usually top right"?

---

### Post by DaveCara on 2012-06-08
I feel like a right dumbass now! found the network tray and stuck my router password in and I'm sorted!
Still really unfamiliar territory for me, but im sure i'll get to grips with it!
Thanks for the reply!

---

### Post by mbzn01 on 2012-06-08
We all do stupid things, go take a look at ubuntu pocket guide here [http://www.ubuntupocketguide.com/download_main.html](http://www.ubuntupocketguide.com/download_main.html)
Got me going in the beginning.

---

