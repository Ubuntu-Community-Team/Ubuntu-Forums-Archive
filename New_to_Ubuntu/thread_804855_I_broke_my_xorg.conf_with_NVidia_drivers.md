---
title: "I broke my xorg.conf with NVidia drivers"
date: 2008-05-23
forum: New to Ubuntu
---

### Post by causticburning on 2008-05-23
My problem is that I can't boot into X without it going into some sort of safe mode vesa 800x600.  So far I've installed the proprietary NVidia drivers from their site as per instructions, destroyed my xorg.conf

<rant> somehow many times, loaded a lot of backups, gotten confused, followed a bunch of guides which broke more things, totally broke x again, trawled google, forums, irc, cried for hours in the foetal position, considered reinstalling windows, forgot that idea, got onto this forum... </rant>

The only reason I wanted the nvidia driver instead of the nv driver is so I can run opengl apps on my video hardware.  Here's all the information that I could get that seemed to be relevant - please help!

```

laren@laren-desktop:~$ glxinfo | grep rendering
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".

laren@laren-desktop:~$ lspci | grep -i nvidia
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600 GT (rev a1)


```

My xorg conf
```

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    RgbPath         "/usr/lib/X11/rgb"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
    Load	   "v4l"
#    Load           "dri"
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
    Identifier     "Benq"
    VendorName     "Generic LCD Display"
    ModelName      "LCD Panel 1680x1050"
    HorizSync       31.5 - 65.5
    VertRefresh     56.0 - 65.0
    Gamma           1
    ModeLine       "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
    ModeLine       "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
    ModeLine       "1280x768@60" 80.1 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
    ModeLine       "1280x720@60" 74.5 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
    ModeLine       "1280x800@60" 83.5 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
    ModeLine       "1440x900@60" 106.5 1440 1520 1672 1904 900 901 904 932 -hsync +vsync
    ModeLine       "1600x1024@60" 136.4 1600 1704 1872 2144 1024 1025 1028 1060 -hsync +vsync
    ModeLine       "1680x1050@60" 147.1 1680 1784 1968 2256 1050 1051 1054 1087 -hsync +vsync
EndSection


Section "Device"
    Identifier     "6600GT"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    Option         "RenderAccel" "true"
    Option         "AllowGLXWithComposite" "true"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "6600GT"
    Monitor        "Benq"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
    Option         "DisableGLXRootClipping" "true"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection


```

My xorg log
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
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9)
Current Operating System: Linux laren-desktop 2.6.24-16-rt #1 SMP PREEMPT RT Thu Apr 10 15:15:40 UTC 2008 i686
Build Date: 15 April 2008  05:26:17PM
 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat May 24 02:27:48 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Layout0"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Benq"
(**) |   |-->Device "6600GT"
(**) |-->Input Device "Keyboard0"
(**) |-->Input Device "Mouse0"
(==) Automatically adding devices
(==) Automatically enabling devices
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
(**) RgbPath set to "/usr/lib/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(**) Extension "Composite" is enabled
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
(II) PCI: 00:00:0: chip 8086,29c0 card 1458,5000 rev 02 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,29c1 card 0000,0000 rev 02 class 06,04,00 hdr 01
(II) PCI: 00:1a:0: chip 8086,2937 card 1458,5004 rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1a:1: chip 8086,2938 card 1458,5004 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1a:2: chip 8086,2939 card 1458,5004 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1a:7: chip 8086,293c card 1458,5006 rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1b:0: chip 8086,293e card 1458,a002 rev 02 class 04,03,00 hdr 00
(II) PCI: 00:1c:0: chip 8086,2940 card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1c:3: chip 8086,2946 card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1c:4: chip 8086,2948 card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1d:0: chip 8086,2934 card 1458,5004 rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,2935 card 1458,5004 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,2936 card 1458,5004 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,293a card 1458,5006 rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev 92 class 06,04,01 hdr 01
(II) PCI: 00:1f:0: chip 8086,2916 card 1458,5001 rev 02 class 06,01,00 hdr 80
(II) PCI: 00:1f:2: chip 8086,2920 card 1458,b002 rev 02 class 01,01,8a hdr 00
(II) PCI: 00:1f:3: chip 8086,2930 card 1458,5001 rev 02 class 0c,05,00 hdr 00
(II) PCI: 00:1f:5: chip 8086,2926 card 1458,b002 rev 02 class 01,01,85 hdr 00
(II) PCI: 01:00:0: chip 10de,0402 card 1458,3447 rev a1 class 03,00,00 hdr 00
(II) PCI: 03:00:0: chip 197b,2363 card 1458,b000 rev 02 class 01,06,01 hdr 80
(II) PCI: 03:00:1: chip 197b,2363 card 1458,b000 rev 02 class 01,01,85 hdr 00
(II) PCI: 04:00:0: chip 10ec,8168 card 1458,e000 rev 01 class 02,00,00 hdr 00
(II) PCI: 05:01:0: chip 11c1,5811 card 1799,0502 rev 61 class 0c,00,10 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,5), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000b000 - 0x0000bfff (0x1000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xf4000000 - 0xf7ffffff (0x4000000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:28:0), (0,2,2), BCTRL: 0x0000 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x0000a000 - 0x0000afff (0x1000) IX[B]
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:28:3), (0,3,3), BCTRL: 0x0000 (VGA_EN is cleared)
(II) Bus 3 I/O range:
	[0] -1	0	0x0000c000 - 0x0000cfff (0x1000) IX[B]
