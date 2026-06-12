---
title: "OpenGL problem"
date: 2011-08-31
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Beeblebrx on 2011-08-31
I have [COLOR=DarkGreen]mesa[/COLOR] libraries installed on my system.  When I try to run an app through [COLOR=DarkGreen]wine[/COLOR] I get:```
wine: Call from 0x7b839702 to unimplemented function ntoskrnl.exe.KeDelayExecutionThread, aborting
wine: Unimplemented function ntoskrnl.exe.KeDelayExecutionThread called at address 0x7b839702 (thread 002a), starting debugger...
fixme:ntoskrnl:KeInitializeSpinLock stub: 0x5477a4
wine: Call from 0x7b839702 to unimplemented function ntoskrnl.exe.KeDelayExecutionThread, aborting
fixme:imm:ImmDisableTextFrameService Stub
fixme:imm:ImmReleaseContext (0x10082, 0x17c0b0): stub
fixme:imm:NotifyIME NI_CLOSECANDIDATE
fixme:imm:ImmGetOpenStatus (0x17c0b0): semi-stub
err:wgl:has_opengl Failed to load libGL: libGL.so.1: cannot open shared object file: No such file or directory
err:wgl:has_opengl OpenGL support is disabled.
err:d3d_caps:WineD3D_CreateFakeGLContext Can't find a suitable iPixelFormat.
err:d3d:InitAdapters Failed to get a gl context for default adapter
Direct3D8 is not available without OpenGL.
```[COLOR=DarkGreen]# glxinfo[/COLOR] shows:
```
name of display: :0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.4
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_MESA_copy_sub_buffer, GLX_INTEL_swap_event
client glx vendor string: Mesa Project and SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_framebuffer_sRGB, 
    GLX_MESA_copy_sub_buffer, GLX_MESA_multithread_makecurrent, 
    GLX_MESA_swap_control, GLX_OML_swap_method, GLX_OML_sync_control, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap, 
    GLX_INTEL_swap_event
GLX version: 1.4
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_MESA_multithread_makecurrent, GLX_OML_swap_method, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_INTEL_swap_event
OpenGL vendor string: Mesa Project
OpenGL renderer string: Software Rasterizer
OpenGL version string: 2.1 Mesa 7.11
OpenGL shading language version string: 1.20
```My motherboard is a foxconn model SiS-661 64 bit system.  The on-board vga controller is shown in [COLOR=DarkGreen]lshw[/COLOR] as:```
product: 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter [1039:6330]
vendor: Silicon Integrated Systems [SiS] [1039]
bus info: pci@0000:01:00.0  version: 00
width: 32 bits  clock: 66MHz
capabilities:  Power Management, AGP, AGP 3.0, vga_controller, PCI capabilities listing
configuration:  latency: 0
resources:  memory: e0000000-e7ffffff  memory: ea000000-ea01ffff
ioport: d000(size=128)
this device hasn't been claimed
```Strange here that a 64 bit MB states its on-board vga controller as 32 bits and is logged as unclaimed.

---

### Post by lucazade on 2011-08-31
OpenGL renderer string: Software Rasterizer
you're using software emulation, something wrong in video drivers.
unfortunately i've no experience with SIS drivers, what is the output of /var/log/Xorg.0.log ?

---

