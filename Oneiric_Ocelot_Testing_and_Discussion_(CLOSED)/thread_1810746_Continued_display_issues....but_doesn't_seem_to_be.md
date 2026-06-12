---
title: "Continued display issues....but doesn't seem to be nVidia driver...."
date: 2011-07-23
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Smithie on 2011-07-23
So, I've been struggling with graphics/display issues and an increasing slowing system in general for awhile now, but I can't seem to piece together exactly what is going on.  I have an newish nVidia 8400GS driver, Pentium D processor, but my Xorg files don't seem to show that as the primary issue.  (I'm basing this off of particularly entry #280 in the very lengthy "Graphics Resolution- Upgrade/Blank Screen after Reboot" thread, [http://ubuntuforums.org/showthread.php?t=1743535&page=28](http://ubuntuforums.org/showthread.php?t=1743535&page=28))

The only thing I can piece together is that entires 277.336 and 277.370 claim that "Display (Sony SDM-HS75P (CRT-1)) does not support NVIDIA 3D".  I'm not really buying this though, so does anyone out there know how to solve my issue (or at least what my issue is so I can ask more coherent questions in the future)?  Xorg.0.log file is below.

I don't know if this is related, but I have a series of about 40-50 updates, many of which involve Compiz and OpenGL, which seem to be consistently held back.  This has been going on since Alpha 1.

Thanks for the help!

