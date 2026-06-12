---
title: "Wireless Connection Issue in 12.10"
date: 2012-11-14
forum: New to Ubuntu
---

### Post by ssdurn on 2012-11-14
I can't seem to get my wireless working, the hardware switch is on but I can only get onto the network using ethernet.

Other PCs on the network working OK.

I've tried installing the driver and it's showing as installed, but still no joy.

Here is the lshw output:

```
steve@steve-HP-Pavilion-dv6000-GB166EA-ABU:~$ sudo lshw -C network
  *-network UNCLAIMED     
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:d6000000-d6003fff
  *-network
       description: Ethernet interface
       product: PRO/100 VE Network Connection
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:05:08.0
       logical name: eth0
       version: 02
       serial: 00:1b:24:00:57:8b
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=full ip=192.168.1.127 latency=64 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100Mbit/s
       resources: irq:20 memory:d8000000-d8000fff ioport:4000(size=64)
```

---

### Post by NikTh on 2012-11-14
Hi , 
please follow bellow instructions for debugging. 

Open a terminal (CTRL+ALT+T) and paste bellow commands , one line at time. (You will need an active Internet connection)
```
wget "http://ubuntuone.com/1kKCgeRTZHszxUdsSEekYz" -O ~/wirelessinfo
chmod +x wirelessinfo
./wirelessinfo
```From the last command , a file with name **netifno.txt** will be produced in your /home directory.
Click on "New Reply" and attach the file. [See here on how to attach a file]("http://i.stack.imgur.com/0E6qS.png") 

Thanks

---

### Post by ssdurn on 2012-11-14
Here ya go!

---

### Post by NikTh on 2012-11-14
Hi , 
open a terminal and do 
```
sudo apt-get remove --purge bcmwl-kernel-source 
sudo apt-get install linux-firmware-nonfree
```

unplug your Ethernet cable , reboot and see if wireless raised.

Thanks

---

### Post by ssdurn on 2012-11-14
Thanks a million - all working fine now.

---

### Post by DiagonalArg on 2012-12-28
NikTh - Similar problem.  I have two wireless adapters. They were working fine in 12.04 but in 12.10 the ath5k adapter is not working and the Realtek is very iffy.  I can play with the latter one, and with some effort get it to connect, but it will drop out after some time.  Any input would be appreciated.  I'm attaching the netinfo.txt, here.

Thanks!
/DA

---

