---
title: "My WiFi issues"
date: 2008-11-20
forum: New to Ubuntu
---

### Post by afd on 2008-11-20
Ok, we've all seen WiFi issues brought up and talked about on the various ubuntu forums / blogs but my card is still giving me jip after trying all those different 'solutions' that float about.

I have an HP G6031ea laptop. I'm not sure what the chipset/wifi card is but I reckon it's a broadcom one...

I installed 64bit Ubuntu Ibex successfully last week and then one day the wifi driver (and hardware) disappeared. I had a strop about it and went back to vista (installing a 64bit version) and the WiFi was again an issue -as HP said they wouldn't support any OS that wasn't installed by themselves- so I thought that maybe it was just the laptop not being 'ready' for 64bit OS, so I thought I'd give it another go with Ibex - this time the 32bit OS.

That's pretty much where I've got to - all attempts to use ndis wrapper and the wifi tools aren't working - I can't even i.d. the card when using "lspci" in Terminal...

The card was recognised and auto-installed under 64bit Ibex and I believe I have all the same repos now as I did under then.. Can anyone think of a way that this may be fixable?

---

### Post by rampageoberon on 2008-11-20
Thats quite strange and annoying of HP. What do you get with this command.

```
sudo lshw -C network
```

---

### Post by afd on 2008-11-20
>   *-network DISABLED      
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: d2:31:09:b4:c3:98
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes


When using the 'lspci' command the list contained ethernet devices but I was sure this was only for the 10/100 ethernet port and not the WiFi card.

---

### Post by random turnip on 2008-11-20
Are you using Ubuntu 8.04 or 8.10?

I hope you find a solution cos I have a HP and the wireless has never worked on mine yet, Im upgrading to 8.10 (runing 8.04 at the moment) tonight in hope that it will sought out my problems, although I'm not holding my breath about it.

---

### Post by rampageoberon on 2008-11-20
> **afd said:**
> When using the 'lspci' command the list contained ethernet devices but I was sure this was only for the 10/100 ethernet port and not the WiFi card.

Okay do the following command to enable the card

```
sudo ifconfig pan0 up
```

and could you please post the output of 'ifconfig' here. its a bit strange that your card is not showing up in in the lshw output.

---

### Post by afd on 2008-11-20
```
eth0      Link encap:Ethernet  HWaddr 00:1b:24:c1:51:24  
          inet addr:192.168.0.12  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:24ff:fec1:5124/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:711 errors:0 dropped:0 overruns:0 frame:0
          TX packets:728 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:728065 (728.0 KB)  TX bytes:102230 (102.2 KB)
          Interrupt:22 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:253 errors:0 dropped:0 overruns:0 frame:0
          TX packets:253 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:16680 (16.6 KB)  TX bytes:16680 (16.6 KB)

pan0      Link encap:Ethernet  HWaddr fe:d6:28:79:b1:7b  
          inet6 addr: fe80::fcd6:28ff:fe79:b17b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:468 (468.0 B)

```

Random Turnip - I'm running Ibex (8.10) 32bit after the 64bit version had the WiFi usage drop off out of the blue. If you're lucky the Network Manager in Ibex will set your drivers to use proprietary versions straight out of the box as mine did on the 64bit version.

Thanks for all your help with this :D One thing you can't fault with Ubuntu is the community!

---

### Post by afd on 2008-11-20
I'm guessing the pan0 details are what applies to my wifi card but I'm still not seeing it under the network icon on the desktop panel.  Also I tried using System/Administration/Hardware Drivers once I'd used "sudo ifconfig pan0 up" in Terminal and it still didn't know I had the hardware to have a driver problem with :@

Any more takers?

---

### Post by bobnutfield on 2008-11-20
Post the results of

> lspci -v 

and also

> dmesg | tail

The lspci result will identify if the system recognizes the wireless chipset at all.  I do not believe pan0 is your wireless.

dmesg will also tell you what network devices were found at boot up.

---

### Post by afd on 2008-11-20
Hi Bob,

Here's what you asked for.

"lspci -v" gives:

> 
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
	Subsystem: Hewlett-Packard Company Device 30b7
	Flags: bus master, 66MHz, fast devsel, latency 0
	Capabilities: <access denied>

