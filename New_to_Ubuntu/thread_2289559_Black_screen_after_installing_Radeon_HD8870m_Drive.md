---
title: "Black screen after installing Radeon HD8870m Driver"
date: 2015-08-05
forum: New to Ubuntu
---

### Post by Cheolho_Kang on 2015-08-05
[COLOR=#333333]Hello I'm using Samsung New Chronos5(nt570z5e-s78s)[/COLOR]
[COLOR=#333333]This have two graphic card. One is [/COLOR]**Radeon HD 8870M. **The other is **Intel Corporation 3rd Gen Core processor Graphic.**
[COLOR=#333333]
I already installed CCC latest deriver in [/COLOR][COLOR=#333333]AMD/ATI site. and I checked that is correctly installed through command.[/COLOR]** $ lspci | grep VGA & sudo lshw -C video**[COLOR=#333333] 
[/COLOR]Here is the result

[COLOR=#333333]$ lspci | grep VGA & sudo lshw -C video[/COLOR]
[COLOR=#333333]00:02.0 VGA compatible controller: [/COLOR]**Intel Corporation 3rd Gen Core processor Graphics Controller**[COLOR=#333333] (rev 09)[/COLOR]
[COLOR=#333333]*-display [/COLOR]
[COLOR=#333333]description: Display controller[/COLOR]
[COLOR=#333333]product: Venus XT [[/COLOR]**Radeon HD 8870M**[COLOR=#333333]][/COLOR]
[COLOR=#333333]vendor: Advanced Micro Devices, Inc. [AMD/ATI][/COLOR]
[COLOR=#333333]physical id: 0[/COLOR]
[COLOR=#333333]bus info: pci@0000:01:00.0[/COLOR]
[COLOR=#333333]version: 00[/COLOR]
[COLOR=#333333]width: 64 bits[/COLOR]
[COLOR=#333333]clock: 33MHz[/COLOR]
[COLOR=#333333]capabilities: pm pciexpress msi bus_master cap_list rom[/COLOR]
[COLOR=#333333]configuration: driver=fglrx_pci latency=0[/COLOR]
[COLOR=#333333]resources: irq:50 memory:e0000000-efffffff memory:f7d00000-f7d3ffff ioport:e000(size=256) memory:f7d40000-f7d5ffff[/COLOR]
[COLOR=#333333]*-display[/COLOR]
[COLOR=#333333]description: VGA compatible controller[/COLOR]
[COLOR=#333333]product: [/COLOR]**3rd Gen Core processor Graphics Controller**
[COLOR=#333333]vendor: Intel Corporation[/COLOR]
[COLOR=#333333]physical id: 2[/COLOR]
[COLOR=#333333]bus info: pci@0000:00:02.0[/COLOR]
[COLOR=#333333]version: 09[/COLOR]
[COLOR=#333333]width: 64 bits[/COLOR]
[COLOR=#333333]clock: 33MHz[/COLOR]
[COLOR=#333333]capabilities: msi pm vga_controller bus_master cap_list rom[/COLOR]
[COLOR=#333333]configuration: driver=i915 latency=0[/COLOR]
[COLOR=#333333]resources: irq:48 memory:f7800000-f7bfffff memory:d0000000-dfffffff ioport:f000(size=64)[/COLOR]
[COLOR=#333333]
* I printed this log when I turn on the laptop connecting HDMI cable. And I can see through external monitor. laptop monitor is still black screen.[/COLOR]
[COLOR=#333333]** External monitor and laptop monitor is black screen when I turn on the computer unconnecting HDMI cable. And external monitor is still black screen. even if connect the HDMI cable[/COLOR]
[COLOR=#333333]*** Although I can see the laptop monitor through "nomodeset" boot option. But resolution is so low[/COLOR]

[COLOR=#333333]some people said. that is issue cause Graphic driver didn't install correctly. So I installed the two file at the AMD site[/COLOR]
[http://support.amd.com/ko-kr/download/d ... ntu+x86+64]("http://support.amd.com/ko-kr/download/desktop?os=Ubuntu+x86+64")
[COLOR=#333333]AMD Catalyst™ 15.7 Proprietary Ubuntu 14.04 x86_64 Minimal Video Driver for Graphics Accelerators (Non-X Support) <- (fgrlx-core) and[/COLOR]
[COLOR=#333333]AMD Catalyst™ 15.7 Proprietary Ubuntu 14.04 x86_64 Video Driver for Graphics Accelerators[/COLOR]
[COLOR=#333333]
But laptop monitor still black screen when I reboot after typing this command $ [/COLOR]**sudo amdconfig --initial --adapter=all**
[COLOR=#333333]
And another people said black screen issue can solve through changing screen bright. 
but that is not reason.. because I cannot find list of laptop monitor in settings[/COLOR]
[COLOR=#333333]Setting -> Display

Has anyone had this issue before and fixed it?
Happy Regards,
Jacob[/COLOR]

---

### Post by dino99 on 2015-08-05
Install the driver ONLY from the ubuntu archive  (purge the faulty installed one first)

[https://help.ubuntu.com/community/BinaryDriverHowto/AMD](https://help.ubuntu.com/community/BinaryDriverHowto/AMD)

---

### Post by mastablasta on 2015-08-05
it could be that laptops Is not compatible for dual chips. or rather that drivers do not support your hw configuration.

what output does "fglrxinfo" give?

if you can see external monitor maybe something is not configured correctly and it could be that external is recognised as primary monitor or that external plug uses AMD chip. hard to say really. I think xorg file or files would be generated. maybe you could post those. also since you can see the computer - any log files would be good to have. you can see on them what happens on boot and which chips get initialised. xorg.log, system.log etc...

---

### Post by Cheolho_Kang on 2015-08-05
**@[[COLOR=#000000]dino99[/COLOR]]("http://ubuntuforums.org/member.php?u=129712")**[COLOR=#000000]
[/COLOR] 
thank you for your advice.

I tried just before.

$ sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.BAK
$ sudo apt-get remove --purge fglrx*
$ sudo apt-get install linux-headers-genericsudo apt-get install fglrx xvba-va-driver libva-glx1 libva-egl1 vainfo 
$ sudo amdconfig --adapter=all --initial
but this issue still same T.T[B]

@[[COLOR=#000000]mastablasta[/COLOR]]("http://ubuntuforums.org/member.php?u=964486")[/B][COLOR=#000000]
[/COLOR]thank you for your advice
first. I can see the output about "fglrxinfo"
kbright0912@kbright0912-Chronos5:~$ **fglrxinfo**
display: :0  screen: 0
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: AMD Radeon R9 M270X 
OpenGL version string: 4.4.13374 Compatibility Profile Context 15.20.1013


and here is **/etc/X11/xorg.conf**
```
Section "Module"
EndSection

Section "Monitor"
        Identifier   "amd-monitor"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

Section "Device"
        Identifier  "intel"
        Driver      "intel"
        Option      "AccelMethod" "uxa"
        BusID       "PCI:0@0:2:0"
EndSection

Section "Device"
        Identifier  "amd-device"
        Driver      "fglrx"
        BusID       "PCI:1:0:0"
EndSection

Section "Screen"
        Identifier "amd-screen"
        Device     "amd-device"
        Monitor    "amd-monitor"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection
```

and could you please see my xorg.log?? I tried to read this log. but this is so hard. I need some help.. sorry^^;;
[B]
/var/log/Xorg.0.log[/B]
```

[     3.430] 
X.Org X Server 1.15.1
Release Date: 2014-04-13
[     3.430] X Protocol Version 11, Revision 0
[     3.430] Build Operating System: Linux 3.2.0-76-generic x86_64 Ubuntu
[     3.430] Current Operating System: Linux kbright0912-Chronos5 3.13.0-61-generic #100-Ubuntu SMP Wed Jul 29 11:21:34 UTC 2015 x86_64
[     3.430] Kernel command line: BOOT_IMAGE=/vmlinuz-3.13.0-61-generic.efi.signed root=UUID=ec961145-aa22-4407-9dc0-f6d7b9f0ec70 ro splash quiet plymouth:debug=1 vt.handoff=7
[     3.431] Build Date: 12 February 2015  02:49:29PM
[     3.431] xorg-server 2:1.15.1-0ubuntu2.7 (For technical support please see http://www.ubuntu.com/support) 
[     3.431] Current version of pixman: 0.30.2
[     3.431]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[     3.431] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[     3.431] (==) Log file: "/var/log/Xorg.0.log", Time: Wed Aug  5 18:53:18 2015
[     3.434] (==) Using config file: "/etc/X11/xorg.conf"
[     3.434] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[     3.436] (==) ServerLayout "amd-layout"
[     3.436] (**) |-->Screen "amd-screen" (0)
[     3.436] (**) |   |-->Monitor "amd-monitor"
[     3.436] (**) |   |-->Device "amd-device"
[     3.436] (==) Automatically adding devices
[     3.436] (==) Automatically enabling devices
[     3.436] (==) Automatically adding GPU devices
[     3.437] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[     3.437]     Entry deleted from font path.
[     3.437] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[     3.437]     Entry deleted from font path.
[     3.437] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[     3.437]     Entry deleted from font path.
[     3.437] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[     3.437]     Entry deleted from font path.
[     3.437] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[     3.437]     Entry deleted from font path.
[     3.437] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[     3.437] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[     3.437] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[     3.437] (II) Loader magic: 0x7f41527a2d40
[     3.437] (II) Module ABI versions:
[     3.437]     X.Org ANSI C Emulation: 0.4
[     3.437]     X.Org Video Driver: 15.0
[     3.437]     X.Org XInput driver : 20.0
[     3.437]     X.Org Server Extension : 8.0
[     3.437] (II) xfree86: Adding drm device (/dev/dri/card0)
[     3.438] (--) PCI:*(0:0:2:0) 8086:0166:144d:c0e7 rev 9, Mem @ 0xf7800000/4194304, 0xd0000000/268435456, I/O @ 0x0000f000/64
[     3.438] (--) PCI: (0:1:0:0) 1002:6821:144d:c0e7 rev 0, Mem @ 0xe0000000/268435456, 0xf7d00000/262144, I/O @ 0x0000e000/256, BIOS @ 0x????????/131072
[     3.439] Initializing built-in extension Generic Event Extension
[     3.439] Initializing built-in extension SHAPE
[     3.439] Initializing built-in extension MIT-SHM
[     3.439] Initializing built-in extension XInputExtension
[     3.439] Initializing built-in extension XTEST
[     3.439] Initializing built-in extension BIG-REQUESTS
[     3.439] Initializing built-in extension SYNC
[     3.439] Initializing built-in extension XKEYBOARD
[     3.439] Initializing built-in extension XC-MISC
[     3.439] Initializing built-in extension SECURITY
[     3.439] Initializing built-in extension XINERAMA
[     3.439] Initializing built-in extension XFIXES
[     3.439] Initializing built-in extension RENDER
[     3.439] Initializing built-in extension RANDR
[     3.439] Initializing built-in extension COMPOSITE
[     3.439] Initializing built-in extension DAMAGE
[     3.439] Initializing built-in extension MIT-SCREEN-SAVER
[     3.439] Initializing built-in extension DOUBLE-BUFFER
[     3.439] Initializing built-in extension RECORD
[     3.439] Initializing built-in extension DPMS
[     3.439] Initializing built-in extension Present
[     3.439] Initializing built-in extension DRI3
[     3.439] Initializing built-in extension X-Resource
[     3.439] Initializing built-in extension XVideo
[     3.439] Initializing built-in extension XVideo-MotionCompensation
[     3.439] Initializing built-in extension SELinux
[     3.439] Initializing built-in extension XFree86-VidModeExtension
[     3.439] Initializing built-in extension XFree86-DGA
[     3.439] Initializing built-in extension XFree86-DRI
[     3.439] Initializing built-in extension DRI2
[     3.439] (II) "glx" will be loaded by default.
[     3.439] (WW) "xmir" is not to be loaded by default. Skipping.
[     3.439] (II) LoadModule: "glx"
[     3.440] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/extensions/libglx.so
[     3.444] (II) Module glx: vendor="Advanced Micro Devices, Inc."
[     3.444]     compiled for 6.9.0, module version = 1.0.0
[     3.444] Loading extension GLX
[     3.444] (II) LoadModule: "fglrx"
[     3.445] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/drivers/fglrx_drv.so
[     3.500] (II) Module fglrx: vendor="FireGL - AMD Technologies Inc."
[     3.500]     compiled for 1.4.99.906, module version = 15.20.2
[     3.500]     Module class: X.Org Video Driver
[     3.500] (II) Loading sub module "fglrxdrm"
[     3.500] (II) LoadModule: "fglrxdrm"
[     3.500] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/linux/libfglrxdrm.so
[     3.503] (II) Module fglrxdrm: vendor="FireGL - AMD Technologies Inc."
[     3.503]     compiled for 1.4.99.906, module version = 15.20.2
[     3.503] (II) AMD Proprietary Linux Driver Version Identifier:15.20.2
[     3.503] (II) AMD Proprietary Linux Driver Release Identifier: UNSUPPORTED-15.20.1013               
[     3.503] (II) AMD Proprietary Linux Driver Build Date: Feb 27 2015 03:27:32
[     3.503] (++) using VT number 7


[     3.503] (WW) Falling back to old probe method for fglrx
[     3.525] (II) Loading PCS database from /etc/ati/amdpcsdb /etc/ati/amdpcsdb.default
[     3.527] ukiDynamicMajor: found major device number 251
[     3.527] ukiDynamicMajor: found major device number 251
[     3.527] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[     3.527] ukiOpenDevice: node name is /dev/ati/card0
[     3.527] ukiOpenDevice: open result is 9, (OK)
[     4.973] ukiOpenByBusid: ukiOpenMinor returns 9
[     4.973] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[     4.976] (--) Chipset Supported AMD Graphics Processor (0x6821) found
[     4.977] (II) fglrx: intel VGA device detected, load intel driver.
[     4.977] (II) LoadModule: "intel"
[     4.977] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[     4.984] (II) Module intel: vendor="X.Org Foundation"
[     4.984]     compiled for 1.15.1, module version = 2.99.917
[     4.984]     Module class: X.Org Video Driver
[     4.984]     ABI class: X.Org Video Driver, version 15.0
[     4.984] (II) fglrx(0): pEnt->device->identifier=0x7f415403dfe0
[     4.985] (II) intel(1): pEnt->device->identifier=(nil)
[     4.985] (EE) Screen 1 deleted because of no matching config section.
[     4.985] (II) UnloadModule: "intel"
[     4.985] (II) fglrx(0): === [xdl_xs115_atiddxPreInit] === begin
[     4.985] (II) fglrx(0): FB driver is enabled
[     4.985] (II) fglrx(0): PowerXpress: Discrete GPU is selected.
[     5.529] (**) fglrx(0): Depth 24, (--) framebuffer bpp 32
[     5.529] (==) fglrx(0): RGB weight 888
[     5.529] (==) fglrx(0): Default visual is TrueColor
[     5.529] (**) fglrx(0): Option "Tiling" "off"
[     5.529] (**) fglrx(0): Option "LinearFramebuffer" "on"
[     5.529] (--) fglrx(0): Integrated Graphics Chipset: Intel(R) HD Graphics 4000
[     5.529] (**) fglrx(0): Relaxed fencing enabled
[     5.529] (**) fglrx(0): Wait on SwapBuffers? enabled
[     5.529] (**) fglrx(0): Triple buffering? enabled
[     5.529] (**) fglrx(0): Framebuffer linear
[     5.529] (**) fglrx(0): Pixmaps linear
[     5.530] (**) fglrx(0): 3D buffers tiled
[     5.530] (**) fglrx(0): SwapBuffers wait enabled
[     5.530] (==) fglrx(0): video overlay key set to 0x101fe
[     5.531] (II) fglrx(0): Output VGA1 using monitor section amd-monitor
[     5.581] (II) fglrx(0): Output HDMI1 has no monitor section
[     5.608] (II) fglrx(0): Output DP1 has no monitor section
[     5.608] (II) fglrx(0): EDID for output VGA1
[     5.658] (II) fglrx(0): EDID for output HDMI1
[     5.658] (II) fglrx(0): Manufacturer: DEL  Model: a08e  Serial#: 810042956
[     5.658] (II) fglrx(0): Year: 2013  Week: 38
[     5.658] (II) fglrx(0): EDID Version: 1.3
[     5.658] (II) fglrx(0): Digital Display Input
[     5.658] (II) fglrx(0): Max Image Size [cm]: horiz.: 60  vert.: 34
[     5.658] (II) fglrx(0): Gamma: 2.20
[     5.658] (II) fglrx(0): DPMS capabilities: StandBy Suspend Off
[     5.658] (II) fglrx(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[     5.658] (II) fglrx(0): First detailed timing is preferred mode
[     5.658] (II) fglrx(0): redX: 0.640 redY: 0.338   greenX: 0.315 greenY: 0.623
[     5.658] (II) fglrx(0): blueX: 0.151 blueY: 0.063   whiteX: 0.313 whiteY: 0.329
[     5.658] (II) fglrx(0): Supported established timings:
[     5.658] (II) fglrx(0): 720x400@70Hz
[     5.658] (II) fglrx(0): 640x480@60Hz
[     5.658] (II) fglrx(0): 640x480@75Hz
[     5.658] (II) fglrx(0): 800x600@60Hz
[     5.658] (II) fglrx(0): 800x600@75Hz
[     5.658] (II) fglrx(0): 1024x768@60Hz
[     5.658] (II) fglrx(0): 1024x768@75Hz
[     5.658] (II) fglrx(0): 1280x1024@75Hz
[     5.658] (II) fglrx(0): Manufacturer's mask: 0
[     5.658] (II) fglrx(0): Supported standard timings:
[     5.658] (II) fglrx(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[     5.658] (II) fglrx(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[     5.658] (II) fglrx(0): #2: hsize: 1920  vsize 1080  refresh: 60  vid: 49361
[     5.658] (II) fglrx(0): Supported detailed timing:
[     5.658] (II) fglrx(0): clock: 148.5 MHz   Image Size:  598 x 336 mm
[     5.658] (II) fglrx(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[     5.658] (II) fglrx(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
[     5.658] (II) fglrx(0): Serial No: P7D0G39I0HFL
[     5.658] (II) fglrx(0): Monitor name: DELL S2740L
[     5.658] (II) fglrx(0): Ranges: V min: 56 V max: 76 Hz, H min: 30 H max: 83 kHz, PixClock max 175 MHz
[     5.658] (II) fglrx(0): Supported detailed timing:
[     5.658] (II) fglrx(0): clock: 148.5 MHz   Image Size:  598 x 336 mm
[     5.658] (II) fglrx(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[     5.658] (II) fglrx(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
[     5.658] (II) fglrx(0): Supported detailed timing:
[     5.658] (II) fglrx(0): clock: 74.2 MHz   Image Size:  598 x 336 mm
[     5.658] (II) fglrx(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[     5.658] (II) fglrx(0): v_active: 540  v_sync: 542  v_sync_end 547 v_blanking: 562 v_border: 0
[     5.658] (II) fglrx(0): Supported detailed timing:
[     5.658] (II) fglrx(0): clock: 74.2 MHz   Image Size:  598 x 336 mm
[     5.658] (II) fglrx(0): h_active: 1280  h_sync: 1390  h_sync_end 1430 h_blank_end 1650 h_border: 0
[     5.658] (II) fglrx(0): v_active: 720  v_sync: 725  v_sync_end 730 v_blanking: 750 v_border: 0
[     5.658] (II) fglrx(0): Supported detailed timing:
[     5.658] (II) fglrx(0): clock: 27.0 MHz   Image Size:  598 x 336 mm
[     5.658] (II) fglrx(0): h_active: 720  h_sync: 736  h_sync_end 798 h_blank_end 858 h_border: 0
[     5.658] (II) fglrx(0): v_active: 480  v_sync: 489  v_sync_end 495 v_blanking: 525 v_border: 0
[     5.658] (II) fglrx(0): Number of EDID sections to follow: 1
[     5.658] (II) fglrx(0): EDID (in hex):
[     5.658] (II) fglrx(0):     00ffffffffffff0010ac8ea04c464830
[     5.658] (II) fglrx(0):     26170103803c2278eaeed5a356509f26
[     5.658] (II) fglrx(0):     105054a54b00714f8180d1c001010101
[     5.658] (II) fglrx(0):     010101010101023a801871382d40582c
[     5.658] (II) fglrx(0):     450056502100001e000000ff00503744
[     5.658] (II) fglrx(0):     30473339493048464c0a000000fc0044
[     5.658] (II) fglrx(0):     454c4c2053323734304c0a20000000fd
[     5.658] (II) fglrx(0):     00384c1e5311000a202020202020017d
[     5.658] (II) fglrx(0):     02031ff14c9005040302071601141f12
[     5.658] (II) fglrx(0):     132309070765030c0010008301000002
[     5.658] (II) fglrx(0):     3a801871382d40582c45005650210000
[     5.658] (II) fglrx(0):     1e011d8018711c1620582c2500565021
[     5.658] (II) fglrx(0):     00009e011d007251d01e206e28550056
[     5.658] (II) fglrx(0):     502100001e8c0ad08a20e02d10103e96
[     5.658] (II) fglrx(0):     00565021000018000000000000000000
[     5.658] (II) fglrx(0):     0000000000000000000000000000007b
[     5.658] (II) fglrx(0): Printing probed modes for output HDMI1
[     5.658] (II) fglrx(0): Modeline "1920x1080"x60.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[     5.658] (II) fglrx(0): Modeline "1920x1080"x50.0  148.50  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[     5.658] (II) fglrx(0): Modeline "1920x1080"x59.9  148.35  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.4 kHz e)
[     5.658] (II) fglrx(0): Modeline "1920x1080i"x60.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz e)
[     5.658] (II) fglrx(0): Modeline "1920x1080i"x50.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz e)
[     5.658] (II) fglrx(0): Modeline "1920x1080i"x59.9   74.18  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.7 kHz e)
[     5.658] (II) fglrx(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[     5.658] (II) fglrx(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[     5.659] (II) fglrx(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[     5.659] (II) fglrx(0): Modeline "1280x720"x60.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[     5.659] (II) fglrx(0): Modeline "1280x720"x50.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz e)
[     5.659] (II) fglrx(0): Modeline "1280x720"x59.9   74.18  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[     5.659] (II) fglrx(0): Modeline "1440x576i"x50.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz e)
[     5.659] (II) fglrx(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz e)
[     5.659] (II) fglrx(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[     5.659] (II) fglrx(0): Modeline "1440x480i"x60.0   27.03  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.8 kHz e)
[     5.659] (II) fglrx(0): Modeline "1440x480i"x59.9   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz e)
[     5.659] (II) fglrx(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[     5.659] (II) fglrx(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[     5.659] (II) fglrx(0): Modeline "720x576"x50.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz e)
[     5.659] (II) fglrx(0): Modeline "720x480"x60.0   27.03  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
[     5.659] (II) fglrx(0): Modeline "720x480"x59.9   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
[     5.659] (II) fglrx(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[     5.659] (II) fglrx(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[     5.659] (II) fglrx(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[     5.659] (II) fglrx(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[     5.684] (II) fglrx(0): EDID for output DP1
[     5.684] (II) fglrx(0): Output VGA1 disconnected
[     5.684] (II) fglrx(0): Output HDMI1 connected
[     5.684] (II) fglrx(0): Output DP1 disconnected
[     5.684] (II) fglrx(0): Using exact sizes for initial modes
[     5.684] (II) fglrx(0): Output HDMI1 using initial mode 1920x1080
[     5.684] (II) fglrx(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[     5.684] (II) fglrx(0): Kernel page flipping support detected, enabling
[     5.684] (==) fglrx(0): DPI set to (96, 96)
[     5.684] (II) Loading sub module "fb"
[     5.684] (II) LoadModule: "fb"
[     5.684] (II) Loading /usr/lib/xorg/modules/libfb.so
[     5.685] (II) Module fb: vendor="X.Org Foundation"
[     5.685]     compiled for 1.15.1, module version = 1.0.0
[     5.685]     ABI class: X.Org ANSI C Emulation, version 0.4
[     5.685] (II) Loading sub module "dri2"
[     5.685] (II) LoadModule: "dri2"
[     5.685] (II) Module "dri2" already built-in
[     5.685] (**) fglrx(0): Depth 24, (--) framebuffer bpp 32
[     5.685] (II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[     5.685] (==) fglrx(0): Default visual is TrueColor
[     5.685] (**) fglrx(0): Option "DPMS" "true"
[     5.685] (==) fglrx(0): RGB weight 888
[     5.685] (II) fglrx(0): Using 8 bits per RGB 
[     5.685] (==) fglrx(0): Buffer Tiling is ON
[     5.685] (II) Loading sub module "fglrxdrm"
[     5.685] (II) LoadModule: "fglrxdrm"
[     5.685] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/linux/libfglrxdrm.so
[     5.685] (II) Module fglrxdrm: vendor="FireGL - AMD Technologies Inc."
[     5.685]     compiled for 1.4.99.906, module version = 15.20.2
[     5.687] ukiDynamicMajor: found major device number 251
[     5.687] ukiDynamicMajor: found major device number 251
[     5.687] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[     5.687] ukiOpenDevice: node name is /dev/ati/card0
[     5.687] ukiOpenDevice: open result is 12, (OK)
[     5.687] ukiOpenByBusid: ukiOpenMinor returns 12
[     5.687] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[     5.687] (**) fglrx(0): NoAccel = NO
[     5.687] (**) fglrx(0): AMD 2D Acceleration Architecture enabled
[     5.687] (--) fglrx(0): Chipset: "AMD Radeon R9 M270X " (Chipset = 0x6821)
[     5.687] (--) fglrx(0): (PciSubVendor = 0x144d, PciSubDevice = 0xc0e7)
[     5.687] (==) fglrx(0): board vendor info: third party graphics adapter - NOT original AMD
[     5.687] (--) fglrx(0): Linear framebuffer (phys) at 0xe0000000
[     5.687] (--) fglrx(0): MMIO registers at 0xf7d00000
[     5.687] (--) fglrx(0): I/O port at 0x0000e000
[     5.687] (==) fglrx(0): ROM-BIOS at 0x000c0000
[     5.688] (II) fglrx(0): AC Adapter is used
[     5.688] (II) fglrx(0): AMD Video BIOS revision 9 or later detected
[     5.688] (--) fglrx(0): Video RAM: 2097152 kByte, Type: GDDR5
[     5.688] (II) fglrx(0): PCIE card detected
[     5.688] (--) fglrx(0): Using per-process page tables (PPPT) as GART.
[     5.688] (WW) fglrx(0): board is an unknown third party board, chipset is supported
[     5.761] (II) fglrx(0): [FB] MC range(MCFBBase = 0xf400000000, MCFBSize = 0x80000000)
[     5.761] (II) fglrx(0): RandR 1.2 support is enabled!
[     5.761] (II) fglrx(0): RandR 1.2 rotation support is enabled!
[     5.761] (II) Loading sub module "fb"
[     5.761] (II) LoadModule: "fb"
[     5.761] (II) Loading /usr/lib/xorg/modules/libfb.so
[     5.761] (II) Module fb: vendor="X.Org Foundation"
[     5.761]     compiled for 1.15.1, module version = 1.0.0
[     5.761]     ABI class: X.Org ANSI C Emulation, version 0.4
[     5.761] (II) fglrx(0): EDID Management option: EDID Management is enabled
[     5.761] (II) Loading sub module "ddc"
[     5.761] (II) LoadModule: "ddc"
[     5.761] (II) Module "ddc" already built-in
[     5.794] (II) fglrx(0): Eyefinity capable adapter detected.
[     5.794] (II) fglrx(0): Adapter AMD Radeon R9 M270X  has 6 configurable heads and 0 displays connected.
[     5.794] (==) fglrx(0):  PseudoColor visuals disabled
[     5.794] (II) Loading sub module "ramdac"
[     5.794] (II) LoadModule: "ramdac"
[     5.794] (II) Module "ramdac" already built-in
[     5.794] (==) fglrx(0): NoDRI = NO
[     5.794] (==) fglrx(0): Capabilities: 0x00000000
[     5.794] (==) fglrx(0): CapabilitiesEx: 0x00000000
[     5.794] (==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
[     5.794] (==) fglrx(0): UseFastTLS=0
[     5.794] (II) fglrx(0): TearFreeDesktop is not supported on PowerXpress systems currently.
[     5.794] (--) Depth 24 pixmap format is 32 bpp
[     5.795] (II) LoadModule: "glesx"
[     5.795] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/glesx.so
[     5.809] (II) Module glesx: vendor="X.Org Foundation"
[     5.809]     compiled for 1.4.99.906, module version = 1.0.0
[     5.809] Loading extension GLESX
[     5.811] (II) fglrx(0): Allocated new frame buffer 1920x1080 stride 7680, untiled
[     5.813] (II) UXA(0): Driver registered support for the following operations:
[     5.813] (II)         solid
[     5.813] (II)         copy
[     5.813] (II)         composite (RENDER acceleration)
[     5.813] (II)         put_image
[     5.813] (II)         get_image
[     5.813] (II) fglrx(0): [DRI2] Setup complete
[     5.813] (II) fglrx(0): [DRI2]   DRI driver: i965
[     5.813] (II) fglrx(0): [DRI2]   VDPAU driver: va_gl
[     5.813] (==) fglrx(0): Backing store enabled
[     5.813] (==) fglrx(0): Silken mouse enabled
[     5.813] (II) fglrx(0): Initializing HW Cursor
[     5.813] (II) fglrx(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[     5.813] (**) fglrx(0): DPMS enabled
[     5.813] (==) fglrx(0): Intel XvMC decoder enabled
[     5.813] (II) fglrx(0): Set up textured video
[     5.813] (II) fglrx(0): [XvMC] xvmc_vld driver initialized.
[     5.813] (II) fglrx(0): DRI2: Enabled
[     5.813] (II) fglrx(0): DRI3: Disabled
[     5.813] (WW) fglrx(0): Option "VendorName" is not used
[     5.813] (WW) fglrx(0): Option "ModelName" is not used
[     5.813] (WW) fglrx(0): Option "Shadow" is not used
[     5.813] (WW) fglrx(0): Option "Tiling" is not used
[     5.813] (WW) fglrx(0): Option "LinearFramebuffer" is not used
[     5.813] (==) fglrx(0): hotplug detection: "enabled"
[     5.840] Loading extension ATIFGLRXDRI
[     5.840] (II) fglrx(0): doing swlDriScreenInit
[     5.840] (II) fglrx(0): swlDriScreenInit for fglrx driver
[     5.840] ukiDynamicMajor: found major device number 251
[     5.840] ukiDynamicMajor: found major device number 251
[     5.840] ukiDynamicMajor: found major device number 251
[     5.840] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[     5.840] ukiOpenDevice: node name is /dev/ati/card0
[     5.840] ukiOpenDevice: open result is 14, (OK)
[     5.840] ukiOpenByBusid: ukiOpenMinor returns 14
[     5.840] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[     5.840] (II) fglrx(0): [uki] DRM interface version 1.0
[     5.840] (II) fglrx(0): [uki] created "fglrx" driver at busid "PCI:1:0:0"
[     5.840] (II) fglrx(0): [uki] added 8192 byte SAREA at 0x2000
[     5.840] (II) fglrx(0): [uki] mapped SAREA 0x2000 to 0x7f414b644000
[     5.840] (II) fglrx(0): [uki] framebuffer handle = 0x3000
[     5.840] (II) fglrx(0): [uki] added 1 reserved context for kernel
[     5.840] (II) fglrx(0): swlDriScreenInit done
[     5.840] (II) fglrx(0): Kernel Module Version Information:
[     5.840] (II) fglrx(0):     Name: fglrx
[     5.840] (II) fglrx(0):     Version: 15.20.2
[     5.840] (II) fglrx(0):     Date: Feb 27 2015
[     5.840] (II) fglrx(0):     Desc: AMD FireGL DRM kernel module
[     5.840] (II) fglrx(0): Kernel Module version matches driver.
[     5.840] (II) fglrx(0): Kernel Module Build Time Information:
[     5.840] (II) fglrx(0):     Build-Kernel UTS_RELEASE:        3.13.0-61-generic
[     5.840] (II) fglrx(0):     Build-Kernel MODVERSIONS:        yes
[     5.840] (II) fglrx(0):     Build-Kernel __SMP__:            yes
[     5.840] (II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
[     5.840] (II) fglrx(0): [uki] register handle = 0x00004000
[     5.843] (II) fglrx(0): DRI initialization successfull
[     5.843] (II) fglrx(0): FBADPhys: 0xf400000000 FBMappedSize: 0x010e0000
[     5.844] (II) fglrx(0): Intel display surface mc addr for AMD: ffe8117000
[     5.844] (==) fglrx(0): Backing store enabled
[     5.844] Loading extension FGLRXEXTENSION
[     5.844] (**) fglrx(0): DPMS enabled
[     5.844] (II) fglrx(0): Initialized in-driver Xinerama extension
[     5.844] (**) fglrx(0): Textured Video is enabled.
[     5.845] (II) fglrx(0): GLESX enableFlags = 9040
[     5.845] (II) fglrx(0): GLESX is enabled
[     5.845] (II) LoadModule: "amdxmm"
[     5.845] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/amdxmm.so
[     5.846] (II) Module amdxmm: vendor="X.Org Foundation"
[     5.846]     compiled for 1.4.99.906, module version = 2.0.0
[     5.847] Loading extension AMDXVOPL
[     5.847] Loading extension AMDXVBA
[     5.847] XvScreenInit: screen devPrivates ptr non-NULL before init
[     5.848] (II) fglrx(0): UVD feature is enabled(II) fglrx(0): 
[     5.855] (II) fglrx(0): Enable composite support successfully
[     5.855] (WW) fglrx(0): Option "VendorName" is not used
[     5.855] (WW) fglrx(0): Option "ModelName" is not used
[     5.855] (WW) fglrx(0): Option "Shadow" is not used
[     5.855] (WW) fglrx(0): Option "Tiling" is not used
[     5.855] (WW) fglrx(0): Option "LinearFramebuffer" is not used
[     5.855] (II) fglrx(0): X context handle = 0x1
[     5.855] (II) fglrx(0): [DRI] installation complete
[     5.859] (--) RandR disabled
[     5.863] (II) SELinux: Disabled on system
[     5.864] ukiDynamicMajor: found major device number 251
[     5.864] ukiDynamicMajor: found major device number 251
[     5.864] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[     5.864] ukiOpenDevice: node name is /dev/ati/card0
[     5.864] ukiOpenDevice: open result is 15, (OK)
[     5.864] ukiOpenByBusid: ukiOpenMinor returns 15
[     5.864] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[     5.864] (EE) AIGLX error: failed to open /usr/X11R6/lib64/modules/dri/fglrx_dri.so, error[/usr/X11R6/lib64/modules/dri/fglrx_dri.so: cannot open shared object file: No such file or directory]
[     5.864] (EE) AIGLX error: failed to open /usr/lib64/dri/fglrx_dri.so, error[/usr/lib64/dri/fglrx_dri.so: cannot open shared object file: No such file or directory]
[     5.864] (EE) AIGLX error: failed to open /usr/X11R6/lib/modules/dri/fglrx_dri.so, error[/usr/X11R6/lib/modules/dri/fglrx_dri.so: cannot open shared object file: No such file or directory]
[     5.887] ukiDynamicMajor: found major device number 251
[     5.887] ukiDynamicMajor: found major device number 251
[     5.887] ukiDynamicMajor: found major device number 251
[     5.887] ukiOpenDevice: node name is /dev/ati/card0
[     5.887] ukiOpenDevice: open result is 16, (OK)
[     5.887] ukiGetBusid returned 'PCI:1:0:0'
[     5.887] ukiOpenDevice: node name is /dev/ati/card1
[     5.887] ukiOpenDevice: open result is -1, (No such device)
[     5.887] ukiOpenDevice: open result is -1, (No such device)
[     5.887] ukiOpenDevice: Open failed
[     5.887] ukiOpenDevice: node name is /dev/ati/card2
[     5.887] ukiOpenDevice: open result is -1, (No such device)
[     5.887] ukiOpenDevice: open result is -1, (No such device)
[     5.887] ukiOpenDevice: Open failed
[     5.887] ukiOpenDevice: node name is /dev/ati/card3
[     5.887] ukiOpenDevice: open result is -1, (No such device)
[     5.887] ukiOpenDevice: open result is -1, (No such device)
[     5.887] ukiOpenDevice: Open failed
[     5.887] ukiOpenDevice: node name is /dev/ati/card4
[     5.887] ukiOpenDevice: open result is -1, (No such device)
[     5.887] ukiOpenDevice: open result is -1, (No such device)
[     5.887] ukiOpenDevice: Open failed
[     5.887] ukiOpenDevice: node name is /dev/ati/card5
[     5.887] ukiOpenDevice: open result is -1, (No such device)
[     5.887] ukiOpenDevice: open result is -1, (No such device)
[     5.887] ukiOpenDevice: Open failed
[     5.887] ukiOpenDevice: node name is /dev/ati/card6
[     5.887] ukiOpenDevice: open result is -1, (No such device)
[     5.887] ukiOpenDevice: open result is -1, (No such device)
[     5.887] ukiOpenDevice: Open failed
[     5.887] ukiOpenDevice: node name is /dev/ati/card7
[     5.887] ukiOpenDevice: open result is -1, (No such device)
[     5.887] ukiOpenDevice: open result is -1, (No such device)
[     5.887] ukiOpenDevice: Open failed
[     5.887] ukiOpenDevice: node name is /dev/ati/card8
[     5.887] ukiOpenDevice: open result is -1, (No such device)
[     5.887] ukiOpenDevice: open result is -1, (No such device)
[     5.887] ukiOpenDevice: Open failed
[     5.887] ukiOpenDevice: node name is /dev/ati/card9
[     5.887] ukiOpenDevice: open result is -1, (No such device)
[     5.887] ukiOpenDevice: open result is -1, (No such device)
[     5.887] ukiOpenDevice: Open failed
[     5.887] ukiOpenDevice: node name is /dev/ati/card10
[     5.887] ukiOpenDevice: open result is -1, (No such device)
[     5.887] ukiOpenDevice: open result is -1, (No such device)
[     5.887] ukiOpenDevice: Open failed
[     5.887] ukiOpenDevice: node name is /dev/ati/card11
[     5.887] ukiOpenDevice: open result is -1, (No such device)
[     5.887] ukiOpenDevice: open result is -1, (No such device)
[     5.887] ukiOpenDevice: Open failed
[     5.887] ukiOpenDevice: node name is /dev/ati/card12
[     5.887] ukiOpenDevice: open result is -1, (No such device)
[     5.887] ukiOpenDevice: open result is -1, (No such device)
[     5.887] ukiOpenDevice: Open failed
[     5.887] ukiOpenDevice: node name is /dev/ati/card13
[     5.887] ukiOpenDevice: open result is -1, (No such device)
[     5.887] ukiOpenDevice: open result is -1, (No such device)
[     5.887] ukiOpenDevice: Open failed
[     5.887] ukiOpenDevice: node name is /dev/ati/card14
[     5.887] ukiOpenDevice: open result is -1, (No such device)
[     5.887] ukiOpenDevice: open result is -1, (No such device)
[     5.887] ukiOpenDevice: Open failed
[     5.887] ukiOpenDevice: node name is /dev/ati/card15
[     5.887] ukiOpenDevice: open result is -1, (No such device)
[     5.887] ukiOpenDevice: open result is -1, (No such device)
[     5.887] ukiOpenDevice: Open failed
[     5.887] ukiDynamicMajor: found major device number 251
[     5.887] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[     5.887] ukiOpenDevice: node name is /dev/ati/card0
[     5.887] ukiOpenDevice: open result is 16, (OK)
[     5.887] ukiOpenByBusid: ukiOpenMinor returns 16
[     5.887] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[     6.005] (II) AIGLX: Loaded and initialized OpenGL driver(II) GLX: Initialized DRI GL provider for screen 0
[     6.005] ukiDynamicMajor: found major device number 251
[     6.005] ukiDynamicMajor: found major device number 251
[     6.005] ukiDynamicMajor: found major device number 251
[     6.005] ukiOpenDevice: node name is /dev/ati/card0
[     6.005] ukiOpenDevice: open result is 17, (OK)
[     6.005] ukiGetBusid returned 'PCI:1:0:0'
[     6.005] ukiOpenDevice: node name is /dev/ati/card1
[     6.005] ukiOpenDevice: open result is -1, (No such device)
[     6.005] ukiOpenDevice: open result is -1, (No such device)
[     6.005] ukiOpenDevice: Open failed
[     6.005] ukiOpenDevice: node name is /dev/ati/card2
[     6.005] ukiOpenDevice: open result is -1, (No such device)
[     6.005] ukiOpenDevice: open result is -1, (No such device)
[     6.005] ukiOpenDevice: Open failed
[     6.005] ukiOpenDevice: node name is /dev/ati/card3
[     6.005] ukiOpenDevice: open result is -1, (No such device)
[     6.005] ukiOpenDevice: open result is -1, (No such device)
[     6.005] ukiOpenDevice: Open failed
[     6.005] ukiOpenDevice: node name is /dev/ati/card4
[     6.005] ukiOpenDevice: open result is -1, (No such device)
[     6.005] ukiOpenDevice: open result is -1, (No such device)
[     6.005] ukiOpenDevice: Open failed
[     6.005] ukiOpenDevice: node name is /dev/ati/card5
[     6.005] ukiOpenDevice: open result is -1, (No such device)
[     6.005] ukiOpenDevice: open result is -1, (No such device)
[     6.005] ukiOpenDevice: Open failed
[     6.005] ukiOpenDevice: node name is /dev/ati/card6
[     6.005] ukiOpenDevice: open result is -1, (No such device)
[     6.005] ukiOpenDevice: open result is -1, (No such device)
[     6.005] ukiOpenDevice: Open failed
[     6.005] ukiOpenDevice: node name is /dev/ati/card7
[     6.005] ukiOpenDevice: open result is -1, (No such device)
[     6.005] ukiOpenDevice: open result is -1, (No such device)
[     6.005] ukiOpenDevice: Open failed
[     6.005] ukiOpenDevice: node name is /dev/ati/card8
[     6.005] ukiOpenDevice: open result is -1, (No such device)
[     6.005] ukiOpenDevice: open result is -1, (No such device)
[     6.005] ukiOpenDevice: Open failed
[     6.005] ukiOpenDevice: node name is /dev/ati/card9
[     6.005] ukiOpenDevice: open result is -1, (No such device)
[     6.005] ukiOpenDevice: open result is -1, (No such device)
[     6.005] ukiOpenDevice: Open failed
[     6.005] ukiOpenDevice: node name is /dev/ati/card10
[     6.005] ukiOpenDevice: open result is -1, (No such device)
[     6.005] ukiOpenDevice: open result is -1, (No such device)
[     6.005] ukiOpenDevice: Open failed
[     6.005] ukiOpenDevice: node name is /dev/ati/card11
[     6.005] ukiOpenDevice: open result is -1, (No such device)
[     6.005] ukiOpenDevice: open result is -1, (No such device)
[     6.005] ukiOpenDevice: Open failed
[     6.005] ukiOpenDevice: node name is /dev/ati/card12
[     6.005] ukiOpenDevice: open result is -1, (No such device)
[     6.005] ukiOpenDevice: open result is -1, (No such device)
[     6.005] ukiOpenDevice: Open failed
[     6.005] ukiOpenDevice: node name is /dev/ati/card13
[     6.005] ukiOpenDevice: open result is -1, (No such device)
[     6.005] ukiOpenDevice: open result is -1, (No such device)
[     6.005] ukiOpenDevice: Open failed
[     6.005] ukiOpenDevice: node name is /dev/ati/card14
[     6.005] ukiOpenDevice: open result is -1, (No such device)
[     6.005] ukiOpenDevice: open result is -1, (No such device)
[     6.005] ukiOpenDevice: Open failed
[     6.005] ukiOpenDevice: node name is /dev/ati/card15
[     6.005] ukiOpenDevice: open result is -1, (No such device)
[     6.005] ukiOpenDevice: open result is -1, (No such device)
[     6.005] ukiOpenDevice: Open failed
[     6.005] ukiDynamicMajor: found major device number 251
[     6.005] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[     6.005] ukiOpenDevice: node name is /dev/ati/card0
[     6.005] ukiOpenDevice: open result is 17, (OK)
[     6.005] ukiOpenByBusid: ukiOpenMinor returns 17
[     6.005] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[     6.041] (II) fglrx(0): OverDrive5 Detected!
[     6.048] (II) fglrx(0): Setting screen physical size to 508 x 285
[     6.063] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[     6.065] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[     6.065] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[     6.065] (II) LoadModule: "evdev"
[     6.065] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     6.067] (II) Module evdev: vendor="X.Org Foundation"
[     6.067]     compiled for 1.15.0, module version = 2.8.2
[     6.067]     Module class: X.Org XInput Driver
[     6.067]     ABI class: X.Org XInput driver, version 20.0
[     6.067] (II) Using input driver 'evdev' for 'Power Button'
[     6.067] (**) Power Button: always reports core events
[     6.067] (**) evdev: Power Button: Device: "/dev/input/event2"
[     6.067] (--) evdev: Power Button: Vendor 0 Product 0x1
[     6.067] (--) evdev: Power Button: Found keys
[     6.067] (II) evdev: Power Button: Configuring as keyboard
[     6.067] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[     6.067] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[     6.067] (**) Option "xkb_rules" "evdev"
[     6.067] (**) Option "xkb_model" "pc105"
[     6.067] (**) Option "xkb_layout" "kr"
[     6.067] (**) Option "xkb_variant" "kr104"
[     6.068] (II) XKB: reuse xkmfile /var/lib/xkb/server-ECB16C83A536A4391DD7C11C6204272462B2FEE2.xkm
[     6.068] (II) config/udev: Adding input device Video Bus (/dev/input/event8)
[     6.068] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[     6.068] (II) Using input driver 'evdev' for 'Video Bus'
[     6.068] (**) Video Bus: always reports core events
[     6.068] (**) evdev: Video Bus: Device: "/dev/input/event8"
[     6.069] (--) evdev: Video Bus: Vendor 0 Product 0x6
[     6.069] (--) evdev: Video Bus: Found keys
[     6.069] (II) evdev: Video Bus: Configuring as keyboard
[     6.069] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:01/input/input9/event8"
[     6.069] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[     6.069] (**) Option "xkb_rules" "evdev"
[     6.069] (**) Option "xkb_model" "pc105"
[     6.069] (**) Option "xkb_layout" "kr"
[     6.069] (**) Option "xkb_variant" "kr104"
[     6.069] (II) config/udev: Adding input device Video Bus (/dev/input/event7)
[     6.069] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[     6.069] (II) Using input driver 'evdev' for 'Video Bus'
[     6.069] (**) Video Bus: always reports core events
[     6.069] (**) evdev: Video Bus: Device: "/dev/input/event7"
[     6.069] (--) evdev: Video Bus: Vendor 0 Product 0x6
[     6.069] (--) evdev: Video Bus: Found keys
[     6.069] (II) evdev: Video Bus: Configuring as keyboard
[     6.069] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:0e/LNXVIDEO:00/input/input8/event7"
[     6.069] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 8)
[     6.069] (**) Option "xkb_rules" "evdev"
[     6.069] (**) Option "xkb_model" "pc105"
[     6.069] (**) Option "xkb_layout" "kr"
[     6.069] (**) Option "xkb_variant" "kr104"
[     6.069] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[     6.069] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[     6.069] (II) Using input driver 'evdev' for 'Power Button'
[     6.069] (**) Power Button: always reports core events
[     6.069] (**) evdev: Power Button: Device: "/dev/input/event1"
[     6.069] (--) evdev: Power Button: Vendor 0 Product 0x1
[     6.069] (--) evdev: Power Button: Found keys
[     6.069] (II) evdev: Power Button: Configuring as keyboard
[     6.069] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1/event1"
[     6.069] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 9)
[     6.069] (**) Option "xkb_rules" "evdev"
[     6.069] (**) Option "xkb_model" "pc105"
[     6.069] (**) Option "xkb_layout" "kr"
[     6.069] (**) Option "xkb_variant" "kr104"
[     6.069] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[     6.070] (II) No input driver specified, ignoring this device.
[     6.070] (II) This device may have been added with another device file.
[     6.070] (II) config/udev: Adding drm device (/dev/dri/card0) card0 /sys/devices/pci0000:00/0000:00:02.0/drm/card0
[     6.070] (II) config/udev: Ignoring already known drm device (/dev/dri/card0)
[     6.070] (II) config/udev: Adding input device Dell Dell USB Wired Entry Keyboard (/dev/input/event5)
[     6.070] (**) Dell Dell USB Wired Entry Keyboard: Applying InputClass "evdev keyboard catchall"
[     6.070] (II) Using input driver 'evdev' for 'Dell Dell USB Wired Entry Keyboard'
[     6.070] (**) Dell Dell USB Wired Entry Keyboard: always reports core events
[     6.070] (**) evdev: Dell Dell USB Wired Entry Keyboard: Device: "/dev/input/event5"
[     6.070] (--) evdev: Dell Dell USB Wired Entry Keyboard: Vendor 0x413c Product 0x2111
[     6.070] (--) evdev: Dell Dell USB Wired Entry Keyboard: Found keys
[     6.070] (II) evdev: Dell Dell USB Wired Entry Keyboard: Configuring as keyboard
[     6.070] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb3/3-2/3-2:1.0/input/input6/event5"
[     6.070] (II) XINPUT: Adding extended input device "Dell Dell USB Wired Entry Keyboard" (type: KEYBOARD, id 10)
[     6.070] (**) Option "xkb_rules" "evdev"
[     6.070] (**) Option "xkb_model" "pc105"
[     6.070] (**) Option "xkb_layout" "kr"
[     6.070] (**) Option "xkb_variant" "kr104"
[     6.070] (II) config/udev: Adding input device Dell Dell USB Wired Entry Keyboard (/dev/input/event6)
[     6.070] (**) Dell Dell USB Wired Entry Keyboard: Applying InputClass "evdev keyboard catchall"
[     6.070] (II) Using input driver 'evdev' for 'Dell Dell USB Wired Entry Keyboard'
[     6.070] (**) Dell Dell USB Wired Entry Keyboard: always reports core events
[     6.070] (**) evdev: Dell Dell USB Wired Entry Keyboard: Device: "/dev/input/event6"
[     6.070] (--) evdev: Dell Dell USB Wired Entry Keyboard: Vendor 0x413c Product 0x2111
[     6.070] (--) evdev: Dell Dell USB Wired Entry Keyboard: Found 1 mouse buttons
[     6.070] (--) evdev: Dell Dell USB Wired Entry Keyboard: Found scroll wheel(s)
[     6.070] (--) evdev: Dell Dell USB Wired Entry Keyboard: Found relative axes
[     6.070] (II) evdev: Dell Dell USB Wired Entry Keyboard: Forcing relative x/y axes to exist.
[     6.070] (--) evdev: Dell Dell USB Wired Entry Keyboard: Found absolute axes
[     6.070] (II) evdev: Dell Dell USB Wired Entry Keyboard: Forcing absolute x/y axes to exist.
[     6.070] (--) evdev: Dell Dell USB Wired Entry Keyboard: Found keys
[     6.070] (II) evdev: Dell Dell USB Wired Entry Keyboard: Configuring as mouse
[     6.070] (II) evdev: Dell Dell USB Wired Entry Keyboard: Configuring as keyboard
[     6.070] (II) evdev: Dell Dell USB Wired Entry Keyboard: Adding scrollwheel support
[     6.070] (**) evdev: Dell Dell USB Wired Entry Keyboard: YAxisMapping: buttons 4 and 5
[     6.070] (**) evdev: Dell Dell USB Wired Entry Keyboard: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[     6.070] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb3/3-2/3-2:1.1/input/input7/event6"
[     6.070] (II) XINPUT: Adding extended input device "Dell Dell USB Wired Entry Keyboard" (type: KEYBOARD, id 11)
[     6.070] (**) Option "xkb_rules" "evdev"
[     6.070] (**) Option "xkb_model" "pc105"
[     6.070] (**) Option "xkb_layout" "kr"
[     6.070] (**) Option "xkb_variant" "kr104"
[     6.070] (II) evdev: Dell Dell USB Wired Entry Keyboard: initialized for relative axes.
[     6.070] (WW) evdev: Dell Dell USB Wired Entry Keyboard: ignoring absolute axes.
[     6.071] (**) Dell Dell USB Wired Entry Keyboard: (accel) keeping acceleration scheme 1
[     6.071] (**) Dell Dell USB Wired Entry Keyboard: (accel) acceleration profile 0
[     6.071] (**) Dell Dell USB Wired Entry Keyboard: (accel) acceleration factor: 2.000
[     6.071] (**) Dell Dell USB Wired Entry Keyboard: (accel) acceleration threshold: 4
[     6.071] (II) config/udev: Adding input device WebCam SC-10HDP12631N (/dev/input/event12)
[     6.071] (**) WebCam SC-10HDP12631N: Applying InputClass "evdev keyboard catchall"
[     6.071] (II) Using input driver 'evdev' for 'WebCam SC-10HDP12631N'
[     6.071] (**) WebCam SC-10HDP12631N: always reports core events
[     6.071] (**) evdev: WebCam SC-10HDP12631N: Device: "/dev/input/event12"
[     6.071] (--) evdev: WebCam SC-10HDP12631N: Vendor 0x2232 Product 0x1045
[     6.071] (--) evdev: WebCam SC-10HDP12631N: Found keys
[     6.071] (II) evdev: WebCam SC-10HDP12631N: Configuring as keyboard
[     6.071] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.4/1-1.4:1.0/input/input13/event12"
[     6.071] (II) XINPUT: Adding extended input device "WebCam SC-10HDP12631N" (type: KEYBOARD, id 12)
[     6.071] (**) Option "xkb_rules" "evdev"
[     6.071] (**) Option "xkb_model" "pc105"
[     6.071] (**) Option "xkb_layout" "kr"
[     6.071] (**) Option "xkb_variant" "kr104"
[     6.071] (II) config/udev: Adding input device HDA Intel PCH Mic (/dev/input/event11)
[     6.071] (II) No input driver specified, ignoring this device.
[     6.071] (II) This device may have been added with another device file.
[     6.071] (II) config/udev: Adding input device HDA Intel PCH Headphone (/dev/input/event10)
[     6.071] (II) No input driver specified, ignoring this device.
[     6.071] (II) This device may have been added with another device file.
[     6.071] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=3 (/dev/input/event9)
[     6.071] (II) No input driver specified, ignoring this device.
[     6.071] (II) This device may have been added with another device file.
[     6.072] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[     6.072] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[     6.072] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[     6.072] (**) AT Translated Set 2 keyboard: always reports core events
[     6.072] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[     6.072] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[     6.072] (--) evdev: AT Translated Set 2 keyboard: Found keys
[     6.072] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[     6.072] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[     6.072] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 13)
[     6.072] (**) Option "xkb_rules" "evdev"
[     6.072] (**) Option "xkb_model" "pc105"
[     6.072] (**) Option "xkb_layout" "kr"
[     6.072] (**) Option "xkb_variant" "kr104"
[     6.072] (II) config/udev: Adding input device ETPS/2 Elantech Touchpad (/dev/input/event4)
[     6.072] (**) ETPS/2 Elantech Touchpad: Applying InputClass "evdev touchpad catchall"
[     6.072] (**) ETPS/2 Elantech Touchpad: Applying InputClass "touchpad catchall"
[     6.072] (**) ETPS/2 Elantech Touchpad: Applying InputClass "Default clickpad buttons"
[     6.072] (II) LoadModule: "synaptics"
[     6.072] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[     6.073] (II) Module synaptics: vendor="X.Org Foundation"
[     6.073]     compiled for 1.15.0, module version = 1.7.4
[     6.073]     Module class: X.Org XInput Driver
[     6.073]     ABI class: X.Org XInput driver, version 20.0
[     6.073] (II) Using input driver 'synaptics' for 'ETPS/2 Elantech Touchpad'
[     6.073] (**) ETPS/2 Elantech Touchpad: always reports core events
[     6.073] (**) Option "Device" "/dev/input/event4"
[     6.092] (II) synaptics: ETPS/2 Elantech Touchpad: found clickpad property
[     6.092] (--) synaptics: ETPS/2 Elantech Touchpad: x-axis range 0 - 3260 (res 32)
[     6.092] (--) synaptics: ETPS/2 Elantech Touchpad: y-axis range 0 - 2282 (res 32)
[     6.092] (--) synaptics: ETPS/2 Elantech Touchpad: pressure range 0 - 255
[     6.092] (--) synaptics: ETPS/2 Elantech Touchpad: finger width range 0 - 15
[     6.092] (--) synaptics: ETPS/2 Elantech Touchpad: buttons: left double triple
[     6.092] (--) synaptics: ETPS/2 Elantech Touchpad: Vendor 0x2 Product 0xe
[     6.092] (**) Option "SoftButtonAreas" "50% 0 82% 0 0 0 0 0"
[     6.092] (--) synaptics: ETPS/2 Elantech Touchpad: touchpad found
[     6.092] (**) ETPS/2 Elantech Touchpad: always reports core events
[     6.104] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input5/event4"
[     6.104] (II) XINPUT: Adding extended input device "ETPS/2 Elantech Touchpad" (type: TOUCHPAD, id 14)
[     6.104] (**) synaptics: ETPS/2 Elantech Touchpad: (accel) MinSpeed is now constant deceleration 2.5
[     6.104] (**) synaptics: ETPS/2 Elantech Touchpad: (accel) MaxSpeed is now 1.75
[     6.104] (**) synaptics: ETPS/2 Elantech Touchpad: (accel) AccelFactor is now 0.050
[     6.104] (**) ETPS/2 Elantech Touchpad: (accel) keeping acceleration scheme 1
[     6.104] (**) ETPS/2 Elantech Touchpad: (accel) acceleration profile 1
[     6.104] (**) ETPS/2 Elantech Touchpad: (accel) acceleration factor: 2.000
[     6.104] (**) ETPS/2 Elantech Touchpad: (accel) acceleration threshold: 4
[     6.104] (--) synaptics: ETPS/2 Elantech Touchpad: touchpad found
[     6.104] (II) config/udev: Adding input device ETPS/2 Elantech Touchpad (/dev/input/mouse0)
[     6.104] (**) ETPS/2 Elantech Touchpad: Ignoring device from InputClass "touchpad ignore duplicates"
[     6.108] (II) fglrx(0): Restoring Recent Mode via PCS is not supported in RANDR 1.2 capable environments
[     6.636] (II) fglrx(0): EDID vendor "DEL", prod id 41102
[     6.636] (II) fglrx(0): Using EDID range info for horizontal sync
[     6.636] (II) fglrx(0): Using EDID range info for vertical refresh
[     6.636] (II) fglrx(0): Printing DDC gathered Modelines:
[     6.636] (II) fglrx(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[     6.636] (II) fglrx(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz e)
[     6.636] (II) fglrx(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[     6.636] (II) fglrx(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
[     6.636] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[     6.636] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[     6.636] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[     6.636] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[     6.636] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[     6.636] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[     6.636] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[     6.636] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[     6.636] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[     6.636] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[     6.636] (II) fglrx(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)
[     6.636] (II) fglrx(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz e)
[     6.636] (II) fglrx(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz e)
[     6.636] (II) fglrx(0): Modeline "1440x240"x0.0   27.00  1440 1478 1602 1716  240 244 247 262 -hsync -vsync (15.7 kHz e)
[     6.636] (II) fglrx(0): Modeline "1440x288"x0.0   27.00  1440 1464 1590 1728  288 290 293 312 -hsync -vsync (15.6 kHz e)
[     6.636] (II) fglrx(0): Modeline "1440x576i"x0.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz e)
[     6.636] (II) fglrx(0): Modeline "1920x1080"x0.0   74.25  1920 2558 2602 2750  1080 1084 1089 1125 +hsync +vsync (27.0 kHz e)
[     6.636] (II) fglrx(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz e)
[     6.636] (II) fglrx(0): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz e)
[     7.971] (II) fglrx(0): EDID vendor "DEL", prod id 41102
[     7.971] (II) fglrx(0): Using hsync ranges from config file
[     7.971] (II) fglrx(0): Using vrefresh ranges from config file
[     7.971] (II) fglrx(0): Printing DDC gathered Modelines:
[     7.971] (II) fglrx(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[     7.971] (II) fglrx(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz e)
[     7.971] (II) fglrx(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[     7.971] (II) fglrx(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
[     7.971] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[     7.971] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[     7.971] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[     7.971] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[     7.971] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[     7.971] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[     7.971] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[     7.971] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[     7.971] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[     7.971] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[     7.971] (II) fglrx(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)
[     7.971] (II) fglrx(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz e)
[     7.971] (II) fglrx(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz e)
[     7.971] (II) fglrx(0): Modeline "1440x240"x0.0   27.00  1440 1478 1602 1716  240 244 247 262 -hsync -vsync (15.7 kHz e)
[     7.971] (II) fglrx(0): Modeline "1440x288"x0.0   27.00  1440 1464 1590 1728  288 290 293 312 -hsync -vsync (15.6 kHz e)
[     7.971] (II) fglrx(0): Modeline "1440x576i"x0.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz e)
[     7.971] (II) fglrx(0): Modeline "1920x1080"x0.0   74.25  1920 2558 2602 2750  1080 1084 1089 1125 +hsync +vsync (27.0 kHz e)
[     7.971] (II) fglrx(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz e)
[     7.971] (II) fglrx(0): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz e)
[     8.170] (II) fglrx(0): EDID vendor "DEL", prod id 41102
[     8.170] (II) fglrx(0): Using hsync ranges from config file
[     8.170] (II) fglrx(0): Using vrefresh ranges from config file
[     8.170] (II) fglrx(0): Printing DDC gathered Modelines:
[     8.170] (II) fglrx(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[     8.170] (II) fglrx(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz e)
[     8.170] (II) fglrx(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[     8.170] (II) fglrx(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
[     8.170] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[     8.170] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[     8.170] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[     8.170] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[     8.170] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[     8.170] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[     8.170] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[     8.170] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[     8.170] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[     8.170] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[     8.170] (II) fglrx(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)
[     8.170] (II) fglrx(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz e)
[     8.170] (II) fglrx(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz e)
[     8.170] (II) fglrx(0): Modeline "1440x240"x0.0   27.00  1440 1478 1602 1716  240 244 247 262 -hsync -vsync (15.7 kHz e)
[     8.170] (II) fglrx(0): Modeline "1440x288"x0.0   27.00  1440 1464 1590 1728  288 290 293 312 -hsync -vsync (15.6 kHz e)
[     8.170] (II) fglrx(0): Modeline "1440x576i"x0.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz e)
[     8.170] (II) fglrx(0): Modeline "1920x1080"x0.0   74.25  1920 2558 2602 2750  1080 1084 1089 1125 +hsync +vsync (27.0 kHz e)
[     8.170] (II) fglrx(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz e)
[     8.170] (II) fglrx(0): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz e)
[     8.211] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[     8.349] (II) fglrx(0): EDID vendor "DEL", prod id 41102
[     8.349] (II) fglrx(0): Using hsync ranges from config file
[     8.349] (II) fglrx(0): Using vrefresh ranges from config file
[     8.349] (II) fglrx(0): Printing DDC gathered Modelines:
[     8.349] (II) fglrx(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[     8.349] (II) fglrx(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz e)
[     8.349] (II) fglrx(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[     8.349] (II) fglrx(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
[     8.349] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[     8.349] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[     8.349] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[     8.349] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[     8.349] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[     8.349] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[     8.349] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[     8.349] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[     8.349] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[     8.349] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[     8.349] (II) fglrx(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)
[     8.349] (II) fglrx(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz e)
[     8.349] (II) fglrx(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz e)
[     8.349] (II) fglrx(0): Modeline "1440x240"x0.0   27.00  1440 1478 1602 1716  240 244 247 262 -hsync -vsync (15.7 kHz e)
[     8.349] (II) fglrx(0): Modeline "1440x288"x0.0   27.00  1440 1464 1590 1728  288 290 293 312 -hsync -vsync (15.6 kHz e)
[     8.349] (II) fglrx(0): Modeline "1440x576i"x0.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz e)
[     8.349] (II) fglrx(0): Modeline "1920x1080"x0.0   74.25  1920 2558 2602 2750  1080 1084 1089 1125 +hsync +vsync (27.0 kHz e)
[     8.349] (II) fglrx(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz e)
[     8.349] (II) fglrx(0): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz e)
[     8.526] (II) fglrx(0): EDID vendor "DEL", prod id 41102
[     8.526] (II) fglrx(0): Using hsync ranges from config file
[     8.526] (II) fglrx(0): Using vrefresh ranges from config file
[     8.526] (II) fglrx(0): Printing DDC gathered Modelines:
[     8.526] (II) fglrx(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[     8.526] (II) fglrx(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz e)
[     8.526] (II) fglrx(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[     8.526] (II) fglrx(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
[     8.526] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[     8.526] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[     8.526] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[     8.526] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[     8.526] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[     8.526] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[     8.526] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[     8.526] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[     8.526] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[     8.526] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[     8.526] (II) fglrx(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)
[     8.526] (II) fglrx(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz e)
[     8.526] (II) fglrx(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz e)
[     8.526] (II) fglrx(0): Modeline "1440x240"x0.0   27.00  1440 1478 1602 1716  240 244 247 262 -hsync -vsync (15.7 kHz e)
[     8.526] (II) fglrx(0): Modeline "1440x288"x0.0   27.00  1440 1464 1590 1728  288 290 293 312 -hsync -vsync (15.6 kHz e)
[     8.526] (II) fglrx(0): Modeline "1440x576i"x0.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz e)
[     8.526] (II) fglrx(0): Modeline "1920x1080"x0.0   74.25  1920 2558 2602 2750  1080 1084 1089 1125 +hsync +vsync (27.0 kHz e)
[     8.526] (II) fglrx(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz e)
[     8.526] (II) fglrx(0): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz e)
[     8.583] (II) XKB: reuse xkmfile /var/lib/xkb/server-13402A8E98604F1C22CB685E35E4BC7DEEF8D390.xkm
[     8.603] (II) XKB: reuse xkmfile /var/lib/xkb/server-13402A8E98604F1C22CB685E35E4BC7DEEF8D390.xkm
[     8.656] (II) fglrx(0): EDID vendor "DEL", prod id 41102
[     8.656] (II) fglrx(0): Using hsync ranges from config file
[     8.656] (II) fglrx(0): Using vrefresh ranges from config file
[     8.656] (II) fglrx(0): Printing DDC gathered Modelines:
[     8.656] (II) fglrx(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[     8.656] (II) fglrx(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz e)
[     8.656] (II) fglrx(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[     8.656] (II) fglrx(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
[     8.656] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[     8.656] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[     8.656] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[     8.656] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[     8.656] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[     8.656] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[     8.656] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[     8.656] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[     8.656] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[     8.656] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[     8.656] (II) fglrx(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)
[     8.656] (II) fglrx(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz e)
[     8.656] (II) fglrx(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz e)
[     8.656] (II) fglrx(0): Modeline "1440x240"x0.0   27.00  1440 1478 1602 1716  240 244 247 262 -hsync -vsync (15.7 kHz e)
[     8.656] (II) fglrx(0): Modeline "1440x288"x0.0   27.00  1440 1464 1590 1728  288 290 293 312 -hsync -vsync (15.6 kHz e)
[     8.656] (II) fglrx(0): Modeline "1440x576i"x0.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz e)
[     8.656] (II) fglrx(0): Modeline "1920x1080"x0.0   74.25  1920 2558 2602 2750  1080 1084 1089 1125 +hsync +vsync (27.0 kHz e)
[     8.656] (II) fglrx(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz e)
[     8.656] (II) fglrx(0): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz e)
[     8.688] (II) XKB: reuse xkmfile /var/lib/xkb/server-13402A8E98604F1C22CB685E35E4BC7DEEF8D390.xkm
[     8.692] (II) config/udev: Adding input device Logitech Unifying Device. Wireless PID:101a (/dev/input/mouse1)
[     8.692] (II) No input driver specified, ignoring this device.
[     8.692] (II) This device may have been added with another device file.
[     8.692] (II) config/udev: Adding input device Logitech Unifying Device. Wireless PID:101a (/dev/input/event13)
[     8.692] (**) Logitech Unifying Device. Wireless PID:101a: Applying InputClass "evdev pointer catchall"
[     8.692] (II) Using input driver 'evdev' for 'Logitech Unifying Device. Wireless PID:101a'
[     8.692] (**) Logitech Unifying Device. Wireless PID:101a: always reports core events
[     8.692] (**) evdev: Logitech Unifying Device. Wireless PID:101a: Device: "/dev/input/event13"
[     8.692] (--) evdev: Logitech Unifying Device. Wireless PID:101a: Vendor 0x46d Product 0xc52b
[     8.692] (--) evdev: Logitech Unifying Device. Wireless PID:101a: Found 20 mouse buttons
[     8.692] (--) evdev: Logitech Unifying Device. Wireless PID:101a: Found scroll wheel(s)
[     8.692] (--) evdev: Logitech Unifying Device. Wireless PID:101a: Found relative axes
[     8.692] (--) evdev: Logitech Unifying Device. Wireless PID:101a: Found x and y relative axes
[     8.692] (II) evdev: Logitech Unifying Device. Wireless PID:101a: Configuring as mouse
[     8.692] (II) evdev: Logitech Unifying Device. Wireless PID:101a: Adding scrollwheel support
[     8.692] (**) evdev: Logitech Unifying Device. Wireless PID:101a: YAxisMapping: buttons 4 and 5
[     8.692] (**) evdev: Logitech Unifying Device. Wireless PID:101a: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[     8.692] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb3/3-4/3-4:1.2/0003:046D:C52B.0005/input/input14/event13"
[     8.692] (II) XINPUT: Adding extended input device "Logitech Unifying Device. Wireless PID:101a" (type: MOUSE, id 15)
[     8.692] (II) evdev: Logitech Unifying Device. Wireless PID:101a: initialized for relative axes.
[     8.692] (**) Logitech Unifying Device. Wireless PID:101a: (accel) keeping acceleration scheme 1
[     8.692] (**) Logitech Unifying Device. Wireless PID:101a: (accel) acceleration profile 0
[     8.692] (**) Logitech Unifying Device. Wireless PID:101a: (accel) acceleration factor: 2.000
[     8.692] (**) Logitech Unifying Device. Wireless PID:101a: (accel) acceleration threshold: 4
[     9.220] (II) XKB: reuse xkmfile /var/lib/xkb/server-A313DD82F61D289C6F5CCA68170662D5E91E337A.xkm
[    39.056] (II) fglrx(0): EDID vendor "DEL", prod id 41102
[    39.056] (II) fglrx(0): Using hsync ranges from config file
[    39.056] (II) fglrx(0): Using vrefresh ranges from config file
[    39.056] (II) fglrx(0): Printing DDC gathered Modelines:
[    39.056] (II) fglrx(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[    39.056] (II) fglrx(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz e)
[    39.056] (II) fglrx(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[    39.056] (II) fglrx(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
[    39.056] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    39.056] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    39.056] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    39.056] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    39.056] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    39.056] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    39.056] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    39.056] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    39.056] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[    39.056] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    39.056] (II) fglrx(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)
[    39.056] (II) fglrx(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz e)
[    39.056] (II) fglrx(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz e)
[    39.056] (II) fglrx(0): Modeline "1440x240"x0.0   27.00  1440 1478 1602 1716  240 244 247 262 -hsync -vsync (15.7 kHz e)
[    39.056] (II) fglrx(0): Modeline "1440x288"x0.0   27.00  1440 1464 1590 1728  288 290 293 312 -hsync -vsync (15.6 kHz e)
[    39.056] (II) fglrx(0): Modeline "1440x576i"x0.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz e)
[    39.056] (II) fglrx(0): Modeline "1920x1080"x0.0   74.25  1920 2558 2602 2750  1080 1084 1089 1125 +hsync +vsync (27.0 kHz e)
[    39.056] (II) fglrx(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz e)
[    39.056] (II) fglrx(0): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz e)
[   362.588] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[   393.747] (II) XKB: reuse xkmfile /var/lib/xkb/server-13402A8E98604F1C22CB685E35E4BC7DEEF8D390.xkm
[   464.701] (II) fglrx(0): EDID vendor "DEL", prod id 41102
[   464.701] (II) fglrx(0): Using hsync ranges from config file
[   464.701] (II) fglrx(0): Using vrefresh ranges from config file
[   464.701] (II) fglrx(0): Printing DDC gathered Modelines:
[   464.701] (II) fglrx(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[   464.701] (II) fglrx(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz e)
[   464.702] (II) fglrx(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[   464.702] (II) fglrx(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
[   464.702] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[   464.702] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[   464.702] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[   464.702] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[   464.702] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[   464.702] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[   464.702] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[   464.702] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[   464.702] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[   464.702] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[   464.702] (II) fglrx(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)
[   464.702] (II) fglrx(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz e)
[   464.702] (II) fglrx(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz e)
[   464.702] (II) fglrx(0): Modeline "1440x240"x0.0   27.00  1440 1478 1602 1716  240 244 247 262 -hsync -vsync (15.7 kHz e)
[   464.702] (II) fglrx(0): Modeline "1440x288"x0.0   27.00  1440 1464 1590 1728  288 290 293 312 -hsync -vsync (15.6 kHz e)
[   464.702] (II) fglrx(0): Modeline "1440x576i"x0.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz e)
[   464.702] (II) fglrx(0): Modeline "1920x1080"x0.0   74.25  1920 2558 2602 2750  1080 1084 1089 1125 +hsync +vsync (27.0 kHz e)
[   464.702] (II) fglrx(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz e)
[   464.702] (II) fglrx(0): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz e)
[   834.072] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[   851.913] (II) XKB: reuse xkmfile /var/lib/xkb/server-13402A8E98604F1C22CB685E35E4BC7DEEF8D390.xkm

```

---

### Post by dino99 on 2015-08-05
the kernel directly deal with X, so avoid using a xorg.conf when not necessary (a simple typo or error inside, and you get headaches)

---

### Post by mastablasta on 2015-08-05
well I am not too familiar with the logs and I also do not have any hybrid GPU (yet) as well but two things seem a bit off:

```
[     4.985] (EE) Screen 1 deleted because of no matching config section.
[     4.985] (II) UnloadModule: "intel"

```
Why does it unload it?

 
```
[     5.684] (II) fglrx(0): Output VGA1 disconnected
[     5.684] (II) fglrx(0): Output HDMI1 connected
[     5.684] (II) fglrx(0): Output DP1 disconnected

```
assuming HDM1 is your external monitor I can only wonder why VGA1 was disconnected (assuming thi sis the laptop's monitor).

By the way what is the laptop model? did you search by it on internet? sometimes others have solution or workaround. I know that in past not all intel+amd models worked. while some worked perfectly.

when second monitor is in is it possible to reach catalyst center and switch the GPU chips?

---

### Post by Cheolho_Kang on 2015-08-05
**@**[COLOR=#000000]**[[COLOR=#000000]dino99[/COLOR]]("http://ubuntuforums.org/member.php?u=129712")** 

okay I can keep in mind your advice thanks!! :)

[B]@[[COLOR=#000000]mastablasta[/COLOR]]("http://ubuntuforums.org/member.php?u=964486") 
[/B]
yes I already searched all about that through my laptop model name (NT570Z5E-S78S, Samsung NewChronos5). But I cannot find any correct information..
I guess second monitor can reach connected **HDMI cable when I before boot**
But I an not sure this GPU is Intel's or AMD's

[/COLOR]

---

### Post by mastablasta on 2015-08-06
Samsung often does not support Linux. I see some guys at Arch disabled AMD on it: [https://bbs.archlinux.org/viewtopic.php?id=164182&p=2](https://bbs.archlinux.org/viewtopic.php?id=164182&p=2)

still before giving up completely - if you have a free 8 GB USB flash drive try installing newer Ubuntu there and see if newer kernel give better support. After that and if it still doesn't work try a similar thing with something like Fedora or Manjaro or some Ubuntu beta/alpha or Debian sid. these would be the easiest to try out fast. if this is fresh install you can play around hardcore - on your "production PC" no need for USB. :) you can install only newer kernel on Ubuntu as well. only I am not sure how it will affect stability.

you see drivers are in Linux part of kernel and what AMD does with proprietary drivers is they add stuff to kernel like a patch. which is why sometimes the whole thing can break when kernel get's an update but there is no patch yet from AMD. I think your AMD chip is one of those that will benefit from new AMD scheme said to be out with kernel 4.2 - where most stuff in proprietary driver will move to open source and then only extra closed source  modules will be added for improved performance (gaming).

In any case from what I saw online you seem to have few options:
- try newer kernel and latest (maybe even beta drivers)
- try latest opensource drivers (x-org edgers PPA or another one forgot the name) - perhaps switching works (I doubt this one)
- disable AMD card on Linux using only Intel GPU to reduce power consumption (at least until issue is fixed if it is ever fixed)

---

### Post by Cheolho_Kang on 2015-08-07
[B]@[[COLOR=#000000]mastablasta[/COLOR]]("http://ubuntuforums.org/member.php?u=964486") 
[/B]
Thank you for your consecutive attention!! I hope the time come soon when I solve this problem perfectly!! :)
I have two question.

1. How can I download the opensource drivers (x-org). I sometimes heard opensource driver is better than AMD/ATI public driver.
so I tried that through the control panel. but I think that is not latest version. How can I download the latest opensource driver? I tried to find web-site. but I couldn't T.T

2. I heard Samsung conceal the bios setting. just provide simple option. so User cannot disable AMD card. Is there another way to disable AMD card without BIOS setting??

thank you

---

### Post by Cheolho_Kang on 2015-10-03
I finally find the way to display! When I select boot aption to "CSM" instead of "UEFI". My laptop can just detect internel display monitor.
but I don't know why this boot option make screen display.
Did anybody have same experience like my situation?  coud u mention about it??

---

### Post by mastablasta on 2015-10-05
> **Cheolho_Kang said:**
> I finally find the way to display! When I select boot aption to "CSM" instead of "UEFI". My laptop can just detect internel display monitor.
but I don't know why this boot option make screen display.
Did anybody have same experience like my situation?  coud u mention about it??


it could be that is loads drivers in a different way - :"Compatibility Support Module (CSM) provides legacy BIOS compatibility"

[https://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](https://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

> [**Device drivers[[edit]("https://en.wikipedia.org/w/index.php?title=Unified_Extensible_Firmware_Interface&action=edit&section=12")]**

In addition to standard architecture-specific device drivers, the EFI specification provides for a processor-independent [device driver]("https://en.wikipedia.org/wiki/Device_driver") environment, called *EFI byte code* or *EBC*. System firmware is required by the UEFI specification to carry an interpreter for any EBC images that reside in or are loaded into the environment. In that sense, EBC is analogous to [Open Firmware]("https://en.wikipedia.org/wiki/Open_Firmware"), the hardware-independent firmware used in [PowerPC]("https://en.wikipedia.org/wiki/PowerPC")-based [Apple Macintosh]("https://en.wikipedia.org/wiki/Apple_Macintosh") and [Sun Microsystems]("https://en.wikipedia.org/wiki/Sun_Microsystems") [SPARC]("https://en.wikipedia.org/wiki/SPARC") computers, among others.
Some architecture-specific (non-EBC) EFI device driver types can have interfaces for use from the operating system. This allows the operating system to rely on EFI for basic graphics and network functions until operating-system-specific drivers are loaded.


> **CSM booting[[edit]("https://en.wikipedia.org/w/index.php?title=Unified_Extensible_Firmware_Interface&action=edit&section=17")]**

To ensure backward compatibility, most UEFI firmware implementations on PC-class machines also support booting in legacy BIOS mode from MBR-partitioned disks, through the *Compatibility Support Module (CSM)* that provides legacy BIOS compatibility. In this scenario, booting is performed in the same way as on legacy BIOS-based systems, by ignoring the partition table and relying on the content of a [boot sector]("https://en.wikipedia.org/wiki/Boot_sector").[SUP][[SIZE=2][31][/SIZE]]("https://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface#cite_note-arch-forum-uefi-mbr-33")[/SUP]
BIOS-style booting from MBR-partitioned disks is commonly called *BIOS-MBR*, regardless of it being performed on UEFI or legacy BIOS-based systems. Furthermore, booting legacy BIOS-based systems from GPT disks is also possible, and such a boot scheme is commonly called *BIOS-GPT*.
Despite the fact that the UEFI specification requires MBR partition tables to be fully supported,[SUP][[SIZE=2][19][/SIZE]]("https://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface#cite_note-uefi-spec-24-21")[/SUP] some UEFI firmware implementations immediately switch to the BIOS-based CSM booting depending on the type of boot disk's partition table, effectively preventing UEFI booting to be performed from EFI System partitions on MBR-partitioned disks.[SUP][[SIZE=2][31][/SIZE]]("https://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface#cite_note-arch-forum-uefi-mbr-33")[/SUP] Such a boot scheme is commonly called *UEFI-MBR*.



---

