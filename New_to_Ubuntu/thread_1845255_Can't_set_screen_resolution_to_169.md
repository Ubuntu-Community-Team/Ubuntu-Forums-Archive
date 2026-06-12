---
title: "Can't set screen resolution to 16:9"
date: 2011-09-16
forum: New to Ubuntu
---

### Post by TrebleClef on 2011-09-16
I have an emachines e525 laptop with windows 7 which came pre-installed. I have installed ubuntu studio 11.04 but can't set  the screen resolution to a 16:9 one. There is only one option available and that is 4:3. Do I need to install any drivers? I would love to continue to use ubuntu but can't use it with this resolution as I use it to edit photo's amongst other things and everything looks stretched on my screen. Your help would be greatly appreciated.

---

### Post by TeoBigusGeekus on 2011-09-16
Have you checked the "Hardware Drivers" to see if there's a restricted driver for your graphics card?

---

### Post by TrebleClef on 2011-09-17
Do you mean under the "Additional Drivers" option in the System > Administration menu? I have looked there and the only thing that comes up is my WiFi card driver.

---

### Post by Lisiano on 2011-09-17
What version of Ubuntu are you using? I have a eMachine eM350 netbook and it doesn't want to play nice with older versions of Ubuntu and BackTrack.
Also could you post your lspci?
Open a terminal and type lspci, you should get something similar to this
```
lisiano@Lisiano-Ubuntu:~$ lspci
00:00.0 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP78S [GeForce 8200] LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP78S [GeForce 8200] SMBus (rev a1)
...
lisiano@Lisiano-Ubuntu:~$
```
Copy paste it from the start till the finish

---

### Post by TrebleClef on 2011-09-17
Here is the output of lspci:

00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 09)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 09)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
04:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
05:00.0 Ethernet controller: Atheros Communications AR8132 Fast Ethernet (rev c0)

I am using ubuntu studio.

---

### Post by Lisiano on 2011-09-17
Agh didn't notice you said the version in the OP. Anyway. Could you try doing the following. Log out, press Ctrl+Alt+F2 and login, then type the following
```
sudo /etc/init.d/gdm stop
sudo X -configure
sudo /etc/init.d/gdm start
```

---

### Post by TrebleClef on 2011-09-17
Everything remains just the same.

---

### Post by Lisiano on 2011-09-17
Hmm... Could you post your /etc/X11/xorg.conf and the resolution you used in Windows? I'm no expert on xorg.conf files but I could try editing it have a forced resolution.

---

### Post by BicyclerBoy on 2011-09-17
Check the intel driver is loaded & not the vesa..

The current syntax to [] the gdm from console:
sudo service gdm [stop, start, restart]

---

### Post by TrebleClef on 2011-09-18
The resolution I use in Windows 7 is 1366x768. I only have a xorg.conf.failsafe file in the etc/X11 directory. I also have a xorg.conf.new file in my home folder.

Here is the contents of them both:

xorg.conf.failsafe:

Section "Device"
    Identifier    "Configured Video Device"
    Driver        "fbdev"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

xorg.conf.new:

Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
    Screen      2  "Screen2" RightOf "Screen1"
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
    ModulePath   "/usr/lib/xorg/modules"
    FontPath     "/usr/share/fonts/X11/misc"
    FontPath     "/usr/share/fonts/X11/cyrillic"
    FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/Type1"
    FontPath     "/usr/share/fonts/X11/100dpi"
    FontPath     "/usr/share/fonts/X11/75dpi"
    FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
    FontPath     "built-ins"
EndSection

Section "Module"
    Load  "dri"
    Load  "dbe"
    Load  "extmod"
    Load  "dri2"
    Load  "glx"
    Load  "record"
EndSection

Section "InputDevice"
    Identifier  "Keyboard0"
    Driver      "kbd"
EndSection

Section "InputDevice"
    Identifier  "Mouse0"
    Driver      "mouse"
    Option        "Protocol" "auto"
    Option        "Device" "/dev/input/mice"
    Option        "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
    Identifier   "Monitor0"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection

Section "Monitor"
    Identifier   "Monitor1"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection

Section "Monitor"
    Identifier   "Monitor2"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "AccelMethod"            # [<str>]
        #Option     "DRI"                    # [<bool>]
        #Option     "ColorKey"               # <i>
        #Option     "VideoKey"               # <i>
        #Option     "FallbackDebug"          # [<bool>]
        #Option     "Tiling"                 # [<bool>]
        #Option     "Shadow"                 # [<bool>]
        #Option     "SwapbuffersWait"        # [<bool>]
        #Option     "XvMC"                   # [<bool>]
        #Option     "XvPreferOverlay"        # [<bool>]
        #Option     "DebugFlushBatches"      # [<bool>]
        #Option     "DebugFlushCaches"       # [<bool>]
        #Option     "DebugWait"              # [<bool>]
        #Option     "HotPlug"                # [<bool>]
        #Option     "RelaxedFencing"         # [<bool>]
    Identifier  "Card0"
    Driver      "intel"
    BusID       "PCI:0:2:0"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "ShadowFB"               # [<bool>]
        #Option     "Rotate"                 # <str>
        #Option     "fbdev"                  # <str>
        #Option     "debug"                  # [<bool>]
    Identifier  "Card1"
    Driver      "fbdev"
    BusID       "PCI:0:2:0"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "ShadowFB"               # [<bool>]
        #Option     "DefaultRefresh"         # [<bool>]
        #Option     "ModeSetClearScreen"     # [<bool>]
    Identifier  "Card2"
    Driver      "vesa"
    BusID       "PCI:0:2:0"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
    SubSection "Display"
        Viewport   0 0
        Depth     1
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

Section "Screen"
    Identifier "Screen1"
    Device     "Card1"
    Monitor    "Monitor1"
    SubSection "Display"
        Viewport   0 0
        Depth     1
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

Section "Screen"
    Identifier "Screen2"
    Device     "Card2"
    Monitor    "Monitor2"
    SubSection "Display"
        Viewport   0 0
        Depth     1
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

---

### Post by TrebleClef on 2011-09-18
Is it anything to do with me having to use "nomodeset" when I boot. If I don't use nomodeset then I just get a very dark unusable display.

---

### Post by BicyclerBoy on 2011-09-18
The grub option 'nomodeset' prevents any kernel space video mode setting (kms).

All the recent video drivers (for intel nVidia AMD) require kms.
Fairly sure this is the case for the open source AMD & nouveau.

AFAIK If you use nomodeset, then you will end up with vesa driver unless the intel driver is manually modprobe loaded.

You could post your
/var/log/Xorg.0.log
This should help ..

---

### Post by TrebleClef on 2011-09-18
Hiya. Thanks alot for trying to help me. The contents of the Xorg.0.log file are as follows:

[    21.061] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[    21.061] X Protocol Version 11, Revision 0
[    21.061] Build Operating System: Linux 2.6.24-29-server i686 Ubuntu
[    21.061] Current Operating System: Linux ubuntu-gary 2.6.38-11-generic #48-Ubuntu SMP Fri Jul 29 19:05:14 UTC 2011 i686
[    21.061] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-11-generic root=UUID=b37d9056-4fb2-4f9a-be3d-2541fa08f6d2 ro nomodeset vt.handoff=7
[    21.061] Build Date: 11 August 2011  03:47:56PM
[    21.061] xorg-server 2:1.10.1-1ubuntu1.2 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    21.061] Current version of pixman: 0.20.2
[    21.061]     Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
[    21.061] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    21.061] (==) Log file: "/var/log/Xorg.0.log", Time: Sun Sep 18 18:54:31 2011
[    21.103] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    21.103] (==) No Layout section.  Using the first Screen section.
[    21.108] (==) No screen section available. Using defaults.
[    21.108] (**) |-->Screen "Default Screen Section" (0)
[    21.108] (**) |   |-->Monitor "<default monitor>"
[    21.108] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    21.108] (==) Automatically adding devices
[    21.108] (==) Automatically enabling devices
[    21.108] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    21.108]     Entry deleted from font path.
[    21.108] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    21.108]     Entry deleted from font path.
[    21.108] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    21.108]     Entry deleted from font path.
[    21.109] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    21.109]     Entry deleted from font path.
[    21.109] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    21.109]     Entry deleted from font path.
[    21.109] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    21.109] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    21.109] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    21.109] (II) Loader magic: 0x81ffde0
[    21.109] (II) Module ABI versions:
[    21.109]     X.Org ANSI C Emulation: 0.4
[    21.109]     X.Org Video Driver: 10.0
[    21.109]     X.Org XInput driver : 12.3
[    21.109]     X.Org Server Extension : 5.0
[    21.110] (--) PCI:*(0:0:2:0) 8086:2a42:1025:0212 rev 9, Mem @ 0x50000000/4194304, 0x40000000/268435456, I/O @ 0x000050f0/8
[    21.110] (--) PCI: (0:0:2:1) 8086:2a43:1025:0212 rev 9, Mem @ 0x53400000/1048576
[    21.110] (II) Open ACPI successful (/var/run/acpid.socket)
[    21.110] (II) LoadModule: "extmod"
[    21.151] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    21.156] (II) Module extmod: vendor="X.Org Foundation"
[    21.157]     compiled for 1.10.1, module version = 1.0.0
[    21.157]     Module class: X.Org Server Extension
[    21.157]     ABI class: X.Org Server Extension, version 5.0
[    21.157] (II) Loading extension MIT-SCREEN-SAVER
[    21.157] (II) Loading extension XFree86-VidModeExtension
[    21.157] (II) Loading extension XFree86-DGA
[    21.157] (II) Loading extension DPMS
[    21.157] (II) Loading extension XVideo
[    21.157] (II) Loading extension XVideo-MotionCompensation
[    21.157] (II) Loading extension X-Resource
[    21.157] (II) LoadModule: "dbe"
[    21.157] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    21.157] (II) Module dbe: vendor="X.Org Foundation"
[    21.157]     compiled for 1.10.1, module version = 1.0.0
[    21.157]     Module class: X.Org Server Extension
[    21.157]     ABI class: X.Org Server Extension, version 5.0
[    21.157] (II) Loading extension DOUBLE-BUFFER
[    21.157] (II) LoadModule: "glx"
[    21.157] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    21.157] (II) Module glx: vendor="X.Org Foundation"
[    21.157]     compiled for 1.10.1, module version = 1.0.0
[    21.157]     ABI class: X.Org Server Extension, version 5.0
[    21.157] (==) AIGLX enabled
[    21.157] (II) Loading extension GLX
[    21.157] (II) LoadModule: "record"
[    21.157] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    21.157] (II) Module record: vendor="X.Org Foundation"
[    21.157]     compiled for 1.10.1, module version = 1.13.0
[    21.157]     Module class: X.Org Server Extension
[    21.157]     ABI class: X.Org Server Extension, version 5.0
[    21.158] (II) Loading extension RECORD
[    21.158] (II) LoadModule: "dri"
[    21.158] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    21.158] (II) Module dri: vendor="X.Org Foundation"
[    21.158]     compiled for 1.10.1, module version = 1.0.0
[    21.158]     ABI class: X.Org Server Extension, version 5.0
[    21.158] (II) Loading extension XFree86-DRI
[    21.158] (II) LoadModule: "dri2"
[    21.158] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    21.158] (II) Module dri2: vendor="X.Org Foundation"
[    21.158]     compiled for 1.10.1, module version = 1.2.0
[    21.158]     ABI class: X.Org Server Extension, version 5.0
[    21.158] (II) Loading extension DRI2
[    21.158] (==) Matched intel as autoconfigured driver 0
[    21.158] (==) Matched vesa as autoconfigured driver 1
[    21.158] (==) Matched fbdev as autoconfigured driver 2
[    21.158] (==) Assigned the driver to the xf86ConfigLayout
[    21.158] (II) LoadModule: "intel"
[    21.159] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    21.159] (II) Module intel: vendor="X.Org Foundation"
[    21.159]     compiled for 1.10.1, module version = 2.14.0
[    21.159]     Module class: X.Org Video Driver
[    21.159]     ABI class: X.Org Video Driver, version 10.0
[    21.159] (II) LoadModule: "vesa"
[    21.159] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    21.159] (II) Module vesa: vendor="X.Org Foundation"
[    21.159]     compiled for 1.10.0, module version = 2.3.0
[    21.159]     Module class: X.Org Video Driver
[    21.159]     ABI class: X.Org Video Driver, version 10.0
[    21.159] (II) LoadModule: "fbdev"
[    21.159] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    21.159] (II) Module fbdev: vendor="X.Org Foundation"
[    21.159]     compiled for 1.10.0, module version = 0.4.2
[    21.159]     ABI class: X.Org Video Driver, version 10.0
[    21.159] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
    i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
    E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
    965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
    4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
    Sandybridge, Sandybridge, Sandybridge, Sandybridge, Sandybridge,
    Sandybridge, Sandybridge
[    21.160] (II) VESA: driver for VESA chipsets: vesa
[    21.160] (II) FBDEV: driver for framebuffer: fbdev
[    21.160] (++) using VT number 7

