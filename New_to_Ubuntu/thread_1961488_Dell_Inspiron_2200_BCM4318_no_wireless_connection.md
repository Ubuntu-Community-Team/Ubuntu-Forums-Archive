---
title: "Dell Inspiron 2200 BCM4318 no wireless connection"
date: 2012-04-19
forum: New to Ubuntu
---

### Post by Debian1989 on 2012-04-19
Hi everyone I'm complete;y new to linux. i installed ubuntu two days ago and have been able to get the wireless to work at first it would show the wireless connection in option but wouldn't pick up any networks. Now the wireless option is gon all-together. I really need help with this, ive been trying for two days to do it on my own by reading forums but i'm willing to admit defeat and ask for her. Can someone with some experience please help me

---

### Post by audiomick on 2012-04-19
Hi.
I'm not going to be able to get you very far with this, but I would suggest two things.

Firstly, have you let the system look for proprietary drivers for the wireless card? I gather from what I read here that this is the most likely thing to be causing a problem. To do this, connect the machine to the internet via a cable, and then open the "hardware drivers" application.

I assume you have a newer Ubuntu which is using the Unity desktop? In this case, go to the dash and type "hardware" in the search box. It should throw up the Hardware Drivers application. Click on it, let it do it's business, restart for good measure and then try the wireless again.

On older Ubuntu versions before Unity, the application is in System> administration> hardware drivers, I think. That or system>preferences.

If you have already done this, I would suggest providing exact information about your wireless card.

To do this, open a terminal and type in
```
sudo lshw -class hardware
```
hit enter and then type in your password when you see this line
```
mick@mick-MS-7345:~$ sudo lshw -class network
[sudo] password for mick: 

```
You wont see what you are typing. Hit enter again.

It will then give you output like this
```
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 01
       serial: 00:1d:92:db:23:da
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=N/A ip=192.168.0.3 latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
       resources: irq:44 ioport:d800(size=256) memory:feaff000-feafffff memory:feac0000-feadffff
  *-network
       description: Network controller
       product: A1 ISDN [Fritz]
       vendor: AVM GmbH
       physical id: 1
       bus info: pci@0000:05:01.0
       version: 02
       width: 32 bits
       clock: 33MHz
       configuration: driver=fcpci latency=0
       resources: irq:17 memory:febffc00-febffc1f ioport:ec00(size=32)

```

Post that here so that potential helpers can see what you are dealing with.

To copy out of the terminal, you have to select the block of text by wiping the mouse over it, then ctrl+shift+c to copy.

To get the nice box around it here in your post, use the code tags button. That is the one marked # at the top of the post window.

---

