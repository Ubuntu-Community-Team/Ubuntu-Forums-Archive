---
title: "Internet no longer works"
date: 2008-11-08
forum: New to Ubuntu
---

### Post by rossjman1 on 2008-11-08
I am having a major issue right now. For the past few days I have been unable to access the internet. It just suddenly stopped working. I have tried to unplug the router and modem, but that didn't work. I am also unable to connect via ethernet cord. My roommate has no trouble connecting to the wireless, and my xbox can connect also. What's the issue. I just upgraded to intrepid, and the connection was working for a few days after that, then just stopped. I'm on my friends computer right now, but coppied the output of ifconfig to my flashdrive. My wireless usually connects to ath0.
```
jeff@jeff-laptop:~/Desktop$ ifconfig
ath0      Link encap:Ethernet  HWaddr 00:15:e9:72:db:ef  
          inet addr:10.0.1.2  Bcast:10.0.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:576  Metric:1
          RX packets:22 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5711 (5.7 KB)  TX bytes:3427 (3.4 KB)

eth0      Link encap:Ethernet  HWaddr 00:15:58:0b:dd:76  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Memory:ee000000-ee020000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:304 errors:0 dropped:0 overruns:0 frame:0
          TX packets:304 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:18916 (18.9 KB)  TX bytes:18916 (18.9 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-15-E9-72-DB-EF-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10141 errors:0 dropped:0 overruns:0 frame:13744
          TX packets:383 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:1705433 (1.7 MB)  TX bytes:28371 (28.3 KB)
          Interrupt:16 


```

---

### Post by rossjman1 on 2008-11-08
Also, the network manager claims I am connected to either the wireless or wired network even though I am not.

---

### Post by anystupidname on 2008-11-08
Hmmm, I've seen this before... Déjà vu... Awe man! Ya dun went an broke da internets!


Anyway, you see the wifi0 adapter with the whacky mac address? That happened to me when udev was having shenanigans. It had something to do with the crappy PCMCIA wifi adapter I was using.

If I remember correctly, I forced a re detection of devices by nuking the udev rules and rebooting. Incidentally, I guarantee none of this. It was a fluke type of thing so if you try this and your entire college dorm explodes, I warned ya...

Find this file /etc/udev/rules.d/70-persistent-net.rules
(make a backup!)
Nuke all entries pertaining to the broken devices (wifi0, ath0, your mom)
and reboot. Can't hurt to cross your fingers.

---

### Post by rossjman1 on 2008-11-08
I deleted all contents of that file, but it still wont work.

---

### Post by anystupidname on 2008-11-08
OK... That isn't what I said to do but what does it look like now? 
Also, post your old rules file.
Also, what does your ifconfig look like now? Throw in lspci, lsusb, and lspcmcia for good measure...

Also, what does it say when you do a /etc/init.d/networking restart
?

You may be dealing with one of these bugs. It is hard to tell...
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/192845](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/192845)

---

### Post by rossjman1 on 2008-11-08
```
jeff@jeff-laptop:~/Desktop$ sudo /etc/init.d/networking restart
Password or swipe finger: 
 * Reconfiguring network interfaces...                                          Ignoring unknown interface ath0=ath0.


```

---

### Post by rossjman1 on 2008-11-09
bump

---

### Post by anystupidname on 2008-11-09
Bump what? Are you accustomed to having people help you when you ignore what they say and/or only provide one fifth of what they ask you for?

---

### Post by rossjman1 on 2008-11-09
It is kinda difficult to post output to commands when I can't connect to the internet on said computer. ```

jeff@jeff-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:15:58:0b:dd:76  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Memory:ee000000-ee020000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:328 errors:0 dropped:0 overruns:0 frame:0
          TX packets:328 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:20388 (20.3 KB)  TX bytes:20388 (20.3 KB)

jeff@jeff-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility X1400
02:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller
15:00.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
jeff@jeff-laptop:~$ lsusb
Bus 005 Device 004: ID 0781:5151 SanDisk Corp. Cruzer Micro 256/512MB Flash Drive
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 004: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 004 Device 003: ID 0a5c:2110 Broadcom Corp. Bluetooth Controller
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
jeff@jeff-laptop:~$ lspcmcia
Socket 0 Bridge:   	[yenta_cardbus] 	(bus ID: 0000:15:00.0)
jeff@jeff-laptop:~$ 



