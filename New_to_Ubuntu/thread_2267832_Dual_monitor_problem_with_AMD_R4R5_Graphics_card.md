---
title: "Dual monitor problem with AMD R4/R5 Graphics card"
date: 2015-03-04
forum: New to Ubuntu
---

### Post by Anh_Tran on 2015-03-04
Hello all,

I have a problem with my HDMI cable when using dual monitor. HDMI to DVI-D cable works fine; I understand a direct cable from HDMI to VGA wouldn't work so I bought the adapter as well. The problem is that while the dual screen is detected in Settings > Display, it remains black and tells me no signal is received. So far I've tried *fglrx, fglrx-updates* and *X* but none of them are capable of displaying the second screen. If anyone has some experience encounter this, please let me know how to solve. 

```
fglrxinfo
```
> OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: AMD Radeon(TM) R5E Graphics
OpenGL version string: 4.4.12968 Compatibility Profile Context 14.201.1006.1002


```
lspci -vvnn | grep VGA
```
> Control: I/O- Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
00:01.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Mullins [Radeon R4/R5 Graphics] [1002:9851] (prog-if 00 [VGA controller])
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O+ Mem+ BusMaster+ SpecCycle+ MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-

xorg.conf:
> Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Module"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    BusID       "PCI:0:1:0"
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[0]-0"
    Device     "aticonfig-Device[0]-0"
    Monitor    "aticonfig-Monitor[0]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

I've also tried direct .deb package from AMD/ATI website.

Thanks! :p

---

### Post by dino99 on 2015-03-04
xorg only knows about 1 monitor; you need to run catalyst to set the 2 monitors first

---

### Post by Anh_Tran on 2015-03-04
could you please show me how to install AMD Catalyst? I went on here

[http://support.amd.com/en-us/download/desktop?os=Ubuntu+x86+64](http://support.amd.com/en-us/download/desktop?os=Ubuntu+x86+64)

and download .deb packages instead. They only open the Software Center and ask me if I want to install the packages or not. Did I miss something? Thanks

---

### Post by dino99 on 2015-03-04
> **Anh_Tran said:**
> could you please show me how to install AMD Catalyst? I went on here

[http://support.amd.com/en-us/download/desktop?os=Ubuntu+x86+64](http://support.amd.com/en-us/download/desktop?os=Ubuntu+x86+64)

and download .deb packages instead. They only open the Software Center and ask me if I want to install the packages or not. Did I miss something? Thanks

Sorry but i'm not an amd user, so can't share my experience with it  ;)
Follow this howto: [https://help.ubuntu.com/community/BinaryDriverHowto/AMD](https://help.ubuntu.com/community/BinaryDriverHowto/AMD)

---

### Post by Mark Phelps on 2015-03-04
Might help if you told us HOW your monitors are connected -- what kind of plugs and what kinds of adapters.

---

### Post by Anh_Tran on 2015-03-06
^
^
thanks for the How-to, that was neat.

> **Mark Phelps said:**
> Might help if you told us HOW your monitors are connected -- what kind of plugs and what kinds of adapters.

So somehow I come across the topic that HDMI can't be directly go with VGA, so I need an adapter. So I went on eBay and got it

[http://www.ebay.com/itm/NEW-HDMI-Male-to-VGA-Female-Video-Cable-Cord-Converter-Adapter-1080P-for-PC-/181604241555?pt=LH_DefaultDomain_0&hash=item2a4874d093](http://www.ebay.com/itm/NEW-HDMI-Male-to-VGA-Female-Video-Cable-Cord-Converter-Adapter-1080P-for-PC-/181604241555?pt=LH_DefaultDomain_0&hash=item2a4874d093)

I use VGA-VGA cable with this HDMI-VGA adapter to connect HDMI (computer) - VGA (monitor). My computer detects signal from the monitor by showing me there are 2 displays in Settings > Display, but the monitor remains black. I tried to go through different input modes but no luck. For the same monitor, I was able to connect HDMI (computer) - DVI-D (monitor). I haven't tried the Catalyst yet, please let me know if you have seen something like this before. Thanks!

---

### Post by Mark Phelps on 2015-03-06
Sorry, haven't tried this kind of adapter.  In have two monitors, one HDMI, the other VGA, but my video card also has a VGA connector -- so I don't need the adapter.

---

### Post by gordintoronto on 2015-03-07
What OS are you using?

In many cases, Software Center is the default program for installing a deb. However, I prefer to get drivers from "additional drivers" rather than a vendor site.

---

### Post by Anh_Tran on 2015-03-16
So I went to the AMD Catalyst Center; it seems to detect the second monitor. I took a screenshot, the second desktop background was captured!! but on the monitor it was totally black. I haven't seen anything this weird. Please let me know if you have a solution. Muchas Gracias! 
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=260654&d=1426510018[/IMG]

---

