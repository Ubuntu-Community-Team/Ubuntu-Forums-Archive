---
title: "Can't Connect Wireless"
date: 2013-01-21
forum: New to Ubuntu
---

### Post by shackleton056 on 2013-01-21
I just installed 12.10 last night.  I can't detect any wireless networks. The switch for my wireless is on.  Do I have to install a driver or something? Can someone walk me through this?

i have an hp pavillion dv 6000

---

### Post by audiomick on 2013-01-21
It is very likely that you have to install a driver to make the wireless work.

Let us know what wireless card you have.

Open a terminal and do
```
sudo lshw -c network
```

And post the results here. Use the # button at the top of the post window to put code tags around the result.

---

### Post by shackleton056 on 2013-01-21
Here's the result

zubin@Zubin:~$ sudo lshw -c network
[sudo] password for zubin: 
  *-network               
       description: Network controller
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:16 memory:f4000000-f4003fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 01
       serial: 00:1e:68:bd:0c:a6
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.0.8 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:44 ioport:c000(size=256) memory:f8200000-f8200fff memory:c0000000-c001ffff
zubin@Zubin:~$

---

### Post by shackleton056 on 2013-01-21
ps I don't understand any of that haha. thanks for the quick reply!

---

### Post by Warren Hill on 2013-01-21
There are known issues with broadcom wireless cards.  The fix is known too see here
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

### Post by shackleton056 on 2013-01-21
I tried downloading but then I have no idea what to do. I tried to find an .inf file (I think) through the wireless windows driver program...

---

### Post by audiomick on 2013-01-21
Yes, broadcom can be a bit dodgy, but my netbook has broadcom and it does work.

That link does contain good information, but you should perhaps try the additiional drivers utility first to see what it offers you. You need to be on a cable connection so the machine can get the stuff out of the internet. When you have a connection, go to the software centre and look around in there. I don't know exactly where it is, but I believe the utility has been moved to the software centre for 12.10.

---

