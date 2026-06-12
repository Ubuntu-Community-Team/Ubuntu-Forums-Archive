---
title: "Input signal out of range - instead of grub screen."
date: 2012-11-19
forum: New to Ubuntu
---

### Post by r3bol on 2012-11-19
I recently got a second hand PC and installed xubuntu on it. At boot though, instead of the grub screen, I would get the message:
"Input signal out of range. Change settings to 60hz 1280x1024."
...but ignored it, because after about 5 seconds the OS would boot as expected.

After several boots though, it will stop booting normally and will be stuck on the 'Input signal out of range' message.
I can boot with the xubuntu a live USB disk I created for the install though.

I looked around on the web and found: [http://askubuntu.com/questions/189566/input-signal-out-of-range-change-settings-to-1600-x-900](http://askubuntu.com/questions/189566/input-signal-out-of-range-change-settings-to-1600-x-900) 

So I did like the post suggested, but the problem remains. I also tried to enter my monitors resolution instead of 640x480.

So, what do you think?

Other stuff I've tried...
I tried other monitors and an old hard drive which has Linux mint installed and got the same message. 

Here is my grub file. 

```
cat /etc/default/grub

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
# info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"


```
Here is my hardware info...
```
evian@evian:~$ sudo lspci -v
[sudo] password for evian: 
00:00.0 Host bridge: Advanced Micro Devices [AMD] nee ATI Radeon Xpress 200 Host Bridge (rev 01)
	Subsystem: Micro-Star International Co., Ltd. Device 7254
	Flags: bus master, 66MHz, medium devsel, latency 64
	Memory at <ignored> (64-bit, non-prefetchable)

00:01.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI RS480 PCI Bridge (prog-if 00 [Normal decode])
	Flags: bus master, 66MHz, medium devsel, latency 99
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=68
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: fde00000-fdefffff
	Prefetchable memory behind bridge: d0000000-dfffffff
	Capabilities: [b0] Subsystem: Advanced Micro Devices [AMD] nee ATI RS480 PCI Bridge
	Kernel modules: shpchp

00:12.0 IDE interface: Advanced Micro Devices [AMD] nee ATI IXP SB400 Serial ATA Controller (rev 80) (prog-if 8f [Master SecP SecO PriP PriO])
	Subsystem: Micro-Star International Co., Ltd. Device 7254
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 22
	I/O ports at ff00 [size=8]
	I/O ports at fe00 [size=4]
	I/O ports at fd00 [size=8]
	I/O ports at fc00 [size=4]
	I/O ports at fb00 [size=16]
	Memory at fdfff000 (32-bit, non-prefetchable) [size=512]
	[virtual] Expansion ROM at 78000000 [disabled] [size=512K]
	Capabilities: [60] Power Management version 2
	Capabilities: [50] MSI: Enable- Count=1/1 Maskable- 64bit-
	Kernel driver in use: sata_sil
	Kernel modules: sata_sil

00:13.0 USB controller: Advanced Micro Devices [AMD] nee ATI IXP SB400 USB Host Controller (rev 80) (prog-if 10 [OHCI])
	Subsystem: Micro-Star International Co., Ltd. Device 7254
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
	Memory at fdffe000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:13.1 USB controller: Advanced Micro Devices [AMD] nee ATI IXP SB400 USB Host Controller (rev 80) (prog-if 10 [OHCI])
	Subsystem: Micro-Star International Co., Ltd. Device 7254
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
	Memory at fdffd000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:13.2 USB controller: Advanced Micro Devices [AMD] nee ATI IXP SB400 USB2 Host Controller (rev 80) (prog-if 20 [EHCI])
	Subsystem: Micro-Star International Co., Ltd. Device 7254
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
	Memory at fdffc000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [dc] Power Management version 2
	Kernel driver in use: ehci_hcd

00:14.0 SMBus: Advanced Micro Devices [AMD] nee ATI IXP SB400 SMBus Controller (rev 82)
	Subsystem: Micro-Star International Co., Ltd. Device 7254
	Flags: 66MHz, medium devsel
	I/O ports at 0500 [size=16]
	Memory at 78080000 (32-bit, non-prefetchable) [size=1K]
	Kernel driver in use: piix4_smbus
	Kernel modules: i2c-piix4

00:14.1 IDE interface: Advanced Micro Devices [AMD] nee ATI IXP SB400 IDE Controller (rev 80) (prog-if 82 [Master PriP])
	Subsystem: Micro-Star International Co., Ltd. Device 7254
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at f900 [size=16]
	Capabilities: [70] MSI: Enable- Count=1/1 Maskable- 64bit-
	Kernel driver in use: pata_atiixp
	Kernel modules: pata_atiixp

00:14.2 Audio device: Advanced Micro Devices [AMD] nee ATI IXP SB4x0 High Definition Audio Controller (rev 01)
	Subsystem: Micro-Star International Co., Ltd. Device 7254
	Flags: bus master, slow devsel, latency 64, IRQ 16
	Memory at fdff4000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Capabilities: [60] MSI: Enable- Count=1/1 Maskable- 64bit+
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd-hda-intel

00:14.3 ISA bridge: Advanced Micro Devices [AMD] nee ATI IXP SB400 PCI-ISA Bridge (rev 80)
	Subsystem: Micro-Star International Co., Ltd. Device 7254
	Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: Advanced Micro Devices [AMD] nee ATI IXP SB400 PCI-PCI Bridge (rev 80) (prog-if 01 [Subtractive decode])
	Flags: bus master, VGA palette snoop, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=64
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: fdd00000-fddfffff
	Prefetchable memory behind bridge: fdc00000-fdcfffff

01:05.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RC410 [Radeon Xpress 200] (prog-if 00 [VGA controller])
	Subsystem: Micro-Star International Co., Ltd. Device 7254
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
	Memory at d0000000 (32-bit, prefetchable) [size=256M]
	I/O ports at ee00 [size=256]
	Memory at fdef0000 (32-bit, non-prefetchable) [size=64K]
	[virtual] Expansion ROM at fde00000 [disabled] [size=128K]
	Capabilities: [50] Power Management version 2
	Capabilities: [80] MSI: Enable- Count=1/1 Maskable- 64bit-
	Kernel driver in use: radeon
	Kernel modules: radeon

02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
	Subsystem: Micro-Star International Co., Ltd. Device 254c
	Flags: bus master, medium devsel, latency 64, IRQ 23
	I/O ports at de00 [size=256]
	Memory at fddff000 (32-bit, non-prefetchable) [size=256]
	Capabilities: [50] Power Management version 2
	Kernel driver in use: 8139too
	Kernel modules: 8139too, 8139cp

```

Thanks in advance :)

