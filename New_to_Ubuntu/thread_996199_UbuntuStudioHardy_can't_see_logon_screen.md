---
title: "UbuntuStudio/Hardy can't see logon screen"
date: 2008-11-28
forum: New to Ubuntu
---

### Post by NotoriousMOK on 2008-11-28
I have a working copy of Intrepid (NOT Studio) on this machine, and just added another partition and installed UbuntuStudio/Hardy (for RT kernel support, not present in Intrepid).  When I installed intrepid, I had to deal with correcting the screen resolution from jumbo 800x600, but this time around, I can't even see the logon screen -- it just flickers/flashes a pattern and a couple of characters.  I AM able to ctrl-alt-f1 to a command prompt.

On the working copy, I have used 800x600, 640x480, and 1280x800(preferred) all at 60hz successfully.

I have tried "sudo dpkg-reconfigure -phigh xserver-xorg" with no success, as well as manually entering the above resolutions into xorg.conf but still no luck.

Also, a check of installed intel drivers from synaptic (on the working copy) shows the following three are installed, but I'm not sure which are actually being used;
xserver-xorg-video-intel
xserver-xorg-video-i810
xserver-xorg-video-i740


 FYI- This is a Sony Vaio laptop VGN-NS135E with Intel video on the system board.

The xorg.conf files seem quite a bit different between 8.10 and 8.04, so I have not yet tried just copying the 8.10 version to the 8.04 install, would this be a safe choice?

I'm confident that once I get a GUI at ANY resolution, I can meddle about and get it fine tuned from there, but I'm stuck at the prompt for the time being --  thanks in advance for any help you can offer!



The xorg.conf from my working 8.10 is as follows; (less default comments)
```

Section "Device"
    Identifier    "Configured Video Device"
    Option        "UseFBDev"        "true"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

```

The xorg.conf from my broken 8.04 is as follows; (less default comments)
```

Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc104"
    Option        "XkbLayout"    "us"
EndSection

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
EndSection

Section "InputDevice"
    Identifier    "Synaptics Touchpad"
    Driver        "synaptics"
    Option        "SendCoreEvents"    "true"
    Option        "Device"        "/dev/psaux"
    Option        "Protocol"        "auto-dev"
    Option        "HorizEdgeScroll"    "0"
EndSection

Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
    Screen        "Default Screen"
    InputDevice    "Synaptics Touchpad"
EndSection

```Output from 'sudo lshw -C display'
```

  *-display:0 UNCLAIMED   
       description: VGA compatible controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm bus_master cap_list
       configuration: latency=0
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0

```

---

### Post by NotoriousMOK on 2008-11-29
> **NotoriousMOK said:**
> 
The xorg.conf files seem quite a bit different between 8.10 and 8.04, so I have not yet tried just copying the 8.10 version to the 8.04 install, would this be a safe choice?


tried this, still no joy -- thanks for any help!

---

### Post by NotoriousMOK on 2008-12-01
bump?

---

### Post by jenkinbr on 2008-12-01
I do remember having a similar problem in hardy running ubuntu where I could only see something like only 1/4 of the login screen.  Mine didn't flicker theough.

