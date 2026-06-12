---
title: "help with wired internet"
date: 2012-06-12
forum: New to Ubuntu
---

### Post by usakov on 2012-06-12
Hello!
I've installed Kubuntu 12.04 on my laptop, but I can't connect to my wired internet (by the way, I use router).  I have been searching in forums for weeks but I don't really know what might be the problem. The Network Manager says: "setting network address", but it doesn't really do anything, the ip address never shows up.  I paste here the output of lspci -k:

03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
        Subsystem: Hewlett-Packard Company Device 306a
        Kernel driver in use: r8101
        Kernel modules: r8101

and ifconfig:

eth0      Link encap:Ethernet  HWaddr 00:23:8b:d8:0d:c6  
          inet6 addr: fe80::223:8bff:fed8:dc6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:57 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1368 (1.3 KB)  TX bytes:13686 (13.6 KB)
          Interrupt:17 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1296 (1.2 KB)  TX bytes:1296 (1.2 KB)

Where shall I search? What shall I do? Please, help me if you have any thoughts!

---

### Post by spikoley on 2012-06-13
Maybe [this thread]("http://ubuntuforums.org/showthread.php?t=1580175&highlight=RTL8101E") might help.  Sorry I don't know the answer, but I figured I would give you something to try and a bump.

Good Luck!

---

### Post by usakov on 2012-06-13
Thanks for the answear, I've already tried to install the latest driver (r8101 instead of r8169) but it didn't help :(
It is strange, because during the installation of Kubuntu it downloaded the language packages and stuff, now I can't even reach the router's menu (through a browser).  Unfortunately I'm not very good at networking, so maybe it's just a tiny, annoying problem that could be helped easily...

---

### Post by spikoley on 2012-06-13
If you are not acquiring an IP address then you will not be able to reach the router.  The command *dhclient* will attempt to acquire an IP address.  I don't think it is going to help, but it is worth a shot.

```
sudo dhclient
```

---

