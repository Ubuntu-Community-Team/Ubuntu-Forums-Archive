---
title: "Laptop Monitor Wrong Resolution"
date: 2012-02-02
forum: New to Ubuntu
---

### Post by BarnOwl on 2012-02-02
This is 64-bit Unbuntu 10.04. I was setting it up for my wife. I use an external monitor but, that's not how it will be used when she uses it.  Somehow it's detecting the wrong resolution for the laptop monitor even if I boot it off an install CD.

Booted off the install CD

Without the external monitor, the laptop monitor comes up at the wrong resolution.

If I plug in the external monitor, by default the external monitor will work but, the laptop monitor won't.  It looks like Linux is detecting 1220 X 800 resolution when it's 1024 X 768.  I can only get the laptop monitor to work when I don't mirror the displays in preferences and I set it to 1024 X 768.  If I turn off the external monitor in preferences or try to mirror with the resolution set to 1024 X 768, the laptop monitor goes to the wrong resolution.

I'm willing to reinstall, if necessary but, I'll have to use the external monitor.

Any ideas?

---

### Post by cortman on 2012-02-02
Have you tried running

```
xrandr --auto
```

?? If that doesn't fix the resolution, you can manually set it as well with the xrandr command. Type

```
xrandr -s 1024x768
```

---

### Post by wolfen69 on 2012-02-02
Post the output of
```
lspci
```

---

### Post by BarnOwl on 2012-02-03
Thank you both for the replies.

> **cortman said:**
> Have you tried running

```
xrandr --auto
```

?? If that doesn't fix the resolution, you can manually set it as well with the xrandr command. Type

```
xrandr -s 1024x768
```

Neither of those had any effect.

> **wolfen69 said:**
> Post the output of
```
lspci
```

It was a little tricky transferring but, here it is:

```
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 13)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS482 [Radeon Xpress 200M]
05:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
08:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
08:01.0 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
08:01.1 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 01)
```

---

### Post by BarnOwl on 2012-02-05
I got it to work.  I'm not entirely sure why.  I was wrong about the resolution alone being the issue.  I booted in safe mode and it came up with 1280x800 resolution.  

Then I tried an xorg.conf file and turned off vatious options in the redeon driver.  No luck there. I tried the ATI driver instead of radeon.  No change.  The vesa driver caused it to come up in failsafe.  I tried the fbdev driver (That's what failsafe uses).  That worked but, the video was too slow.  

Finally I read an article about the FGLRX driver.  I thought that was for newer ATI cards than mine but, it indicated that it had some updates to the radeon driver.  I loaded it and renamed my xorg.conf file. That didn't work but, the xorg log file indicated that it tried all kinds of drivers before settling on one that didn't work.  So, I put my xorg.conf file back and specified the radeon driver again.  That worked.

I'm not sure why though.

---

