---
title: "Wlan on Ubuntu Hardy: my experiences"
date: 2008-08-18
forum: New to Ubuntu
---

### Post by tw.engel@gmail.com on 2008-08-18
Totally unexperienced with Linux, I tried to boot Ubuntu Hardy on my AMD Athlon / MSI MS-6712 based PC one week ago. Everything seemed fine at first, so I installed the OS by formatting the HD in the process. Now, the internet connection did not work so well after all. I would only accidentially receive an IP address, but then the connection would quickly deteriorate and/or I would get dropped. I then started with trying to remediate the problem. This is my report from the last week.

I have a Sparklan WU682(??) USB Wlan adapter that run against a 802.11g Thomson router with a WPA personal coding set-up. When I searched the Ubuntu forums concerning this problem, I found different answers. There are, on the one hand, a whole lot of different people suggesting different remedies, but overall they come to the same conclusion: change the driver. On the other hand, there are experts saying that the Ubuntu Hardy release is supposed to support Ralink rt2570 chipset based devices, that it should be incorporated into the integrated rt2500usb driver. For me, the last opinion was simply not true. 

I went trough a long series of different drivers, most of which did not install properly. I also tried to remove the integrated wpa supplicant, and replace the Network Manager with the alternative Wicd n.m. But all to no avail. In the end, the Ubuntu system seemed so dysfunctional that I thought it better to reinstall Ubuntu from the installation disc.

Then I tried once more to remediate the problem. I now had more knowledge of the different elements in the wireless network connection. Straight away I installed Wicd and had N.M. removed, as Wicd seemed to provide a more stable reception of the networks in range. I then unloaded the rt2500usb driver (rmmod rt2500usb). I installed the driver tar.gz package from Serialmonkey (rt2570_CVS...) (make & make install). I loaded the new driver, blacklisted the former (sudo gedit /etc/modprobe.d/blacklist). I now restarted, and voila ... I still had no internet connection. Then I modified the lan interface file (/etc/network/interfaces), so that rausb0 was initiated instead of wlan0 (keeping the original two lines auto lo & iface lo loopback (??)). 

Now I could hook up with a neighbour's network, as he/she runs it without encryption. Curiously, the available networks now show up with stronger signals (at least the domestic on going from ca -73 dBm to -1). Also, the connection is incredibly stable and fast (up to 400 kbs). But as I open the settings for the domestic AP, it is displayed as running on a WEP-key, even as I know for a fact that it is running on WPA-personal. I cannot connect to this AP at all.

Now, I've had it with this USB adapter, and I want to buy a lan cable so that I can connect the in-case Accton EN-1216 Ethernet card directly to the rooter. Hopefullly, this will work. But in the process I have grown found of Linux Ubuntu :)

---

### Post by nicedude on 2008-08-18
Just FYI Ethernet works 100% out of the gate on Ubuntu with no setup on your part. The only reason Wifi adapters are so spotty is the various manufacturers not releasing Linux based driver or not releasing specs for making them so others can, so if you have problems with a Wifi adapter in Linux be sure to send an Email to the manufacturer and let them know of your trouble/anger with them for not providing Linux support. If we all do this there will be far less problems in the future as corporations only listen when allot of people speak out and they are afraid of losing business, not because they care :-(

---

### Post by ugm6hr on 2008-09-07
What is interesting is that RaLink are the only wifi chipset manufacturer that **do** officially supprt Linux.

Unfortunately, their drivers don't play nice with Ubuntu / Network Manager very well.

I'm having similar problems with intermittent disconnections with my Edimax USB wifi that uses the same chipset.  I love Ubuntu, but having done my research to find that Edimax use Linux-compatible / supported Ra chipsets, and then buying one for this specific purpose, I'm a bit upset that it doesn't work very well at all.

Shame really.

---

