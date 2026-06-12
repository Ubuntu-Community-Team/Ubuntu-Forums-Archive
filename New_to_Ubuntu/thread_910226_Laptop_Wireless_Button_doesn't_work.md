---
title: "Laptop Wireless Button doesn't work"
date: 2008-09-04
forum: New to Ubuntu
---

### Post by Matuku on 2008-09-04
Pressing the wireless button on the laptop fails to turn the wireless on; is there a way to see whether the wireless itself isn't working or if it's just the button? I.e. is there a way to turn the wireless on manually?

---

### Post by bobnutfield on 2008-09-04
Type in a terminal:

> sudo ifconfig -a

This will identify which network devices are recognized on your system.  The button is a hardware device and wireless must be set up on the operating system first.

---

### Post by pmlxuser on 2008-09-04
if you duo boot try switching it on in windows and see if things change.

say is you wireless switch just one button or a combination of keys?

---

### Post by Matuku on 2008-09-04
> **pmlxuser said:**
> if you duo boot try switching it on in windows and see if things change.

say is you wireless switch just one button or a combination of keys?

A single button, next to the power button.

---

### Post by Matuku on 2008-09-04
> **bobnutfield said:**
> 
This will identify which network devices are recognized on your system.  The button is a hardware device and wireless must be set up on the operating system first.

Here's the output:
```

eth0      Link encap:Ethernet  HWaddr 00:1d:72:65:62:99  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:222 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1620 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1620 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:81000 (79.1 KB)  TX bytes:81000 (79.1 KB)

```

I assume that means the wireless isn't working? (on another note, neither is my ethernet)

---

### Post by bobnutfield on 2008-09-04
Your ethernet is being recognized and probably just needs to be configured.  But unfortunately, you are correct the wireless is not being recognized, but that does mean that it can't still be enabled.

Do you know what wireless chip is in your laptop?  For your ethernet, first try to go to System>Network and see if your ethernet can be enabled from there.  You should see an entry for a wired connection.  If you do, it should not be difficult to enable it.

---

### Post by Matuku on 2008-09-04
From another thread I got this output from the terminal
```

 *-network               
       description: Ethernet interface
       product: nVidia Corporation
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1d:72:65:62:99
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.61 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:07:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0

```

> **porchrat said:**
> 

Your card is an AR242x...also known as an atheros AR5007, or just 5007 sometimes.

So it appears that it's not that the button isn't working, it's the wireless itself? If that's the case I'll have to try Madwifi I guess (or NDISwrapper).

---

