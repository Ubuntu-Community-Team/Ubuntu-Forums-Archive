---
title: "Power managment -- fan noise Asus U31"
date: 2012-10-09
forum: New to Ubuntu
---

### Post by nsznaj on 2012-10-09
Hi everyone.

I have an issue with my new Asus U31SG. I couldn't find any similar issue on the web...

My fan spins a lot, a bit noisy, but most importantly, it makes the touchpad zone vibrate, and is like uncomfortable. 

I saw [https://wiki.ubuntu.com/Kernel/PowerManagement/IdentifyingIssues](https://wiki.ubuntu.com/Kernel/PowerManagement/IdentifyingIssues)
and followed the instructions, but don't know how to interpret the results nor how to improve on the power management. I suppose there's something wrong with my laptop power configuration!

Here's what I did:

Installed powertop-1.13

Run ~$ sudo powertop-1.13 -d -t 60 > powertop.log

Got the file powertop.txt (attached).

Then, installed  fatrace

Run ~$ sudo power-usage-report

And got the report filed in power-usage-report.txt (see attachments)


I have no idea what to do with them, and I don't know how bad those numbers are!

Help much appreciated folks!

---

### Post by nsznaj on 2012-10-16
no one???????

---

### Post by NikTh on 2012-10-17
Hi , 

As I saw from the attached files , you have dual graphics (hybrid graphics) Intel & Nvidia. 
Have you seen this project ? 
[http://bumblebee-project.org/](http://bumblebee-project.org/)

Also powertop have some suggestions you can enable with commands in terminal. I don't really know if those suggestions will help you or not , but you can try to apply them. 

At the Unity environment you can see what graphics you use by this command in a terminal 
```
/usr/lib/nux/unity_support_test -p
```You can open a terminal with Ctrl+Alt+T keys combo. 
Also you can see various info with this command 
```
lspci -nnk | grep -iA2 vga
```Install psesnor and lm-sensors to watch you temperatures. If temperatures are good then maybe this is a hardware (fun) problem. 

```
sudo apt-get install lm-sensors psensor 
sudo sensors-detect **#**answer (Y)es to all questions here , by pressing [Enter] key.
```Reboot your PC.

Thanks

---

### Post by nsznaj on 2012-10-21
thank you!

this is what I got. I don't know if it's right or not...
```
nahuel@nahuel:~$ /usr/lib/nux/unity_support_test -p
Xlib:  extension "GLX" missing on display ":0.0".
Error: GLX is not available on the system
nahuel@nahuel:~$ lspci -nnk | grep -iA2 vga
00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0126] (rev 09)
	Subsystem: ASUSTeK Computer Inc. Device [1043:2129]
	Kernel driver in use: i915
--
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation Device [10de:105a] (rev a1)
	Subsystem: ASUSTeK Computer Inc. Device [1043:2129]
	Kernel driver in use: nvidia

```

Afterwards, I installed the psensor: temperatures are less than or equal to 50 C while there is this awkward vibration... 

here the output of the 'sensors' program (the psensor is graphical)

```
nahuel@nahuel:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:        +50.0°C  (crit = +103.0°C)

coretemp-isa-0000
Adapter: ISA adapter
Physical id 0:  +50.0°C  (high = +86.0°C, crit = +100.0°C)
Core 0:         +50.0°C  (high = +86.0°C, crit = +100.0°C)
Core 1:         +49.0°C  (high = +86.0°C, crit = +100.0°C)

asus-isa-0000
Adapter: ISA adapter
temp1:        +50.0°C  

```


a hardware problem might be the most likely explanation...but this laptop has only 3 months use, I just bought it!

what shall I do? Shall I get a new fan?

Thank you for your help

---

### Post by NikTh on 2012-10-21
> **nsznaj said:**
> 
a hardware problem might be the most likely explanation...but this laptop has only 3 months use, I just bought it!

what shall I do? Shall I get a new fan?


If the laptop is only 3 months , then it should have the warranty  active. In your situation I would give it for a check. 

The temperatures are just fine.

This is another problem and I don't think is related with the fun. 
> ```
nahuel@nahuel:~$ /usr/lib/nux/unity_support_test -p 
Xlib:  extension "GLX" missing on display ":0.0". 
Error: GLX is not available on the system
```Give the results of 

```
dpkg -l | grep -i nvidia 
echo $DESKTOP_SESSION
cat /etc/X11/xorg.conf 
cat /var/log/Xorg.0.log|grep -e WW -e EE
```Thanks

---

### Post by nsznaj on 2012-10-21
Hi, 

I don't have warranty, I bought it in the US and brought it to Argentina... so it's all up to me

here the results
```
nahuel@nahuel:~$ dpkg -l | grep -i nvidia 
ii  nvidia-common                          1:0.2.44.2                              Find obsolete NVIDIA drivers
ii  nvidia-current                         295.40-0ubuntu1.1                       NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-settings                        295.33-0ubuntu1                         Tool of configuring the NVIDIA graphics driver
nahuel@nahuel:~$ echo $DESKTOP_SESSION
ubuntu-2d
nahuel@nahuel:~$ cat /etc/X11/xorg.conf 

Section "Device"
	Identifier	"Default Device"
	Option	"NoLogo"	"True"
EndSection

nahuel@nahuel:~$ 

```

---

### Post by NikTh on 2012-10-21
Sorry , but I edited my post above.. and added one more command. Please re-read and re-post. 

Thanks

---

### Post by nsznaj on 2012-10-21
Hi, 

I don't have warranty, I bought it in the US and brought it to Argentina... so it's all up to me

here the results
```
nahuel@nahuel:~$ dpkg -l | grep -i nvidia 
ii  nvidia-common                          1:0.2.44.2                              Find obsolete NVIDIA drivers
ii  nvidia-current                         295.40-0ubuntu1.1                       NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-settings                        295.33-0ubuntu1                         Tool of configuring the NVIDIA graphics driver
nahuel@nahuel:~$ echo $DESKTOP_SESSION
ubuntu-2d
nahuel@nahuel:~$ cat /etc/X11/xorg.conf 

Section "Device"
	Identifier	"Default Device"
	Option	"NoLogo"	"True"
EndSection

nahuel@nahuel:~$ 

```

the last one is too large!




```
nahuel@nahuel:~$ cat /var/log/Xorg.0.log
[    15.698] 
X.Org X Server 1.11.3
Release Date: 2011-12-16
[    15.699] X Protocol Version 11, Revision 0
[    15.699] Build Operating System: Linux 2.6.42-23-generic x86_64 Ubuntu
[    15.699] Current Operating System: Linux nahuel 3.2.0-32-generic #51-Ubuntu SMP Wed Sep 26 21:33:09 UTC 2012 x86_64
[    15.699] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-32-generic root=UUID=041656ce-f595-4c47-a941-6e2c82ab7d35 ro quiet splash vt.handoff=7
[    15.699] Build Date: 29 August 2012  12:12:33AM
[    15.699] xorg-server 2:1.11.4-0ubuntu10.8 (For technical support please see http://www.ubuntu.com/support) 
[    15.699] Current version of pixman: 0.24.4
[    15.699] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    15.699] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    15.699] (==) Log file: "/var/log/Xorg.0.log", Time: Sun Oct 21 11:24:50 2012
[    15.699] (==) Using config file: "/etc/X11/xorg.conf"
[    15.699] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    15.699] (==) No Layout section.  Using the first Screen section.
[    15.699] (==) No screen section available. Using defaults.
[    15.699] (**) |-->Screen "Default Screen Section" (0)
[    15.699] (**) |   |-->Monitor "<default monitor>"
[    15.699] (==) No device specified for screen "Default Screen Section".
	Using the first device section listed.
[    15.699] (**) |   |-->Device "Default Device"
[    15.699] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    15.699] (==) Automatically adding devices
[    15.699] (==) Automatically enabling devices
[    15.699] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    15.699] 	Entry deleted from font path.
[    15.699] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    15.699] 	Entry deleted from font path.
[    15.699] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    15.699] 	Entry deleted from font path.
[    15.699] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    15.699] 	Entry deleted from font path.
[    15.699] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    15.699] 	Entry deleted from font path.
[    15.699] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    15.699] 	Entry deleted from font path.
[    15.699] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins
[    15.699] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    15.699] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    15.699] (II) Loader magic: 0x7f932b40ab00
[    15.699] (II) Module ABI versions:
[    15.699] 	X.Org ANSI C Emulation: 0.4
[    15.699] 	X.Org Video Driver: 11.0
[    15.699] 	X.Org XInput driver : 16.0
[    15.699] 	X.Org Server Extension : 6.0
[    15.700] (--) PCI:*(0:0:2:0) 8086:0126:1043:2129 rev 9, Mem @ 0xdd400000/4194304, 0xb0000000/268435456, I/O @ 0x0000e000/64
[    15.700] (--) PCI: (0:1:0:0) 10de:105a:1043:2129 rev 161, Mem @ 0xdc000000/16777216, 0xc0000000/268435456, 0xd0000000/33554432, I/O @ 0x0000d000/128, BIOS @ 0x????????/524288
[    15.700] (II) Open ACPI successful (/var/run/acpid.socket)
[    15.700] (II) LoadModule: "extmod"
[    15.700] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    15.700] (II) Module extmod: vendor="X.Org Foundation"
[    15.700] 	compiled for 1.11.3, module version = 1.0.0
[    15.700] 	Module class: X.Org Server Extension
[    15.700] 	ABI class: X.Org Server Extension, version 6.0
[    15.700] (II) Loading extension MIT-SCREEN-SAVER
[    15.700] (II) Loading extension XFree86-VidModeExtension
[    15.700] (II) Loading extension XFree86-DGA
[    15.700] (II) Loading extension DPMS
[    15.700] (II) Loading extension XVideo
[    15.700] (II) Loading extension XVideo-MotionCompensation
[    15.700] (II) Loading extension X-Resource
[    15.700] (II) LoadModule: "dbe"
[    15.700] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    15.700] (II) Module dbe: vendor="X.Org Foundation"
[    15.700] 	compiled for 1.11.3, module version = 1.0.0
[    15.700] 	Module class: X.Org Server Extension
[    15.700] 	ABI class: X.Org Server Extension, version 6.0
[    15.700] (II) Loading extension DOUBLE-BUFFER
[    15.700] (II) LoadModule: "glx"
[    15.700] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[    15.707] (II) Module glx: vendor="NVIDIA Corporation"
[    15.707] 	compiled for 4.0.2, module version = 1.0.0
[    15.707] 	Module class: X.Org Server Extension
[    15.707] (II) NVIDIA GLX Module  295.40  Thu Apr  5 21:57:38 PDT 2012
[    15.707] (II) Loading extension GLX
[    15.707] (II) LoadModule: "record"
[    15.707] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    15.707] (II) Module record: vendor="X.Org Foundation"
[    15.707] 	compiled for 1.11.3, module version = 1.13.0
[    15.707] 	Module class: X.Org Server Extension
[    15.707] 	ABI class: X.Org Server Extension, version 6.0
[    15.707] (II) Loading extension RECORD
[    15.707] (II) LoadModule: "dri"
[    15.707] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    15.707] (II) Module dri: vendor="X.Org Foundation"
[    15.707] 	compiled for 1.11.3, module version = 1.0.0
[    15.707] 	ABI class: X.Org Server Extension, version 6.0
[    15.707] (II) Loading extension XFree86-DRI
[    15.707] (II) LoadModule: "dri2"
[    15.707] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    15.707] (II) Module dri2: vendor="X.Org Foundation"
[    15.707] 	compiled for 1.11.3, module version = 1.2.0
[    15.707] 	ABI class: X.Org Server Extension, version 6.0
[    15.707] (II) Loading extension DRI2
[    15.707] (==) Matched intel as autoconfigured driver 0
[    15.707] (==) Matched vesa as autoconfigured driver 1
[    15.707] (==) Matched fbdev as autoconfigured driver 2
[    15.707] (==) Assigned the driver to the xf86ConfigLayout
[    15.707] (II) LoadModule: "intel"
[    15.707] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    15.708] (II) Module intel: vendor="X.Org Foundation"
[    15.708] 	compiled for 1.11.3, module version = 2.17.0
[    15.708] 	Module class: X.Org Video Driver
[    15.708] 	ABI class: X.Org Video Driver, version 11.0
[    15.708] (II) LoadModule: "vesa"
[    15.708] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    15.708] (II) Module vesa: vendor="X.Org Foundation"
[    15.708] 	compiled for 1.11.3, module version = 2.3.0
[    15.708] 	Module class: X.Org Video Driver
[    15.708] 	ABI class: X.Org Video Driver, version 11.0
[    15.708] (II) LoadModule: "fbdev"
[    15.708] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    15.708] (II) Module fbdev: vendor="X.Org Foundation"
[    15.708] 	compiled for 1.11.3, module version = 0.4.2
[    15.708] 	ABI class: X.Org Video Driver, version 11.0
[    15.708] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
	965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
	4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
	Sandybridge Desktop (GT1), Sandybridge Desktop (GT2),
	Sandybridge Desktop (GT2+), Sandybridge Mobile (GT1),
	Sandybridge Mobile (GT2), Sandybridge Mobile (GT2+),
	Sandybridge Server, Ivybridge Mobile (GT1), Ivybridge Mobile (GT2),
	Ivybridge Desktop (GT1), Ivybridge Desktop (GT2), Ivybridge Server
[    15.708] (II) VESA: driver for VESA chipsets: vesa
[    15.708] (II) FBDEV: driver for framebuffer: fbdev
[    15.708] (++) using VT number 7

[    15.710] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    15.710] (WW) Falling back to old probe method for vesa
[    15.710] (WW) Falling back to old probe method for fbdev
[    15.710] (II) Loading sub module "fbdevhw"
[    15.710] (II) LoadModule: "fbdevhw"
[    15.710] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    15.710] (II) Module fbdevhw: vendor="X.Org Foundation"
[    15.710] 	compiled for 1.11.3, module version = 0.0.2
[    15.710] 	ABI class: X.Org Video Driver, version 11.0
[    15.710] drmOpenDevice: node name is /dev/dri/card0
[    15.710] drmOpenDevice: open result is 9, (OK)
[    15.710] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[    15.710] drmOpenDevice: node name is /dev/dri/card0
[    15.710] drmOpenDevice: open result is 9, (OK)
[    15.710] drmOpenByBusid: drmOpenMinor returns 9
[    15.710] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    15.710] (II) intel(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    15.710] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    15.710] (==) intel(0): RGB weight 888
[    15.710] (==) intel(0): Default visual is TrueColor
[    15.710] (II) intel(0): Integrated Graphics Chipset: Intel(R) Sandybridge Mobile (GT2+)
[    15.710] (--) intel(0): Chipset: "Sandybridge Mobile (GT2+)"
[    15.710] (**) intel(0): Relaxed fencing enabled
[    15.710] (**) intel(0): Wait on SwapBuffers? enabled
[    15.710] (**) intel(0): Triple buffering? enabled
[    15.710] (**) intel(0): Framebuffer tiled
[    15.710] (**) intel(0): Pixmaps tiled
[    15.710] (**) intel(0): 3D buffers tiled
[    15.710] (**) intel(0): SwapBuffers wait enabled
[    15.710] (==) intel(0): video overlay key set to 0x101fe
[    15.710] (II) intel(0): Output LVDS1 has no monitor section
[    15.710] (II) intel(0): found backlight control interface /sys/class/backlight/acpi_video0
[    15.710] (II) intel(0): Output VGA1 has no monitor section
[    15.715] (II) intel(0): Output HDMI1 has no monitor section
[    15.768] (II) intel(0): Output DP1 has no monitor section
[    15.768] (II) intel(0): EDID for output LVDS1
[    15.768] (II) intel(0): Manufacturer: CMO  Model: 1333  Serial#: 0
[    15.768] (II) intel(0): Year: 2010  Week: 32
[    15.768] (II) intel(0): EDID Version: 1.3
[    15.768] (II) intel(0): Digital Display Input
[    15.768] (II) intel(0): Max Image Size [cm]: horiz.: 29  vert.: 16
[    15.768] (II) intel(0): Gamma: 2.20
[    15.768] (II) intel(0): No DPMS capabilities specified
[    15.768] (II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    15.768] (II) intel(0): First detailed timing is preferred mode
[    15.768] (II) intel(0): redX: 0.584 redY: 0.349   greenX: 0.338 greenY: 0.574
[    15.768] (II) intel(0): blueX: 0.157 blueY: 0.126   whiteX: 0.313 whiteY: 0.329
[    15.768] (II) intel(0): Manufacturer's mask: 0
[    15.768] (II) intel(0): Supported detailed timing:
[    15.768] (II) intel(0): clock: 75.4 MHz   Image Size:  293 x 164 mm
[    15.768] (II) intel(0): h_active: 1366  h_sync: 1397  h_sync_end 1462 h_blank_end 1560 h_border: 0
[    15.768] (II) intel(0): v_active: 768  v_sync: 772  v_sync_end 784 v_blanking: 806 v_border: 0
[    15.768] (II) intel(0):  N133BGE-L41
[    15.768] (II) intel(0):  CMO
[    15.768] (II) intel(0):  N133BGE-L41
[    15.768] (II) intel(0): EDID (in hex):
[    15.768] (II) intel(0): 	00ffffffffffff000daf331300000000
[    15.768] (II) intel(0): 	20140103801d10780a98559559569328
[    15.768] (II) intel(0): 	20505400000001010101010101010101
[    15.768] (II) intel(0): 	010101010101781d56c2500026301f41
[    15.768] (II) intel(0): 	4c0025a410000018000000fe004e3133
[    15.768] (II) intel(0): 	334247452d4c34310a20000000fe0043
[    15.768] (II) intel(0): 	4d4f20202020202020202020000000fe
[    15.768] (II) intel(0): 	004e3133334247452d4c34310a20005e
[    15.768] (II) intel(0): EDID vendor "CMO", prod id 4915
[    15.768] (II) intel(0): Printing DDC gathered Modelines:
[    15.768] (II) intel(0): Modeline "1366x768"x0.0   75.44  1366 1397 1462 1560  768 772 784 806 -hsync -vsync (48.4 kHz)
[    15.768] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[    15.768] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    15.768] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    15.768] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[    15.768] (II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
[    15.768] (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
[    15.768] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[    15.768] (II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
[    15.768] (II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
[    15.768] (II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
[    15.768] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    15.768] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    15.768] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    15.768] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[    15.768] (II) intel(0): Not using default mode "720x450" (doublescan mode not supported)
[    15.768] (II) intel(0): Not using default mode "800x512" (doublescan mode not supported)
[    15.768] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    15.768] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    15.768] (II) intel(0): Not using default mode "960x540" (doublescan mode not supported)
[    15.768] (II) intel(0): Not using default mode "960x600" (doublescan mode not supported)
[    15.768] (II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
[    15.768] (II) intel(0): Printing probed modes for output LVDS1
[    15.768] (II) intel(0): Modeline "1366x768"x60.0   75.44  1366 1397 1462 1560  768 772 784 806 -hsync -vsync (48.4 kHz)
[    15.768] (II) intel(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
[    15.768] (II) intel(0): Modeline "1360x768"x60.0   72.00  1360 1408 1440 1520  768 771 781 790 +hsync -vsync (47.4 kHz)
[    15.768] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    15.768] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    15.768] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    15.768] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    15.768] (II) intel(0): EDID for output VGA1
[    15.773] (II) intel(0): EDID for output HDMI1
[    15.820] (II) intel(0): EDID for output DP1
[    15.820] (II) intel(0): Output LVDS1 connected
[    15.820] (II) intel(0): Output VGA1 disconnected
[    15.820] (II) intel(0): Output HDMI1 disconnected
[    15.820] (II) intel(0): Output DP1 disconnected
[    15.820] (II) intel(0): Using exact sizes for initial modes
[    15.820] (II) intel(0): Output LVDS1 using initial mode 1366x768
[    15.820] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    15.820] (II) intel(0): Kernel page flipping support detected, enabling
[    15.820] (**) intel(0): Display dimensions: (290, 160) mm
[    15.820] (**) intel(0): DPI set to (119, 121)
[    15.820] (II) Loading sub module "fb"
[    15.820] (II) LoadModule: "fb"
[    15.820] (II) Loading /usr/lib/xorg/modules/libfb.so
[    15.820] (II) Module fb: vendor="X.Org Foundation"
[    15.820] 	compiled for 1.11.3, module version = 1.0.0
[    15.820] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    15.820] (II) Loading sub module "dri2"
[    15.820] (II) LoadModule: "dri2"
[    15.821] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    15.821] (II) Module dri2: vendor="X.Org Foundation"
[    15.821] 	compiled for 1.11.3, module version = 1.2.0
[    15.821] 	ABI class: X.Org Server Extension, version 6.0
[    15.821] (II) UnloadModule: "vesa"
[    15.821] (II) Unloading vesa
[    15.821] (II) UnloadModule: "fbdev"
[    15.821] (II) Unloading fbdev
[    15.821] (II) UnloadModule: "fbdevhw"
[    15.821] (II) Unloading fbdevhw
[    15.821] (==) Depth 24 pixmap format is 32 bpp
[    15.821] (II) intel(0): [DRI2] Setup complete
[    15.821] (II) intel(0): [DRI2]   DRI driver: i965
[    15.821] (II) intel(0): Allocated new frame buffer 1408x768 stride 5632, tiled
[    15.822] (II) UXA(0): Driver registered support for the following operations:
[    15.822] (II)         solid
[    15.822] (II)         copy
[    15.822] (II)         composite (RENDER acceleration)
[    15.822] (II)         put_image
[    15.822] (II)         get_image
[    15.822] (==) intel(0): Backing store disabled
[    15.822] (==) intel(0): Silken mouse enabled
[    15.822] (II) intel(0): Initializing HW Cursor
[    15.880] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    15.880] (==) intel(0): DPMS enabled
[    15.880] (==) intel(0): Intel XvMC decoder enabled
[    15.880] (II) intel(0): Set up textured video
[    15.880] (II) intel(0): [XvMC] xvmc_vld driver initialized.
[    15.880] (II) intel(0): direct rendering: DRI2 Enabled
[    15.880] (WW) intel(0): Option "NoLogo" is not used
[    15.880] (==) intel(0): hotplug detection: "enabled"
[    15.880] (--) RandR disabled
[    15.880] (II) Initializing built-in extension Generic Event Extension
[    15.880] (II) Initializing built-in extension SHAPE
[    15.880] (II) Initializing built-in extension MIT-SHM
[    15.880] (II) Initializing built-in extension XInputExtension
[    15.880] (II) Initializing built-in extension XTEST
[    15.880] (II) Initializing built-in extension BIG-REQUESTS
[    15.881] (II) Initializing built-in extension SYNC
[    15.881] (II) Initializing built-in extension XKEYBOARD
[    15.881] (II) Initializing built-in extension XC-MISC
[    15.881] (II) Initializing built-in extension SECURITY
[    15.881] (II) Initializing built-in extension XINERAMA
[    15.881] (II) Initializing built-in extension XFIXES
[    15.881] (II) Initializing built-in extension RENDER
[    15.881] (II) Initializing built-in extension RANDR
[    15.881] (II) Initializing built-in extension COMPOSITE
[    15.881] (II) Initializing built-in extension DAMAGE
[    15.882] (EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
[    15.884] (II) intel(0): Setting screen physical size to 361 x 203
[    15.889] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    15.890] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    15.890] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    15.890] (II) LoadModule: "evdev"
[    15.937] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    15.937] (II) Module evdev: vendor="X.Org Foundation"
[    15.937] 	compiled for 1.11.3, module version = 2.7.0
[    15.937] 	Module class: X.Org XInput Driver
[    15.937] 	ABI class: X.Org XInput driver, version 16.0
[    15.937] (II) Using input driver 'evdev' for 'Power Button'
[    15.937] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    15.937] (**) Power Button: always reports core events
[    15.937] (**) evdev: Power Button: Device: "/dev/input/event2"
[    15.937] (--) evdev: Power Button: Vendor 0 Product 0x1
[    15.937] (--) evdev: Power Button: Found keys
[    15.937] (II) evdev: Power Button: Configuring as keyboard
[    15.937] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[    15.937] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    15.937] (**) Option "xkb_rules" "evdev"
[    15.937] (**) Option "xkb_model" "pc105"
[    15.937] (**) Option "xkb_layout" "us"
[    15.938] (II) config/udev: Adding input device Video Bus (/dev/input/event8)
[    15.938] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    15.938] (II) Using input driver 'evdev' for 'Video Bus'
[    15.938] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    15.938] (**) Video Bus: always reports core events
[    15.938] (**) evdev: Video Bus: Device: "/dev/input/event8"
[    15.938] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    15.938] (--) evdev: Video Bus: Found keys
[    15.938] (II) evdev: Video Bus: Configuring as keyboard
[    15.938] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:01/input/input8/event8"
[    15.938] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[    15.938] (**) Option "xkb_rules" "evdev"
[    15.938] (**) Option "xkb_model" "pc105"
[    15.938] (**) Option "xkb_layout" "us"
[    15.938] (II) config/udev: Adding input device Video Bus (/dev/input/event7)
[    15.938] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    15.938] (II) Using input driver 'evdev' for 'Video Bus'
[    15.938] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    15.938] (**) Video Bus: always reports core events
[    15.938] (**) evdev: Video Bus: Device: "/dev/input/event7"
[    15.938] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    15.938] (--) evdev: Video Bus: Found keys
[    15.938] (II) evdev: Video Bus: Configuring as keyboard
[    15.938] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/LNXVIDEO:00/input/input7/event7"
[    15.938] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 8)
[    15.938] (**) Option "xkb_rules" "evdev"
[    15.938] (**) Option "xkb_model" "pc105"
[    15.938] (**) Option "xkb_layout" "us"
[    15.938] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    15.938] (II) No input driver specified, ignoring this device.
[    15.938] (II) This device may have been added with another device file.
[    15.938] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
[    15.938] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    15.938] (II) Using input driver 'evdev' for 'Sleep Button'
[    15.939] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    15.939] (**) Sleep Button: always reports core events
[    15.939] (**) evdev: Sleep Button: Device: "/dev/input/event1"
[    15.939] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[    15.939] (--) evdev: Sleep Button: Found keys
[    15.939] (II) evdev: Sleep Button: Configuring as keyboard
[    15.939] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1/event1"
[    15.939] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 9)
[    15.939] (**) Option "xkb_rules" "evdev"
[    15.939] (**) Option "xkb_model" "pc105"
[    15.939] (**) Option "xkb_layout" "us"
[    15.939] (II) config/udev: Adding input device ASUS USB2.0 WebCam (/dev/input/event4)
[    15.939] (**) ASUS USB2.0 WebCam: Applying InputClass "evdev keyboard catchall"
[    15.939] (II) Using input driver 'evdev' for 'ASUS USB2.0 WebCam'
[    15.939] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    15.939] (**) ASUS USB2.0 WebCam: always reports core events
[    15.939] (**) evdev: ASUS USB2.0 WebCam: Device: "/dev/input/event4"
[    15.939] (--) evdev: ASUS USB2.0 WebCam: Vendor 0x58f Product 0xa014
[    15.939] (--) evdev: ASUS USB2.0 WebCam: Found keys
[    15.939] (II) evdev: ASUS USB2.0 WebCam: Configuring as keyboard
[    15.939] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2/1-1.2:1.0/input/input4/event4"
[    15.939] (II) XINPUT: Adding extended input device "ASUS USB2.0 WebCam" (type: KEYBOARD, id 10)
[    15.939] (**) Option "xkb_rules" "evdev"
[    15.939] (**) Option "xkb_model" "pc105"
[    15.939] (**) Option "xkb_layout" "us"
[    15.939] (II) config/udev: Adding input device HDA Intel PCH Headphone (/dev/input/event10)
[    15.939] (II) No input driver specified, ignoring this device.
[    15.939] (II) This device may have been added with another device file.
[    15.939] (II) config/udev: Adding input device HDA Intel PCH Mic (/dev/input/event9)
[    15.939] (II) No input driver specified, ignoring this device.
[    15.939] (II) This device may have been added with another device file.
[    15.940] (II) config/udev: Adding input device Asus WMI hotkeys (/dev/input/event5)
[    15.940] (**) Asus WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[    15.940] (II) Using input driver 'evdev' for 'Asus WMI hotkeys'
[    15.940] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    15.940] (**) Asus WMI hotkeys: always reports core events
[    15.940] (**) evdev: Asus WMI hotkeys: Device: "/dev/input/event5"
[    15.940] (--) evdev: Asus WMI hotkeys: Vendor 0 Product 0
[    15.940] (--) evdev: Asus WMI hotkeys: Found keys
[    15.940] (II) evdev: Asus WMI hotkeys: Configuring as keyboard
[    15.940] (**) Option "config_info" "udev:/sys/devices/platform/asus-nb-wmi/input/input5/event5"
[    15.940] (II) XINPUT: Adding extended input device "Asus WMI hotkeys" (type: KEYBOARD, id 11)
[    15.940] (**) Option "xkb_rules" "evdev"
[    15.940] (**) Option "xkb_model" "pc105"
[    15.940] (**) Option "xkb_layout" "us"
[    15.940] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    15.940] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    15.940] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    15.940] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    15.940] (**) AT Translated Set 2 keyboard: always reports core events
[    15.940] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    15.940] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    15.940] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    15.940] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    15.940] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[    15.940] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 12)
[    15.940] (**) Option "xkb_rules" "evdev"
[    15.940] (**) Option "xkb_model" "pc105"
[    15.940] (**) Option "xkb_layout" "us"
[    15.940] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event6)
[    15.940] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    15.940] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    15.940] (II) LoadModule: "synaptics"
[    15.941] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    15.941] (II) Module synaptics: vendor="X.Org Foundation"
[    15.941] 	compiled for 1.11.3, module version = 1.6.2
[    15.941] 	Module class: X.Org XInput Driver
[    15.941] 	ABI class: X.Org XInput driver, version 16.0
[    15.941] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[    15.941] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    15.941] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    15.941] (**) Option "Device" "/dev/input/event6"
[    16.204] (II) synaptics: SynPS/2 Synaptics TouchPad: ignoring touch events for semi-multitouch device
[    16.204] (--) synaptics: SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5564
[    16.204] (--) synaptics: SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4700
[    16.204] (--) synaptics: SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    16.204] (--) synaptics: SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[    16.204] (--) synaptics: SynPS/2 Synaptics TouchPad: buttons: left right double triple
[    16.204] (--) synaptics: SynPS/2 Synaptics TouchPad: Vendor 0x2 Product 0x7
[    16.204] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    16.204] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    16.248] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio4/input/input6/event6"
[    16.248] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD, id 13)
[    16.248] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[    16.248] (**) synaptics: SynPS/2 Synaptics TouchPad: MaxSpeed is now 1.75
[    16.248] (**) synaptics: SynPS/2 Synaptics TouchPad: AccelFactor is now 0.038
[    16.248] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    16.248] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[    16.248] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    16.248] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    16.248] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    16.248] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[    16.248] (**) SynPS/2 Synaptics TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"
[    16.642] (II) intel(0): EDID vendor "CMO", prod id 4915
[    16.642] (II) intel(0): Printing DDC gathered Modelines:
[    16.642] (II) intel(0): Modeline "1366x768"x0.0   75.44  1366 1397 1462 1560  768 772 784 806 -hsync -vsync (48.4 kHz)
[    19.260] (II) intel(0): EDID vendor "CMO", prod id 4915
[    19.260] (II) intel(0): Printing DDC gathered Modelines:
[    19.260] (II) intel(0): Modeline "1366x768"x0.0   75.44  1366 1397 1462 1560  768 772 784 806 -hsync -vsync (48.4 kHz)
[   113.417] (II) intel(0): EDID vendor "CMO", prod id 4915
[   113.417] (II) intel(0): Printing DDC gathered Modelines:
[   113.417] (II) intel(0): Modeline "1366x768"x0.0   75.44  1366 1397 1462 1560  768 772 784 806 -hsync -vsync (48.4 kHz)
[   114.085] (II) intel(0): EDID vendor "CMO", prod id 4915
[   114.085] (II) intel(0): Printing DDC gathered Modelines:
[   114.085] (II) intel(0): Modeline "1366x768"x0.0   75.44  1366 1397 1462 1560  768 772 784 806 -hsync -vsync (48.4 kHz)
[   115.189] (II) XKB: reuse xkmfile /var/lib/xkb/server-4B050285AA260048E61484054F3D591E0E9440EC.xkm
[   140.315] (II) intel(0): EDID vendor "CMO", prod id 4915
[   140.315] (II) intel(0): Printing DDC gathered Modelines:
[   140.315] (II) intel(0): Modeline "1366x768"x0.0   75.44  1366 1397 1462 1560  768 772 784 806 -hsync -vsync (48.4 kHz)
[  3240.418] (II) XKB: reuse xkmfile /var/lib/xkb/server-4B050285AA260048E61484054F3D591E0E9440EC.xkm
[  4287.639] (II) XKB: reuse xkmfile /var/lib/xkb/server-4B050285AA260048E61484054F3D591E0E9440EC.xkm
[  7339.454] (II) XKB: reuse xkmfile /var/lib/xkb/server-4B050285AA260048E61484054F3D591E0E9440EC.xkm
[  7422.118] (II) XKB: reuse xkmfile /var/lib/xkb/server-4B050285AA260048E61484054F3D591E0E9440EC.xkm
nahuel@nahuel:~$ 

```

THanks!

---

### Post by nsznaj on 2012-10-21
```
nahuel@nahuel:~$ cat /var/log/Xorg.0.log|grep -e WW -e EE
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    15.699] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    15.699] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    15.699] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    15.699] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    15.699] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    15.699] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    15.700] (II) Loading extension MIT-SCREEN-SAVER
[    15.710] (WW) Falling back to old probe method for vesa
[    15.710] (WW) Falling back to old probe method for fbdev
[    15.880] (WW) intel(0): Option "NoLogo" is not used
[    15.882] (EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
nahuel@nahuel:~$ 

```

---

### Post by NikTh on 2012-10-21
OK. 

This is a problem with the Nvidia driver (module). 

Now follow bellow commands with order 

```
sudo apt-get remove --purge nvidia-current 
sudo rm /etc/X11/xorg.conf

```Then

```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update 
sudo apt-get dist-upgrade
sudo apt-get install nvidia-current 
sudo nvidia-xconfig
```Then 
```
sudo add-apt-repository ppa:bumblebee/stable
sudo apt-get update
sudo apt-get install bumblebee bumblebee-nvidia
```Reboot your system.

After reboot , give again the results of 

```
/usr/lib/nux/unity_support_test -p 
cat /var/log/Xorg.0.log | grep -e WW -e EE
```Thanks

---

### Post by nsznaj on 2012-10-21
I got stuck at 



```

nahuel@nahuel:~$ sudo apt-get install nvidia-current 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  nvidia-current
0 upgraded, 1 newly installed, 0 to remove and 10 not upgraded.
Need to get 67.8 MB of archives.
After this operation, 204 MB of additional disk space will be used.
Get:1 http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/ precise/main nvidia-current amd64 304.60-0ubuntu1~precise~xup2 [67.8 MB]
Fetched 67.8 MB in 5min 3s (223 kB/s)                                          
Selecting previously unselected package nvidia-current.
(Reading database ... 309871 files and directories currently installed.)
Unpacking nvidia-current (from .../nvidia-current_304.60-0ubuntu1~precise~xup2_amd64.deb) ...
Processing triggers for man-db ...
Setting up nvidia-current (304.60-0ubuntu1~precise~xup2) ...
update-alternatives: using /usr/lib/nvidia-current/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode.
update-alternatives: using /usr/lib/nvidia-current/alt_ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode.
update-initramfs: deferring update (trigger activated)
INFO:Enable nvidia-current
DEBUG:Parsing /usr/share/nvidia-common/quirks/lenovo_thinkpad
DEBUG:Parsing /usr/share/nvidia-common/quirks/put_your_quirks_here
DEBUG:Parsing /usr/share/nvidia-common/quirks/dell_latitude
DEBUG:Processing quirk ThinkPad T420s
DEBUG:Failure to match ASUSTeK Computer Inc. with LENOVO
DEBUG:Quirk doesn't match
DEBUG:Processing quirk Latitude E6530
DEBUG:Failure to match ASUSTeK Computer Inc. with Dell Inc.
DEBUG:Quirk doesn't match
Loading new nvidia-current-304.60 DKMS files...
First Installation: checking all kernels...
Building only for 3.2.0-32-generic
Building for architecture x86_64
Building initial module for 3.2.0-32-generic
Done.

nvidia_current:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.2.0-32-generic/updates/dkms/

depmod....

DKMS: install completed.
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-32-generic
nahuel@nahuel:~$ sudo nvidia-xconfig

WARNING: Unable to locate/open X configuration file.

New X configuration file written to '/etc/X11/xorg.conf'

nahuel@nahuel:~$ 

```

---

### Post by NikTh on 2012-10-21
No , this is not a stuck .. OK , continue.. 

Thanks

---

### Post by nsznaj on 2012-10-21
Did it, rebooted, but now the configuration of the screen is changed...

help me get it right please.


Besides that, here the results

```
nahuel@nahuel:~$ /usr/lib/nux/unity_support_test -p 
Xlib:  extension "GLX" missing on display ":0.0".
Error: GLX is not available on the system
nahuel@nahuel:~$ cat /var/log/Xorg.0.log | grep -e WW -e EE
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    18.097] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    18.097] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    18.097] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    18.097] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    18.097] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    18.097] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    18.097] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[    18.097] (WW) Disabling Keyboard0
[    18.097] (WW) Disabling Mouse0
[    18.145] (II) Loading extension MIT-SCREEN-SAVER
[    19.342] (EE) No devices detected.
[    19.378] (WW) xf86OpenConsole: setpgid failed: Operation not permitted
[    19.378] (WW) xf86OpenConsole: setsid failed: Operation not permitted
[    19.379] (WW) Falling back to old probe method for vesa
[    19.379] (WW) Falling back to old probe method for fbdev
[    19.909] (EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
nahuel@nahuel:~$

```

---

### Post by NikTh on 2012-10-21
Give the results of 
```
cat /etc/bumblebee/bumblebee.conf
```

---

### Post by nsznaj on 2012-10-21
```
nahuel@nahuel:~$ cat /etc/bumblebee/bumblebee.conf
cat: /etc/bumblebee/bumblebee.conf: No such file or directory
nahuel@nahuel:~$ 

```

I must have done something wrong

---

### Post by NikTh on 2012-10-21
> **nsznaj said:**
> 
I must have done something wrong
I've done something wrong not you. Forgot the ```
sudo apt-get update
``` command in bumblebee section in 10th post. Just added. Sorry . 
Give these commands and reboot 

```
sudo add-apt-repository ppa:bumblebee/stable 
sudo apt-get update
sudo apt-get install bumblebee bumblebee-nvidia
```And then give again the results 
```
/usr/lib/nux/unity_support_test -p  
cat /var/log/Xorg.0.log | grep -e WW -e EE
dpkg -l | grep -ie nvidia -ie bumblebee 
cat /etc/bumblebee/bumblebee.conf
```Thanks

---

### Post by nsznaj on 2012-10-21
When I reboot there's this error none of the selected modes were compatible with the possible modes:

Trying modes for CRTC 63
CRTC 63: trying mode 640x480@60Hz with output at 1366x768@60Hz (pass 0)
CRTC 63: trying mode 640x480@60Hz with output at 1366x768@60Hz (pass 1)
Trying modes for CRTC 64
CRTC 64: trying mode 640x480@60Hz with output at 1366x768@60Hz (pass 0)
CRTC 64: trying mode 640x480@60Hz with output at 1366x768@60Hz (pass 1)



And the screen isn't right, one sec I'll give the results of the other commands

---

### Post by nsznaj on 2012-10-21
```
nahuel@nahuel:~$ /usr/lib/nux/unity_support_test -p 
OpenGL vendor string:   Intel Open Source Technology Center
OpenGL renderer string: Mesa DRI Intel(R) Sandybridge Mobile 
OpenGL version string:  3.0 Mesa 9.0

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes
nahuel@nahuel:~$ cat /var/log/Xorg.0.log | grep -e WW -e EE
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    17.714] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    17.714] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    17.714] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    17.735] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    17.735] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    17.735] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    17.735] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[    17.735] (WW) Disabling Keyboard0
[    17.735] (WW) Disabling Mouse0
[    17.784] (II) Loading extension MIT-SCREEN-SAVER
[    17.866] (WW) Warning, couldn't open module nvidia
[    17.866] (EE) Failed to load module "nvidia" (module does not exist, 0)
[    17.906] (WW) Falling back to old probe method for vesa
[    17.906] (WW) Falling back to old probe method for fbdev
nahuel@nahuel:~$ 

