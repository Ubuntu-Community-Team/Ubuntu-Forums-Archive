---
title: "Ubuntu 18.04.1 Unable to set 1600x1200 Resolution"
date: 2018-09-10
forum: New to Ubuntu
---

### Post by maweb on 2018-09-10
Hi, I'm new to this software, after over 20 years of different windows systems.

The  problem I pose is that I have a 24-inch monitor, (Samsung P24FHD) in windows I use a  resolution of 1600x1200 pixels, instead Ubuntu gives me only as a  maximum of 1600x900 pixels.
[B]The monitor is connected to the graphics card via a dvi-vga adapter cable
[/B]
Following some threads in various forums, I tried to make a configuration via a terminal that i submit:

```
~$ xrandr
Screen 0: minimum 8 x 8, current 1600 x 900, maximum 16384 x 16384
DVI-I-0[/B] connected primary 1600x900+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768      60.00 +
   1600x900      59.82* 
   1400x900      59.88  
   1368x768      59.88    59.85  
   1360x768      59.96    59.80  
   1280x800      59.91    59.81  
   1280x720      59.86    59.74  
   1152x864      60.00  
   1024x576      59.90    59.82  
   960x540       59.82    59.63  
   864x486       59.92    59.57  
   800x600       72.19    60.32    56.25  
   800x450       59.82  
   700x450       59.88  
   684x384       59.88    59.85  
   680x384       59.96    59.80  
   640x480       59.94  
   640x400       59.98    59.88  
   640x360       59.86    59.83  
   512x384       60.00  
   512x288       60.00    59.92  
   480x270       59.82    59.63  
   432x243       59.92    59.57  
   400x300       72.19  
   320x240       60.05  
DVI-I-1 disconnected (normal left inverted right x axis y axis)
HDMI-0 disconnected (normal left inverted right x axis y axis)
DP-0 disconnected (normal left inverted right x axis y axis)
DVI-D-0 disconnected (normal left inverted right x axis y axis)
DP-1 disconnected (normal left inverted right x axis y axis)

```
**Then:**

```
~$ cvt 1600 1200
# 1600x1200 59.87 Hz (CVT 1.92M3) hsync: 74.54 kHz; pclk: 161.00 MHz
Modeline "1600x1200_60.00"  161.00  1600 1712 1880 2160  1200 1203 1207 1245 -hsync +vsync
```

**Then:**

```
~$ sudo xrandr --newmode "1600x1200_60.00"  161.00  1600 1712 1880 2160  1200 1203 1207 1245 -hsync +vsync
```

**Then:**

```
~$ sudo xrandr --addmode DVI-I-0 "1600x1200_60.00"
```

**Result:**

```
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  140 (RANDR)
  Minor opcode of failed request:  18 (RRAddOutputMode)
  Serial number of failed request:  39
  Current serial number in output stream:  40

```
The graphics card is the **Nvidia GeForce GTX 660**
The driver is **NVIDIA-SMI 390.48** "In use NVIDIA metapackage driver from nvidia-driver-390 (owner, tested)"

Also with the  1600x900 resolution I have the problem that the desktop is vertically  long, cut in the lower part, that is not centered rightly vertically.

I do not know what fish to take and a help would be welcome, thank you very much.

---

### Post by Autodave on 2018-09-10
You may be restricting the resolution because of the VGA cable?  Usually, 1600 x 900 is the max you can get from VGA.  Can you hook it up w/o using VGA in the mix?

I have also run into cheap VGA cords that don't have one particular wire in them (and I can't remember what # it is in) that do not send out from the monitor the monitor's max resolution to inform the video card.

At the very least, try another VGA cable. But, you will probably be better getting VGA out of the equation.

---

### Post by NM5TF on 2018-09-10
you might try this...

```
xrandr --output DVI-I-0 --mode "1600x1200_60.00"
```

tommy

---

### Post by Yellow Pasque on 2018-09-11
Looking at the available resolutions and comparing to the manual, I would guess that you're being limited to modes with 60Hz VertRefresh. You can post /var/log/Xorg.0.log to confirm (use code tags or pastebin). 
You may have to manually specify Horizsync and Vertrefresh and use something like: 
```
Option "UseEDIDFreqs" "FALSE"
```
in xorg.conf

> Also with the 1600x900 resolution I have the problem that the desktop is vertically long, cut in the lower part, that is not centered rightly vertically.
You may want to check the settings on the TV/display itself, and make sure it's not set to stretch.