(II) Bus 3 non-prefetchable memory range:
	[0] -1	0	0xfa000000 - 0xfa0fffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 4: bridge is at (0:28:4), (0,4,4), BCTRL: 0x0000 (VGA_EN is cleared)
(II) Bus 4 I/O range:
	[0] -1	0	0x0000d000 - 0x0000dfff (0x1000) IX[B]
(II) Bus 4 non-prefetchable memory range:
	[0] -1	0	0xf8000000 - 0xf9ffffff (0x2000000) MX[B]
(II) Bus 4 prefetchable memory range:
	[0] -1	0	0x80000000 - 0x800fffff (0x100000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 5: bridge is at (0:30:0), (0,5,5), BCTRL: 0x0000 (VGA_EN is cleared)
(II) Bus 5 non-prefetchable memory range:
	[0] -1	0	0xfa100000 - 0xfa1fffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) nVidia Corporation GeForce 8600 GT rev 161, Mem @ 0xf6000000/24, 0xe0000000/28, 0xf4000000/25, I/O @ 0xb000/7
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) Active PCI resource ranges:
	[0] -1	0	0xfa100000 - 0xfa100fff (0x1000) MX[B]
	[1] -1	0	0xf9000000 - 0xf9000fff (0x1000) MX[B]
	[2] -1	0	0xfa000000 - 0xfa001fff (0x2000) MX[B]
	[3] -1	0	0xfa206000 - 0xfa2060ff (0x100) MX[B]
	[4] -1	0	0xfa204000 - 0xfa2043ff (0x400) MX[B]
	[5] -1	0	0xfa200000 - 0xfa203fff (0x4000) MX[B]
	[6] -1	0	0xfa205000 - 0xfa2053ff (0x400) MX[B]
	[7] -1	0	0xf4000000 - 0xf5ffffff (0x2000000) MX[B](B)
	[8] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[9] -1	0	0xf6000000 - 0xf6ffffff (0x1000000) MX[B](B)
	[10] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[11] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[12] -1	0	0x0000c300 - 0x0000c303 (0x4) IX[B]
	[13] -1	0	0x0000c200 - 0x0000c207 (0x8) IX[B]
	[14] -1	0	0x0000c100 - 0x0000c103 (0x4) IX[B]
	[15] -1	0	0x0000c000 - 0x0000c007 (0x8) IX[B]
	[16] -1	0	0x0000ec00 - 0x0000ec0f (0x10) IX[B]
	[17] -1	0	0x0000eb00 - 0x0000eb0f (0x10) IX[B]
	[18] -1	0	0x0000ea00 - 0x0000ea03 (0x4) IX[B]
	[19] -1	0	0x0000e900 - 0x0000e907 (0x8) IX[B]
	[20] -1	0	0x0000e800 - 0x0000e803 (0x4) IX[B]
	[21] -1	0	0x0000e700 - 0x0000e707 (0x8) IX[B]
	[22] -1	0	0x00000500 - 0x0000051f (0x20) IX[B]
	[23] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[24] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[28] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[29] -1	0	0x0000e500 - 0x0000e51f (0x20) IX[B]
	[30] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[31] -1	0	0x0000e300 - 0x0000e31f (0x20) IX[B]
	[32] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[33] -1	0	0x0000e200 - 0x0000e21f (0x20) IX[B]
	[34] -1	0	0x0000e100 - 0x0000e11f (0x20) IX[B]
	[35] -1	0	0x0000b000 - 0x0000b07f (0x80) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xfa100000 - 0xfa100fff (0x1000) MX[B]
	[1] -1	0	0xf9000000 - 0xf9000fff (0x1000) MX[B]
	[2] -1	0	0xfa000000 - 0xfa001fff (0x2000) MX[B]
	[3] -1	0	0xfa206000 - 0xfa2060ff (0x100) MX[B]
	[4] -1	0	0xfa204000 - 0xfa2043ff (0x400) MX[B]
	[5] -1	0	0xfa200000 - 0xfa203fff (0x4000) MX[B]
	[6] -1	0	0xfa205000 - 0xfa2053ff (0x400) MX[B]
	[7] -1	0	0xf4000000 - 0xf5ffffff (0x2000000) MX[B](B)
	[8] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[9] -1	0	0xf6000000 - 0xf6ffffff (0x1000000) MX[B](B)
	[10] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[11] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[12] -1	0	0x0000c300 - 0x0000c303 (0x4) IX[B]
	[13] -1	0	0x0000c200 - 0x0000c207 (0x8) IX[B]
	[14] -1	0	0x0000c100 - 0x0000c103 (0x4) IX[B]
	[15] -1	0	0x0000c000 - 0x0000c007 (0x8) IX[B]
	[16] -1	0	0x0000ec00 - 0x0000ec0f (0x10) IX[B]
	[17] -1	0	0x0000eb00 - 0x0000eb0f (0x10) IX[B]
	[18] -1	0	0x0000ea00 - 0x0000ea03 (0x4) IX[B]
	[19] -1	0	0x0000e900 - 0x0000e907 (0x8) IX[B]
	[20] -1	0	0x0000e800 - 0x0000e803 (0x4) IX[B]
	[21] -1	0	0x0000e700 - 0x0000e707 (0x8) IX[B]
	[22] -1	0	0x00000500 - 0x0000051f (0x20) IX[B]
	[23] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[24] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[28] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[29] -1	0	0x0000e500 - 0x0000e51f (0x20) IX[B]
	[30] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[31] -1	0	0x0000e300 - 0x0000e31f (0x20) IX[B]
	[32] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[33] -1	0	0x0000e200 - 0x0000e21f (0x20) IX[B]
	[34] -1	0	0x0000e100 - 0x0000e11f (0x20) IX[B]
	[35] -1	0	0x0000b000 - 0x0000b07f (0x80) IX[B](B)
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfa100000 - 0xfa100fff (0x1000) MX[B]
	[5] -1	0	0xf9000000 - 0xf9000fff (0x1000) MX[B]
	[6] -1	0	0xfa000000 - 0xfa001fff (0x2000) MX[B]
	[7] -1	0	0xfa206000 - 0xfa2060ff (0x100) MX[B]
	[8] -1	0	0xfa204000 - 0xfa2043ff (0x400) MX[B]
	[9] -1	0	0xfa200000 - 0xfa203fff (0x4000) MX[B]
	[10] -1	0	0xfa205000 - 0xfa2053ff (0x400) MX[B]
	[11] -1	0	0xf4000000 - 0xf5ffffff (0x2000000) MX[B](B)
	[12] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[13] -1	0	0xf6000000 - 0xf6ffffff (0x1000000) MX[B](B)
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[17] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[18] -1	0	0x0000c300 - 0x0000c303 (0x4) IX[B]
	[19] -1	0	0x0000c200 - 0x0000c207 (0x8) IX[B]
	[20] -1	0	0x0000c100 - 0x0000c103 (0x4) IX[B]
	[21] -1	0	0x0000c000 - 0x0000c007 (0x8) IX[B]
	[22] -1	0	0x0000ec00 - 0x0000ec0f (0x10) IX[B]
	[23] -1	0	0x0000eb00 - 0x0000eb0f (0x10) IX[B]
	[24] -1	0	0x0000ea00 - 0x0000ea03 (0x4) IX[B]
	[25] -1	0	0x0000e900 - 0x0000e907 (0x8) IX[B]
	[26] -1	0	0x0000e800 - 0x0000e803 (0x4) IX[B]
	[27] -1	0	0x0000e700 - 0x0000e707 (0x8) IX[B]
	[28] -1	0	0x00000500 - 0x0000051f (0x20) IX[B]
	[29] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[30] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[31] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[32] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[33] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[34] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[35] -1	0	0x0000e500 - 0x0000e51f (0x20) IX[B]
	[36] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[37] -1	0	0x0000e300 - 0x0000e31f (0x20) IX[B]
	[38] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[39] -1	0	0x0000e200 - 0x0000e21f (0x20) IX[B]
	[40] -1	0	0x0000e100 - 0x0000e11f (0x20) IX[B]
	[41] -1	0	0x0000b000 - 0x0000b07f (0x80) IX[B](B)