```

---

### Post by nsznaj on 2012-10-21
```

nahuel@nahuel:~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   Intel Open Source Technology Center
OpenGL renderer string: Mesa DRI Intel(R) Sandybridge Mobile 
OpenGL version string:  3.0 Mesa 9.0

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes
nahuel@nahuel:~$ cat /var/log/Xorg.0.log | grep -e WW -e EE
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    14.398] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    14.398] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    14.398] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    14.398] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    14.398] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    14.398] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    14.398] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[    14.398] (WW) Disabling Keyboard0
[    14.398] (WW) Disabling Mouse0
[    14.411] (II) Loading extension MIT-SCREEN-SAVER
[    14.417] (WW) Warning, couldn't open module nvidia
[    14.417] (EE) Failed to load module "nvidia" (module does not exist, 0)
[    14.419] (WW) Falling back to old probe method for vesa
[    14.419] (WW) Falling back to old probe method for fbdev
nahuel@nahuel:~$ dpkg -l | grep -ie nvidia -ie bumblebee
ii  bbswitch-dkms                          0.4.2-2~preciseppa1                     Interface for toggling the power on nVidia Optimus video cards
ii  bumblebee                              3.0.1-3~preciseppa1                     nVidia Optimus support
ii  bumblebee-nvidia                       3.0.1-3~preciseppa1                     nVidia Optimus support using the proprietary NVIDIA driver
ii  nvidia-common                          1:0.2.44.2                              Find obsolete NVIDIA drivers
ii  nvidia-current                         304.60-0ubuntu1~precise~xup2            NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-settings                        304.60-0ubuntu1~precise~xup2            Tool of configuring the NVIDIA graphics driver
nahuel@nahuel:~$ 