---

### Post by maweb on 2018-09-11
> **Temüjin said:**
> Looking at the available resolutions and comparing to the manual, I would guess that you're being limited to modes with 60Hz VertRefresh. You can post /var/log/Xorg.0.log to confirm (use code tags or pastebin). 
You may have to manually specify Horizsync and Vertrefresh and use something like: 
```
Option "UseEDIDFreqs" "FALSE"
```
in xorg.conf


You may want to check the settings on the TV/display itself, and make sure it's not set to stretch.

Here yo are...



```
[    58.897] (--) Log file renamed from "/var/log/Xorg.pid-1141.log" to "/var/log/Xorg.0.log"
[    58.898] 
X.Org X Server 1.19.6
Release Date: 2017-12-20
[    58.898] X Protocol Version 11, Revision 0
[    58.898] Build Operating System: Linux 4.4.0-119-generic x86_64 Ubuntu
[    58.898] Current Operating System: Linux mauro-linux-pc 4.15.0-34-generic #37-Ubuntu SMP Mon Aug 27 15:21:48 UTC 2018 x86_64
[    58.898] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.15.0-34-generic root=UUID=08d426ce-a730-4fa9-a294-1f43b2b9858a ro quiet splash vt.handoff=1
[    58.898] Build Date: 13 April 2018  08:07:36PM
[    58.898] xorg-server 2:1.19.6-1ubuntu4 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    58.898] Current version of pixman: 0.34.0
[    58.898]     Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
[    58.898] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    58.898] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Sep 11 17:41:28 2018
[    58.898] (==) Using config file: "/etc/X11/xorg.conf"
[    58.898] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    58.898] (==) ServerLayout "Layout0"
[    58.898] (**) |-->Screen "Screen0" (0)
[    58.898] (**) |   |-->Monitor "Monitor0"
[    58.898] (**) |   |-->Device "Device0"
[    58.898] (**) |-->Input Device "Keyboard0"
[    58.898] (**) |-->Input Device "Mouse0"
[    58.898] (**) Option "Xinerama" "0"
[    58.898] (==) Automatically adding devices
[    58.898] (==) Automatically enabling devices
[    58.898] (==) Automatically adding GPU devices
[    58.898] (==) Automatically binding GPU devices
[    58.898] (==) Max clients allowed: 256, resource mask: 0x1fffff
[    58.898] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    58.898]     Entry deleted from font path.
[    58.898] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    58.898]     Entry deleted from font path.
[    58.898] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    58.898]     Entry deleted from font path.
[    58.898] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    58.898]     Entry deleted from font path.
[    58.898] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    58.898]     Entry deleted from font path.
[    58.899] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    58.899] (==) ModulePath set to "/usr/lib/xorg/modules"
[    58.899] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[    58.899] (WW) Disabling Keyboard0
[    58.899] (WW) Disabling Mouse0
[    58.899] (II) Loader magic: 0x55f368177020
[    58.899] (II) Module ABI versions:
[    58.899]     X.Org ANSI C Emulation: 0.4
[    58.899]     X.Org Video Driver: 23.0
[    58.899]     X.Org XInput driver : 24.1
[    58.899]     X.Org Server Extension : 10.0
[    58.899] (++) using VT number 1

[    58.900] (II) systemd-logind: took control of session /org/freedesktop/login1/session/c2
[    58.900] (II) xfree86: Adding drm device (/dev/dri/card0)
[    58.900] (II) systemd-logind: got fd for /dev/dri/card0 226:0 fd 12 paused 0
[    58.901] (**) OutputClass "nvidia" ModulePath extended to "/usr/lib/x86_64-linux-gnu/nvidia/xorg,/usr/lib/xorg/modules"
[    58.902] (--) PCI:*(0:1:0:0) 10de:11c0:1043:843b rev 161, Mem @ 0xee000000/16777216, 0xe0000000/134217728, 0xe8000000/33554432, I/O @ 0x0000e000/128, BIOS @ 0x????????/131072
[    58.902] (II) "glx" will be loaded. This was enabled by default and also specified in the config file.
[    58.902] (II) LoadModule: "dbe"
[    58.902] (II) Module "dbe" already built-in
[    58.902] (II) LoadModule: "extmod"
[    58.902] (II) Module "extmod" already built-in
[    58.902] (II) LoadModule: "glx"
[    58.902] (II) Loading /usr/lib/x86_64-linux-gnu/nvidia/xorg/libglx.so
[    59.327] (II) Module glx: vendor="NVIDIA Corporation"
[    59.327]     compiled for 4.0.2, module version = 1.0.0
[    59.327]     Module class: X.Org Server Extension
[    59.328] (II) NVIDIA GLX Module  390.48  Wed Mar 21 23:42:56 PDT 2018
[    59.336] (II) LoadModule: "nvidia"
[    59.336] (II) Loading /usr/lib/x86_64-linux-gnu/nvidia/xorg/nvidia_drv.so
[    59.336] (II) Module nvidia: vendor="NVIDIA Corporation"
[    59.336]     compiled for 4.0.2, module version = 1.0.0
[    59.336]     Module class: X.Org Video Driver
[    59.336] (II) NVIDIA dlloader X Driver  390.48  Wed Mar 21 23:18:15 PDT 2018
[    59.336] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    59.336] (II) systemd-logind: releasing fd for 226:0
[    59.337] (II) Loading sub module "fb"
[    59.337] (II) LoadModule: "fb"
[    59.349] (II) Loading /usr/lib/xorg/modules/libfb.so
[    59.349] (II) Module fb: vendor="X.Org Foundation"
[    59.349]     compiled for 1.19.6, module version = 1.0.0
[    59.349]     ABI class: X.Org ANSI C Emulation, version 0.4
[    59.349] (II) Loading sub module "wfb"
[    59.349] (II) LoadModule: "wfb"
[    59.349] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    59.349] (II) Module wfb: vendor="X.Org Foundation"
[    59.349]     compiled for 1.19.6, module version = 1.0.0
[    59.349]     ABI class: X.Org ANSI C Emulation, version 0.4
[    59.349] (II) Loading sub module "ramdac"
[    59.349] (II) LoadModule: "ramdac"
[    59.349] (II) Module "ramdac" already built-in
[    59.350] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[    59.350] (==) NVIDIA(0): RGB weight 888
[    59.350] (==) NVIDIA(0): Default visual is TrueColor
[    59.350] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    59.350] (II) Applying OutputClass "nvidia" options to /dev/dri/card0
[    59.350] (**) NVIDIA(0): Option "Stereo" "0"
[    59.350] (**) NVIDIA(0): Option "nvidiaXineramaInfoOrder" "CRT-0"
[    59.350] (**) NVIDIA(0): Option "SLI" "Off"
[    59.350] (**) NVIDIA(0): Option "MultiGPU" "Off"
[    59.350] (**) NVIDIA(0): Option "BaseMosaic" "off"
[    59.350] (**) NVIDIA(0): Option "AllowEmptyInitialConfiguration"
[    59.350] (**) NVIDIA(0): Stereo disabled by request
[    59.350] (**) NVIDIA(0): NVIDIA SLI disabled.
[    59.350] (**) NVIDIA(0): NVIDIA Multi-GPU disabled.
[    59.350] (**) NVIDIA(0): Option "MetaModes" "nvidia-auto-select +0+0"
[    59.350] (**) NVIDIA(0): Enabling 2D acceleration
[    59.621] (--) NVIDIA(0): Valid display device(s) on GPU-0 at PCI:1:0:0
[    59.621] (--) NVIDIA(0):     CRT-0 (boot)
[    59.621] (--) NVIDIA(0):     DFP-0
[    59.621] (--) NVIDIA(0):     DFP-1
[    59.621] (--) NVIDIA(0):     DFP-2
[    59.621] (--) NVIDIA(0):     DFP-3
[    59.621] (--) NVIDIA(0):     DFP-4
[    59.622] (II) NVIDIA(0): NVIDIA GPU GeForce GTX 660 (GK106) at PCI:1:0:0 (GPU-0)
[    59.622] (--) NVIDIA(0): Memory: 2097152 kBytes
[    59.622] (--) NVIDIA(0): VideoBIOS: 80.06.58.00.09
[    59.622] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[    59.638] (--) NVIDIA(GPU-0): CRT-0: connected
[    59.638] (--) NVIDIA(GPU-0): CRT-0: 400.0 MHz maximum pixel clock
[    59.638] (--) NVIDIA(GPU-0): 
[    59.652] (--) NVIDIA(GPU-0): DFP-0: disconnected
[    59.652] (--) NVIDIA(GPU-0): DFP-0: Internal TMDS
[    59.652] (--) NVIDIA(GPU-0): DFP-0: 330.0 MHz maximum pixel clock
[    59.652] (--) NVIDIA(GPU-0): 
[    59.652] (--) NVIDIA(GPU-0): DFP-1: disconnected
[    59.652] (--) NVIDIA(GPU-0): DFP-1: Internal TMDS
[    59.652] (--) NVIDIA(GPU-0): DFP-1: 165.0 MHz maximum pixel clock
[    59.652] (--) NVIDIA(GPU-0): 
[    59.652] (--) NVIDIA(GPU-0): DFP-2: disconnected
[    59.652] (--) NVIDIA(GPU-0): DFP-2: Internal TMDS
[    59.652] (--) NVIDIA(GPU-0): DFP-2: 165.0 MHz maximum pixel clock
[    59.652] (--) NVIDIA(GPU-0): 
[    59.652] (--) NVIDIA(GPU-0): DFP-3: disconnected
[    59.652] (--) NVIDIA(GPU-0): DFP-3: Internal TMDS
[    59.652] (--) NVIDIA(GPU-0): DFP-3: 330.0 MHz maximum pixel clock
[    59.652] (--) NVIDIA(GPU-0): 
[    59.652] (--) NVIDIA(GPU-0): DFP-4: disconnected
[    59.652] (--) NVIDIA(GPU-0): DFP-4: Internal DisplayPort
[    59.652] (--) NVIDIA(GPU-0): DFP-4: 960.0 MHz maximum pixel clock
[    59.652] (--) NVIDIA(GPU-0): 
[    59.655] (II) NVIDIA(0): Validated MetaModes:
[    59.655] (II) NVIDIA(0):     "nvidia-auto-select+0+0"
[    59.655] (II) NVIDIA(0): Virtual screen size determined to be 1024 x 768
[    59.659] (WW) NVIDIA(0): CRT-0 does not have an EDID, or its EDID does not contain a
[    59.659] (WW) NVIDIA(0):     maximum image size; cannot compute DPI from CRT-0's EDID.
[    59.659] (==) NVIDIA(0): DPI set to (75, 75); computed from built-in default
[    59.659] (--) Depth 24 pixmap format is 32 bpp
[    59.660] (II) NVIDIA: Using 6144.00 MB of virtual memory for indirect memory
[    59.660] (II) NVIDIA:     access.
[    59.673] (II) NVIDIA(0): Setting mode "nvidia-auto-select+0+0"
[    59.723] (==) NVIDIA(0): Disabling shared memory pixmaps
[    59.723] (==) NVIDIA(0): Backing store enabled
[    59.723] (==) NVIDIA(0): Silken mouse enabled
[    59.724] (**) NVIDIA(0): DPMS enabled
[    59.740] (II) Loading sub module "dri2"
[    59.740] (II) LoadModule: "dri2"
[    59.740] (II) Module "dri2" already built-in
[    59.740] (II) NVIDIA(0): [DRI2] Setup complete
[    59.740] (II) NVIDIA(0): [DRI2]   VDPAU driver: nvidia
[    59.740] (--) RandR disabled
[    59.742] (II) SELinux: Disabled on system
[    59.743] (II) Initializing extension GLX
[    59.743] (II) Indirect GLX disabled.
[    59.883] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    59.883] (**) Power Button: Applying InputClass "libinput keyboard catchall"
[    59.883] (II) LoadModule: "libinput"
[    59.883] (II) Loading /usr/lib/xorg/modules/input/libinput_drv.so
[    59.884] (II) Module libinput: vendor="X.Org Foundation"
[    59.884]     compiled for 1.19.6, module version = 0.27.1
[    59.884]     Module class: X.Org XInput Driver
[    59.884]     ABI class: X.Org XInput driver, version 24.1
[    59.884] (II) Using input driver 'libinput' for 'Power Button'
[    59.884] (II) systemd-logind: got fd for /dev/input/event1 13:65 fd 38 paused 0
[    59.884] (**) Power Button: always reports core events
[    59.884] (**) Option "Device" "/dev/input/event1"
[    59.884] (**) Option "_source" "server/udev"
[    59.885] (II) event1  - Power Button: is tagged by udev as: Keyboard
[    59.885] (II) event1  - Power Button: device is a keyboard
[    59.885] (II) event1  - Power Button: device removed
[    59.885] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    59.885] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    59.885] (**) Option "xkb_model" "pc105"
[    59.885] (**) Option "xkb_layout" "it"
[    59.894] (II) event1  - Power Button: is tagged by udev as: Keyboard
[    59.894] (II) event1  - Power Button: device is a keyboard
[    59.894] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    59.894] (**) Power Button: Applying InputClass "libinput keyboard catchall"
[    59.894] (II) Using input driver 'libinput' for 'Power Button'
[    59.895] (II) systemd-logind: got fd for /dev/input/event0 13:64 fd 41 paused 0
[    59.895] (**) Power Button: always reports core events
[    59.895] (**) Option "Device" "/dev/input/event0"
[    59.895] (**) Option "_source" "server/udev"
[    59.895] (II) event0  - Power Button: is tagged by udev as: Keyboard
[    59.895] (II) event0  - Power Button: device is a keyboard
[    59.895] (II) event0  - Power Button: device removed
[    59.895] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
[    59.895] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    59.895] (**) Option "xkb_model" "pc105"
[    59.895] (**) Option "xkb_layout" "it"
[    59.896] (II) event0  - Power Button: is tagged by udev as: Keyboard
[    59.896] (II) event0  - Power Button: device is a keyboard
[    59.896] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=3 (/dev/input/event13)
[    59.896] (II) No input driver specified, ignoring this device.
[    59.896] (II) This device may have been added with another device file.
[    59.896] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=7 (/dev/input/event14)
[    59.896] (II) No input driver specified, ignoring this device.
[    59.896] (II) This device may have been added with another device file.
[    59.897] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=8 (/dev/input/event15)
[    59.897] (II) No input driver specified, ignoring this device.
[    59.897] (II) This device may have been added with another device file.
[    59.897] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=9 (/dev/input/event16)
[    59.897] (II) No input driver specified, ignoring this device.
[    59.897] (II) This device may have been added with another device file.
[    59.897] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event2)
[    59.897] (**) Logitech USB Receiver: Applying InputClass "libinput keyboard catchall"
[    59.897] (II) Using input driver 'libinput' for 'Logitech USB Receiver'
[    59.898] (II) systemd-logind: got fd for /dev/input/event2 13:66 fd 42 paused 0
[    59.898] (**) Logitech USB Receiver: always reports core events
[    59.898] (**) Option "Device" "/dev/input/event2"
[    59.898] (**) Option "_source" "server/udev"
[    59.898] (II) event2  - Logitech USB Receiver: is tagged by udev as: Keyboard
[    59.898] (II) event2  - Logitech USB Receiver: device is a keyboard
[    59.898] (II) event2  - Logitech USB Receiver: device removed
[    59.899] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb3/3-5/3-5:1.0/0003:046D:C534.0001/input/input2/event2"
[    59.899] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD, id 8)
[    59.899] (**) Option "xkb_model" "pc105"
[    59.899] (**) Option "xkb_layout" "it"
[    59.899] (II) event2  - Logitech USB Receiver: is tagged by udev as: Keyboard
[    59.899] (II) event2  - Logitech USB Receiver: device is a keyboard
[    59.900] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event3)
[    59.900] (**) Logitech USB Receiver: Applying InputClass "libinput pointer catchall"
[    59.900] (**) Logitech USB Receiver: Applying InputClass "libinput keyboard catchall"
[    59.900] (II) Using input driver 'libinput' for 'Logitech USB Receiver'
[    59.900] (II) systemd-logind: got fd for /dev/input/event3 13:67 fd 43 paused 0
[    59.900] (**) Logitech USB Receiver: always reports core events
[    59.900] (**) Option "Device" "/dev/input/event3"
[    59.900] (**) Option "_source" "server/udev"
[    59.901] (II) event3  - Logitech USB Receiver: is tagged by udev as: Keyboard Mouse
[    59.901] (II) event3  - Logitech USB Receiver: device is a pointer
[    59.901] (II) event3  - Logitech USB Receiver: device is a keyboard
[    59.901] (II) event3  - Logitech USB Receiver: device removed
[    59.901] (II) libinput: Logitech USB Receiver: needs a virtual subdevice
[    59.901] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb3/3-5/3-5:1.1/0003:046D:C534.0002/input/input3/event3"
[    59.901] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: MOUSE, id 9)
[    59.901] (**) Option "AccelerationScheme" "none"
[    59.901] (**) Logitech USB Receiver: (accel) selected scheme none/0
[    59.901] (**) Logitech USB Receiver: (accel) acceleration factor: 2.000
[    59.901] (**) Logitech USB Receiver: (accel) acceleration threshold: 4
[    59.901] (II) event3  - Logitech USB Receiver: is tagged by udev as: Keyboard Mouse
[    59.901] (II) event3  - Logitech USB Receiver: device is a pointer
[    59.901] (II) event3  - Logitech USB Receiver: device is a keyboard
[    59.902] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/mouse0)
[    59.902] (II) No input driver specified, ignoring this device.
[    59.902] (II) This device may have been added with another device file.
[    59.902] (II) config/udev: Adding input device HDA Intel PCH Line Out CLFE (/dev/input/event10)
[    59.902] (II) No input driver specified, ignoring this device.
[    59.902] (II) This device may have been added with another device file.
[    59.902] (II) config/udev: Adding input device HDA Intel PCH Line Out Side (/dev/input/event11)
[    59.902] (II) No input driver specified, ignoring this device.
[    59.902] (II) This device may have been added with another device file.
[    59.903] (II) config/udev: Adding input device HDA Intel PCH Front Headphone (/dev/input/event12)
[    59.903] (II) No input driver specified, ignoring this device.
[    59.903] (II) This device may have been added with another device file.
[    59.903] (II) config/udev: Adding input device HDA Intel PCH Front Mic (/dev/input/event5)
[    59.903] (II) No input driver specified, ignoring this device.
[    59.903] (II) This device may have been added with another device file.
[    59.903] (II) config/udev: Adding input device HDA Intel PCH Rear Mic (/dev/input/event6)
[    59.903] (II) No input driver specified, ignoring this device.
[    59.903] (II) This device may have been added with another device file.
[    59.903] (II) config/udev: Adding input device HDA Intel PCH Line (/dev/input/event7)
[    59.903] (II) No input driver specified, ignoring this device.
[    59.903] (II) This device may have been added with another device file.
[    59.904] (II) config/udev: Adding input device HDA Intel PCH Line Out Front (/dev/input/event8)
[    59.904] (II) No input driver specified, ignoring this device.
[    59.904] (II) This device may have been added with another device file.
[    59.904] (II) config/udev: Adding input device HDA Intel PCH Line Out Surround (/dev/input/event9)
[    59.904] (II) No input driver specified, ignoring this device.
[    59.904] (II) This device may have been added with another device file.
[    59.904] (II) config/udev: Adding input device Eee PC WMI hotkeys (/dev/input/event4)
[    59.904] (**) Eee PC WMI hotkeys: Applying InputClass "libinput keyboard catchall"
[    59.904] (II) Using input driver 'libinput' for 'Eee PC WMI hotkeys'
[    59.904] (II) systemd-logind: got fd for /dev/input/event4 13:68 fd 44 paused 0
[    59.904] (**) Eee PC WMI hotkeys: always reports core events
[    59.904] (**) Option "Device" "/dev/input/event4"
[    59.904] (**) Option "_source" "server/udev"
[    59.905] (II) event4  - Eee PC WMI hotkeys: is tagged by udev as: Keyboard
[    59.905] (II) event4  - Eee PC WMI hotkeys: device is a keyboard
[    59.905] (II) event4  - Eee PC WMI hotkeys: device removed
[    59.905] (**) Option "config_info" "udev:/sys/devices/platform/eeepc-wmi/input/input4/event4"
[    59.905] (II) XINPUT: Adding extended input device "Eee PC WMI hotkeys" (type: KEYBOARD, id 10)
[    59.905] (**) Option "xkb_model" "pc105"
[    59.905] (**) Option "xkb_layout" "it"
[    59.905] (II) event4  - Eee PC WMI hotkeys: is tagged by udev as: Keyboard
[    59.905] (II) event4  - Eee PC WMI hotkeys: device is a keyboard
[    59.908] (**) Logitech USB Receiver: Applying InputClass "libinput pointer catchall"
[    59.908] (**) Logitech USB Receiver: Applying InputClass "libinput keyboard catchall"
[    59.908] (II) Using input driver 'libinput' for 'Logitech USB Receiver'
[    59.908] (II) systemd-logind: returning pre-existing fd for /dev/input/event3 13:67
[    59.908] (**) Logitech USB Receiver: always reports core events
[    59.908] (**) Option "Device" "/dev/input/event3"
[    59.908] (**) Option "_source" "_driver/libinput"
[    59.908] (II) libinput: Logitech USB Receiver: is a virtual subdevice
[    59.908] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb3/3-5/3-5:1.1/0003:046D:C534.0002/input/input3/event3"
[    59.908] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD, id 11)
[    59.908] (**) Option "xkb_model" "pc105"
[    59.908] (**) Option "xkb_layout" "it"
[    60.322] (--) NVIDIA(GPU-0): CRT-0: connected
[    60.322] (--) NVIDIA(GPU-0): CRT-0: 400.0 MHz maximum pixel clock
[    60.322] (--) NVIDIA(GPU-0): 
[    60.337] (--) NVIDIA(GPU-0): DFP-0: disconnected
[    60.337] (--) NVIDIA(GPU-0): DFP-0: Internal TMDS
[    60.337] (--) NVIDIA(GPU-0): DFP-0: 330.0 MHz maximum pixel clock
[    60.337] (--) NVIDIA(GPU-0): 
[    60.337] (--) NVIDIA(GPU-0): DFP-1: disconnected
[    60.337] (--) NVIDIA(GPU-0): DFP-1: Internal TMDS
[    60.337] (--) NVIDIA(GPU-0): DFP-1: 165.0 MHz maximum pixel clock
[    60.337] (--) NVIDIA(GPU-0): 
[    60.337] (--) NVIDIA(GPU-0): DFP-2: disconnected
[    60.337] (--) NVIDIA(GPU-0): DFP-2: Internal TMDS
[    60.337] (--) NVIDIA(GPU-0): DFP-2: 165.0 MHz maximum pixel clock
[    60.337] (--) NVIDIA(GPU-0): 
[    60.337] (--) NVIDIA(GPU-0): DFP-3: disconnected
[    60.337] (--) NVIDIA(GPU-0): DFP-3: Internal TMDS
[    60.337] (--) NVIDIA(GPU-0): DFP-3: 330.0 MHz maximum pixel clock
[    60.337] (--) NVIDIA(GPU-0): 
[    60.337] (--) NVIDIA(GPU-0): DFP-4: disconnected
[    60.337] (--) NVIDIA(GPU-0): DFP-4: Internal DisplayPort
[    60.337] (--) NVIDIA(GPU-0): DFP-4: 960.0 MHz maximum pixel clock
[    60.337] (--) NVIDIA(GPU-0): 
[    68.753] (**) Option "fd" "38"
[    68.754] (II) event1  - Power Button: device removed
[    68.754] (**) Option "fd" "41"
[    68.754] (II) event0  - Power Button: device removed
[    68.754] (**) Option "fd" "42"
[    68.754] (II) event2  - Logitech USB Receiver: device removed
[    68.754] (**) Option "fd" "43"
[    68.754] (**) Option "fd" "44"
[    68.754] (II) event4  - Eee PC WMI hotkeys: device removed
[    68.754] (**) Option "fd" "43"
[    68.754] (II) event3  - Logitech USB Receiver: device removed
[    68.817] (II) systemd-logind: got pause for 13:66
[    68.817] (II) systemd-logind: got pause for 13:67
[    68.817] (II) systemd-logind: got pause for 13:65
[    68.817] (II) systemd-logind: got pause for 13:64
[    68.817] (II) systemd-logind: got pause for 13:68
```

