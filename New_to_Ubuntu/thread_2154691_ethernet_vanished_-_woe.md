---
title: "ethernet vanished - woe"
date: 2013-06-15
forum: New to Ubuntu
---

### Post by briar rabbit on 2013-06-15
I had ethernet last night and this morning it is gone.

Searched the forums to no avail.

I have wireless but I also need ethernet.

I checked in the BIOS and it says that the 'ethernet LAN' is enabled.

Help please.

Ubuntu 10.04
Kernel Linux 2.6.32-37-generic
GNOME 2.30.2

---

### Post by briar rabbit on 2013-06-15
I am at the neighbors house and will have to give up now and try again tomorrow.

I did the "ifconfig" without the ethernet cable attached and got this results:
ferg@ferg-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1c:25:18:61:c4  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Memory:fe200000-fe220000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2681 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2681 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:379625 (379.6 KB)  TX bytes:379625 (379.6 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1c:bf:39:9f:c0  
          inet addr:192.168.1.70  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:bfff:fe39:9fc0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6105 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5185 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4922609 (4.9 MB)  TX bytes:836067 (836.0 KB)

I did the "ifconfig" again with the ethernet cable attached and got this results:
ferg@ferg-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1c:25:18:61:c4  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Memory:fe200000-fe220000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2702 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2702 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:382937 (382.9 KB)  TX bytes:382937 (382.9 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1c:bf:39:9f:c0  
          inet addr:192.168.1.70  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:bfff:fe39:9fc0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6803 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5613 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5513696 (5.5 MB)  TX bytes:894963 (894.9 KB)

what does it all mean?

---

### Post by Iowan on 2013-06-15
> **briar rabbit said:**
> 
what does it all mean?In brief: wireless works, wired - not so much... ;)
I kinda hate to suggest turning off the wireless and trying again.  Sometimes my laptop balks a bit when I do that. To what does the wire connect: router, modem, hub/switch?  I suspect the machine isn't getting IP address from DHCP server. Have you tried another cable, or router/hub/switch port?

---

### Post by Cheesehead on 2013-06-16
When wired mysteriously stops working, try to narrow down the problem.
Your description did not say "after an upgrade..." so a hardware fault may be possible.

Hardware: Do you get the blinky TX/RX lights on the jacks? Or is it dark?

Try restarting the machines at both ends of the connection (not at the same time). That eliminates most software problems and some hardware problems. Try restarting a couple times, different machine order each time.

Next, look at the cable. Unplug it. Try it reversed. Check the cable for kinks or breaks or pulled ends. Try a spare cable (get a spare cable). Try plugging the cable into a different router jack and/or a different computer. See if you can figure out which end is bad.

Home routers do fail. Mice do eat through cables. Stuff happens.

---

### Post by briar rabbit on 2013-06-16
Thanks for the replies.

Well, I have no idea why I lost the ethernet or why it has come back.

Things I tried (while the ethernet was done) that did not work; restart (several times), tried turning off waiting and then turning back on, update (which I seldom normally do), checked the ethernet cable with a cable tester and tried a known good cable. Tried a port 'modem' (?) that had a working PC with internet connection on it.  The yellow and green lights at the ethernet plugin were on as they usually are.

I did notice that my laptop was exceedingly slow during the ethernet lose.  For example, when I took a screenshot the popup for it would ghost-out (linger) for several seconds before completing and while in 'gedit' the type was 8 letters behind my key strokes - very strange since I am not that fast at typing (and most irritating).

At any rate I have the ethernet back and the laptop is functioning at a normal speed.

Sorry to say I do not know whether I have a 'router' or 'modem'.  There are 2 wired PCs, a fax/copier and 1 wireless laptop on it and it plugs into the phone line.  I had always thought it was a 'modem'.

> Try restarting the machines at both ends of the connection (not at the  same time). That eliminates most software problems and some hardware  problems. Try restarting a couple times, different machine order each  time.
Not sure what "both ends of the connection" means but will keep it in mind for future problems.

Thanks again for the help.  Like Cheesehead said "Stuff happens".

---