[    21.162] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    21.162] (WW) Falling back to old probe method for fbdev
[    21.162] (II) Loading sub module "fbdevhw"
[    21.162] (II) LoadModule: "fbdevhw"
[    21.162] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    21.162] (II) Module fbdevhw: vendor="X.Org Foundation"
[    21.162]     compiled for 1.10.1, module version = 0.0.2
[    21.162]     ABI class: X.Org Video Driver, version 10.0
[    21.162] (II) Loading sub module "vbe"
[    21.162] (II) LoadModule: "vbe"
[    21.163] (II) Loading /usr/lib/xorg/modules/libvbe.so
[    21.163] (II) Module vbe: vendor="X.Org Foundation"
[    21.163]     compiled for 1.10.1, module version = 1.1.0
[    21.163]     ABI class: X.Org Video Driver, version 10.0
[    21.163] (II) Loading sub module "int10"
[    21.163] (II) LoadModule: "int10"
[    21.163] (II) Loading /usr/lib/xorg/modules/libint10.so
[    21.163] (II) Module int10: vendor="X.Org Foundation"
[    21.163]     compiled for 1.10.1, module version = 1.0.0
[    21.163]     ABI class: X.Org Video Driver, version 10.0
[    21.163] (II) VESA(0): initializing int10
[    21.163] (II) VESA(0): Bad V_BIOS checksum
[    21.163] (II) VESA(0): Primary V_BIOS segment is: 0xc000
[    21.164] (II) VESA(0): VESA BIOS detected
[    21.164] (II) VESA(0): VESA VBE Version 3.0
[    21.164] (II) VESA(0): VESA VBE Total Mem: 65472 kB
[    21.164] (II) VESA(0): VESA VBE OEM: Intel(r)Cantiga Graphics Chip Accelerated VGA BIOS
[    21.164] (II) VESA(0): VESA VBE OEM Software Rev: 1.0
[    21.164] (II) VESA(0): VESA VBE OEM Vendor: Intel Corporation
[    21.164] (II) VESA(0): VESA VBE OEM Product: Intel(r)Cantiga Graphics Controller
[    21.164] (II) VESA(0): VESA VBE OEM Product Rev: Hardware Version 0.0
[    21.177] (II) VESA(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    21.177] (==) VESA(0): Depth 24, (--) framebuffer bpp 32
[    21.177] (==) VESA(0): RGB weight 888
[    21.177] (==) VESA(0): Default visual is TrueColor
[    21.177] (==) VESA(0): Using gamma correction (1.0, 1.0, 1.0)
[    21.177] (II) Loading sub module "ddc"
[    21.177] (II) LoadModule: "ddc"
[    21.177] (II) Module "ddc" already built-in
[    21.177] (II) VESA(0): VESA VBE DDC supported
[    21.177] (II) VESA(0): VESA VBE DDC Level 2
[    21.177] (II) VESA(0): VESA VBE DDC transfer in appr. 1 sec.
[    21.190] (II) VESA(0): VESA VBE DDC read successfully
[    21.190] (II) VESA(0): Manufacturer: LGD  Model: 1c2  Serial#: 0
[    21.190] (II) VESA(0): Year: 2008  Week: 0
[    21.190] (II) VESA(0): EDID Version: 1.3
[    21.190] (II) VESA(0): Digital Display Input
[    21.190] (II) VESA(0): Max Image Size [cm]: horiz.: 34  vert.: 19
[    21.190] (II) VESA(0): Gamma: 2.20
[    21.190] (II) VESA(0): No DPMS capabilities specified
[    21.190] (II) VESA(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    21.190] (II) VESA(0): First detailed timing is preferred mode
[    21.190] (II) VESA(0): redX: 0.608 redY: 0.338   greenX: 0.283 greenY: 0.586
[    21.190] (II) VESA(0): blueX: 0.150 blueY: 0.103   whiteX: 0.313 whiteY: 0.329
[    21.190] (II) VESA(0): Manufacturer's mask: 0
[    21.190] (II) VESA(0): Supported detailed timing:
[    21.190] (II) VESA(0): clock: 72.3 MHz   Image Size:  344 x 194 mm
[    21.190] (II) VESA(0): h_active: 1366  h_sync: 1414  h_sync_end 1446 h_blank_end 1526 h_border: 0
[    21.190] (II) VESA(0): v_active: 768  v_sync: 771  v_sync_end 776 v_blanking: 790 v_border: 0
[    21.190] (II) VESA(0):  LG Display
[    21.190] (II) VESA(0): Monitor name: LP156WH1-TLA3
[    21.190] (II) VESA(0): EDID (in hex):
[    21.190] (II) VESA(0):     00ffffffffffff0030e4c20100000000
[    21.190] (II) VESA(0):     00120103802213780ae8959b56489626
[    21.190] (II) VESA(0):     1a505400000001010101010101010101
[    21.190] (II) VESA(0):     0101010101013e1c56a0500016303020
[    21.190] (II) VESA(0):     350058c2100000190000000000000000
[    21.190] (II) VESA(0):     00000000000000000000000000fe004c
[    21.190] (II) VESA(0):     4720446973706c61790a2020000000fc
[    21.190] (II) VESA(0):     004c503135365748312d544c413300de
[    21.190] (II) VESA(0): EDID vendor "LGD", prod id 450
[    21.190] (II) VESA(0): Printing DDC gathered Modelines:
[    21.190] (II) VESA(0): Modeline "1366x768"x0.0   72.30  1366 1414 1446 1526  768 771 776 790 -hsync -vsync (47.4 kHz)
[    21.190] (II) VESA(0): Searching for matching VESA mode(s):
[    21.190] Mode: 160 (0x0)
[    21.190]     ModeAttributes: 0x0
[    21.190]     WinAAttributes: 0x0
[    21.190]     WinBAttributes: 0x0
[    21.190]     WinGranularity: 0
[    21.190]     WinSize: 0
[    21.190]     WinASegment: 0x0
[    21.190]     WinBSegment: 0x0
[    21.190]     WinFuncPtr: 0x0
[    21.190]     BytesPerScanline: 0
[    21.190]     XResolution: 0
[    21.190]     YResolution: 0
[    21.190]     XCharSize: 0
[    21.190]     YCharSize: 0
[    21.190]     NumberOfPlanes: 0
[    21.190]     BitsPerPixel: 0
[    21.190]     NumberOfBanks: 0
[    21.190]     MemoryModel: 0
[    21.190]     BankSize: 0
[    21.190]     NumberOfImages: 0
[    21.190]     RedMaskSize: 0
[    21.190]     RedFieldPosition: 0
[    21.190]     GreenMaskSize: 0
[    21.190]     GreenFieldPosition: 0
[    21.190]     BlueMaskSize: 0
[    21.190]     BlueFieldPosition: 0
[    21.190]     RsvdMaskSize: 0
[    21.190]     RsvdFieldPosition: 0
[    21.190]     DirectColorModeInfo: 0
[    21.190]     PhysBasePtr: 0x0
[    21.190]     LinBytesPerScanLine: 0
[    21.190]     BnkNumberOfImagePages: 0
[    21.190]     LinNumberOfImagePages: 0
[    21.190]     LinRedMaskSize: 0
[    21.190]     LinRedFieldPosition: 0
[    21.190]     LinGreenMaskSize: 0
[    21.190]     LinGreenFieldPosition: 0
[    21.190]     LinBlueMaskSize: 0
[    21.190]     LinBlueFieldPosition: 0
[    21.190]     LinRsvdMaskSize: 0
[    21.190]     LinRsvdFieldPosition: 0
[    21.190]     MaxPixelClock: 0
[    21.191] Mode: 161 (0x0)
[    21.191]     ModeAttributes: 0x0
[    21.191]     WinAAttributes: 0x0
[    21.191]     WinBAttributes: 0x0
[    21.191]     WinGranularity: 0
[    21.191]     WinSize: 0
[    21.191]     WinASegment: 0x0
[    21.191]     WinBSegment: 0x0
[    21.191]     WinFuncPtr: 0x0
[    21.191]     BytesPerScanline: 0
[    21.191]     XResolution: 0
[    21.191]     YResolution: 0
[    21.191]     XCharSize: 0
[    21.191]     YCharSize: 0
[    21.191]     NumberOfPlanes: 0
[    21.191]     BitsPerPixel: 0
[    21.191]     NumberOfBanks: 0
[    21.191]     MemoryModel: 0
[    21.191]     BankSize: 0
[    21.191]     NumberOfImages: 0
[    21.191]     RedMaskSize: 0
[    21.191]     RedFieldPosition: 0
[    21.191]     GreenMaskSize: 0
[    21.191]     GreenFieldPosition: 0
[    21.191]     BlueMaskSize: 0
[    21.191]     BlueFieldPosition: 0
[    21.191]     RsvdMaskSize: 0
[    21.191]     RsvdFieldPosition: 0
[    21.191]     DirectColorModeInfo: 0
[    21.191]     PhysBasePtr: 0x0
[    21.191]     LinBytesPerScanLine: 0
[    21.191]     BnkNumberOfImagePages: 0
[    21.191]     LinNumberOfImagePages: 0
[    21.191]     LinRedMaskSize: 0
[    21.191]     LinRedFieldPosition: 0
[    21.191]     LinGreenMaskSize: 0
[    21.191]     LinGreenFieldPosition: 0
[    21.191]     LinBlueMaskSize: 0
[    21.191]     LinBlueFieldPosition: 0
[    21.191]     LinRsvdMaskSize: 0
[    21.191]     LinRsvdFieldPosition: 0
[    21.191]     MaxPixelClock: 0
[    21.191] Mode: 162 (0x0)
[    21.191]     ModeAttributes: 0x0
[    21.191]     WinAAttributes: 0x0
[    21.191]     WinBAttributes: 0x0
[    21.191]     WinGranularity: 0
[    21.191]     WinSize: 0
[    21.191]     WinASegment: 0x0
[    21.191]     WinBSegment: 0x0
[    21.191]     WinFuncPtr: 0x0
[    21.191]     BytesPerScanline: 0
[    21.191]     XResolution: 0
[    21.191]     YResolution: 0
[    21.191]     XCharSize: 0
[    21.191]     YCharSize: 0
[    21.191]     NumberOfPlanes: 0
[    21.191]     BitsPerPixel: 0
[    21.191]     NumberOfBanks: 0
[    21.191]     MemoryModel: 0
[    21.191]     BankSize: 0
[    21.191]     NumberOfImages: 0
[    21.191]     RedMaskSize: 0
[    21.191]     RedFieldPosition: 0
[    21.191]     GreenMaskSize: 0
[    21.191]     GreenFieldPosition: 0
[    21.191]     BlueMaskSize: 0
[    21.191]     BlueFieldPosition: 0
[    21.191]     RsvdMaskSize: 0
[    21.191]     RsvdFieldPosition: 0
[    21.191]     DirectColorModeInfo: 0
[    21.191]     PhysBasePtr: 0x0
[    21.191]     LinBytesPerScanLine: 0
[    21.191]     BnkNumberOfImagePages: 0
[    21.191]     LinNumberOfImagePages: 0
[    21.191]     LinRedMaskSize: 0
[    21.191]     LinRedFieldPosition: 0
[    21.191]     LinGreenMaskSize: 0
[    21.191]     LinGreenFieldPosition: 0
[    21.191]     LinBlueMaskSize: 0
[    21.191]     LinBlueFieldPosition: 0
[    21.191]     LinRsvdMaskSize: 0
[    21.191]     LinRsvdFieldPosition: 0
[    21.191]     MaxPixelClock: 0
[    21.191] Mode: 163 (0x0)
[    21.191]     ModeAttributes: 0x0
[    21.191]     WinAAttributes: 0x0
[    21.191]     WinBAttributes: 0x0
[    21.191]     WinGranularity: 0
[    21.191]     WinSize: 0
[    21.191]     WinASegment: 0x0
[    21.191]     WinBSegment: 0x0
[    21.191]     WinFuncPtr: 0x0
[    21.191]     BytesPerScanline: 0
[    21.192]     XResolution: 0
[    21.192]     YResolution: 0
[    21.192]     XCharSize: 0
[    21.192]     YCharSize: 0
[    21.192]     NumberOfPlanes: 0
[    21.192]     BitsPerPixel: 0
[    21.192]     NumberOfBanks: 0
[    21.192]     MemoryModel: 0
[    21.192]     BankSize: 0
[    21.192]     NumberOfImages: 0
[    21.192]     RedMaskSize: 0
[    21.192]     RedFieldPosition: 0
[    21.192]     GreenMaskSize: 0
[    21.192]     GreenFieldPosition: 0
[    21.192]     BlueMaskSize: 0
[    21.192]     BlueFieldPosition: 0
[    21.192]     RsvdMaskSize: 0
[    21.192]     RsvdFieldPosition: 0
[    21.192]     DirectColorModeInfo: 0
[    21.192]     PhysBasePtr: 0x0
[    21.192]     LinBytesPerScanLine: 0
[    21.192]     BnkNumberOfImagePages: 0
[    21.192]     LinNumberOfImagePages: 0
[    21.192]     LinRedMaskSize: 0
[    21.192]     LinRedFieldPosition: 0
[    21.192]     LinGreenMaskSize: 0
[    21.192]     LinGreenFieldPosition: 0
[    21.192]     LinBlueMaskSize: 0
[    21.192]     LinBlueFieldPosition: 0
[    21.192]     LinRsvdMaskSize: 0
[    21.192]     LinRsvdFieldPosition: 0
[    21.192]     MaxPixelClock: 0
[    21.192] Mode: 164 (0x0)
[    21.192]     ModeAttributes: 0x0
[    21.192]     WinAAttributes: 0x0
[    21.192]     WinBAttributes: 0x0
[    21.192]     WinGranularity: 0
[    21.192]     WinSize: 0
[    21.192]     WinASegment: 0x0
[    21.192]     WinBSegment: 0x0
[    21.192]     WinFuncPtr: 0x0
[    21.192]     BytesPerScanline: 0
[    21.192]     XResolution: 0
[    21.192]     YResolution: 0
[    21.192]     XCharSize: 0
[    21.192]     YCharSize: 0
[    21.192]     NumberOfPlanes: 0
[    21.192]     BitsPerPixel: 0
[    21.192]     NumberOfBanks: 0
[    21.192]     MemoryModel: 0
[    21.192]     BankSize: 0
[    21.192]     NumberOfImages: 0
[    21.192]     RedMaskSize: 0
[    21.192]     RedFieldPosition: 0
[    21.192]     GreenMaskSize: 0
[    21.192]     GreenFieldPosition: 0
[    21.192]     BlueMaskSize: 0
[    21.192]     BlueFieldPosition: 0
[    21.192]     RsvdMaskSize: 0
[    21.192]     RsvdFieldPosition: 0
[    21.192]     DirectColorModeInfo: 0
[    21.192]     PhysBasePtr: 0x0
[    21.192]     LinBytesPerScanLine: 0
[    21.192]     BnkNumberOfImagePages: 0
[    21.192]     LinNumberOfImagePages: 0
[    21.192]     LinRedMaskSize: 0
[    21.192]     LinRedFieldPosition: 0
[    21.192]     LinGreenMaskSize: 0
[    21.192]     LinGreenFieldPosition: 0
[    21.192]     LinBlueMaskSize: 0
[    21.192]     LinBlueFieldPosition: 0
[    21.192]     LinRsvdMaskSize: 0
[    21.192]     LinRsvdFieldPosition: 0
[    21.192]     MaxPixelClock: 0
[    21.192] Mode: 165 (0x0)
[    21.192]     ModeAttributes: 0x0
[    21.192]     WinAAttributes: 0x0
[    21.192]     WinBAttributes: 0x0
[    21.192]     WinGranularity: 0
[    21.192]     WinSize: 0
[    21.192]     WinASegment: 0x0
[    21.192]     WinBSegment: 0x0
[    21.192]     WinFuncPtr: 0x0
[    21.192]     BytesPerScanline: 0
[    21.192]     XResolution: 0
[    21.192]     YResolution: 0
[    21.192]     XCharSize: 0
[    21.192]     YCharSize: 0
[    21.192]     NumberOfPlanes: 0
[    21.192]     BitsPerPixel: 0
[    21.192]     NumberOfBanks: 0
[    21.192]     MemoryModel: 0
[    21.192]     BankSize: 0
[    21.192]     NumberOfImages: 0
[    21.192]     RedMaskSize: 0
[    21.192]     RedFieldPosition: 0
[    21.192]     GreenMaskSize: 0
[    21.192]     GreenFieldPosition: 0
[    21.192]     BlueMaskSize: 0
[    21.192]     BlueFieldPosition: 0
[    21.193]     RsvdMaskSize: 0
[    21.193]     RsvdFieldPosition: 0
[    21.193]     DirectColorModeInfo: 0
[    21.193]     PhysBasePtr: 0x0
[    21.193]     LinBytesPerScanLine: 0
[    21.193]     BnkNumberOfImagePages: 0
[    21.193]     LinNumberOfImagePages: 0
[    21.193]     LinRedMaskSize: 0
[    21.193]     LinRedFieldPosition: 0
[    21.193]     LinGreenMaskSize: 0
[    21.193]     LinGreenFieldPosition: 0
[    21.193]     LinBlueMaskSize: 0
[    21.193]     LinBlueFieldPosition: 0
[    21.193]     LinRsvdMaskSize: 0
[    21.193]     LinRsvdFieldPosition: 0
[    21.193]     MaxPixelClock: 0
[    21.193] Mode: 166 (0x0)
[    21.193]     ModeAttributes: 0x0
[    21.193]     WinAAttributes: 0x0
[    21.193]     WinBAttributes: 0x0
[    21.193]     WinGranularity: 0
[    21.193]     WinSize: 0
[    21.193]     WinASegment: 0x0
[    21.193]     WinBSegment: 0x0
[    21.193]     WinFuncPtr: 0x0
[    21.193]     BytesPerScanline: 0
[    21.193]     XResolution: 0
[    21.193]     YResolution: 0
[    21.193]     XCharSize: 0
[    21.193]     YCharSize: 0
[    21.193]     NumberOfPlanes: 0
[    21.193]     BitsPerPixel: 0
[    21.193]     NumberOfBanks: 0
[    21.193]     MemoryModel: 0
[    21.193]     BankSize: 0
[    21.193]     NumberOfImages: 0
[    21.193]     RedMaskSize: 0
[    21.193]     RedFieldPosition: 0
[    21.193]     GreenMaskSize: 0
[    21.193]     GreenFieldPosition: 0
[    21.193]     BlueMaskSize: 0
[    21.193]     BlueFieldPosition: 0
[    21.193]     RsvdMaskSize: 0
[    21.193]     RsvdFieldPosition: 0
[    21.193]     DirectColorModeInfo: 0
[    21.193]     PhysBasePtr: 0x0
[    21.193]     LinBytesPerScanLine: 0
[    21.193]     BnkNumberOfImagePages: 0
[    21.193]     LinNumberOfImagePages: 0
[    21.193]     LinRedMaskSize: 0
[    21.193]     LinRedFieldPosition: 0
[    21.193]     LinGreenMaskSize: 0
[    21.193]     LinGreenFieldPosition: 0
[    21.193]     LinBlueMaskSize: 0
[    21.193]     LinBlueFieldPosition: 0
[    21.193]     LinRsvdMaskSize: 0
[    21.193]     LinRsvdFieldPosition: 0
[    21.193]     MaxPixelClock: 0
[    21.193] Mode: 167 (0x0)
[    21.193]     ModeAttributes: 0x0
[    21.193]     WinAAttributes: 0x0
[    21.193]     WinBAttributes: 0x0
[    21.193]     WinGranularity: 0
[    21.193]     WinSize: 0
[    21.193]     WinASegment: 0x0
[    21.193]     WinBSegment: 0x0
[    21.193]     WinFuncPtr: 0x0
[    21.193]     BytesPerScanline: 0
[    21.193]     XResolution: 0
[    21.193]     YResolution: 0
[    21.193]     XCharSize: 0
[    21.193]     YCharSize: 0
[    21.193]     NumberOfPlanes: 0
[    21.193]     BitsPerPixel: 0
[    21.193]     NumberOfBanks: 0
[    21.193]     MemoryModel: 0
[    21.193]     BankSize: 0
[    21.193]     NumberOfImages: 0
[    21.193]     RedMaskSize: 0
[    21.193]     RedFieldPosition: 0
[    21.193]     GreenMaskSize: 0
[    21.193]     GreenFieldPosition: 0
[    21.193]     BlueMaskSize: 0
[    21.193]     BlueFieldPosition: 0
[    21.193]     RsvdMaskSize: 0
[    21.193]     RsvdFieldPosition: 0
[    21.193]     DirectColorModeInfo: 0
[    21.193]     PhysBasePtr: 0x0
[    21.193]     LinBytesPerScanLine: 0
[    21.193]     BnkNumberOfImagePages: 0
[    21.193]     LinNumberOfImagePages: 0
[    21.193]     LinRedMaskSize: 0
[    21.193]     LinRedFieldPosition: 0
[    21.193]     LinGreenMaskSize: 0
[    21.193]     LinGreenFieldPosition: 0
[    21.193]     LinBlueMaskSize: 0
[    21.193]     LinBlueFieldPosition: 0
[    21.193]     LinRsvdMaskSize: 0
[    21.193]     LinRsvdFieldPosition: 0
[    21.193]     MaxPixelClock: 0
[    21.194] Mode: 168 (0x0)
[    21.194]     ModeAttributes: 0x0
[    21.194]     WinAAttributes: 0x0
[    21.194]     WinBAttributes: 0x0
[    21.194]     WinGranularity: 0
[    21.194]     WinSize: 0
[    21.194]     WinASegment: 0x0
[    21.194]     WinBSegment: 0x0
[    21.194]     WinFuncPtr: 0x0
[    21.194]     BytesPerScanline: 0
[    21.194]     XResolution: 0
[    21.194]     YResolution: 0
[    21.194]     XCharSize: 0
[    21.194]     YCharSize: 0
[    21.194]     NumberOfPlanes: 0
[    21.194]     BitsPerPixel: 0
[    21.194]     NumberOfBanks: 0
[    21.194]     MemoryModel: 0
[    21.194]     BankSize: 0
[    21.194]     NumberOfImages: 0
[    21.194]     RedMaskSize: 0
[    21.194]     RedFieldPosition: 0
[    21.194]     GreenMaskSize: 0
[    21.194]     GreenFieldPosition: 0
[    21.194]     BlueMaskSize: 0
[    21.194]     BlueFieldPosition: 0
[    21.194]     RsvdMaskSize: 0
[    21.194]     RsvdFieldPosition: 0
[    21.194]     DirectColorModeInfo: 0
[    21.194]     PhysBasePtr: 0x0
[    21.194]     LinBytesPerScanLine: 0
[    21.194]     BnkNumberOfImagePages: 0
[    21.194]     LinNumberOfImagePages: 0
[    21.194]     LinRedMaskSize: 0
[    21.194]     LinRedFieldPosition: 0
[    21.194]     LinGreenMaskSize: 0
[    21.194]     LinGreenFieldPosition: 0
[    21.194]     LinBlueMaskSize: 0
[    21.194]     LinBlueFieldPosition: 0
[    21.194]     LinRsvdMaskSize: 0
[    21.194]     LinRsvdFieldPosition: 0
[    21.194]     MaxPixelClock: 0
[    21.194] Mode: 169 (0x0)
[    21.194]     ModeAttributes: 0x0
[    21.194]     WinAAttributes: 0x0
[    21.194]     WinBAttributes: 0x0
[    21.194]     WinGranularity: 0
[    21.194]     WinSize: 0
[    21.194]     WinASegment: 0x0
[    21.194]     WinBSegment: 0x0
[    21.194]     WinFuncPtr: 0x0
[    21.194]     BytesPerScanline: 0
[    21.194]     XResolution: 0
[    21.194]     YResolution: 0
[    21.194]     XCharSize: 0
[    21.194]     YCharSize: 0
[    21.194]     NumberOfPlanes: 0
[    21.194]     BitsPerPixel: 0
[    21.194]     NumberOfBanks: 0
[    21.194]     MemoryModel: 0
[    21.194]     BankSize: 0
[    21.194]     NumberOfImages: 0
[    21.194]     RedMaskSize: 0
[    21.194]     RedFieldPosition: 0
[    21.194]     GreenMaskSize: 0
[    21.194]     GreenFieldPosition: 0
[    21.194]     BlueMaskSize: 0
[    21.194]     BlueFieldPosition: 0
[    21.194]     RsvdMaskSize: 0
[    21.194]     RsvdFieldPosition: 0
[    21.194]     DirectColorModeInfo: 0
[    21.194]     PhysBasePtr: 0x0
[    21.194]     LinBytesPerScanLine: 0
[    21.194]     BnkNumberOfImagePages: 0
[    21.194]     LinNumberOfImagePages: 0
[    21.194]     LinRedMaskSize: 0
[    21.194]     LinRedFieldPosition: 0
[    21.194]     LinGreenMaskSize: 0
[    21.194]     LinGreenFieldPosition: 0
[    21.194]     LinBlueMaskSize: 0
[    21.194]     LinBlueFieldPosition: 0
[    21.194]     LinRsvdMaskSize: 0
[    21.194]     LinRsvdFieldPosition: 0
[    21.194]     MaxPixelClock: 0
[    21.195] Mode: 16a (0x0)
[    21.195]     ModeAttributes: 0x0
[    21.195]     WinAAttributes: 0x0
[    21.195]     WinBAttributes: 0x0
[    21.195]     WinGranularity: 0
[    21.195]     WinSize: 0
[    21.195]     WinASegment: 0x0
[    21.195]     WinBSegment: 0x0
[    21.195]     WinFuncPtr: 0x0
[    21.195]     BytesPerScanline: 0
[    21.195]     XResolution: 0
[    21.195]     YResolution: 0
[    21.195]     XCharSize: 0
[    21.195]     YCharSize: 0
[    21.195]     NumberOfPlanes: 0
[    21.195]     BitsPerPixel: 0
[    21.195]     NumberOfBanks: 0
[    21.195]     MemoryModel: 0
[    21.195]     BankSize: 0
[    21.195]     NumberOfImages: 0
[    21.195]     RedMaskSize: 0
[    21.195]     RedFieldPosition: 0
[    21.195]     GreenMaskSize: 0
[    21.195]     GreenFieldPosition: 0
[    21.195]     BlueMaskSize: 0
[    21.195]     BlueFieldPosition: 0
[    21.195]     RsvdMaskSize: 0
[    21.195]     RsvdFieldPosition: 0
[    21.195]     DirectColorModeInfo: 0
[    21.195]     PhysBasePtr: 0x0
[    21.195]     LinBytesPerScanLine: 0
[    21.195]     BnkNumberOfImagePages: 0
[    21.195]     LinNumberOfImagePages: 0
[    21.195]     LinRedMaskSize: 0
[    21.195]     LinRedFieldPosition: 0
[    21.195]     LinGreenMaskSize: 0
[    21.195]     LinGreenFieldPosition: 0
[    21.195]     LinBlueMaskSize: 0
[    21.195]     LinBlueFieldPosition: 0
[    21.195]     LinRsvdMaskSize: 0
[    21.195]     LinRsvdFieldPosition: 0
[    21.195]     MaxPixelClock: 0
[    21.195] Mode: 16b (0x0)
[    21.195]     ModeAttributes: 0x0
[    21.195]     WinAAttributes: 0x0
[    21.195]     WinBAttributes: 0x0
[    21.195]     WinGranularity: 0
[    21.195]     WinSize: 0
[    21.195]     WinASegment: 0x0
[    21.195]     WinBSegment: 0x0
[    21.195]     WinFuncPtr: 0x0
[    21.195]     BytesPerScanline: 0
[    21.195]     XResolution: 0
[    21.195]     YResolution: 0
[    21.195]     XCharSize: 0
[    21.195]     YCharSize: 0
[    21.195]     NumberOfPlanes: 0
[    21.195]     BitsPerPixel: 0
[    21.195]     NumberOfBanks: 0
[    21.195]     MemoryModel: 0
[    21.195]     BankSize: 0
[    21.195]     NumberOfImages: 0
[    21.195]     RedMaskSize: 0
[    21.195]     RedFieldPosition: 0
[    21.195]     GreenMaskSize: 0
[    21.195]     GreenFieldPosition: 0
[    21.195]     BlueMaskSize: 0
[    21.195]     BlueFieldPosition: 0
[    21.195]     RsvdMaskSize: 0
[    21.195]     RsvdFieldPosition: 0
[    21.195]     DirectColorModeInfo: 0
[    21.195]     PhysBasePtr: 0x0
[    21.195]     LinBytesPerScanLine: 0
[    21.195]     BnkNumberOfImagePages: 0
[    21.195]     LinNumberOfImagePages: 0
[    21.195]     LinRedMaskSize: 0
[    21.195]     LinRedFieldPosition: 0
[    21.195]     LinGreenMaskSize: 0
[    21.195]     LinGreenFieldPosition: 0
[    21.195]     LinBlueMaskSize: 0
[    21.195]     LinBlueFieldPosition: 0
[    21.195]     LinRsvdMaskSize: 0
[    21.195]     LinRsvdFieldPosition: 0
[    21.195]     MaxPixelClock: 0
[    21.195] Mode: 16c (0x0)
[    21.195]     ModeAttributes: 0x0
[    21.195]     WinAAttributes: 0x0
[    21.195]     WinBAttributes: 0x0
[    21.195]     WinGranularity: 0
[    21.195]     WinSize: 0
[    21.195]     WinASegment: 0x0
[    21.195]     WinBSegment: 0x0
[    21.195]     WinFuncPtr: 0x0
[    21.195]     BytesPerScanline: 0
[    21.195]     XResolution: 0
[    21.195]     YResolution: 0
[    21.196]     XCharSize: 0
[    21.196]     YCharSize: 0
[    21.196]     NumberOfPlanes: 0
[    21.196]     BitsPerPixel: 0
[    21.196]     NumberOfBanks: 0
[    21.196]     MemoryModel: 0
[    21.196]     BankSize: 0
[    21.196]     NumberOfImages: 0
[    21.196]     RedMaskSize: 0
[    21.196]     RedFieldPosition: 0
[    21.196]     GreenMaskSize: 0
[    21.196]     GreenFieldPosition: 0
[    21.196]     BlueMaskSize: 0
[    21.196]     BlueFieldPosition: 0
[    21.196]     RsvdMaskSize: 0
[    21.196]     RsvdFieldPosition: 0
[    21.196]     DirectColorModeInfo: 0
[    21.196]     PhysBasePtr: 0x0
[    21.196]     LinBytesPerScanLine: 0
[    21.196]     BnkNumberOfImagePages: 0
[    21.196]     LinNumberOfImagePages: 0
[    21.196]     LinRedMaskSize: 0
[    21.196]     LinRedFieldPosition: 0
[    21.196]     LinGreenMaskSize: 0
[    21.196]     LinGreenFieldPosition: 0
[    21.196]     LinBlueMaskSize: 0
[    21.196]     LinBlueFieldPosition: 0
[    21.196]     LinRsvdMaskSize: 0
[    21.196]     LinRsvdFieldPosition: 0
[    21.196]     MaxPixelClock: 0
[    21.196] Mode: 16d (0x0)
[    21.196]     ModeAttributes: 0x0
[    21.196]     WinAAttributes: 0x0
[    21.196]     WinBAttributes: 0x0
[    21.196]     WinGranularity: 0
[    21.196]     WinSize: 0
[    21.196]     WinASegment: 0x0
[    21.196]     WinBSegment: 0x0
[    21.196]     WinFuncPtr: 0x0
[    21.196]     BytesPerScanline: 0
[    21.196]     XResolution: 0
[    21.196]     YResolution: 0
[    21.196]     XCharSize: 0
[    21.196]     YCharSize: 0
[    21.196]     NumberOfPlanes: 0
[    21.196]     BitsPerPixel: 0
[    21.196]     NumberOfBanks: 0
[    21.196]     MemoryModel: 0
[    21.196]     BankSize: 0
[    21.196]     NumberOfImages: 0
[    21.196]     RedMaskSize: 0
[    21.196]     RedFieldPosition: 0
[    21.196]     GreenMaskSize: 0
[    21.196]     GreenFieldPosition: 0
[    21.196]     BlueMaskSize: 0
[    21.196]     BlueFieldPosition: 0
[    21.196]     RsvdMaskSize: 0
[    21.196]     RsvdFieldPosition: 0
[    21.196]     DirectColorModeInfo: 0
[    21.196]     PhysBasePtr: 0x0
[    21.196]     LinBytesPerScanLine: 0
[    21.196]     BnkNumberOfImagePages: 0
[    21.196]     LinNumberOfImagePages: 0
[    21.196]     LinRedMaskSize: 0
[    21.196]     LinRedFieldPosition: 0
[    21.196]     LinGreenMaskSize: 0
[    21.196]     LinGreenFieldPosition: 0
[    21.196]     LinBlueMaskSize: 0
[    21.196]     LinBlueFieldPosition: 0
[    21.196]     LinRsvdMaskSize: 0
[    21.196]     LinRsvdFieldPosition: 0
[    21.196]     MaxPixelClock: 0
[    21.196] Mode: 16e (0x0)
[    21.196]     ModeAttributes: 0x0
[    21.196]     WinAAttributes: 0x0
[    21.196]     WinBAttributes: 0x0
[    21.196]     WinGranularity: 0
[    21.196]     WinSize: 0
[    21.196]     WinASegment: 0x0
[    21.196]     WinBSegment: 0x0
[    21.196]     WinFuncPtr: 0x0
[    21.196]     BytesPerScanline: 0
[    21.196]     XResolution: 0
[    21.196]     YResolution: 0
[    21.196]     XCharSize: 0
[    21.196]     YCharSize: 0
[    21.196]     NumberOfPlanes: 0
[    21.196]     BitsPerPixel: 0
[    21.196]     NumberOfBanks: 0
[    21.196]     MemoryModel: 0
[    21.196]     BankSize: 0
[    21.196]     NumberOfImages: 0
[    21.196]     RedMaskSize: 0
[    21.196]     RedFieldPosition: 0
[    21.196]     GreenMaskSize: 0
[    21.197]     GreenFieldPosition: 0
[    21.197]     BlueMaskSize: 0
[    21.197]     BlueFieldPosition: 0
[    21.197]     RsvdMaskSize: 0
[    21.197]     RsvdFieldPosition: 0
[    21.197]     DirectColorModeInfo: 0
[    21.197]     PhysBasePtr: 0x0
[    21.197]     LinBytesPerScanLine: 0
[    21.197]     BnkNumberOfImagePages: 0
[    21.197]     LinNumberOfImagePages: 0
[    21.197]     LinRedMaskSize: 0
[    21.197]     LinRedFieldPosition: 0
[    21.197]     LinGreenMaskSize: 0
[    21.197]     LinGreenFieldPosition: 0
[    21.197]     LinBlueMaskSize: 0
[    21.197]     LinBlueFieldPosition: 0
[    21.197]     LinRsvdMaskSize: 0
[    21.197]     LinRsvdFieldPosition: 0
[    21.197]     MaxPixelClock: 0
[    21.197] Mode: 16f (0x0)
[    21.197]     ModeAttributes: 0x0
[    21.197]     WinAAttributes: 0x0
[    21.197]     WinBAttributes: 0x0
[    21.197]     WinGranularity: 0
[    21.197]     WinSize: 0
[    21.197]     WinASegment: 0x0
[    21.197]     WinBSegment: 0x0
[    21.197]     WinFuncPtr: 0x0
[    21.197]     BytesPerScanline: 0
[    21.197]     XResolution: 0
[    21.197]     YResolution: 0
[    21.197]     XCharSize: 0
[    21.197]     YCharSize: 0
[    21.197]     NumberOfPlanes: 0
[    21.197]     BitsPerPixel: 0
[    21.197]     NumberOfBanks: 0
[    21.197]     MemoryModel: 0
[    21.197]     BankSize: 0
[    21.197]     NumberOfImages: 0
[    21.197]     RedMaskSize: 0
[    21.197]     RedFieldPosition: 0
[    21.197]     GreenMaskSize: 0
[    21.197]     GreenFieldPosition: 0
[    21.197]     BlueMaskSize: 0
[    21.197]     BlueFieldPosition: 0
[    21.197]     RsvdMaskSize: 0
[    21.197]     RsvdFieldPosition: 0
[    21.197]     DirectColorModeInfo: 0
[    21.197]     PhysBasePtr: 0x0
[    21.197]     LinBytesPerScanLine: 0
[    21.197]     BnkNumberOfImagePages: 0
[    21.197]     LinNumberOfImagePages: 0
[    21.197]     LinRedMaskSize: 0
[    21.197]     LinRedFieldPosition: 0
[    21.197]     LinGreenMaskSize: 0
[    21.197]     LinGreenFieldPosition: 0
[    21.197]     LinBlueMaskSize: 0
[    21.197]     LinBlueFieldPosition: 0
[    21.197]     LinRsvdMaskSize: 0
[    21.197]     LinRsvdFieldPosition: 0
[    21.197]     MaxPixelClock: 0
[    21.197] Mode: 170 (0x0)
[    21.197]     ModeAttributes: 0x0
[    21.197]     WinAAttributes: 0x0
[    21.197]     WinBAttributes: 0x0
[    21.197]     WinGranularity: 0
[    21.197]     WinSize: 0
[    21.197]     WinASegment: 0x0
[    21.197]     WinBSegment: 0x0
[    21.197]     WinFuncPtr: 0x0
[    21.197]     BytesPerScanline: 0
[    21.197]     XResolution: 0
[    21.197]     YResolution: 0
[    21.197]     XCharSize: 0
[    21.197]     YCharSize: 0
[    21.197]     NumberOfPlanes: 0
[    21.197]     BitsPerPixel: 0
[    21.197]     NumberOfBanks: 0
[    21.197]     MemoryModel: 0
[    21.197]     BankSize: 0
[    21.197]     NumberOfImages: 0
[    21.197]     RedMaskSize: 0
[    21.197]     RedFieldPosition: 0
[    21.197]     GreenMaskSize: 0
[    21.197]     GreenFieldPosition: 0
[    21.197]     BlueMaskSize: 0
[    21.197]     BlueFieldPosition: 0
[    21.197]     RsvdMaskSize: 0
[    21.197]     RsvdFieldPosition: 0
[    21.197]     DirectColorModeInfo: 0
[    21.197]     PhysBasePtr: 0x0
[    21.197]     LinBytesPerScanLine: 0
[    21.197]     BnkNumberOfImagePages: 0
[    21.197]     LinNumberOfImagePages: 0
[    21.197]     LinRedMaskSize: 0
[    21.197]     LinRedFieldPosition: 0
[    21.198]     LinGreenMaskSize: 0
[    21.198]     LinGreenFieldPosition: 0
[    21.198]     LinBlueMaskSize: 0
[    21.198]     LinBlueFieldPosition: 0
[    21.198]     LinRsvdMaskSize: 0
[    21.198]     LinRsvdFieldPosition: 0
[    21.198]     MaxPixelClock: 0
[    21.198] Mode: 171 (0x0)
[    21.198]     ModeAttributes: 0x0
[    21.198]     WinAAttributes: 0x0
[    21.198]     WinBAttributes: 0x0
[    21.198]     WinGranularity: 0
[    21.198]     WinSize: 0
[    21.198]     WinASegment: 0x0
[    21.198]     WinBSegment: 0x0
[    21.198]     WinFuncPtr: 0x0
[    21.198]     BytesPerScanline: 0
[    21.198]     XResolution: 0
[    21.198]     YResolution: 0
[    21.198]     XCharSize: 0
[    21.198]     YCharSize: 0
[    21.198]     NumberOfPlanes: 0
[    21.198]     BitsPerPixel: 0
[    21.198]     NumberOfBanks: 0
[    21.198]     MemoryModel: 0
[    21.198]     BankSize: 0
[    21.198]     NumberOfImages: 0
[    21.198]     RedMaskSize: 0
[    21.198]     RedFieldPosition: 0
[    21.198]     GreenMaskSize: 0
[    21.198]     GreenFieldPosition: 0
[    21.198]     BlueMaskSize: 0
[    21.198]     BlueFieldPosition: 0
[    21.198]     RsvdMaskSize: 0
[    21.198]     RsvdFieldPosition: 0
[    21.198]     DirectColorModeInfo: 0
[    21.198]     PhysBasePtr: 0x0
[    21.198]     LinBytesPerScanLine: 0
[    21.198]     BnkNumberOfImagePages: 0
[    21.198]     LinNumberOfImagePages: 0
[    21.198]     LinRedMaskSize: 0
[    21.198]     LinRedFieldPosition: 0
[    21.198]     LinGreenMaskSize: 0
[    21.198]     LinGreenFieldPosition: 0
[    21.198]     LinBlueMaskSize: 0
[    21.198]     LinBlueFieldPosition: 0
[    21.198]     LinRsvdMaskSize: 0
[    21.198]     LinRsvdFieldPosition: 0
[    21.198]     MaxPixelClock: 0
[    21.198] Mode: 13c (0x0)
[    21.199]     ModeAttributes: 0x0
[    21.199]     WinAAttributes: 0x0
[    21.199]     WinBAttributes: 0x0
[    21.199]     WinGranularity: 0
[    21.199]     WinSize: 0
[    21.199]     WinASegment: 0x0
[    21.199]     WinBSegment: 0x0
[    21.199]     WinFuncPtr: 0x0
[    21.199]     BytesPerScanline: 0
[    21.199]     XResolution: 0
[    21.199]     YResolution: 0
[    21.199]     XCharSize: 0
[    21.199]     YCharSize: 0
[    21.199]     NumberOfPlanes: 0
[    21.199]     BitsPerPixel: 0
[    21.199]     NumberOfBanks: 0
[    21.199]     MemoryModel: 0
[    21.199]     BankSize: 0
[    21.199]     NumberOfImages: 0
[    21.199]     RedMaskSize: 0
[    21.199]     RedFieldPosition: 0
[    21.199]     GreenMaskSize: 0
[    21.199]     GreenFieldPosition: 0
[    21.199]     BlueMaskSize: 0
[    21.199]     BlueFieldPosition: 0
[    21.199]     RsvdMaskSize: 0
[    21.199]     RsvdFieldPosition: 0
[    21.199]     DirectColorModeInfo: 0
[    21.199]     PhysBasePtr: 0x0
[    21.199]     LinBytesPerScanLine: 0
[    21.199]     BnkNumberOfImagePages: 0
[    21.199]     LinNumberOfImagePages: 0
[    21.199]     LinRedMaskSize: 0
[    21.199]     LinRedFieldPosition: 0
[    21.199]     LinGreenMaskSize: 0
[    21.199]     LinGreenFieldPosition: 0
[    21.199]     LinBlueMaskSize: 0
[    21.199]     LinBlueFieldPosition: 0
[    21.199]     LinRsvdMaskSize: 0
[    21.199]     LinRsvdFieldPosition: 0
[    21.199]     MaxPixelClock: 0
[    21.199] Mode: 14d (0x0)
[    21.199]     ModeAttributes: 0x0
[    21.199]     WinAAttributes: 0x0
[    21.199]     WinBAttributes: 0x0
[    21.199]     WinGranularity: 0
[    21.199]     WinSize: 0
[    21.199]     WinASegment: 0x0
[    21.199]     WinBSegment: 0x0
[    21.199]     WinFuncPtr: 0x0
[    21.199]     BytesPerScanline: 0
[    21.199]     XResolution: 0
[    21.199]     YResolution: 0
[    21.199]     XCharSize: 0
[    21.199]     YCharSize: 0
[    21.199]     NumberOfPlanes: 0
[    21.199]     BitsPerPixel: 0
[    21.199]     NumberOfBanks: 0
[    21.199]     MemoryModel: 0
[    21.199]     BankSize: 0
[    21.199]     NumberOfImages: 0
[    21.199]     RedMaskSize: 0
[    21.199]     RedFieldPosition: 0
[    21.199]     GreenMaskSize: 0
[    21.199]     GreenFieldPosition: 0
[    21.199]     BlueMaskSize: 0
[    21.199]     BlueFieldPosition: 0
[    21.199]     RsvdMaskSize: 0
[    21.199]     RsvdFieldPosition: 0
[    21.199]     DirectColorModeInfo: 0
[    21.199]     PhysBasePtr: 0x0
[    21.199]     LinBytesPerScanLine: 0
[    21.199]     BnkNumberOfImagePages: 0
[    21.199]     LinNumberOfImagePages: 0
[    21.199]     LinRedMaskSize: 0
[    21.199]     LinRedFieldPosition: 0
[    21.199]     LinGreenMaskSize: 0
[    21.199]     LinGreenFieldPosition: 0
[    21.199]     LinBlueMaskSize: 0
[    21.199]     LinBlueFieldPosition: 0
[    21.199]     LinRsvdMaskSize: 0
[    21.199]     LinRsvdFieldPosition: 0
[    21.200]     MaxPixelClock: 0
[    21.200] Mode: 15c (0x0)
[    21.200]     ModeAttributes: 0x0
[    21.200]     WinAAttributes: 0x0
[    21.200]     WinBAttributes: 0x0
[    21.200]     WinGranularity: 0
[    21.200]     WinSize: 0
[    21.200]     WinASegment: 0x0
[    21.200]     WinBSegment: 0x0
[    21.200]     WinFuncPtr: 0x0
[    21.200]     BytesPerScanline: 0
[    21.200]     XResolution: 0
[    21.200]     YResolution: 0
[    21.200]     XCharSize: 0
[    21.200]     YCharSize: 0
[    21.200]     NumberOfPlanes: 0
[    21.200]     BitsPerPixel: 0
[    21.200]     NumberOfBanks: 0
[    21.200]     MemoryModel: 0
[    21.200]     BankSize: 0
[    21.200]     NumberOfImages: 0
[    21.200]     RedMaskSize: 0
[    21.200]     RedFieldPosition: 0
[    21.200]     GreenMaskSize: 0
[    21.200]     GreenFieldPosition: 0
[    21.200]     BlueMaskSize: 0
[    21.200]     BlueFieldPosition: 0
[    21.200]     RsvdMaskSize: 0
[    21.200]     RsvdFieldPosition: 0
[    21.200]     DirectColorModeInfo: 0
[    21.200]     PhysBasePtr: 0x0
[    21.200]     LinBytesPerScanLine: 0
[    21.200]     BnkNumberOfImagePages: 0
[    21.200]     LinNumberOfImagePages: 0
[    21.200]     LinRedMaskSize: 0
[    21.200]     LinRedFieldPosition: 0
[    21.200]     LinGreenMaskSize: 0
[    21.200]     LinGreenFieldPosition: 0
[    21.200]     LinBlueMaskSize: 0
[    21.200]     LinBlueFieldPosition: 0
[    21.200]     LinRsvdMaskSize: 0
[    21.200]     LinRsvdFieldPosition: 0
[    21.200]     MaxPixelClock: 0
[    21.200] Mode: 13a (0x0)
[    21.200]     ModeAttributes: 0x0
[    21.200]     WinAAttributes: 0x0
[    21.200]     WinBAttributes: 0x0
[    21.200]     WinGranularity: 0
[    21.200]     WinSize: 0
[    21.200]     WinASegment: 0x0
[    21.200]     WinBSegment: 0x0
[    21.200]     WinFuncPtr: 0x0
[    21.200]     BytesPerScanline: 0
[    21.200]     XResolution: 0
[    21.200]     YResolution: 0
[    21.200]     XCharSize: 0
[    21.200]     YCharSize: 0
[    21.200]     NumberOfPlanes: 0
[    21.200]     BitsPerPixel: 0
[    21.200]     NumberOfBanks: 0
[    21.200]     MemoryModel: 0
[    21.200]     BankSize: 0
[    21.201]     NumberOfImages: 0
[    21.201]     RedMaskSize: 0
[    21.201]     RedFieldPosition: 0
[    21.201]     GreenMaskSize: 0
[    21.201]     GreenFieldPosition: 0
[    21.201]     BlueMaskSize: 0
[    21.201]     BlueFieldPosition: 0
[    21.201]     RsvdMaskSize: 0
[    21.201]     RsvdFieldPosition: 0
[    21.201]     DirectColorModeInfo: 0
[    21.201]     PhysBasePtr: 0x0
[    21.201]     LinBytesPerScanLine: 0
[    21.201]     BnkNumberOfImagePages: 0
[    21.201]     LinNumberOfImagePages: 0
[    21.201]     LinRedMaskSize: 0
[    21.201]     LinRedFieldPosition: 0
[    21.201]     LinGreenMaskSize: 0
[    21.201]     LinGreenFieldPosition: 0
[    21.201]     LinBlueMaskSize: 0
[    21.201]     LinBlueFieldPosition: 0
[    21.201]     LinRsvdMaskSize: 0
[    21.201]     LinRsvdFieldPosition: 0
[    21.201]     MaxPixelClock: 0
[    21.201] Mode: 14b (0x0)
[    21.201]     ModeAttributes: 0x0
[    21.201]     WinAAttributes: 0x0
[    21.201]     WinBAttributes: 0x0
[    21.201]     WinGranularity: 0
[    21.201]     WinSize: 0
[    21.201]     WinASegment: 0x0
[    21.201]     WinBSegment: 0x0
[    21.201]     WinFuncPtr: 0x0
[    21.201]     BytesPerScanline: 0
[    21.201]     XResolution: 0
[    21.201]     YResolution: 0
[    21.201]     XCharSize: 0
[    21.201]     YCharSize: 0
[    21.201]     NumberOfPlanes: 0
[    21.201]     BitsPerPixel: 0
[    21.201]     NumberOfBanks: 0
[    21.201]     MemoryModel: 0
[    21.201]     BankSize: 0
[    21.201]     NumberOfImages: 0
[    21.201]     RedMaskSize: 0
[    21.201]     RedFieldPosition: 0
[    21.201]     GreenMaskSize: 0
[    21.201]     GreenFieldPosition: 0
[    21.201]     BlueMaskSize: 0
[    21.201]     BlueFieldPosition: 0
[    21.201]     RsvdMaskSize: 0
[    21.201]     RsvdFieldPosition: 0
[    21.201]     DirectColorModeInfo: 0
[    21.201]     PhysBasePtr: 0x0
[    21.201]     LinBytesPerScanLine: 0
[    21.201]     BnkNumberOfImagePages: 0
[    21.201]     LinNumberOfImagePages: 0
[    21.201]     LinRedMaskSize: 0
[    21.201]     LinRedFieldPosition: 0
[    21.201]     LinGreenMaskSize: 0
[    21.201]     LinGreenFieldPosition: 0
[    21.201]     LinBlueMaskSize: 0
[    21.201]     LinBlueFieldPosition: 0
[    21.201]     LinRsvdMaskSize: 0
[    21.201]     LinRsvdFieldPosition: 0
[    21.201]     MaxPixelClock: 0
[    21.202] Mode: 15a (0x0)
[    21.202]     ModeAttributes: 0x0
[    21.202]     WinAAttributes: 0x0
[    21.202]     WinBAttributes: 0x0
[    21.202]     WinGranularity: 0
[    21.202]     WinSize: 0
[    21.202]     WinASegment: 0x0
[    21.202]     WinBSegment: 0x0
[    21.202]     WinFuncPtr: 0x0
[    21.202]     BytesPerScanline: 0
[    21.202]     XResolution: 0
[    21.202]     YResolution: 0
[    21.202]     XCharSize: 0
[    21.202]     YCharSize: 0
[    21.202]     NumberOfPlanes: 0
[    21.202]     BitsPerPixel: 0
[    21.202]     NumberOfBanks: 0
[    21.202]     MemoryModel: 0
[    21.202]     BankSize: 0
[    21.202]     NumberOfImages: 0
[    21.202]     RedMaskSize: 0
[    21.202]     RedFieldPosition: 0
[    21.202]     GreenMaskSize: 0
[    21.202]     GreenFieldPosition: 0
[    21.202]     BlueMaskSize: 0
[    21.202]     BlueFieldPosition: 0
[    21.202]     RsvdMaskSize: 0
[    21.202]     RsvdFieldPosition: 0
[    21.202]     DirectColorModeInfo: 0
[    21.202]     PhysBasePtr: 0x0
[    21.202]     LinBytesPerScanLine: 0
[    21.202]     BnkNumberOfImagePages: 0
[    21.202]     LinNumberOfImagePages: 0
[    21.202]     LinRedMaskSize: 0
[    21.202]     LinRedFieldPosition: 0
[    21.202]     LinGreenMaskSize: 0
[    21.202]     LinGreenFieldPosition: 0
[    21.202]     LinBlueMaskSize: 0
[    21.202]     LinBlueFieldPosition: 0
[    21.202]     LinRsvdMaskSize: 0
[    21.202]     LinRsvdFieldPosition: 0
[    21.202]     MaxPixelClock: 0
[    21.202] Mode: 107 (0x0)
[    21.202]     ModeAttributes: 0x0
[    21.202]     WinAAttributes: 0x0
[    21.202]     WinBAttributes: 0x0
[    21.202]     WinGranularity: 0
[    21.202]     WinSize: 0
[    21.202]     WinASegment: 0x0
[    21.202]     WinBSegment: 0x0
[    21.202]     WinFuncPtr: 0x0
[    21.202]     BytesPerScanline: 0
[    21.202]     XResolution: 0
[    21.202]     YResolution: 0
[    21.202]     XCharSize: 0
[    21.202]     YCharSize: 0
[    21.202]     NumberOfPlanes: 0
[    21.202]     BitsPerPixel: 0
[    21.202]     NumberOfBanks: 0
[    21.202]     MemoryModel: 0
[    21.202]     BankSize: 0
[    21.202]     NumberOfImages: 0
[    21.202]     RedMaskSize: 0
[    21.202]     RedFieldPosition: 0
[    21.202]     GreenMaskSize: 0
[    21.202]     GreenFieldPosition: 0
[    21.202]     BlueMaskSize: 0
[    21.202]     BlueFieldPosition: 0
[    21.202]     RsvdMaskSize: 0
[    21.202]     RsvdFieldPosition: 0
[    21.202]     DirectColorModeInfo: 0
[    21.202]     PhysBasePtr: 0x0
[    21.202]     LinBytesPerScanLine: 0
[    21.202]     BnkNumberOfImagePages: 0
[    21.202]     LinNumberOfImagePages: 0
[    21.202]     LinRedMaskSize: 0
[    21.202]     LinRedFieldPosition: 0
[    21.202]     LinGreenMaskSize: 0
[    21.202]     LinGreenFieldPosition: 0
[    21.202]     LinBlueMaskSize: 0
[    21.202]     LinBlueFieldPosition: 0
[    21.202]     LinRsvdMaskSize: 0
[    21.202]     LinRsvdFieldPosition: 0
[    21.202]     MaxPixelClock: 0
[    21.203] Mode: 11a (0x0)
[    21.203]     ModeAttributes: 0x0
[    21.203]     WinAAttributes: 0x0
[    21.203]     WinBAttributes: 0x0
[    21.203]     WinGranularity: 0
[    21.203]     WinSize: 0
[    21.203]     WinASegment: 0x0
[    21.203]     WinBSegment: 0x0
[    21.203]     WinFuncPtr: 0x0
[    21.203]     BytesPerScanline: 0
[    21.203]     XResolution: 0
[    21.203]     YResolution: 0
[    21.203]     XCharSize: 0
[    21.203]     YCharSize: 0
[    21.203]     NumberOfPlanes: 0
[    21.203]     BitsPerPixel: 0
[    21.203]     NumberOfBanks: 0
[    21.203]     MemoryModel: 0
[    21.203]     BankSize: 0
[    21.203]     NumberOfImages: 0
[    21.203]     RedMaskSize: 0
[    21.203]     RedFieldPosition: 0
[    21.203]     GreenMaskSize: 0
[    21.203]     GreenFieldPosition: 0
[    21.203]     BlueMaskSize: 0
[    21.203]     BlueFieldPosition: 0
[    21.203]     RsvdMaskSize: 0
[    21.203]     RsvdFieldPosition: 0
[    21.203]     DirectColorModeInfo: 0
[    21.203]     PhysBasePtr: 0x0
[    21.203]     LinBytesPerScanLine: 0
[    21.203]     BnkNumberOfImagePages: 0
[    21.203]     LinNumberOfImagePages: 0
[    21.203]     LinRedMaskSize: 0
[    21.203]     LinRedFieldPosition: 0
[    21.203]     LinGreenMaskSize: 0
[    21.203]     LinGreenFieldPosition: 0
[    21.203]     LinBlueMaskSize: 0
[    21.203]     LinBlueFieldPosition: 0
[    21.203]     LinRsvdMaskSize: 0
[    21.203]     LinRsvdFieldPosition: 0
[    21.203]     MaxPixelClock: 0
[    21.203] Mode: 11b (0x0)
[    21.203]     ModeAttributes: 0x0
[    21.203]     WinAAttributes: 0x0
[    21.203]     WinBAttributes: 0x0
[    21.203]     WinGranularity: 0
[    21.203]     WinSize: 0
[    21.203]     WinASegment: 0x0
[    21.203]     WinBSegment: 0x0
[    21.203]     WinFuncPtr: 0x0
[    21.203]     BytesPerScanline: 0
[    21.203]     XResolution: 0
[    21.203]     YResolution: 0
[    21.203]     XCharSize: 0
[    21.203]     YCharSize: 0
[    21.203]     NumberOfPlanes: 0
[    21.203]     BitsPerPixel: 0
[    21.203]     NumberOfBanks: 0
[    21.203]     MemoryModel: 0
[    21.203]     BankSize: 0
[    21.203]     NumberOfImages: 0
[    21.203]     RedMaskSize: 0
[    21.203]     RedFieldPosition: 0
[    21.203]     GreenMaskSize: 0
[    21.203]     GreenFieldPosition: 0
[    21.203]     BlueMaskSize: 0
[    21.203]     BlueFieldPosition: 0
[    21.203]     RsvdMaskSize: 0
[    21.203]     RsvdFieldPosition: 0
[    21.203]     DirectColorModeInfo: 0
[    21.203]     PhysBasePtr: 0x0
[    21.203]     LinBytesPerScanLine: 0
[    21.203]     BnkNumberOfImagePages: 0
[    21.203]     LinNumberOfImagePages: 0
[    21.203]     LinRedMaskSize: 0
[    21.203]     LinRedFieldPosition: 0
[    21.203]     LinGreenMaskSize: 0
[    21.203]     LinGreenFieldPosition: 0
[    21.203]     LinBlueMaskSize: 0
[    21.203]     LinBlueFieldPosition: 0
[    21.203]     LinRsvdMaskSize: 0
[    21.203]     LinRsvdFieldPosition: 0
[    21.204]     MaxPixelClock: 0
[    21.204] Mode: 105 (1024x768)
[    21.204]     ModeAttributes: 0x9b
[    21.204]     WinAAttributes: 0x7
[    21.204]     WinBAttributes: 0x0
[    21.204]     WinGranularity: 64
[    21.204]     WinSize: 64
[    21.204]     WinASegment: 0xa000
[    21.204]     WinBSegment: 0x0
[    21.204]     WinFuncPtr: 0xc00083ea
[    21.204]     BytesPerScanline: 1024
[    21.204]     XResolution: 1024
[    21.204]     YResolution: 768
[    21.204]     XCharSize: 8
[    21.204]     YCharSize: 16
[    21.204]     NumberOfPlanes: 1
[    21.204]     BitsPerPixel: 8
[    21.204]     NumberOfBanks: 1
[    21.204]     MemoryModel: 4
[    21.204]     BankSize: 0
[    21.204]     NumberOfImages: 84
[    21.204]     RedMaskSize: 0
[    21.204]     RedFieldPosition: 0
[    21.204]     GreenMaskSize: 0
[    21.204]     GreenFieldPosition: 0
[    21.204]     BlueMaskSize: 0
[    21.204]     BlueFieldPosition: 0
[    21.204]     RsvdMaskSize: 0
[    21.204]     RsvdFieldPosition: 0
[    21.204]     DirectColorModeInfo: 0
[    21.204]     PhysBasePtr: 0x40000000
[    21.204]     LinBytesPerScanLine: 1024
[    21.204]     BnkNumberOfImagePages: 84
[    21.204]     LinNumberOfImagePages: 84
[    21.204]     LinRedMaskSize: 0
[    21.204]     LinRedFieldPosition: 0
[    21.204]     LinGreenMaskSize: 0
[    21.204]     LinGreenFieldPosition: 0
[    21.204]     LinBlueMaskSize: 0
[    21.204]     LinBlueFieldPosition: 0
[    21.204]     LinRsvdMaskSize: 0
[    21.204]     LinRsvdFieldPosition: 0
[    21.204]     MaxPixelClock: 230000000
[    21.205] Mode: 117 (1024x768)
[    21.205]     ModeAttributes: 0x9b
[    21.205]     WinAAttributes: 0x7
[    21.205]     WinBAttributes: 0x0
[    21.205]     WinGranularity: 64
[    21.205]     WinSize: 64
[    21.205]     WinASegment: 0xa000
[    21.205]     WinBSegment: 0x0
[    21.205]     WinFuncPtr: 0xc00083ea
[    21.205]     BytesPerScanline: 2048
[    21.205]     XResolution: 1024
[    21.205]     YResolution: 768
[    21.205]     XCharSize: 8
[    21.205]     YCharSize: 16
[    21.205]     NumberOfPlanes: 1
[    21.205]     BitsPerPixel: 16
[    21.205]     NumberOfBanks: 1
[    21.205]     MemoryModel: 6
[    21.205]     BankSize: 0
[    21.205]     NumberOfImages: 41
[    21.205]     RedMaskSize: 5
[    21.205]     RedFieldPosition: 11
[    21.205]     GreenMaskSize: 6
[    21.205]     GreenFieldPosition: 5
[    21.205]     BlueMaskSize: 5
[    21.205]     BlueFieldPosition: 0
[    21.205]     RsvdMaskSize: 0
[    21.205]     RsvdFieldPosition: 0
[    21.205]     DirectColorModeInfo: 0
[    21.205]     PhysBasePtr: 0x40000000
[    21.205]     LinBytesPerScanLine: 2048
[    21.205]     BnkNumberOfImagePages: 41
[    21.205]     LinNumberOfImagePages: 41
[    21.205]     LinRedMaskSize: 5
[    21.205]     LinRedFieldPosition: 11
[    21.205]     LinGreenMaskSize: 6
[    21.205]     LinGreenFieldPosition: 5
[    21.205]     LinBlueMaskSize: 5
[    21.205]     LinBlueFieldPosition: 0
[    21.205]     LinRsvdMaskSize: 0
[    21.205]     LinRsvdFieldPosition: 0
[    21.205]     MaxPixelClock: 230000000
[    21.206] *Mode: 118 (1024x768)
[    21.206]     ModeAttributes: 0x9b
[    21.206]     WinAAttributes: 0x7
[    21.206]     WinBAttributes: 0x0
[    21.206]     WinGranularity: 64
[    21.206]     WinSize: 64
[    21.206]     WinASegment: 0xa000
[    21.206]     WinBSegment: 0x0
[    21.206]     WinFuncPtr: 0xc00083ea
[    21.206]     BytesPerScanline: 4096
[    21.206]     XResolution: 1024
[    21.206]     YResolution: 768
[    21.206]     XCharSize: 8
[    21.206]     YCharSize: 16
[    21.206]     NumberOfPlanes: 1
[    21.206]     BitsPerPixel: 32
[    21.206]     NumberOfBanks: 1
[    21.206]     MemoryModel: 6
[    21.206]     BankSize: 0
[    21.206]     NumberOfImages: 20
[    21.206]     RedMaskSize: 8
[    21.206]     RedFieldPosition: 16
[    21.206]     GreenMaskSize: 8
[    21.206]     GreenFieldPosition: 8
[    21.206]     BlueMaskSize: 8
[    21.206]     BlueFieldPosition: 0
[    21.206]     RsvdMaskSize: 8
[    21.206]     RsvdFieldPosition: 24
[    21.206]     DirectColorModeInfo: 0
[    21.206]     PhysBasePtr: 0x40000000
[    21.206]     LinBytesPerScanLine: 4096
[    21.206]     BnkNumberOfImagePages: 20
[    21.206]     LinNumberOfImagePages: 20
[    21.206]     LinRedMaskSize: 8
[    21.206]     LinRedFieldPosition: 16
[    21.206]     LinGreenMaskSize: 8
[    21.206]     LinGreenFieldPosition: 8
[    21.206]     LinBlueMaskSize: 8
[    21.206]     LinBlueFieldPosition: 0
[    21.206]     LinRsvdMaskSize: 8
[    21.206]     LinRsvdFieldPosition: 24
[    21.206]     MaxPixelClock: 230000000
[    21.207] *Mode: 112 (640x480)
[    21.207]     ModeAttributes: 0x9b
[    21.207]     WinAAttributes: 0x7
[    21.207]     WinBAttributes: 0x0
[    21.207]     WinGranularity: 64
[    21.207]     WinSize: 64
[    21.207]     WinASegment: 0xa000
[    21.207]     WinBSegment: 0x0
[    21.207]     WinFuncPtr: 0xc00083ea
[    21.207]     BytesPerScanline: 2560
[    21.207]     XResolution: 640
[    21.207]     YResolution: 480
[    21.207]     XCharSize: 8
[    21.207]     YCharSize: 16
[    21.207]     NumberOfPlanes: 1
[    21.207]     BitsPerPixel: 32
[    21.207]     NumberOfBanks: 1
[    21.207]     MemoryModel: 6
[    21.207]     BankSize: 0
[    21.207]     NumberOfImages: 52
[    21.207]     RedMaskSize: 8
[    21.207]     RedFieldPosition: 16
[    21.207]     GreenMaskSize: 8
[    21.207]     GreenFieldPosition: 8
[    21.207]     BlueMaskSize: 8
[    21.207]     BlueFieldPosition: 0
[    21.207]     RsvdMaskSize: 8
[    21.207]     RsvdFieldPosition: 24
[    21.207]     DirectColorModeInfo: 0
[    21.207]     PhysBasePtr: 0x40000000
[    21.207]     LinBytesPerScanLine: 2560
[    21.207]     BnkNumberOfImagePages: 52
[    21.207]     LinNumberOfImagePages: 52
[    21.207]     LinRedMaskSize: 8
[    21.207]     LinRedFieldPosition: 16
[    21.207]     LinGreenMaskSize: 8
[    21.207]     LinGreenFieldPosition: 8
[    21.207]     LinBlueMaskSize: 8
[    21.207]     LinBlueFieldPosition: 0
[    21.207]     LinRsvdMaskSize: 8
[    21.207]     LinRsvdFieldPosition: 24
[    21.207]     MaxPixelClock: 230000000
[    21.207] Mode: 114 (800x600)
[    21.207]     ModeAttributes: 0x9b
[    21.207]     WinAAttributes: 0x7
[    21.207]     WinBAttributes: 0x0
[    21.207]     WinGranularity: 64
[    21.207]     WinSize: 64
[    21.207]     WinASegment: 0xa000
[    21.207]     WinBSegment: 0x0
[    21.207]     WinFuncPtr: 0xc00083ea
[    21.207]     BytesPerScanline: 1600
[    21.207]     XResolution: 800
[    21.207]     YResolution: 600
[    21.207]     XCharSize: 8
[    21.207]     YCharSize: 16
[    21.207]     NumberOfPlanes: 1
[    21.207]     BitsPerPixel: 16
[    21.207]     NumberOfBanks: 1
[    21.207]     MemoryModel: 6
[    21.207]     BankSize: 0
[    21.207]     NumberOfImages: 67
[    21.207]     RedMaskSize: 5
[    21.207]     RedFieldPosition: 11
[    21.207]     GreenMaskSize: 6
[    21.207]     GreenFieldPosition: 5
[    21.208]     BlueMaskSize: 5
[    21.208]     BlueFieldPosition: 0
[    21.208]     RsvdMaskSize: 0
[    21.208]     RsvdFieldPosition: 0
[    21.208]     DirectColorModeInfo: 0
[    21.208]     PhysBasePtr: 0x40000000
[    21.208]     LinBytesPerScanLine: 1600
[    21.208]     BnkNumberOfImagePages: 67
[    21.208]     LinNumberOfImagePages: 67
[    21.208]     LinRedMaskSize: 5
[    21.208]     LinRedFieldPosition: 11
[    21.208]     LinGreenMaskSize: 6
[    21.208]     LinGreenFieldPosition: 5
[    21.208]     LinBlueMaskSize: 5
[    21.208]     LinBlueFieldPosition: 0
[    21.208]     LinRsvdMaskSize: 0
[    21.208]     LinRsvdFieldPosition: 0
[    21.208]     MaxPixelClock: 230000000
[    21.208] *Mode: 115 (800x600)
[    21.208]     ModeAttributes: 0x9b
[    21.208]     WinAAttributes: 0x7
[    21.208]     WinBAttributes: 0x0
[    21.208]     WinGranularity: 64
[    21.208]     WinSize: 64
[    21.208]     WinASegment: 0xa000
[    21.208]     WinBSegment: 0x0
[    21.208]     WinFuncPtr: 0xc00083ea
[    21.208]     BytesPerScanline: 3200
[    21.208]     XResolution: 800
[    21.208]     YResolution: 600
[    21.208]     XCharSize: 8
[    21.208]     YCharSize: 16
[    21.208]     NumberOfPlanes: 1
[    21.208]     BitsPerPixel: 32
[    21.208]     NumberOfBanks: 1
[    21.208]     MemoryModel: 6
[    21.208]     BankSize: 0
[    21.208]     NumberOfImages: 33
[    21.208]     RedMaskSize: 8
[    21.208]     RedFieldPosition: 16
[    21.208]     GreenMaskSize: 8
[    21.208]     GreenFieldPosition: 8
[    21.208]     BlueMaskSize: 8
[    21.208]     BlueFieldPosition: 0
[    21.208]     RsvdMaskSize: 8
[    21.208]     RsvdFieldPosition: 24
[    21.208]     DirectColorModeInfo: 0
[    21.208]     PhysBasePtr: 0x40000000
[    21.208]     LinBytesPerScanLine: 3200
[    21.208]     BnkNumberOfImagePages: 33
[    21.208]     LinNumberOfImagePages: 33
[    21.208]     LinRedMaskSize: 8
[    21.208]     LinRedFieldPosition: 16
[    21.208]     LinGreenMaskSize: 8
[    21.208]     LinGreenFieldPosition: 8
[    21.208]     LinBlueMaskSize: 8
[    21.209]     LinBlueFieldPosition: 0
[    21.209]     LinRsvdMaskSize: 8
[    21.209]     LinRsvdFieldPosition: 24
[    21.209]     MaxPixelClock: 230000000
[    21.209] Mode: 101 (640x480)
[    21.209]     ModeAttributes: 0x9b
[    21.209]     WinAAttributes: 0x7
[    21.209]     WinBAttributes: 0x0
[    21.209]     WinGranularity: 64
[    21.209]     WinSize: 64
[    21.209]     WinASegment: 0xa000
[    21.209]     WinBSegment: 0x0
[    21.209]     WinFuncPtr: 0xc00083ea
[    21.209]     BytesPerScanline: 640
[    21.209]     XResolution: 640
[    21.209]     YResolution: 480
[    21.209]     XCharSize: 8
[    21.209]     YCharSize: 16
[    21.209]     NumberOfPlanes: 1
[    21.209]     BitsPerPixel: 8
[    21.209]     NumberOfBanks: 1
[    21.209]     MemoryModel: 4
[    21.209]     BankSize: 0
[    21.209]     NumberOfImages: 203
[    21.209]     RedMaskSize: 0
[    21.209]     RedFieldPosition: 0
[    21.209]     GreenMaskSize: 0
[    21.209]     GreenFieldPosition: 0
[    21.209]     BlueMaskSize: 0
[    21.209]     BlueFieldPosition: 0
[    21.209]     RsvdMaskSize: 0
[    21.209]     RsvdFieldPosition: 0
[    21.209]     DirectColorModeInfo: 0
[    21.209]     PhysBasePtr: 0x40000000
[    21.209]     LinBytesPerScanLine: 640
[    21.209]     BnkNumberOfImagePages: 203
[    21.209]     LinNumberOfImagePages: 203
[    21.209]     LinRedMaskSize: 0
[    21.209]     LinRedFieldPosition: 0
[    21.209]     LinGreenMaskSize: 0
[    21.209]     LinGreenFieldPosition: 0
[    21.209]     LinBlueMaskSize: 0
[    21.209]     LinBlueFieldPosition: 0
[    21.209]     LinRsvdMaskSize: 0
[    21.209]     LinRsvdFieldPosition: 0
[    21.209]     MaxPixelClock: 230000000
[    21.210] Mode: 103 (800x600)
[    21.210]     ModeAttributes: 0x9b
[    21.210]     WinAAttributes: 0x7
[    21.210]     WinBAttributes: 0x0
[    21.210]     WinGranularity: 64
[    21.210]     WinSize: 64
[    21.210]     WinASegment: 0xa000
[    21.210]     WinBSegment: 0x0
[    21.210]     WinFuncPtr: 0xc00083ea
[    21.210]     BytesPerScanline: 832
[    21.210]     XResolution: 800
[    21.210]     YResolution: 600
[    21.210]     XCharSize: 8
[    21.210]     YCharSize: 16
[    21.210]     NumberOfPlanes: 1
[    21.210]     BitsPerPixel: 8
[    21.210]     NumberOfBanks: 1
[    21.210]     MemoryModel: 4
[    21.210]     BankSize: 0
[    21.210]     NumberOfImages: 126
[    21.210]     RedMaskSize: 0
[    21.210]     RedFieldPosition: 0
[    21.210]     GreenMaskSize: 0
[    21.210]     GreenFieldPosition: 0
[    21.210]     BlueMaskSize: 0
[    21.210]     BlueFieldPosition: 0
[    21.210]     RsvdMaskSize: 0
[    21.210]     RsvdFieldPosition: 0
[    21.210]     DirectColorModeInfo: 0
[    21.210]     PhysBasePtr: 0x40000000
[    21.210]     LinBytesPerScanLine: 832
[    21.210]     BnkNumberOfImagePages: 126
[    21.210]     LinNumberOfImagePages: 126
[    21.210]     LinRedMaskSize: 0
[    21.210]     LinRedFieldPosition: 0
[    21.210]     LinGreenMaskSize: 0
[    21.210]     LinGreenFieldPosition: 0
[    21.210]     LinBlueMaskSize: 0
[    21.210]     LinBlueFieldPosition: 0
[    21.210]     LinRsvdMaskSize: 0
[    21.210]     LinRsvdFieldPosition: 0
[    21.210]     MaxPixelClock: 230000000
[    21.210] Mode: 111 (640x480)
[    21.210]     ModeAttributes: 0x9b
[    21.210]     WinAAttributes: 0x7
[    21.210]     WinBAttributes: 0x0
[    21.210]     WinGranularity: 64
[    21.210]     WinSize: 64
[    21.210]     WinASegment: 0xa000
[    21.210]     WinBSegment: 0x0
[    21.210]     WinFuncPtr: 0xc00083ea
[    21.210]     BytesPerScanline: 1280
[    21.210]     XResolution: 640
[    21.210]     YResolution: 480
[    21.210]     XCharSize: 8
[    21.210]     YCharSize: 16
[    21.211]     NumberOfPlanes: 1
[    21.211]     BitsPerPixel: 16
[    21.211]     NumberOfBanks: 1
[    21.211]     MemoryModel: 6
[    21.211]     BankSize: 0
[    21.211]     NumberOfImages: 101
[    21.211]     RedMaskSize: 5
[    21.211]     RedFieldPosition: 11
[    21.211]     GreenMaskSize: 6
[    21.211]     GreenFieldPosition: 5
[    21.211]     BlueMaskSize: 5
[    21.211]     BlueFieldPosition: 0
[    21.211]     RsvdMaskSize: 0
[    21.211]     RsvdFieldPosition: 0
[    21.211]     DirectColorModeInfo: 0
[    21.211]     PhysBasePtr: 0x40000000
[    21.211]     LinBytesPerScanLine: 1280
[    21.211]     BnkNumberOfImagePages: 101
[    21.211]     LinNumberOfImagePages: 101
[    21.211]     LinRedMaskSize: 5
[    21.211]     LinRedFieldPosition: 11
[    21.211]     LinGreenMaskSize: 6
[    21.211]     LinGreenFieldPosition: 5
[    21.211]     LinBlueMaskSize: 5
[    21.211]     LinBlueFieldPosition: 0
[    21.211]     LinRsvdMaskSize: 0
[    21.211]     LinRsvdFieldPosition: 0
[    21.211]     MaxPixelClock: 230000000
[    21.211] 
[    21.211] (II) VESA(0): Total Memory: 1023 64KB banks (65472kB)
[    21.211] (II) VESA(0): <default monitor>: Using hsync value of 47.38 kHz
[    21.211] (II) VESA(0): <default monitor>: Using vrefresh value of 59.97 Hz
[    21.211] (WW) VESA(0): Unable to estimate virtual size
[    21.211] (II) VESA(0): Not using built-in mode "1024x768" (no mode of this name)
[    21.211] (II) VESA(0): Not using built-in mode "800x600" (no mode of this name)
[    21.211] (II) VESA(0): Not using built-in mode "640x480" (no mode of this name)
[    21.211] (WW) VESA(0): No valid modes left. Trying less strict filter...
[    21.211] (II) VESA(0): <default monitor>: Using hsync value of 47.38 kHz
[    21.211] (II) VESA(0): <default monitor>: Using vrefresh value of 59.97 Hz
[    21.211] (WW) VESA(0): Unable to estimate virtual size
[    21.211] (II) VESA(0): Not using built-in mode "800x600" (hsync out of range)
[    21.211] (II) VESA(0): Not using built-in mode "640x480" (hsync out of range)
[    21.211] (--) VESA(0): Virtual size is 1024x768 (pitch 1024)
[    21.211] (**) VESA(0): *Built-in mode "1024x768"
[    21.211] (**) VESA(0): Display dimensions: (340, 190) mm
[    21.211] (**) VESA(0): DPI set to (76, 102)
[    21.211] (**) VESA(0): Using "Shadow Framebuffer"
[    21.211] (II) Loading sub module "shadow"
[    21.211] (II) LoadModule: "shadow"
[    21.211] (II) Loading /usr/lib/xorg/modules/libshadow.so
[    21.211] (II) Module shadow: vendor="X.Org Foundation"
[    21.211]     compiled for 1.10.1, module version = 1.1.0
[    21.212]     ABI class: X.Org ANSI C Emulation, version 0.4
[    21.212] (II) Loading sub module "fb"
[    21.212] (II) LoadModule: "fb"
[    21.212] (II) Loading /usr/lib/xorg/modules/libfb.so
[    21.212] (II) Module fb: vendor="X.Org Foundation"
[    21.212]     compiled for 1.10.1, module version = 1.0.0
[    21.212]     ABI class: X.Org ANSI C Emulation, version 0.4
[    21.212] (II) UnloadModule: "fbdev"
[    21.212] (II) Unloading fbdev
[    21.212] (II) UnloadModule: "fbdevhw"
[    21.212] (II) Unloading fbdevhw
[    21.212] (==) Depth 24 pixmap format is 32 bpp
[    21.212] (II) Loading sub module "int10"
[    21.212] (II) LoadModule: "int10"
[    21.212] (II) Loading /usr/lib/xorg/modules/libint10.so
[    21.212] (II) Module int10: vendor="X.Org Foundation"
[    21.212]     compiled for 1.10.1, module version = 1.0.0
[    21.212]     ABI class: X.Org Video Driver, version 10.0
[    21.212] (II) VESA(0): initializing int10
[    21.212] (II) VESA(0): Bad V_BIOS checksum
[    21.212] (II) VESA(0): Primary V_BIOS segment is: 0xc000
[    21.213] (II) VESA(0): VESA BIOS detected
[    21.213] (II) VESA(0): VESA VBE Version 3.0
[    21.213] (II) VESA(0): VESA VBE Total Mem: 65472 kB
[    21.213] (II) VESA(0): VESA VBE OEM: Intel(r)Cantiga Graphics Chip Accelerated VGA BIOS
[    21.213] (II) VESA(0): VESA VBE OEM Software Rev: 1.0
[    21.213] (II) VESA(0): VESA VBE OEM Vendor: Intel Corporation
[    21.213] (II) VESA(0): VESA VBE OEM Product: Intel(r)Cantiga Graphics Controller
[    21.213] (II) VESA(0): VESA VBE OEM Product Rev: Hardware Version 0.0
[    21.224] (II) VESA(0): virtual address = 0xb3667000,
    physical address = 0x40000000, size = 67043328
