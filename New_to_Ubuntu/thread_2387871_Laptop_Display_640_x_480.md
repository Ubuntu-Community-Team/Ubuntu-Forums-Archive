---
title: "Laptop Display 640 x 480"
date: 2018-03-24
forum: New to Ubuntu
---

### Post by electrosteam on 2018-03-24
My Dell 2003 laptop boots up with 640 x 480 resolution.
If I connect an external monitor and boot, the resolution comes up 1280 x 1024, even though the monitor is not powered up.
When I do power the monitor On, it goes to sleep with no signal.

I used to have the dual monitors working and stand-alone boot to the higher resolution, these got lost by one of the updates from 17.04 to 17.10 and current.

I have tried to troubleshoot the problem, but I am not very good at that activity (but hopefully will get better).
Looked at preferences, BIOS and variations on randr.

Need some hints on where and how to tackle this issue.
John

---

### Post by Yellow Pasque on 2018-03-25
Post or pastebin your /var/log/Xorg.0.log

---

### Post by electrosteam on 2018-03-25
Temujin,
Thanks for the suggestion, I booted first this morning with monitor, then without, taking a copy of the log for each boot.  Following is the log without the monitor.

```

john@bluebox:~$ cat /var/log/Xorg.0.log
[    45.190] 
X.Org X Server 1.19.5
Release Date: 2017-10-12
[    45.191] X Protocol Version 11, Revision 0
[    45.191] Build Operating System: Linux 4.4.0-97-generic i686 Ubuntu
[    45.191] Current Operating System: Linux bluebox 4.13.0-37-generic #42-Ubuntu SMP Wed Mar 7 14:12:29 UTC 2018 i686
[    45.191] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.13.0-37-generic root=UUID=751182cf-71e9-4fba-856c-fe3caba5dbfb ro quiet splash vt.handoff=7
[    45.192] Build Date: 15 October 2017  05:51:43PM
[    45.192] xorg-server 2:1.19.5-0ubuntu2 (For technical support please see http://www.ubuntu.com/support) 
[    45.192] Current version of pixman: 0.34.0
[    45.193]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    45.193] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    45.194] (==) Log file: "/var/log/Xorg.0.log", Time: Mon Mar 26 08:24:01 2018
[    45.338] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    45.555] (==) No Layout section.  Using the first Screen section.
[    45.556] (==) No screen section available. Using defaults.
[    45.556] (**) |-->Screen "Default Screen Section" (0)
[    45.556] (**) |   |-->Monitor "<default monitor>"
[    45.577] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    45.577] (==) Automatically adding devices
[    45.577] (==) Automatically enabling devices
[    45.577] (==) Automatically adding GPU devices
[    45.577] (==) Automatically binding GPU devices
[    45.577] (==) Max clients allowed: 256, resource mask: 0x1fffff
[    45.600] (WW) The directory "/usr/share/fonts/X11/misc" does not exist.
[    45.600]     Entry deleted from font path.
[    45.600] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    45.600]     Entry deleted from font path.
[    45.600] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    45.600]     Entry deleted from font path.
[    45.600] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    45.600]     Entry deleted from font path.
[    45.600] (WW) The directory "/usr/share/fonts/X11/Type1" does not exist.
[    45.600]     Entry deleted from font path.
[    45.600] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    45.600]     Entry deleted from font path.
[    45.600] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    45.600]     Entry deleted from font path.
[    45.600] (==) FontPath set to:
    built-ins
[    45.600] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    45.600] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    45.601] (II) Loader magic: 0x755020
[    45.601] (II) Module ABI versions:
[    45.601]     X.Org ANSI C Emulation: 0.4
[    45.601]     X.Org Video Driver: 23.0
[    45.601]     X.Org XInput driver : 24.1
[    45.601]     X.Org Server Extension : 10.0
[    45.602] (++) using VT number 7


[    45.602] (II) systemd-logind: logind integration requires -keeptty and -keeptty was not provided, disabling logind integration
[    45.604] (--) PCI:*(0:1:0:0) 10de:0324:1028:015f rev 161, Mem @ 0xfc000000/16777216, 0xd0000000/268435456, BIOS @ 0x????????/131072
[    45.605] (WW) "glamoregl" will not be loaded unless you've specified it to be loaded elsewhere.
[    45.605] (II) "glx" will be loaded by default.
[    45.605] (II) LoadModule: "glx"
[    45.631] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/libglx.so
[    47.477] (II) Module glx: vendor="NVIDIA Corporation"
[    47.478]     compiled for 4.0.2, module version = 1.0.0
[    47.478]     Module class: X.Org Server Extension
[    47.478] (II) NVIDIA GLX Module  384.111  Tue Dec 19 22:42:43 PST 2017
[    47.478] (==) Matched nvidia as autoconfigured driver 0
[    47.478] (==) Matched nouveau as autoconfigured driver 1
[    47.478] (==) Matched modesetting as autoconfigured driver 2
[    47.478] (==) Matched fbdev as autoconfigured driver 3
[    47.478] (==) Matched vesa as autoconfigured driver 4
[    47.478] (==) Assigned the driver to the xf86ConfigLayout
[    47.478] (II) LoadModule: "nvidia"
[    47.478] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    47.571] (II) Module nvidia: vendor="NVIDIA Corporation"
[    47.571]     compiled for 4.0.2, module version = 1.0.0
[    47.571]     Module class: X.Org Video Driver
[    47.603] (II) LoadModule: "nouveau"
[    47.659] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    47.727] (II) Module nouveau: vendor="X.Org Foundation"
[    47.727]     compiled for 1.19.3, module version = 1.0.15
[    47.727]     Module class: X.Org Video Driver
[    47.727]     ABI class: X.Org Video Driver, version 23.0
[    47.727] (II) LoadModule: "modesetting"
[    47.728] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    47.749] (II) Module modesetting: vendor="X.Org Foundation"
[    47.749]     compiled for 1.19.5, module version = 1.19.5
[    47.749]     Module class: X.Org Video Driver
[    47.749]     ABI class: X.Org Video Driver, version 23.0
[    47.749] (II) LoadModule: "fbdev"
[    47.750] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    47.764] (II) Module fbdev: vendor="X.Org Foundation"
[    47.764]     compiled for 1.19.3, module version = 0.4.4
[    47.764]     Module class: X.Org Video Driver
[    47.764]     ABI class: X.Org Video Driver, version 23.0
[    47.764] (II) LoadModule: "vesa"
[    47.765] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    47.769] (II) Module vesa: vendor="X.Org Foundation"
[    47.769]     compiled for 1.19.3, module version = 2.3.4
[    47.769]     Module class: X.Org Video Driver
[    47.769]     ABI class: X.Org Video Driver, version 23.0
[    47.793] (II) NVIDIA dlloader X Driver  384.111  Tue Dec 19 22:15:48 PST 2017
[    47.793] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    47.805] (II) NOUVEAU driver Date:   Fri Apr 21 14:41:17 2017 -0400
[    47.806] (II) NOUVEAU driver for NVIDIA chipset families :
[    47.806]     RIVA TNT        (NV04)
[    47.806]     RIVA TNT2       (NV05)
[    47.806]     GeForce 256     (NV10)
[    47.806]     GeForce 2       (NV11, NV15)
[    47.807]     GeForce 4MX     (NV17, NV18)
[    47.807]     GeForce 3       (NV20)
[    47.807]     GeForce 4Ti     (NV25, NV28)
[    47.807]     GeForce FX      (NV3x)
[    47.807]     GeForce 6       (NV4x)
[    47.807]     GeForce 7       (G7x)
[    47.813]     GeForce 8       (G8x)
[    47.813]     GeForce GTX 200 (NVA0)
[    47.813]     GeForce GTX 400 (NVC0)
[    47.813] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    47.813] (II) FBDEV: driver for framebuffer: fbdev
[    47.813] (II) VESA: driver for VESA chipsets: vesa
[    47.873] (II) Loading sub module "fb"
[    47.873] (II) LoadModule: "fb"
[    47.874] (II) Loading /usr/lib/xorg/modules/libfb.so
[    47.901] (II) Module fb: vendor="X.Org Foundation"
[    47.902]     compiled for 1.19.5, module version = 1.0.0
[    47.902]     ABI class: X.Org ANSI C Emulation, version 0.4
[    47.903] (II) Loading sub module "wfb"
[    47.903] (II) LoadModule: "wfb"
[    47.905] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    47.976] (II) Module wfb: vendor="X.Org Foundation"
[    47.976]     compiled for 1.19.5, module version = 1.0.0
[    47.976]     ABI class: X.Org ANSI C Emulation, version 0.4
[    47.976] (II) Loading sub module "ramdac"
[    47.976] (II) LoadModule: "ramdac"
[    47.976] (II) Module "ramdac" already built-in
[    48.187] (WW) NVIDIA(0): The NVIDIA GeForce FX Go5200 GPU installed in this system is
[    48.188] (WW) NVIDIA(0):     supported through the NVIDIA 173.14.xx Legacy drivers.
[    48.188] (WW) NVIDIA(0):     Please visit http://www.nvidia.com/object/unix.html for
[    48.189] (WW) NVIDIA(0):     more information.  The 384.111 NVIDIA driver will ignore
[    48.189] (WW) NVIDIA(0):     this GPU.  Continuing probe... 
[    48.376] (EE) [drm] Failed to open DRM device for pci:0000:01:00.0: -19
[    48.376] (EE) open /dev/dri/card0: No such file or directory
[    48.376] (WW) Falling back to old probe method for modesetting
[    48.376] (EE) open /dev/dri/card0: No such file or directory
[    48.376] (II) Loading sub module "fbdevhw"
[    48.376] (II) LoadModule: "fbdevhw"
[    48.376] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    48.433] (II) Module fbdevhw: vendor="X.Org Foundation"
[    48.433]     compiled for 1.19.5, module version = 0.0.2
[    48.433]     ABI class: X.Org Video Driver, version 23.0
[    48.433] (**) FBDEV(1): claimed PCI slot 1@0:0:0
[    48.433] (II) FBDEV(1): using default device
[    48.433] (WW) Falling back to old probe method for vesa
[    48.433] (EE) Screen 0 deleted because of no matching config section.
[    48.433] (II) UnloadModule: "modesetting"
[    48.434] (II) FBDEV(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    48.434] (==) FBDEV(0): Depth 24, (==) framebuffer bpp 32
[    48.434] (==) FBDEV(0): RGB weight 888
[    48.434] (==) FBDEV(0): Default visual is TrueColor
[    48.434] (==) FBDEV(0): Using gamma correction (1.0, 1.0, 1.0)
[    48.434] (II) FBDEV(0): hardware: VESA VGA (video memory: 1216kB)
[    48.434] (II) FBDEV(0): checking modes against framebuffer device...
[    48.434] (II) FBDEV(0): checking modes against monitor...
[    48.434] (--) FBDEV(0): Virtual size is 640x480 (pitch 640)
[    48.434] (**) FBDEV(0):  Built-in mode "current": 30.7 MHz, 36.9 kHz, 73.3 Hz
[    48.434] (II) FBDEV(0): Modeline "current"x0.0   30.72  640 672 752 832  480 484 488 504 -hsync -vsync -csync (36.9 kHz b)
[    48.434] (==) FBDEV(0): DPI set to (96, 96)
[    48.434] (II) Loading sub module "fb"
[    48.434] (II) LoadModule: "fb"
[    48.435] (II) Loading /usr/lib/xorg/modules/libfb.so
[    48.435] (II) Module fb: vendor="X.Org Foundation"
[    48.435]     compiled for 1.19.5, module version = 1.0.0
[    48.435]     ABI class: X.Org ANSI C Emulation, version 0.4
[    48.435] (**) FBDEV(0): using shadow framebuffer
[    48.435] (II) Loading sub module "shadow"
[    48.435] (II) LoadModule: "shadow"
[    48.436] (II) Loading /usr/lib/xorg/modules/libshadow.so
[    48.497] (II) Module shadow: vendor="X.Org Foundation"
[    48.498]     compiled for 1.19.5, module version = 1.1.0
[    48.498]     ABI class: X.Org ANSI C Emulation, version 0.4
[    48.498] (II) UnloadModule: "vesa"
[    48.498] (II) Unloading vesa
[    48.499] (==) Depth 24 pixmap format is 32 bpp
[    48.501] (II) FBDEV(0): FBIOBLANK: Invalid argument (Screen blanking not supported by kernel - disabling)
[    48.674] (==) FBDEV(0): Backing store enabled
[    48.718] (==) FBDEV(0): DPMS enabled
[    48.759] (==) RandR enabled
[    48.826] (II) SELinux: Disabled on system
[    48.888] (EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
[    51.991] (II) config/udev: Adding input device Video Bus (/dev/input/event4)
[    51.991] (**) Video Bus: Applying InputClass "libinput keyboard catchall"
[    51.991] (II) LoadModule: "libinput"
[    51.992] (II) Loading /usr/lib/xorg/modules/input/libinput_drv.so
[    52.105] (II) Module libinput: vendor="X.Org Foundation"
[    52.105]     compiled for 1.19.3, module version = 0.25.0
[    52.105]     Module class: X.Org XInput Driver
[    52.105]     ABI class: X.Org XInput driver, version 24.1
[    52.105] (II) Using input driver 'libinput' for 'Video Bus'
[    52.105] (**) Video Bus: always reports core events
[    52.105] (**) Option "Device" "/dev/input/event4"
[    52.105] (**) Option "_source" "server/udev"
[    52.107] (II) event4  - (II) Video Bus: (II) is tagged by udev as: Keyboard
[    52.108] (II) event4  - (II) Video Bus: (II) device is a keyboard
[    52.108] (II) event4  - (II) Video Bus: (II) device removed
[    52.136] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/device:1a/LNXVIDEO:00/input/input5/event4"
[    52.136] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 6)
[    52.136] (**) Option "xkb_model" "pc105"
[    52.136] (**) Option "xkb_layout" "us"
[    52.137] (II) event4  - (II) Video Bus: (II) is tagged by udev as: Keyboard
[    52.137] (II) event4  - (II) Video Bus: (II) device is a keyboard
[    52.138] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    52.138] (**) Power Button: Applying InputClass "libinput keyboard catchall"
[    52.138] (II) Using input driver 'libinput' for 'Power Button'
[    52.138] (**) Power Button: always reports core events
[    52.139] (**) Option "Device" "/dev/input/event1"
[    52.139] (**) Option "_source" "server/udev"
[    52.139] (II) event1  - (II) Power Button: (II) is tagged by udev as: Keyboard
[    52.139] (II) event1  - (II) Power Button: (II) device is a keyboard
[    52.140] (II) event1  - (II) Power Button: (II) device removed
[    52.156] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1/event1"
[    52.156] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    52.156] (**) Option "xkb_model" "pc105"
[    52.156] (**) Option "xkb_layout" "us"
[    52.158] (II) event1  - (II) Power Button: (II) is tagged by udev as: Keyboard
[    52.158] (II) event1  - (II) Power Button: (II) device is a keyboard
[    52.160] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    52.160] (II) No input driver specified, ignoring this device.
[    52.160] (II) This device may have been added with another device file.
[    52.162] (II) config/udev: Adding input device Sleep Button (/dev/input/event2)
[    52.162] (**) Sleep Button: Applying InputClass "libinput keyboard catchall"
[    52.162] (II) Using input driver 'libinput' for 'Sleep Button'
[    52.162] (**) Sleep Button: always reports core events
[    52.162] (**) Option "Device" "/dev/input/event2"
[    52.162] (**) Option "_source" "server/udev"
[    52.163] (II) event2  - (II) Sleep Button: (II) is tagged by udev as: Keyboard
[    52.164] (II) event2  - (II) Sleep Button: (II) device is a keyboard
[    52.164] (II) event2  - (II) Sleep Button: (II) device removed
[    52.176] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2/event2"
[    52.176] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 8)
[    52.176] (**) Option "xkb_model" "pc105"
[    52.176] (**) Option "xkb_layout" "us"
[    52.178] (II) event2  - (II) Sleep Button: (II) is tagged by udev as: Keyboard
[    52.178] (II) event2  - (II) Sleep Button: (II) device is a keyboard
[    52.181] (II) config/udev: Adding input device Logitech Optical USB Mouse (/dev/input/event5)
[    52.181] (**) Logitech Optical USB Mouse: Applying InputClass "libinput pointer catchall"
[    52.181] (II) Using input driver 'libinput' for 'Logitech Optical USB Mouse'
[    52.181] (**) Logitech Optical USB Mouse: always reports core events
[    52.181] (**) Option "Device" "/dev/input/event5"
[    52.181] (**) Option "_source" "server/udev"
[    52.246] (II) event5  - (II) Logitech Optical USB Mouse: (II) is tagged by udev as: Mouse
[    52.247] (II) event5  - (II) Logitech Optical USB Mouse: (II) device set to 400 DPI
[    52.247] (II) event5  - (II) Logitech Optical USB Mouse: (II) device is a pointer
[    52.250] (II) event5  - (II) Logitech Optical USB Mouse: (II) device removed
[    52.316] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.0/0003:046D:C016.0001/input/input7/event5"
[    52.316] (II) XINPUT: Adding extended input device "Logitech Optical USB Mouse" (type: MOUSE, id 9)
[    52.316] (**) Option "AccelerationScheme" "none"
[    52.317] (**) Logitech Optical USB Mouse: (accel) selected scheme none/0
[    52.317] (**) Logitech Optical USB Mouse: (accel) acceleration factor: 2.000
[    52.317] (**) Logitech Optical USB Mouse: (accel) acceleration threshold: 4
[    52.379] (II) event5  - (II) Logitech Optical USB Mouse: (II) is tagged by udev as: Mouse
[    52.380] (II) event5  - (II) Logitech Optical USB Mouse: (II) device set to 400 DPI
[    52.380] (II) event5  - (II) Logitech Optical USB Mouse: (II) device is a pointer
[    52.385] (II) config/udev: Adding input device Logitech Optical USB Mouse (/dev/input/mouse0)
[    52.386] (II) No input driver specified, ignoring this device.
[    52.386] (II) This device may have been added with another device file.
[    52.390] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    52.390] (**) AT Translated Set 2 keyboard: Applying InputClass "libinput keyboard catchall"
[    52.390] (II) Using input driver 'libinput' for 'AT Translated Set 2 keyboard'
[    52.390] (**) AT Translated Set 2 keyboard: always reports core events
[    52.390] (**) Option "Device" "/dev/input/event3"
[    52.390] (**) Option "_source" "server/udev"
[    52.392] (II) event3  - (II) AT Translated Set 2 keyboard: (II) is tagged by udev as: Keyboard
[    52.393] (II) event3  - (II) AT Translated Set 2 keyboard: (II) device is a keyboard
[    52.393] (II) event3  - (II) AT Translated Set 2 keyboard: (II) device removed
[    52.420] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[    52.420] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 10)
[    52.420] (**) Option "xkb_model" "pc105"
[    52.420] (**) Option "xkb_layout" "us"
[    52.421] (II) event3  - (II) AT Translated Set 2 keyboard: (II) is tagged by udev as: Keyboard
[    52.422] (II) event3  - (II) AT Translated Set 2 keyboard: (II) device is a keyboard
[    52.422] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event6)
[    52.423] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "libinput touchpad catchall"
[    52.423] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    52.423] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "Default clickpad buttons"
[    52.423] (II) LoadModule: "synaptics"
[    52.423] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    52.451] (II) Module synaptics: vendor="X.Org Foundation"
[    52.451]     compiled for 1.19.3, module version = 1.9.0
[    52.452]     Module class: X.Org XInput Driver
[    52.452]     ABI class: X.Org XInput driver, version 24.1
[    52.452] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[    52.452] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    52.452] (**) Option "Device" "/dev/input/event6"
[    52.488] (--) synaptics: SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472 (res 85)
[    52.488] (--) synaptics: SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448 (res 94)
[    52.488] (--) synaptics: SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    52.488] (--) synaptics: SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[    52.488] (--) synaptics: SynPS/2 Synaptics TouchPad: buttons: left right double triple
[    52.488] (--) synaptics: SynPS/2 Synaptics TouchPad: Vendor 0x2 Product 0x7
[    52.488] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    52.488] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    52.596] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input6/event6"
[    52.596] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD, id 11)
[    52.596] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[    52.596] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MaxSpeed is now 1.75
[    52.596] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) AccelFactor is now 0.040
[    52.596] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    52.596] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[    52.596] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    52.596] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    52.596] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    52.597] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse1)
[    52.597] (**) SynPS/2 Synaptics TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"
john@bluebox:~$ 

```

I assume the numbers at the start of each line are system time stamp.
John

---

### Post by Yellow Pasque on 2018-03-25
> (WW) NVIDIA(0): The NVIDIA GeForce FX Go5200 GPU installed in this system is supported through the NVIDIA 173.14.xx Legacy drivers... The 384.111 NVIDIA driver will ignore this GPU

You installed an invalid driver. Remove/purge the nvidia-384 driver and any other nvidia proprietary driver you've installed and try again. 
The only sane video driver choice for a Geforce 5200 is the open source nouveau driver that's installed out of the box. Well, You could go way back to Ubuntu 14.04 and attempt to use the nvidia 173.xx driver, but it's not worth the hassle of using such an old distro. The nouveau driver should give you most of what the proprietary one does. It should at least give you the correct resolution and some 2D/3D accel.

---

### Post by electrosteam on 2018-03-26
Temujin,
Purged all Nvidia, back to Nouveau.
Booted without the monitor with slightly more resolution (1400x1050).
Thank you for your response and suggestions.
Another step in the learning process.

Can now go ex-house with LibreCAD usable in the field.

I installed Nvidia 384 originally trying to get the external monitor working.
Plan now is to wait until 18.04 LTS is proven, then install and attack the monitor.

John

---