00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
	Subsystem: Hewlett-Packard Company Device 30b7
	Flags: 66MHz, fast devsel

00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
	Subsystem: Hewlett-Packard Company Device 30b7
	Flags: 66MHz, fast devsel

00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
	Subsystem: Hewlett-Packard Company Device 30b7
	Flags: 66MHz, fast devsel

00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
	Subsystem: Hewlett-Packard Company Device 30b7
	Flags: bus master, 66MHz, fast devsel, latency 0

00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
	Subsystem: Hewlett-Packard Company Device 30b7
	Flags: bus master, 66MHz, fast devsel, latency 0
	Capabilities: <access denied>

00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
	Subsystem: Hewlett-Packard Company Device 30b7
	Flags: 66MHz, fast devsel

00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
	Flags: 66MHz, fast devsel

00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 00004000-00004fff
	Memory behind bridge: b4000000-b7ffffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000d01fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 00005000-00005fff
	Memory behind bridge: b8000000-bbffffff
	Prefetchable memory behind bridge: 00000000d0200000-00000000d03fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:05.0 VGA compatible controller: nVidia Corporation MCP51 PCI-X GeForce Go 6100 (rev a2)
	Subsystem: Hewlett-Packard Company Device 30b7
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 19
	Memory at b2000000 (32-bit, non-prefetchable) [size=16M]
	Memory at c0000000 (64-bit, prefetchable) [size=256M]
	Memory at b1000000 (64-bit, non-prefetchable) [size=16M]
	[virtual] Expansion ROM at 88000000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidiafb, nvidia

00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
	Subsystem: Hewlett-Packard Company Device 30b7
	Flags: bus master, 66MHz, fast devsel, latency 0
	Capabilities: <access denied>

00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
	Subsystem: Hewlett-Packard Company Device 30b7
	Flags: bus master, 66MHz, fast devsel, latency 0
	I/O ports at 1d00 [size=128]

00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
	Subsystem: Hewlett-Packard Company Device 30b7
	Flags: 66MHz, fast devsel, IRQ 10
	I/O ports at 3040 [size=64]
	I/O ports at 3000 [size=64]
	Capabilities: <access denied>
	Kernel driver in use: nForce2_smbus
	Kernel modules: i2c-nforce2

00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
	Subsystem: Hewlett-Packard Company Device 30b7
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 10
	Memory at b0040000 (32-bit, non-prefetchable) [size=256K]

00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3) (prog-if 10)
	Subsystem: Hewlett-Packard Company Device 30b7
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
	Memory at b0004000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: ohci_hcd
	Kernel modules: ohci-hcd

00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3) (prog-if 20)
	Subsystem: Hewlett-Packard Company Device 30b7
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
	Memory at b0005000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd

00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1) (prog-if 8a [Master SecP PriP])
	Subsystem: Device f03c:30b7
	Flags: bus master, 66MHz, fast devsel, latency 0
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
	I/O ports at 3080 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: pata_amd
	Kernel modules: pata_amd

00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1) (prog-if 85 [Master SecO PriO])
	Subsystem: Hewlett-Packard Company Device 30b7
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
	I/O ports at 30c0 [size=8]
	I/O ports at 30b4 [size=4]
	I/O ports at 30b8 [size=8]
	I/O ports at 30b0 [size=4]
	I/O ports at 3090 [size=16]
	Memory at b0006000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: sata_nv
	Kernel modules: sata_nv

00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2) (prog-if 01)
	Flags: bus master, 66MHz, fast devsel, latency 0
	Bus: primary=00, secondary=07, subordinate=07, sec-latency=0
	Capabilities: <access denied>

00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
	Subsystem: Hewlett-Packard Company Device 30b7
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 18
	Memory at b0000000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
	Subsystem: Hewlett-Packard Company Device 30b7
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
	Memory at b0008000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at 30e0 [size=8]
	Capabilities: <access denied>
	Kernel driver in use: forcedeth
	Kernel modules: forcedeth

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
	Flags: fast devsel
	Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
	Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
	Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
	Flags: fast devsel
	Capabilities: <access denied>
	Kernel driver in use: k8temp
	Kernel modules: k8temp



