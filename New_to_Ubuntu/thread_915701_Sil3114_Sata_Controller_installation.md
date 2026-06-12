---
title: "Sil3114 Sata Controller installation"
date: 2008-09-10
forum: New to Ubuntu
---

### Post by AnarkistNZ on 2008-09-10
Hi everyone.

I've been using Linux for about 18 months or so now, and am generally confident doing most things now. I'm at a bit of a brick wall however with how to install hardware as I've never had to do it before.

I have a new Sil3114 Sata Controller (an STLab A-224) that I want to run a few SATA disks off as I've used the 2 onboard SATA ports already.

Here is the output of lspci

```

root@farpho:~# lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8378 [KM400/A] Chipset Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:07.0 RAID bus controller: Imagenation Corporation Unknown device 3114 (rev 02)
00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
01:00.0 VGA compatible controller: VIA Technologies, Inc. VT8378 [S3 UniChrome] Integrated Video (rev 01)

```

Once I've plugged the hardware in, where is the best place to start with it? I'm running Ubuntu Server 8.04.

fdisk -l doesn't show the devices being detected so I figure I need to configure the SATA controller some how.

Any pointers on where to start are much appreciated. Thanks :)

Josh.

---

