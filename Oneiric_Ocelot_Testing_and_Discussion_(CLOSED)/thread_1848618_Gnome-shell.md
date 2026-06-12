---
title: "Gnome-shell"
date: 2011-09-22
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Hewjr100 on 2011-09-22
This is what I get when trying to install gnome-shell

hewjr@Hewjr:~$ sudo apt-get install gnome-shell
[sudo] password for hewjr: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 gnome-shell : Depends: libcogl2 (>= 1.7.4) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
hewjr@Hewjr:~$

Henry

---

### Post by jbicha on 2011-09-22
Yes, gnome-shell is temporarily uninstallable; we're waiting for caribou to arrive in the repositories. Sorry for the inconvenience.

---

### Post by cariboo on 2011-09-22
As has been said in several threads, have patience, and wait for the packages to be rebuilt. Try it in a day or two.

---

### Post by Hewjr100 on 2011-09-22
Sorry did not know, today was my first foray into ubuntu unity, have been using fedora for the past 3 months.

Henry

---

### Post by Harry33 on 2011-09-23
> **Hewjr100 said:**
> Sorry did not know, today was my first foray into ubuntu unity, have been using fedora for the past 3 months.

Henry

If you really need to have Gnome-shell right now, add and enable Ricotz Testing PPA in your sources.list, and then install Gnome-shell. The fully working version 3.1.92 has been there for two days now.

---

### Post by Roasted on 2011-09-23
Just coming here to confirm I have the same issue. I'll check it randomly on my laptop and post back here if I see it ever gets back online.

---

### Post by cecilpierce on 2011-09-23
I think gnome-shell has a big crack in it, we needs some good glue   :p

---

### Post by jerrrys on 2011-09-23
how good of shape is that PPA in?

---

### Post by cecilpierce on 2011-09-23
@Harry33

I have ricotz in one OO and tista in another,
all I get when I login to gs on either one is mouse cursor and back ground, a week ago they both were fine ???   :confused:

---

### Post by Blasphemist on 2011-09-23
It looks like I shouldn't update right now, right? My last update was 4 days ago and update manager wants to do a partial update and synaptic wants to remove Gnome shell. I've had one error since boot and using gnome shell but seems to be running ok otherwise.

---

### Post by chlorox on 2011-09-23
Check the output of your X.server.log. I'm willing to bet GTK can't find the theme you have specified. Use gconf2 to switch it back to the default theme and restart X.

---

### Post by Blasphemist on 2011-09-23
My theme is up and running and no entries in the Xorg log for that.

---

### Post by chlorox on 2011-09-23
> **Blasphemist said:**
> My theme is up and running and no entries in the Xorg log for that.

What is the output of your log?

---

### Post by Harry33 on 2011-09-23
> **Blasphemist said:**
> It looks like I shouldn't update right now, right? My last update was 4 days ago and update manager wants to do a partial update and synaptic wants to remove Gnome shell. I've had one error since boot and using gnome shell but seems to be running ok otherwise.

You should not upgrade libclutter0, libmutter0, gir1.2-cogl-1.0) packages right now.
Any of these will break gnome-shell.
This is if you have the Oneiric repo version installed.

---

### Post by Harry33 on 2011-09-23
> **cecilpierce said:**
> @Harry33

I have ricotz in one OO and tista in another,
all I get when I login to gs on either one is mouse cursor and back ground, a week ago they both were fine ???   :confused:

Do you have any other PPA's enabled in those setups?
At least xserver 1.11 is known to create issues with Oneiric and especially when using nvidia-current (with "IgnoreAbi=true").

---

### Post by Blasphemist on 2011-09-23
> **chlorox said:**
> What is the output of your log?

Hmmm, don't have a X.server.log.