> **NM5TF said:**
> you might try this...

```
xrandr --output DVI-I-0 --mode "1600x1200_60.00"
```

tommy

Here the result...

```
~$ xrandr --output DVI-I-0 --mode "1600x1200_60.00"
xrandr: cannot find mode 1600x1200_60.00

xorg.conf

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 390.42  (buildd@lcy01-amd64-029)  Thu Mar 22 17:34:03 UTC 2018


Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
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

    # HorizSync source: builtin, VertRefresh source: builtin
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "CRT-0"
    HorizSync       28.0 - 55.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GTX 660"
EndSection

Section "Screen"

# Removed Option "metamodes" "1600x900 +0+0"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "Stereo" "0"
    Option         "nvidiaXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "nvidia-auto-select +0+0"
    Option         "SLI" "Off"
    Option         "MultiGPU" "Off"
    Option         "BaseMosaic" "off"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```

---

### Post by slickymaster on 2018-09-11
@maweb:

Please [use code tags]("https://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168") in your posts when posting output. Output posted as plain text loses its formatting and parts of it sometimes turn into smileys making it difficult to read and understand.

---

### Post by Yellow Pasque on 2018-09-12
Edit /etc/X11/xorg.conf using vim or whatever text editor you prefer:
```
sudo vim /etc/X11/xorg.conf
```