```

---

### Post by rossjman1 on 2008-11-09
/etc/udev/rules.d/70-persitant-whateverthefilenameis:
> # This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.

# PCI device 0x168c:0x0013 (ath_pci)
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:15:e9:72:db:ef", ATTRS{type}=="1", NAME="ath0"

# PCI device 0x8086:0x109a (e1000)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:15:58:0b:dd:76", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


---

### Post by rossjman1 on 2008-11-09
bump

---

### Post by rossjman1 on 2008-11-10
bump

---

### Post by rossjman1 on 2008-11-10
I have a Debian Sarge Net Install Disk from like 3 or 4 years ago. Will I be able to upgrade to the latest Debian testing by just editing the /etc/apt/sources.list file? Or will there be major problems?

---

### Post by rossjman1 on 2008-11-10
bump

---

### Post by rossjman1 on 2008-11-10
bump

---

### Post by rossjman1 on 2008-11-11
Can someone please list all the system files pertaining to networking, so I can copy them over from the live cd that I'm burning right now?

---

### Post by rossjman1 on 2008-11-11
bump... please help!!!

---

### Post by rossjman1 on 2008-11-11
deleted

---

### Post by rossjman1 on 2008-11-12
Ok. I'm running on a live cd. The internet is working, but the sound is not. I don't want to reinstall, then have to deal with not only reinstalling and reapplying all my cocnfigurations, but messing around with the sound to try to get it to work. Does ANYONE know of any file that I can copy over from the live cd to my installation that would fix this issue?

/etc/network/interfaces are the same on both.
/etc/udev/rules.d/70-persistent-net.rules are the same on both.
/etc/hosts are the same on both.

---

### Post by rossjman1 on 2008-11-12
I'm so pissed off right now. Why would Ubuntu break the internet connection??? Why won't anyone help me????

---

### Post by Crafty Kisses on 2008-11-12
What are the results of this command?
```
lshw -C network
```

---

### Post by rossjman1 on 2008-11-12
I will try that command when I get home. Are there any other suggestions?

---

### Post by directcharitycontribution on 2008-11-12
ooh usb key!

you connection may work if u bot with early kernel then to u thing

---

### Post by rossjman1 on 2008-11-12
```

jeff@jeff-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82573L Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 00
       serial: 00:15:58:0b:dd:76
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e1000e driverversion=0.3.3.3-k6 firmware=0.5-1 latency=0 module=e1000e multicast=yes
  *-network
       description: Wireless interface
       product: Atheros AR5001X+ Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:16:00.0
       logical name: wifi0
       version: 01
       serial: 00:15:e9:72:db:ef
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci ip=10.0.1.2 latency=168 maxlatency=28 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11g
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 3a:e8:47:76:89:10
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
jeff@jeff-laptop:~$ sudo lshw -C network
\Password or swipe finger: 
  *-network               
       description: Ethernet interface
       product: 82573L Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 00
       serial: 00:15:58:0b:dd:76
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=0.3.3.3-k6 firmware=0.5-1 latency=0 link=no module=e1000e multicast=yes port=twisted pair
  *-network
       description: AR5001-0000-0000
       product: Wireless LAN Reference Card
       vendor: Atheros Communications, Inc.
       physical id: 0
       version: 00
       slot: Socket 0
       resources: irq:16
  *-network
       description: Wireless interface
       product: Atheros AR5001X+ Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 2
       bus info: pci@0000:16:00.0
       logical name: wifi0
       version: 01
       serial: 00:15:e9:72:db:ef
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci ip=10.0.1.2 latency=168 maxlatency=28 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11g
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 3a:e8:47:76:89:10
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
jeff@jeff-laptop:~$ 

```

---

### Post by rossjman1 on 2008-11-12
Booting with an earlier kernel has the same results.

---

### Post by rossjman1 on 2008-11-12
bump

---

### Post by directcharitycontribution on 2008-11-13
> **rossjman1 said:**
> bump

[http://ubuntuforums.org/tags.php?tag=network](http://ubuntuforums.org/tags.php?tag=network)

---

### Post by nothingspecial on 2008-11-13
Try my first post here -

[http://ge.ubuntuforums.com/showthread.php?t=972691](http://ge.ubuntuforums.com/showthread.php?t=972691)

---

