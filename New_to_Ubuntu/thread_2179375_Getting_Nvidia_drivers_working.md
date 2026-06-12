---
title: "Getting Nvidia drivers working"
date: 2013-10-08
forum: New to Ubuntu
---

### Post by xBf3KyL on 2013-10-08
Ubuntu 12.04

Intel i7 3770k
Asus Sabertooth Z77
Nvidia GTX 690
Mushkin SSD 240GB
16GB RAM

I can't get my graphics card working. When I use Additional Drivers to try to install Nvidia drivers, after rebooting, before the login screen the monitor turns off. To fix it I have to uninstall all Nvidia drivers and it reverts to the Nouveau driver. I've tried nomodeset, xforcevesa, I've tried blacklisting the Nouveau driver. I'm really out of my element here, what do I need to do to get my graphics card working?

I already spent forever just trying to get Ubuntu to install, turns out there's an issue with my motherboard, I had to add a line (libata.atapi_passthru16=0) to the boot options. 

I apologize if I come off a bit hostile, I'm just frustrated. Any help would be greatly appreciated. Thank you!

---

### Post by DuckHook on 2013-10-08
You have a bleeding-edge card that 12.04 in particular is unlikely to support. You will likely need the latest Linux driver from nVidia's site, that is, if there even is such a driver. They may not have released anything for Linux yet, in which case, you are stuck with Nouveau till they do.

---

### Post by Donut50 on 2013-10-08
have you already tried install the properiarity drivers off the nvidia site?

---

### Post by xBf3KyL on 2013-10-08
@DuckHook: I hope that's not the case.

