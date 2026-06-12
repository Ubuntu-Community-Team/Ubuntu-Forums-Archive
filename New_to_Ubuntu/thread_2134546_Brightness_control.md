---
title: "Brightness control"
date: 2013-04-11
forum: New to Ubuntu
---

### Post by arejet on 2013-04-11
Hi Everyone,

I am new to Ubuntu. I cannot adjust the screen brightness in Ubuntu. I have 12.04 LTS 64-bit version on Sony Vaio VPCEH25EN.

Any help is much appreciated.

Thank you in advance.

Arejet

---

### Post by Toz on 2013-04-11
A google search shows that this laptop has an nvidia video card. Can you confirm this by running the following command in a terminal window and posting back the results:
```
sudo lspci -vnn | grep -A12 VGA
```

If it does have an nvidia card, have you installed the proprietary drivers?

And finally, if it _does_ have an nvidia card _and_ you have installed the proprietary drivers, you may need to enable the brightness control. To do so, try adding:
```

Option "RegistryDwords" "EnableBrightnessControl=1"
```
...to the DEVICE section of your /etc/X11/xorg.conf file (logout and back in again to test).

---

### Post by arejet on 2013-04-14
Hi,

Thank you for the suggestions.

I have  installed the proprietary drivers using apt-get install nvidia-current. However, I could not find the xorg.conf file in the specified location.

I ran the lspci command and the following output was printed onto the screen:

arejet@ubuntu:~$ sudo lspci -vnn|grep -A12 VGA
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation Device [10de:1055] (rev a1) (prog-if 00 [VGA controller])
    Subsystem: Sony Corporation Device [104d:908b]
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at d2000000 (32-bit, non-prefetchable) [size=16M]
    Memory at c0000000 (64-bit, prefetchable) [size=256M]
    Memory at d0000000 (64-bit, prefetchable) [size=32M]
    I/O ports at 4000 [size=128]
    Expansion ROM at d3080000 [disabled] [size=512K]
    Capabilities: [60] Power Management version 3
    Capabilities: [68] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [78] Express Endpoint, MSI 00
    Capabilities: [b4] Vendor Specific Information: Len=14 <?>
    Capabilities: [100] Virtual Channel

---

### Post by Toz on 2013-04-14
Does the proprietary driver show as enabled in Software Centre -> Edit -> Software Sources -> Additional Drivers tab?

Can you post the contents of your /etc/X11/Xorg.conf file:
```
pastebinit /var/log/Xorg.0.log
```
...and post back the link that is generated.

---

### Post by arejet on 2013-04-16
Software Centre -> Edit -> Software Sources -> Additional Drivers tab is not enabled. In fact, there is no such tab.

I cannot find the Xorg.conf file in etc/X11/.

By the way, what is this code for? When I paste this link on the terminal, I get, "The program 'pastebinit' is currently not installed.  You can install it by typing:
sudo apt-get install pastebinit"

Thank you
Arejet

---