[    21.231] (II) VESA(0): Setting up VESA Mode 0x118 (1024x768)
[    21.280] (==) VESA(0): Default visual is TrueColor
[    21.281] (==) VESA(0): Backing store disabled
[    21.281] (==) VESA(0): DPMS enabled
[    21.281] (==) RandR enabled
[    21.281] (II) Initializing built-in extension Generic Event Extension
[    21.281] (II) Initializing built-in extension SHAPE
[    21.281] (II) Initializing built-in extension MIT-SHM
[    21.281] (II) Initializing built-in extension XInputExtension
[    21.281] (II) Initializing built-in extension XTEST
[    21.281] (II) Initializing built-in extension BIG-REQUESTS
[    21.281] (II) Initializing built-in extension SYNC
[    21.281] (II) Initializing built-in extension XKEYBOARD
[    21.281] (II) Initializing built-in extension XC-MISC
[    21.281] (II) Initializing built-in extension SECURITY
[    21.281] (II) Initializing built-in extension XINERAMA
[    21.281] (II) Initializing built-in extension XFIXES
[    21.281] (II) Initializing built-in extension RENDER
[    21.281] (II) Initializing built-in extension RANDR
[    21.281] (II) Initializing built-in extension COMPOSITE
[    21.281] (II) Initializing built-in extension DAMAGE
[    21.281] (II) Initializing built-in extension GESTURE
[    21.292] (II) AIGLX: Screen 0 is not DRI2 capable
[    21.292] (II) AIGLX: Screen 0 is not DRI capable
[    21.292] (II) AIGLX: Trying DRI driver /usr/lib/dri/swrast_dri.so
[    21.355] (II) AIGLX: Loaded and initialized swrast
[    21.360] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[    21.376] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    21.386] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[    21.386] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    21.386] (II) LoadModule: "evdev"
[    21.386] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    21.387] (II) Module evdev: vendor="X.Org Foundation"
[    21.387]     compiled for 1.10.0.902, module version = 2.6.0
[    21.387]     Module class: X.Org XInput Driver
[    21.387]     ABI class: X.Org XInput driver, version 12.3
[    21.387] (II) Using input driver 'evdev' for 'Power Button'
[    21.387] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    21.387] (**) Power Button: always reports core events
[    21.387] (**) Power Button: Device: "/dev/input/event3"
[    21.387] (--) Power Button: Found keys
[    21.387] (II) Power Button: Configuring as keyboard
[    21.387] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3/event3"
[    21.387] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    21.387] (**) Option "xkb_rules" "evdev"
[    21.387] (**) Option "xkb_model" "pc105"
[    21.387] (**) Option "xkb_layout" "gb"
[    21.390] (II) XKB: reuse xkmfile /var/lib/xkb/server-2B4266AA55228AE7D9557A18F1965DBA19850816.xkm
[    21.391] (II) config/udev: Adding input device Video Bus (/dev/input/event6)
[    21.391] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    21.391] (II) Using input driver 'evdev' for 'Video Bus'
[    21.391] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    21.391] (**) Video Bus: always reports core events
[    21.391] (**) Video Bus: Device: "/dev/input/event6"
[    21.391] (--) Video Bus: Found keys
[    21.391] (II) Video Bus: Configuring as keyboard
[    21.391] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:01/input/input6/event6"
[    21.391] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[    21.391] (**) Option "xkb_rules" "evdev"
[    21.391] (**) Option "xkb_model" "pc105"
[    21.391] (**) Option "xkb_layout" "gb"
[    21.992] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    21.992] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    21.992] (II) Using input driver 'evdev' for 'Power Button'
[    21.992] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    21.992] (**) Power Button: always reports core events
[    21.992] (**) Power Button: Device: "/dev/input/event0"
[    21.992] (--) Power Button: Found keys
[    21.992] (II) Power Button: Configuring as keyboard
[    21.992] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:0c/PNP0C0C:00/input/input0/event0"
[    21.992] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    21.992] (**) Option "xkb_rules" "evdev"
[    21.992] (**) Option "xkb_model" "pc105"
[    21.992] (**) Option "xkb_layout" "gb"
[    21.993] (II) config/udev: Adding input device Lid Switch (/dev/input/event1)
[    21.993] (II) No input driver/identifier specified (ignoring)
[    21.993] (II) config/udev: Adding input device Sleep Button (/dev/input/event2)
[    21.993] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    21.993] (II) Using input driver 'evdev' for 'Sleep Button'
[    21.993] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    21.993] (**) Sleep Button: always reports core events
[    21.993] (**) Sleep Button: Device: "/dev/input/event2"
[    21.993] (--) Sleep Button: Found keys
[    21.993] (II) Sleep Button: Configuring as keyboard
[    21.993] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:0c/PNP0C0E:00/input/input2/event2"
[    21.993] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[    21.993] (**) Option "xkb_rules" "evdev"
[    21.994] (**) Option "xkb_model" "pc105"
[    21.994] (**) Option "xkb_layout" "gb"
[    21.998] (II) config/udev: Adding input device HDA Intel Headphone (/dev/input/event5)
[    21.998] (II) No input driver/identifier specified (ignoring)
[    22.004] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[    22.004] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    22.004] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    22.004] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    22.004] (**) AT Translated Set 2 keyboard: always reports core events
[    22.004] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event4"
[    22.004] (--) AT Translated Set 2 keyboard: Found keys
[    22.004] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    22.004] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input4/event4"
[    22.004] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    22.004] (**) Option "xkb_rules" "evdev"
[    22.004] (**) Option "xkb_model" "pc105"
[    22.004] (**) Option "xkb_layout" "gb"
[    22.005] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event7)
[    22.005] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    22.005] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    22.005] (II) LoadModule: "synaptics"
[    22.005] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    22.005] (II) Module synaptics: vendor="X.Org Foundation"
[    22.005]     compiled for 1.10.1, module version = 1.3.99
[    22.005]     Module class: X.Org XInput Driver
[    22.005]     ABI class: X.Org XInput driver, version 12.3
[    22.005] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[    22.005] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    22.005] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    22.005] (**) Option "Device" "/dev/input/event7"
[    22.005] (--) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5772
[    22.005] (--) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 5086
[    22.005] (--) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    22.005] (--) SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[    22.005] (--) SynPS/2 Synaptics TouchPad: buttons: left right
[    22.005] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    22.005] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    22.005] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input7/event7"
[    22.005] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
[    22.005] (**) SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[    22.005] (**) SynPS/2 Synaptics TouchPad: MaxSpeed is now 1.75
[    22.005] (**) SynPS/2 Synaptics TouchPad: AccelFactor is now 0.035
[    22.005] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    22.005] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[    22.005] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    22.005] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    22.006] (II) SynPS/2 Synaptics TouchPad: failed to open grail, no gesture support
[    22.006] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    22.006] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[    22.006] (II) No input driver/identifier specified (ignoring)

