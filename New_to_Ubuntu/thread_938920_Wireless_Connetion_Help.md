---
title: "Wireless Connetion Help"
date: 2008-10-05
forum: New to Ubuntu
---

### Post by Mr. Man on 2008-10-05
OK i put Ubuntu on my laptop and all of a sudden my wireless didn't work anymore. I found out that this was because of the drivers. so i bought a Buffalo wireless USB thing with a CD. This CD had lots of .inf files but after about an hour i found one that worked. Then i tried to connect to the internet but with no success. I don't know if this is because there is something wrong with my driver, or my wireless USB, or my router, or just how I'm trying to get it right. I think the problem is my password (but I'm not sure) i checked on my parents computer but I found out they don't have a password on our wireless anymore. This might be the problem because the wireless doesn't have an option for no password when you click on Manual Configuration. The main thing is that I think I have it right but i just cant connect to anything.
     I know its not very detailed but can u just give me a few ideas on what might be the problem...

     -Thanks alot (:

---

### Post by halitech on 2008-10-05
first off, lets make sure the computer is actually seeing the USB adapter. open a terminal and post back the results of
```
lsusb
```
then ```
sudo lshw -C network
```

---

### Post by Mr. Man on 2008-10-06
Ok I think its there because first of all it said hardware found when I installed the new driver from the cd. But also because there wasnt annything in the terminal that sounded or looked like an error. 
     
     Im not sure though so here is what i got when i typed in **lsusb**...

[B]thijs@thijs-laptop:~$ lsusb
Bus 007 Device 003: ID 04f2:b016 Chicony Electronics Co., Ltd 
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 002: ID 03f0:171d Hewlett-Packard 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 046d:c018 Logitech, Inc. 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 08ff:2580 AuthenTec, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  [/B]


Then I typed in **sudo lshw -C network** and I got...
(you might need to know that first it said **CPUID** for about half a second. But then turned into **PCI (sysfs)**. It didnt say CPUID on the line under PCI (sysfs). It just changed like that. Then after 3 seconds or so the rest appeared and the **PCI (sysfs)** was gone. Then it started looking a little more complicated).

[B]thijs@thijs-laptop:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 88E8039 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 14
       serial: 00:1d:72:4a:93:48
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.20 duplex=full firmware=N/A ip=192.168.1.100 latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wmaster0
       version: 02
       serial: 00:1f:3c:04:37:b0
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g[/B]

Thanks again

---

### Post by halitech on 2008-10-06
ok, it is being seen correctly, not sure which it is in the lsusb list but the network info shwos it as the Intel network.

try this
```
sudo iwlist scan
```

this should let us know if its seeing the router

---

### Post by Mr. Man on 2008-10-06
Ok I think its there because first of all it said hardware found when I installed the new driver from the cd. But also because there wasnt annything in the terminal that sounded or looked like an error. 
     
     Im not sure though so here is what i got when i typed in **lsusb**...

[B]thijs@thijs-laptop:~$ lsusb
Bus 007 Device 003: ID 04f2:b016 Chicony Electronics Co., Ltd 
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 002: ID 03f0:171d Hewlett-Packard 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 046d:c018 Logitech, Inc. 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 08ff:2580 AuthenTec, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  [/B]


Then I typed in **sudo lshw -C network** and I got...
(you might need to know that first it said **CPUID** for about half a second. But then turned into **PCI (sysfs)**. It didnt say CPUID on the line under PCI (sysfs). It just changed like that. Then after 3 seconds or so the rest appeared and the **PCI (sysfs)** was gone. Then it started looking a little more complicated).

[B]thijs@thijs-laptop:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 88E8039 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 14
       serial: 00:1d:72:4a:93:48
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.20 duplex=full firmware=N/A ip=192.168.1.100 latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wmaster0
       version: 02
       serial: 00:1f:3c:04:37:b0
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g[/B]

Thanks again

---

### Post by Mr. Man on 2008-10-06
This is what im seeing

thijs@thijs-laptop:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

---

### Post by minky311 on 2008-10-06
I don't seem to see the buffalo usb wireless adapter.
All I see is the one you said didn't work at first so you bought the buffalo wireless adapter.
According to this page those drivers for the original wireless you were using should work.
[http://intellinuxwireless.org/](http://intellinuxwireless.org/)
Try going into the terminal and typing **uname -a** to see what kernel you are using.

---

### Post by Mr. Man on 2008-10-06
Sry, i made a stupid mistake! I didnt have the wireless usb plugged in. My appologies for that.

This is what i get with the usb plugged into my laptop.

lsusb:
thijs@thijs-laptop:~$ lsusb
Bus 007 Device 005: ID 0411:00e8 MelCo., Inc. 
Bus 007 Device 003: ID 04f2:b016 Chicony Electronics Co., Ltd 
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 002: ID 03f0:171d Hewlett-Packard 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 08ff:2580 AuthenTec, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
thijs@thijs-laptop:~$ 

sudo lshw -C network:
thijs@thijs-laptop:~$ sudo lshw -C network
[sudo] password for thijs: 
  *-network               
       description: Ethernet interface
       product: 88E8039 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 14
       serial: 00:1d:72:4a:93:48
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.20 duplex=full firmware=N/A ip=192.168.1.100 latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wmaster0
       version: 02
       serial: 00:1f:3c:04:37:b0
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g
thijs@thijs-laptop:~$ 

sudo iwlist scan:
thijs@thijs-laptop:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.


So it seems prettey much the same though.

This is the kernel
thijs@thijs-laptop:~$ uname -a
Linux thijs-laptop 2.6.24-19-generic #1 SMP Wed Aug 20 22:56:21 UTC 2008 i686 GNU/Linux
thijs@thijs-laptop:~$ 

I also think that the wireless works fine im just doing something wrong when i connect to a router...

---