```


not working :(

---

### Post by NikTh on 2012-10-21
And this command please 

```

cat /etc/bumblebee/bumblebee.conf
```Thanks

---

### Post by nsznaj on 2012-10-21
```

nahuel@nahuel:~$ cat /etc/bumblebee/bumblebee.conf
# Configuration file for Bumblebee. Values should **not** be put between quotes

## Server options. Any change made in this section will need a server restart
# to take effect.
[bumblebeed]
# The secondary Xorg server DISPLAY number
VirtualDisplay=:8
# Should the unused Xorg server be kept running? Set this to true if waiting
# for X to be ready is too long and don't need power management at all.
KeepUnusedXServer=false
# The name of the Bumbleblee server group name (GID name)
ServerGroup=bumblebee
# Card power state at exit. Set to false if the card shoud be ON when Bumblebee
# server exits.
TurnCardOffAtExit=false
# The default behavior of '-f' option on optirun. If set to "true", '-f' will
# be ignored.
NoEcoModeOverride=false
# The Driver used by Bumblebee server. If this value is not set (or empty),
# auto-detection is performed. The available drivers are nvidia and nouveau
# (See also the driver-specific sections below)
Driver=

## Client options. Will take effect on the next optirun executed.
[optirun]
# The method used for VirtualGL to transport frames between X servers.
# Possible values are proxy, jpeg, rgb, xv and yuv.
VGLTransport=proxy
# Should the program run under optirun even if Bumblebee server or nvidia card
# is not available?
AllowFallbackToIGC=false