```
X.Org X Server 1.10.2.902 (1.10.3 RC 2)
Release Date: 2011-07-01
[   276.750] X Protocol Version 11, Revision 0
[   276.750] Build Operating System: Linux 2.6.24-29-server i686 Ubuntu
[   276.750] Current Operating System: Linux superdoof-desktop 3.0.0-6-generic #
7-Ubuntu SMP Wed Jul 20 13:53:50 UTC 2011 i686
[   276.750] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-6-generic root=
UUID=ee583014-e3fc-4c1b-83f3-82d125e84cab ro quiet splash vt.handoff=7
[   276.750] Build Date: 13 July 2011  12:18:21AM
[   276.750] xorg-server 2:1.10.2.902-1ubuntu3 (For technical support please see
 http://www.ubuntu.com/support) 
[   276.750] Current version of pixman: 0.22.2
[   276.750]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[   276.750] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   276.750] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Jul 22 15:30:20 201
1
[   276.750] (==) Using config file: "/etc/X11/xorg.conf"
[   276.750] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   276.751] (==) ServerLayout "Layout0"
[   276.751] (**) |-->Screen "Screen0" (0)
[   276.751] (**) |   |-->Monitor "Monitor0"
[   276.751] (**) |   |-->Device "Device0"
[   276.751] (**) |-->Input Device "Keyboard0"
[   276.751] (**) |-->Input Device "Mouse0"
[   276.751] (**) Option "Xinerama" "0"
[   276.751] (==) Automatically adding devices
[   276.751] (==) Automatically enabling devices
[   276.751] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   276.751]     Entry deleted from font path.
[   276.751] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[   276.751] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,
/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[   276.751] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vm
mouse' will be disabled.
[   276.752] (WW) Disabling Keyboard0
[   276.752] (WW) Disabling Mouse0
[   276.752] (II) Loader magic: 0x8239da0
[   276.752] (II) Module ABI versions:
[   276.752]     X.Org ANSI C Emulation: 0.4
[   276.752]     X.Org Video Driver: 10.0
[   276.752]     X.Org XInput driver : 12.3
[   276.752]     X.Org Server Extension : 5.0
[   276.753] (--) PCI:*(0:1:0:0) 10de:10c3:10de:066d rev 162, Mem @ 0xfb000000/1
6777216, 0xb0000000/268435456, 0xce000000/33554432, I/O @ 0x0000bf00/128, BIOS @
 0x????????/524288
[   276.753] (--) PCI: (0:4:4:0) 4444:0016:104d:813d rev 1, Mem @ 0xf4000000/671
08864
[   276.754] (II) Open ACPI successful (/var/run/acpid.socket)
[   276.754] (II) "extmod" will be loaded by default.
[   276.754] (II) "dbe" will be loaded by default.
[   276.754] (II) "glx" will be loaded. This was enabled by default and also spe
cified in the config file.
[   276.754] (II) "record" will be loaded by default.
[   276.754] (II) "dri" will be loaded by default.
[   276.754] (II) "dri2" will be loaded by default.
[   276.754] (II) LoadModule: "glx"
[   276.754] (II) Loading /usr/lib/xorg/extra-modules/libglx.so
[   276.792] (II) Module glx: vendor="NVIDIA Corporation"
[   276.792]     compiled for 4.0.2, module version = 1.0.0
[   276.792]     Module class: X.Org Server Extension
[   276.792] (II) NVIDIA GLX Module  275.19  Tue Jul 12 18:48:27 PDT 2011
[   276.792] (II) Loading extension GLX
[   276.792] (II) LoadModule: "extmod"
[   276.792] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[   276.793] (II) Module extmod: vendor="X.Org Foundation"
[   276.793]     compiled for 1.10.2.902, module version = 1.0.0
[   276.793]     Module class: X.Org Server Extension
[   276.793]     ABI class: X.Org Server Extension, version 5.0
[   276.793] (II) Loading extension MIT-SCREEN-SAVER
[   276.793] (II) Loading extension XFree86-VidModeExtension
[   276.793] (II) Loading extension XFree86-DGA
[   276.793] (II) Loading extension DPMS
[   276.793] (II) Loading extension XVideo
[   276.793] (II) Loading extension XVideo-MotionCompensation
[   276.793] (II) Loading extension X-Resource
[   276.793] (II) LoadModule: "dbe"
[   276.793] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[   276.793] (II) Module dbe: vendor="X.Org Foundation"
[   276.793]     compiled for 1.10.2.902, module version = 1.0.0
[   276.794]     Module class: X.Org Server Extension
[   276.794]     ABI class: X.Org Server Extension, version 5.0
[   276.794] (II) Loading extension DOUBLE-BUFFER
[   276.794] (II) LoadModule: "record"
[   276.794] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[   276.794] (II) Module record: vendor="X.Org Foundation"
[   276.794]     compiled for 1.10.2.902, module version = 1.13.0
[   276.794]     Module class: X.Org Server Extension
[   276.794]     ABI class: X.Org Server Extension, version 5.0
[   276.794] (II) Loading extension RECORD
[   276.794] (II) LoadModule: "dri"
[   276.795] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[   276.795] (II) Module dri: vendor="X.Org Foundation"
[   276.795]     compiled for 1.10.2.902, module version = 1.0.0
[   276.795]     ABI class: X.Org Server Extension, version 5.0
[   276.795] (II) Loading extension XFree86-DRI
[   276.795] (II) LoadModule: "dri2"
[   276.796] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[   276.796] (II) Module dri2: vendor="X.Org Foundation"
[   276.796]     compiled for 1.10.2.902, module version = 1.2.0
[   276.796]     ABI class: X.Org Server Extension, version 5.0
[   276.796] (II) Loading extension DRI2
[   276.796] (II) LoadModule: "nvidia"
[   276.796] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[   276.797] (II) Module nvidia: vendor="NVIDIA Corporation"
[   276.797]     compiled for 4.0.2, module version = 1.0.0
[   276.797]     Module class: X.Org Video Driver
[   276.797] (II) NVIDIA dlloader X Driver  275.19  Tue Jul 12 18:30:49 PDT 2011
[   276.797] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[   276.797] (--) using VT number 8

[   276.803] (II) Loading sub module "fb"
[   276.803] (II) LoadModule: "fb"
[   276.805] (II) Loading /usr/lib/xorg/modules/libfb.so
[   276.805] (II) Module fb: vendor="X.Org Foundation"
[   276.805]     compiled for 1.10.2.902, module version = 1.0.0
[   276.805]     ABI class: X.Org ANSI C Emulation, version 0.4
[   276.805] (II) Loading sub module "wfb"
[   276.805] (II) LoadModule: "wfb"
[   276.806] (II) Loading /usr/lib/xorg/modules/libwfb.so
[   276.806] (II) Module wfb: vendor="X.Org Foundation"
[   276.806]     compiled for 1.10.2.902, module version = 1.0.0
[   276.806]     ABI class: X.Org ANSI C Emulation, version 0.4
[   276.806] (II) Loading sub module "ramdac"
[   276.806] (II) LoadModule: "ramdac"
[   276.806] (II) Module "ramdac" already built-in
[   276.806] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[   276.806] (II) Loading /usr/lib/xorg/modules/libwfb.so
[   276.806] (II) Loading /usr/lib/xorg/modules/libfb.so
[   276.806] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[   276.806] (==) NVIDIA(0): RGB weight 888
[   276.806] (==) NVIDIA(0): Default visual is TrueColor
[   276.807] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[   276.807] (**) NVIDIA(0): Option "NoLogo" "True"
[   276.807] (**) NVIDIA(0): Option "TwinView" "1"
[   276.807] (**) NVIDIA(0): Option "MetaModes" "CRT: nvidia-auto-select +0+0, D
FP: nvidia-auto-select +1280+0"
[   277.336] (II) NVIDIA(GPU-0): Display (Sony SDM-HS75P (CRT-1)) does not suppo
rt NVIDIA 3D
[   277.336] (II) NVIDIA(GPU-0):     Vision stereo.
[   277.370] (II) NVIDIA(GPU-0): Display (Sony SDM-HS75P (DFP-0)) does not suppo
rt NVIDIA 3D
[   277.370] (II) NVIDIA(GPU-0):     Vision stereo.
[   277.372] (II) NVIDIA(0): NVIDIA GPU GeForce 8400GS (GT218) at PCI:1:0:0 (GPU
-0)
[   277.372] (--) NVIDIA(0): Memory: 1048576 kBytes
[   277.372] (--) NVIDIA(0): VideoBIOS: 70.18.2c.00.04
[   277.372] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[   277.372] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[   277.372] (--) NVIDIA(0): Connected display device(s) on GeForce 8400GS at PC
I:1:0:0
[   277.372] (--) NVIDIA(0):     Sony SDM-HS75P (CRT-1)
[   277.372] (--) NVIDIA(0):     Sony SDM-HS75P (DFP-0)
[   277.372] (--) NVIDIA(0): Sony SDM-HS75P (CRT-1): 160.0 MHz maximum pixel clo
ck
[   277.372] (--) NVIDIA(0): Sony SDM-HS75P (DFP-0): 330.0 MHz maximum pixel clo
ck
[   277.372] (--) NVIDIA(0): Sony SDM-HS75P (DFP-0): Internal Dual Link TMDS
[   277.373] (**) NVIDIA(0): TwinView enabled
[   277.374] (II) NVIDIA(0): Display Devices found referenced in MetaMode: CRT-1
, DFP-0
[   277.456] (II) NVIDIA(0): Assigned Display Devices: CRT-1, DFP-0
[   277.456] (II) NVIDIA(0): Validated modes:
[   277.456] (II) NVIDIA(0):    
[   277.456] (II) NVIDIA(0):     "CRT:nvidia-auto-select+0+0,DFP:nvidia-auto-sel
ect+1280+0"
[   277.456] (II) NVIDIA(0): Virtual screen size determined to be 2560 x 1024
[   277.489] (--) NVIDIA(0): DPI set to (95, 96); computed from "UseEdidDpi" X c
onfig
[   277.489] (--) NVIDIA(0):     option
[   277.489] (--) Depth 24 pixmap format is 32 bpp
[   277.489] (II) NVIDIA: Using 768.00 MB of virtual memory for indirect memory 
access.
[   277.496] (II) NVIDIA(0): Setting mode
[   277.496] (II) NVIDIA(0):     "CRT:nvidia-auto-select+0+0,DFP:nvidia-auto-sel
ect+1280+0"
[   277.526] (II) Loading extension NV-GLX
[   277.674] (==) NVIDIA(0): Disabling shared memory pixmaps
[   277.674] (==) NVIDIA(0): Backing store disabled
[   277.674] (==) NVIDIA(0): Silken mouse enabled
[   277.675] (**) NVIDIA(0): DPMS enabled
[   277.675] (II) Loading extension NV-CONTROL
[   277.675] (II) Loading extension XINERAMA
[   277.676] (II) Loading sub module "dri2"
[   277.676] (II) LoadModule: "dri2"
[   277.676] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[   277.676] (II) Module dri2: vendor="X.Org Foundation"
[   277.676]     compiled for 1.10.2.902, module version = 1.2.0
[   277.676]     ABI class: X.Org Server Extension, version 5.0
[   277.676] (II) NVIDIA(0): [DRI2] Setup complete
[   277.676] (==) RandR enabled
[   277.676] (II) Initializing built-in extension Generic Event Extension
[   277.676] (II) Initializing built-in extension SHAPE
[   277.676] (II) Initializing built-in extension MIT-SHM
[   277.676] (II) Initializing built-in extension XInputExtension
[   277.676] (II) Initializing built-in extension XTEST
[   277.677] (II) Initializing built-in extension BIG-REQUESTS
[   277.677] (II) Initializing built-in extension SYNC
[   277.677] (II) Initializing built-in extension XKEYBOARD
[   277.677] (II) Initializing built-in extension XC-MISC
[   277.677] (II) Initializing built-in extension SECURITY
[   277.677] (II) Initializing built-in extension XINERAMA
[   277.677] (II) Initializing built-in extension XFIXES
[   277.677] (II) Initializing built-in extension RENDER
[   277.677] (II) Initializing built-in extension RANDR
[   277.677] (II) Initializing built-in extension COMPOSITE
[   277.677] (II) Initializing built-in extension DAMAGE
[   277.677] (II) Initializing built-in extension GESTURE
[   277.677] (II) Initializing extension GLX
[   277.729] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E50
1AEF10E0D866E8E92.xkm
[   277.747] (II) config/udev: Adding input device Power Button (/dev/input/even
t1)
[   277.747] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   277.747] (II) LoadModule: "evdev"
[   277.748] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   277.749] (II) Module evdev: vendor="X.Org Foundation"
[   277.749]     compiled for 1.10.2, module version = 2.6.0
[   277.749]     Module class: X.Org XInput Driver
[   277.749]     ABI class: X.Org XInput driver, version 12.3
[   277.749] (II) Using input driver 'evdev' for 'Power Button'
[   277.749] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   277.749] (**) Power Button: always reports core events
[   277.749] (**) Power Button: Device: "/dev/input/event1"
[   277.749] (--) Power Button: Found keys
[   277.749] (II) Power Button: Configuring as keyboard
[   277.750] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:0
0/input/input1/event1"
[   277.750] (II) XINPUT: Adding extended input device "Power Button" (type: KEY
BOARD)
[   277.750] (**) Option "xkb_rules" "evdev"
[   277.750] (**) Option "xkb_model" "pc105"
[   277.750] (**) Option "xkb_layout" "us,cz"
[   277.750] (**) Option "xkb_variant" ","
[   277.750] (**) Option "xkb_options" "grp:alts_toggle"
[   277.754] (II) XKB: reuse xkmfile /var/lib/xkb/server-88BA37E0CC12C65181E9B7C
BBD0DF203CF426CBA.xkm
[   277.759] (II) config/udev: Adding input device Power Button (/dev/input/even
t0)
[   277.759] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   277.759] (II) Using input driver 'evdev' for 'Power Button'
[   277.759] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   277.759] (**) Power Button: always reports core events
[   277.759] (**) Power Button: Device: "/dev/input/event0"
[   277.759] (--) Power Button: Found keys
[   277.759] (II) Power Button: Configuring as keyboard
[   277.759] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/
PNP0C0C:00/input/input0/event0"
[   277.759] (II) XINPUT: Adding extended input device "Power Button" (type: KEY
BOARD)
[   277.759] (**) Option "xkb_rules" "evdev"
[   277.759] (**) Option "xkb_model" "pc105"
[   277.759] (**) Option "xkb_layout" "us,cz"
[   277.759] (**) Option "xkb_variant" ","
[   277.759] (**) Option "xkb_options" "grp:alts_toggle"
[   277.762] (II) config/udev: Adding input device HDA NVidia HDMI/DP (/dev/inpu
t/event4)
[   277.762] (II) No input driver/identifier specified (ignoring)
[   277.763] (II) config/udev: Adding input device HDA NVidia HDMI/DP (/dev/inpu
t/event5)
[   277.763] (II) No input driver/identifier specified (ignoring)
[   277.763] (II) config/udev: Adding input device HDA NVidia HDMI/DP (/dev/inpu
t/event6)
[   277.763] (II) No input driver/identifier specified (ignoring)
[   277.763] (II) config/udev: Adding input device HDA NVidia HDMI/DP (/dev/inpu
t/event7)
[   277.764] (II) No input driver/identifier specified (ignoring)
[   277.782] (II) config/udev: Adding input device AT Translated Set 2 keyboard 
(/dev/input/event2)
[   277.782] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keybo
ard catchall"
[   277.782] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[   277.782] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   277.782] (**) AT Translated Set 2 keyboard: always reports core events
[   277.782] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event2"
[   277.782] (--) AT Translated Set 2 keyboard: Found keys
[   277.782] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[   277.782] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/
input/input2/event2"
[   277.782] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyb
oard" (type: KEYBOARD)
[   277.782] (**) Option "xkb_rules" "evdev"
[   277.782] (**) Option "xkb_model" "pc105"
[   277.782] (**) Option "xkb_layout" "us,cz"
[   277.782] (**) Option "xkb_variant" ","
[   277.782] (**) Option "xkb_options" "grp:alts_toggle"
[   277.783] (II) config/udev: Adding input device ImExPS/2 Logitech Explorer Mo
use (/dev/input/event3)
[   277.783] (**) ImExPS/2 Logitech Explorer Mouse: Applying InputClass "evdev p
ointer catchall"
[   277.783] (II) Using input driver 'evdev' for 'ImExPS/2 Logitech Explorer Mou
se'
[   277.783] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   277.783] (**) ImExPS/2 Logitech Explorer Mouse: always reports core events
[   277.784] (**) ImExPS/2 Logitech Explorer Mouse: Device: "/dev/input/event3"
[   277.784] (--) ImExPS/2 Logitech Explorer Mouse: Found 9 mouse buttons
[   277.784] (--) ImExPS/2 Logitech Explorer Mouse: Found scroll wheel(s)
[   277.784] (--) ImExPS/2 Logitech Explorer Mouse: Found relative axes
[   277.784] (--) ImExPS/2 Logitech Explorer Mouse: Found x and y relative axes
[   277.784] (II) ImExPS/2 Logitech Explorer Mouse: Configuring as mouse
[   277.784] (II) ImExPS/2 Logitech Explorer Mouse: Adding scrollwheel support
[   277.784] (**) ImExPS/2 Logitech Explorer Mouse: YAxisMapping: buttons 4 and 
5
[   277.784] (**) ImExPS/2 Logitech Explorer Mouse: EmulateWheelButton: 4, Emula
teWheelInertia: 10, EmulateWheelTimeout: 200
[   277.784] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/
input/input3/event3"
[   277.784] (II) XINPUT: Adding extended input device "ImExPS/2 Logitech Explor
er Mouse" (type: MOUSE)
[   277.784] (II) ImExPS/2 Logitech Explorer Mouse: initialized for relative axe
s.
[   277.784] (**) ImExPS/2 Logitech Explorer Mouse: (accel) keeping acceleration
 scheme 1
[   277.784] (**) ImExPS/2 Logitech Explorer Mouse: (accel) acceleration profile
 0
[   277.784] (**) ImExPS/2 Logitech Explorer Mouse: (accel) acceleration factor:
 2.000
[   277.784] (**) ImExPS/2 Logitech Explorer Mouse: (accel) acceleration thresho
ld: 4
[   277.785] (II) config/udev: Adding input device ImExPS/2 Logitech Explorer Mo
use (/dev/input/mouse0)
[   277.785] (II) No input driver/identifier specified (ignoring)
[   354.022] (II) XKB: reuse xkmfile /var/lib/xkb/server-624F27300C2E54074A94E9E
F4D3AAD14049F0CC8.xkm
[   354.167] (II) XKB: reuse xkmfile /var/lib/xkb/server-5BA9090663AF605E6AB197F
CA66BB621AD89708D.xkm
[   354.196] (II) XKB: reuse xkmfile /var/lib/xkb/server-5BA9090663AF605E6AB197F
CA66BB621AD89708D.xkm
[   354.202] (II) XKB: reuse xkmfile /var/lib/xkb/server-5BA9090663AF605E6AB197F
CA66BB621AD89708D.xkm
```