(II) "extmod" will be loaded. This was enabled by default and also specified in the config file.
(II) "dbe" will be loaded. This was enabled by default and also specified in the config file.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "freetype" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
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
(II) LoadModule: "type1"
(WW) Warning, couldn't open module type1
(II) UnloadModule: "type1"
(EE) Failed to load module "type1" (module does not exist, 0)
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.4.0.90, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) NVIDIA GLX Module  173.08  Wed Apr  2 00:11:16 PST 2008
(II) Loading extension GLX
(II) LoadModule: "v4l"
(II) Loading /usr/lib/xorg/modules/drivers//v4l_drv.so
(II) Module v4l: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 0.1.1
	ABI class: X.Org Video Driver, version 2.0
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
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Video Driver
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) v4l driver for Video4Linux
(II) NVIDIA dlloader X Driver  173.08  Tue Apr  1 23:51:01 PST 2008
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(--) Assigning device section with no busID to primary device
(--) Chipset NVIDIA GPU found
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules//libwfb.so
(II) Module wfb: vendor="NVIDIA Corporation"
	compiled for 7.1.99.2, module version = 1.0.0
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module "ramdac" already built-in
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfa100000 - 0xfa100fff (0x1000) MX[B]
	[5] -1	0	0xf9000000 - 0xf9000fff (0x1000) MX[B]
	[6] -1	0	0xfa000000 - 0xfa001fff (0x2000) MX[B]
	[7] -1	0	0xfa206000 - 0xfa2060ff (0x100) MX[B]
	[8] -1	0	0xfa204000 - 0xfa2043ff (0x400) MX[B]
	[9] -1	0	0xfa200000 - 0xfa203fff (0x4000) MX[B]
	[10] -1	0	0xfa205000 - 0xfa2053ff (0x400) MX[B]
	[11] -1	0	0xf4000000 - 0xf5ffffff (0x2000000) MX[B](B)
	[12] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[13] -1	0	0xf6000000 - 0xf6ffffff (0x1000000) MX[B](B)
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[17] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[18] -1	0	0x0000c300 - 0x0000c303 (0x4) IX[B]
	[19] -1	0	0x0000c200 - 0x0000c207 (0x8) IX[B]
	[20] -1	0	0x0000c100 - 0x0000c103 (0x4) IX[B]
	[21] -1	0	0x0000c000 - 0x0000c007 (0x8) IX[B]
	[22] -1	0	0x0000ec00 - 0x0000ec0f (0x10) IX[B]
	[23] -1	0	0x0000eb00 - 0x0000eb0f (0x10) IX[B]
	[24] -1	0	0x0000ea00 - 0x0000ea03 (0x4) IX[B]
	[25] -1	0	0x0000e900 - 0x0000e907 (0x8) IX[B]
	[26] -1	0	0x0000e800 - 0x0000e803 (0x4) IX[B]
	[27] -1	0	0x0000e700 - 0x0000e707 (0x8) IX[B]
	[28] -1	0	0x00000500 - 0x0000051f (0x20) IX[B]
	[29] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[30] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[31] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[32] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[33] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[34] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[35] -1	0	0x0000e500 - 0x0000e51f (0x20) IX[B]
	[36] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[37] -1	0	0x0000e300 - 0x0000e31f (0x20) IX[B]
	[38] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[39] -1	0	0x0000e200 - 0x0000e21f (0x20) IX[B]
	[40] -1	0	0x0000e100 - 0x0000e11f (0x20) IX[B]
	[41] -1	0	0x0000b000 - 0x0000b07f (0x80) IX[B](B)
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfa100000 - 0xfa100fff (0x1000) MX[B]
	[5] -1	0	0xf9000000 - 0xf9000fff (0x1000) MX[B]
	[6] -1	0	0xfa000000 - 0xfa001fff (0x2000) MX[B]
	[7] -1	0	0xfa206000 - 0xfa2060ff (0x100) MX[B]
	[8] -1	0	0xfa204000 - 0xfa2043ff (0x400) MX[B]
	[9] -1	0	0xfa200000 - 0xfa203fff (0x4000) MX[B]
	[10] -1	0	0xfa205000 - 0xfa2053ff (0x400) MX[B]
	[11] -1	0	0xf4000000 - 0xf5ffffff (0x2000000) MX[B](B)
	[12] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[13] -1	0	0xf6000000 - 0xf6ffffff (0x1000000) MX[B](B)
	[14] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[15] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[16] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[17] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[19] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[20] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[21] -1	0	0x0000c300 - 0x0000c303 (0x4) IX[B]
	[22] -1	0	0x0000c200 - 0x0000c207 (0x8) IX[B]
	[23] -1	0	0x0000c100 - 0x0000c103 (0x4) IX[B]
	[24] -1	0	0x0000c000 - 0x0000c007 (0x8) IX[B]
	[25] -1	0	0x0000ec00 - 0x0000ec0f (0x10) IX[B]
	[26] -1	0	0x0000eb00 - 0x0000eb0f (0x10) IX[B]
	[27] -1	0	0x0000ea00 - 0x0000ea03 (0x4) IX[B]
	[28] -1	0	0x0000e900 - 0x0000e907 (0x8) IX[B]
	[29] -1	0	0x0000e800 - 0x0000e803 (0x4) IX[B]
	[30] -1	0	0x0000e700 - 0x0000e707 (0x8) IX[B]
	[31] -1	0	0x00000500 - 0x0000051f (0x20) IX[B]
	[32] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[33] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[34] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[35] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[36] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[37] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[38] -1	0	0x0000e500 - 0x0000e51f (0x20) IX[B]
	[39] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[40] -1	0	0x0000e300 - 0x0000e31f (0x20) IX[B]
	[41] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[42] -1	0	0x0000e200 - 0x0000e21f (0x20) IX[B]
	[43] -1	0	0x0000e100 - 0x0000e11f (0x20) IX[B]
	[44] -1	0	0x0000b000 - 0x0000b07f (0x80) IX[B](B)
	[45] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[46] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(**) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "RenderAccel" "true"