# Driver-specific settings are grouped under [driver-NAME]. The sections are
# parsed if the Driver setting in [bumblebeed] is set to NAME (or if auto-
# detection resolves to NAME).
# PMMethod: method to use for saving power by disabling the nvidia card, valid
# values are: auto - automatically detect which PM method to use
#         bbswitch - new in BB 3, recommended if available
#       switcheroo - vga_switcheroo method, use at your own risk
#             none - disable PM completely
# https://github.com/Bumblebee-Project/Bumblebee/wiki/Comparison-of-PM-methods

## Section with nvidia driver specific options, only parsed if Driver=nvidia
[driver-nvidia]
# Module name to load, defaults to Driver if empty or unset
KernelDriver=nvidia-current
Module=nvidia
PMMethod=auto
# colon-separated path to the nvidia libraries
LibraryPath=/usr/lib/nvidia-current:/usr/lib32/nvidia-current
# comma-separated path of the directory containing nvidia_drv.so and the
# default Xorg modules path
XorgModulePath=/usr/lib/nvidia-current/xorg,/usr/lib/xorg/modules
XorgConfFile=/etc/bumblebee/xorg.conf.nvidia

## Section with nouveau driver specific options, only parsed if Driver=nouveau
[driver-nouveau]
KernelDriver=nouveau
PMMethod=auto
XorgConfFile=/etc/bumblebee/xorg.conf.nouveau

