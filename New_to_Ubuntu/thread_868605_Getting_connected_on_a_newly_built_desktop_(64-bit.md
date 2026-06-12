---
title: "Getting connected on a newly built desktop (64-bit)"
date: 2008-07-24
forum: New to Ubuntu
---

### Post by ConMan318 on 2008-07-24
I just got Ubuntu up and running on my new desktop build.  Now I need to get connected to the internet on it.  I have an ethernet cable plugged into a connection that I know is working, but network manager won't show a network.  Right now it has a picture of an orange triangle with an exclamation mark in it.  If I click on it, I get a 'No network devices have been found' option, which is grayed out.  I also get a 'manual configuration' option.  I've played around in there and can't find anything useful.

Output of 'ifconfig', if it'll be of use:
```

lo  Link encap:Local Loopback
    inet addr:127.0.0.1  Mask:255.0.0.0
    inet6 addr:  ::1/128 Scope:Host
    UP LOOPBACK RUNNING  MTU:16436  Metric:1
    RX packets:2584 errors:0 dropped:0 overruns:0 frame:0
    TX packets:2594 errors:0 dropped:0 overruns:0 carrier:0
    collisions:0 txqueuelen:0
    RX bytes:136012 (132.8 KB)  TX bytes:136012 (132.8 KB)


```

Thanks in advance.

---

### Post by SNuxoll on 2008-07-24
What network card/chipset do you have in your machine, the output of lspci would be helpful, along with attaching the output of lspci -v.

---

### Post by El Conquistador on 2008-07-24
try iwconfig see what that gives you. also run ifconfig eth0 up. now if you say your getting a "manual configuration" option i imagine your left clicking on the nm-applet icon. try to right click it and check the Enable Networking box. Hope it helps

---

### Post by SNuxoll on 2008-07-24
iwconfig's not going to help much, this is a ethernet interface...

---

### Post by El Conquistador on 2008-07-24
> **SNuxoll said:**
> iwconfig's not going to help much, this is a ethernet interface...

right right...probably should have thought that one through a little more. LOL! ok but the other stuff might work!

---

### Post by ConMan318 on 2008-07-24
```

connor@connor-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation Eaglelake DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation Eaglelade PCI Express Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation ICH10 USB UHCI Controller #4
00:1a.1 USB Controller: Intel Corporation ICH10 USB UHCI Controller #5
00:1a.2 USB Controller: Intel Corporation ICH10 USB UHCI Controller #6
00:1a.7 USB Controller: Intel Corporation ICH10 USB2 UHCI Controller #2
00:1b.0 Audio device: Intel Corporation ICH10 HD Audio Controller
00:1c.0 PCI Bridge: Intel Corporation ICH10 PCI Express Port 1
00:1c.4 PCI Bridge: Intel Corporation ICH10 PCI Express Port 5
00:1c.5 PCI Bridge: Intel Corporation ICH10 PCI Express Port 6
00:1d.0 USB Controller: Intel Corporation ICH10 USB UHCI Controller #1
00:1d.1 USB Controller: Intel Corporation ICH10 USB UHCI Controller #2
00:1d.2 USB Controller: Intel Corporation ICH10 USB UHCI Controller #3
00:1d.7 USB Controller: Intel Corporation ICH10 USB2 UHCI Controller #1
00:1r.0 PCI Bridge: Intel Corporation 82801 PCI Bridge (rev 90)
00:1f.0 ISA Bridge: Intel Corporation ICH10 LPC Interface Controller
00:1f.2 IDE Interface: Intel Corporation ICH10 4 port SATA IDE Controller
00:1f.3 SMBus: Intel Corporation ICH10 SMBus Controller
00:1f.5 IDE interface: Intel Corporation ICH10 2 port SATA IDE Controller
01:00.0 VGA compatible controller: nVidia Corporation Unknown device 0612 (rev a2)
02:00.0 Ethernet controller: Attansic Technology Corp. Unknown device 1026 (rev b0)
03:00.0 IDE interface: Marvell Technology Group Ltd. 88SE6121 SATA II Controller (rev b2)
05:03.0 firewire (IEEE 1394): Agere Systems FW323 (rev 70)


```

And I don't know what kind of network card/chipset I have.  This is my motherboard: [http://www.newegg.com/Product/Product.aspx?Item=N82E16813131295](http://www.newegg.com/Product/Product.aspx?Item=N82E16813131295) or [http://www.asus.com/products.aspx?modelmenu=2&model=2164&l1=3&l2=11&l3=709&l4=0](http://www.asus.com/products.aspx?modelmenu=2&model=2164&l1=3&l2=11&l3=709&l4=0) might have more info.

And networking is enabled when I right-click network manager.

Also, since I don't have internet I have to type any command line output to show you guys, and 'lspci -v' is gigantic.  Is there any specific part you'd like to see?

EDIT: This part may be helpful:
[code]
02:00.0 Ethernet controller: Attansic Technology Corp. Unknown device 1026 (rev b0)
   Subsystem: ASUSTeK Computer Inc. Unknown device 8226
   Flags: bus master, fast devsel, latency 0, IRQ 11
   Memory at fe9c0000 (64-bit, non-prefetchable) [size=256K]
   I/O ports at dc00 [size=128]
   Capabilities: <access denied>

---

### Post by SNuxoll on 2008-07-24
Try sudo modprobe atl1 and see if that helps.

---

### Post by ConMan318 on 2008-07-24
Doesn't seem to, I ran it and nothing changed.  I tried logging out/back in but still nothing.  Any other ideas?  I really want to get this working, I've spent like 10 hours on this computer today trying to get it working :p.

---

### Post by SNuxoll on 2008-07-24
Then try sudo modprobe atl2

---

### Post by ConMan318 on 2008-07-24
Nope, still nothing.

---

### Post by SNuxoll on 2008-07-24
hrm, it appears that there isn't a drive included for the chipset then...I can't find anything else either, at this point I'd suggest buying a cheap $10 network card.

---