@Donut50: Yes, results were the same. After rebooting the monitor shuts off right before login. Then I have to hit ctrl+alt+f1, uninstall the nvidia drivers and unblacklist the nouveau driver. :(

At least the Nouveau driver allows me to have my native 2560x1440 resolution, but no advanced 3d, even 1080p video sometimes stutters. I want to be done with Windows, but atm I have to keep it for playing games.

---

### Post by DuckHook on 2013-10-08
After doing further research it appears that your instincts are correct and mine were dead wrong. In future, I shall be more careful just popping off the first answer that comes into my head. In fact, my suggestion to install nVidia drivers directly from their site may gum up your works even further.

According to [this]("http://askubuntu.com/questions/248630/boots-into-console-instead-of-gui-gui-wanted-instead") thread, the 304 driver should support your card without problems. This driver is available in the 12.04 repo and is the standard proprietary driver choice (this means: *don't* use "experimental"). However, it s/b installed on a "clean" system that hasn't had its xorg.conf changed. You may wish to follow the steps contained in the linked thread.

Upon re-reading your post more carefully (should have done so from the first), I notice you say:> ...before the login screen the monitor turns off.But in a later posting, you say that you can <Ctrl>+<Alt>+<F1> to switch to a bash session, so it doesn't actually turn off? Did it actually physically turn off or just go black screen (i.e. no video input)?. This is important.

Also important: How many drivers did you try, which were they and how did you install them? How did you *un*install them? Did you use *purge* or just *remove* with apt-get? Please be precise and as detailed as possible. Were they all from the 12.04 repositories? 

A last area of concern was all of the wrestling you did to get Ubuntu to work on your mobo. Actually, two concerns. You may have inadvertently borked something in your efforts to make it work, and the fact that your mobo has already proven itself to be unusual could imply that the problem springs from your graphics card/mobo combination. I offer it only as a possibility. But before jumping to yet another conclusion that may be unwarranted, let's try doing what the linked thread suggests. Please post results of:```
dkms status
```

---

### Post by xBf3KyL on 2013-10-08
For drivers from Nvidia's website I use nvidia-uninstall to remove them, then remove the blacklisting file from modprobe.d. For drivers from Additional Drivers, I use sudo apt-get purge nvidia*. dkms status returns nothing.

Upon boot the monitor physically turns off, hitting ctrl+alt+f1 to switch to a bash session turns the monitor back on.

I figured it best to start fresh, I just reinstalled Ubuntu 12.04, this  time booting the CD via UEFI. This appears to have resolved my  motherboard issue, I wasn't required to add that line mentioned in my  first post to grub.

I decided to try 304.88 from Additional Drivers (I previously used 319.32). This time upon boot a dialog popped up saying "Low Graphics Mode - Your screen, graphics card, and input device setting could not be detected correctly. You need to configure it yourself." I then returned to bash, and purged the nvidia driver. Then I went to  Nvidia to get the latest beta driver, I installed 331.13. Again this Low  Graphics Mode dialog presented itself upon boot.

My previous installation I was using GDM, rather than LightDM, so that may be the difference between the monitor turning off verse receiving the low graphics dialog.

I don't know but maybe the information from lspci -v can help:
```
00:00.0 Host bridge: Intel Corporation Ivy Bridge DRAM Controller (rev 09)
    Subsystem: ASUSTeK Computer Inc. Device 84ca
    Flags: bus master, fast devsel, latency 0
    Capabilities: [e0] Vendor Specific Information: Len=0c <?>

00:01.0 PCI bridge: Intel Corporation Ivy Bridge PCI Express Root Port (rev 09) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=04, sec-latency=0
    I/O behind bridge: 0000b000-0000cfff
    Memory behind bridge: f4000000-f71fffff
    Prefetchable memory behind bridge: 00000000d8000000-00000000f1ffffff
    Capabilities: [88] Subsystem: ASUSTeK Computer Inc. Device 84ca
    Capabilities: [80] Power Management version 3
    Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [a0] Express Root Port (Slot+), MSI 00
    Capabilities: [100] Virtual Channel
    Capabilities: [140] Root Complex Link
    Capabilities: [d94] #19
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:14.0 USB controller: Intel Corporation Panther Point USB xHCI Host Controller (rev 04) (prog-if 30 [XHCI])
    Subsystem: ASUSTeK Computer Inc. Device 84ca
    Flags: bus master, medium devsel, latency 0, IRQ 47
    Memory at f7520000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: [70] Power Management version 2
    Capabilities: [80] MSI: Enable+ Count=1/8 Maskable- 64bit+
    Kernel driver in use: xhci_hcd

00:16.0 Communication controller: Intel Corporation Panther Point MEI Controller #1 (rev 04)
    Subsystem: ASUSTeK Computer Inc. Device 84ca
    Flags: bus master, fast devsel, latency 0, IRQ 57
    Memory at f753b000 (64-bit, non-prefetchable) [size=16]
    Capabilities: [50] Power Management version 3
    Capabilities: [8c] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Kernel driver in use: mei
    Kernel modules: mei

00:19.0 Ethernet controller: Intel Corporation 82579V Gigabit Network Connection (rev 04)
    Subsystem: ASUSTeK Computer Inc. P8P67 Deluxe Motherboard
    Flags: bus master, fast devsel, latency 0, IRQ 56
    Memory at f7500000 (32-bit, non-prefetchable) [size=128K]
    Memory at f7539000 (32-bit, non-prefetchable) [size=4K]
    I/O ports at f040 [size=32]
    Capabilities: [c8] Power Management version 2
    Capabilities: [d0] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [e0] PCI Advanced Features
    Kernel driver in use: e1000e
    Kernel modules: e1000e

00:1a.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #2 (rev 04) (prog-if 20 [EHCI])
    Subsystem: ASUSTeK Computer Inc. Device 84ca
    Flags: bus master, medium devsel, latency 0, IRQ 16
    Memory at f7538000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [50] Power Management version 2
    Capabilities: [58] Debug port: BAR=1 offset=00a0
    Capabilities: [98] PCI Advanced Features
    Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation Panther Point High Definition Audio Controller (rev 04)
    Subsystem: ASUSTeK Computer Inc. Device 8436
    Flags: bus master, fast devsel, latency 0, IRQ 58
    Memory at f7530000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
    Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [100] Virtual Channel
    Capabilities: [130] Root Complex Link
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 1 (rev c4) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: d0100000-d02fffff
    Prefetchable memory behind bridge: 00000000d0300000-00000000d04fffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable- Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: ASUSTeK Computer Inc. Device 84ca
    Capabilities: [a0] Power Management version 2
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.4 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 5 (rev c4) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
    Memory behind bridge: f7400000-f74fffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable- Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: ASUSTeK Computer Inc. Device 84ca
    Capabilities: [a0] Power Management version 2
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.6 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 7 (rev c4) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=07, subordinate=07, sec-latency=0
    I/O behind bridge: 0000e000-0000efff
    Memory behind bridge: f7300000-f73fffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable- Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: ASUSTeK Computer Inc. Device 84ca
    Capabilities: [a0] Power Management version 2
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.7 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 8 (rev c4) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=08, subordinate=08, sec-latency=0
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: f7200000-f72fffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable- Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: ASUSTeK Computer Inc. Device 84ca
    Capabilities: [a0] Power Management version 2
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #1 (rev 04) (prog-if 20 [EHCI])
    Subsystem: ASUSTeK Computer Inc. Device 84ca
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at f7537000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [50] Power Management version 2
    Capabilities: [58] Debug port: BAR=1 offset=00a0
    Capabilities: [98] PCI Advanced Features
    Kernel driver in use: ehci_hcd

00:1f.0 ISA bridge: Intel Corporation Panther Point LPC Controller (rev 04)
    Subsystem: ASUSTeK Computer Inc. Device 84ca
    Flags: bus master, medium devsel, latency 0
    Capabilities: [e0] Vendor Specific Information: Len=0c <?>
    Kernel modules: lpc_ich

00:1f.2 SATA controller: Intel Corporation Panther Point 6 port SATA Controller [AHCI mode] (rev 04) (prog-if 01 [AHCI 1.0])
    Subsystem: ASUSTeK Computer Inc. Device 84ca
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 44
    I/O ports at f090 [size=8]
    I/O ports at f080 [size=4]
    I/O ports at f070 [size=8]
    I/O ports at f060 [size=4]
    I/O ports at f020 [size=32]
    Memory at f7536000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [70] Power Management version 3
    Capabilities: [a8] SATA HBA v1.0
    Capabilities: [b0] PCI Advanced Features
    Kernel driver in use: ahci

00:1f.3 SMBus: Intel Corporation Panther Point SMBus Controller (rev 04)
    Subsystem: ASUSTeK Computer Inc. Device 84ca
    Flags: medium devsel, IRQ 11
    Memory at f7535000 (64-bit, non-prefetchable) [size=256]
    I/O ports at f000 [size=32]
    Kernel modules: i2c-i801

01:00.0 PCI bridge: PLX Technology, Inc. Device 8747 (rev ba) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Memory at f7100000 (32-bit, non-prefetchable) [size=256K]
    Bus: primary=01, secondary=02, subordinate=04, sec-latency=0
    I/O behind bridge: 0000b000-0000cfff
    Memory behind bridge: f4000000-f70fffff
    Prefetchable memory behind bridge: 00000000d8000000-00000000f1ffffff
    Capabilities: [40] Power Management version 3
    Capabilities: [48] MSI: Enable+ Count=1/8 Maskable+ 64bit+
    Capabilities: [68] Express Upstream Port, MSI 00
    Capabilities: [a4] Subsystem: PLX Technology, Inc. Device 8747
    Capabilities: [100] Device Serial Number ba-87-00-10-b5-df-0e-00
    Capabilities: [fb4] Advanced Error Reporting
    Capabilities: [138] Power Budgeting <?>
    Capabilities: [10c] #19
    Capabilities: [148] Virtual Channel
    Capabilities: [e00] #12
    Capabilities: [b00] Latency Tolerance Reporting
    Capabilities: [b70] Vendor Specific Information: ID=0001 Rev=0 Len=010 <?>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

02:08.0 PCI bridge: PLX Technology, Inc. Device 8747 (rev ba) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=02, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 0000c000-0000cfff
    Memory behind bridge: f6000000-f70fffff
    Prefetchable memory behind bridge: 00000000e8000000-00000000f1ffffff
    Capabilities: [40] Power Management version 3
    Capabilities: [48] MSI: Enable+ Count=1/8 Maskable+ 64bit+
    Capabilities: [68] Express Downstream Port (Slot+), MSI 00
    Capabilities: [a4] Subsystem: PLX Technology, Inc. Device 8747
    Capabilities: [100] Device Serial Number ba-87-00-10-b5-df-0e-00
    Capabilities: [fb4] Advanced Error Reporting
    Capabilities: [138] Power Budgeting <?>
    Capabilities: [10c] #19
    Capabilities: [148] Virtual Channel
    Capabilities: [e00] #12
    Capabilities: [f24] Access Control Services
    Capabilities: [b70] Vendor Specific Information: ID=0001 Rev=0 Len=010 <?>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

02:10.0 PCI bridge: PLX Technology, Inc. Device 8747 (rev ba) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=02, secondary=04, subordinate=04, sec-latency=0
    I/O behind bridge: 0000b000-0000bfff
    Memory behind bridge: f4000000-f50fffff
    Prefetchable memory behind bridge: 00000000d8000000-00000000e1ffffff
    Capabilities: [40] Power Management version 3
    Capabilities: [48] MSI: Enable+ Count=1/8 Maskable+ 64bit+
    Capabilities: [68] Express Downstream Port (Slot+), MSI 00
    Capabilities: [a4] Subsystem: PLX Technology, Inc. Device 8747
    Capabilities: [100] Device Serial Number ba-87-00-10-b5-df-0e-00
    Capabilities: [fb4] Advanced Error Reporting
    Capabilities: [138] Power Budgeting <?>
    Capabilities: [10c] #19
    Capabilities: [148] Virtual Channel
    Capabilities: [e00] #12
    Capabilities: [f24] Access Control Services
    Capabilities: [b70] Vendor Specific Information: ID=0001 Rev=0 Len=010 <?>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

03:00.0 3D controller: NVIDIA Corporation Device 1188 (rev a1)
    Subsystem: eVga.com. Corp. Device 2690
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at f6000000 (32-bit, non-prefetchable) [size=16M]
    Memory at e8000000 (64-bit, prefetchable) [size=128M]
    Memory at f0000000 (64-bit, prefetchable) [size=32M]
    I/O ports at c000 [size=128]
    Capabilities: [60] Power Management version 3
    Capabilities: [68] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [78] Express Endpoint, MSI 00
    Capabilities: [b4] Vendor Specific Information: Len=14 <?>
    Capabilities: [100] Virtual Channel
    Capabilities: [128] Power Budgeting <?>
    Capabilities: [600] Vendor Specific Information: ID=0001 Rev=1 Len=024 <?>
    Capabilities: [900] #19
    Kernel driver in use: nouveau
    Kernel modules: nouveau, nvidiafb

03:00.1 Audio device: NVIDIA Corporation Device 0e0a (rev a1)
    Subsystem: eVga.com. Corp. Device 2690
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at f7000000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: [60] Power Management version 3
    Capabilities: [68] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [78] Express Endpoint, MSI 00
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel

04:00.0 VGA compatible controller: NVIDIA Corporation Device 1188 (rev a1) (prog-if 00 [VGA controller])
    Subsystem: eVga.com. Corp. Device 2690
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at f4000000 (32-bit, non-prefetchable) [size=16M]
    Memory at d8000000 (64-bit, prefetchable) [size=128M]
    Memory at e0000000 (64-bit, prefetchable) [size=32M]
    I/O ports at b000 [size=128]
    Expansion ROM at f5000000 [disabled] [size=512K]
    Capabilities: [60] Power Management version 3
    Capabilities: [68] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [78] Express Endpoint, MSI 00
    Capabilities: [b4] Vendor Specific Information: Len=14 <?>
    Capabilities: [100] Virtual Channel
    Capabilities: [128] Power Budgeting <?>
    Capabilities: [600] Vendor Specific Information: ID=0001 Rev=1 Len=024 <?>
    Capabilities: [900] #19
    Kernel driver in use: nouveau
    Kernel modules: nouveau, nvidiafb

04:00.1 Audio device: NVIDIA Corporation Device 0e0a (rev a1)
    Subsystem: eVga.com. Corp. Device 2690
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at f5080000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: [60] Power Management version 3
    Capabilities: [68] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [78] Express Endpoint, MSI 00
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel

06:00.0 USB controller: ASMedia Technology Inc. ASM1042 SuperSpeed USB Host Controller (prog-if 30 [XHCI])
    Subsystem: ASUSTeK Computer Inc. Device 8488
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at f7400000 (64-bit, non-prefetchable) [size=32K]
    Capabilities: [50] MSI: Enable- Count=1/8 Maskable- 64bit+
    Capabilities: [68] MSI-X: Enable+ Count=8 Masked-
    Capabilities: [78] Power Management version 3
    Capabilities: [80] Express Legacy Endpoint, MSI 00
    Capabilities: [100] Virtual Channel
    Kernel driver in use: xhci_hcd

07:00.0 SATA controller: ASMedia Technology Inc. ASM1062 Serial ATA Controller (rev 01) (prog-if 01 [AHCI 1.0])
    Subsystem: ASUSTeK Computer Inc. Device 84b7
    Flags: bus master, fast devsel, latency 0, IRQ 45
    I/O ports at e050 [size=8]
    I/O ports at e040 [size=4]
    I/O ports at e030 [size=8]
    I/O ports at e020 [size=4]
    I/O ports at e000 [size=32]
    Memory at f7300000 (32-bit, non-prefetchable) [size=512]
    Capabilities: [50] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [78] Power Management version 3
    Capabilities: [80] Express Legacy Endpoint, MSI 00
    Capabilities: [100] Virtual Channel
    Kernel driver in use: ahci

08:00.0 SATA controller: ASMedia Technology Inc. ASM1062 Serial ATA Controller (rev 01) (prog-if 01 [AHCI 1.0])
    Subsystem: ASUSTeK Computer Inc. Device 84b7
    Flags: bus master, fast devsel, latency 0, IRQ 46
    I/O ports at d050 [size=8]
    I/O ports at d040 [size=4]
    I/O ports at d030 [size=8]
    I/O ports at d020 [size=4]
    I/O ports at d000 [size=32]
    Memory at f7200000 (32-bit, non-prefetchable) [size=512]
    Capabilities: [50] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [78] Power Management version 3
    Capabilities: [80] Express Legacy Endpoint, MSI 00
    Capabilities: [100] Virtual Channel
    Kernel driver in use: ahci
```

Thank you for following up btw, I appreciate it.


edit: So I just tried installing the latest stable build (319.60) from nvidia. Upon boot the monitor shut off. So my previous thoughts are wrong, the resulting low graphics mode or monitor turning off has no relation to lightdm or gdm.

---

### Post by xBf3KyL on 2013-10-08
Alright I may have made some progress. I turned on my sound after installing an nvidia driver and noticed after booting, when the screen turns off, I hear the login prompt startup sound.

My monitor uses a dual dvi port. It's logical when the monitor turns off that there was no error, the driver is working, however it is not sending the graphics signal to the right port.

I tried editing /etc/X11/xorg.conf and adding the following option to the Screen section:
```
Option "UseDisplayDevice" "DFP"
```

Unfortunately that didn't fix it. I'm going to do some more experimenting.

edit: No solution yet, here is the contents of my xorg.conf:
```
Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "UseDisplayDevice" "DFP"
    SubSection     "Display"
        Depth       24
        Modes      "2560x1440"
    EndSubSection
EndSection
```

Any ideas?

---

### Post by xBf3KyL on 2013-10-08
Woohoo! Solved!!!

It turns out it was a problem with my monitor not being recognized. I have a Korean monitor (Yamakasi Catleap Q270). I found someone who had the same issue. 

**Solution:** Download bin file and place it in your X11 folder (via: sudo mv nameofbinfile.bin /etc/X11/). In your xorg.conf, under screen, add: Option "CustomEDID" "DFP:/etc/X11/nameofbinfile.bin"

See the write up, and get the bin file from: [http://learnitwithme.com/?p=342](http://learnitwithme.com/?p=342)

Thanks for the replies everyone. I'm so happy! Woohoo, bye bye Windows. :)

---

### Post by DuckHook on 2013-10-08
I stepped out for the afternoon and was unable to get back to this thread until now, only to discover that you had found your own solutions to what are a very complex set of problems.

You are one cussed determined fella with a good nose for problem-solving and you have my frank admiration. If I may be so bold, you would make a great helper on these forums.

Congrats and Happy Ubuntuing!

---

### Post by xBf3KyL on 2013-10-08
Ubuntu (Linux) is definitely different than Windows. But having used  Windows since 3.1, I learned to troubleshoot through trial and error (no  matter how frustrating). Luckily most of the time someone else had the same problem, it's just a matter of narrowing down your issue so you can search properly.

Finally I'm able to watch more than one HD stream at a time: [http://s23.postimg.org/q6jgugpy3/Screenshot_from_2013_10_08_19_32_31.png](http://s23.postimg.org/q6jgugpy3/Screenshot_from_2013_10_08_19_32_31.png)

I'm glad I got it working, now to see what games I am able to play. I have high hopes for the future though with the announcement of Steam Machines / SteamOS.

See you around the forum. :)

---