nahuel@nahuel:~$ cat /etc/bumblebee/bumblebee.conf
# Configuration file for Bumblebee. Values should **not** be put between quotes

## Server options. Any change made in this section will need a server restart
# to take effect.
[bumblebeed]
# The secondary Xorg server DISPLAY number
VirtualDisplay=:8
# Should the unused Xorg server be kept running? Set this to true if waiting
# for X to be ready is too long and don't need power management at all.
KeepUnusedXServer=false
# The name of the Bumbleblee server group name (GID name)
ServerGroup=bumblebee
# Card power state at exit. Set to false if the card shoud be ON when Bumblebee
# server exits.
TurnCardOffAtExit=false
# The default behavior of '-f' option on optirun. If set to "true", '-f' will
# be ignored.
NoEcoModeOverride=false
# The Driver used by Bumblebee server. If this value is not set (or empty),
# auto-detection is performed. The available drivers are nvidia and nouveau
# (See also the driver-specific sections below)
Driver=

## Client options. Will take effect on the next optirun executed.
[optirun]
# The method used for VirtualGL to transport frames between X servers.
# Possible values are proxy, jpeg, rgb, xv and yuv.
VGLTransport=proxy
# Should the program run under optirun even if Bumblebee server or nvidia card
# is not available?
AllowFallbackToIGC=false


