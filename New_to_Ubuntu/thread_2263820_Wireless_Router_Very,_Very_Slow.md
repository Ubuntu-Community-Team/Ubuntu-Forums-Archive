---
title: "Wireless Router Very, Very Slow"
date: 2015-02-03
forum: New to Ubuntu
---

### Post by Saturnino_Zertuche on 2015-02-03
Hey everyone. So I just installed Lubuntu on an old Toshiba satellite laptop rocking a gig of ram. The wireless connection (802.11b/g) to the internet is absurdly slow. Just wondering if there was a work around this or could I just buy on of those USB wireless receivers. Thanks in advance for the help community.

---

### Post by mooreted on 2015-02-03
You may need to install firmware and or drivers for your wireless adapter. Open a terminal and tell us what the output of the following command is:

lspci

---

### Post by Saturnino_Zertuche on 2015-02-05
Here's the info that popped up....

00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD/ATI] RC410 Host Bridge (rev 01)
00:01.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RC4xx/RS4xx PCI Bridge [int gfx]
00:04.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RC4xx/RS4xx PCI Express Port 1
00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 USB Host Controller (rev 80)
00:13.1 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 USB Host Controller (rev 80)
00:13.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 USB2 Host Controller (rev 80)
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 SMBus Controller (rev 81)
00:14.1 IDE interface: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 IDE Controller (rev 80)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 PCI-PCI Bridge (rev 80)
00:14.5 Multimedia audio controller: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB400 AC'97 Audio Controller (rev 80)
00:14.6 Modem: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB400 AC'97 Modem Controller (rev 80)
01:05.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RC410M [Mobility Radeon Xpress 200M]
04:02.0 Ethernet controller: Qualcomm Atheros AR2413/AR2414 Wireless Network Adapter [AR5005G(S) 802.11bg] (rev 01)
04:04.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
04:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

---

### Post by mooreted on 2015-02-05
Ok, you have a:

Qualcomm Atheros AR2413/AR2414 adapter. I'll look around and see if there's a driver for it.

---

### Post by mooreted on 2015-02-05
Weird double post. oops

---

### Post by mooreted on 2015-02-05
Here's something worth looking at:

[http://ubuntuforums.org/showthread.php?t=2239155](http://ubuntuforums.org/showthread.php?t=2239155)

---