---

### Post by BicyclerBoy on 2011-09-18
That log file shows vesa driver taking over..this will limit the resolution to 1024x768 because the driver can not determine the virtual size..

This laptop is using Integrated Intel GMA 4500MHD Cantiga, also known as "Intel Mobile 4 Series".
This chipset graphics can work well with linux but there are lots of reports of problems over the last year. Some of the problems are similar to yours..

It may be easier to get the vesa driver to accept your video mode.
Do you need h/w video decode & OpenGL performance or ?

We need to get the Xorg.0.log file with the intel driver loaded (nomodeset removed).
One trick you could try is to use a console login to access the /var/log/Xorg.0.log.

1.  edit grub to remove nomodeset
2. reboot to blank X server screen vt7
3. <ctrl> + <alt> + <f1>  into vt1
4. login with normal user & password
5. copy /var/log/Xorg.0.log to some temp file in ~/  (home)
6. dmesg > ~/loginfo.txt

7. fix grub by some means to get back to vesa.

Post the log files from above

---

### Post by TrebleClef on 2011-09-18
When I reboot and press <ctrl> + <alt> + <f1>, my screen just goes blank.
I can't do anything apart from restart.

---

### Post by anewguy on 2011-09-19
Yep - that's why you need nomodeset on the boot line.  It's a catch-22 for some.  The thing is, you can edit the xorg.conf.new file that is in your home folder (was created in the X -configure), add modelines for your resolution, which may also require specifying clock rates, and you should at least get the resolution you want.  You may not be able to do some of the eye candy, etc., with just the vesa driver, but you can play with xorg.conf to get things as best as possible.

