---
title: "My iMac hates Ubuntu!"
date: 2008-07-08
forum: New to Ubuntu
---

### Post by silvine on 2008-07-08
Hi All,

I installed Ubuntu on my iMac last week and am having a few problems. I am trying to enable the full graphics effects on the desktop, as I want to see the famous Cube in action.

When I run Ubuntu from boot, it fails to recognise the wireless card of my iMac (latest model). This means I can't connect to the internet and download the drivers I want to get the cube working. I've even tried plugging my router into the iMac but this didn't work. 

To further complicate things, I am booting  into Ubuntu via Vista, through Bootcamp. OSX wouldn't recognise my Ubuntu disc, but my Vista  installation does.

When I install Ubuntu on a virtualised machine on OSX, using VMWare, it recognises the wireless card. However, it won't recognise my graphics card. I downloaded all the recommended updates but it still won't activate the full grapgics effects.

I understand VMware is picky about what graphics effects it will do. However, I can't figure out why Ubuntu won't regonise my wireless networking card. 


Please help.

PS Free software rocks

---

### Post by ChameleonDave on 2008-07-08
I'm not a Mac user, so I don't know much about your hardware.

Enter the following command into a terminal:

```

lspci -v

```

Paste the output here.  Use the "#" button to format it as quoted code.  It'll make it easier to read.

The info may help someone to help you.

---

### Post by wolfen69 on 2008-07-08
please remember to give specifications when asking for help. your post is akin to "help me, my car wont run". you get the idea.

---

### Post by ChameleonDave on 2008-07-08
> **wolfen69 said:**
> please remember to give specifications when asking for help. your post is akin to "help me, my car wont run". you get the idea.

Hey, he said it was the latest iMac.  That's more info than most newbies give!

Silvine, post the output of these commands too:

```

uname -a
cat /etc/lsb-release

```

Also have a look in the menu System --> Administration --> Networking.  Is there anything you can configure?

---

### Post by avtolle on 2008-07-08
I'd also suggest he take a look at the Apple Users Forum [http://ubuntuforums.org/forumdisplay.php?s=&daysprune=&f=328](http://ubuntuforums.org/forumdisplay.php?s=&daysprune=&f=328) to see whether there are any helpful threads there. NB, the Apple Users Forum deals with intel based Macs as well as the older PPC Macs.

---

### Post by silvine on 2008-07-08
Hi Folks, 

Here's what I got when I typed the commands into the terminal operating under Vmware in OSX. I'll have a look at that other forum too, thanks avtolle.

```
 
Linux bryan-desktop 2.6.24-19-generic #1 SMP Wed Jun 18 14:43:41 UTC 2008 i686 GNU/Linux

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.04
DISTRIB_CODENAME=hardy
DISTRIB_DESCRIPTION="Ubuntu 8.04.1"


00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 01)
	Subsystem: VMware Inc Virtual Machine Chipset
	Flags: bus master, medium devsel, latency 0

00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 01) (prog-if 00 [Normal decode])
	Flags: bus master, 66MHz, medium devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=64

00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 08)
	Subsystem: VMware Inc Virtual Machine Chipset
	Flags: bus master, medium devsel, latency 0

00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01) (prog-if 8a [Master SecP PriP])
	Subsystem: VMware Inc Virtual Machine Chipset
	Flags: bus master, medium devsel, latency 64
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
	I/O ports at 1050 [size=16]

00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (prog-if 00 [UHCI])
	Subsystem: VMware Inc Virtual Machine Chipset
	Flags: bus master, medium devsel, latency 64, IRQ 18
	I/O ports at 1060 [size=32]

00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 08)
	Subsystem: VMware Inc Virtual Machine Chipset
	Flags: medium devsel, IRQ 9

00:0f.0 VGA compatible controller: VMware Inc Abstract SVGA II Adapter (prog-if 00 [VGA controller])
	Subsystem: VMware Inc Abstract SVGA II Adapter
	Flags: bus master, medium devsel, latency 64
	I/O ports at 1400 [size=16]
	Memory at f0000000 (32-bit, non-prefetchable) [size=128M]
	Memory at e8000000 (32-bit, non-prefetchable) [size=8M]
	[virtual] Expansion ROM at 40000000 [disabled] [size=32K]

00:10.0 SCSI storage controller: LSI Logic / Symbios Logic 53c1030 PCI-X Fusion-MPT Dual Ultra320 SCSI (rev 01)
	Flags: bus master, medium devsel, latency 64, IRQ 17
	I/O ports at 1080 [size=128]
	Memory at e8800000 (32-bit, non-prefetchable) [size=4K]
	[virtual] Expansion ROM at 40008000 [disabled] [size=16K]

00:11.0 PCI bridge: VMware Inc Unknown device 0790 (rev 02) (prog-if 01 [Subtractive decode])
	Flags: bus master, medium devsel, latency 64
	Memory at e8801000 (64-bit, non-prefetchable) [size=4K]
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=68
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: e8900000-e89fffff
	Capabilities: <access denied>

02:00.0 Ethernet controller: Advanced Micro Devices [AMD] 79c970 [PCnet32 LANCE] (rev 10)
	Subsystem: Advanced Micro Devices [AMD] PCnet - Fast 79C971
	Flags: bus master, medium devsel, latency 64, IRQ 16
	I/O ports at 2000 [size=128]
	[virtual] Expansion ROM at e8910000 [disabled] [size=64K]

02:01.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 02)
	Subsystem: Ensoniq Creative Sound Blaster AudioPCI64V, AudioPCI128
	Flags: bus master, ?? devsel, latency 64, IRQ 18
	I/O ports at 2080 [size=64]

02:02.0 USB Controller: VMware Inc Abstract USB2 EHCI Controller (prog-if 20 [EHCI])
	Subsystem: VMware Inc Abstract USB2 EHCI Controller
	Flags: bus master, fast devsel, latency 64, IRQ 19
	Memory at e8900000 (32-bit, non-prefetchable) [size=4K]

bryan@bryan-desktop:~$ 

```

---

### Post by ChameleonDave on 2008-07-08
> **silvine said:**
> Hi Folks, 

Here's what I got when I typed the commands into the terminal operating under Vmware in OSX. I'll have a look at that other forum too, thanks avtolle.

Well, I was thinking more of running that command on Ubuntu directly on your hardware.  Running it on VMware just tells us that... you're running Ubuntu on VMware.  ;-)

For your VMware problem, I suspect that you might need to install the packages *open-vm-tools* and *open-vm-tools-gui*.  Similar software is necessary to make my guest OSes work correctly with VirtualBox.

---

