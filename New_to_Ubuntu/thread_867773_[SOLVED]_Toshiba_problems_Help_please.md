---
title: "[SOLVED] Toshiba problems Help please"
date: 2008-07-23
forum: New to Ubuntu
---

### Post by markab9569 on 2008-07-23
I have purchased a Toshiba Satellite A205-S5000 for the sole purpose of running Ubunto and learning all about Linux. ($398 at Wal mart)

 My problem is that I have loaded up Ubuntu 8.04 from a disk (which went well) but it will not recognize my wireless card, and even after hooking up the computer directly by wire I can not access the Internet.

Can anybody give me some insight into my problem and possible solutions?

Mark

---

### Post by overdrank on 2008-07-23
> **markab9569 said:**
> I have purchased a Toshiba Satellite A205-S5000 for the sole purpose of running Ubunto and learning all about Linux. ($398 at Wal mart)

 My problem is that I have loaded up Ubuntu 8.04 from a disk (which went well) but it will not recognize my wireless card, and even after hooking up the computer directly by wire I can not access the Internet.

Can anybody give me some insight into my problem and possible solutions?

Mark

Hi and welcome, you can use the command ```
lspci
``` 
In the terminal located under applications, accessories, terminal and this will identify your hardware and then you can search the forums or post the info.

---

### Post by HieroPosche on 2008-07-23
Please post the output from

```
lspci
```

and 

```
ifconfig
```

ALso in make sure roaming mode is enabled in the system->Administration->network section.  It should be, by default, but can't hurt to check.

---

### Post by markab9569 on 2008-07-23
I have attached the results of running those commands

---

### Post by markab9569 on 2008-07-23
Here are the results as simple text. 

mark@mark-ubunto:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
05:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
0c:04.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
0c:04.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
0c:04.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
0c:04.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller
mark@mark-ubunto:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1e:ec:38:de:33  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:250 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1382 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1382 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:69100 (67.4 KB)  TX bytes:69100 (67.4 KB)

---

### Post by halitech on 2008-07-23
ok, you have an Atheros wireless card.

[color=red]05:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)[/color]

but Ubuntu doesn't see it so far. this thread may help

[http://ubuntuforums.org/showthread.php?t=718244&highlight=Atheros](http://ubuntuforums.org/showthread.php?t=718244&highlight=Atheros)

---

### Post by markab9569 on 2008-07-23
I am still having a problem with the first half of this question, which is getting a hardwire connection to the internet.

I put the ethernet cable from the cable modem directly into the ethernet jack on the toshiba, and it recognizes the network, but firefox still won't go to the Internet.

I have checked and roaming is enabled and browser is in online mode


Mark

---

### Post by spupy on 2008-07-23
> **markab9569 said:**
> I am still having a problem with the first half of this question, which is getting a hardwire connection to the internet.

I put the ethernet cable from the cable modem directly into the ethernet jack on the toshiba, and it recognizes the network, but firefox still won't go to the Internet.

I have checked and roaming is enabled and browser is in online mode


Mark

Are you sure you don't need any proxy settings? Or a static IP?
Also, after you think you are connected to the internet, **ifconfig** should show you your IP address (inet addr). If it is still 127.0.0.1, as the text you pasted shows, I think there might be a problem with receiving an IP.

---

### Post by halitech on 2008-07-23
the 127.0.0.1 is for his lo (loopback) address. His eth0 isn't showing an address at all.

open a terminal and try
```
sudo ifup eth0
```

---

### Post by markab9569 on 2008-07-23
I ran that command and got the message ignoring unknown interface eth0=eth0

---

### Post by markab9569 on 2008-07-24
On the advice of a friend, I ran the following commands:

ifconfig eth0 up and dhclient eth0

they returned:

Internet Systems Consortium DHCP Client V3.0.6

Copyright 2004-2007 Internet Systems Consortium.

All rights reserved.

For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)



Listening on LPF/eth0/00:1e:ec:38:de:33

Sending on   LPF/eth0/00:1e:ec:38:de:33

Sending on   Socket/fallback

DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8

DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 21

DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 2

No DHCPOFFERS received.

No working leases in persistent database - sleeping.

 ... And I still Firefox still won't connect to the internet

---

### Post by markab9569 on 2008-07-24
bump

---

### Post by markab9569 on 2008-07-29
OK, I finally got the problem solved. Thanks so much for oyur help

---

### Post by homeboy2kfun on 2008-09-01
im so lost can you help

---

### Post by halitech on 2008-09-01
you might have better luck starting a new thread, with a good description of what the problem is and then describing what you have done already to try and resolve the problem.

---

