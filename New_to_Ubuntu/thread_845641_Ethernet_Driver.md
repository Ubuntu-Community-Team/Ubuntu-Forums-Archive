---
title: "Ethernet Driver"
date: 2008-06-30
forum: New to Ubuntu
---

### Post by wizard710 on 2008-06-30
Basically I know very little about ubuntu as I have only been using it for about 4 - 5 hours. I couldn't get my ethernet working but now have found a driver for it but it says that it needs to run as root, how do I do that in terminal

---

### Post by Xerp on 2008-06-30
I'd say step back a little and let us help :) Which NIC do you have? If you're not sure, open a terminal and run

```
lspci
```

and post the output.

Also, post the output from

```
ifconfig -a
```

---

### Post by wizard710 on 2008-07-01
lspci
> 
00:00.0 Host bridge: Intel Corporation 82830 830 Chipset Host Bridge (rev 04)
00:02.0 VGA compatible controller: Intel Corporation 82830 CGC [Chipset Graphics Controller] (rev 04)
00:02.1 Display controller: Intel Corporation 82830 CGC [Chipset Graphics Controller]
00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
00:1f.0 ISA Bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 02)
02:01.0 Cardbus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)

ifconfig -a
> 
lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask 255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B0


I have also done some digging and found that I have a 3com 3c905 ethernet port

---

### Post by wizard710 on 2008-07-01
I found this site with drivers on it [http://support.3com.com/infodeli/tools/nic/linuxdownload.htm](http://support.3com.com/infodeli/tools/nic/linuxdownload.htm) but they explanations are for other distros of linux and as I have little knowledge of ubuntu I can't do it on hardy, can some one help

---

### Post by Xerp on 2008-07-01
Hm. The 3c905 is an ancient card and has been supported for years. It doesn't show up at all when you to lspci, which would lead me to believe the card is either faulty or not quite in right. Have you ever had the NIC working?

---