Change:
```
   HorizSync       28.0 - 55.0
    VertRefresh     43.0 - 72.0
```
to:
```
   HorizSync       30.0 - 81.0
    VertRefresh     55.0 - 75.0
```

(Note: These values were taken from the manual found at: [https://www.samsung.com/uk/support/model/LS24EMLKF/EN/](https://www.samsung.com/uk/support/model/LS24EMLKF/EN/) )

Reboot and see if you can get further with xrandr.

---

### Post by Yellow Pasque on 2018-09-12
> **Autodave said:**
> I have also run into cheap VGA cords that don't have one particular wire in them (and I can't remember what # it is in) that do not send out from the monitor the monitor's max resolution to inform the video card.

The EDID is not being read from the monitor, so that may be what is happening here. 
An inexpensive DVI-HDMI adapter would be ideal here, for picture quality if nothing else. I don't know why someone would want to run 1600x1200 on a 1920x1080 display, but that's personal preference I guess.

> Usually, 1600 x 900 is the max you can get from VGA.

The last time I checked, analog VGA cables could handle large resolutions (and very large resolutions if the cable was well-made, well-insulated, etc.). The max resolution depended on the GPU transmitting the signal.
VGA didn't have a hard limit like DVI or HDMI cables.

---

### Post by maweb on 2018-09-12
> **Temüjin said:**
> The EDID is not being read from the monitor, so that may be what is happening here. 
An inexpensive DVI-HDMI adapter would be ideal here, for picture quality if nothing else. I don't know why someone would want to run 1600x1200 on a 1920x1080 display, but that's personal preference I guess.



The last time I checked, analog VGA cables could handle large resolutions (and very large resolutions if the cable was well-made, well-insulated, etc.). The max resolution depended on the GPU transmitting the signal.
VGA didn't have a hard limit like DVI or HDMI cables.

Sorry, I wrote an error, it's not a dvi/vga cable, but it is an adpter plug with a vga cable.

---

### Post by Autodave on 2018-09-12
And I just saw the mistake that I made yesterday: it should have said cable and not card. Some cheaper VGA *cables *do not have the extra wire in them to feed the monitor's info to the card.  Try another cable or get rid of VGA altogether if possible.

Sorry for any confusion.

---

### Post by maweb on 2018-09-12
Sorry if I disturb again ...
I  connected the HDMI cable to the video card, when I change from PC to  HDMI mode from the remote control of the monitor, I can not see the  screen well, it is basically moved to the bottom right, then icons on  the left are not visible.

The resolution in HDMI is set to 1920x1080

```
xrandr
Screen 0: minimum 8 x 8, current 2944 x 1080, maximum 16384 x 16384
DVI-I-0 connected primary 1600x900+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768      60.00 +
   1600x900      59.82* 
   1400x900      59.88  
   1368x768      59.88    59.85  
   1360x768      59.96    59.80  
   1280x800      59.91    59.81  
   1280x720      59.86    59.74  
   1152x864      60.00  
   1024x576      59.90    59.82  
   960x540       59.82    59.63  
   864x486       59.92    59.57  
   800x600       72.19    60.32    56.25  
   800x450       59.82  
   700x450       59.88  
   684x384       59.88    59.85  
   680x384       59.96    59.80  
   640x480       59.94  
   640x400       59.98    59.88  
   640x360       59.86    59.83  
   512x384       60.00  
   512x288       60.00    59.92  
   480x270       59.82    59.63  
   432x243       59.92    59.57  
   400x300       72.19  
   320x240       60.05  
DVI-I-1 disconnected (normal left inverted right x axis y axis)
HDMI-0 connected 1920x1080+1024+0 (normal left inverted right x axis y axis) 160mm x 90mm
   1920x1080     60.05*+  60.00    50.04  
   1280x800      59.81  
   1280x720      60.00    59.94    50.00  
   1024x768      60.00  
   800x600       72.19    60.32    56.25  
   720x576       50.00    50.00  
   720x480       59.94    59.94  
   640x480       72.81    59.94  
DP-0 disconnected (normal left inverted right x axis y axis)
DVI-D-0 disconnected (normal left inverted right x axis y axis)
DP-1 disconnected (normal left inverted right x axis y axis)
```

---

### Post by Yellow Pasque on 2018-09-12
> current 2944 x 1080

It looks like it is trying to create some sort of extended desktop because you have both cables plugged in.
Connect only the HDMI cable and restart the system. Does it work?

---