### Post by Beeblebrx on 2011-08-31
Partial output of log below.  Most important, driver appears to be for [COLOR=DarkGreen]SIS660/[M]661[/COLOR] but gives messgae "DRI disabled" nonetheless:
```
[    61.881] (II) Loading extension MIT-SCREEN-SAVER
[    61.881] (II) Loading extension XFree86-VidModeExtension
[    61.881] (II) Loading extension XFree86-DGA
[    61.881] (II) Loading extension DPMS
[    61.881] (II) Loading extension XVideo
[    61.881] (II) Loading extension XVideo-MotionCompensation
[    61.881] (II) Loading extension X-Resource
[    61.881] (II) LoadModule: "dbe"
[    61.882] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    61.882] (II) Module dbe: vendor="X.Org Foundation"
[    61.882]     compiled for 1.10.2.902, module version = 1.0.0
[    61.882]     Module class: X.Org Server Extension
[    61.882]     ABI class: X.Org Server Extension, version 5.0
[    61.882] (II) Loading extension DOUBLE-BUFFER
[    61.882] (II) LoadModule: "glx"
[    61.883] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    61.883] (II) Module glx: vendor="X.Org Foundation"
[    61.883]     compiled for 1.10.2.902, module version = 1.0.0
[    61.883]     ABI class: X.Org Server Extension, version 5.0
[    61.883] (==) AIGLX enabled
[    61.883] (II) Loading extension GLX
[    61.883] (II) LoadModule: "record"
[    61.887] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    61.888] (II) Module record: vendor="X.Org Foundation"
[    61.888]     compiled for 1.10.2.902, module version = 1.13.0
[    61.890]     Module class: X.Org Server Extension
[    61.890]     ABI class: X.Org Server Extension, version 5.0
[    61.890] (II) Loading extension RECORD
[    61.890] (II) LoadModule: "dri"
[    61.890] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    61.891] (II) Module dri: vendor="X.Org Foundation"
[    61.891]     compiled for 1.10.2.902, module version = 1.0.0
[    61.891]     ABI class: X.Org Server Extension, version 5.0
[    61.891] (II) Loading extension XFree86-DRI
[    61.891] (II) LoadModule: "dri2"
[    61.892] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    61.892] (II) Module dri2: vendor="X.Org Foundation"
[    61.892]     compiled for 1.10.2.902, module version = 1.2.0
[    61.892]     ABI class: X.Org Server Extension, version 5.0
[    61.892] (II) Loading extension DRI2
[    61.892] (==) Matched sis as autoconfigured driver 0
[    61.892] (==) Matched vesa as autoconfigured driver 1
[    61.892] (==) Matched fbdev as autoconfigured driver 2
[    61.892] (==) Assigned the driver to the xf86ConfigLayout
[    61.892] (II) LoadModule: "sis"
[    61.893] (II) Loading /usr/lib/xorg/modules/drivers/sis_drv.so
[    61.893] (II) Module sis: vendor="X.Org Foundation"
[    61.893]     compiled for 1.10.1, module version = 0.10.3
[    61.893]     Module class: X.Org Video Driver
[    61.893]     ABI class: X.Org Video Driver, version 10.0
[    61.893] (II) LoadModule: "vesa"
[    61.894] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    61.894] (II) Module vesa: vendor="X.Org Foundation"
[    61.894]     compiled for 1.10.2, module version = 2.3.0
[    61.894]     Module class: X.Org Video Driver
[    61.894]     ABI class: X.Org Video Driver, version 10.0
[    61.894] (II) LoadModule: "fbdev"
[    61.895] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    61.895] (II) Module fbdev: vendor="X.Org Foundation"
[    61.895]     compiled for 1.10.0, module version = 0.4.2
[    61.895]     ABI class: X.Org Video Driver, version 10.0
[    61.895] (II) SIS: driver for SiS chipsets: SIS5597/5598, SIS530/620,
    SIS6326/AGP/DVD, SIS300/305, SIS630/730, SIS540, SIS315, SIS315H,
    SIS315PRO/E, SIS550, SIS650/M650/651/740, SIS330(Xabre),
    SIS660/[M]661[F|M]X/[M]670/[M]741[GX]/[M]760[GX]/[M]761[GX]/[M]770[GX],
    SIS340
[    61.896] (II) SIS: driver for XGI chipsets: Volari Z7 (XG20),
    Volari V3XT/V5/V8/Duo (XG40)
[    61.896] (II) VESA: driver for VESA chipsets: vesa
[    61.896] (II) FBDEV: driver for framebuffer: fbdev
[    61.896] (++) using VT number 7
[    61.896] (WW) xf86OpenConsole: setpgid failed: Operation not permitted
[    61.896] (WW) xf86OpenConsole: setsid failed: Operation not permitted
[    61.900] (WW) Falling back to old probe method for sis
[    61.900] (--) Assigning device section with no busID to primary device
[    61.900] (--) Chipset SIS660/[M]661[F|M]X/[M]670/[M]741[GX]/[M]760[GX]/[M]761[GX]/[M]770[GX] found
[    61.900] (II) Loading /usr/lib/xorg/modules/drivers/sis_drv.so
[    61.900] (WW) Falling back to old probe method for vesa
[    61.900] (WW) Falling back to old probe method for fbdev
[    61.901] (II) Loading sub module "fbdevhw"
[    61.901] (II) LoadModule: "fbdevhw"
[    61.902] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    61.902] (II) Module fbdevhw: vendor="X.Org Foundation"
[    61.902]     compiled for 1.10.2.902, module version = 0.0.2
[    61.902]     ABI class: X.Org Video Driver, version 10.0
[    61.902] (EE) open /dev/fb0: No such file or directory
[    61.902] (II) SIS(0): SiS driver (2005/09/20-1, compiled for X.org 1.10.1.0)
[    61.902] (II) SIS(0): Copyright (C) 2001-2005 Thomas Winischhofer <thomas@winischhofer.net> and others
[    61.903] (II) SIS(0): *** See http://www.winischhofer.eu/linuxsisvga.shtml
[    61.903] (II) SIS(0): *** for documentation and updates.
[    61.903] (--) SIS(0): sisfb not found
[    61.903] (--) SIS(0): Relocated I/O registers at 0xD000
[    61.903] (II) Loading sub module "ramdac"
[    61.903] (II) LoadModule: "ramdac"
[    61.903] (II) Module "ramdac" already built-in
[    61.903] (II) SIS(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    61.903] (==) SIS(0): Depth 24, (--) framebuffer bpp 32
[    61.903] (==) SIS(0): RGB weight 888
[    61.903] (==) SIS(0): Default visual is TrueColor
[    61.904] (WW) SIS(0): Could not find/read video BIOS
[    61.904] (==) SIS(0): Using XAA acceleration architecture
[    61.904] (==) SIS(0): Using HW cursor
[    61.904] (==) SIS(0): Color HW cursor is enabled
[    61.904] (II) SIS(0): Using VRAM command queue, size 512k
[    61.904] (==) SIS(0): Hotkey display switching is enabled
[    61.904] (II) SIS(0): WARNING: Using the Hotkey might freeze your machine, regardless
[    61.904] (II) SIS(0):          whether enabled or disabled. This is no driver bug.
[    61.904] (==) SIS(0): SiSCtrl utility interface is disabled
[    61.904] (II) SIS(0): For information on SiSCtrl, see
        http://www.winischhofer.eu/linuxsispart1.shtml#sisctrl
[    61.904] (==) SIS(0): DRI disabled
[    61.904] (II) SIS(0): Checking OS for SSE support is not supported in this version of X.org
[    61.904] (II) SIS(0): If your OS supports SSE, set the option "UseSSE" to "on".
[    61.904] (--) SIS(0): DIMM0 is DDR SDRAM
[    61.904] (--) SIS(0): DIMM1 is DDR SDRAM
[    61.904] (--) SIS(0): DIMM2 is not installed
[    61.904] (--) SIS(0): DRAM type: DDR SDRAM
[    61.904] (--) SIS(0): Memory clock: 397.722 MHz
[    61.904] (--) SIS(0): DRAM bus width: 64 bit
[    61.904] (--) SIS(0): Linear framebuffer at 0xE0000000
[    61.904] (--) SIS(0): MMIO registers at 0xEA000000 (size 64K)
[    61.904] (--) SIS(0): VideoRAM: 32768 KB
[    61.904] (II) SIS(0): Using 32192K of framebuffer memory at offset 0K
[    61.904] (--) SIS(0): Hardware supports two video overlays
[    61.905] (==) SIS(0): Using gamma correction (1.0, 1.0, 1.0)
[    61.905] (II) SIS(0): Gamma correction is enabled
[    61.905] (II) SIS(0): Separate Xv gamma correction is disabled
[    61.905] (--) SIS(0): Memory bandwidth at 32 bpp is 795.444 MHz
[    61.905] (II) Loading sub module "ddc"
[    61.905] (II) LoadModule: "ddc"
```

---

### Post by dino99 on 2011-08-31
Some doc here:

[http://www.winischhofer.net/linuxsispart1.shtml](http://www.winischhofer.net/linuxsispart1.shtml)

---

### Post by Beeblebrx on 2011-09-01
Thanks, dino99 for the link.  From that page:
> *Once again: **There is no DRI/OpenGL/3D support for the  SiS 6326, 5597/5598, 530/620, 315, 550, 650, 651, 740, 330, 661, 741,  760, 761 including all model variations with letters in the model  number.***This means no DRI / OpenGL for you! I suppose Thomas' are the only drivers available in linux? Oh well...

---

