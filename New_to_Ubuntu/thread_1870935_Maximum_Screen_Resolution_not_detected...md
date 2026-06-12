---
title: "Maximum Screen Resolution not detected.."
date: 2011-10-28
forum: New to Ubuntu
---

### Post by Guruprasad on 2011-10-28
Sometimes my Ubuntu 10.1 can not detect the monitors highest screen resolution. Whereas sometimes it does. 

How can we fix this problem?

---

### Post by ofnuts on 2011-10-28
> **Guruprasad said:**
> Sometimes my Ubuntu 10.1 can not detect the monitors highest screen resolution. Whereas sometimes it does. 

How can we fix this problem?
Ubuntu 10.1? What release is that? 10.10?

Telling us what display hardware you have ("lspci", "lshw -class display" commands, and what it's supposed to be, in case you spot discrepancies) would be a good idea.

---

### Post by Guruprasad on 2011-10-28
Yes I mean 10.10 version

> $ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: ASUSTeK Computer Inc. RS880 PCI to PCI bridge (int gfx)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3c)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc 760G [Radeon 3000]
02:00.0 Ethernet controller: Atheros Communications AR8131 Gigabit Ethernet (rev c0)
03:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)



>  sudo lshw -class display
[sudo] password for guruprasad: 
  *-display               
       description: VGA compatible controller
       product: 760G [Radeon 3000]
       vendor: ATI Technologies Inc
       physical id: 5
       bus info: pci@0000:01:05.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:18 memory:d0000000-dfffffff ioport:c000(size=256) memory:fe9f0000-fe9fffff memory:fe800000-fe8fffff


---

### Post by ofnuts on 2011-10-28
> **Guruprasad said:**
> 
```
*-display               
       description: VGA compatible controller
       product: 760G [Radeon 3000]
       vendor: ATI Technologies Inc
       physical id: 5
       bus info: pci@0000:01:05.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:18 memory:d0000000-dfffffff ioport:c000(size=256) memory:fe9f0000-fe9fffff memory:fe800000-fe8fffff 			 		
```
It's getting out of my competence by IIRC for Radeon you have the choice between the politically correct open source driver or the closed source driver from Radeon. Which one did you use?

---

### Post by fantab on 2011-10-28
> **Guruprasad said:**
> Sometimes my Ubuntu 10.1 can not detect the monitors highest screen resolution. Whereas sometimes it does. 

How can we fix this problem?

Perhaps you will have to force the required resolution, if it is supported, using xrandr... See [this LINK]("http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html"). 

I hope this helps.

---

### Post by CatKiller on 2011-10-29
> **Guruprasad said:**
> Sometimes my Ubuntu 10.1 can not detect the monitors highest screen resolution. Whereas sometimes it does. 

How can we fix this problem?

The fact that it works sometimes is very encouraging. Resolution detection works by EDID, where your monitor tells the system which resolutions it can do. Is there a pattern to when it doesn't work? You'll probably have most luck with the monitor powered up before the computer tries to boot and without using a KVM or similar.

If there's no discernable pattern, we can look at logs when it works and when it doesn't to try to discover where the problem lies.

---

### Post by Guruprasad on 2011-10-30
> **CatKiller said:**
> The fact that it works sometimes is very encouraging. Resolution detection works by EDID, where your monitor tells the system which resolutions it can do. Is there a pattern to when it doesn't work? You'll probably have most luck with the monitor powered up before the computer tries to boot and without using a KVM or similar.

If there's no discernable pattern, we can look at logs when it works and when it doesn't to try to discover where the problem lies.

The monitor was getting detected for almost a year without any problem. Just recently the problem started. Often it does not work when the computer starts. But sometimes it start working when we log off.

I opend monitor preferences where it shows unknown monitor. I clicked Detect Monitor button and following is the output in sys.log
> 
Oct 30 19:06:17 guruprasad kernel: [ 1235.472307] [drm:radeon_vga_detect] *ERROR* VGA-1: probed a monitor but no|invalid EDID
Oct 30 19:06:17 guruprasad kernel: [ 1235.473138] i2c i2c-0: sendbytes: NAK bailout.

Can you make out anything out of this log?

---

### Post by Guruprasad on 2011-10-30
> **ofnuts said:**
> It's getting out of my competence by IIRC for Radeon you have the choice between the politically correct open source driver or the closed source driver from Radeon. Which one did you use?

I was under the impression that I am using some fglrx closed source driver but when now when I check  Administration > Additional Drivers the it shows "No proprietary drivers used on this system."

---

### Post by matt_symes on 2011-10-30
Hi

> **Guruprasad said:**
> I was under the impression that I am using some fglrx closed source driver but when now when I check  Administration > Additional Drivers the it shows "No proprietary drivers used on this system."
> 
configuration: **driver=radeon** latency=0You are using the open source radeon driver.

Kind regards

---

### Post by Guruprasad on 2011-10-30
> **fantab said:**
> Perhaps you will have to force the required resolution, if it is supported, using xrandr... See [this LINK]("http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html"). 

I hope this helps.

I followed the steps mentioned in the link you gave. It added the highest resolution to my Ubuntu and everything works fine. Thank you very much to all.

---

