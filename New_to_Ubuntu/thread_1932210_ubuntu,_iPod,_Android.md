---
title: "ubuntu, iPod, Android"
date: 2012-02-27
forum: New to Ubuntu
---

### Post by loopybazz on 2012-02-27
Hi All.):P I am using ubuntu 11.10 on my note book. I want to use my note books internet connection by my Android phone and my iPod. How can I do this?

---

### Post by ahiung on 2012-02-27
I see your post goes like this...
"I want to use my laptops as modem, so my ipod and android can connected to internet using wifi."
Is this right?
If so, you should make your ubuntu laptop as modem server.

---

### Post by loopybazz on 2012-02-27
That's what I want to do. How do I do that?

---

### Post by kevdog on 2012-02-27
Let me know more about your notebook.  You have a wired and wireless connection correct?  You want the clients to access wirelessly and then communicate through the wired connection to the internet.  In order for your wireless card to operate to receive connections from clients it needs to support infrastructure or ad hoc mode.  This would depend on the type of driver that supports your wireless card.  Do you have any information for your wireless card?

---

### Post by audiomick on 2012-02-27
If you don't know what your wireless is, you can do

```
sudo lshw -class network
```

in a terminal. You will be asked for a password. Type in your user password and hit enter. You wont see what you are typing when you type the password.

You will get an output similar to this.

```
mick@mick-laptop:~$ sudo lshw -class network
  *-network DISABLED      
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 61
       serial: 00:1d:e0:13:d4:89
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:30 memory:d6d00000-d6d01fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 01
       serial: 00:19:db:ec:d7:01
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.100.195 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:29 ioport:1000(size=256) memory:d3120000-d3120fff memory:d3100000-d311ffff(prefetchable)

```

I have to admit that this doesn't mean much to me, but if you post it here, maybe someone can help translate. ;)

Use code tags if you do post it here. That is the button with a hash # above the post window.

---

### Post by loopybazz on 2012-02-27
Thanks for replying. Here is the output from the command that audiomick suggested.

```
  *-network
       description: Ethernet interface
       product: AR8152 v1.1 Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: c1
       serial: 1c:75:08:fb:13:19
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI duplex=full firmware=N/A ip=10.1.1.2 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:44 memory:57000000-5703ffff ioport:5000(size=128)
  *-network
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 68:a3:c4:7b:47:b3
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.0.0-16-generic firmware=N/A ip=10.42.43.1 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:56000000-5600ffff
```

Any help?

---

### Post by 3rdalbum on 2012-02-27
Use the Create New Wireless Network function in Network Manager.

---

### Post by audiomick on 2012-02-27
It's a bit of a shot in the dark, but you could try an internet search (google, if you must... ;) ) for your wireless adaptor and see if you can find some specs of it.

This is it

```
AR9285 Wireless Network Adapter (PCI-Express)
```

---

### Post by grahammechanical on 2012-02-27
I am not an expert at this. I am using the information in my motherboard User Guide for my wireless device.

There are three modes for a wireless adapter in a computer.

1) Infrastructure Mode. This is where the computer uses its wireless adapter to connect to a wireless Access Point (AP) such as a router/modem that is connected to the Internet Service Provider (ISP) by telephone cable.

2) Ad-hoc Mode. This is where the wireless adapter will let the computer connect to other wireless devices (computers) without using an Access Point.

3) Access Point Mode (AP Mode). This is where the computer acts as the access point for other computers with wireless adapters.

You need to set your laptop up in Access Point Mode (AP Mode). The laptop will need to be connected to the router/modem by ethernet cable. This is because the laptop's wireless adapter will be used to connect to the phone and ipad.

There is one little problem. It is not easy to use Ubuntu to put a computer's wireless adapter into AP Mode.

When we set up a wireless connection we can set either Infrastructure mode (which is the usual setting for a home computer to connect to a modem/router, or Ad-hoc mode but not AP mode.

There is some goodnews. In Ubuntu 12.04 we have or will have the option to set the wireless adapter to AP mode.

Wait a few weeks and then when Ubuntu 12.04 is released open System Settings and run the Network Utility. Select your wireless adapter from the list in the left-hand panel and you will see a button called "Use as an hotspot." That I think will put the wireless adapter in AP mode.

Although I am using 12.04 development branch right now I have not tested this as I have no need of this function. But it is there.

Of course, if you have room on your hard disk for another  partition you could always install 12.04 beta and dual boot into it and find out if this feature works.

Regards.

---

### Post by loopybazz on 2012-02-29
I think I'll wait till the 12.04 it sounds like it will let me do what I want a lot easier than if I have to get indepth and change things myself. I am using the Android phone as an AP mobile for the iPod at the moment but the connection only has 2 gb and in todays world that is bare minimum. The notebook has 120 gb via the wired connection. Who was it that said 64k of something was more than enough for anything? :D Thank you for the help.

---

### Post by loopybazz on 2012-03-01
Hi again. I couldn't wait. I downloaded a file I found via the ubuntu web site. It's called precise-desktop-i386.iso I created a startup usb. Ran the 'try it out mode'. Went to System Settings, Networks, Wireless, create new and pressed (I think it said) Add as HotSpot. The iPod found it straight away, the Anrdoid phone (Samsung Galaxy S) didn't. Although the iPod show it's connected to the Notebook, which is called ubuntu. But it doesn't connect to the internet. Looking at the settings in 12.04 it says Adhock. I tried the adhock in the 11.10 and had the same results. Ipod says it can but doesn't, Android just doesn't. Any advise on this?

---