(**) NVIDIA(0): Option "AllowGLXWithComposite" "true"
(**) NVIDIA(0): Option "AddARGBGLXVisuals" "True"
(**) NVIDIA(0): Option "DisableGLXRootClipping" "true"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(EE) NVIDIA(0): Failed to load the NVIDIA kernel module!
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(II) UnloadModule: "wfb"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

```

Thanks heaps, I'm going to go get a drink, I'll look forward to any replies :)

---

### Post by phidia on 2008-05-23
It looks like you have a geforce 6600GT gpu is that correct? What version of Ubuntu are you using?
You could try using the [envy script]("http://albertomilone.com/nvidia_scripts1.html") from the general nvidia [how to]("http://ubuntuforums.org/showthread.php?t=301499").
Hope that helps.

---

### Post by Helgiks on 2008-05-23
Did the "restricted drivers" thingy that comes with Ubuntu not work do get the nvidia drivers up'n runnining?

You can use dpkg to automate a new xorg.conf file with either ```
sudo dpkg-reconfigure xserver-xorg
``` than you'll be asked a bunch of questions and finally get a new xorg.conf file (that should work) or use the -phigh argument to make it fully automated, ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` Than startup X, go to System -> Administartion -> Restricted Drivers ... (I'm not on Ubuntu, don't remember the name) and there you can check the "Nvidia drivers" and reboot.

That is the easiest way to make it work as far as im concerned.

---

### Post by alienexplorers on 2008-05-23
When loading 8.04 I was asked once in the program to load the Restricted drivers.  After doing this and rebooting I was stuck with 800x600 graphics and no glx drivers. My xorg.conf said I was using the nvidia driver, but the system just would not run correctly.  I ended up uninstalling Restricted drivers and running Envy-ng.  I selected to manually load the drivers and choose the 96.x.x driver.  This is the nvidia-glx driver.  After rebooting I had full use of nvidia-settings which allowed me to select the proper resolution and refresh rate I wanted.  I was also able to then run the compiz effects and glx was operational.

---

### Post by causticburning on 2008-05-24
I've uninstalled the nVidia driver with envyNG, so I can boot up into my normal resolution, but now I can't run anything openGL, and hardware drivers has no option to turn on the normal driver.

---