Once you've updated that file:

sudo cp xorg.conf.new /etc/X11/xorg.conf

This will place the file with the correct name in the folder it needs to be in.

Try rebooting and see what happens.  If just a terminal log in comes up, log in and do:

sudo rm /etc/X11/xorg.conf

then reboot.


Dave ;)

---

### Post by BicyclerBoy on 2011-09-19
One view of it:
Your chipset graphics got forgotten about in the rush/panic to support GMA HD (core) & then sandybridge HD 2000 3000.
Only now is the GMA4500HD getting the work it needs.

vesa soln:
The vesa driver has the correct video modeline for the attached display from the EDID DDC.
It rejects the mode with error "unable to estimate virtual screen size".
It knows the resolution, it knows the screen size in (mm).
This virtual size could be used to allocate memory.
Someone must know how to fix..Sorry, I have never used the vesa driver..
Could try sticking this in Screen Display subsection
Virtual 2048 2048

Or
Try adding this to the monitor section.
  HorizSync    30-60
  VertRefresh  48-62


There could be a need to specify the memory required as well.
The old intel driver was like that..
The old drivers are documented worse than the new ones.
Getting them to work was a rite-of-passage.

intel soln:
later kernel must eventually fix this bug..waiting game..

Windows soln:
Just use it as you paid for it. Give ubuntu another try in couple of months.

---

### Post by TrebleClef on 2011-09-19
Sorry, I don't know how to do this. Not worth messing with anymore. I think I will take your advice and carry on using Windows! Thanksalot for trying to help me out. Cheers.

---

### Post by BicyclerBoy on 2011-09-19
That's fine, got to go with what works.

It's a shame some of the common video h/w has been overlooked..

In a couple of months things may be different.
Just try a live USB-stick of ubuntu 11.10, no need to install.

---

