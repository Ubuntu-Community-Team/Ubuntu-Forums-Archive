---
title: "I'm so co-dependent. (Wireless internet help)"
date: 2008-10-21
forum: New to Ubuntu
---

### Post by wownerd87 on 2008-10-21
Ok,
Ubuntu is dual booting with vista, greatly. My next problem. Wireless isn't working. I am a little familiar with Ubuntu and I know I'm supposed to go to "Restricted Drivers" or something like that but I can't find it. Using 8.04. Thanks

---

### Post by Ctrl+Alt+Del on 2008-10-21
Go to System --> Administration --> Hardware Drivers and enable everything that is red.. should be pretty self explanatory

---

### Post by wownerd87 on 2008-10-21
> **Ctrl+Alt+Del said:**
> Go to System --> Administration --> Hardware Drivers and enable everything that is red.. should be pretty self explanatory

Alright thanks, I'm gonna go try it now.

---

### Post by wownerd87 on 2008-10-21
Ok, I'm using my wire Ethernet connection. I went to the Hardware Drivers and it didn't show anything. Nothing was red. But there is still no wireless :(

---

### Post by melojo on 2008-10-21
open a console and type commands below and post the output
sudo lshw -C network

ifconfig

---

### Post by wownerd87 on 2008-10-21
matt@matt-laptop:~$ sudo lshw -C network
[sudo] password for matt: 
  *-network               
       description: Network controller
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Ethernet interface
       product: NetLink BCM5906M Fast Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:1c:23:fa:f6:3b
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.86 duplex=full ip=192.168.1.108 latency=0 link=yes module=tg3 multicast=yes port=twisted pair speed=100MB/s
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:1e:4c:81:ed:a4
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g
matt@matt-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1c:23:fa:f6:3b  
          inet addr:192.168.1.108  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:23ff:fefa:f63b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3158 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2857 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3715016 (3.5 MB)  TX bytes:440856 (430.5 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1910 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1910 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:95500 (93.2 KB)  TX bytes:95500 (93.2 KB)

matt@matt-laptop:~$

---

### Post by melojo on 2008-10-21
have a look at this thread
[http://ubuntuforums.org/showthread.php?t=769990](http://ubuntuforums.org/showthread.php?t=769990)

---

### Post by wownerd87 on 2008-10-21
> **melojo said:**
> have a look at this thread
[http://ubuntuforums.org/showthread.php?t=769990](http://ubuntuforums.org/showthread.php?t=769990)

Ok the first step won't even work, the link isnt valid anymore...

---

### Post by melojo on 2008-10-21
[http://ubuntuforums.org/showthread.php?t=769990&page=29](http://ubuntuforums.org/showthread.php?t=769990&page=29)
This is the last page of the thread look through it

---

### Post by wownerd87 on 2008-10-21
Ok thanks.

---

### Post by wownerd87 on 2008-10-21
> **melojo said:**
> [http://ubuntuforums.org/showthread.php?t=769990&page=29](http://ubuntuforums.org/showthread.php?t=769990&page=29)
This is the last page of the thread look through it

THANK YOU THANK YOU THANK YOU! I got wireless working!!!!

---

### Post by melojo on 2008-10-21
glad you got it working!!!

---

### Post by eternalnewbee on 2008-10-21
Well then you can mark this thread as solved.
And may you live long & prosper.

---

### Post by eternalnewbee on 2008-10-21
Well then you can mark this thread as solved.
And may you live long & prosper.

---