---

### Post by PhantmKllr on 2011-07-24
You'd probably want to go ahead and install those updates.

I had been having problems with my Nvidia graphics card, up until a recent update.

---

### Post by awam66 on 2011-07-24
Try the recovery boot option then pick "Fix Broken Packages" from the menu. This may well install the held back packages.

---

### Post by Smithie on 2011-07-24
Great, thanks for the advice!  So, I did the "repair broken packages route" and that installed almost all of those long held back packages.  Only 5 packages remain held back now, 3 involving various appindicators, and 2 for unity-2d.

But, although ubuntu2d is working well now (in an Alpha 2 sense), ubuntu3d is still a mess, esp. headers, icons, and the panel.  The four issues I know I still have are:

1. Gnome settings daemon isn't working - this seems to be a more common problem right now, and I added myself to the launchpad report.

2. AT SPI Registry isn't working - this seems to be a more common problem again, and I added myself to the launchpad report.

3. I still have the "Driver activated but not in use" message, even though my Xorg.0.log doesn't show any driver errors.

4.  In that same Xorg.0.log report, I still get the "Display (Sony SDM-HS75P) does not support NVIDIA 3D".  I have two of these monitors working on a dual screen set-up.  I've been using Twinview in nVidia Settings to keep them both functional, as X will immediately disable one of my screens.

So, since I don't think the first 2 are really part of my graphics/display problem, is this actually a hardware issue?  Should I think about switching to Noveau if nVidia proprietary drivers won't use the 3d on my Sony monitors?  I'm a little confused, since depending on the daily update over the past two months, I've definitely had 3d working on my monitors at certain points despite the constant driver issues.

Also, I tried to get some EDID data out of the terminal to share/see if it offered any more information, but none of the terminal commands I am familiar with (dmesg | grep EDID, and read-edid | parse-edid) are working.

---