Have this Xorg.0.log
```
[    24.170] 
X.Org X Server 1.10.4
Release Date: 2011-08-19
[    24.170] X Protocol Version 11, Revision 0
[    24.170] Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
[    24.170] Current Operating System: Linux jim-Satellite-L505 3.0.0-11-generic #18-Ubuntu SMP Tue Sep 13 23:38:01 UTC 2011 x86_64
[    24.171] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-11-generic root=UUID=f980979c-02d8-4ed7-9187-48f1e4e9999a ro quiet splash acpi_osi=Linux vt.handoff=7
[    24.171] Build Date: 19 September 2011  07:02:53AM
[    24.171] xorg-server 2:1.10.4-1ubuntu2 (For technical support please see http://www.ubuntu.com/support) 
[    24.171] Current version of pixman: 0.22.2
[    24.171] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    24.171] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    24.171] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Sep 23 09:45:07 2011
[    24.210] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    24.210] (==) No Layout section.  Using the first Screen section.
[    24.210] (==) No screen section available. Using defaults.
[    24.210] (**) |-->Screen "Default Screen Section" (0)
[    24.210] (**) |   |-->Monitor "<default monitor>"
[    24.210] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    24.210] (==) Automatically adding devices
[    24.210] (==) Automatically enabling devices
[    24.210] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    24.210] 	Entry deleted from font path.
[    24.210] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    24.210] 	Entry deleted from font path.
[    24.210] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    24.210] 	Entry deleted from font path.
[    24.210] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    24.210] 	Entry deleted from font path.
[    24.210] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    24.210] 	Entry deleted from font path.
[    24.210] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    24.210] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    24.210] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    24.210] (II) Loader magic: 0x7e0220
[    24.210] (II) Module ABI versions:
[    24.210] 	X.Org ANSI C Emulation: 0.4
[    24.210] 	X.Org Video Driver: 10.0
[    24.210] 	X.Org XInput driver : 12.3
[    24.210] 	X.Org Server Extension : 5.0
[    24.212] (--) PCI:*(0:0:2:0) 8086:2a42:1179:ff10 rev 7, Mem @ 0xd0000000/4194304, 0xc0000000/268435456, I/O @ 0x00005110/8
[    24.212] (--) PCI: (0:0:2:1) 8086:2a43:1179:ff10 rev 7, Mem @ 0xd3500000/1048576
[    24.212] (II) Open ACPI successful (/var/run/acpid.socket)
[    24.212] (II) LoadModule: "extmod"
[    24.236] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    24.236] (II) Module extmod: vendor="X.Org Foundation"
[    24.236] 	compiled for 1.10.4, module version = 1.0.0
[    24.236] 	Module class: X.Org Server Extension
[    24.236] 	ABI class: X.Org Server Extension, version 5.0
[    24.236] (II) Loading extension MIT-SCREEN-SAVER
[    24.236] (II) Loading extension XFree86-VidModeExtension
[    24.236] (II) Loading extension XFree86-DGA
[    24.236] (II) Loading extension DPMS
[    24.236] (II) Loading extension XVideo
[    24.236] (II) Loading extension XVideo-MotionCompensation
[    24.236] (II) Loading extension X-Resource
[    24.236] (II) LoadModule: "dbe"
[    24.236] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    24.236] (II) Module dbe: vendor="X.Org Foundation"
[    24.236] 	compiled for 1.10.4, module version = 1.0.0
[    24.236] 	Module class: X.Org Server Extension
[    24.236] 	ABI class: X.Org Server Extension, version 5.0
[    24.236] (II) Loading extension DOUBLE-BUFFER
[    24.236] (II) LoadModule: "glx"
[    24.237] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    24.237] (II) Module glx: vendor="X.Org Foundation"
[    24.237] 	compiled for 1.10.4, module version = 1.0.0
[    24.237] 	ABI class: X.Org Server Extension, version 5.0
[    24.237] (==) AIGLX enabled
[    24.237] (II) Loading extension GLX
[    24.237] (II) LoadModule: "record"
[    24.237] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    24.237] (II) Module record: vendor="X.Org Foundation"
[    24.237] 	compiled for 1.10.4, module version = 1.13.0
[    24.237] 	Module class: X.Org Server Extension
[    24.237] 	ABI class: X.Org Server Extension, version 5.0
[    24.237] (II) Loading extension RECORD
[    24.237] (II) LoadModule: "dri"
[    24.238] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    24.238] (II) Module dri: vendor="X.Org Foundation"
[    24.238] 	compiled for 1.10.4, module version = 1.0.0
[    24.238] 	ABI class: X.Org Server Extension, version 5.0
[    24.238] (II) Loading extension XFree86-DRI
[    24.238] (II) LoadModule: "dri2"
[    24.238] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    24.238] (II) Module dri2: vendor="X.Org Foundation"
[    24.238] 	compiled for 1.10.4, module version = 1.2.0
[    24.238] 	ABI class: X.Org Server Extension, version 5.0
[    24.238] (II) Loading extension DRI2
[    24.238] (==) Matched intel as autoconfigured driver 0
[    24.238] (==) Matched vesa as autoconfigured driver 1
[    24.238] (==) Matched fbdev as autoconfigured driver 2
[    24.238] (==) Assigned the driver to the xf86ConfigLayout
[    24.238] (II) LoadModule: "intel"
[    24.238] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    24.239] (II) Module intel: vendor="X.Org Foundation"
[    24.239] 	compiled for 1.10.2.902, module version = 2.15.901
[    24.239] 	Module class: X.Org Video Driver
[    24.239] 	ABI class: X.Org Video Driver, version 10.0
[    24.239] (II) LoadModule: "vesa"
[    24.239] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    24.239] (II) Module vesa: vendor="X.Org Foundation"
[    24.239] 	compiled for 1.10.2, module version = 2.3.0
[    24.239] 	Module class: X.Org Video Driver
[    24.239] 	ABI class: X.Org Video Driver, version 10.0
[    24.239] (II) LoadModule: "fbdev"
[    24.239] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    24.239] (II) Module fbdev: vendor="X.Org Foundation"
[    24.239] 	compiled for 1.10.0, module version = 0.4.2
[    24.239] 	ABI class: X.Org Video Driver, version 10.0
[    24.239] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
	965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
	4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
	Sandybridge Desktop (GT1), Sandybridge Desktop (GT2),
	Sandybridge Desktop (GT2+), Sandybridge Mobile (GT1),
	Sandybridge Mobile (GT2), Sandybridge Mobile (GT2+),
	Sandybridge Server, Ivybridge Mobile (GT1), Ivybridge Mobile (GT2),
	Ivybridge Desktop (GT1), Ivybridge Desktop (GT2), Ivybridge Server
[    24.240] (II) VESA: driver for VESA chipsets: vesa
[    24.240] (II) FBDEV: driver for framebuffer: fbdev
[    24.240] (++) using VT number 7

[    24.240] (WW) xf86OpenConsole: setpgid failed: Operation not permitted
[    24.240] (WW) xf86OpenConsole: setsid failed: Operation not permitted
[    24.242] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    24.242] (WW) Falling back to old probe method for vesa
[    24.242] (WW) Falling back to old probe method for fbdev
[    24.242] (II) Loading sub module "fbdevhw"
[    24.242] (II) LoadModule: "fbdevhw"
[    24.242] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    24.242] (II) Module fbdevhw: vendor="X.Org Foundation"
[    24.242] 	compiled for 1.10.4, module version = 0.0.2
[    24.242] 	ABI class: X.Org Video Driver, version 10.0
[    24.243] drmOpenDevice: node name is /dev/dri/card0
[    24.243] drmOpenDevice: open result is 12, (OK)
[    24.243] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[    24.243] drmOpenDevice: node name is /dev/dri/card0
[    24.243] drmOpenDevice: open result is 12, (OK)
[    24.243] drmOpenByBusid: drmOpenMinor returns 12
[    24.243] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    24.243] (II) intel(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    24.243] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    24.243] (==) intel(0): RGB weight 888
[    24.243] (==) intel(0): Default visual is TrueColor
[    24.243] (II) intel(0): Integrated Graphics Chipset: Intel(R) GM45
[    24.243] (--) intel(0): Chipset: "GM45"
[    24.243] (**) intel(0): Relaxed fencing enabled
[    24.243] (**) intel(0): Wait on SwapBuffers? enabled
[    24.243] (**) intel(0): Triple buffering? enabled
[    24.243] (**) intel(0): Framebuffer tiled
[    24.243] (**) intel(0): Pixmaps tiled
[    24.243] (**) intel(0): 3D buffers tiled
[    24.243] (**) intel(0): SwapBuffers wait enabled
[    24.243] (==) intel(0): video overlay key set to 0x101fe
[    24.243] (II) intel(0): Output LVDS1 has no monitor section
[    24.243] (II) intel(0): found backlight control interface /sys/class/backlight/acpi_video0
[    24.280] (II) intel(0): Output VGA1 has no monitor section
[    24.281] (II) intel(0): Output DP1 has no monitor section
[    24.611] (II) intel(0): Output TV1 has no monitor section
[    24.611] (II) intel(0): EDID for output LVDS1
[    24.611] (II) intel(0): Manufacturer: SEC  Model: 3041  Serial#: 0
[    24.611] (II) intel(0): Year: 2008  Week: 0
[    24.611] (II) intel(0): EDID Version: 1.3
[    24.611] (II) intel(0): Digital Display Input
[    24.611] (II) intel(0): Max Image Size [cm]: horiz.: 35  vert.: 20
[    24.611] (II) intel(0): Gamma: 2.20
[    24.611] (II) intel(0): No DPMS capabilities specified
[    24.611] (II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    24.611] (II) intel(0): First detailed timing is preferred mode
[    24.611] (II) intel(0): redX: 0.580 redY: 0.340   greenX: 0.310 greenY: 0.550
[    24.611] (II) intel(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
[    24.611] (II) intel(0): Manufacturer's mask: 0
[    24.611] (II) intel(0): Supported detailed timing:
[    24.611] (II) intel(0): clock: 69.9 MHz   Image Size:  353 x 198 mm
[    24.611] (II) intel(0): h_active: 1366  h_sync: 1414  h_sync_end 1446 h_blank_end 1474 h_border: 0
[    24.611] (II) intel(0): v_active: 768  v_sync: 770  v_sync_end 775 v_blanking: 790 v_border: 0
[    24.611] (II) intel(0): Unknown vendor-specific block f
[    24.611] (II) intel(0):  SAMSUNG
[    24.611] (II) intel(0):  160AT01-T02
[    24.611] (II) intel(0): EDID (in hex):
[    24.611] (II) intel(0): 	00ffffffffffff004ca3413000000000
[    24.611] (II) intel(0): 	00120103802314780a87f594574f8c27
[    24.611] (II) intel(0): 	27505400000001010101010101010101
[    24.611] (II) intel(0): 	0101010101014a1b566c500016303020
[    24.611] (II) intel(0): 	250061c6100000190000000f00000000
[    24.611] (II) intel(0): 	00000000001eb4027400000000fe0053
[    24.611] (II) intel(0): 	414d53554e470a2020202020000000fe
[    24.611] (II) intel(0): 	00313630415430312d5430320a2000dc
[    24.611] (II) intel(0): EDID vendor "SEC", prod id 12353
[    24.611] (II) intel(0): Printing DDC gathered Modelines:
[    24.611] (II) intel(0): Modeline "1366x768"x0.0   69.86  1366 1414 1446 1474  768 770 775 790 -hsync -vsync (47.4 kHz)
[    24.611] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[    24.611] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    24.611] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    24.611] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[    24.611] (II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
[    24.611] (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
[    24.612] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[    24.612] (II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
[    24.612] (II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
[    24.612] (II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
[    24.612] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    24.612] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    24.612] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    24.612] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[    24.612] (II) intel(0): Not using default mode "720x450" (doublescan mode not supported)
[    24.612] (II) intel(0): Not using default mode "800x512" (doublescan mode not supported)
[    24.612] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    24.612] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    24.612] (II) intel(0): Not using default mode "960x540" (doublescan mode not supported)
[    24.612] (II) intel(0): Not using default mode "960x600" (doublescan mode not supported)
[    24.612] (II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
[    24.612] (II) intel(0): Printing probed modes for output LVDS1
[    24.612] (II) intel(0): Modeline "1366x768"x60.0   69.86  1366 1414 1446 1474  768 770 775 790 -hsync -vsync (47.4 kHz)
[    24.612] (II) intel(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
[    24.612] (II) intel(0): Modeline "1360x768"x60.0   72.00  1360 1408 1440 1520  768 771 781 790 +hsync -vsync (47.4 kHz)
[    24.612] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    24.612] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    24.612] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    24.612] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    24.650] (II) intel(0): EDID for output VGA1
[    24.651] (II) intel(0): EDID for output DP1
[    24.971] (II) intel(0): EDID for output TV1
[    24.971] (II) intel(0): Output LVDS1 connected
[    24.971] (II) intel(0): Output VGA1 disconnected
[    24.971] (II) intel(0): Output DP1 disconnected
[    24.971] (II) intel(0): Output TV1 disconnected
[    24.971] (II) intel(0): Using exact sizes for initial modes
[    24.971] (II) intel(0): Output LVDS1 using initial mode 1366x768
[    24.971] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    24.971] (II) intel(0): Kernel page flipping support detected, enabling
[    24.971] (**) intel(0): Display dimensions: (350, 200) mm
[    24.971] (**) intel(0): DPI set to (99, 97)
[    24.971] (II) Loading sub module "fb"
[    24.971] (II) LoadModule: "fb"
[    24.971] (II) Loading /usr/lib/xorg/modules/libfb.so
[    24.972] (II) Module fb: vendor="X.Org Foundation"
[    24.972] 	compiled for 1.10.4, module version = 1.0.0
[    24.972] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    24.972] (II) Loading sub module "dri2"
[    24.972] (II) LoadModule: "dri2"
[    24.972] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    24.972] (II) Module dri2: vendor="X.Org Foundation"
[    24.972] 	compiled for 1.10.4, module version = 1.2.0
[    24.972] 	ABI class: X.Org Server Extension, version 5.0
[    24.972] (II) UnloadModule: "vesa"
[    24.972] (II) Unloading vesa
[    24.972] (II) UnloadModule: "fbdev"
[    24.972] (II) Unloading fbdev
[    24.972] (II) UnloadModule: "fbdevhw"
[    24.972] (II) Unloading fbdevhw
[    24.972] (==) Depth 24 pixmap format is 32 bpp
[    24.972] (II) intel(0): [DRI2] Setup complete
[    24.972] (II) intel(0): [DRI2]   DRI driver: i965
[    24.972] (II) intel(0): Allocated new frame buffer 1408x768 stride 5632, tiled
[    24.983] (II) UXA(0): Driver registered support for the following operations:
[    24.983] (II)         solid
[    24.983] (II)         copy
[    24.983] (II)         composite (RENDER acceleration)
[    24.983] (II)         put_image
[    24.983] (II)         get_image
[    24.983] (==) intel(0): Backing store disabled
[    24.983] (==) intel(0): Silken mouse enabled
[    24.983] (II) intel(0): Initializing HW Cursor
[    25.010] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    25.017] (==) intel(0): DPMS enabled
[    25.018] (==) intel(0): Intel XvMC decoder enabled
[    25.018] (II) intel(0): Set up textured video
[    25.018] (II) intel(0): [XvMC] xvmc_vld driver initialized.
[    25.018] (II) intel(0): direct rendering: DRI2 Enabled
[    25.018] (==) intel(0): hotplug detection: "enabled"
[    25.018] (--) RandR disabled
[    25.018] (II) Initializing built-in extension Generic Event Extension
[    25.018] (II) Initializing built-in extension SHAPE
[    25.018] (II) Initializing built-in extension MIT-SHM
[    25.018] (II) Initializing built-in extension XInputExtension
[    25.018] (II) Initializing built-in extension XTEST
[    25.018] (II) Initializing built-in extension BIG-REQUESTS
[    25.018] (II) Initializing built-in extension SYNC
[    25.018] (II) Initializing built-in extension XKEYBOARD
[    25.018] (II) Initializing built-in extension XC-MISC
[    25.018] (II) Initializing built-in extension SECURITY
[    25.018] (II) Initializing built-in extension XINERAMA
[    25.018] (II) Initializing built-in extension XFIXES
[    25.018] (II) Initializing built-in extension RENDER
[    25.018] (II) Initializing built-in extension RANDR
[    25.018] (II) Initializing built-in extension COMPOSITE
[    25.018] (II) Initializing built-in extension DAMAGE
[    25.018] (II) Initializing built-in extension GESTURE
[    25.024] (II) AIGLX: Trying DRI driver /usr/lib/x86_64-linux-gnu/dri/i965_dri.so
[    25.028] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    25.028] (II) AIGLX: enabled GLX_INTEL_swap_event
[    25.028] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    25.028] (II) AIGLX: enabled GLX_SGI_make_current_read
[    25.028] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    25.028] (II) AIGLX: Loaded and initialized i965
[    25.028] (II) GLX: Initialized DRI2 GL provider for screen 0
[    25.028] (II) intel(0): Setting screen physical size to 361 x 203
[    25.037] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    25.048] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    25.048] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    25.048] (II) LoadModule: "evdev"
[    25.048] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    25.049] (II) Module evdev: vendor="X.Org Foundation"
[    25.049] 	compiled for 1.10.2, module version = 2.6.0
[    25.049] 	Module class: X.Org XInput Driver
[    25.049] 	ABI class: X.Org XInput driver, version 12.3
[    25.049] (II) Using input driver 'evdev' for 'Power Button'
[    25.049] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    25.049] (**) Power Button: always reports core events
[    25.049] (**) Power Button: Device: "/dev/input/event2"
[    25.049] (--) Power Button: Found keys
[    25.049] (II) Power Button: Configuring as keyboard
[    25.049] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[    25.049] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    25.049] (**) Option "xkb_rules" "evdev"
[    25.049] (**) Option "xkb_model" "pc105"
[    25.049] (**) Option "xkb_layout" "us"
[    25.050] (II) config/udev: Adding input device Video Bus (/dev/input/event4)
[    25.050] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    25.050] (II) Using input driver 'evdev' for 'Video Bus'
[    25.050] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    25.050] (**) Video Bus: always reports core events
[    25.050] (**) Video Bus: Device: "/dev/input/event4"
[    25.050] (--) Video Bus: Found keys
[    25.051] (II) Video Bus: Configuring as keyboard
[    25.051] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input4/event4"
[    25.051] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[    25.051] (**) Option "xkb_rules" "evdev"
[    25.051] (**) Option "xkb_model" "pc105"
[    25.051] (**) Option "xkb_layout" "us"
[    25.055] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    25.055] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    25.055] (II) Using input driver 'evdev' for 'Power Button'
[    25.055] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    25.055] (**) Power Button: always reports core events
[    25.055] (**) Power Button: Device: "/dev/input/event0"
[    25.055] (--) Power Button: Found keys
[    25.055] (II) Power Button: Configuring as keyboard
[    25.055] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    25.055] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    25.055] (**) Option "xkb_rules" "evdev"
[    25.055] (**) Option "xkb_model" "pc105"
[    25.055] (**) Option "xkb_layout" "us"
[    25.056] (II) config/udev: Adding input device Lid Switch (/dev/input/event1)
[    25.056] (II) No input driver/identifier specified (ignoring)
[    25.058] (II) config/udev: Adding input device USB2.0 UVC WebCam (/dev/input/event7)
[    25.058] (**) USB2.0 UVC WebCam: Applying InputClass "evdev keyboard catchall"
[    25.058] (II) Using input driver 'evdev' for 'USB2.0 UVC WebCam'
[    25.058] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    25.058] (**) USB2.0 UVC WebCam: always reports core events
[    25.059] (**) USB2.0 UVC WebCam: Device: "/dev/input/event7"
[    25.059] (--) USB2.0 UVC WebCam: Found keys
[    25.059] (II) USB2.0 UVC WebCam: Configuring as keyboard
[    25.059] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.7/usb1/1-2/1-2:1.0/input/input7/event7"
[    25.059] (II) XINPUT: Adding extended input device "USB2.0 UVC WebCam" (type: KEYBOARD)
[    25.059] (**) Option "xkb_rules" "evdev"
[    25.059] (**) Option "xkb_model" "pc105"
[    25.059] (**) Option "xkb_layout" "us"
[    25.060] (II) config/udev: Adding input device HDA Intel Mic (/dev/input/event5)
[    25.060] (II) No input driver/identifier specified (ignoring)
[    25.060] (II) config/udev: Adding input device HDA Intel Headphone (/dev/input/event6)
[    25.060] (II) No input driver/identifier specified (ignoring)
[    25.067] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    25.067] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    25.067] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    25.067] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    25.067] (**) AT Translated Set 2 keyboard: always reports core events
[    25.067] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    25.067] (--) AT Translated Set 2 keyboard: Found keys
[    25.067] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    25.067] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[    25.067] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    25.067] (**) Option "xkb_rules" "evdev"
[    25.067] (**) Option "xkb_model" "pc105"
[    25.067] (**) Option "xkb_layout" "us"
[    25.067] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event8)
[    25.067] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    25.067] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    25.067] (II) LoadModule: "synaptics"
[    25.068] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    25.068] (II) Module synaptics: vendor="X.Org Foundation"
[    25.068] 	compiled for 1.10.2, module version = 1.4.1
[    25.068] 	Module class: X.Org XInput Driver
[    25.068] 	ABI class: X.Org XInput driver, version 12.3
[    25.068] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[    25.068] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    25.068] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    25.068] (**) Option "Device" "/dev/input/event8"
[    25.074] (--) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5692
[    25.074] (--) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4680
[    25.074] (--) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    25.074] (--) SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[    25.074] (--) SynPS/2 Synaptics TouchPad: buttons: left right double triple
[    25.084] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    25.084] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    25.084] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input8/event8"
[    25.084] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
[    25.085] (**) SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[    25.085] (**) SynPS/2 Synaptics TouchPad: MaxSpeed is now 1.75
[    25.085] (**) SynPS/2 Synaptics TouchPad: AccelFactor is now 0.037
[    25.085] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    25.085] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[    25.085] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    25.085] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    25.085] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    25.086] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[    25.086] (II) No input driver/identifier specified (ignoring)
[    26.873] (II) intel(0): EDID vendor "SEC", prod id 12353
[    26.873] (II) intel(0): Printing DDC gathered Modelines:
[    26.873] (II) intel(0): Modeline "1366x768"x0.0   69.86  1366 1414 1446 1474  768 770 775 790 -hsync -vsync (47.4 kHz)
[    27.565] (II) intel(0): EDID vendor "SEC", prod id 12353
[    27.565] (II) intel(0): Printing DDC gathered Modelines:
[    27.565] (II) intel(0): Modeline "1366x768"x0.0   69.86  1366 1414 1446 1474  768 770 775 790 -hsync -vsync (47.4 kHz)
[    28.010] (II) intel(0): EDID vendor "SEC", prod id 12353
[    28.010] (II) intel(0): Printing DDC gathered Modelines:
[    28.010] (II) intel(0): Modeline "1366x768"x0.0   69.86  1366 1414 1446 1474  768 770 775 790 -hsync -vsync (47.4 kHz)
[    28.544] (II) intel(0): EDID vendor "SEC", prod id 12353
[    28.544] (II) intel(0): Printing DDC gathered Modelines:
[    28.544] (II) intel(0): Modeline "1366x768"x0.0   69.86  1366 1414 1446 1474  768 770 775 790 -hsync -vsync (47.4 kHz)
[    29.103] (II) intel(0): EDID vendor "SEC", prod id 12353
[    29.103] (II) intel(0): Printing DDC gathered Modelines:
[    29.103] (II) intel(0): Modeline "1366x768"x0.0   69.86  1366 1414 1446 1474  768 770 775 790 -hsync -vsync (47.4 kHz)
[    29.633] (II) intel(0): EDID vendor "SEC", prod id 12353
[    29.634] (II) intel(0): Printing DDC gathered Modelines:
[    29.634] (II) intel(0): Modeline "1366x768"x0.0   69.86  1366 1414 1446 1474  768 770 775 790 -hsync -vsync (47.4 kHz)
[    32.739] (II) intel(0): EDID vendor "SEC", prod id 12353
[    32.739] (II) intel(0): Printing DDC gathered Modelines:
[    32.739] (II) intel(0): Modeline "1366x768"x0.0   69.86  1366 1414 1446 1474  768 770 775 790 -hsync -vsync (47.4 kHz)
[    45.214] (II) intel(0): EDID vendor "SEC", prod id 12353
[    45.214] (II) intel(0): Printing DDC gathered Modelines:
[    45.214] (II) intel(0): Modeline "1366x768"x0.0   69.86  1366 1414 1446 1474  768 770 775 790 -hsync -vsync (47.4 kHz)
[    45.758] (II) intel(0): EDID vendor "SEC", prod id 12353
[    45.758] (II) intel(0): Printing DDC gathered Modelines:
[    45.758] (II) intel(0): Modeline "1366x768"x0.0   69.86  1366 1414 1446 1474  768 770 775 790 -hsync -vsync (47.4 kHz)
[    46.368] (II) intel(0): EDID vendor "SEC", prod id 12353
[    46.368] (II) intel(0): Printing DDC gathered Modelines:
[    46.368] (II) intel(0): Modeline "1366x768"x0.0   69.86  1366 1414 1446 1474  768 770 775 790 -hsync -vsync (47.4 kHz)
[    46.902] (II) intel(0): EDID vendor "SEC", prod id 12353
[    46.902] (II) intel(0): Printing DDC gathered Modelines:
[    46.902] (II) intel(0): Modeline "1366x768"x0.0   69.86  1366 1414 1446 1474  768 770 775 790 -hsync -vsync (47.4 kHz)
[    47.462] (II) intel(0): EDID vendor "SEC", prod id 12353
[    47.462] (II) intel(0): Printing DDC gathered Modelines:
[    47.462] (II) intel(0): Modeline "1366x768"x0.0   69.86  1366 1414 1446 1474  768 770 775 790 -hsync -vsync (47.4 kHz)
[    48.022] (II) intel(0): EDID vendor "SEC", prod id 12353
[    48.023] (II) intel(0): Printing DDC gathered Modelines:
[    48.023] (II) intel(0): Modeline "1366x768"x0.0   69.86  1366 1414 1446 1474  768 770 775 790 -hsync -vsync (47.4 kHz)
[    48.826] (II) intel(0): EDID vendor "SEC", prod id 12353
[    48.826] (II) intel(0): Printing DDC gathered Modelines:
[    48.826] (II) intel(0): Modeline "1366x768"x0.0   69.86  1366 1414 1446 1474  768 770 775 790 -hsync -vsync (47.4 kHz)
[    49.312] (II) intel(0): EDID vendor "SEC", prod id 12353
[    49.312] (II) intel(0): Printing DDC gathered Modelines:
[    49.312] (II) intel(0): Modeline "1366x768"x0.0   69.86  1366 1414 1446 1474  768 770 775 790 -hsync -vsync (47.4 kHz)
[    50.241] (II) XKB: reuse xkmfile /var/lib/xkb/server-A77BBE312A49C9FE89948D38B2A8CB84C3CBB410.xkm
[    55.169] (II) intel(0): EDID vendor "SEC", prod id 12353
[    55.169] (II) intel(0): Printing DDC gathered Modelines:
[    55.169] (II) intel(0): Modeline "1366x768"x0.0   69.86  1366 1414 1446 1474  768 770 775 790 -hsync -vsync (47.4 kHz)

```
I'll also go into my oneiric part that has E instead of G3 shell.