---

### Post by oldfred on 2012-11-19
Is your Radeon older? I do not know AMD as I have nVidia.

Advanced Micro Devices [AMD] nee ATI RC410 [Radeon Xpress 200] (prog-if 00 [VGA controller])

       
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_1210_amdstock&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_1210_amdstock&num=1)
On the proprietary driver side, the AMD Catalyst 12.11 Beta Linux graphics driver was used. For this initial testing, three discrete graphics cards from the AMD Radeon HD 5000/6000 series were used, since pre-HD5000 graphics cards are now on the Catalyst Legacy driver and the latest-generation Radeon HD 7000 series hardware still doesn't fully work with the open-source Gallium3D "RadeonSI" driver.

   This repository provides AMD Catalyst drivers for legacy graphics Radeon HD 2xxx - 4xxx for Ubuntu 12.10 Quantal Quetzal.
[https://launchpad.net/~makson96/+archive/fglrx](https://launchpad.net/~makson96/+archive/fglrx)


       
 [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)
[http://ubuntuforums.org/showthread.php?t=1558406](http://ubuntuforums.org/showthread.php?t=1558406)

---

### Post by r3bol on 2012-11-21
> **oldfred said:**
> Is your Radeon older? I do not know AMD as I have nVidia.

Advanced Micro Devices [AMD] nee ATI RC410 [Radeon Xpress 200] (prog-if 00 [VGA controller])

       
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_1210_amdstock&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_1210_amdstock&num=1)
On the proprietary driver side, the AMD Catalyst 12.11 Beta Linux graphics driver was used. For this initial testing, three discrete graphics cards from the AMD Radeon HD 5000/6000 series were used, since pre-HD5000 graphics cards are now on the Catalyst Legacy driver and the latest-generation Radeon HD 7000 series hardware still doesn't fully work with the open-source Gallium3D "RadeonSI" driver.

   This repository provides AMD Catalyst drivers for legacy graphics Radeon HD 2xxx - 4xxx for Ubuntu 12.10 Quantal Quetzal.
[https://launchpad.net/~makson96/+archive/fglrx](https://launchpad.net/~makson96/+archive/fglrx)


       
 [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)
[http://ubuntuforums.org/showthread.php?t=1558406](http://ubuntuforums.org/showthread.php?t=1558406)
Hi I was following the steps on the second link, but the last step I get...
> evian@evian:~$ sudo apt-get install fglrx-legacy
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package fglrx-legacy


Any advise?

---

