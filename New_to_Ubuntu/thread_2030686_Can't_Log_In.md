---
title: "Can't Log In"
date: 2012-07-20
forum: New to Ubuntu
---

### Post by DGINSD on 2012-07-20
This is the second time this issue has happened to me, the first time I just reinstalled, as there were some things I wanted to change about the install and it had only been a week since the first install.

Anyway,  heres the issue I try to log in to my account, I enter the correct password the screen blanks as if to load the desktop, then after a few seconds I get popped right back out to the greeter screen. If I enter the correct password again same result. If I log into my wifes account (that I made an administrator account, thank god) all is well. 

I have no Idea how this happened or how to resolve it. The last thing I was doing was switching to the integrated GPU (AMD/ATI Hybrid Graphics) to see if using that GPU would keep the random freezes from happening (A problem I've been trying to figure out since I first installed 12.04) I restarted the computer to restart X and initialize the change. After the reboot I couldn't log back in.

PLEASE HELP? I really don't want to go to the install all over again.


[COLOR="Red"][SIZE="3"]EDIT:[/SIZE][/COLOR] In the interest of saving others time reading the whole thread the fix for this issue is found on post #14 courtesy of zombifier25. I apparently broke Xauthority for my account it was repaired by issuing;
```
sudo chown yourusername:yourusername ~/.Xauthority
``` 
Where yourusername, in both places found, is replaced by the username of the account, via tty1 (CTRL ALT F1)

---

### Post by lrcaballero on 2012-07-20
Hey, I am from SD too!

Anyways, click on switch user and then re0enter your user and password again and this should do the trick! 

We are experiencing the same issue on my sons pc but when doing what I mentioned above does the trick.

Good luck and Cheers

---

### Post by NikTh on 2012-07-20
> **DGINSD said:**
> 
Anyway,  heres the issue I try to log in to my account, I enter the correct password the screen blanks as if to load the desktop, then after a few seconds I get popped right back out to the greeter screen. If I enter the correct password again same result. If I log into my wifes account (that I made an administrator account, thank god) all is well. 


Hi , 
so its not a password problem i guess. Maybe its something wrong with your environment settings. 
Try to post back the results of 
```
gedit /var/log/Xorg.0.log
``` 

Thanks

---

### Post by ryanepod on 2012-07-20
Do you have the correct video drivers installed? I had a very similar problem when I was still using Ubuntu try changing to the 2d unity desktop and installing the video drivers that should help?

---

### Post by DGINSD on 2012-07-20
Here is the output of the Xorg.0.log. The account that works is Darryl the busted one is David.

```
[    95.998] 
X.Org X Server 1.11.3
Release Date: 2011-12-16
[    95.998] X Protocol Version 11, Revision 0
[    95.998] Build Operating System: Linux 2.6.42-26-generic x86_64 Ubuntu
[    95.998] Current Operating System: Linux david-HP-Pavilion-g6-Notebook-PC 3.2.0-26-generic #41-Ubuntu SMP Thu Jun 14 17:49:24 UTC 2012 x86_64
[    95.998] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-26-generic root=UUID=7bb9c2f1-d3da-4e0e-85ce-4360d5c413fe ro quiet splash vt.handoff=7
[    95.998] Build Date: 16 July 2012  08:06:31PM
[    95.998] xorg-server 2:1.11.4-0ubuntu10.6 (For technical support please see http://www.ubuntu.com/support) 
[    95.998] Current version of pixman: 0.24.4
[    95.998]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    95.998] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    95.998] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Jul 20 20:43:43 2012
[    95.999] (==) Using config file: "/etc/X11/xorg.conf"
[    95.999] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    95.999] (==) ServerLayout "aticonfig Layout"
[    95.999] (**) |-->Screen "aticonfig-Screen[0]-0" (0)
[    95.999] (**) |   |-->Monitor "aticonfig-Monitor[0]-0"
[    96.000] (**) |   |-->Device "aticonfig-Device[0]-0"
[    96.000] (==) Automatically adding devices
[    96.000] (==) Automatically enabling devices
[    96.000] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    96.000]     Entry deleted from font path.
[    96.000] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    96.000]     Entry deleted from font path.
[    96.000] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    96.000]     Entry deleted from font path.
[    96.000] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    96.000]     Entry deleted from font path.
[    96.000] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    96.000]     Entry deleted from font path.
[    96.000] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    96.000]     Entry deleted from font path.
[    96.000] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    96.000] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    96.000] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    96.000] (II) Loader magic: 0x7ffab6e9cb00
[    96.000] (II) Module ABI versions:
[    96.000]     X.Org ANSI C Emulation: 0.4
[    96.000]     X.Org Video Driver: 11.0
[    96.000]     X.Org XInput driver : 16.0
[    96.000]     X.Org Server Extension : 6.0
[    96.002] (--) PCI:*(0:0:1:0) 1002:9649:103c:169b rev 0, Mem @ 0xe0000000/268435456, 0xf0500000/262144, I/O @ 0x00004000/256
[    96.002] (II) Open ACPI successful (/var/run/acpid.socket)
[    96.002] (II) "extmod" will be loaded by default.
[    96.002] (II) "dbe" will be loaded by default.
[    96.002] (II) "glx" will be loaded by default.
[    96.002] (II) "record" will be loaded by default.
[    96.002] (II) "dri" will be loaded by default.
[    96.003] (II) "dri2" will be loaded by default.
[    96.003] (II) LoadModule: "extmod"
[    96.004] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    96.004] (II) Module extmod: vendor="X.Org Foundation"
[    96.004]     compiled for 1.11.3, module version = 1.0.0
[    96.004]     Module class: X.Org Server Extension
[    96.004]     ABI class: X.Org Server Extension, version 6.0
[    96.004] (II) Loading extension MIT-SCREEN-SAVER
[    96.004] (II) Loading extension XFree86-VidModeExtension
[    96.004] (II) Loading extension XFree86-DGA
[    96.004] (II) Loading extension DPMS
[    96.004] (II) Loading extension XVideo
[    96.004] (II) Loading extension XVideo-MotionCompensation
[    96.004] (II) Loading extension X-Resource
[    96.004] (II) LoadModule: "dbe"
[    96.005] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    96.005] (II) Module dbe: vendor="X.Org Foundation"
[    96.005]     compiled for 1.11.3, module version = 1.0.0
[    96.005]     Module class: X.Org Server Extension
[    96.005]     ABI class: X.Org Server Extension, version 6.0
[    96.005] (II) Loading extension DOUBLE-BUFFER
[    96.005] (II) LoadModule: "glx"
[    96.005] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/extensions/libglx.so
[    96.006] (II) Module glx: vendor="Advanced Micro Devices, Inc."
[    96.006]     compiled for 6.9.0, module version = 1.0.0
[    96.006] (II) Loading extension GLX
[    96.006] (II) LoadModule: "record"
[    96.007] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    96.007] (II) Module record: vendor="X.Org Foundation"
[    96.007]     compiled for 1.11.3, module version = 1.13.0
[    96.007]     Module class: X.Org Server Extension
[    96.007]     ABI class: X.Org Server Extension, version 6.0
[    96.007] (II) Loading extension RECORD
[    96.007] (II) LoadModule: "dri"
[    96.008] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    96.009] (II) Module dri: vendor="X.Org Foundation"
[    96.009]     compiled for 1.11.3, module version = 1.0.0
[    96.009]     ABI class: X.Org Server Extension, version 6.0
[    96.009] (II) Loading extension XFree86-DRI
[    96.009] (II) LoadModule: "dri2"
[    96.009] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    96.010] (II) Module dri2: vendor="X.Org Foundation"
[    96.010]     compiled for 1.11.3, module version = 1.2.0
[    96.010]     ABI class: X.Org Server Extension, version 6.0
[    96.010] (II) Loading extension DRI2
[    96.010] (II) LoadModule: "fglrx"
[    96.010] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/drivers/fglrx_drv.so
[    96.057] (II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
[    96.057]     compiled for 1.4.99.906, module version = 8.96.4
[    96.057]     Module class: X.Org Video Driver
[    96.058] (II) Loading sub module "fglrxdrm"
[    96.058] (II) LoadModule: "fglrxdrm"
[    96.058] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/linux/libfglrxdrm.so
[    96.059] (II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
[    96.059]     compiled for 1.4.99.906, module version = 8.96.4
[    96.059] (II) ATI Proprietary Linux Driver Version Identifier:8.96.4
[    96.059] (II) ATI Proprietary Linux Driver Release Identifier: 8.961                                
[    96.059] (II) ATI Proprietary Linux Driver Build Date: Apr  5 2012 23:06:21
[    96.059] (++) using VT number 7

[    96.059] (WW) Falling back to old probe method for fglrx
[    96.096] (II) Loading PCS database from /etc/ati/amdpcsdb
[    96.100] (--) Chipset Supported AMD Graphics Processor (0x9649) found
[    96.100] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:1:1) found
[    96.103] (II) AMD Video driver is running on a device belonging to a group targeted for this release
[    96.103] (II) AMD Video driver is signed
[    96.104] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/drivers/fglrx_drv.so
[    96.104] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/linux/libfglrxdrm.so
[    96.104] (II) fglrx(0): pEnt->device->identifier=0x7ffab7547cb0
[    96.104] (II) fglrx(0): === [xdl_xs111_atiddxPreInit] === begin
[    96.105] (II) Loading sub module "vgahw"
[    96.105] (II) LoadModule: "vgahw"
[    96.106] (II) Loading /usr/lib/xorg/modules/libvgahw.so
[    96.106] (II) Module vgahw: vendor="X.Org Foundation"
[    96.106]     compiled for 1.11.3, module version = 0.1.0
[    96.106]     ABI class: X.Org Video Driver, version 11.0
[    96.106] (**) fglrx(0): Depth 24, (--) framebuffer bpp 32
[    96.106] (II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    96.106] (==) fglrx(0): Default visual is TrueColor
[    96.106] (**) fglrx(0): Option "DPMS" "true"
[    96.106] (==) fglrx(0): RGB weight 888
[    96.106] (II) fglrx(0): Using 8 bits per RGB 
[    96.106] (==) fglrx(0): Buffer Tiling is ON
[    96.106] (II) Loading sub module "fglrxdrm"
[    96.106] (II) LoadModule: "fglrxdrm"
[    96.107] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/linux/libfglrxdrm.so
[    96.107] (II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
[    96.107]     compiled for 1.4.99.906, module version = 8.96.4
[    96.111] ukiDynamicMajor: found major device number 251
[    96.111] ukiDynamicMajor: found major device number 251
[    96.111] ukiOpenByBusid: Searching for BusID PCI:0:1:0
[    96.111] ukiOpenDevice: node name is /dev/ati/card0
[    96.111] ukiOpenDevice: open result is 12, (OK)
[    96.111] ukiOpenByBusid: ukiOpenMinor returns 12
[    96.111] ukiOpenByBusid: ukiGetBusid reports PCI:0:1:0
[    96.112] (**) fglrx(0): NoAccel = NO
[    96.112] (**) fglrx(0): ATI 2D Acceleration Architecture enabled
[    96.112] (--) fglrx(0): Chipset: "AMD Radeon(TM) HD 6480G" (Chipset = 0x9649)
[    96.112] (--) fglrx(0): (PciSubVendor = 0x103c, PciSubDevice = 0x169b)
[    96.112] (==) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
[    96.112] (--) fglrx(0): Linear framebuffer (phys) at 0xe0000000
[    96.112] (--) fglrx(0): MMIO registers at 0xf0500000
[    96.112] (--) fglrx(0): I/O port at 0x00004000
[    96.112] (==) fglrx(0): ROM-BIOS at 0x000c0000
[    96.116] (II) fglrx(0): ATIF platform detected
[    96.117] (II) fglrx(0): AC Adapter is used
[    96.148] (II) fglrx(0): Primary V_BIOS segment is: 0xc000
[    96.150] (II) Loading sub module "vbe"
[    96.150] (II) LoadModule: "vbe"
[    96.150] (II) Loading /usr/lib/xorg/modules/libvbe.so
[    96.150] (II) Module vbe: vendor="X.Org Foundation"
[    96.150]     compiled for 1.11.3, module version = 1.1.0
[    96.150]     ABI class: X.Org Video Driver, version 11.0
[    96.150] (II) fglrx(0): VESA BIOS detected
[    96.150] (II) fglrx(0): VESA VBE Version 3.0
[    96.150] (II) fglrx(0): VESA VBE Total Mem: 16384 kB
[    96.150] (II) fglrx(0): VESA VBE OEM: AMD ATOMBIOS
[    96.150] (II) fglrx(0): VESA VBE OEM Software Rev: 12.43
[    96.150] (II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2010, AMD Technologies Inc. 
[    96.150] (II) fglrx(0): VESA VBE OEM Product: SUMO
[    96.150] (II) fglrx(0): VESA VBE OEM Product Rev: 01.00
[    96.159] (II) fglrx(0): ATI Video BIOS revision 9 or later detected
[    96.159] (--) fglrx(0): Video RAM: 524288 kByte, Type: DDR3
[    96.159] (II) fglrx(0): PCIE card detected
[    96.159] (--) fglrx(0): Using per-process page tables (PPPT) as GART.
[    96.159] (WW) fglrx(0): board is an unknown third party board, chipset is supported
[    96.170] (II) fglrx(0): Using adapter: 0:1.0.
[    97.189] (II) fglrx(0): [FB] MC range(MCFBBase = 0xf00000000, MCFBSize = 0x20000000)
[    97.199] (II) fglrx(0): Interrupt handler installed at IRQ 44.
[    97.200] (II) fglrx(0): RandR 1.2 support is enabled!
[    97.200] (II) fglrx(0): RandR 1.2 rotation support is enabled!
[    97.200] (==) fglrx(0): Center Mode is disabled 
[    97.200] (II) Loading sub module "fb"
[    97.200] (II) LoadModule: "fb"
[    97.200] (II) Loading /usr/lib/xorg/modules/libfb.so
[    97.201] (II) Module fb: vendor="X.Org Foundation"
[    97.201]     compiled for 1.11.3, module version = 1.0.0
[    97.201]     ABI class: X.Org ANSI C Emulation, version 0.4
[    97.201] (II) Loading sub module "ddc"
[    97.201] (II) LoadModule: "ddc"
[    97.201] (II) Module "ddc" already built-in
[    97.349] (II) fglrx(0): Finished Initialize PPLIB!
[    97.350] (II) fglrx(0): Output LVDS using monitor section aticonfig-Monitor[0]-0
[    97.350] (II) fglrx(0): Output DFP1 has no monitor section
[    97.350] (II) fglrx(0): Output CRT1 has no monitor section
[    97.350] (II) Loading sub module "ddc"
[    97.350] (II) LoadModule: "ddc"
[    97.350] (II) Module "ddc" already built-in
[    97.350] (II) fglrx(0): Connected Display0: LVDS
[    97.350] (II) fglrx(0): Display0 EDID data ---------------------------
[    97.350] (II) fglrx(0): Manufacturer: LGD  Model: 2f2  Serial#: 0
[    97.350] (II) fglrx(0): Year: 2010  Week: 0
[    97.350] (II) fglrx(0): EDID Version: 1.3
[    97.350] (II) fglrx(0): Digital Display Input
[    97.350] (II) fglrx(0): Max Image Size [cm]: horiz.: 34  vert.: 19
[    97.350] (II) fglrx(0): Gamma: 2.20
[    97.350] (II) fglrx(0): No DPMS capabilities specified
[    97.350] (II) fglrx(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    97.350] (II) fglrx(0): First detailed timing is preferred mode
[    97.350] (II) fglrx(0): redX: 0.605 redY: 0.355   greenX: 0.329 greenY: 0.579
[    97.350] (II) fglrx(0): blueX: 0.150 blueY: 0.055   whiteX: 0.313 whiteY: 0.329
[    97.350] (II) fglrx(0): Manufacturer's mask: 0
[    97.350] (II) fglrx(0): Supported detailed timing:
[    97.350] (II) fglrx(0): clock: 69.3 MHz   Image Size:  344 x 194 mm
[    97.350] (II) fglrx(0): h_active: 1366  h_sync: 1402  h_sync_end 1442 h_blank_end 1480 h_border: 0
[    97.350] (II) fglrx(0): v_active: 768  v_sync: 771  v_sync_end 776 v_blanking: 780 v_border: 0
[    97.351] (II) fglrx(0):  LG Display
[    97.351] (II) fglrx(0):  LP156WH4-TLC1
[    97.351] (II) fglrx(0): EDID (in hex):
[    97.351] (II) fglrx(0):     00ffffffffffff0030e4f20200000000
[    97.351] (II) fglrx(0):     00140103802213780a05859b5b549426
[    97.351] (II) fglrx(0):     0e505400000001010101010101010101
[    97.351] (II) fglrx(0):     010101010101121b567250000c302428
[    97.351] (II) fglrx(0):     350058c2100000190000000000000000
[    97.351] (II) fglrx(0):     00000000000000000000000000fe004c
[    97.351] (II) fglrx(0):     4720446973706c61790a2020000000fe
[    97.351] (II) fglrx(0):     004c503135365748342d544c433100ff
[    97.351] (II) fglrx(0): End of Display0 EDID data --------------------
[    97.352] (II) fglrx(0): EDID for output LVDS
[    97.352] (II) fglrx(0): Manufacturer: LGD  Model: 2f2  Serial#: 0
[    97.352] (II) fglrx(0): Year: 2010  Week: 0
[    97.352] (II) fglrx(0): EDID Version: 1.3
[    97.352] (II) fglrx(0): Digital Display Input
[    97.352] (II) fglrx(0): Max Image Size [cm]: horiz.: 34  vert.: 19
[    97.352] (II) fglrx(0): Gamma: 2.20
[    97.352] (II) fglrx(0): No DPMS capabilities specified
[    97.352] (II) fglrx(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    97.352] (II) fglrx(0): First detailed timing is preferred mode
[    97.352] (II) fglrx(0): redX: 0.605 redY: 0.355   greenX: 0.329 greenY: 0.579
[    97.352] (II) fglrx(0): blueX: 0.150 blueY: 0.055   whiteX: 0.313 whiteY: 0.329
[    97.352] (II) fglrx(0): Manufacturer's mask: 0
[    97.352] (II) fglrx(0): Supported detailed timing:
[    97.352] (II) fglrx(0): clock: 69.3 MHz   Image Size:  344 x 194 mm
[    97.352] (II) fglrx(0): h_active: 1366  h_sync: 1402  h_sync_end 1442 h_blank_end 1480 h_border: 0
[    97.352] (II) fglrx(0): v_active: 768  v_sync: 771  v_sync_end 776 v_blanking: 780 v_border: 0
[    97.352] (II) fglrx(0):  LG Display
[    97.352] (II) fglrx(0):  LP156WH4-TLC1
[    97.352] (II) fglrx(0): EDID (in hex):
[    97.352] (II) fglrx(0):     00ffffffffffff0030e4f20200000000
[    97.352] (II) fglrx(0):     00140103802213780a05859b5b549426
[    97.352] (II) fglrx(0):     0e505400000001010101010101010101
[    97.352] (II) fglrx(0):     010101010101121b567250000c302428
[    97.352] (II) fglrx(0):     350058c2100000190000000000000000
[    97.352] (II) fglrx(0):     00000000000000000000000000fe004c
[    97.352] (II) fglrx(0):     4720446973706c61790a2020000000fe
[    97.352] (II) fglrx(0):     004c503135365748342d544c433100ff
[    97.353] (II) fglrx(0): EDID vendor "LGD", prod id 754
[    97.353] (II) fglrx(0): Printing DDC gathered Modelines:
[    97.353] (II) fglrx(0): Modeline "1366x768"x0.0   69.30  1366 1402 1442 1480  768 771 776 780 -hsync -vsync (46.8 kHz)
[    97.353] (II) fglrx(0): Printing probed modes for output LVDS
[    97.353] (II) fglrx(0): Modeline "1366x768"x60.0   69.30  1366 1402 1442 1480  768 771 776 780 -hsync -vsync (46.8 kHz)
[    97.353] (II) fglrx(0): Modeline "1360x768"x60.0   69.30  1360 1402 1442 1480  768 771 776 780 -hsync -vsync (46.8 kHz)
[    97.353] (II) fglrx(0): Modeline "1280x768"x60.0   69.30  1280 1402 1442 1480  768 771 776 780 -hsync -vsync (46.8 kHz)
[    97.353] (II) fglrx(0): Modeline "1280x720"x60.0   69.30  1280 1402 1442 1480  720 771 776 780 -hsync -vsync (46.8 kHz)
[    97.353] (II) fglrx(0): Modeline "1024x768"x60.0   69.30  1024 1402 1442 1480  768 771 776 780 -hsync -vsync (46.8 kHz)
[    97.353] (II) fglrx(0): Modeline "1024x600"x60.0   69.30  1024 1402 1442 1480  600 771 776 780 -hsync -vsync (46.8 kHz)
[    97.353] (II) fglrx(0): Modeline "800x600"x60.0   69.30  800 1402 1442 1480  600 771 776 780 -hsync -vsync (46.8 kHz)
[    97.353] (II) fglrx(0): Modeline "800x480"x60.0   69.30  800 1402 1442 1480  480 771 776 780 -hsync -vsync (46.8 kHz)
[    97.353] (II) fglrx(0): Modeline "640x480"x60.0   69.30  640 1402 1442 1480  480 771 776 780 -hsync -vsync (46.8 kHz)
[    97.353] (II) fglrx(0): EDID for output DFP1
[    97.353] (II) fglrx(0): EDID for output CRT1
[    97.353] (II) fglrx(0): Output LVDS connected
[    97.353] (II) fglrx(0): Output DFP1 disconnected
[    97.353] (II) fglrx(0): Output CRT1 disconnected
[    97.353] (II) fglrx(0): Using exact sizes for initial modes
[    97.353] (II) fglrx(0): Output LVDS using initial mode 1366x768
[    97.353] (II) fglrx(0): Display dimensions: (340, 190) mm
[    97.353] (II) fglrx(0): DPI set to (102, 102)
[    97.353] (II) fglrx(0): Adapter AMD Radeon(TM) HD 6480G has 2 configurable heads and 1 displays connected.
[    97.353] (==) fglrx(0):  PseudoColor visuals disabled
[    97.353] (II) Loading sub module "ramdac"
[    97.353] (II) LoadModule: "ramdac"
[    97.353] (II) Module "ramdac" already built-in
[    97.353] (==) fglrx(0): NoDRI = NO
[    97.353] (==) fglrx(0): Capabilities: 0x00000000
[    97.353] (==) fglrx(0): CapabilitiesEx: 0x00000000
[    97.353] (==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
[    97.354] (==) fglrx(0): UseFastTLS=0
[    97.354] (--) Depth 24 pixmap format is 32 bpp
[    97.354] (II) Loading extension ATIFGLRXDRI
[    97.354] (II) fglrx(0): doing swlDriScreenInit
[    97.354] (II) fglrx(0): swlDriScreenInit for fglrx driver
[    97.355] ukiDynamicMajor: found major device number 251
[    97.355] ukiDynamicMajor: found major device number 251
[    97.355] ukiDynamicMajor: found major device number 251
[    97.355] ukiOpenByBusid: Searching for BusID PCI:0:1:0
[    97.355] ukiOpenDevice: node name is /dev/ati/card0
[    97.355] ukiOpenDevice: open result is 17, (OK)
[    97.355] ukiOpenByBusid: ukiOpenMinor returns 17
[    97.355] ukiOpenByBusid: ukiGetBusid reports PCI:0:1:0
[    97.355] (II) fglrx(0): [uki] DRM interface version 1.0
[    97.355] (II) fglrx(0): [uki] created "fglrx" driver at busid "PCI:0:1:0"
[    97.355] (II) fglrx(0): [uki] added 8192 byte SAREA at 0x5d4000
[    97.355] (II) fglrx(0): [uki] mapped SAREA 0x5d4000 to 0x7ffab6a8d000
[    97.355] (II) fglrx(0): [uki] framebuffer handle = 0x5d5000
[    97.355] (II) fglrx(0): [uki] added 1 reserved context for kernel
[    97.355] (II) fglrx(0): swlDriScreenInit done
[    97.355] (II) fglrx(0): Kernel Module Version Information:
[    97.355] (II) fglrx(0):     Name: fglrx
[    97.355] (II) fglrx(0):     Version: 8.96.4
[    97.355] (II) fglrx(0):     Date: Apr  5 2012
[    97.355] (II) fglrx(0):     Desc: ATI FireGL DRM kernel module
[    97.355] (II) fglrx(0): Kernel Module version matches driver.
[    97.355] (II) fglrx(0): Kernel Module Build Time Information:
[    97.355] (II) fglrx(0):     Build-Kernel UTS_RELEASE:        3.2.0-26-generic
[    97.355] (II) fglrx(0):     Build-Kernel MODVERSIONS:        no
[    97.355] (II) fglrx(0):     Build-Kernel __SMP__:            yes
[    97.355] (II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
[    97.355] (II) fglrx(0): [uki] register handle = 0x005d6000
[    97.388] (II) fglrx(0): DRI initialization successfull
[    97.388] (II) fglrx(0): FBADPhys: 0xf00000000 FBMappedSize: 0x01004000
[    97.389] (==) fglrx(0): Backing store disabled
[    97.389] (II) Loading extension FGLRXEXTENSION
[    97.389] (**) fglrx(0): DPMS enabled
[    97.389] (II) fglrx(0): Initialized in-driver Xinerama extension
[    97.389] (**) fglrx(0): Textured Video is enabled.
[    97.389] (II) LoadModule: "glesx"
[    97.390] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/glesx.so
[    97.391] (II) Module glesx: vendor="X.Org Foundation"
[    97.391]     compiled for 1.4.99.906, module version = 1.0.0
[    97.391] (II) Loading extension GLESX
[    97.391] (II) fglrx(0): GLESX enableFlags = 592
[    97.391] (II) fglrx(0): GLESX is enabled
[    97.391] (II) LoadModule: "amdxmm"
[    97.391] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/amdxmm.so
[    97.391] (II) Module amdxmm: vendor="X.Org Foundation"
[    97.391]     compiled for 1.4.99.906, module version = 2.0.0
[    97.416] (II) Loading extension AMDXVOPL
[    97.416] (II) Loading extension AMDXVBA
[    97.418] (II) fglrx(0): UVD feature is enabled(II) fglrx(0): 
[    97.424] (II) fglrx(0): Enable composite support successfully
[    97.424] (WW) fglrx(0): Option "VendorName" is not used
[    97.424] (WW) fglrx(0): Option "ModelName" is not used
[    97.424] (II) fglrx(0): X context handle = 0x1
[    97.424] (II) fglrx(0): [DRI] installation complete
[    97.424] (==) fglrx(0): Silken mouse enabled
[    97.424] (==) fglrx(0): Using HW cursor of display infrastructure!
[    97.425] (II) fglrx(0): Disabling in-server RandR and enabling in-driver RandR 1.2.
[    97.425] (II) fglrx(0): 'LVDS LCD' ConnectorType, abstracted as 'Panel'
[    97.425] (II) fglrx(0): 'eDP LCD' ConnectorType, abstracted as 'Panel'
[    98.486] (II) fglrx(0): Framebuffer compression enabled: mcAddr=0xf0f7b0000 width=0x800 height=0x258
[    98.486] (--) RandR disabled
[    98.486] (II) Initializing built-in extension Generic Event Extension
[    98.486] (II) Initializing built-in extension SHAPE
[    98.486] (II) Initializing built-in extension MIT-SHM
[    98.486] (II) Initializing built-in extension XInputExtension
[    98.486] (II) Initializing built-in extension XTEST
[    98.486] (II) Initializing built-in extension BIG-REQUESTS
[    98.486] (II) Initializing built-in extension SYNC
[    98.486] (II) Initializing built-in extension XKEYBOARD
[    98.486] (II) Initializing built-in extension XC-MISC
[    98.486] (II) Initializing built-in extension SECURITY
[    98.486] (II) Initializing built-in extension XINERAMA
[    98.486] (II) Initializing built-in extension XFIXES
[    98.486] (II) Initializing built-in extension RENDER
[    98.487] (II) Initializing built-in extension RANDR
[    98.487] (II) Initializing built-in extension COMPOSITE
[    98.487] (II) Initializing built-in extension DAMAGE
[    98.489] ukiDynamicMajor: found major device number 251
[    98.489] ukiDynamicMajor: found major device number 251
[    98.489] ukiOpenByBusid: Searching for BusID PCI:0:1:0
[    98.489] ukiOpenDevice: node name is /dev/ati/card0
[    98.489] ukiOpenDevice: open result is 18, (OK)
[    98.489] ukiOpenByBusid: ukiOpenMinor returns 18
[    98.489] ukiOpenByBusid: ukiGetBusid reports PCI:0:1:0
[    98.596] (II) AIGLX: Loaded and initialized OpenGL driver(II) GLX: Initialized DRI GL provider for screen 0
[    98.615] (II) fglrx(0): Enable the clock gating!
[    98.615] (II) fglrx(0): Setting screen physical size to 361 x 203
[    98.626] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    98.629] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    98.629] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    98.629] (II) LoadModule: "evdev"
[    98.629] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    98.630] (II) Module evdev: vendor="X.Org Foundation"
[    98.630]     compiled for 1.11.3, module version = 2.7.0
[    98.630]     Module class: X.Org XInput Driver
[    98.630]     ABI class: X.Org XInput driver, version 16.0
[    98.630] (II) Using input driver 'evdev' for 'Power Button'
[    98.630] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    98.630] (**) Power Button: always reports core events
[    98.630] (**) evdev: Power Button: Device: "/dev/input/event2"
[    98.630] (--) evdev: Power Button: Vendor 0 Product 0x1
[    98.630] (--) evdev: Power Button: Found keys
[    98.630] (II) evdev: Power Button: Configuring as keyboard
[    98.630] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[    98.630] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    98.630] (**) Option "xkb_rules" "evdev"
[    98.630] (**) Option "xkb_model" "pc105"
[    98.630] (**) Option "xkb_layout" "us"
[    98.630] (II) config/udev: Adding input device Video Bus (/dev/input/event4)
[    98.630] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    98.630] (II) Using input driver 'evdev' for 'Video Bus'
[    98.630] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    98.631] (**) Video Bus: always reports core events
[    98.631] (**) evdev: Video Bus: Device: "/dev/input/event4"
[    98.631] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    98.631] (--) evdev: Video Bus: Found keys
[    98.631] (II) evdev: Video Bus: Configuring as keyboard
[    98.631] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input4/event4"
[    98.631] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[    98.631] (**) Option "xkb_rules" "evdev"
[    98.631] (**) Option "xkb_model" "pc105"
[    98.631] (**) Option "xkb_layout" "us"
[    98.631] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    98.631] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    98.631] (II) Using input driver 'evdev' for 'Power Button'
[    98.631] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    98.631] (**) Power Button: always reports core events
[    98.631] (**) evdev: Power Button: Device: "/dev/input/event0"
[    98.631] (--) evdev: Power Button: Vendor 0 Product 0x1
[    98.631] (--) evdev: Power Button: Found keys
[    98.631] (II) evdev: Power Button: Configuring as keyboard
[    98.631] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    98.631] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 8)
[    98.631] (**) Option "xkb_rules" "evdev"
[    98.631] (**) Option "xkb_model" "pc105"
[    98.631] (**) Option "xkb_layout" "us"
[    98.632] (II) config/udev: Adding input device Lid Switch (/dev/input/event1)
[    98.632] (II) No input driver specified, ignoring this device.
[    98.632] (II) This device may have been added with another device file.
[    98.632] (II) config/udev: Adding input device HD-Audio Generic HDMI/DP,pcm=3 (/dev/input/event6)
[    98.632] (II) No input driver specified, ignoring this device.
[    98.632] (II) This device may have been added with another device file.
[    98.633] (II) config/udev: Adding input device HP Webcam-101 (/dev/input/event5)
[    98.633] (**) HP Webcam-101: Applying InputClass "evdev keyboard catchall"
[    98.633] (II) Using input driver 'evdev' for 'HP Webcam-101'
[    98.633] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    98.633] (**) HP Webcam-101: always reports core events
[    98.633] (**) evdev: HP Webcam-101: Device: "/dev/input/event5"
[    98.633] (--) evdev: HP Webcam-101: Vendor 0x4f2 Product 0xb249
[    98.633] (--) evdev: HP Webcam-101: Found keys
[    98.633] (II) evdev: HP Webcam-101: Configuring as keyboard
[    98.633] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:13.2/usb2/2-2/2-2:1.0/input/input5/event5"
[    98.633] (II) XINPUT: Adding extended input device "HP Webcam-101" (type: KEYBOARD, id 9)
[    98.633] (**) Option "xkb_rules" "evdev"
[    98.633] (**) Option "xkb_model" "pc105"
[    98.633] (**) Option "xkb_layout" "us"
[    98.633] (II) config/udev: Adding input device HD-Audio Generic Mic (/dev/input/event7)
[    98.633] (II) No input driver specified, ignoring this device.
[    98.633] (II) This device may have been added with another device file.
[    98.634] (II) config/udev: Adding input device HD-Audio Generic Headphone (/dev/input/event8)
[    98.634] (II) No input driver specified, ignoring this device.
[    98.634] (II) This device may have been added with another device file.
[    98.634] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    98.634] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    98.634] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    98.634] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    98.634] (**) AT Translated Set 2 keyboard: always reports core events
[    98.634] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    98.634] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    98.634] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    98.634] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    98.634] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[    98.634] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 10)
[    98.634] (**) Option "xkb_rules" "evdev"
[    98.634] (**) Option "xkb_model" "pc105"
[    98.634] (**) Option "xkb_layout" "us"
[    98.635] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event10)
[    98.635] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    98.635] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    98.635] (II) LoadModule: "synaptics"
[    98.635] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    98.635] (II) Module synaptics: vendor="X.Org Foundation"
[    98.635]     compiled for 1.11.3, module version = 1.6.2
[    98.635]     Module class: X.Org XInput Driver
[    98.635]     ABI class: X.Org XInput driver, version 16.0
[    98.635] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[    98.635] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    98.635] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    98.635] (**) Option "Device" "/dev/input/event10"
[    98.644] (II) synaptics: SynPS/2 Synaptics TouchPad: ignoring touch events for semi-multitouch device
[    98.644] (--) synaptics: SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5634
[    98.644] (--) synaptics: SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4598
[    98.644] (--) synaptics: SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    98.644] (--) synaptics: SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[    98.644] (--) synaptics: SynPS/2 Synaptics TouchPad: buttons: left right double triple
[    98.644] (--) synaptics: SynPS/2 Synaptics TouchPad: Vendor 0x2 Product 0x7
[    98.644] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    98.644] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    98.652] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio4/input/input10/event10"
[    98.652] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD, id 11)
[    98.652] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[    98.652] (**) synaptics: SynPS/2 Synaptics TouchPad: MaxSpeed is now 1.75
[    98.652] (**) synaptics: SynPS/2 Synaptics TouchPad: AccelFactor is now 0.038
[    98.652] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    98.652] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[    98.652] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    98.652] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    98.652] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    98.653] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[    98.653] (**) SynPS/2 Synaptics TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"
[    98.654] (II) config/udev: Adding input device HP WMI hotkeys (/dev/input/event9)
[    98.654] (**) HP WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[    98.654] (II) Using input driver 'evdev' for 'HP WMI hotkeys'
[    98.654] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    98.654] (**) HP WMI hotkeys: always reports core events
[    98.654] (**) evdev: HP WMI hotkeys: Device: "/dev/input/event9"
[    98.654] (--) evdev: HP WMI hotkeys: Vendor 0 Product 0
[    98.654] (--) evdev: HP WMI hotkeys: Found keys
[    98.654] (II) evdev: HP WMI hotkeys: Configuring as keyboard
[    98.654] (**) Option "config_info" "udev:/sys/devices/virtual/input/input9/event9"
[    98.655] (II) XINPUT: Adding extended input device "HP WMI hotkeys" (type: KEYBOARD, id 12)
[    98.655] (**) Option "xkb_rules" "evdev"
[    98.655] (**) Option "xkb_model" "pc105"
[    98.655] (**) Option "xkb_layout" "us"
[    98.659] (II) fglrx(0): Restoring Recent Mode via PCS is not supported in RANDR 1.2 capable environments
[    99.080] (II) fglrx(0): EDID vendor "LGD", prod id 754
[    99.080] (II) fglrx(0): Printing DDC gathered Modelines:
[    99.080] (II) fglrx(0): Modeline "1366x768"x0.0   69.30  1366 1402 1442 1480  768 771 776 780 -hsync -vsync (46.8 kHz)
[    99.218] (II) fglrx(0): EDID vendor "LGD", prod id 754
[    99.218] (II) fglrx(0): Printing DDC gathered Modelines:
[    99.218] (II) fglrx(0): Modeline "1366x768"x0.0   69.30  1366 1402 1442 1480  768 771 776 780 -hsync -vsync (46.8 kHz)
[   118.592] (II) fglrx(0): EDID vendor "LGD", prod id 754
[   118.592] (II) fglrx(0): Printing DDC gathered Modelines:
[   118.592] (II) fglrx(0): Modeline "1366x768"x0.0   69.30  1366 1402 1442 1480  768 771 776 780 -hsync -vsync (46.8 kHz)
[   119.201] (II) fglrx(0): EDID vendor "LGD", prod id 754
[   119.201] (II) fglrx(0): Printing DDC gathered Modelines:
[   119.201] (II) fglrx(0): Modeline "1366x768"x0.0   69.30  1366 1402 1442 1480  768 771 776 780 -hsync -vsync (46.8 kHz)
[   119.287] (II) fglrx(0): EDID vendor "LGD", prod id 754
[   119.287] (II) fglrx(0): Printing DDC gathered Modelines:
[   119.287] (II) fglrx(0): Modeline "1366x768"x0.0   69.30  1366 1402 1442 1480  768 771 776 780 -hsync -vsync (46.8 kHz)
[   122.768] (II) XKB: reuse xkmfile /var/lib/xkb/server-03AF3717FF3AB439A4BAABA686CCB40771CDF520.xkm
[   140.073] (II) fglrx(0): EDID vendor "LGD", prod id 754
[   140.073] (II) fglrx(0): Printing DDC gathered Modelines:
[   140.073] (II) fglrx(0): Modeline "1366x768"x0.0   69.30  1366 1402 1442 1480  768 771 776 780 -hsync -vsync (46.8 kHz)
```

---

### Post by DGINSD on 2012-07-20
> **ryanepod said:**
> Do you have the correct video drivers installed? I had a very similar problem when I was still using Ubuntu try changing to the 2d unity desktop and installing the video drivers that should help?

I have the 12.4 Cataylist driver direct from AMD but I'm seriously looking into switching to the open source ones, so long as they don't have the freezing/lockups that the closed source ones are giving me, and they provide at least enough 3D to do desktop effects.

---

### Post by NikTh on 2012-07-20
> **DGINSD said:**
> I have the 12.4 Cataylist driver direct from AMD but I'm seriously looking into switching to the open source ones, so long as they don't have the freezing/lockups that the closed source ones are giving me, and they provide at least enough 3D to do desktop effects.

Hi , 
yeap , its probably fglrx problem , open a terminal(or maybe from VT) and try this command 
```
 sudo aticonfig --*initial*  -f
``` 
see if problem corrected. 

If you have no problems with Open Source drivers (radeon) then... Yes. Switch to open source. 
Thanks

---

### Post by QIII on 2012-07-21
For the switchable graphics, I would try

```
sudo aticonfig --adapter=all --initial
```

followed by a reboot.

---

### Post by DGINSD on 2012-07-21
> **lrcaballero said:**
> Hey, I am from SD too!

Anyways, click on switch user and then re0enter your user and password again and this should do the trick! 

We are experiencing the same issue on my sons pc but when doing what I mentioned above does the trick.

Good luck and Cheers

SD is great I've lived here my whole life.

Thanks for the tip, but it didn't work for me  produced the same result.

Just though this might help the last command I issued  was;
```
sudo startX
```

which  produced some errors can't remember exactly what but I think it tried to restart X a few times.

Also I can CTRL ALT F1 and login to the "David" just fine in tty1 but graphical mode is a no go

---

### Post by DGINSD on 2012-07-21
> **NikTh said:**
> Hi , 
yeap , its probably fglrx problem , open a terminal(or maybe from VT) and try this command 
```
 sudo aticonfig --*initial*  -f
```see if problem corrected. 

If you have no problems with Open Source drivers (radeon) then... Yes. Switch to open source. 
Thanks

Even though I can log in with other graphical accounts just fine?

---

### Post by NikTh on 2012-07-21
> **DGINSD said:**
> Even though I can log in with other graphical accounts just fine?
Hi ,
If the other graphical account has the ability to run  sudo.. then ok. 
But see @QIII's suggest . 
Thanks

---

### Post by DGINSD on 2012-07-21
> **QIII said:**
> For the switchable graphics, I would try

```
sudo aticonfig --adapter=all --initial
```followed by a reboot.

No change, logging in with "David" kicks me right back out to the greeter screen. 

I can log in with the "David" account fine on tty1, and the other accounts will log in graphically and in tty mode just fine.

---

### Post by NikTh on 2012-07-21
> **DGINSD said:**
> No change, logging in with "David" kicks me right back out to the greeter screen. 

I can log in with the "David" account fine on tty1, and the other accounts will log in graphically and in tty mode just fine.

Then you can try to delete ALL your configuration files. Do you want to try this ? 
You will return to an "original" state. 

If yes , login with _your account_ (from tty1) and write this command
```
rm -rf .compiz* .gconf* .config/dconf/ .config/compiz*
```[COLOR=Red]Be careful[/COLOR] to write the command correct . Write it down to a paper if you want (or "screen-shot it" with mobile phone)

[SIZE=3]**EDIT: Try first ****[zombifier25]("http://ubuntuforums.org/member.php?u=1251447")'s suggestion below **[/SIZE]

Thanks

---

### Post by zombifier25 on 2012-07-21
This issue is so common I'm certain this command will fix it:
```
sudo chown yourusername:yourusername ~/.Xauthority 
```
Replace yourusername with your username.

---

### Post by NikTh on 2012-07-21
> **zombifier25 said:**
> This issue is so common I'm certain this command will fix it:
```
sudo chown yourusername:yourusername ~/.Xauthority 
```Replace yourusername with your username.

Ohhhh ... how i missed it ?

=D>

**Question: **[DGINSD]("http://ubuntuforums.org/member.php?u=1246264") i assume that you opened a GUI with sudo command . Didn't you ? 
Example .. sudo nautilus.. 

If you didn't know : It is wrong to open a graphical app (GUI) with sudo command. Use** gksudo **instead.

Thanks

---

### Post by DGINSD on 2012-07-21
> **zombifier25 said:**
> This issue is so common I'm certain this command will fix it:
```
sudo chown yourusername:yourusername ~/.Xauthority 
```Replace yourusername with your username.

Do I need to issue this command logged into the bad account via tty1, or can use any  account with sudo privileges?

---

### Post by NikTh on 2012-07-21
> **DGINSD said:**
> Do I need to issue this command logged into the bad account via tty1, or can use any  account with sudo privileges?

Its better to apply the command** from your account. **
If you apply it from another account , (then you will break the other account too) 
.Xauthority from other account will belong to you , so the other user probably wouldn't be able to login. 
Or 
you must apply it with full path.. e.g home/username/.Xauthority

Its easier and safer to apply the command from your account.

---

### Post by DGINSD on 2012-07-21
Excellent!!! Worked like a charm, Thank you all very much for your help and suggestions, it is very much appreciated.

So I'm assuming the "sudo startX" I issued caused this? Should it of been a "gksudo startX" instead?

A better question is whats the proper way to restart X, without rebooting?

---

### Post by NikTh on 2012-07-21
> **DGINSD said:**
> 
So I'm assuming the "sudo startX" I issued caused this? Should it of been a "gksudo startX" instead?

A better question is whats the proper way to restart X, without rebooting?
My comment and suggestion with gksudo was about graphical app's (like nautilus). 

If you want to restart X-server , let you display manager to handle this.. 
```
 sudo service lightdm restart
``` if you use lightdm (the default Display Manager for Ubuntu 12.04)

And yes , i assume that sudo startx did the damage.

Glad you corrected it. 

Regards

---

### Post by DGINSD on 2012-07-21
Will make a note of it, and again thanks a lot guys.

---