---

### Post by kainos on 2011-09-23
Ricotz worked for me

[https://launchpad.net/~ricotz/+archive/testing](https://launchpad.net/~ricotz/+archive/testing)

---

### Post by sgage on 2011-09-23
> **kainos said:**
> Ricotz worked for me

[https://launchpad.net/~ricotz/+archive/testing](https://launchpad.net/~ricotz/+archive/testing)

Ricotz working fine for me, too.

---

### Post by jbicha on 2011-09-23
GNOME Shell should once again be installable.

---

### Post by cariboo on 2011-09-23
I can confirm that gnome-shell is installable again.

---

### Post by cecilpierce on 2011-09-23
> **Harry33 said:**
> Do you have any other PPA's enabled in those setups?
At least xserver 1.11 is known to create issues with Oneiric and especially when using nvidia-current (with "IgnoreAbi=true").

No just ricotz in one and tista in the other and nvidia-current with a fgx6200 card, you think nouveau would make a difference ? 
Ive tried purge and reinstall and all I get is mouse cursor, Im ready for re-install on both    :confused:

---

### Post by Harry33 on 2011-09-24
> **cecilpierce said:**
> No just ricotz in one and tista in the other and nvidia-current with a fgx6200 card, you think nouveau would make a difference ? 
Ive tried purge and reinstall and all I get is mouse cursor, Im ready for re-install on both    :confused:

If you are using xserver 1.10.4, nvidia-current works very well, no need to try nouveau.
Something else is wrong with your setup.
Of course you could try purging Ricotz, because Gnome-shell 3.1.92 is now available from Oneiric repos.
If you have a fully updated setup now, it is enough if you downgrade packages gnome-shell, gir12.-caribou-1.0 and libcaribou0. Also remove gnome-shell extensions. All other other gnome-shell related packages are newer in Oneiric.

---

### Post by Makova on 2011-09-24
I've been able to install, thanks ...):P

---

### Post by Roasted on 2011-09-24
Working here fine now. :popcorn:

---