### Post by Toz on 2013-04-16
> **arejet said:**
> Software Centre -> Edit -> Software Sources -> Additional Drivers tab is not enabled. In fact, there is no such tab.
Perhaps its still a separate app in 12.04 (can't remember). Search the dash for "Additional Drivers".

> By the way, what is this code for? 
This will upload a copy of your /var/log/Xorg.0.log file to the internet so that we can view it

> When I paste this link on the terminal, I get, "The program 'pastebinit' is currently not installed.  You can install it by typing:
sudo apt-get install pastebinit"
Okay. You should install it then - its a very handy program for others to be able to easily view your log files. Either that or simply copy/paste the contents of /var/log/Xorg.0.log back here.

---

### Post by arejet on 2013-04-21
> **Toz said:**
> Perhaps its still a separate app in 12.04 (can't remember). Search the dash for "Additional Drivers".

I searched the dash. I found this: NVIDIA accelarated graphics driver

This will upload a copy of your /var/log/Xorg.0.log file to the internet so that we can view it

I will install this on my system

Okay. You should install it then - its a very handy program for others to be able to easily view your log files. Either that or simply copy/paste the contents of /var/log/Xorg.0.log back here.

Here are the contents of the Xorg.0.log:
```
[    17.680] 
X.Org X Server 1.13.0
Release Date: 2012-09-05
[    17.680] X Protocol Version 11, Revision 0
[    17.680] Build Operating System: Linux 2.6.42-35-generic x86_64 Ubuntu
[    17.680] Current Operating System: Linux ubuntu 3.5.0-27-generic #46~precise1-Ubuntu SMP Tue Mar 26 19:33:21 UTC 2013 x86_64
[    17.680] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.5.0-27-generic root=UUID=0898E86798E8552A loop=/ubuntu/disks/root.disk ro quiet splash vt.handoff=7
[    17.680] Build Date: 19 January 2013  12:37:44PM
[    17.680] xorg-server 2:1.13.0-0ubuntu6.1~precise2 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    17.681] Current version of pixman: 0.24.4
[    17.681]     Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
[    17.681] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    17.681] (==) Log file: "/var/log/Xorg.0.log", Time: Sun Apr 21 09:45:04 2013
[    17.681] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    17.681] (==) No Layout section.  Using the first Screen section.
[    17.681] (==) No screen section available. Using defaults.
[    17.681] (**) |-->Screen "Default Screen Section" (0)
[    17.681] (**) |   |-->Monitor "<default monitor>"
[    17.681] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    17.681] (==) Automatically adding devices
[    17.681] (==) Automatically enabling devices
[    17.681] (==) Automatically adding GPU devices
[    17.681] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    17.681]     Entry deleted from font path.
[    17.681] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    17.681]     Entry deleted from font path.
[    17.681] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    17.681]     Entry deleted from font path.
[    17.681] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    17.681]     Entry deleted from font path.
[    17.681] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    17.681]     Entry deleted from font path.
[    17.681] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    17.681]     Entry deleted from font path.
[    17.681] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    17.681] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    17.681] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    17.681] (II) Loader magic: 0x7f840077bc20
[    17.681] (II) Module ABI versions:
[    17.681]     X.Org ANSI C Emulation: 0.4
[    17.681]     X.Org Video Driver: 13.0
[    17.681]     X.Org XInput driver : 18.0
[    17.681]     X.Org Server Extension : 7.0
[    17.683] (--) PCI:*(0:1:0:0) 10de:1055:104d:908b rev 161, Mem @ 0xd2000000/16777216, 0xc0000000/268435456, 0xd0000000/33554432, I/O @ 0x00004000/128, BIOS @ 0x????????/524288
[    17.683] (II) Open ACPI successful (/var/run/acpid.socket)
[    17.683] Initializing built-in extension Generic Event Extension
[    17.683] Initializing built-in extension SHAPE
[    17.683] Initializing built-in extension MIT-SHM
[    17.683] Initializing built-in extension XInputExtension
[    17.683] Initializing built-in extension XTEST
[    17.683] Initializing built-in extension BIG-REQUESTS
[    17.683] Initializing built-in extension SYNC
[    17.683] Initializing built-in extension XKEYBOARD
[    17.683] Initializing built-in extension XC-MISC
[    17.683] Initializing built-in extension SECURITY
[    17.683] Initializing built-in extension XINERAMA
[    17.683] Initializing built-in extension XFIXES
[    17.683] Initializing built-in extension RENDER
[    17.683] Initializing built-in extension RANDR
[    17.683] Initializing built-in extension COMPOSITE
[    17.683] Initializing built-in extension DAMAGE
[    17.683] Initializing built-in extension MIT-SCREEN-SAVER
[    17.683] Initializing built-in extension DOUBLE-BUFFER
[    17.683] Initializing built-in extension RECORD
[    17.683] Initializing built-in extension DPMS
[    17.683] Initializing built-in extension X-Resource
[    17.683] Initializing built-in extension XVideo
[    17.683] Initializing built-in extension XVideo-MotionCompensation
[    17.683] Initializing built-in extension XFree86-VidModeExtension
[    17.683] Initializing built-in extension XFree86-DGA
[    17.683] Initializing built-in extension XFree86-DRI
[    17.683] Initializing built-in extension DRI2
[    17.683] (II) LoadModule: "glx"
[    17.746] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[    18.915] (II) Module glx: vendor="NVIDIA Corporation"
[    18.915]     compiled for 4.0.2, module version = 1.0.0
[    18.915]     Module class: X.Org Server Extension
[    18.915] (II) NVIDIA GLX Module  304.88  Wed Mar 27 14:46:57 PDT 2013
[    18.915] Loading extension GLX
[    18.915] (==) Matched nvidia as autoconfigured driver 0
[    18.915] (==) Matched nouveau as autoconfigured driver 1
[    18.915] (==) Matched nv as autoconfigured driver 2
[    18.915] (==) Matched vesa as autoconfigured driver 3
[    18.915] (==) Matched modesetting as autoconfigured driver 4
[    18.915] (==) Matched fbdev as autoconfigured driver 5
[    18.915] (==) Assigned the driver to the xf86ConfigLayout
[    18.915] (II) LoadModule: "nvidia"
[    18.915] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    19.033] (II) Module nvidia: vendor="NVIDIA Corporation"
[    19.033]     compiled for 4.0.2, module version = 1.0.0
[    19.033]     Module class: X.Org Video Driver
[    19.094] (II) LoadModule: "nouveau"
[    19.095] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    19.095] (II) Module nouveau: vendor="X.Org Foundation"
[    19.095]     compiled for 1.13.0, module version = 1.0.2
[    19.095]     Module class: X.Org Video Driver
[    19.095]     ABI class: X.Org Video Driver, version 13.0
[    19.095] (II) LoadModule: "nv"
[    19.105] (WW) Warning, couldn't open module nv
[    19.105] (II) UnloadModule: "nv"
[    19.105] (II) Unloading nv
[    19.105] (EE) Failed to load module "nv" (module does not exist, 0)
[    19.105] (II) LoadModule: "vesa"
[    19.105] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    19.105] (II) Module vesa: vendor="X.Org Foundation"
[    19.105]     compiled for 1.13.0, module version = 2.3.2
[    19.105]     Module class: X.Org Video Driver
[    19.105]     ABI class: X.Org Video Driver, version 13.0
[    19.105] (II) LoadModule: "modesetting"
[    19.105] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    19.105] (II) Module modesetting: vendor="X.Org Foundation"
[    19.105]     compiled for 1.13.0, module version = 0.5.0
[    19.105]     Module class: X.Org Video Driver
[    19.105]     ABI class: X.Org Video Driver, version 13.0
[    19.105] (II) LoadModule: "fbdev"
[    19.105] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    19.105] (II) Module fbdev: vendor="X.Org Foundation"
[    19.105]     compiled for 1.13.0, module version = 0.4.3
[    19.105]     Module class: X.Org Video Driver
[    19.106]     ABI class: X.Org Video Driver, version 13.0
[    19.106] (==) Matched nvidia as autoconfigured driver 0
[    19.106] (==) Matched nouveau as autoconfigured driver 1
[    19.106] (==) Matched nv as autoconfigured driver 2
[    19.106] (==) Matched vesa as autoconfigured driver 3
[    19.106] (==) Matched modesetting as autoconfigured driver 4
[    19.106] (==) Matched fbdev as autoconfigured driver 5
[    19.106] (==) Assigned the driver to the xf86ConfigLayout
[    19.106] (II) LoadModule: "nvidia"
[    19.106] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    19.106] (II) Module nvidia: vendor="NVIDIA Corporation"
[    19.106]     compiled for 4.0.2, module version = 1.0.0
[    19.106]     Module class: X.Org Video Driver
[    19.106] (II) UnloadModule: "nvidia"
[    19.106] (II) Unloading nvidia
[    19.106] (II) Failed to load module "nvidia" (already loaded, 32644)
[    19.106] (II) LoadModule: "nouveau"
[    19.106] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    19.106] (II) Module nouveau: vendor="X.Org Foundation"
[    19.106]     compiled for 1.13.0, module version = 1.0.2
[    19.106]     Module class: X.Org Video Driver
[    19.106]     ABI class: X.Org Video Driver, version 13.0
[    19.106] (II) UnloadModule: "nouveau"
[    19.106] (II) Unloading nouveau
[    19.106] (II) Failed to load module "nouveau" (already loaded, 32644)
[    19.106] (II) LoadModule: "nv"
[    19.106] (WW) Warning, couldn't open module nv
[    19.106] (II) UnloadModule: "nv"
[    19.106] (II) Unloading nv
[    19.106] (EE) Failed to load module "nv" (module does not exist, 0)
[    19.106] (II) LoadModule: "vesa"
[    19.106] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    19.106] (II) Module vesa: vendor="X.Org Foundation"
[    19.106]     compiled for 1.13.0, module version = 2.3.2
[    19.106]     Module class: X.Org Video Driver
[    19.106]     ABI class: X.Org Video Driver, version 13.0
[    19.106] (II) UnloadModule: "vesa"
[    19.106] (II) Unloading vesa
[    19.106] (II) Failed to load module "vesa" (already loaded, 0)
[    19.106] (II) LoadModule: "modesetting"
[    19.107] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    19.107] (II) Module modesetting: vendor="X.Org Foundation"
[    19.107]     compiled for 1.13.0, module version = 0.5.0
[    19.107]     Module class: X.Org Video Driver
[    19.107]     ABI class: X.Org Video Driver, version 13.0
[    19.107] (II) UnloadModule: "modesetting"
[    19.107] (II) Unloading modesetting
[    19.107] (II) Failed to load module "modesetting" (already loaded, 0)
[    19.107] (II) LoadModule: "fbdev"
[    19.107] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    19.107] (II) Module fbdev: vendor="X.Org Foundation"
[    19.107]     compiled for 1.13.0, module version = 0.4.3
[    19.107]     Module class: X.Org Video Driver
[    19.107]     ABI class: X.Org Video Driver, version 13.0
[    19.107] (II) UnloadModule: "fbdev"
[    19.107] (II) Unloading fbdev
[    19.107] (II) Failed to load module "fbdev" (already loaded, 0)
[    19.107] (II) NVIDIA dlloader X Driver  304.88  Wed Mar 27 14:28:14 PDT 2013
[    19.107] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    19.107] (II) NOUVEAU driver Date:   Wed Sep 12 13:42:43 2012 +0200
[    19.107] (II) NOUVEAU driver for NVIDIA chipset families :
[    19.107]     RIVA TNT        (NV04)
[    19.107]     RIVA TNT2       (NV05)
[    19.107]     GeForce 256     (NV10)
[    19.107]     GeForce 2       (NV11, NV15)
[    19.107]     GeForce 4MX     (NV17, NV18)
[    19.107]     GeForce 3       (NV20)
[    19.107]     GeForce 4Ti     (NV25, NV28)
[    19.107]     GeForce FX      (NV3x)
[    19.107]     GeForce 6       (NV4x)
[    19.107]     GeForce 7       (G7x)
[    19.107]     GeForce 8       (G8x)
[    19.107]     GeForce GTX 200 (NVA0)
[    19.107]     GeForce GTX 400 (NVC0)
[    19.107] (II) VESA: driver for VESA chipsets: vesa
[    19.107] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    19.107] (II) FBDEV: driver for framebuffer: fbdev
[    19.107] (++) using VT number 7

[    19.107] (II) Loading sub module "fb"
[    19.107] (II) LoadModule: "fb"
[    19.108] (II) Loading /usr/lib/xorg/modules/libfb.so
[    19.108] (II) Module fb: vendor="X.Org Foundation"
[    19.108]     compiled for 1.13.0, module version = 1.0.0
[    19.108]     ABI class: X.Org ANSI C Emulation, version 0.4
[    19.108] (II) Loading sub module "wfb"
[    19.108] (II) LoadModule: "wfb"
[    19.108] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    19.108] (II) Module wfb: vendor="X.Org Foundation"
[    19.108]     compiled for 1.13.0, module version = 1.0.0
[    19.108]     ABI class: X.Org ANSI C Emulation, version 0.4
[    19.108] (II) Loading sub module "ramdac"
[    19.108] (II) LoadModule: "ramdac"
[    19.108] (II) Module "ramdac" already built-in
[    19.109] (WW) Falling back to old probe method for vesa
[    19.109] (WW) Falling back to old probe method for modesetting
[    19.109] (EE) open /dev/dri/card0: No such file or directory
[    19.109] (EE) open /dev/dri/card0: No such file or directory
[    19.109] (WW) Falling back to old probe method for fbdev
[    19.109] (II) Loading sub module "fbdevhw"
[    19.109] (II) LoadModule: "fbdevhw"
[    19.109] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    19.109] (II) Module fbdevhw: vendor="X.Org Foundation"
[    19.109]     compiled for 1.13.0, module version = 0.0.2
[    19.109]     ABI class: X.Org Video Driver, version 13.0
[    19.109] (II) NVIDIA(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    19.109] (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
[    19.109] (==) NVIDIA(0): RGB weight 888
[    19.109] (==) NVIDIA(0): Default visual is TrueColor
[    19.109] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    19.110] (**) NVIDIA(0): Enabling 2D acceleration
[    19.908] (II) NVIDIA(GPU-0): Display (Chi Mei Optoelectronics corp. (DFP-0)) does not
[    19.908] (II) NVIDIA(GPU-0):     support NVIDIA 3D Vision stereo.
[    19.910] (II) NVIDIA(0): NVIDIA GPU GeForce 410M (GF119) at PCI:1:0:0 (GPU-0)
[    19.910] (--) NVIDIA(0): Memory: 524288 kBytes
[    19.910] (--) NVIDIA(0): VideoBIOS: 75.19.0c.00.03
[    19.910] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[    19.910] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[    19.913] (--) NVIDIA(0): Valid display device(s) on GeForce 410M at PCI:1:0:0
[    19.913] (--) NVIDIA(0):     CRT-0
[    19.913] (--) NVIDIA(0):     Chi Mei Optoelectronics corp. (DFP-0) (connected)
[    19.913] (--) NVIDIA(0):     DFP-1
[    19.913] (--) NVIDIA(0): CRT-0: 400.0 MHz maximum pixel clock
[    19.913] (--) NVIDIA(0): Chi Mei Optoelectronics corp. (DFP-0): 330.0 MHz maximum pixel clock
[    19.913] (--) NVIDIA(0): Chi Mei Optoelectronics corp. (DFP-0): Internal Dual Link LVDS
[    19.913] (--) NVIDIA(0): DFP-1: 165.0 MHz maximum pixel clock
[    19.913] (--) NVIDIA(0): DFP-1: Internal Single Link TMDS
[    19.913] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    19.913] (**) NVIDIA(0):     device Chi Mei Optoelectronics corp. (DFP-0) (Using EDID
[    19.913] (**) NVIDIA(0):     frequencies has been enabled on all display devices.)
[    19.913] (==) NVIDIA(0): 
[    19.913] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[    19.913] (==) NVIDIA(0):     will be used as the requested mode.
[    19.913] (==) NVIDIA(0): 
[    19.913] (II) NVIDIA(0): Validated MetaModes:
[    19.913] (II) NVIDIA(0):     "DFP-0:nvidia-auto-select"
[    19.913] (II) NVIDIA(0): Virtual screen size determined to be 1366 x 768
[    20.675] (--) NVIDIA(0): DPI set to (99, 102); computed from "UseEdidDpi" X config
[    20.675] (--) NVIDIA(0):     option
[    20.675] (II) UnloadModule: "nouveau"
[    20.675] (II) Unloading nouveau
[    20.675] (II) UnloadModule: "vesa"
[    20.675] (II) Unloading vesa
[    20.675] (II) UnloadModule: "modesetting"
[    20.675] (II) Unloading modesetting
[    20.676] (II) UnloadModule: "fbdev"
[    20.676] (II) Unloading fbdev
[    20.676] (II) UnloadSubModule: "fbdevhw"
[    20.676] (II) Unloading fbdevhw
[    20.676] (--) Depth 24 pixmap format is 32 bpp
[    20.676] (II) NVIDIA: Using 3072.00 MB of virtual memory for indirect memory
[    20.676] (II) NVIDIA:     access.
[    20.681] (II) NVIDIA(0): Setting mode "DFP-0:nvidia-auto-select"
[    20.969] Loading extension NV-GLX
[    20.990] (==) NVIDIA(0): Disabling shared memory pixmaps
[    20.990] (==) NVIDIA(0): Backing store disabled
[    20.990] (==) NVIDIA(0): Silken mouse enabled
[    20.991] (==) NVIDIA(0): DPMS enabled
[    20.991] Loading extension NV-CONTROL
[    20.991] Loading extension XINERAMA
[    20.991] (II) Loading sub module "dri2"
[    20.991] (II) LoadModule: "dri2"
[    20.991] (II) Module "dri2" already built-in
[    20.991] (II) NVIDIA(0): [DRI2] Setup complete
[    20.991] (II) NVIDIA(0): [DRI2]   VDPAU driver: nvidia
[    20.991] (--) RandR disabled
[    20.996] (II) Initializing extension GLX
[    21.101] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    21.103] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    21.104] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    21.104] (II) LoadModule: "evdev"
[    21.104] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    21.104] (II) Module evdev: vendor="X.Org Foundation"
[    21.104]     compiled for 1.13.0, module version = 2.7.3
[    21.104]     Module class: X.Org XInput Driver
[    21.104]     ABI class: X.Org XInput driver, version 18.0
[    21.104] (II) Using input driver 'evdev' for 'Power Button'
[    21.104] (**) Power Button: always reports core events
[    21.104] (**) evdev: Power Button: Device: "/dev/input/event2"
[    21.104] (--) evdev: Power Button: Vendor 0 Product 0x1
[    21.104] (--) evdev: Power Button: Found keys
[    21.104] (II) evdev: Power Button: Configuring as keyboard
[    21.104] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[    21.104] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    21.104] (**) Option "xkb_rules" "evdev"
[    21.104] (**) Option "xkb_model" "pc105"
[    21.104] (**) Option "xkb_layout" "us"
[    21.105] (II) config/udev: Adding input device Sony Vaio Keys (/dev/input/event6)
[    21.105] (**) Sony Vaio Keys: Applying InputClass "evdev keyboard catchall"
[    21.105] (II) Using input driver 'evdev' for 'Sony Vaio Keys'
[    21.105] (**) Sony Vaio Keys: always reports core events
[    21.105] (**) evdev: Sony Vaio Keys: Device: "/dev/input/event6"
[    21.105] (--) evdev: Sony Vaio Keys: Vendor 0x104d Product 0
[    21.105] (--) evdev: Sony Vaio Keys: Found keys
[    21.105] (II) evdev: Sony Vaio Keys: Configuring as keyboard
[    21.105] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/SNY5001:00/input/input7/event6"
[    21.105] (II) XINPUT: Adding extended input device "Sony Vaio Keys" (type: KEYBOARD, id 7)
[    21.105] (**) Option "xkb_rules" "evdev"
[    21.105] (**) Option "xkb_model" "pc105"
[    21.105] (**) Option "xkb_layout" "us"
[    21.105] (II) config/udev: Adding input device Sony Vaio Jogdial (/dev/input/event7)
[    21.105] (II) No input driver specified, ignoring this device.
[    21.105] (II) This device may have been added with another device file.
[    21.105] (II) config/udev: Adding input device Sony Vaio Jogdial (/dev/input/mouse1)
[    21.105] (II) No input driver specified, ignoring this device.
[    21.105] (II) This device may have been added with another device file.
[    21.105] (II) config/udev: Adding input device Video Bus (/dev/input/event10)
[    21.105] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    21.105] (II) Using input driver 'evdev' for 'Video Bus'
[    21.105] (**) Video Bus: always reports core events
[    21.105] (**) evdev: Video Bus: Device: "/dev/input/event10"
[    21.106] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    21.106] (--) evdev: Video Bus: Found keys
[    21.106] (II) evdev: Video Bus: Configuring as keyboard
[    21.106] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:20/LNXVIDEO:00/input/input11/event10"
[    21.106] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 8)
[    21.106] (**) Option "xkb_rules" "evdev"
[    21.106] (**) Option "xkb_model" "pc105"
[    21.106] (**) Option "xkb_layout" "us"
[    21.106] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    21.106] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    21.106] (II) Using input driver 'evdev' for 'Power Button'
[    21.106] (**) Power Button: always reports core events
[    21.106] (**) evdev: Power Button: Device: "/dev/input/event0"
[    21.106] (--) evdev: Power Button: Vendor 0 Product 0x1
[    21.106] (--) evdev: Power Button: Found keys
[    21.106] (II) evdev: Power Button: Configuring as keyboard
[    21.106] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
[    21.106] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 9)
[    21.106] (**) Option "xkb_rules" "evdev"
[    21.106] (**) Option "xkb_model" "pc105"
[    21.106] (**) Option "xkb_layout" "us"
[    21.106] (II) config/udev: Adding input device Lid Switch (/dev/input/event1)
[    21.106] (II) No input driver specified, ignoring this device.
[    21.106] (II) This device may have been added with another device file.
[    21.107] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=3 (/dev/input/event11)
[    21.107] (II) No input driver specified, ignoring this device.
[    21.107] (II) This device may have been added with another device file.
[    21.107] (II) config/udev: Adding input device Sony Visual Communication Camer (/dev/input/event5)
[    21.107] (**) Sony Visual Communication Camer: Applying InputClass "evdev keyboard catchall"
[    21.107] (II) Using input driver 'evdev' for 'Sony Visual Communication Camer'
[    21.107] (**) Sony Visual Communication Camer: always reports core events
[    21.107] (**) evdev: Sony Visual Communication Camer: Device: "/dev/input/event5"
[    21.107] (--) evdev: Sony Visual Communication Camer: Vendor 0x4f2 Product 0xb28a
[    21.107] (--) evdev: Sony Visual Communication Camer: Found keys
[    21.107] (II) evdev: Sony Visual Communication Camer: Configuring as keyboard
[    21.107] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2/1-1.2:1.0/input/input6/event5"
[    21.107] (II) XINPUT: Adding extended input device "Sony Visual Communication Camer" (type: KEYBOARD, id 10)
[    21.107] (**) Option "xkb_rules" "evdev"
[    21.107] (**) Option "xkb_model" "pc105"
[    21.107] (**) Option "xkb_layout" "us"
[    21.107] (II) config/udev: Adding input device HDA Intel PCH Headphone (/dev/input/event9)
[    21.107] (II) No input driver specified, ignoring this device.
[    21.107] (II) This device may have been added with another device file.
[    21.108] (II) config/udev: Adding input device HDA Intel PCH Mic (/dev/input/event8)
[    21.108] (II) No input driver specified, ignoring this device.
[    21.108] (II) This device may have been added with another device file.
[    21.108] (II) config/udev: Adding input device SIGMACHIP Usb Mouse (/dev/input/event4)
[    21.108] (**) SIGMACHIP Usb Mouse: Applying InputClass "evdev pointer catchall"
[    21.108] (II) Using input driver 'evdev' for 'SIGMACHIP Usb Mouse'
[    21.108] (**) SIGMACHIP Usb Mouse: always reports core events
[    21.108] (**) evdev: SIGMACHIP Usb Mouse: Device: "/dev/input/event4"
[    21.108] (--) evdev: SIGMACHIP Usb Mouse: Vendor 0x1c4f Product 0x3
[    21.108] (--) evdev: SIGMACHIP Usb Mouse: Found 9 mouse buttons
[    21.108] (--) evdev: SIGMACHIP Usb Mouse: Found scroll wheel(s)
[    21.108] (--) evdev: SIGMACHIP Usb Mouse: Found relative axes
[    21.108] (--) evdev: SIGMACHIP Usb Mouse: Found x and y relative axes
[    21.108] (II) evdev: SIGMACHIP Usb Mouse: Configuring as mouse
[    21.108] (II) evdev: SIGMACHIP Usb Mouse: Adding scrollwheel support
[    21.108] (**) evdev: SIGMACHIP Usb Mouse: YAxisMapping: buttons 4 and 5
[    21.108] (**) evdev: SIGMACHIP Usb Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    21.108] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5/2-1.5:1.0/input/input5/event4"
[    21.108] (II) XINPUT: Adding extended input device "SIGMACHIP Usb Mouse" (type: MOUSE, id 11)
[    21.108] (II) evdev: SIGMACHIP Usb Mouse: initialized for relative axes.
[    21.108] (**) SIGMACHIP Usb Mouse: (accel) keeping acceleration scheme 1
[    21.108] (**) SIGMACHIP Usb Mouse: (accel) acceleration profile 0
[    21.108] (**) SIGMACHIP Usb Mouse: (accel) acceleration factor: 2.000
[    21.108] (**) SIGMACHIP Usb Mouse: (accel) acceleration threshold: 4
[    21.108] (II) config/udev: Adding input device SIGMACHIP Usb Mouse (/dev/input/mouse0)
[    21.108] (II) No input driver specified, ignoring this device.
[    21.108] (II) This device may have been added with another device file.
[    21.109] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    21.109] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    21.109] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    21.109] (**) AT Translated Set 2 keyboard: always reports core events
[    21.109] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    21.109] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    21.109] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    21.109] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    21.109] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[    21.109] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 12)
[    21.109] (**) Option "xkb_rules" "evdev"
[    21.109] (**) Option "xkb_model" "pc105"
[    21.109] (**) Option "xkb_layout" "us"
[    21.109] (II) config/udev: Adding input device DualPoint Stick (/dev/input/event12)
[    21.109] (**) DualPoint Stick: Applying InputClass "evdev pointer catchall"
[    21.109] (**) DualPoint Stick: Applying InputClass "trackpoint catchall"
[    21.109] (II) Using input driver 'evdev' for 'DualPoint Stick'
[    21.109] (**) DualPoint Stick: always reports core events
[    21.109] (**) evdev: DualPoint Stick: Device: "/dev/input/event12"
[    21.109] (--) evdev: DualPoint Stick: Vendor 0x2 Product 0x8
[    21.109] (--) evdev: DualPoint Stick: Found 3 mouse buttons
[    21.109] (--) evdev: DualPoint Stick: Found relative axes
[    21.109] (--) evdev: DualPoint Stick: Found x and y relative axes
[    21.109] (II) evdev: DualPoint Stick: Configuring as mouse
[    21.109] (**) Option "Emulate3Buttons" "true"
[    21.109] (**) Option "EmulateWheel" "true"
[    21.109] (**) Option "EmulateWheelButton" "2"
[    21.109] (**) Option "YAxisMapping" "4 5"
[    21.109] (**) evdev: DualPoint Stick: YAxisMapping: buttons 4 and 5
[    21.109] (**) Option "XAxisMapping" "6 7"
[    21.109] (**) evdev: DualPoint Stick: XAxisMapping: buttons 6 and 7
[    21.109] (**) evdev: DualPoint Stick: EmulateWheelButton: 2, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    21.109] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input13/event12"
[    21.109] (II) XINPUT: Adding extended input device "DualPoint Stick" (type: MOUSE, id 13)
[    21.109] (II) evdev: DualPoint Stick: initialized for relative axes.
[    21.110] (**) DualPoint Stick: (accel) keeping acceleration scheme 1
[    21.110] (**) DualPoint Stick: (accel) acceleration profile 0
[    21.110] (**) DualPoint Stick: (accel) acceleration factor: 2.000
[    21.110] (**) DualPoint Stick: (accel) acceleration threshold: 4
[    21.110] (II) config/udev: Adding input device DualPoint Stick (/dev/input/mouse2)
[    21.110] (II) No input driver specified, ignoring this device.
[    21.110] (II) This device may have been added with another device file.
[    21.110] (II) config/udev: Adding input device AlpsPS/2 ALPS DualPoint TouchPad (/dev/input/event13)
[    21.110] (**) AlpsPS/2 ALPS DualPoint TouchPad: Applying InputClass "evdev touchpad catchall"
[    21.110] (**) AlpsPS/2 ALPS DualPoint TouchPad: Applying InputClass "touchpad catchall"
[    21.110] (**) AlpsPS/2 ALPS DualPoint TouchPad: Applying InputClass "Default clickpad buttons"
[    21.110] (II) LoadModule: "synaptics"
[    21.110] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    21.110] (II) Module synaptics: vendor="X.Org Foundation"
[    21.110]     compiled for 1.13.0, module version = 1.6.2
[    21.110]     Module class: X.Org XInput Driver
[    21.110]     ABI class: X.Org XInput driver, version 18.0
[    21.110] (II) Using input driver 'synaptics' for 'AlpsPS/2 ALPS DualPoint TouchPad'
[    21.110] (**) AlpsPS/2 ALPS DualPoint TouchPad: always reports core events
[    21.110] (**) Option "Device" "/dev/input/event13"
[    21.111] (II) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: ignoring touch events for semi-multitouch device
[    21.111] (--) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: x-axis range 0 - 2000
[    21.111] (--) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: y-axis range 0 - 1400
[    21.111] (--) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: pressure range 0 - 127
[    21.111] (II) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: device does not report finger width.
[    21.111] (--) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: buttons: left right middle double triple
[    21.111] (--) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: Vendor 0x2 Product 0x8
[    21.111] (--) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: invalid finger width range.  defaulting to 0 - 15
[    21.111] (--) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: touchpad found
[    21.111] (**) AlpsPS/2 ALPS DualPoint TouchPad: always reports core events
[    21.111] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input14/event13"
[    21.111] (II) XINPUT: Adding extended input device "AlpsPS/2 ALPS DualPoint TouchPad" (type: TOUCHPAD, id 14)
[    21.111] (**) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[    21.111] (**) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: MaxSpeed is now 1.75
[    21.111] (**) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: AccelFactor is now 0.082
[    21.111] (**) AlpsPS/2 ALPS DualPoint TouchPad: (accel) keeping acceleration scheme 1
[    21.111] (**) AlpsPS/2 ALPS DualPoint TouchPad: (accel) acceleration profile 1
[    21.111] (**) AlpsPS/2 ALPS DualPoint TouchPad: (accel) acceleration factor: 2.000
[    21.111] (**) AlpsPS/2 ALPS DualPoint TouchPad: (accel) acceleration threshold: 4
[    21.111] (--) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: touchpad found
[    21.111] (II) config/udev: Adding input device AlpsPS/2 ALPS DualPoint TouchPad (/dev/input/mouse3)
[    21.111] (**) AlpsPS/2 ALPS DualPoint TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"
[    21.841] (II) NVIDIA(GPU-0): Display (Chi Mei Optoelectronics corp. (DFP-0)) does not
[    21.841] (II) NVIDIA(GPU-0):     support NVIDIA 3D Vision stereo.
[    21.841] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    21.841] (**) NVIDIA(0):     device Chi Mei Optoelectronics corp. (DFP-0) (Using EDID
[    21.841] (**) NVIDIA(0):     frequencies has been enabled on all display devices.)
[    24.853] (II) NVIDIA(GPU-0): Display (Chi Mei Optoelectronics corp. (DFP-0)) does not
[    24.853] (II) NVIDIA(GPU-0):     support NVIDIA 3D Vision stereo.
[    24.853] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    24.853] (**) NVIDIA(0):     device Chi Mei Optoelectronics corp. (DFP-0) (Using EDID
[    24.853] (**) NVIDIA(0):     frequencies has been enabled on all display devices.)
[    76.618] (II) NVIDIA(GPU-0): Display (Chi Mei Optoelectronics corp. (DFP-0)) does not
[    76.619] (II) NVIDIA(GPU-0):     support NVIDIA 3D Vision stereo.
[    76.619] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    76.619] (**) NVIDIA(0):     device Chi Mei Optoelectronics corp. (DFP-0) (Using EDID
[    76.619] (**) NVIDIA(0):     frequencies has been enabled on all display devices.)
[    76.890] (II) NVIDIA(GPU-0): Display (Chi Mei Optoelectronics corp. (DFP-0)) does not
[    76.890] (II) NVIDIA(GPU-0):     support NVIDIA 3D Vision stereo.
[    76.890] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    76.890] (**) NVIDIA(0):     device Chi Mei Optoelectronics corp. (DFP-0) (Using EDID
[    76.890] (**) NVIDIA(0):     frequencies has been enabled on all display devices.)
[    78.568] (II) NVIDIA(GPU-0): Display (Chi Mei Optoelectronics corp. (DFP-0)) does not
[    78.568] (II) NVIDIA(GPU-0):     support NVIDIA 3D Vision stereo.
[    78.568] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    78.568] (**) NVIDIA(0):     device Chi Mei Optoelectronics corp. (DFP-0) (Using EDID
[    78.568] (**) NVIDIA(0):     frequencies has been enabled on all display devices.)
[    84.692] (II) XKB: reuse xkmfile /var/lib/xkb/server-03AF3717FF3AB439A4BAABA686CCB40771CDF520.xkm
[    98.227] (II) NVIDIA(GPU-0): Display (Chi Mei Optoelectronics corp. (DFP-0)) does not
[    98.227] (II) NVIDIA(GPU-0):     support NVIDIA 3D Vision stereo.
[    98.227] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    98.227] (**) NVIDIA(0):     device Chi Mei Optoelectronics corp. (DFP-0) (Using EDID
[    98.227] (**) NVIDIA(0):     frequencies has been enabled on all display devices.)
```


Thank you so much for your help :)

---

### Post by Toz on 2013-04-21
Try this:

1. Create the file /usr/share/X11/xorg.conf.d/15-nvidia.conf:
```
gksu gedit /usr/share/X11/xorg.conf.d/15-nvidia.conf
```

2. Copy/paste the following content:
```
Section "Device"
  Identifier              "Device0"
  Driver                  "nvidia"
  VendorName              "NVIDIA Corporation"
  Option "RegistryDwords" "EnableBrightnessControl=1"
EndSection
```

3. Save the file and reboot

---

### Post by arejet on 2013-04-23
Hi,

Thank you so much for your help. It worked like magic !!

Regards,
Arejet

---

### Post by Toz on 2013-04-23
Glad to hear it worked.
Can you please mark this thread as solved by clicking the "Edit" link on your _first post_ in this thread, then clicking on the "Go Advanced" button and finally changing the Prefix to "[SOLVED]"?
Thanks.

---

### Post by arejet on 2013-04-24
Changed :)

---