# Driver-specific settings are grouped under [driver-NAME]. The sections are
# parsed if the Driver setting in [bumblebeed] is set to NAME (or if auto-
# detection resolves to NAME).
# PMMethod: method to use for saving power by disabling the nvidia card, valid
# values are: auto - automatically detect which PM method to use
#         bbswitch - new in BB 3, recommended if available
#       switcheroo - vga_switcheroo method, use at your own risk
#             none - disable PM completely
# https://github.com/Bumblebee-Project/Bumblebee/wiki/Comparison-of-PM-methods

## Section with nvidia driver specific options, only parsed if Driver=nvidia
[driver-nvidia]
# Module name to load, defaults to Driver if empty or unset
KernelDriver=nvidia-current
Module=nvidia
PMMethod=auto
# colon-separated path to the nvidia libraries
LibraryPath=/usr/lib/nvidia-current:/usr/lib32/nvidia-current
# comma-separated path of the directory containing nvidia_drv.so and the
# default Xorg modules path
XorgModulePath=/usr/lib/nvidia-current/xorg,/usr/lib/xorg/modules
XorgConfFile=/etc/bumblebee/xorg.conf.nvidia

## Section with nouveau driver specific options, only parsed if Driver=nouveau
[driver-nouveau]
KernelDriver=nouveau
PMMethod=auto
XorgConfFile=/etc/bumblebee/xorg.conf.nouveau

nahuel@nahuel:~$ cat /etc/bumblebee/bumblebee.conf
# Configuration file for Bumblebee. Values should **not** be put between quotes

## Server options. Any change made in this section will need a server restart
# to take effect.
[bumblebeed]
# The secondary Xorg server DISPLAY number
VirtualDisplay=:8
# Should the unused Xorg server be kept running? Set this to true if waiting
# for X to be ready is too long and don't need power management at all.
KeepUnusedXServer=false
# The name of the Bumbleblee server group name (GID name)
ServerGroup=bumblebee
# Card power state at exit. Set to false if the card shoud be ON when Bumblebee
# server exits.
TurnCardOffAtExit=false
# The default behavior of '-f' option on optirun. If set to "true", '-f' will
# be ignored.
NoEcoModeOverride=false
# The Driver used by Bumblebee server. If this value is not set (or empty),
# auto-detection is performed. The available drivers are nvidia and nouveau
# (See also the driver-specific sections below)
Driver=