I never did solve the problem (or even tried solving it - I just let it go and typed my username/password in anyways (even though I could not see it.)

---

### Post by NotoriousMOK on 2008-12-01
I appreciate your input, jenkinbr.  I have tried as you posted, and I hear all the right sounds that indicate that I've logged in, but display is still jacked once I'm in, so I can't read anything.

Thanks!

---

### Post by markbuntu on 2008-12-01
Did you install with the ubuntustudio dvd or did you install ubuntu and then get the studio metapackages?

A lot of people have problems with that dvd.

---

### Post by NotoriousMOK on 2008-12-01
> **markbuntu said:**
> Did you install with the ubuntustudio dvd or did you install ubuntu and then get the studio metapackages?

A lot of people have problems with that dvd.

Actually, I initially installed UStudio from the DVD, but then read of the DVD woes you mentioned.  I have since done a clean install using the straight ubuntu (actually, the alternate) CD (non-studio), but the same problem remains.

I've been diddling with a variety of xorg tweaks, but no joy so far -- thanks for any advice you can offer!

---

### Post by burnetbj on 2008-12-01
I know you posted you had tried to first command in this next post but please read through all of as this fixed my graphical errors 

Sounds very simular

Hope this helps

[http://ubuntuforums.org/showthread.php?t=685113](http://ubuntuforums.org/showthread.php?t=685113)

---

### Post by NotoriousMOK on 2008-12-02
Thanks burnetbj, i just went through it again just to be sure, but still no luck -- will keep trying -- thanks for the attempt all the same!

---

### Post by NotoriousMOK on 2008-12-02
here is the latest Xorg.0.log -- i see a number of WW warnings, but I'm not so familiar with what all this jazz means -- any ideas?? thanks!

```

This is a pre-release version of the X server from The X.Org Foundation.
It is not supported in any way.
Bugs may be filed in the bugzilla at http://bugs.freedesktop.org/.
Select the "xorg" product for bugs you find in this release.
Before reporting bugs in pre-release versions please check the
latest version in the X.Org Foundation git repository.
See http://wiki.x.org/wiki/GitPage for git access instructions.

X.Org X Server 1.4.0.90
Release Date: 5 September 2007
X Protocol Version 11, Revision 0
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9.2)
Current Operating System: Linux ust804 2.6.24-19-generic #1 SMP Wed Aug 20 22:56:21 UTC 2008 i686
Build Date: 13 June 2008  01:08:21AM
 
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Dec  2 18:58:40 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
(**) |-->Input Device "Synaptics Touchpad"
(==) Automatically adding devices
(==) Automatically enabling devices
(==) No FontPath specified.  Using compiled-in default.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
    Entry deleted from font path.
(==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(==) |-->Input Device "Configured Mouse"
(==) |-->Input Device "Generic Keyboard"
(==) The core pointer device wasn't specified explicitly in the layout.
    Using the first core pointer device.
(==) The core keyboard device wasn't specified explicitly in the layout.
    Using the first keyboard device.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81dc500
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.3
    X.Org Video Driver: 2.0
    X.Org XInput driver : 2.0
    X.Org Server Extension : 0.3
    X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
    compiled for 1.4.0.90, module version = 1.0.0
    ABI class: X.Org Video Driver, version 2.0
(--) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,2a40 card 104d,9045 rev 07 class 06,00,00 hdr 00
(II) PCI: 00:02:0: chip 8086,2a42 card 104d,9045 rev 07 class 03,00,00 hdr 80
(II) PCI: 00:02:1: chip 8086,2a43 card 104d,9045 rev 07 class 03,80,00 hdr 80
(II) PCI: 00:1a:0: chip 8086,2937 card 104d,9045 rev 03 class 0c,03,00 hdr 80
(II) PCI: 00:1a:1: chip 8086,2938 card 104d,9045 rev 03 class 0c,03,00 hdr 00
(II) PCI: 00:1a:2: chip 8086,2939 card 104d,9045 rev 03 class 0c,03,00 hdr 00
(II) PCI: 00:1a:7: chip 8086,293c card 104d,9045 rev 03 class 0c,03,20 hdr 00
(II) PCI: 00:1b:0: chip 8086,293e card 104d,9045 rev 03 class 04,03,00 hdr 00
(II) PCI: 00:1c:0: chip 8086,2940 card 0000,0000 rev 03 class 06,04,00 hdr 81
(II) PCI: 00:1c:1: chip 8086,2942 card 0000,0000 rev 03 class 06,04,00 hdr 81
(II) PCI: 00:1c:2: chip 8086,2944 card 0000,0000 rev 03 class 06,04,00 hdr 81
(II) PCI: 00:1d:0: chip 8086,2934 card 104d,9045 rev 03 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,2935 card 104d,9045 rev 03 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,2936 card 104d,9045 rev 03 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,293a card 104d,9045 rev 03 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,2448 card 0000,0000 rev 93 class 06,04,01 hdr 01
(II) PCI: 00:1f:0: chip 8086,2919 card 104d,9045 rev 03 class 06,01,00 hdr 80
(II) PCI: 00:1f:2: chip 8086,2929 card 104d,9045 rev 03 class 01,06,01 hdr 00
(II) PCI: 00:1f:3: chip 8086,2930 card 104d,9045 rev 03 class 0c,05,00 hdr 00
(II) PCI: 01:00:0: chip 11ab,4363 card 104d,9045 rev 13 class 02,00,00 hdr 00
(II) PCI: 04:00:0: chip 168c,002a card 105b,e007 rev 01 class 02,80,00 hdr 00
(II) PCI: 05:03:0: chip 1180,0832 card 104d,9045 rev 05 class 0c,00,10 hdr 80
(II) PCI: 05:03:1: chip 1180,0822 card 104d,9045 rev 22 class 08,05,00 hdr 80
(II) PCI: 05:03:2: chip 1180,0592 card 104d,9045 rev 12 class 08,80,00 hdr 80
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,5), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
    [0] -1    0    0x00000000 - 0x0000ffff (0x10000) IX[b]
(II) Bus 0 non-prefetchable memory range:
    [0] -1    0    0x00000000 - 0xffffffff (0x0) MX[b]
(II) Bus 0 prefetchable memory range:
    [0] -1    0    0x00000000 - 0xffffffff (0x0) MX[b]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:28:0), (0,1,1), BCTRL: 0x0000 (VGA_EN is cleared)
(II) Bus 1 I/O range:
    [0] -1    0    0x0000d000 - 0x0000dfff (0x1000) IX[b]
(II) Bus 1 non-prefetchable memory range:
    [0] -1    0    0xd2d00000 - 0xd40fffff (0x1400000) MX[b]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:28:1), (0,2,3), BCTRL: 0x0000 (VGA_EN is cleared)
(II) Bus 2 I/O range:
    [0] -1    0    0x0000c000 - 0x0000cfff (0x1000) IX[b]
(II) Bus 2 non-prefetchable memory range:
    [0] -1    0    0xd1900000 - 0xd2cfffff (0x1400000) MX[b]
(II) PCI-to-PCI bridge:
(II) Bus 4: bridge is at (0:28:2), (0,4,4), BCTRL: 0x0000 (VGA_EN is cleared)
(II) Bus 4 I/O range:
    [0] -1    0    0x0000b000 - 0x0000bfff (0x1000) IX[b]
(II) Bus 4 non-prefetchable memory range:
    [0] -1    0    0xd0500000 - 0xd18fffff (0x1400000) MX[b]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 5: bridge is at (0:30:0), (0,5,5), BCTRL: 0x0000 (VGA_EN is cleared)
(II) Bus 5 non-prefetchable memory range:
    [0] -1    0    0xd4100000 - 0xd41fffff (0x100000) MX[b]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(0:2:0) Intel Corporation Mobile Integrated Graphics Controller rev 7, Mem @ 0xd0000000/22, 0xc0000000/28, I/O @ 0xe140/3
(--) PCI: (0:2:1) Intel Corporation Mobile Integrated Graphics Controller rev 7, Mem @ 0xd0400000/20
(II) Addressable bus resource ranges are
    [0] -1    0    0x00000000 - 0xffffffff (0x0) MX[b]
    [1] -1    0    0x00000000 - 0x0000ffff (0x10000) IX[b]
(II) OS-reported resource ranges:
    [0] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[b]E(B)
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [5] -1    0    0x00000000 - 0x000000ff (0x100) IX[b]
(II) Active PCI resource ranges:
    [0] -1    0    0xd4100800 - 0xd41008ff (0x100) MX[b]
    [1] -1    0    0xd4100900 - 0xd41009ff (0x100) MX[b]
    [2] -1    0    0xd4100000 - 0xd41007ff (0x800) MX[b]
    [3] -1    0    0xd0500000 - 0xd050ffff (0x10000) MX[b]
    [4] -1    0    0xd2d20000 - 0xd2d23fff (0x4000) MX[b]
    [5] -1    0    0xd4204000 - 0xd42047ff (0x800) MX[b]
    [6] -1    0    0xd4204800 - 0xd4204bff (0x400) MX[b]
    [7] -1    0    0xd4200000 - 0xd4203fff (0x4000) MX[b]
    [8] -1    0    0xd4204c00 - 0xd4204fff (0x400) MX[b]
    [9] -1    0    0xd0400000 - 0xd04fffff (0x100000) MX[b](B)
    [10] -1    0    0xc0000000 - 0xcfffffff (0x10000000) MX[b](B)
    [11] -1    0    0xd0000000 - 0xd03fffff (0x400000) MX[b](B)
    [12] -1    0    0x0000d000 - 0x0000d0ff (0x100) IX[b]
    [13] -1    0    0x0000e000 - 0x0000e01f (0x20) IX[b]
    [14] -1    0    0x0000e020 - 0x0000e03f (0x20) IX[b]
    [15] -1    0    0x0000e100 - 0x0000e103 (0x4) IX[b]
    [16] -1    0    0x0000e110 - 0x0000e117 (0x8) IX[b]
    [17] -1    0    0x0000e120 - 0x0000e123 (0x4) IX[b]
    [18] -1    0    0x0000e130 - 0x0000e137 (0x8) IX[b]
    [19] -1    0    0x0000e040 - 0x0000e05f (0x20) IX[b]
    [20] -1    0    0x0000e060 - 0x0000e07f (0x20) IX[b]
    [21] -1    0    0x0000e080 - 0x0000e09f (0x20) IX[b]
    [22] -1    0    0x0000e0a0 - 0x0000e0bf (0x20) IX[b]
    [23] -1    0    0x0000e0c0 - 0x0000e0df (0x20) IX[b]
    [24] -1    0    0x0000e0e0 - 0x0000e0ff (0x20) IX[b]
    [25] -1    0    0x0000e140 - 0x0000e147 (0x8) IX[b](B)
(II) Inactive PCI resource ranges:
    [0] -1    0    0xd4205000 - 0xd42050ff (0x100) MX[b]
(II) Active PCI resource ranges after removing overlaps:
    [0] -1    0    0xd4100800 - 0xd41008ff (0x100) MX[b]
    [1] -1    0    0xd4100900 - 0xd41009ff (0x100) MX[b]
    [2] -1    0    0xd4100000 - 0xd41007ff (0x800) MX[b]
    [3] -1    0    0xd0500000 - 0xd050ffff (0x10000) MX[b]
    [4] -1    0    0xd2d20000 - 0xd2d23fff (0x4000) MX[b]
    [5] -1    0    0xd4204000 - 0xd42047ff (0x800) MX[b]
    [6] -1    0    0xd4204800 - 0xd4204bff (0x400) MX[b]
    [7] -1    0    0xd4200000 - 0xd4203fff (0x4000) MX[b]
    [8] -1    0    0xd4204c00 - 0xd4204fff (0x400) MX[b]
    [9] -1    0    0xd0400000 - 0xd04fffff (0x100000) MX[b](B)
    [10] -1    0    0xc0000000 - 0xcfffffff (0x10000000) MX[b](B)
    [11] -1    0    0xd0000000 - 0xd03fffff (0x400000) MX[b](B)
    [12] -1    0    0x0000d000 - 0x0000d0ff (0x100) IX[b]
    [13] -1    0    0x0000e000 - 0x0000e01f (0x20) IX[b]
    [14] -1    0    0x0000e020 - 0x0000e03f (0x20) IX[b]
    [15] -1    0    0x0000e100 - 0x0000e103 (0x4) IX[b]
    [16] -1    0    0x0000e110 - 0x0000e117 (0x8) IX[b]
    [17] -1    0    0x0000e120 - 0x0000e123 (0x4) IX[b]
    [18] -1    0    0x0000e130 - 0x0000e137 (0x8) IX[b]
    [19] -1    0    0x0000e040 - 0x0000e05f (0x20) IX[b]
    [20] -1    0    0x0000e060 - 0x0000e07f (0x20) IX[b]
    [21] -1    0    0x0000e080 - 0x0000e09f (0x20) IX[b]
    [22] -1    0    0x0000e0a0 - 0x0000e0bf (0x20) IX[b]
    [23] -1    0    0x0000e0c0 - 0x0000e0df (0x20) IX[b]
    [24] -1    0    0x0000e0e0 - 0x0000e0ff (0x20) IX[b]
    [25] -1    0    0x0000e140 - 0x0000e147 (0x8) IX[b](B)
(II) Inactive PCI resource ranges after removing overlaps:
    [0] -1    0    0xd4205000 - 0xd42050ff (0x100) MX[b]
(II) OS-reported resource ranges after removing overlaps with PCI:
    [0] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[b]E(B)
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [5] -1    0    0x00000000 - 0x000000ff (0x100) IX[b]
(II) All system resource ranges:
    [0] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[b]E(B)
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0xd4100800 - 0xd41008ff (0x100) MX[b]
    [5] -1    0    0xd4100900 - 0xd41009ff (0x100) MX[b]
    [6] -1    0    0xd4100000 - 0xd41007ff (0x800) MX[b]
    [7] -1    0    0xd0500000 - 0xd050ffff (0x10000) MX[b]
    [8] -1    0    0xd2d20000 - 0xd2d23fff (0x4000) MX[b]
    [9] -1    0    0xd4204000 - 0xd42047ff (0x800) MX[b]
    [10] -1    0    0xd4204800 - 0xd4204bff (0x400) MX[b]
    [11] -1    0    0xd4200000 - 0xd4203fff (0x4000) MX[b]
    [12] -1    0    0xd4204c00 - 0xd4204fff (0x400) MX[b]
    [13] -1    0    0xd0400000 - 0xd04fffff (0x100000) MX[b](B)
    [14] -1    0    0xc0000000 - 0xcfffffff (0x10000000) MX[b](B)
    [15] -1    0    0xd0000000 - 0xd03fffff (0x400000) MX[b](B)
    [16] -1    0    0xd4205000 - 0xd42050ff (0x100) MX[b]
    [17] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [18] -1    0    0x00000000 - 0x000000ff (0x100) IX[b]
    [19] -1    0    0x0000d000 - 0x0000d0ff (0x100) IX[b]
    [20] -1    0    0x0000e000 - 0x0000e01f (0x20) IX[b]
    [21] -1    0    0x0000e020 - 0x0000e03f (0x20) IX[b]
    [22] -1    0    0x0000e100 - 0x0000e103 (0x4) IX[b]
    [23] -1    0    0x0000e110 - 0x0000e117 (0x8) IX[b]
    [24] -1    0    0x0000e120 - 0x0000e123 (0x4) IX[b]
    [25] -1    0    0x0000e130 - 0x0000e137 (0x8) IX[b]
    [26] -1    0    0x0000e040 - 0x0000e05f (0x20) IX[b]
    [27] -1    0    0x0000e060 - 0x0000e07f (0x20) IX[b]
    [28] -1    0    0x0000e080 - 0x0000e09f (0x20) IX[b]
    [29] -1    0    0x0000e0a0 - 0x0000e0bf (0x20) IX[b]
    [30] -1    0    0x0000e0c0 - 0x0000e0df (0x20) IX[b]
    [31] -1    0    0x0000e0e0 - 0x0000e0ff (0x20) IX[b]
    [32] -1    0    0x0000e140 - 0x0000e147 (0x8) IX[b](B)
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
    compiled for 1.4.0.90, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 0.3
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
    compiled for 1.4.0.90, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
    compiled for 1.4.0.90, module version = 1.0.0
    ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
    compiled for 1.4.0.90, module version = 2.1.0
    Module class: X.Org Font Renderer
    ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 1.4.0.90, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 1.4.0.90, module version = 1.0.0
    ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) Matched intel from file name intel.ids in autoconfig
(==) Matched intel for the autoconfigured driver
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "intel"
(II) Loading /usr/lib/xorg/modules/drivers//intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
    compiled for 1.4.0.90, module version = 2.2.1
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 2.0
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
    compiled for 4.3.99.902, module version = 1.0.0
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 2.0
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
    compiled for 1.4.0, module version = 1.2.3
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 2.0
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
    compiled for 1.4.0, module version = 1.2.2
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 2.0
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
    i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
    E7221 (i915), 915GM, 945G, 945GM, 945GME, 965G, G35, 965Q, 946GZ,
    965GM, 965GME/GLE, G33, Q35, Q33, Intel Integrated Graphics Device
(II) Primary Device is: PCI 00:02:0
(--) Assigning device section with no busID to primary device
(WW) intel: No matching Device section for instance (BusID PCI:0:2:1) found
(--) Chipset Intel Integrated Graphics Device found
(II) resource ranges after xf86ClaimFixedResources() call:
    [0] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[b]E(B)
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0xd4100800 - 0xd41008ff (0x100) MX[b]
    [5] -1    0    0xd4100900 - 0xd41009ff (0x100) MX[b]
    [6] -1    0    0xd4100000 - 0xd41007ff (0x800) MX[b]
    [7] -1    0    0xd0500000 - 0xd050ffff (0x10000) MX[b]
    [8] -1    0    0xd2d20000 - 0xd2d23fff (0x4000) MX[b]
    [9] -1    0    0xd4204000 - 0xd42047ff (0x800) MX[b]
    [10] -1    0    0xd4204800 - 0xd4204bff (0x400) MX[b]
    [11] -1    0    0xd4200000 - 0xd4203fff (0x4000) MX[b]
    [12] -1    0    0xd4204c00 - 0xd4204fff (0x400) MX[b]
    [13] -1    0    0xd0400000 - 0xd04fffff (0x100000) MX[b](B)
    [14] -1    0    0xc0000000 - 0xcfffffff (0x10000000) MX[b](B)
    [15] -1    0    0xd0000000 - 0xd03fffff (0x400000) MX[b](B)
    [16] -1    0    0xd4205000 - 0xd42050ff (0x100) MX[b]
    [17] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [18] -1    0    0x00000000 - 0x000000ff (0x100) IX[b]
    [19] -1    0    0x0000d000 - 0x0000d0ff (0x100) IX[b]
    [20] -1    0    0x0000e000 - 0x0000e01f (0x20) IX[b]
    [21] -1    0    0x0000e020 - 0x0000e03f (0x20) IX[b]
    [22] -1    0    0x0000e100 - 0x0000e103 (0x4) IX[b]
    [23] -1    0    0x0000e110 - 0x0000e117 (0x8) IX[b]
    [24] -1    0    0x0000e120 - 0x0000e123 (0x4) IX[b]
    [25] -1    0    0x0000e130 - 0x0000e137 (0x8) IX[b]
    [26] -1    0    0x0000e040 - 0x0000e05f (0x20) IX[b]
    [27] -1    0    0x0000e060 - 0x0000e07f (0x20) IX[b]
    [28] -1    0    0x0000e080 - 0x0000e09f (0x20) IX[b]
    [29] -1    0    0x0000e0a0 - 0x0000e0bf (0x20) IX[b]
    [30] -1    0    0x0000e0c0 - 0x0000e0df (0x20) IX[b]
    [31] -1    0    0x0000e0e0 - 0x0000e0ff (0x20) IX[b]
    [32] -1    0    0x0000e140 - 0x0000e147 (0x8) IX[b](B)
(II) resource ranges after probing:
    [0] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[b]E(B)
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0xd4100800 - 0xd41008ff (0x100) MX[b]
    [5] -1    0    0xd4100900 - 0xd41009ff (0x100) MX[b]
    [6] -1    0    0xd4100000 - 0xd41007ff (0x800) MX[b]
    [7] -1    0    0xd0500000 - 0xd050ffff (0x10000) MX[b]
    [8] -1    0    0xd2d20000 - 0xd2d23fff (0x4000) MX[b]
    [9] -1    0    0xd4204000 - 0xd42047ff (0x800) MX[b]
    [10] -1    0    0xd4204800 - 0xd4204bff (0x400) MX[b]
    [11] -1    0    0xd4200000 - 0xd4203fff (0x4000) MX[b]
    [12] -1    0    0xd4204c00 - 0xd4204fff (0x400) MX[b]
    [13] -1    0    0xd0400000 - 0xd04fffff (0x100000) MX[b](B)
    [14] -1    0    0xc0000000 - 0xcfffffff (0x10000000) MX[b](B)
    [15] -1    0    0xd0000000 - 0xd03fffff (0x400000) MX[b](B)
    [16] -1    0    0xd4205000 - 0xd42050ff (0x100) MX[b]
    [17] 0    0    0x000a0000 - 0x000affff (0x10000) MS[b]
    [18] 0    0    0x000b0000 - 0x000b7fff (0x8000) MS[b]
    [19] 0    0    0x000b8000 - 0x000bffff (0x8000) MS[b]
    [20] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [21] -1    0    0x00000000 - 0x000000ff (0x100) IX[b]
    [22] -1    0    0x0000d000 - 0x0000d0ff (0x100) IX[b]
    [23] -1    0    0x0000e000 - 0x0000e01f (0x20) IX[b]
    [24] -1    0    0x0000e020 - 0x0000e03f (0x20) IX[b]
    [25] -1    0    0x0000e100 - 0x0000e103 (0x4) IX[b]
    [26] -1    0    0x0000e110 - 0x0000e117 (0x8) IX[b]
    [27] -1    0    0x0000e120 - 0x0000e123 (0x4) IX[b]
    [28] -1    0    0x0000e130 - 0x0000e137 (0x8) IX[b]
    [29] -1    0    0x0000e040 - 0x0000e05f (0x20) IX[b]
    [30] -1    0    0x0000e060 - 0x0000e07f (0x20) IX[b]
    [31] -1    0    0x0000e080 - 0x0000e09f (0x20) IX[b]
    [32] -1    0    0x0000e0a0 - 0x0000e0bf (0x20) IX[b]
    [33] -1    0    0x0000e0c0 - 0x0000e0df (0x20) IX[b]
    [34] -1    0    0x0000e0e0 - 0x0000e0ff (0x20) IX[b]
    [35] -1    0    0x0000e140 - 0x0000e147 (0x8) IX[b](B)
    [36] 0    0    0x000003b0 - 0x000003bb (0xc) IS[b]
    [37] 0    0    0x000003c0 - 0x000003df (0x20) IS[b]
(II) Setting vga for screen 0.
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
    compiled for 1.4.0.90, module version = 1.0.0
    ABI class: X.Org Video Driver, version 2.0
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
    compiled for 1.4.0.90, module version = 1.1.0
    ABI class: X.Org Video Driver, version 2.0
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
    compiled for 1.4.0.90, module version = 0.1.0
    ABI class: X.Org Video Driver, version 2.0
(II) intel(0): Creating default Display subsection in Screen section
    "Default Screen" for depth/fbbpp 24/32
(==) intel(0): Depth 24, (==) framebuffer bpp 32
(==) intel(0): RGB weight 888
(==) intel(0): Default visual is TrueColor
(II) intel(0): Integrated Graphics Chipset: Intel(R) Intel Integrated Graphics Device
(--) intel(0): Chipset: "Intel Integrated Graphics Device"
(--) intel(0): Linear framebuffer at 0xC0000000
(--) intel(0): IO registers at addr 0xD0000000
(II) intel(0): 2 display pipes available.
(==) intel(0): Using EXA for acceleration
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module "ddc" already built-in
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"(II) Module "i2c" already built-in
(II) intel(0): Output VGA using monitor section Configured Monitor
(II) intel(0): I2C bus "CRTDDC_A" initialized.
(II) intel(0): Output LVDS has no monitor section
(II) intel(0): I2C bus "LVDSDDC_C" initialized.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" removed.
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) intel(0): initializing int10
(WW) intel(0): Bad V_BIOS checksum
(II) intel(0): Primary V_BIOS segment is: 0xc000
(II) intel(0): VESA BIOS detected
(II) intel(0): VESA VBE Version 3.0
(II) intel(0): VESA VBE Total Mem: 131008 kB
(II) intel(0): VESA VBE OEM: Intel(r)Cantiga Graphics Chip Accelerated VGA BIOS
(II) intel(0): VESA VBE OEM Software Rev: 1.0
(II) intel(0): VESA VBE OEM Vendor: Intel Corporation
(II) intel(0): VESA VBE OEM Product: Intel(r)Cantiga Graphics Controller
(II) intel(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) intel(0): found backlight control method /sys/class/backlight/acpi_video0
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOB" initialized.
(II) intel(0): I2C device "SDVOCTRL_E for SDVOB:SDVO Controller B" registered at address 0x70.
(II) intel(0): No SDVO device found on SDVOB
(II) intel(0): I2C device "SDVOCTRL_E for SDVOB:SDVO Controller B" removed.
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOB" removed.
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOC" initialized.
(II) intel(0): I2C device "SDVOCTRL_E for SDVOC:SDVO Controller C" registered at address 0x72.
(II) intel(0): No SDVO device found on SDVOC
(II) intel(0): I2C device "SDVOCTRL_E for SDVOC:SDVO Controller C" removed.
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOC" removed.
(II) intel(0): Output TV has no monitor section
(II) intel(0): I2C device "LVDSDDC_C:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" removed.
(II) intel(0): Output VGA disconnected
(II) intel(0): Output LVDS connected
(II) intel(0): Output TV disconnected
(II) intel(0): Output LVDS using initial mode 1280x800
(II) intel(0): Monitoring connected displays enabled
(II) intel(0): detected 512 kB GTT.
(II) intel(0): detected 130556 kB stolen memory.
(==) intel(0): video overlay key set to 0x101fe
(==) intel(0): Will not try to enable page flipping
(==) intel(0): Triple buffering disabled
(==) intel(0): Using gamma correction (1.0, 1.0, 1.0)
(==) intel(0): DPI set to (96, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.4.0.90, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "exa"
(II) LoadModule: "exa"
(II) Loading /usr/lib/xorg/modules//libexa.so
(II) Module exa: vendor="X.Org Foundation"
    compiled for 1.4.0.90, module version = 2.2.0
    ABI class: X.Org Video Driver, version 2.0
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module "ramdac" already built-in
(II) intel(0): Comparing regs from server start up to After PreInit
(WW) intel(0): Register 0x61200 (PP_STATUS) changed from 0xc0000008 to 0xd000000a
(WW) intel(0): PP_STATUS before: on, ready, sequencing idle
(WW) intel(0): PP_STATUS after: on, ready, sequencing on
(WW) intel(0): Register 0x321b (FBC_FENCE_OFF) changed from 0xa003d600 to 0xaf03a200
(==) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
    [0] 0    0    0xc0000000 - 0xcfffffff (0x10000000) MS[b]
    [1] 0    0    0xd0000000 - 0xd03fffff (0x400000) MS[b]
    [2] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[b]E(B)
    [3] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [4] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [5] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [6] -1    0    0xd4100800 - 0xd41008ff (0x100) MX[b]
    [7] -1    0    0xd4100900 - 0xd41009ff (0x100) MX[b]
    [8] -1    0    0xd4100000 - 0xd41007ff (0x800) MX[b]
    [9] -1    0    0xd0500000 - 0xd050ffff (0x10000) MX[b]
    [10] -1    0    0xd2d20000 - 0xd2d23fff (0x4000) MX[b]
    [11] -1    0    0xd4204000 - 0xd42047ff (0x800) MX[b]
    [12] -1    0    0xd4204800 - 0xd4204bff (0x400) MX[b]
    [13] -1    0    0xd4200000 - 0xd4203fff (0x4000) MX[b]
    [14] -1    0    0xd4204c00 - 0xd4204fff (0x400) MX[b]
    [15] -1    0    0xd0400000 - 0xd04fffff (0x100000) MX[b](B)
    [16] -1    0    0xc0000000 - 0xcfffffff (0x10000000) MX[b](B)
    [17] -1    0    0xd0000000 - 0xd03fffff (0x400000) MX[b](B)
    [18] -1    0    0xd4205000 - 0xd42050ff (0x100) MX[b]
    [19] 0    0    0x000a0000 - 0x000affff (0x10000) MS[b](OprD)
    [20] 0    0    0x000b0000 - 0x000b7fff (0x8000) MS[b](OprD)
    [21] 0    0    0x000b8000 - 0x000bffff (0x8000) MS[b](OprD)
    [22] 0    0    0x0000e140 - 0x0000e147 (0x8) IS[b]
    [23] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [24] -1    0    0x00000000 - 0x000000ff (0x100) IX[b]
    [25] -1    0    0x0000d000 - 0x0000d0ff (0x100) IX[b]
    [26] -1    0    0x0000e000 - 0x0000e01f (0x20) IX[b]
    [27] -1    0    0x0000e020 - 0x0000e03f (0x20) IX[b]
    [28] -1    0    0x0000e100 - 0x0000e103 (0x4) IX[b]
    [29] -1    0    0x0000e110 - 0x0000e117 (0x8) IX[b]
    [30] -1    0    0x0000e120 - 0x0000e123 (0x4) IX[b]
    [31] -1    0    0x0000e130 - 0x0000e137 (0x8) IX[b]
    [32] -1    0    0x0000e040 - 0x0000e05f (0x20) IX[b]
    [33] -1    0    0x0000e060 - 0x0000e07f (0x20) IX[b]
    [34] -1    0    0x0000e080 - 0x0000e09f (0x20) IX[b]
    [35] -1    0    0x0000e0a0 - 0x0000e0bf (0x20) IX[b]
    [36] -1    0    0x0000e0c0 - 0x0000e0df (0x20) IX[b]
    [37] -1    0    0x0000e0e0 - 0x0000e0ff (0x20) IX[b]
    [38] -1    0    0x0000e140 - 0x0000e147 (0x8) IX[b](B)
    [39] 0    0    0x000003b0 - 0x000003bb (0xc) IS[b](OprU)
    [40] 0    0    0x000003c0 - 0x000003df (0x20) IS[b](OprU)
(II) intel(0): Kernel reported 715776 total, 1 used
(II) intel(0): I830CheckAvailableMemory: 2863100 kB available
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(II) [drm] DRM interface version 1.3
(II) [drm] DRM open master succeeded.
(II) intel(0): [drm] Using the DRM lock SAREA also for drawables.
(II) intel(0): [drm] framebuffer mapped by ddx driver
(II) intel(0): [drm] added 1 reserved context for kernel
(II) intel(0): X context handle = 0x1
(II) intel(0): [drm] installed DRM signal handler
(==) intel(0): VideoRam: 262144 KB
(**) intel(0): Framebuffer compression disabled
(**) intel(0): Tiling enabled
(II) intel(0): Attempting memory allocation with tiled buffers.
(II) intel(0): Success.
(II) intel(0): [drm] Registers = 0xd0000000
(II) intel(0): [drm] ring buffer = 0xc0000000
(II) intel(0): [drm] mapped front buffer at 0xc0100000, handle = 0xc0100000
(II) intel(0): [drm] mapped back buffer at 0xc1a00000, handle = 0xc1a00000
(II) intel(0): [drm] mapped depth buffer at 0xc2040000, handle = 0xc2040000
(II) intel(0): [drm] mapped classic textures at 0xc2680000, handle = 0xc2680000
(II) intel(0): [drm] Initialized kernel agp heap manager, 33554432
(II) intel(0): [dri] visual configs initialized
(II) intel(0): Page Flipping disabled
(==) intel(0): Write-combining range (0xc0000000,0x10000000)
(II) intel(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(WW) intel(0): EXA greedy migration mode enabled.
(II) EXA(0): Forcing greedy migration option
(II) EXA(0): Offscreen pixmap area of 19660800 bytes
(II) EXA(0): Driver registered support for the following operations:
(II)         Solid
(II)         Copy
(II)         Composite (RENDER acceleration)
(==) intel(0): Backing store disabled
(==) intel(0): Silken mouse enabled
(II) intel(0): Initializing HW Cursor
(II) intel(0): [DRI] installation complete
(II) intel(0): xf86BindGARTMemory: bind key 0 at 0x07f7f000 (pgoffset 32639)
(II) intel(0): Fixed memory allocation layout:
(II) intel(0): 0x00000000-0x0001ffff: ring buffer (128 kB)
(II) intel(0): 0x00020000-0x00029fff: HW cursors (40 kB)
(II) intel(0): 0x0002a000-0x00031fff: logical 3D context (32 kB)
(II) intel(0): 0x00032000-0x00041fff: exa G965 state buffer (64 kB)
(II) intel(0): 0x00042000-0x00042fff: overlay registers (4 kB)
(II) intel(0): 0x00100000-0x0073ffff: front buffer (6400 kB) X tiled
(II) intel(0): 0x00740000-0x019fffff: exa offscreen (19200 kB)
(II) intel(0): 0x01a00000-0x0203ffff: back buffer (6400 kB) X tiled
(II) intel(0): 0x02040000-0x0267ffff: depth buffer (6400 kB) Y tiled
(II) intel(0): 0x02680000-0x0467ffff: classic textures (32768 kB)
(II) intel(0): 0x07f7f000:            end of stolen memory
(II) intel(0): 0x07f7f000-0x07f7ffff: HW status (4 kB)
(II) intel(0): 0x10000000:            end of aperture
(WW) intel(0): ESR is 0x00000010, page table error
(WW) intel(0): PGTBL_ER is 0x00100000, CS instruction GTT PTE
(WW) intel(0): Existing errors found in hardware state.
(II) intel(0): Output configuration:
(II) intel(0):   Pipe A is off
(II) intel(0):   Display plane A is now disabled and connected to pipe A.
(II) intel(0):   Pipe B is on
(II) intel(0):   Display plane B is now enabled and connected to pipe B.
(II) intel(0):   Output VGA is connected to pipe none
(II) intel(0):   Output LVDS is connected to pipe B
(II) intel(0):   Output TV is connected to pipe none
(II) intel(0): [drm] dma control initialized, using IRQ 17
(II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(II) intel(0): DPMS enabled
(II) intel(0): Set up overlay video
(II) intel(0): direct rendering: Enabled
(--) RandR disabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: drmOpenMinor returns 9
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(WW) AIGLX: 3D driver claims to not support visual 0x23
(WW) AIGLX: 3D driver claims to not support visual 0x24
(WW) AIGLX: 3D driver claims to not support visual 0x25
(WW) AIGLX: 3D driver claims to not support visual 0x26
(WW) AIGLX: 3D driver claims to not support visual 0x27
(WW) AIGLX: 3D driver claims to not support visual 0x28
(WW) AIGLX: 3D driver claims to not support visual 0x29
(WW) AIGLX: 3D driver claims to not support visual 0x2a
(WW) AIGLX: 3D driver claims to not support visual 0x2b
(WW) AIGLX: 3D driver claims to not support visual 0x2c
(WW) AIGLX: 3D driver claims to not support visual 0x2d
(WW) AIGLX: 3D driver claims to not support visual 0x2e
(WW) AIGLX: 3D driver claims to not support visual 0x2f
(WW) AIGLX: 3D driver claims to not support visual 0x30
(WW) AIGLX: 3D driver claims to not support visual 0x31
(WW) AIGLX: 3D driver claims to not support visual 0x32
(II) AIGLX: Loaded and initialized /usr/lib/dri/i965_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
(II) intel(0): Setting screen physical size to 338 x 211
Atom 4, CARD32 4, unsigned long 4
(II) Synaptics touchpad driver version 0.14.6 (1406)
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event7
(**) Option "Device" "/dev/input/event7"
(**) Option "HorizEdgeScroll" "0"
(--) Synaptics Touchpad touchpad found
(**) Option "SendCoreEvents" "true"
(**) Synaptics Touchpad: always reports core events
(WW) Configured Mouse: No Device specified, looking for one...
(II) Configured Mouse: Setting Device option to "/dev/input/mice"
(--) Configured Mouse: Device: "/dev/input/mice"
(==) Configured Mouse: Protocol: "Auto"
(**) Option "CorePointer"
(**) Configured Mouse: always reports core events
(**) Option "Device" "/dev/input/mice"
(==) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Configured Mouse: Sensitivity: 1
(**) Option "CoreKeyboard"
(**) Generic Keyboard: always reports core events
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(II) evaluating device (Generic Keyboard)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) evaluating device (Configured Mouse)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) evaluating device (Synaptics Touchpad)
(II) XINPUT: Adding extended input device "Synaptics Touchpad" (type: MOUSE)
(--) Configured Mouse: PnP-detected protocol: "ExplorerPS/2"
(II) Configured Mouse: ps2EnableDataReporting: succeeded
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event7
(**) Option "Device" "/dev/input/event7"
(--) Synaptics Touchpad touchpad found
(II) AIGLX: Suspending AIGLX clients for VT switch
(II) intel(0): xf86UnbindGARTMemory: unbind key 0
(II) intel(0): [drm] removed 1 reserved context for kernel
(II) intel(0): [drm] unmapping 8192 bytes of SAREA 0xf8d65000 at 0xb7eda000
(II) intel(0): [drm] Closed DRM master.
FreeFontPath: FPE "/usr/share/fonts/X11/misc" refcount is 2, should be 1; fixing.
```

---

### Post by NotoriousMOK on 2008-12-10
bump?

---

### Post by markbuntu on 2008-12-10
It seems that there is a problem with the driver recognizing some parts of the hardware. This is most likely due to some tweaks from the OEM but it really is trying to work. You should file a bug report at Launchpad or try to find a similar one to confirm the bug.

Meanwhile, you can try booting up in safe mode and changing to the VESA driver. That should work no matter what. Once you do that, you can boot into gnome safe mode and at least have a gui so you can look in the logs a little easier.

---

### Post by NotoriousMOK on 2008-12-10
> **markbuntu said:**
> It seems that there is a problem with the driver recognizing some parts of the hardware. This is most likely due to some tweaks from the OEM but it really is trying to work. You should file a bug report at Launchpad or try to find a similar one to confirm the bug.

Meanwhile, you can try booting up in safe mode and changing to the VESA driver. That should work no matter what. Once you do that, you can boot into gnome safe mode and at least have a gui so you can look in the logs a little easier.

the vesa driver still does not give me a display I can use -- is there another way I can direct to gnome safe mode?

thank you!

---

### Post by markbuntu on 2008-12-11
If you boot into recovery mode, you can change the screen resolution in the same place youset up the vesa driver.

---

