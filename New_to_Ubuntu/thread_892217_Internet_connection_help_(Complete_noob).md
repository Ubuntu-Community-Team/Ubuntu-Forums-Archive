---
title: "Internet connection help (Complete noob)"
date: 2008-08-16
forum: New to Ubuntu
---

### Post by Riboflavin444 on 2008-08-16
I recently installed Ubuntu 8.04 on an old laptop, but I have been unable to get it connected to the internet. I'm very new at this, so I don't even know where to start to look for the problem. The laptop is unable to find my wireless network, and when I wired it to the router it still was unable to connect. I ran the hardware test, and it was able to find the network controllers, but the test for the internet gave this error:

ERROR:root:Could not find def gateway info in /proc 

and then a long list of errors

Could someone please point me in the right direction?

---

### Post by cariboo on 2008-08-16
In a Applications-->Accessories-->Terminal type:

```
lspci
```

This command will give you a list of your devices

```
ifconfig
```

This command will list your network connection

If you could paste the output of these commands in your next post, we can get started on solving your problem.

Jim

---

### Post by Riboflavin444 on 2008-08-17
With command lspci:

andrew@andrew-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV250 [Mobility FireGL 9000] (rev 02)
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5705M Gigabit Ethernet (rev 01)
02:01.0 CardBus bridge: O2 Micro, Inc. OZ711EC1 SmartCardBus Controller (rev 20)
02:01.1 CardBus bridge: O2 Micro, Inc. OZ711EC1 SmartCardBus Controller (rev 20)
02:03.0 Network controller: Broadcom Corporation BCM4309 802.11a/b/g (rev 02)


With ifconfig:

andrew@andrew-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0f:1f:b3:f5:35  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:11 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1628 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1628 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:81400 (79.4 KB)  TX bytes:81400 (79.4 KB)

---

### Post by lyni on 2008-08-17
one quick way is to call your Internet Service Provider and they will walk you through it over the phone.

---

### Post by Crafty Kisses on 2008-08-17
Sorry for all the outputs you have to post, post the following:
```
lshw -C network
```

---

### Post by the_hardy_kid on 2008-08-17
Actually, lyni, thats not such a great idea. To be honest, most ISPs are scared of Linux. They will simply tell you that their internet will not work on Linux. All because they are scared...

---

### Post by Riboflavin444 on 2008-08-17
andrew@andrew-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: NetXtreme BCM5705M Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:0f:1f:b3:f5:35
       width: 64 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.86 firmware=5705-v3.16 latency=32 mingnt=64 module=tg3 multicast=yes
  *-network:1
       description: Network controller
       product: BCM4309 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=32 module=ssb
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:90:4b:83:e7:85
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

---

### Post by ingeva on 2008-08-17
> **Riboflavin444 said:**
> *-network:0             
       description: Ethernet interface
       product: NetXtreme BCM5705M Gigabit Ethernet
       vendor: Broadcom Corporation
       

First, use your wired interface to establish contact with you router.

Do this in the following order:
1. Switch off your router and let it be off for a minute.
2. Connect the ethernet cable.
3. Switch the router back ON.
4. (re)start the computer.

If you now have a connection, post the output of ifconfig here.
Among other data, it gives you the IP address assigned to your computer.
Replace the last number with a "1", and in 90% of the cases that will be the router's gateway address. Take a browser and access this address directly
(For instance I use [http://10.10.10.1](http://10.10.10.1))
You should now have the router's menu and be able to set up a configuration for the wireless.

The wireless in your computer must be set up accordingly, but one thing at a time. Your broadcom WiFi may not have Linux drivers, so you may need ndiswrapper to get it going. I'm not an expert on that but there's a lot of info about it in this forum.

Good luck!

---