## Client options. Will take effect on the next optirun executed.
[optirun]
# The method used for VirtualGL to transport frames between X servers.
# Possible values are proxy, jpeg, rgb, xv and yuv.
VGLTransport=proxy
# Should the program run under optirun even if Bumblebee server or nvidia card
# is not available?
AllowFallbackToIGC=false


# Driver-specific settings are grouped under [driver-NAME]. The sections are
# parsed if the Driver setting in [bumblebeed] is set to NAME (or if auto-
# detection resolves to NAME).
# PMMethod: method to use for saving power by disabling the nvidia card, valid
# values are: auto - automatically detect which PM method to use
#         bbswitch - new in BB 3, recommended if available
#       switcheroo - vga_switcheroo method, use at your own risk
#             none - disable PM completely
# https://github.com/Bumblebee-Project/Bumblebee/wiki/Comparison-of-PM-methods

## Section with nvidia driver specific options, only parsed if Driver=nvidia
[driver-nvidia]
# Module name to load, defaults to Driver if empty or unset
KernelDriver=nvidia-current
Module=nvidia
PMMethod=auto
# colon-separated path to the nvidia libraries
LibraryPath=/usr/lib/nvidia-current:/usr/lib32/nvidia-current
# comma-separated path of the directory containing nvidia_drv.so and the
# default Xorg modules path
XorgModulePath=/usr/lib/nvidia-current/xorg,/usr/lib/xorg/modules
XorgConfFile=/etc/bumblebee/xorg.conf.nvidia

## Section with nouveau driver specific options, only parsed if Driver=nouveau
[driver-nouveau]
KernelDriver=nouveau
PMMethod=auto
XorgConfFile=/etc/bumblebee/xorg.conf.nouveau

nahuel@nahuel:~$ 


```

---

### Post by NikTh on 2012-10-21
Copy-paste carefully this command from here to your terminal .. 

```
sudo sed 's/KernelDriver=nvidia-current/KernelDriver=nvidia/g' -i /etc/bumblebee/bumblebee.conf
```Reboot your system and give the results 

```
cat /var/log/Xorg.0.log|grep -e WW -e EE
cat /etc/bumblebee/bumblebee.conf | grep KernelDriver
```Thanks

---

### Post by nsznaj on 2012-10-21
```


nahuel@nahuel:~$ sed 's/KernelDriver=nvidia-current/KernelDriver=nvidia/g' -i /etc/bumblebee/bumblebee.conf
sed: couldn't open temporary file /etc/bumblebee/sed4Gs1Yz: Permission denied
nahuel@nahuel:~$ 


```

---

### Post by NikTh on 2012-10-21
Prefix with sudo . Edited. Try again.

---

### Post by nsznaj on 2012-10-21
i added sudo and did it, now rebooting!

---

### Post by nsznaj on 2012-10-21
```
nahuel@nahuel:~$ cat /var/log/Xorg.0.log|grep -e WW -e EE
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    14.467] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    14.467] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    14.467] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    14.467] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    14.467] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    14.467] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    14.467] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[    14.467] (WW) Disabling Keyboard0
[    14.467] (WW) Disabling Mouse0
[    14.480] (II) Loading extension MIT-SCREEN-SAVER
[    14.498] (WW) Warning, couldn't open module nvidia
[    14.498] (EE) Failed to load module "nvidia" (module does not exist, 0)
[    14.500] (WW) Falling back to old probe method for vesa
[    14.500] (WW) Falling back to old probe method for fbdev
nahuel@nahuel:~$ cat /etc/bumblebee/bumblebee.conf | grep KernelDriver
KernelDriver=nvidia
KernelDriver=nouveau
nahuel@nahuel:~$ 

```

---

### Post by NikTh on 2012-10-21
Lets try something else... 

```
echo 'blacklist nouveau' | sudo tee -a /etc/modprobe.d/blacklist.conf
echo 'nvidia' | sudo tee -a /etc/modules
```You have to reboot again .. 

Give the results of 

```
cat /etc/modules
cat /etc/modprobe.d/blacklist.conf 
cat /var/log/Xorg.0.log|grep -e WW -e EE 
cat /etc/bumblebee/bumblebee.conf
lspci -nnk | grep -iA2 vga
```Thanks

---

### Post by nsznaj on 2012-10-21
```

nahuel@nahuel:~$ echo 'blacklist nouveau' | sudo tee -a /etc/modprobe.d/blacklist.conf
[sudo] password for nahuel: 
blacklist nouveau
nahuel@nahuel:~$ echo 'nvidia' | sudo tee -e /etc/modules
tee: invalid option -- 'e'
Try `tee --help' for more information.
nahuel@nahuel:~$ 

```

---

### Post by NikTh on 2012-10-21
I think I have to buy glasses , -a not -e . Edited. 

Also try these commands before reboot. 

```
sudo rm /etc/X11/xorg.conf 
sudo nvidia-xconfig
```Then reboot.

---

### Post by nsznaj on 2012-10-21
```

nahuel@nahuel:~$ echo 'nvidia' | sudo tee -a /etc/modules
nvidia
nahuel@nahuel:~$ sudo rm /etc/X11/xorg.conf 
nahuel@nahuel:~$ sudo nvidia-xconfig
sudo: nvidia-xconfig: command not found
nahuel@nahuel:~$ sudo nvidia-
nvidia-detector  nvidia-settings  
nahuel@nahuel:~$ 

```

---

### Post by NikTh on 2012-10-21
Hmmm.. weird. 

```
sudo apt-get install --reinstall nvidia-current nvidia-settings
``` 
```
sudo nvidia-xconfig
```

---

### Post by nsznaj on 2012-10-21
```
nahuel@nahuel:~$ sudo apt-get install --reinstall nvidia-current nvidia-settingsReading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 2 reinstalled, 0 to remove and 10 not upgraded.
Need to get 0 B/69.1 MB of archives.
After this operation, 0 B of additional disk space will be used.
(Reading database ... 310221 files and directories currently installed.)
Preparing to replace nvidia-current 304.60-0ubuntu1~precise~xup2 (using .../nvidia-current_304.60-0ubuntu1~precise~xup2_amd64.deb) ...
Removing all DKMS Modules
Done.
Unpacking replacement nvidia-current ...
Preparing to replace nvidia-settings 304.60-0ubuntu1~precise~xup2 (using .../nvidia-settings_304.60-0ubuntu1~precise~xup2_amd64.deb) ...
Unpacking replacement nvidia-settings ...
Processing triggers for man-db ...
Setting up nvidia-current (304.60-0ubuntu1~precise~xup2) ...
INFO:Enable nvidia-current
DEBUG:Parsing /usr/share/nvidia-common/quirks/lenovo_thinkpad
DEBUG:Parsing /usr/share/nvidia-common/quirks/put_your_quirks_here
DEBUG:Parsing /usr/share/nvidia-common/quirks/dell_latitude
DEBUG:Processing quirk ThinkPad T420s
DEBUG:Failure to match ASUSTeK Computer Inc. with LENOVO
DEBUG:Quirk doesn't match
DEBUG:Processing quirk Latitude E6530
DEBUG:Failure to match ASUSTeK Computer Inc. with Dell Inc.
DEBUG:Quirk doesn't match
Loading new nvidia-current-304.60 DKMS files...
Building only for 3.2.0-32-generic
Building for architecture x86_64
Building initial module for 3.2.0-32-generic
Done.

nvidia_current:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.2.0-32-generic/updates/dkms/

depmod....

DKMS: install completed.
Setting up nvidia-settings (304.60-0ubuntu1~precise~xup2) ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
nahuel@nahuel:~$ sudo nvidia-xconfig
sudo: nvidia-xconfig: command not found
nahuel@nahuel:~$ 

```

---

### Post by NikTh on 2012-10-21
Try 

```
sudo apt-get install ppa-purge
sudo ppa-purge ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get dist-upgrade 
sudo nvidia-xconfig
```

Thanks

---

### Post by nsznaj on 2012-10-21
```


nahuel@nahuel:~$ sudo nvidia-xconfig
sudo: nvidia-xconfig: command not found
nahuel@nahuel:~$ 

```

still not working,
shall I reboot first?

---

