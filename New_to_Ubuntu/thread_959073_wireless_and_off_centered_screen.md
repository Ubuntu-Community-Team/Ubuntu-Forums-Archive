---
title: "wireless and off centered screen"
date: 2008-10-26
forum: New to Ubuntu
---

### Post by qdlbp on 2008-10-26
My primary OS is Vista. I just installed Ubuntu 8.04.1 on a partition.

First, my wireless card in my computer is sour, so I bought a wireless USB adapter. It works for Vista, but I don't know how to get it to work for Ubuntu. Wireless Network Connection doesn't appear in my list of network settings (all it offers is wired connection an pt to pt connection). How do I configure the wireless adapter I bought to Ubuntu?

Next, my desktop for Ubuntu is shifted about 1/8 to the right with the left most 1/8 of my screen black (my mouse can't even go there). The desktop falls off the other side of the screen. 
I tried fixing it in xvidtune and it worked until I restarted.

Help would be much appreciated. Thanks in advance.

---

### Post by Peter09 on 2008-10-26
can you post the output of

```
lshw -C network
```

and
```
ifconfig
```

---

### Post by qdlbp on 2008-10-26
For lshw -C network:

*-network UNCLAIMED
description: Ethernet controller
product:AR5413 802.11abg NIC
vendor: Atheros Communications Inc.
physical id: 9
bus info: pci@0000:03:09.0
version: 01
width: 32bits
clock:33MHz
capabilities: cap_list
configuration: latency=68 maxlatency=28 mingnt=10

for ifconfig:

eth0      Link encap:Ethernet  HWaddr 00:1a:92:2e:d3:9c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2176 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2176 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:108800 (106.2 KB)  TX bytes:108800 (106.2 KB)

---

### Post by Peter09 on 2008-10-26
Here is a thread about your wireless card - looks a bit of a problem

[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=778726](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=778726)

---

### Post by prismpirate on 2008-10-26
Could you post a screenshot of your off centered screen? I used to have a problem similar to this, and I might help.

---

### Post by qdlbp on 2008-10-29
I actually can't take a screen shot of the effect. Every time I try, it shows up as having the entire screen in view. How did you fix your problem? It would at least be something I can try.

The login screen is off center as well as the desktop by about 1/8 the width of the screen. This is on Ubuntu only. I have full screen in Vista.

---

### Post by Kevbert on 2008-10-29
For the display problem you need to have a wired connection to the internet (or wireless working). Your offset screen is probably due to the generic display driver being use by Ubuntu. You need to get the proper driver installed.  Firstly you want to go to System-Administration-Software Sources and check that all four top boxes on the Ubuntu tab are ticked and Important, Recommended and Unsupported boxes are ticked on the Updates tab.
Now if you go to System-Administration-Hardware Drivers are there any Device drivers shown as not being in use (one should be your display adapter). Enable it by ticking the box. Firmware drivers should now be installed (it may take a little while to download).
If this does not work please enter in Terminal
```
lspci
```
and post back the result (the display adapter will probably be the last item).

---

