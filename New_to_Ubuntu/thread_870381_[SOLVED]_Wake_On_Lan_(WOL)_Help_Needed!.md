---
title: "[SOLVED] Wake On Lan (WOL) Help Needed!"
date: 2008-07-25
forum: New to Ubuntu
---

### Post by master_kernel on 2008-07-25
I have set up wake-on-lan according to the instructions in this thread: [http://ubuntuforums.org/showthread.php?t=234588](http://ubuntuforums.org/showthread.php?t=234588)

It is configured for the onboard NIC using interface eth1. Whenever I shut down the machine from Ubuntu Hardy, sending the magic packet from a network machine does not work; however, if I turn the computer on until the BIOS screen comes up and then press the power button < 4 seconds to turn it off, and then send a magic packet, it works!

Output from lspci:
> 00:05.0 Bridge: nVidia Corporation CK8S Ethernet Controller (rev a2)
The onboard controller uses the forcedeth ethernet driver.

/proc/acpi/wakeup:
> Device	S-state	  Status   Sysfs node
PS2K	  S4	 disabled  pnp:00:0a
PS2M	  S4	 disabled  pnp:00:0b
UAR1	  S4	 disabled  pnp:00:0e
UAR2	  S4	 disabled  pnp:00:0f
USB0	  S4	 disabled  pci:0000:00:02.0
MAC	  S5	 enabled   pci:0000:00:05.0
USB1	  S4	 disabled  pci:0000:00:02.1
USB2	  S4	 disabled  pci:0000:00:02.2
P0P1	  S4	 disabled  pci:0000:00:0e.0

System Specs:
ASUS K8N-E Deluxe Motherboard
nForce3 Chipset
AMD Athlon 64 2800+

Any help is appreciated!

---

### Post by damis648 on 2008-07-25
Is WOL enabled in the BIOS? If it wasn't I suppose it wouldn't work at all but best to make sure.

---

### Post by master_kernel on 2008-07-25
It is. Also, here is the output from ethtool eth1:
> 
I'll add it in once I get it.

---

### Post by master_kernel on 2008-07-26
Output from ethtool eth1:
> Settings for eth1:
	Supported ports: [ MII ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Advertised auto-negotiation: Yes
	Speed: 100Mb/s
	Duplex: Full
	Port: MII
	PHYAD: 1
	Transceiver: external
	Auto-negotiation: on
	Supports Wake-on: g
	Wake-on: g
	Link detected: yes


I can see the light on the ethernet port when the computer is powered off.

---

### Post by master_kernel on 2008-07-26
**UPDATE:** WOL does work from S3/S4 states (suspend/hibernate), but not from poweroff(S5) unless I quickly turn it on an off by using the power button.

---

### Post by master_kernel on 2008-07-28
*bump*

---

### Post by master_kernel on 2008-07-28
**Solved,** thanks to this post by majoridiot: [http://ubuntuforums.org/showpost.php?p=2186749&postcount=22](http://ubuntuforums.org/showpost.php?p=2186749&postcount=22)

I had to disable RTC wakeup in my BIOS.

Master Kernel

---