### Post by nsznaj on 2012-10-21
```

nahuel@nahuel:~$ cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
rtc

# Generated by sensors-detect on Sat Oct 13 15:01:49 2012
# Chip drivers
coretemp
nvidia
nahuel@nahuel:~$ cat /etc/modprobe.d/blacklist.conf 
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
blacklist nouveau
nahuel@nahuel:~$ cat /var/log/Xorg.0.log|grep -e WW -e EE 
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    17.829] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    17.829] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    17.829] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    17.829] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    17.829] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    17.829] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    17.866] (II) Loading extension MIT-SCREEN-SAVER
[    18.048] (WW) Falling back to old probe method for vesa
[    18.048] (WW) Falling back to old probe method for fbdev
nahuel@nahuel:~$ cat /etc/bumblebee/bumblebee.conf
# Configuration file for Bumblebee. Values should **not** be put between quotes

## Server options. Any change made in this section will need a server restart
# to take effect.
[bumblebeed]
# The secondary Xorg server DISPLAY number
VirtualDisplay=:8
# Should the unused Xorg server be kept running? Set this to true if waiting
# for X to be ready is too long and don't need power management at all.
KeepUnusedXServer=false
# The name of the Bumbleblee server group name (GID name)
ServerGroup=bumblebee
# Card power state at exit. Set to false if the card shoud be ON when Bumblebee
# server exits.
TurnCardOffAtExit=false
# The default behavior of '-f' option on optirun. If set to "true", '-f' will
# be ignored.
NoEcoModeOverride=false
# The Driver used by Bumblebee server. If this value is not set (or empty),
# auto-detection is performed. The available drivers are nvidia and nouveau
# (See also the driver-specific sections below)
Driver=

## Client options. Will take effect on the next optirun executed.
[optirun]
# The method used for VirtualGL to transport frames between X servers.
# Possible values are proxy, jpeg, rgb, xv and yuv.
VGLTransport=proxy
# Should the program run under optirun even if Bumblebee server or nvidia card
# is not available?
AllowFallbackToIGC=false


# Driver-specific settings are grouped under [driver-NAME]. The sections are
# parsed if the Driver setting in [bumblebeed] is set to NAME (or if auto-
# detection resolves to NAME).
# PMMethod: method to use for saving power by disabling the nvidia card, valid
# values are: auto - automatically detect which PM method to use
#         bbswitch - new in BB 3, recommended if available
#       switcheroo - vga_switcheroo method, use at your own risk
#             none - disable PM completely
# https://github.com/Bumblebee-Project/Bumblebee/wiki/Comparison-of-PM-methods

## Section with nvidia driver specific options, only parsed if Driver=nvidia
[driver-nvidia]
# Module name to load, defaults to Driver if empty or unset
KernelDriver=nvidia
Module=nvidia
PMMethod=auto
# colon-separated path to the nvidia libraries
LibraryPath=/usr/lib/nvidia-current:/usr/lib32/nvidia-current
# comma-separated path of the directory containing nvidia_drv.so and the
# default Xorg modules path
XorgModulePath=/usr/lib/nvidia-current/xorg,/usr/lib/xorg/modules
XorgConfFile=/etc/bumblebee/xorg.conf.nvidia

## Section with nouveau driver specific options, only parsed if Driver=nouveau
[driver-nouveau]
KernelDriver=nouveau
PMMethod=auto
XorgConfFile=/etc/bumblebee/xorg.conf.nouveau

nahuel@nahuel:~$ lspci -nnk | grep -iA2 vga
00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0126] (rev 09)
	Subsystem: ASUSTeK Computer Inc. Device [1043:2129]
	Kernel driver in use: i915
--
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation Device [10de:105a] (rev ff)
04:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
	Subsystem: AzureWave AW-NB037H 802.11bgn Wireless Half-size Mini PCIe Card [AR9002WB-1NGCD] [1a3b:2c37]
nahuel@nahuel:~$ 



```

---

### Post by NikTh on 2012-10-21
Lets try one more time.. 

```
sudo apt-get purge nvidia*
sudo apt-get purge bumblebee*
sudo rm /etc/X11/xorg.conf
sudo rm /etc/bumblebee/bumblebee.conf
``` 

Then 

```
sudo apt-get install nvidia-current 
sudo apt-get install bumblebee bumblebee-nvidia
```

Reboot after that and tell me if graphics are OK.

---

### Post by nsznaj on 2012-10-21
graphics are OK now, I haven't done your last post yet.

But, still not working this:

```
nahuel@nahuel:~$ sudo nvidia-xconfig
[sudo] password for nahuel: 
sudo: nvidia-xconfig: command not found
nahuel@nahuel:~$ 

```


Shall I try again anyway? 

(temperatures got a bit higher though, 48-53 C on average)

---

### Post by NikTh on 2012-10-21
This command maybe not supported due to bumblebee installation. Xorg.conf file (that command generates) is not supported well. 

If the graphics are OK , then give the result of command 

```
/usr/lib/nux/unity_support_test -p
```

---

### Post by nsznaj on 2012-10-21
```
nahuel@nahuel:~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) Sandybridge Mobile 
OpenGL version string:  3.0 Mesa 8.0.4

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes
nahuel@nahuel:~$ 

```

---

### Post by NikTh on 2012-10-21
OK, you are using the Intel card now. 

Lets try to see if bumblebee works OK. 

What is the result ? 

```
optirun nvidia-settings -c :8
```

---

### Post by nsznaj on 2012-10-21
it opened the NVIDIA X Server Settings


please find a print screen attached

---

### Post by NikTh on 2012-10-21
Hooray !! :) 

Your hybrid graphics card configured correctly.. everything seems to work as it should. 

As for the fan.. watch it 1-2 days and if still make a lot of noise come back , I will give you something to add , for extra power-saving with the intel card. (this card you will use mostly). 

And for your temperatures , do not bother for 2-3-4 degrees.. My temperatures are 50 to 60 . Do not forget it is a Laptop. Very good temperatures. 
Thanks

---

### Post by nsznaj on 2012-10-21
Thanks a lot for this supportive help!

Excellent, I'll live this thread open for a few days when I tell you how this goes.

Thank you !

---

### Post by nsznaj on 2012-10-23
Hi again

She keeps complaining. It goes like 10 seconds per minute. It vibrates and makes a noticeable (not too loud) noise.

Also, using kile I hear a low sound (like a fast clock ticking)  every time I press a key :( Is that normal?


Thanks!

---

### Post by NikTh on 2012-10-23
Give the results of ```
cat /etc/default/grub
``` and we will try an option for the Intel card that sets the card in a low power state when its idle. 

Cannot go further , I don't know something else except this parameter. 
Maybe you should look the hardware .

---

### Post by nsznaj on 2012-10-23
OK, here the result

> 
nahuel@nahuel:~$ cat /etc/default/grub
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
nahuel@nahuel:~$ 


---

### Post by NikTh on 2012-10-23
First give this command (copy-paste from here)

```
sudo sed 's/GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"/GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i915.i915_enable_rc6=1"/' -i /etc/default/grub
```
To check the change give this command ```
cat /etc/default/grub | grep GRUB_CMDLINE
```The result must be ```
**[COLOR=Red]GRUB_CMDLINE[/COLOR]**_LINUX_DEFAULT="quiet splash i915.i915_enable_rc6=1"
[COLOR=Red]**GRUB_CMDLINE**[/COLOR]_LINUX=""
```Then run ```
sudo update-grub
```and reboot.

Thanks

---

### Post by nsznaj on 2012-10-23
OK

I did it, the result afterwards was the same as yours.

BTW, what does this command mean? What changed?

code: 
```

sudo sed 's/GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"/GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i915.i915_enable_rc6=1"/' -i /etc/default/grub


```




However, at least at the moment I find everything unchanged...

Thank you anyway!!! You're great!

---

### Post by NikTh on 2012-10-24
Cannot do anything else. If this is a hardware problem (fan) you should check it. 

The command changes this line ```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
``` to this 
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i915.i915_enable_rc6=1"
```This is the parameter I told you about the power-save with Intel card. We enabled this through the boot-loader (grub) in the kernel. By default is disabled. 

Thanks

---

### Post by nsznaj on 2012-12-09
Hi my friend, 

Do you know how to truly set the screen brightness for once and for ever?

It changes wildly, it increases a lot. I can't seem to find the proper commands, I found this to set the brightness down:
```
echo 300 > /sys/class/backlight/intel_backlight/brightness

```
but after a while it increases again...

The keys Fn+F5 and  Fn+F6 work fine, but the lowest they can get is still too bright, that's why I'm using the backlight command on the terminal.

Any hints?
Thanks

---

