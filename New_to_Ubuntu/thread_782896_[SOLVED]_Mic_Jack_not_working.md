---
title: "[SOLVED] Mic Jack not working?"
date: 2008-05-05
forum: New to Ubuntu
---

### Post by Promaster91 on 2008-05-05
Hi. I have been using Ubuntu for about six months now and I just realized that my mic jack is not working. Here is the output of lspci.
```

stefan@stefan-laptop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:05.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1)
00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2)
00:07.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 3)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]
0e:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
14:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
1a:04.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
1a:04.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
1a:04.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
1a:04.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller

```

Is there any drivers I need to install? I will keep searching the forums but so far I have come up empty handed. Can anybody help me? Thanks in advance.:)

---

### Post by HotShotDJ on 2008-05-05
> **Promaster91 said:**
> Hi. I have been using Ubuntu for about six months now and I just realized that my mic jack is not working.Firstly, make sure that the microphone is not muted.  That was my problem when my microphone wasn't working.

Open the speaker icon from your panel (left click --> Open Volume Control) -- if its not there, add it by left clicking on the panel --> Add to Panel --> Volume Control.

See if you can find a microphone option under the recording tab.  It might not be there.  If not, you'll need to add it.  While still in the Volume Control dialog, click Edit --> Preferences.  Check off everything. Now, you should find your microphone.  Unmute it and set the volume.  Adjust as desired.

If this doesn't help, then I'm not sure what could be causing your issue.

---

### Post by Promaster91 on 2008-05-05
Hey! It works. Thanks. I had it set to "mic" but after playing around with it ... my input is name "capture". Thanks for the help!

---

