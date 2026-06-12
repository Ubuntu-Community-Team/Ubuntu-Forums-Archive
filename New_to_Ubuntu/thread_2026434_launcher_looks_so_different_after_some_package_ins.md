---
title: "launcher looks so different after some package installtion!"
date: 2012-07-15
forum: New to Ubuntu
---

### Post by nerdinator on 2012-07-15
I opened Synaptic Package manager **and installed the following**:
nvidia-common
nvidia-settings-update
nvidia-common
nvidia-current
nvidia-current-updates

The following were installed before(when unity launcher looked normal):

jockey-common
psensor
nvidia-settings
jockey-gtk
xserver-xorg-video-nouveau

My intention was to use Nvidia drivers.

After a restart **Launcher** looks sick!

[[IMG]http://pzy.be/t/2/Screenshot+from+2012-07-15+165739.png[/IMG]]("http://pzy.be/v/2/Screenshot+from+2012-07-15+165739.png")

Why is this?

---

### Post by Gone fishing on 2012-07-15
It's now using Unity 2D. I think when you installed the nvidia driver something went wrong. If you cat /var/log/Xorg.0.log you should be able to see which driver is being loaded.  I would install through the driver utility.

---

### Post by nerdinator on 2012-07-15
Hi.
Where do I find [B]driver utility?
[/B]I googled and checked on Software Center , but could find no such software.


Here is my Xorg.0.log :

```
[    17.299] 
X.Org X Server 1.11.3
Release Date: 2011-12-16
[    17.299] X Protocol Version 11, Revision 0
[    17.299] Build Operating System: Linux 2.6.42-26-generic x86_64 Ubuntu
[    17.299] Current Operating System: Linux Sachin-system 3.2.0-26-generic #41-Ubuntu SMP Thu Jun 14 17:49:24 UTC 2012 x86_64
[    17.299] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-26-generic root=UUID=3bb4cc62-6cb2-4540-90d7-bc631a1d03b8 ro quiet splash vt.handoff=7
[    17.300] Build Date: 09 July 2012  11:30:07PM
[    17.300] xorg-server 2:1.11.4-0ubuntu10.5 (For technical support please see http://www.ubuntu.com/support) 
[    17.300] Current version of pixman: 0.24.4
[    17.300]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    17.300] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    17.300] (==) Log file: "/var/log/Xorg.0.log", Time: Sun Jul 15 19:58:19 2012
[    17.318] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    17.318] (==) No Layout section.  Using the first Screen section.
[    17.318] (==) No screen section available. Using defaults.
[    17.318] (**) |-->Screen "Default Screen Section" (0)
[    17.319] (**) |   |-->Monitor "<default monitor>"
[    17.319] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    17.319] (==) Automatically adding devices
[    17.319] (==) Automatically enabling devices
[    17.319] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    17.319]     Entry deleted from font path.
[    17.319] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    17.319]     Entry deleted from font path.
[    17.319] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    17.319]     Entry deleted from font path.
[    17.319] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    17.319]     Entry deleted from font path.
[    17.319] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    17.319]     Entry deleted from font path.
[    17.319] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    17.319]     Entry deleted from font path.
[    17.319] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    17.319] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    17.319] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    17.319] (II) Loader magic: 0x7f8a8b612b00
[    17.319] (II) Module ABI versions:
[    17.319]     X.Org ANSI C Emulation: 0.4
[    17.319]     X.Org Video Driver: 11.0
[    17.319]     X.Org XInput driver : 16.0
[    17.319]     X.Org Server Extension : 6.0
[    17.319] (--) PCI:*(0:0:2:0) 8086:0116:1028:050e rev 9, Mem @ 0xf1400000/4194304, 0xe0000000/268435456, I/O @ 0x00004000/64
[    17.319] (--) PCI: (0:1:0:0) 10de:0df4:1028:050e rev 161, Mem @ 0xf0000000/16777216, 0xc0000000/268435456, 0xd0000000/33554432, I/O @ 0x00003000/128, BIOS @ 0x????????/524288
[    17.319] (II) Open ACPI successful (/var/run/acpid.socket)
[    17.319] (II) LoadModule: "extmod"
[    17.368] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    17.368] (II) Module extmod: vendor="X.Org Foundation"
[    17.368]     compiled for 1.11.3, module version = 1.0.0
[    17.368]     Module class: X.Org Server Extension
[    17.368]     ABI class: X.Org Server Extension, version 6.0
[    17.368] (II) Loading extension MIT-SCREEN-SAVER
[    17.368] (II) Loading extension XFree86-VidModeExtension
[    17.368] (II) Loading extension XFree86-DGA
[    17.368] (II) Loading extension DPMS
[    17.368] (II) Loading extension XVideo
[    17.368] (II) Loading extension XVideo-MotionCompensation
[    17.368] (II) Loading extension X-Resource
[    17.368] (II) LoadModule: "dbe"
[    17.368] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    17.368] (II) Module dbe: vendor="X.Org Foundation"
[    17.368]     compiled for 1.11.3, module version = 1.0.0
[    17.368]     Module class: X.Org Server Extension
[    17.368]     ABI class: X.Org Server Extension, version 6.0
[    17.368] (II) Loading extension DOUBLE-BUFFER
[    17.368] (II) LoadModule: "glx"
[    17.368] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[    17.944] (II) Module glx: vendor="NVIDIA Corporation"
[    17.944]     compiled for 4.0.2, module version = 1.0.0
[    17.944]     Module class: X.Org Server Extension
[    17.944] (II) NVIDIA GLX Module  295.49  Tue May  1 00:09:10 PDT 2012
[    17.944] (II) Loading extension GLX
[    17.944] (II) LoadModule: "record"
[    17.944] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    17.944] (II) Module record: vendor="X.Org Foundation"
[    17.944]     compiled for 1.11.3, module version = 1.13.0
[    17.944]     Module class: X.Org Server Extension
[    17.944]     ABI class: X.Org Server Extension, version 6.0
[    17.944] (II) Loading extension RECORD
[    17.944] (II) LoadModule: "dri"
[    17.945] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    17.945] (II) Module dri: vendor="X.Org Foundation"
[    17.945]     compiled for 1.11.3, module version = 1.0.0
[    17.945]     ABI class: X.Org Server Extension, version 6.0
[    17.945] (II) Loading extension XFree86-DRI
[    17.945] (II) LoadModule: "dri2"
[    17.945] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    17.945] (II) Module dri2: vendor="X.Org Foundation"
[    17.945]     compiled for 1.11.3, module version = 1.2.0
[    17.945]     ABI class: X.Org Server Extension, version 6.0
[    17.945] (II) Loading extension DRI2
[    17.945] (==) Matched intel as autoconfigured driver 0
[    17.945] (==) Matched vesa as autoconfigured driver 1
[    17.945] (==) Matched fbdev as autoconfigured driver 2
[    17.945] (==) Assigned the driver to the xf86ConfigLayout
[    17.945] (II) LoadModule: "intel"
[    17.945] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    17.945] (II) Module intel: vendor="X.Org Foundation"
[    17.945]     compiled for 1.11.3, module version = 2.17.0
[    17.945]     Module class: X.Org Video Driver
[    17.945]     ABI class: X.Org Video Driver, version 11.0
[    17.945] (II) LoadModule: "vesa"
[    17.945] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    17.945] (II) Module vesa: vendor="X.Org Foundation"
[    17.945]     compiled for 1.11.3, module version = 2.3.0
[    17.945]     Module class: X.Org Video Driver
[    17.945]     ABI class: X.Org Video Driver, version 11.0
[    17.945] (II) LoadModule: "fbdev"
[    17.946] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    17.946] (II) Module fbdev: vendor="X.Org Foundation"
[    17.946]     compiled for 1.11.3, module version = 0.4.2
[    17.946]     ABI class: X.Org Video Driver, version 11.0
[    17.946] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
    i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
    E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
    965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
    4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
    Sandybridge Desktop (GT1), Sandybridge Desktop (GT2),
    Sandybridge Desktop (GT2+), Sandybridge Mobile (GT1),
    Sandybridge Mobile (GT2), Sandybridge Mobile (GT2+),
    Sandybridge Server, Ivybridge Mobile (GT1), Ivybridge Mobile (GT2),
    Ivybridge Desktop (GT1), Ivybridge Desktop (GT2), Ivybridge Server
[    17.946] (II) VESA: driver for VESA chipsets: vesa
[    17.946] (II) FBDEV: driver for framebuffer: fbdev
[    17.946] (++) using VT number 7

[    17.947] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    17.947] (WW) Falling back to old probe method for vesa
[    17.947] (WW) Falling back to old probe method for fbdev
[    17.947] (II) Loading sub module "fbdevhw"
[    17.947] (II) LoadModule: "fbdevhw"
[    17.947] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    17.947] (II) Module fbdevhw: vendor="X.Org Foundation"
[    17.947]     compiled for 1.11.3, module version = 0.0.2
[    17.947]     ABI class: X.Org Video Driver, version 11.0
[    17.947] drmOpenDevice: node name is /dev/dri/card0
[    17.947] drmOpenDevice: open result is 9, (OK)
[    17.947] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[    17.947] drmOpenDevice: node name is /dev/dri/card0
[    17.947] drmOpenDevice: open result is 9, (OK)
[    17.947] drmOpenByBusid: drmOpenMinor returns 9
[    17.947] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    17.947] (II) intel(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    17.947] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    17.947] (==) intel(0): RGB weight 888
[    17.947] (==) intel(0): Default visual is TrueColor
[    17.948] (II) intel(0): Integrated Graphics Chipset: Intel(R) Sandybridge Mobile (GT2)
[    17.948] (--) intel(0): Chipset: "Sandybridge Mobile (GT2)"
[    17.948] (**) intel(0): Relaxed fencing enabled
[    17.948] (**) intel(0): Wait on SwapBuffers? enabled
[    17.948] (**) intel(0): Triple buffering? enabled
[    17.948] (**) intel(0): Framebuffer tiled
[    17.948] (**) intel(0): Pixmaps tiled
[    17.948] (**) intel(0): 3D buffers tiled
[    17.948] (**) intel(0): SwapBuffers wait enabled
[    17.948] (==) intel(0): video overlay key set to 0x101fe
[    17.948] (II) intel(0): Output LVDS1 has no monitor section
[    17.948] (II) intel(0): found backlight control interface /sys/class/backlight/acpi_video0
[    17.948] (II) intel(0): Output VGA1 has no monitor section
[    17.952] (II) intel(0): Output HDMI1 has no monitor section
[    18.000] (II) intel(0): Output DP1 has no monitor section
[    18.000] (II) intel(0): EDID for output LVDS1
[    18.000] (II) intel(0): Manufacturer: AUO  Model: 22ec  Serial#: 0
[    18.000] (II) intel(0): Year: 2009  Week: 1
[    18.000] (II) intel(0): EDID Version: 1.3
[    18.000] (II) intel(0): Digital Display Input
[    18.000] (II) intel(0): Max Image Size [cm]: horiz.: 34  vert.: 19
[    18.000] (II) intel(0): Gamma: 2.20
[    18.000] (II) intel(0): No DPMS capabilities specified
[    18.000] (II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    18.000] (II) intel(0): First detailed timing is preferred mode
[    18.000] (II) intel(0): redX: 0.620 redY: 0.340   greenX: 0.330 greenY: 0.570
[    18.000] (II) intel(0): blueX: 0.150 blueY: 0.060   whiteX: 0.313 whiteY: 0.329
[    18.000] (II) intel(0): Manufacturer's mask: 0
[    18.000] (II) intel(0): Supported detailed timing:
[    18.000] (II) intel(0): clock: 65.1 MHz   Image Size:  344 x 193 mm
[    18.000] (II) intel(0): h_active: 1366  h_sync: 1382  h_sync_end 1390 h_blank_end 1398 h_border: 0
[    18.000] (II) intel(0): v_active: 768  v_sync: 771  v_sync_end 775 v_blanking: 776 v_border: 0
[    18.000] (II) intel(0): Supported detailed timing:
[    18.000] (II) intel(0): clock: 65.1 MHz   Image Size:  344 x 193 mm
[    18.000] (II) intel(0): h_active: 1366  h_sync: 1382  h_sync_end 1390 h_blank_end 1398 h_border: 0
[    18.000] (II) intel(0): v_active: 768  v_sync: 771  v_sync_end 775 v_blanking: 776 v_border: 0
[    18.000] (II) intel(0):  1JC2N\80B156XW2
[    18.000] (II) intel(0): Unknown vendor-specific block 0
[    18.000] (II) intel(0): EDID (in hex):
[    18.000] (II) intel(0):     00ffffffffffff0006afec2200000000
[    18.000] (II) intel(0):     01130103902213780ac8959e57549226
[    18.000] (II) intel(0):     0f505400000001010101010101010101
[    18.000] (II) intel(0):     0101010101016e195620500008301008
[    18.000] (II) intel(0):     340058c11000001a6e19562050000830
[    18.000] (II) intel(0):     1008340058c11000001a000000fe0031
[    18.000] (II) intel(0):     4a43324e804231353658573200000000
[    18.000] (II) intel(0):     00000000000000000001010a202000d4
[    18.000] (II) intel(0): EDID vendor "AUO", prod id 8940
[    18.000] (II) intel(0): Printing DDC gathered Modelines:
[    18.000] (II) intel(0): Modeline "1366x768"x0.0   65.10  1366 1382 1390 1398  768 771 775 776 +hsync -vsync (46.6 kHz)
[    18.000] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[    18.000] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    18.000] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    18.000] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[    18.000] (II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
[    18.000] (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
[    18.000] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[    18.000] (II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
[    18.000] (II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
[    18.000] (II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
[    18.000] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    18.000] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    18.000] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    18.000] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[    18.000] (II) intel(0): Not using default mode "720x450" (doublescan mode not supported)
[    18.000] (II) intel(0): Not using default mode "800x512" (doublescan mode not supported)
[    18.000] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    18.000] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    18.000] (II) intel(0): Not using default mode "960x540" (doublescan mode not supported)
[    18.000] (II) intel(0): Not using default mode "960x600" (doublescan mode not supported)
[    18.000] (II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
[    18.000] (II) intel(0): Printing probed modes for output LVDS1
[    18.000] (II) intel(0): Modeline "1366x768"x60.0   65.10  1366 1382 1390 1398  768 771 775 776 +hsync -vsync (46.6 kHz)
[    18.000] (II) intel(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
[    18.000] (II) intel(0): Modeline "1360x768"x60.0   72.00  1360 1408 1440 1520  768 771 781 790 +hsync -vsync (47.4 kHz)
[    18.000] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    18.000] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    18.000] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    18.000] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    18.000] (II) intel(0): EDID for output VGA1
[    18.004] (II) intel(0): EDID for output HDMI1
[    18.052] (II) intel(0): EDID for output DP1
[    18.052] (II) intel(0): Output LVDS1 connected
[    18.052] (II) intel(0): Output VGA1 disconnected
[    18.052] (II) intel(0): Output HDMI1 disconnected
[    18.052] (II) intel(0): Output DP1 disconnected
[    18.052] (II) intel(0): Using exact sizes for initial modes
[    18.052] (II) intel(0): Output LVDS1 using initial mode 1366x768
[    18.052] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    18.052] (II) intel(0): Kernel page flipping support detected, enabling
[    18.052] (**) intel(0): Display dimensions: (340, 190) mm
[    18.052] (**) intel(0): DPI set to (102, 102)
[    18.052] (II) Loading sub module "fb"
[    18.052] (II) LoadModule: "fb"
[    18.052] (II) Loading /usr/lib/xorg/modules/libfb.so
[    18.052] (II) Module fb: vendor="X.Org Foundation"
[    18.052]     compiled for 1.11.3, module version = 1.0.0
[    18.052]     ABI class: X.Org ANSI C Emulation, version 0.4
[    18.052] (II) Loading sub module "dri2"
[    18.052] (II) LoadModule: "dri2"
[    18.052] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    18.052] (II) Module dri2: vendor="X.Org Foundation"
[    18.052]     compiled for 1.11.3, module version = 1.2.0
[    18.052]     ABI class: X.Org Server Extension, version 6.0
[    18.052] (II) UnloadModule: "vesa"
[    18.052] (II) Unloading vesa
[    18.052] (II) UnloadModule: "fbdev"
[    18.052] (II) Unloading fbdev
[    18.052] (II) UnloadModule: "fbdevhw"
[    18.052] (II) Unloading fbdevhw
[    18.052] (==) Depth 24 pixmap format is 32 bpp
[    18.052] (II) intel(0): [DRI2] Setup complete
[    18.052] (II) intel(0): [DRI2]   DRI driver: i965
[    18.052] (II) intel(0): Allocated new frame buffer 1408x768 stride 5632, tiled
[    18.053] (II) UXA(0): Driver registered support for the following operations:
[    18.053] (II)         solid
[    18.053] (II)         copy
[    18.053] (II)         composite (RENDER acceleration)
[    18.053] (II)         put_image
[    18.053] (II)         get_image
[    18.053] (==) intel(0): Backing store disabled
[    18.053] (==) intel(0): Silken mouse enabled
[    18.053] (II) intel(0): Initializing HW Cursor
[    18.112] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    18.112] (==) intel(0): DPMS enabled
[    18.112] (==) intel(0): Intel XvMC decoder enabled
[    18.112] (II) intel(0): Set up textured video
[    18.112] (II) intel(0): [XvMC] xvmc_vld driver initialized.
[    18.112] (II) intel(0): direct rendering: DRI2 Enabled
[    18.112] (==) intel(0): hotplug detection: "enabled"
[    18.112] (--) RandR disabled
[    18.112] (II) Initializing built-in extension Generic Event Extension
[    18.112] (II) Initializing built-in extension SHAPE
[    18.112] (II) Initializing built-in extension MIT-SHM
[    18.112] (II) Initializing built-in extension XInputExtension
[    18.112] (II) Initializing built-in extension XTEST
[    18.112] (II) Initializing built-in extension BIG-REQUESTS
[    18.112] (II) Initializing built-in extension SYNC
[    18.112] (II) Initializing built-in extension XKEYBOARD
[    18.112] (II) Initializing built-in extension XC-MISC
[    18.112] (II) Initializing built-in extension SECURITY
[    18.112] (II) Initializing built-in extension XINERAMA
[    18.112] (II) Initializing built-in extension XFIXES
[    18.112] (II) Initializing built-in extension RENDER
[    18.112] (II) Initializing built-in extension RANDR
[    18.112] (II) Initializing built-in extension COMPOSITE
[    18.112] (II) Initializing built-in extension DAMAGE
[    18.129] (EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
[    18.132] (II) intel(0): Setting screen physical size to 361 x 203
[    18.136] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    18.137] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[    18.138] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    18.138] (II) LoadModule: "evdev"
[    18.138] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    18.138] (II) Module evdev: vendor="X.Org Foundation"
[    18.138]     compiled for 1.11.3, module version = 2.7.0
[    18.138]     Module class: X.Org XInput Driver
[    18.138]     ABI class: X.Org XInput driver, version 16.0
[    18.138] (II) Using input driver 'evdev' for 'Power Button'
[    18.138] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    18.138] (**) Power Button: always reports core events
[    18.138] (**) evdev: Power Button: Device: "/dev/input/event3"
[    18.138] (--) evdev: Power Button: Vendor 0 Product 0x1
[    18.138] (--) evdev: Power Button: Found keys
[    18.138] (II) evdev: Power Button: Configuring as keyboard
[    18.138] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3/event3"
[    18.138] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    18.138] (**) Option "xkb_rules" "evdev"
[    18.138] (**) Option "xkb_model" "pc105"
[    18.138] (**) Option "xkb_layout" "us"
[    18.138] (II) config/udev: Adding input device Video Bus (/dev/input/event11)
[    18.138] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    18.138] (II) Using input driver 'evdev' for 'Video Bus'
[    18.138] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    18.138] (**) Video Bus: always reports core events
[    18.138] (**) evdev: Video Bus: Device: "/dev/input/event11"
[    18.138] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    18.138] (--) evdev: Video Bus: Found keys
[    18.138] (II) evdev: Video Bus: Configuring as keyboard
[    18.138] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:01/input/input11/event11"
[    18.138] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[    18.138] (**) Option "xkb_rules" "evdev"
[    18.138] (**) Option "xkb_model" "pc105"
[    18.138] (**) Option "xkb_layout" "us"
[    18.139] (II) config/udev: Adding input device Video Bus (/dev/input/event10)
[    18.139] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    18.139] (II) Using input driver 'evdev' for 'Video Bus'
[    18.139] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    18.139] (**) Video Bus: always reports core events
[    18.139] (**) evdev: Video Bus: Device: "/dev/input/event10"
[    18.139] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    18.139] (--) evdev: Video Bus: Found keys
[    18.139] (II) evdev: Video Bus: Configuring as keyboard
[    18.139] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:33/LNXVIDEO:00/input/input10/event10"
[    18.139] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 8)
[    18.139] (**) Option "xkb_rules" "evdev"
[    18.139] (**) Option "xkb_model" "pc105"
[    18.139] (**) Option "xkb_layout" "us"
[    18.139] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    18.139] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    18.139] (II) Using input driver 'evdev' for 'Power Button'
[    18.139] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    18.139] (**) Power Button: always reports core events
[    18.139] (**) evdev: Power Button: Device: "/dev/input/event0"
[    18.139] (--) evdev: Power Button: Vendor 0 Product 0x1
[    18.139] (--) evdev: Power Button: Found keys
[    18.139] (II) evdev: Power Button: Configuring as keyboard
[    18.139] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    18.139] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 9)
[    18.139] (**) Option "xkb_rules" "evdev"
[    18.139] (**) Option "xkb_model" "pc105"
[    18.139] (**) Option "xkb_layout" "us"
[    18.139] (II) config/udev: Adding input device Lid Switch (/dev/input/event2)
[    18.139] (II) No input driver specified, ignoring this device.
[    18.139] (II) This device may have been added with another device file.
[    18.140] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
[    18.140] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    18.140] (II) Using input driver 'evdev' for 'Sleep Button'
[    18.140] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    18.140] (**) Sleep Button: always reports core events
[    18.140] (**) evdev: Sleep Button: Device: "/dev/input/event1"
[    18.140] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[    18.140] (--) evdev: Sleep Button: Found keys
[    18.140] (II) evdev: Sleep Button: Configuring as keyboard
[    18.140] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1/event1"
[    18.140] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 10)
[    18.140] (**) Option "xkb_rules" "evdev"
[    18.140] (**) Option "xkb_model" "pc105"
[    18.140] (**) Option "xkb_layout" "us"
[    18.140] (II) config/udev: Adding input device Laptop_Integrated_Webcam_2HDM (/dev/input/event9)
[    18.140] (**) Laptop_Integrated_Webcam_2HDM: Applying InputClass "evdev keyboard catchall"
[    18.140] (II) Using input driver 'evdev' for 'Laptop_Integrated_Webcam_2HDM'
[    18.140] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    18.140] (**) Laptop_Integrated_Webcam_2HDM: always reports core events
[    18.140] (**) evdev: Laptop_Integrated_Webcam_2HDM: Device: "/dev/input/event9"
[    18.140] (--) evdev: Laptop_Integrated_Webcam_2HDM: Vendor 0x408 Product 0x2fb1
[    18.140] (--) evdev: Laptop_Integrated_Webcam_2HDM: Found keys
[    18.140] (II) evdev: Laptop_Integrated_Webcam_2HDM: Configuring as keyboard
[    18.140] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.4/1-1.4:1.0/input/input9/event9"
[    18.140] (II) XINPUT: Adding extended input device "Laptop_Integrated_Webcam_2HDM" (type: KEYBOARD, id 11)
[    18.140] (**) Option "xkb_rules" "evdev"
[    18.140] (**) Option "xkb_model" "pc105"
[    18.140] (**) Option "xkb_layout" "us"
[    18.140] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=3 (/dev/input/event13)
[    18.140] (II) No input driver specified, ignoring this device.
[    18.140] (II) This device may have been added with another device file.
[    18.141] (II) config/udev: Adding input device HDA Intel PCH Mic (/dev/input/event14)
[    18.141] (II) No input driver specified, ignoring this device.
[    18.141] (II) This device may have been added with another device file.
[    18.141] (II) config/udev: Adding input device HDA Intel PCH Headphone (/dev/input/event15)
[    18.141] (II) No input driver specified, ignoring this device.
[    18.141] (II) This device may have been added with another device file.
[    18.141] (II) config/udev: Adding input device HDA Intel PCH Headphone (/dev/input/event16)
[    18.141] (II) No input driver specified, ignoring this device.
[    18.141] (II) This device may have been added with another device file.
[    18.141] (II) config/udev: Adding input device Logitech USB Keyboard (/dev/input/event5)
[    18.141] (**) Logitech USB Keyboard: Applying InputClass "evdev keyboard catchall"
[    18.141] (II) Using input driver 'evdev' for 'Logitech USB Keyboard'
[    18.141] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    18.141] (**) Logitech USB Keyboard: always reports core events
[    18.141] (**) evdev: Logitech USB Keyboard: Device: "/dev/input/event5"
[    18.141] (--) evdev: Logitech USB Keyboard: Vendor 0x46d Product 0xc31c
[    18.141] (--) evdev: Logitech USB Keyboard: Found keys
[    18.141] (II) evdev: Logitech USB Keyboard: Configuring as keyboard
[    18.141] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1c.3/0000:04:00.0/usb3/3-1/3-1:1.0/input/input5/event5"
[    18.141] (II) XINPUT: Adding extended input device "Logitech USB Keyboard" (type: KEYBOARD, id 12)
[    18.141] (**) Option "xkb_rules" "evdev"
[    18.141] (**) Option "xkb_model" "pc105"
[    18.141] (**) Option "xkb_layout" "us"
[    18.141] (II) config/udev: Adding input device Logitech USB Keyboard (/dev/input/event6)
[    18.141] (**) Logitech USB Keyboard: Applying InputClass "evdev keyboard catchall"
[    18.141] (II) Using input driver 'evdev' for 'Logitech USB Keyboard'
[    18.141] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    18.141] (**) Logitech USB Keyboard: always reports core events
[    18.141] (**) evdev: Logitech USB Keyboard: Device: "/dev/input/event6"
[    18.141] (--) evdev: Logitech USB Keyboard: Vendor 0x46d Product 0xc31c
[    18.141] (--) evdev: Logitech USB Keyboard: Found absolute axes
[    18.141] (II) evdev: Logitech USB Keyboard: Forcing absolute x/y axes to exist.
[    18.141] (--) evdev: Logitech USB Keyboard: Found keys
[    18.141] (II) evdev: Logitech USB Keyboard: Configuring as mouse
[    18.141] (II) evdev: Logitech USB Keyboard: Configuring as keyboard
[    18.142] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1c.3/0000:04:00.0/usb3/3-1/3-1:1.1/input/input6/event6"
[    18.142] (II) XINPUT: Adding extended input device "Logitech USB Keyboard" (type: KEYBOARD, id 13)
[    18.142] (**) Option "xkb_rules" "evdev"
[    18.142] (**) Option "xkb_model" "pc105"
[    18.142] (**) Option "xkb_layout" "us"
[    18.142] (II) evdev: Logitech USB Keyboard: initialized for absolute axes.
[    18.142] (**) Logitech USB Keyboard: (accel) keeping acceleration scheme 1
[    18.142] (**) Logitech USB Keyboard: (accel) acceleration profile 0
[    18.142] (**) Logitech USB Keyboard: (accel) acceleration factor: 2.000
[    18.142] (**) Logitech USB Keyboard: (accel) acceleration threshold: 4
[    18.142] (II) config/udev: Adding input device USB Optical Mouse (/dev/input/event7)
[    18.142] (**) USB Optical Mouse: Applying InputClass "evdev pointer catchall"
[    18.142] (II) Using input driver 'evdev' for 'USB Optical Mouse'
[    18.142] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    18.142] (**) USB Optical Mouse: always reports core events
[    18.142] (**) evdev: USB Optical Mouse: Device: "/dev/input/event7"
[    18.142] (--) evdev: USB Optical Mouse: Vendor 0x461 Product 0x4d81
[    18.142] (--) evdev: USB Optical Mouse: Found 3 mouse buttons
[    18.142] (--) evdev: USB Optical Mouse: Found scroll wheel(s)
[    18.142] (--) evdev: USB Optical Mouse: Found relative axes
[    18.142] (--) evdev: USB Optical Mouse: Found x and y relative axes
[    18.142] (II) evdev: USB Optical Mouse: Configuring as mouse
[    18.142] (II) evdev: USB Optical Mouse: Adding scrollwheel support
[    18.142] (**) evdev: USB Optical Mouse: YAxisMapping: buttons 4 and 5
[    18.142] (**) evdev: USB Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    18.142] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1c.3/0000:04:00.0/usb3/3-2/3-2:1.0/input/input7/event7"
[    18.142] (II) XINPUT: Adding extended input device "USB Optical Mouse" (type: MOUSE, id 14)
[    18.142] (II) evdev: USB Optical Mouse: initialized for relative axes.
[    18.142] (**) USB Optical Mouse: (accel) keeping acceleration scheme 1
[    18.142] (**) USB Optical Mouse: (accel) acceleration profile 0
[    18.142] (**) USB Optical Mouse: (accel) acceleration factor: 2.000
[    18.142] (**) USB Optical Mouse: (accel) acceleration threshold: 4
[    18.142] (II) config/udev: Adding input device USB Optical Mouse (/dev/input/mouse0)
[    18.142] (II) No input driver specified, ignoring this device.
[    18.142] (II) This device may have been added with another device file.
[    18.143] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[    18.143] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    18.143] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    18.143] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    18.143] (**) AT Translated Set 2 keyboard: always reports core events
[    18.143] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event4"
[    18.143] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    18.143] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    18.143] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    18.143] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input4/event4"
[    18.143] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 15)
[    18.143] (**) Option "xkb_rules" "evdev"
[    18.143] (**) Option "xkb_model" "pc105"
[    18.143] (**) Option "xkb_layout" "us"
[    18.143] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event12)
[    18.143] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    18.143] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    18.143] (II) LoadModule: "synaptics"
[    18.143] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    18.143] (II) Module synaptics: vendor="X.Org Foundation"
[    18.143]     compiled for 1.11.3, module version = 1.6.2
[    18.143]     Module class: X.Org XInput Driver
[    18.143]     ABI class: X.Org XInput driver, version 16.0
[    18.143] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[    18.143] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    18.143] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    18.143] (**) Option "Device" "/dev/input/event12"
[    18.256] (II) synaptics: SynPS/2 Synaptics TouchPad: ignoring touch events for semi-multitouch device
[    18.256] (--) synaptics: SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5398
[    18.256] (--) synaptics: SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4728
[    18.256] (--) synaptics: SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    18.256] (--) synaptics: SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[    18.256] (--) synaptics: SynPS/2 Synaptics TouchPad: buttons: left right double triple
[    18.256] (--) synaptics: SynPS/2 Synaptics TouchPad: Vendor 0x2 Product 0x7
[    18.256] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    18.256] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    18.256] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input12/event12"
[    18.256] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD, id 16)
[    18.256] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[    18.256] (**) synaptics: SynPS/2 Synaptics TouchPad: MaxSpeed is now 1.75
[    18.256] (**) synaptics: SynPS/2 Synaptics TouchPad: AccelFactor is now 0.039
[    18.256] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    18.256] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[    18.256] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    18.256] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    18.256] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    18.257] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse1)
[    18.257] (**) SynPS/2 Synaptics TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"
[    18.258] (II) config/udev: Adding input device Dell WMI hotkeys (/dev/input/event8)
[    18.258] (**) Dell WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[    18.258] (II) Using input driver 'evdev' for 'Dell WMI hotkeys'
[    18.258] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    18.258] (**) Dell WMI hotkeys: always reports core events
[    18.258] (**) evdev: Dell WMI hotkeys: Device: "/dev/input/event8"
[    18.258] (--) evdev: Dell WMI hotkeys: Vendor 0 Product 0
[    18.258] (--) evdev: Dell WMI hotkeys: Found keys
[    18.258] (II) evdev: Dell WMI hotkeys: Configuring as keyboard
[    18.258] (**) Option "config_info" "udev:/sys/devices/virtual/input/input8/event8"
[    18.258] (II) XINPUT: Adding extended input device "Dell WMI hotkeys" (type: KEYBOARD, id 17)
[    18.258] (**) Option "xkb_rules" "evdev"
[    18.258] (**) Option "xkb_model" "pc105"
[    18.258] (**) Option "xkb_layout" "us"
[    18.582] (II) intel(0): EDID vendor "AUO", prod id 8940
[    18.582] (II) intel(0): Printing DDC gathered Modelines:
[    18.582] (II) intel(0): Modeline "1366x768"x0.0   65.10  1366 1382 1390 1398  768 771 775 776 +hsync -vsync (46.6 kHz)
[    21.795] (II) intel(0): EDID vendor "AUO", prod id 8940
[    21.795] (II) intel(0): Printing DDC gathered Modelines:
[    21.795] (II) intel(0): Modeline "1366x768"x0.0   65.10  1366 1382 1390 1398  768 771 775 776 +hsync -vsync (46.6 kHz)
[    98.387] (II) intel(0): EDID vendor "AUO", prod id 8940
[    98.387] (II) intel(0): Printing DDC gathered Modelines:
[    98.387] (II) intel(0): Modeline "1366x768"x0.0   65.10  1366 1382 1390 1398  768 771 775 776 +hsync -vsync (46.6 kHz)
[    98.965] (II) XKB: reuse xkmfile /var/lib/xkb/server-03AF3717FF3AB439A4BAABA686CCB40771CDF520.xkm
[    99.698] (II) intel(0): EDID vendor "AUO", prod id 8940
[    99.698] (II) intel(0): Printing DDC gathered Modelines:
[    99.698] (II) intel(0): Modeline "1366x768"x0.0   65.10  1366 1382 1390 1398  768 771 775 776 +hsync -vsync (46.6 kHz)
[   120.598] (II) intel(0): EDID vendor "AUO", prod id 8940
[   120.598] (II) intel(0): Printing DDC gathered Modelines:
[   120.598] (II) intel(0): Modeline "1366x768"x0.0   65.10  1366 1382 1390 1398  768 771 775 776 +hsync -vsync (46.6 kHz)
```

So which driver is being used?

---

### Post by nerdinator on 2012-07-15
Oh, and I use **Ubuntu 12.04**.

---

### Post by Gone fishing on 2012-07-15
There should be a line like 

Loading /usr/lib/xorg/modules/drivers/nvidia-drv.so

as there isn't we can assume the nvidia driver isn't loading hence you are using 2D Unity probably with the vesa driver. I would uninstall xserver-xorg-video-nouveau the opensource driver and then install the nvidia driver using the Additional drivers utility which should install the correct drivers an apply them correctly. Or you could un-install the proprietary drivers and use nouveau. 

I assume if you run nvidia-settings in a terminal the application either doesn't start or tells you that you are not using a nvidia video card.

---

