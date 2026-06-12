---
title: "adding new hardware Should I expect any problems"
date: 2008-05-13
forum: New to Ubuntu
---

### Post by Shadowmeph on 2008-05-13
I am adding some hardware to my computer the first thing I am adding is a n Xonare XD PCI express7.1 soundcard to replace the onboard sound and the second thing I am adding is an intel pro/1000 GT Gigabit PCI network card to replace onboard. Now  is there going to be any problems doing this? I am asking because I am not sure if Ubuntu will auto detect changes in my hardware.

---

### Post by SunnyRabbiera on 2008-05-13
it shouldnt, as usually ubuntu is good with hardware detection.
as long as both do have some compatibility with linux, your intel wireless card will probably work as usually linux is good with them...
not sure on the soundcard though

---

### Post by philinux on 2008-05-13
Only thing you need to do is change the bios settings to the new hardware.

---

### Post by ToSsMaStR on 2008-05-13
check out [www.ubuntuhcl.org](www.ubuntuhcl.org) - If your hardware is not there, but sure to add it :-)

---

### Post by Shadowmeph on 2008-05-13
> **ToSsMaStR said:**
> check out [www.ubuntuhcl.org](www.ubuntuhcl.org) - If your hardware is not there, but sure to add it :-)

hmm well it didn't detect my card so I will try there site

---

### Post by Inxsible on 2008-05-13
yup, you should always expect problems when you add new hardware to an existing installation. Some problems are just harder than others, but there are always problems.

---

### Post by Shadowmeph on 2008-05-13
> **Shadowmeph said:**
> hmm well it didn't detect my card so I will try there site

Hmm and of course they don't have Linux drivers :( hoe can I tell if the system even see's the card?

---

### Post by mlentink on 2008-05-13
> **Shadowmeph said:**
> Hmm and of course they don't have Linux drivers :( hoe can I tell if the system even see's the card?

```
sudo lspci
```

will list all pci adapters in your box

---

### Post by Shadowmeph on 2008-05-13
> **mlentink said:**
> ```
sudo lspci
```

will list all pci adapters in your box

Hmm this is what comes up ( my sound card is PCI express not sure if that matters)

```
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IB (ICH9) LPC Interface Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801IB (ICH9) 4 port SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon HD 3870
01:00.1 Audio device: ATI Technologies Inc Radeon HD 3870 Audio device
03:00.0 PCI bridge: PLX Technology, Inc. PEX8112 x1 Lane PCI Express-to-PCI Bridge (rev aa)
04:04.0 Multimedia audio controller: C-Media Electronics Inc CMI8788 [Oxygen HD Audio]
05:00.0 IDE interface: JMicron Technologies, Inc. JMB368 IDE controller
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
07:02.0 Ethernet controller: Intel Corporation 82541PI Gigabit Ethernet Controller (rev 05)

```

---

### Post by Shadowmeph on 2008-05-13
ok so I am going to take a logical guess and say that the card is listed as 
> Multimedia audio controller: C-Media Electronics Inc CMI8788 [Oxygen HD Audio so that would mean that this driver > CMI8788 driver should work but the thing is it says> Quick install
=============

1) You must have full configured source for the Linux kernel which you
   want to use for the ALSA drivers. Note that ALSA drivers are part
   of the kernel, so there is necessary to resolve all symbol dependencies
   between the used kernel and ALSA driver code. Partly installed kernels
   (for example from distributor makers) can be unuseable for this action.

2) You must turn on sound support (soundcore module).

3) Run './configure' script.

 * General Options
   If you do not want ISA PnP support, use --with-isapnp=no switch.
   If you do not want sequencer support, use --with-sequencer=no switch.
   If you do not want OSS/Free emulation, use --with-oss=no switch.
   If you have udev or devfs and want to use more than eight cards, use
   --enable-dynamic-minors switch.
   If you want to turn on debug mode, use --with-debug=full switch.
   If you want to debug soundcard detection, try --with-debug=detect switch.

 * Kernel Source Tree
   On 2.4/2.6 kernels, the location of the kernel source tree is
   parsed automatilly from the running kernel.
   If it's not in the standard place, specify the path via
   --with-kernel=<kernel_directory>. 
   On 2.6 kernels, the build directory has to be given via
   --with-build=<kernel_build_dir> option additionally, too.

 * Drivers to Compile
   The card drivers to be compiled can be selected via --with-cards option.
   Pass the card driver name without "snd-" prefix.  To specify
   multiple drivers, list names with comma (,).
   Passing "all" will compile all possible drivers (and this is the
   default choice).
   Some drivers have compile options.  They can be passed via
   --with-card-options option.  Multiple options can be passed with comma,
   too.  The default is "all".
   For available cards and options, see ./configure --help.

 * Example
      ./configure --with-debug=full
      ./configure --with-cards=sb16,emu10k1 --with-card-options=sb16-csp
 now I am not sure how to do this

---

### Post by Motorhead Kaze on 2008-07-01
Hi, this is not in line with the sound card/driver issue, but can you tell me how to FIND HARDWARE that isn't showing up?

For some reason, today, on a new install of Hardy my second monitor does not show in xrandr or in screen resolution. Where is the device locater tool?

---

