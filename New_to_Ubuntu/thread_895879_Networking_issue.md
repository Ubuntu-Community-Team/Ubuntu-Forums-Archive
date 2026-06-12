---
title: "Networking issue"
date: 2008-08-20
forum: New to Ubuntu
---

### Post by foobun2 on 2008-08-20
trying to swith to Ubuntu Linux from Windows XP. I am so far really impressed with Ubuntu and look forward to learning and working with it more.

I am having a hard time trouble shooting my network connectivity. Everything was working fine but I think installing VMWare really hosed things up. I have tried using static ip and dhcp but neither seem to work although in dhcp I do get an ip from the server.

Using the network tools app when I try to use the configure option on any of the interfaces I get an error that says "interface does not exist"

Looking at my ifconfig everything looks normal but I cannot even connect to resources on my network using ip addresses. I tried disabling the vmware interfaces but that did not help.

eth0      Link encap:Ethernet  HWaddr 00:1d:60:e7:f9:24  
          inet addr:192.168.3.37  Bcast:192.168.3.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:60ff:fee7:f924/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:374 errors:0 dropped:0 overruns:0 frame:0
          TX packets:144 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:23412 (22.8 KB)  TX bytes:18524 (18.0 KB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2053 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2053 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:143528 (140.1 KB)  TX bytes:143528 (140.1 KB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:c0:00:01  
          inet addr:192.168.3.89  Bcast:192.168.3.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:464 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:c0:00:08  
          inet addr:192.168.3.88  Bcast:192.168.3.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:57 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by Pro-reason on 2008-08-20
Sometimes it can help to go to your working Windows installation and note down the IP settings etc.  Then do the same on your Ubuntu installation.  That has worked for me.

---

### Post by foobun2 on 2008-08-20
ok it works now!

I booted into windows to post this thread and when I went back to linux it works. But I did change my IP set up to static IP,

I wonder if there is an issue with my router which handles the DHCP, Because I got a dual boot system both OS's use the same nic and possibly the DHCP saw that the hardware address already had a lease?

Any one know haw to do a release and renew on the ip lease?

Thanks

---

### Post by blastus on 2008-08-20
[QUOTE=foobun2]ok it works now!

I booted into windows to post this thread and when I went back to linux it works. But I did change my IP set up to static IP,

I wonder if there is an issue with my router which handles the DHCP, Because I got a dual boot system both OS's use the same nic and possibly the DHCP saw that the hardware address already had a lease?[/QUOTE]

I suppose it's possible. One time I had to reboot my router because it issued the same IP address to two different machines.

[QUOTE=foobun2]Any one know haw to do a release and renew on the ip lease?

Thanks[/QUOTE]

```
sudo ifdown eth0
sudo ifup eth0
```

---