"dmesg | tail" gives:

> [ 5487.751146] scsi 4:0:0:0: rejecting I/O to dead device
[ 5508.361343] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.
[ 5508.909074] usb 1-6: new full speed USB device using ohci_hcd and address 3
[ 5509.123420] usb 1-6: configuration #1 chosen from 1 choice
[ 5509.125750] cdc_acm 1-6:1.0: ttyACM0: USB ACM device
[ 5534.660385] PPP generic driver version 2.4.2
[ 5534.960397] PPP BSD Compression module registered
[ 5535.109409] PPP Deflate Compression module registered
[12022.169048] CE: hpet increasing min_delta_ns to 22500 nsec
[17680.633045] CE: hpet increasing min_delta_ns to 33750 nsec


There is obviously a cure for the driver issue - it's just finding out what the hardware is... But why it worked out of the box with 64bit Ibex and not the 32bit Ibex is beyond me but hey...

---

### Post by bobnutfield on 2008-11-20
Your network devices do not show up at all....yet the ethernet does in ifconfig with an IP address.  Rarely, an internal wireless is connected via USB.  The RTL8187B is such a device and only show up when running lsusb.  Try:

> lsusb

Just to see if the wireless shows up there.  You might need to go the HP site to enter your exact model no. and identify the wireless.  A quick check suggests that the HP G60 series have used both Atheros and Broadcom, both of which should  be detected and supported with the 2.6.27 kernel which is used in Intrepid.

---

### Post by LowSky on 2008-11-20
really strange that it doent pop up as under lspci, which means it isn't there, mabe is usb based?

type  ```
 lsusb -v
```

---

### Post by afd on 2008-11-21
running "lsusb" gives out:
> Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

I think you're right as to having to find the make and model of the card from the manufacturer... unfortunately they haven't released that info on the net and their online assistance is useless so I'm waiting on the reply to my email.

Does anyone have a clue as to how 64bit Ibex recongised the hardware but 32bit Ibex didn't?

---

### Post by afd on 2008-11-21
As is often the case with my dealing with ubuntu - some things just happen and I'm not always sure why (could be an additional set of repos that came good?).

Well the restricted drivers pop-up came along and pointed me towards fwcutter and the B43 Wireless Driver. This seemed to do 90% of the job of setting up the hardware.

The Restricted drivers section is also giving me the option of using the Broadcom STA wireless driver.

As yet I'm having difficulty using security protocols over WiFi under fwcutter.  Maybe the STA driver will help with this?

I'll be sure to post any results as I find them.

Thanks again for everyone's help getting this sorted. Would have been completely in the dark without ubuntuforums' users :D

As a final thought - I wonder if it was the repos or anything else that prompted the restricted drivers to pick up the hardware?  If I want to reinstall ubuntu at another time I'd like to know exactly what has made the Wifi work before.

---

### Post by afd on 2008-11-25
It turned out the STA driver was the one that had managed to sort out the Wifi + security.  Great! -somehow magically fixed- but great!

*deep breath*
After a restart all that had magically turned great, magically turned **** again :(

Luckily I had already looked into backup/restore scenarios and had made a tar backup file according to this thread: [http://ubuntuforums.org/showthread.php?t=35087]("http://ubuntuforums.org/showthread.php?t=35087")

Unfortunately I've experienced further problems getting the restore to take me to the exact situation I was in when the backup was created (most importantly - with working wifi) as you can read here: [http://ubuntuforums.org/showpost.php?p=6248514&postcount=742]("http://ubuntuforums.org/showpost.php?p=6248514&postcount=742")

Anyone care to assist?

ps. Once I've got this particular hardware peachy I'm writing a how-to guide for all owners of the same laptop. I might even create a distro, as I wouldn't want to see anyone else go through the pain of trying to do all this stuff from scratch.

---

### Post by afd on 2008-11-29
From what I've been told in another thread my hardware may be readable sometimes and not others - sort of off-and-on all the time, giving me the problems with wifi working with the correct drivers installed but not after reboot, hibernate etc.

At this present moment it IS working so I'm desperately trying to figure out if there's a way of solving the recognition of the hardware before it dissappears again and then forcing that setting from boot to try and get the wifi card to work every time.

---

