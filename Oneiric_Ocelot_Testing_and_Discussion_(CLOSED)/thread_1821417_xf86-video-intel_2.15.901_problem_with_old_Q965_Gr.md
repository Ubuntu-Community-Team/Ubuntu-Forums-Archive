---
title: "xf86-video-intel 2.15.901 problem with old Q965 Graphics"
date: 2011-08-09
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by redkiwi on 2011-08-09
With the new **xserver-xorg-video-intel** (2:2.15.901-1ubuntu1) package, X-Server will not start anymore.
The system freezes when starting X-Server. The previous version worked perfectly.


New Package:
```
$ apt-cache policy xserver-xorg-video-intel
xserver-xorg-video-intel:
  Installiert: 2:2.15.901-1ubuntu1
  Kandidat:    2:2.15.901-1ubuntu1
  Versionstabelle:
 *** 2:2.15.901-1ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ oneiric/main amd64 Packages
        100 /var/lib/dpkg/status

```ASUS P5B-VM DO Mainboard with Intel Corporation 82Q963/Q965 Integrated Graphics Controller:
```
00:02.0 VGA compatible controller: Intel Corporation 82Q963/Q965 Integrated Graphics Controller (rev 02) (prog-if 00 [VGA controller])
    Subsystem: ASUSTeK Computer Inc. Device 81e9
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin A routed to IRQ 42
    Region 0: Memory at fea00000 (32-bit, non-prefetchable) [size=1M]
    Region 2: Memory at e0000000 (64-bit, prefetchable) [size=256M]
    Region 4: I/O ports at ec00 [size=8]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
        Address: fee0300c  Data: 4179
    Capabilities: [d0] Power Management version 2
        Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
        Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
    Kernel modules: i915

```

---

### Post by x-shaney-x on 2011-08-09
Same problem here with Intel HD graphics on both ubuntu and kubuntu

Had to reinstall the older version to get a graphical desktop.

---

### Post by redkiwi on 2011-08-09
As a workaround, I'm running nomodeset and waiting for a package update...

```
$ xrandr 
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 640 x 480, current 1280 x 1024, maximum 1280 x 1024
default connected 1280x1024+0+0 0mm x 0mm
   1280x1024       0.0* 
   1024x768        0.0  
   800x600         0.0  
   640x480         0.0  

```only 1280x1024 and no video acceleration hurts, but better then nothing :biggrin:

---

### Post by hloeung on 2011-08-09
I had the same problem and only just upgraded to 2.15.901-1ubuntu2 which seems to have fixed it for me.

---

### Post by redkiwi on 2011-08-09
> **hloeung said:**
> I had the same problem and only just upgraded to 2.15.901-1ubuntu2 which seems to have fixed it for me.The latest version on archive.ubuntu.com is **2.15.901-1ubuntu1** .
What is your Mirror-Server?


:edit
I can confirm 2.15.901-1ubuntu2 fixes the problem.

```
xserver-xorg-video-intel (2:2.15.901-1ubuntu2) oneiric; **urgency=low**

  * 101_copy-fb.patch: intel_batch_submit_internal is no longer added by
    this patch.  Don't reference it.  Fixes Xserver failing to start
    with symbol error.

```[B]urgency=low :lolflag:


[/B] :edit2
wow, compiz runs noticeable faster with the new **2.15.901-1ubuntu2** driver. great work :D


:edit3
NEWS: [xf86-video-intel]("http://cgit.freedesktop.org/xorg/driver/xf86-video-intel/") 2.16.0 release
[http://cgit.freedesktop.org/xorg/driver/xf86-video-intel/commit/?id=3a81bb6bafdbd37802dab96b8f05173ec6701d7f](http://cgit.freedesktop.org/xorg/driver/xf86-video-intel/commit/?id=3a81bb6bafdbd37802dab96b8f05173ec6701d7f)

---

