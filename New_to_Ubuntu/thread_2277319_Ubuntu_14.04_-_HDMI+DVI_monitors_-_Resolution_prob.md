---
title: "Ubuntu 14.04 - HDMI+DVI monitors - Resolution problems"
date: 2015-05-08
forum: New to Ubuntu
---

### Post by anthony61 on 2015-05-08
Hello,

I ran accross A LOT of blogs / stackoverflow / threads / everything, to correctly setup the resolution of my second monitor screen without any success so far... (spent around 4hours...)

So, here's my setup :

1 HDMI monitor 
1 DVI monitor (actually it's a VGA with a DVI adapter)


What I would like : Both screens with 1920x1080 resolution

---------------

Working setup :
- NO OpenGL drivers
- xrandr --addmode DVI-I-1 1920x1080

When I installed OpenGL, it screwed up the DVI screen resolution.

What I tried so far to make it work with NVIDIA + OpenGL drivers :

xrandr output :
```
Screen 0: minimum 8 x 8, current 3280 x 1080, maximum 16384 x 16384
DVI-I-0 connected 1360x768+1920+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0 +
   1360x768       60.0*    59.8  
   1152x864       60.0  
   800x600        72.2     60.3     56.2  
   680x384        60.0     59.8  
   640x480        59.9  
   512x384        60.0  
   400x300        72.2  
   320x240        60.1  
DVI-I-1 disconnected (normal left inverted right x axis y axis)
HDMI-0 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 509mm x 286mm
   1920x1080      60.0*+   59.9     50.0     60.0     50.0  
   1440x900       59.9  
   1280x1024      60.0  
   1280x800       59.8  
   1280x720       59.9     50.0  
   1152x864       75.0  
   1024x768       70.1     60.0  
   800x600        60.3     56.2  
   720x576        50.0  
   720x480        59.9  
   640x480        59.9     59.9  
DP-0 disconnected (normal left inverted right x axis y axis)
DVI-D-0 disconnected (normal left inverted right x axis y axis)
DP-1 disconnected (normal left inverted right x axis y axis)
  1920x1080_60.00 (0x2bf)  173.0MHz
        h: width  1920 start 2048 end 2248 total 2576 skew    0 clock   67.2KHz
        v: height 1080 start 1083 end 1088 total 1120           clock   60.0Hz

```

I actually had MAX resolution set at 640x480 for the second monitor until I added in /usr/share/X11/xorg.conf.d/10-monitor.conf the following content :

```
Section "Monitor"
  Identifier "Monitor0"
  Modeline "1920x1080_60.00"  172.80  1920 2040 2248 2576  1080 1081 1084 1118  -HSync +Vsync
EndSection
Section "Screen"
  Identifier "Screen0"
  Device "DVI-I-0"
  Monitor "Monitor0"
  DefaultDepth 24
  SubSection "Display"
    Depth 24
    Modes "1920x1080_60.00"
  EndSubSection
EndSection
```

The modline was generated with :

```
$ cvt 1920 1080 60
# 1920x1080 59.96 Hz (CVT 2.07M9) hsync: 67.16 kHz; pclk: 173.00 MHz
Modeline "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
```

Now the maximum resolution I can get is 1360x768. (By the way, monitors are of the same model, and YES, It can run 1920x1080)

If I generate a /etc/X11/xorg.conf using nvidia-xconfig, the max resolution I can get is 640x480, and still unable to xrandr --addmode for the desired display (DVI-I-0)

```
$xrandr --addmode DVI-I-0 1920x1080
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  140 (RANDR)
  Minor opcode of failed request:  18 (RRAddOutputMode)
  Serial number of failed request:  41
  Current serial number in output stream:  42

```

In the Xorg.0.log I can find the following : 

```

[     4.919] (WW) NVIDIA(0): Unable to read EDID for display device CRT-0
[     4.931] (II) NVIDIA(0): Display (Acer G236HL (DFP-1)) does not support NVIDIA 3D
[     4.931] (II) NVIDIA(0):     Vision stereo.
[     4.931] (II) NVIDIA(GPU-0): Found DRM driver nvidia-drm (20130102)
[     4.932] (II) NVIDIA(0): NVIDIA GPU GeForce GTX 680 (GK104) at PCI:1:0:0 (GPU-0)
[     4.932] (--) NVIDIA(0): Memory: 2097152 kBytes
[     4.932] (--) NVIDIA(0): VideoBIOS: 80.04.47.00.0d
[     4.932] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[     4.935] (--) NVIDIA(0): Valid display device(s) on GeForce GTX 680 at PCI:1:0:0
[     4.935] (--) NVIDIA(0):     CRT-0 (boot, connected)
[     4.935] (--) NVIDIA(0):     DFP-0
[     4.935] (--) NVIDIA(0):     Acer G236HL (DFP-1) (connected)
[     4.935] (--) NVIDIA(0):     DFP-2
[     4.935] (--) NVIDIA(0):     DFP-3
[     4.935] (--) NVIDIA(0):     DFP-4
[     4.935] (--) NVIDIA(0): CRT-0: 400.0 MHz maximum pixel clock
[     4.935] (--) NVIDIA(0): DFP-0: Internal Single Link TMDS
[     4.935] (--) NVIDIA(0): DFP-0: 330.0 MHz maximum pixel clock
[     4.935] (--) NVIDIA(0): Acer G236HL (DFP-1): Internal Single Link TMDS
[     4.935] (--) NVIDIA(0): Acer G236HL (DFP-1): 165.0 MHz maximum pixel clock
[     4.935] (--) NVIDIA(0): DFP-2: Internal Single Link TMDS
[     4.935] (--) NVIDIA(0): DFP-2: 165.0 MHz maximum pixel clock
[     4.935] (--) NVIDIA(0): DFP-3: Internal Single Link TMDS
[     4.935] (--) NVIDIA(0): DFP-3: 330.0 MHz maximum pixel clock
[     4.935] (--) NVIDIA(0): DFP-4: Internal DisplayPort
[     4.935] (--) NVIDIA(0): DFP-4: 960.0 MHz maximum pixel clock
[     4.935] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[     4.935] (**) NVIDIA(0):     device CRT-0 (Using EDID frequencies has been enabled on
[     4.935] (**) NVIDIA(0):     all display devices.)
[     4.937] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[     4.937] (**) NVIDIA(0):     device Acer G236HL (DFP-1) (Using EDID frequencies has
[     4.937] (**) NVIDIA(0):     been enabled on all display devices.)
[     4.937] (WW) NVIDIA(GPU-0): The EDID for Acer G236HL (DFP-1) contradicts itself: mode
[     4.937] (WW) NVIDIA(GPU-0):     "720x576" is specified in the EDID; however, the EDID's
[     4.937] (WW) NVIDIA(GPU-0):     valid VertRefresh range (55.000-75.000 Hz) would exclude
[     4.937] (WW) NVIDIA(GPU-0):     this mode's VertRefresh (50.0 Hz); ignoring VertRefresh
[     4.937] (WW) NVIDIA(GPU-0):     check for mode "720x576".
[     4.937] (WW) NVIDIA(GPU-0): The EDID for Acer G236HL (DFP-1) contradicts itself: mode
[     4.937] (WW) NVIDIA(GPU-0):     "1280x720" is specified in the EDID; however, the EDID's
[     4.937] (WW) NVIDIA(GPU-0):     valid VertRefresh range (55.000-75.000 Hz) would exclude
[     4.937] (WW) NVIDIA(GPU-0):     this mode's VertRefresh (50.0 Hz); ignoring VertRefresh
[     4.937] (WW) NVIDIA(GPU-0):     check for mode "1280x720".
[     4.937] (WW) NVIDIA(GPU-0): The EDID for Acer G236HL (DFP-1) contradicts itself: mode
[     4.937] (WW) NVIDIA(GPU-0):     "1920x1080" is specified in the EDID; however, the EDID's
[     4.937] (WW) NVIDIA(GPU-0):     valid HorizSync range (30.000-80.000 kHz) would exclude
[     4.937] (WW) NVIDIA(GPU-0):     this mode's HorizSync (28.1 kHz); ignoring HorizSync check
[     4.937] (WW) NVIDIA(GPU-0):     for mode "1920x1080".
[     4.937] (WW) NVIDIA(GPU-0): The EDID for Acer G236HL (DFP-1) contradicts itself: mode
[     4.937] (WW) NVIDIA(GPU-0):     "1920x1080" is specified in the EDID; however, the EDID's
[     4.937] (WW) NVIDIA(GPU-0):     valid VertRefresh range (55.000-75.000 Hz) would exclude
[     4.937] (WW) NVIDIA(GPU-0):     this mode's VertRefresh (50.0 Hz); ignoring VertRefresh
[     4.937] (WW) NVIDIA(GPU-0):     check for mode "1920x1080".
[     4.937] (WW) NVIDIA(GPU-0): The EDID for Acer G236HL (DFP-1) contradicts itself: mode
[     4.937] (WW) NVIDIA(GPU-0):     "1920x1080" is specified in the EDID; however, the EDID's
[     4.937] (WW) NVIDIA(GPU-0):     valid VertRefresh range (55.000-75.000 Hz) would exclude
[     4.937] (WW) NVIDIA(GPU-0):     this mode's VertRefresh (50.0 Hz); ignoring VertRefresh
[     4.937] (WW) NVIDIA(GPU-0):     check for mode "1920x1080".
[     4.938] (WW) NVIDIA(0): No valid modes for
[     4.938] (WW) NVIDIA(0):     "CRT-0:1920x1080_60.00,DFP-1:1920x1080_60.00"; removing.
[     4.938] (WW) NVIDIA(0): 
[     4.938] (WW) NVIDIA(0): Unable to validate any modes; falling back to the default mode
[     4.938] (WW) NVIDIA(0):     "nvidia-auto-select".
[     4.938] (WW) NVIDIA(0): 
[     4.938] (II) NVIDIA(0): Validated MetaModes:
[     4.938] (II) NVIDIA(0):     "CRT-0:nvidia-auto-select,DFP-1:nvidia-auto-select"
[     4.938] (II) NVIDIA(0): Virtual screen size determined to be 2944 x 1080
[     4.959] (WW) NVIDIA(0): Unable to get display device CRT-0's EDID; cannot compute DPI
[     4.960] (WW) NVIDIA(0):     from CRT-0's EDID.
[     4.960] (==) NVIDIA(0): DPI set to (75, 75); computed from built-in default
[     4.960] (II) UnloadModule: "nouveau"
[     4.960] (II) Unloading nouveau
[     4.960] (II) UnloadModule: "modesetting"
[     4.960] (II) Unloading modesetting
[     4.960] (II) UnloadModule: "fbdev"
[     4.960] (II) Unloading fbdev
[     4.960] (II) UnloadSubModule: "fbdevhw"
[     4.960] (II) Unloading fbdevhw
[     4.960] (II) UnloadModule: "vesa"
[     4.960] (II) Unloading vesa
[     4.960] (--) Depth 24 pixmap format is 32 bpp
[     4.960] (II) NVIDIA: Using 3072.00 MB of virtual memory for indirect memory
[     4.960] (II) NVIDIA:     access.
[     4.965] (II) NVIDIA(0): Setting mode "CRT-0:nvidia-auto-select,DFP-1:nvidia-auto-select"
[     5.073] (==) NVIDIA(0): Disabling shared memory pixmaps
[     5.073] (==) NVIDIA(0): Backing store enabled
[     5.073] (==) NVIDIA(0): Silken mouse enabled
[     5.073] (==) NVIDIA(0): DPMS enabled
[     5.074] (II) Loading sub module "dri2"
[     5.074] (II) LoadModule: "dri2"
[     5.074] (II) Module "dri2" already built-in
[     5.074] (II) NVIDIA(0): [DRI2] Setup complete
[     5.074] (II) NVIDIA(0): [DRI2]   VDPAU driver: nvidia
[     5.074] (--) RandR disabled
[     5.077] (II) Initializing extension GLX
[     5.085] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[     5.086] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[     5.086] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[     5.086] (II) LoadModule: "evdev"
[     5.086] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     5.088] (II) Module evdev: vendor="X.Org Foundation"
[     5.088]     compiled for 1.16.0, module version = 2.9.0
[     5.088]     Module class: X.Org XInput Driver
[     5.088]     ABI class: X.Org XInput driver, version 21.0
[     5.088] (II) Using input driver 'evdev' for 'Power Button'
[     5.088] (**) Power Button: always reports core events
[     5.088] (**) evdev: Power Button: Device: "/dev/input/event1"
[     5.088] (--) evdev: Power Button: Vendor 0 Product 0x1
[     5.088] (--) evdev: Power Button: Found keys
[     5.088] (II) evdev: Power Button: Configuring as keyboard
[     5.088] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[     5.088] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[     5.088] (**) Option "xkb_rules" "evdev"
[     5.088] (**) Option "xkb_model" "pc105"
[     5.088] (**) Option "xkb_layout" "fr"
[     5.088] (**) Option "xkb_variant" "latin9"
[     5.089] (II) XKB: reuse xkmfile /var/lib/xkb/server-816A055A5FF7D63897839A4BDEDC3908551E49DA.xkm
[     5.089] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[     5.089] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[     5.089] (II) Using input driver 'evdev' for 'Power Button'
[     5.089] (**) Power Button: always reports core events
[     5.089] (**) evdev: Power Button: Device: "/dev/input/event0"
[     5.089] (--) evdev: Power Button: Vendor 0 Product 0x1
[     5.089] (--) evdev: Power Button: Found keys
[     5.089] (II) evdev: Power Button: Configuring as keyboard
[     5.089] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
[     5.089] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[     5.089] (**) Option "xkb_rules" "evdev"
[     5.089] (**) Option "xkb_model" "pc105"
[     5.089] (**) Option "xkb_layout" "fr"
[     5.089] (**) Option "xkb_variant" "latin9"
[     5.089] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=3 (/dev/input/event13)
[     5.089] (II) No input driver specified, ignoring this device.
[     5.089] (II) This device may have been added with another device file.
[     5.089] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=7 (/dev/input/event14)
[     5.089] (II) No input driver specified, ignoring this device.
[     5.089] (II) This device may have been added with another device file.
[     5.090] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=8 (/dev/input/event15)
[     5.090] (II) No input driver specified, ignoring this device.
[     5.090] (II) This device may have been added with another device file.
[     5.090] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=9 (/dev/input/event16)
[     5.090] (II) No input driver specified, ignoring this device.
[     5.090] (II) This device may have been added with another device file.
[     5.090] (II) config/udev: Adding input device Logitech Logitech Illuminated Keyboard (/dev/input/event2)
[     5.090] (**) Logitech Logitech Illuminated Keyboard: Applying InputClass "evdev keyboard catchall"
[     5.090] (II) Using input driver 'evdev' for 'Logitech Logitech Illuminated Keyboard'
[     5.090] (**) Logitech Logitech Illuminated Keyboard: always reports core events
[     5.090] (**) evdev: Logitech Logitech Illuminated Keyboard: Device: "/dev/input/event2"
[     5.090] (--) evdev: Logitech Logitech Illuminated Keyboard: Vendor 0x46d Product 0xc318
[     5.090] (--) evdev: Logitech Logitech Illuminated Keyboard: Found keys
[     5.090] (II) evdev: Logitech Logitech Illuminated Keyboard: Configuring as keyboard
[     5.090] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3:1.0/0003:046D:C318.0001/input/input5/event2"
[     5.090] (II) XINPUT: Adding extended input device "Logitech Logitech Illuminated Keyboard" (type: KEYBOARD, id 8)
[     5.090] (**) Option "xkb_rules" "evdev"
[     5.090] (**) Option "xkb_model" "pc105"
[     5.090] (**) Option "xkb_layout" "fr"
[     5.090] (**) Option "xkb_variant" "latin9"
[     5.090] (II) config/udev: Adding input device Logitech Logitech Illuminated Keyboard (/dev/input/event3)
[     5.090] (**) Logitech Logitech Illuminated Keyboard: Applying InputClass "evdev keyboard catchall"
[     5.090] (II) Using input driver 'evdev' for 'Logitech Logitech Illuminated Keyboard'
[     5.090] (**) Logitech Logitech Illuminated Keyboard: always reports core events
[     5.090] (**) evdev: Logitech Logitech Illuminated Keyboard: Device: "/dev/input/event3"
[     5.090] (--) evdev: Logitech Logitech Illuminated Keyboard: Vendor 0x46d Product 0xc318
[     5.090] (--) evdev: Logitech Logitech Illuminated Keyboard: Found 1 mouse buttons
[     5.090] (--) evdev: Logitech Logitech Illuminated Keyboard: Found scroll wheel(s)
[     5.090] (--) evdev: Logitech Logitech Illuminated Keyboard: Found relative axes
[     5.090] (II) evdev: Logitech Logitech Illuminated Keyboard: Forcing relative x/y axes to exist.
[     5.090] (--) evdev: Logitech Logitech Illuminated Keyboard: Found absolute axes
[     5.090] (II) evdev: Logitech Logitech Illuminated Keyboard: Forcing absolute x/y axes to exist.
[     5.090] (--) evdev: Logitech Logitech Illuminated Keyboard: Found keys
[     5.090] (II) evdev: Logitech Logitech Illuminated Keyboard: Configuring as mouse
[     5.090] (II) evdev: Logitech Logitech Illuminated Keyboard: Configuring as keyboard
[     5.090] (II) evdev: Logitech Logitech Illuminated Keyboard: Adding scrollwheel support
[     5.090] (**) evdev: Logitech Logitech Illuminated Keyboard: YAxisMapping: buttons 4 and 5
[     5.090] (**) evdev: Logitech Logitech Illuminated Keyboard: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[     5.090] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3:1.1/0003:046D:C318.0002/input/input6/event3"
[     5.090] (II) XINPUT: Adding extended input device "Logitech Logitech Illuminated Keyboard" (type: KEYBOARD, id 9)
[     5.090] (**) Option "xkb_rules" "evdev"
[     5.090] (**) Option "xkb_model" "pc105"
[     5.090] (**) Option "xkb_layout" "fr"
[     5.090] (**) Option "xkb_variant" "latin9"
[     5.090] (II) evdev: Logitech Logitech Illuminated Keyboard: initialized for relative axes.
[     5.090] (WW) evdev: Logitech Logitech Illuminated Keyboard: ignoring absolute axes.
[     5.090] (**) Logitech Logitech Illuminated Keyboard: (accel) keeping acceleration scheme 1
[     5.090] (**) Logitech Logitech Illuminated Keyboard: (accel) acceleration profile 0
[     5.090] (**) Logitech Logitech Illuminated Keyboard: (accel) acceleration factor: 2.000
[     5.090] (**) Logitech Logitech Illuminated Keyboard: (accel) acceleration threshold: 4
[     5.091] (II) config/udev: Adding input device SteelSeries Kana Gaming Mouse (/dev/input/event4)
[     5.091] (**) SteelSeries Kana Gaming Mouse: Applying InputClass "evdev pointer catchall"
[     5.091] (II) Using input driver 'evdev' for 'SteelSeries Kana Gaming Mouse'
[     5.091] (**) SteelSeries Kana Gaming Mouse: always reports core events
[     5.091] (**) evdev: SteelSeries Kana Gaming Mouse: Device: "/dev/input/event4"
[     5.091] (--) evdev: SteelSeries Kana Gaming Mouse: Vendor 0x1038 Product 0x1364
[     5.091] (--) evdev: SteelSeries Kana Gaming Mouse: Found 9 mouse buttons
[     5.091] (--) evdev: SteelSeries Kana Gaming Mouse: Found scroll wheel(s)
[     5.091] (--) evdev: SteelSeries Kana Gaming Mouse: Found relative axes
[     5.091] (--) evdev: SteelSeries Kana Gaming Mouse: Found x and y relative axes
[     5.091] (II) evdev: SteelSeries Kana Gaming Mouse: Configuring as mouse
[     5.091] (II) evdev: SteelSeries Kana Gaming Mouse: Adding scrollwheel support
[     5.091] (**) evdev: SteelSeries Kana Gaming Mouse: YAxisMapping: buttons 4 and 5
[     5.091] (**) evdev: SteelSeries Kana Gaming Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[     5.091] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.4/1-1.4:1.1/0003:1038:1364.0004/input/input7/event4"
[     5.091] (II) XINPUT: Adding extended input device "SteelSeries Kana Gaming Mouse" (type: MOUSE, id 10)
[     5.091] (II) evdev: SteelSeries Kana Gaming Mouse: initialized for relative axes.
[     5.091] (**) SteelSeries Kana Gaming Mouse: (accel) keeping acceleration scheme 1
[     5.091] (**) SteelSeries Kana Gaming Mouse: (accel) acceleration profile 0
[     5.091] (**) SteelSeries Kana Gaming Mouse: (accel) acceleration factor: 2.000
[     5.091] (**) SteelSeries Kana Gaming Mouse: (accel) acceleration threshold: 4
[     5.091] (II) config/udev: Adding input device SteelSeries Kana Gaming Mouse (/dev/input/mouse0)
[     5.091] (II) No input driver specified, ignoring this device.
[     5.091] (II) This device may have been added with another device file.
[     5.091] (II) config/udev: Adding input device HDA Intel PCH Rear Mic (/dev/input/event7)
[     5.091] (II) No input driver specified, ignoring this device.
[     5.091] (II) This device may have been added with another device file.
[     5.091] (II) config/udev: Adding input device HDA Intel PCH Line (/dev/input/event8)
[     5.091] (II) No input driver specified, ignoring this device.
[     5.091] (II) This device may have been added with another device file.
[     5.091] (II) config/udev: Adding input device HDA Intel PCH Line Out Front (/dev/input/event9)
[     5.091] (II) No input driver specified, ignoring this device.
[     5.091] (II) This device may have been added with another device file.
[     5.091] (II) config/udev: Adding input device HDA Intel PCH Line Out Surround (/dev/input/event10)
[     5.091] (II) No input driver specified, ignoring this device.
[     5.091] (II) This device may have been added with another device file.
[     5.092] (II) config/udev: Adding input device HDA Intel PCH Line Out CLFE (/dev/input/event11)
[     5.092] (II) No input driver specified, ignoring this device.
[     5.092] (II) This device may have been added with another device file.
[     5.092] (II) config/udev: Adding input device HDA Intel PCH Front Headphone (/dev/input/event12)
[     5.092] (II) No input driver specified, ignoring this device.
[     5.092] (II) This device may have been added with another device file.
[     5.092] (II) config/udev: Adding input device HDA Intel PCH Front Mic (/dev/input/event6)
[     5.092] (II) No input driver specified, ignoring this device.
[     5.092] (II) This device may have been added with another device file.
[     5.092] (II) config/udev: Adding input device Eee PC WMI hotkeys (/dev/input/event5)
[     5.092] (**) Eee PC WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[     5.092] (II) Using input driver 'evdev' for 'Eee PC WMI hotkeys'
[     5.092] (**) Eee PC WMI hotkeys: always reports core events
[     5.092] (**) evdev: Eee PC WMI hotkeys: Device: "/dev/input/event5"
[     5.092] (--) evdev: Eee PC WMI hotkeys: Vendor 0 Product 0
[     5.092] (--) evdev: Eee PC WMI hotkeys: Found keys
[     5.092] (II) evdev: Eee PC WMI hotkeys: Configuring as keyboard
[     5.092] (**) Option "config_info" "udev:/sys/devices/platform/eeepc-wmi/input/input8/event5"
[     5.092] (II) XINPUT: Adding extended input device "Eee PC WMI hotkeys" (type: KEYBOARD, id 11)
[     5.092] (**) Option "xkb_rules" "evdev"
[     5.092] (**) Option "xkb_model" "pc105"
[     5.092] (**) Option "xkb_layout" "fr"
[     5.092] (**) Option "xkb_variant" "latin9"
[     7.504] (WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-0
[     7.504] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[     7.504] (**) NVIDIA(0):     device CRT-0 (Using EDID frequencies has been enabled on
[     7.504] (**) NVIDIA(0):     all display devices.)
[     7.517] (II) NVIDIA(GPU-0): Display (Acer G236HL (DFP-1)) does not support NVIDIA 3D
[     7.517] (II) NVIDIA(GPU-0):     Vision stereo.
[     7.720] (WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-0
[     7.720] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[     7.720] (**) NVIDIA(0):     device CRT-0 (Using EDID frequencies has been enabled on
[     7.720] (**) NVIDIA(0):     all display devices.)
[     7.733] (II) NVIDIA(GPU-0): Display (Acer G236HL (DFP-1)) does not support NVIDIA 3D
[     7.733] (II) NVIDIA(GPU-0):     Vision stereo.
[    13.403] (WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-0
[    13.403] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    13.403] (**) NVIDIA(0):     device CRT-0 (Using EDID frequencies has been enabled on
[    13.403] (**) NVIDIA(0):     all display devices.)
[    13.416] (II) NVIDIA(GPU-0): Display (Acer G236HL (DFP-1)) does not support NVIDIA 3D
[    13.416] (II) NVIDIA(GPU-0):     Vision stereo.
[    13.537] (WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-0
[    13.537] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    13.537] (**) NVIDIA(0):     device CRT-0 (Using EDID frequencies has been enabled on
[    13.537] (**) NVIDIA(0):     all display devices.)
[    13.550] (II) NVIDIA(GPU-0): Display (Acer G236HL (DFP-1)) does not support NVIDIA 3D
[    13.550] (II) NVIDIA(GPU-0):     Vision stereo.
[    13.567] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    13.684] (II) NVIDIA(0): Setting mode "DVI-I-0: 1360x768 @1360x768 +1920+0 {ViewPortIn=1360x768, ViewPortOut=1360x768+0+0}, HDMI-0: nvidia-auto-select @1920x1080 +1024+0 {ViewPortIn=1920x1080, ViewPortOut=1920x1080+0+0}"
[    13.862] (II) NVIDIA(0): Setting mode "DVI-I-0: 1360x768 @1360x768 +1920+0 {ViewPortIn=1360x768, ViewPortOut=1360x768+0+0}, HDMI-0: nvidia-auto-select @1920x1080 +0+0 {ViewPortIn=1920x1080, ViewPortOut=1920x1080+0+0}"
[    13.942] (WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-0
[    13.942] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    13.942] (**) NVIDIA(0):     device CRT-0 (Using EDID frequencies has been enabled on
[    13.942] (**) NVIDIA(0):     all display devices.)
[    13.955] (II) NVIDIA(GPU-0): Display (Acer G236HL (DFP-1)) does not support NVIDIA 3D
[    13.955] (II) NVIDIA(GPU-0):     Vision stereo.
[    17.963] (WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-0
[    17.963] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    17.963] (**) NVIDIA(0):     device CRT-0 (Using EDID frequencies has been enabled on
[    17.963] (**) NVIDIA(0):     all display devices.)
[    17.976] (II) NVIDIA(GPU-0): Display (Acer G236HL (DFP-1)) does not support NVIDIA 3D
[    17.976] (II) NVIDIA(GPU-0):     Vision stereo.
[    17.978] (II) XKB: reuse xkmfile /var/lib/xkb/server-5383DF796A878338E939152C37AA178207D58F40.xkm
[    17.984] (II) XKB: reuse xkmfile /var/lib/xkb/server-5383DF796A878338E939152C37AA178207D58F40.xkm
[    18.495] (II) XKB: reuse xkmfile /var/lib/xkb/server-AC39741F7E9835FA082114AD24730D6B80353EA3.xkm
[    32.930] (WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-0
[    32.930] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    32.930] (**) NVIDIA(0):     device CRT-0 (Using EDID frequencies has been enabled on
[    32.930] (**) NVIDIA(0):     all display devices.)
[    32.943] (II) NVIDIA(GPU-0): Display (Acer G236HL (DFP-1)) does not support NVIDIA 3D
[    32.943] (II) NVIDIA(GPU-0):     Vision stereo.
[    32.963] (WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-0
[    32.963] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    32.963] (**) NVIDIA(0):     device CRT-0 (Using EDID frequencies has been enabled on
[    32.963] (**) NVIDIA(0):     all display devices.)
[    32.976] (II) NVIDIA(GPU-0): Display (Acer G236HL (DFP-1)) does not support NVIDIA 3D
[    32.976] (II) NVIDIA(GPU-0):     Vision stereo.
[    45.377] (WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-0
[    45.377] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    45.377] (**) NVIDIA(0):     device CRT-0 (Using EDID frequencies has been enabled on
[    45.377] (**) NVIDIA(0):     all display devices.)
[    45.390] (II) NVIDIA(GPU-0): Display (Acer G236HL (DFP-1)) does not support NVIDIA 3D
[    45.390] (II) NVIDIA(GPU-0):     Vision stereo.
[    80.382] (WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-0
[    80.382] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    80.382] (**) NVIDIA(0):     device CRT-0 (Using EDID frequencies has been enabled on
[    80.382] (**) NVIDIA(0):     all display devices.)
[    80.401] (II) NVIDIA(GPU-0): Display (Acer G236HL (DFP-1)) does not support NVIDIA 3D
[    80.401] (II) NVIDIA(GPU-0):     Vision stereo.
[   130.223] (WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-0
[   130.223] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[   130.223] (**) NVIDIA(0):     device CRT-0 (Using EDID frequencies has been enabled on
[   130.223] (**) NVIDIA(0):     all display devices.)
[   130.244] (II) NVIDIA(GPU-0): Display (Acer G236HL (DFP-1)) does not support NVIDIA 3D
[   130.244] (II) NVIDIA(GPU-0):     Vision stereo.
[   168.783] (WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-0
[   168.783] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[   168.783] (**) NVIDIA(0):     device CRT-0 (Using EDID frequencies has been enabled on
[   168.783] (**) NVIDIA(0):     all display devices.)
[   168.804] (II) NVIDIA(GPU-0): Display (Acer G236HL (DFP-1)) does not support NVIDIA 3D
[   168.804] (II) NVIDIA(GPU-0):     Vision stereo.
[   180.130] (WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-0
[   180.130] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[   180.130] (**) NVIDIA(0):     device CRT-0 (Using EDID frequencies has been enabled on
[   180.130] (**) NVIDIA(0):     all display devices.)
[   180.150] (II) NVIDIA(GPU-0): Display (Acer G236HL (DFP-1)) does not support NVIDIA 3D
[   180.150] (II) NVIDIA(GPU-0):     Vision stereo.
[   183.550] (WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-0
[   183.550] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[   183.550] (**) NVIDIA(0):     device CRT-0 (Using EDID frequencies has been enabled on
[   183.550] (**) NVIDIA(0):     all display devices.)
[   183.570] (II) NVIDIA(GPU-0): Display (Acer G236HL (DFP-1)) does not support NVIDIA 3D
[   183.570] (II) NVIDIA(GPU-0):     Vision stereo.
[   196.232] (WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-0
[   196.232] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[   196.232] (**) NVIDIA(0):     device CRT-0 (Using EDID frequencies has been enabled on
[   196.232] (**) NVIDIA(0):     all display devices.)
[   196.252] (II) NVIDIA(GPU-0): Display (Acer G236HL (DFP-1)) does not support NVIDIA 3D
[   196.252] (II) NVIDIA(GPU-0):     Vision stereo.
[   325.896] (WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-0
[   325.896] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[   325.896] (**) NVIDIA(0):     device CRT-0 (Using EDID frequencies has been enabled on
[   325.896] (**) NVIDIA(0):     all display devices.)
[   325.916] (II) NVIDIA(GPU-0): Display (Acer G236HL (DFP-1)) does not support NVIDIA 3D
[   325.916] (II) NVIDIA(GPU-0):     Vision stereo.
[   325.929] (WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-0
[   325.929] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[   325.929] (**) NVIDIA(0):     device CRT-0 (Using EDID frequencies has been enabled on
[   325.929] (**) NVIDIA(0):     all display devices.)
[   325.949] (II) NVIDIA(GPU-0): Display (Acer G236HL (DFP-1)) does not support NVIDIA 3D
[   325.949] (II) NVIDIA(GPU-0):     Vision stereo.
[   364.424] (WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-0
[   364.424] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[   364.424] (**) NVIDIA(0):     device CRT-0 (Using EDID frequencies has been enabled on
[   364.424] (**) NVIDIA(0):     all display devices.)
[   364.444] (II) NVIDIA(GPU-0): Display (Acer G236HL (DFP-1)) does not support NVIDIA 3D
[   364.444] (II) NVIDIA(GPU-0):     Vision stereo.
[   389.902] (WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-0
[   389.902] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[   389.902] (**) NVIDIA(0):     device CRT-0 (Using EDID frequencies has been enabled on
[   389.902] (**) NVIDIA(0):     all display devices.)
[   389.922] (II) NVIDIA(GPU-0): Display (Acer G236HL (DFP-1)) does not support NVIDIA 3D
[   389.922] (II) NVIDIA(GPU-0):     Vision stereo.
[   401.566] (WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-0
[   401.566] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[   401.566] (**) NVIDIA(0):     device CRT-0 (Using EDID frequencies has been enabled on
[   401.566] (**) NVIDIA(0):     all display devices.)
[   401.586] (II) NVIDIA(GPU-0): Display (Acer G236HL (DFP-1)) does not support NVIDIA 3D
[   401.586] (II) NVIDIA(GPU-0):     Vision stereo.
[   405.437] (WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-0
[   405.437] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[   405.437] (**) NVIDIA(0):     device CRT-0 (Using EDID frequencies has been enabled on
[   405.437] (**) NVIDIA(0):     all display devices.)
[   405.457] (II) NVIDIA(GPU-0): Display (Acer G236HL (DFP-1)) does not support NVIDIA 3D
[   405.457] (II) NVIDIA(GPU-0):     Vision stereo.
[   421.339] (WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-0
[   421.339] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[   421.339] (**) NVIDIA(0):     device CRT-0 (Using EDID frequencies has been enabled on
[   421.339] (**) NVIDIA(0):     all display devices.)
[   421.358] (II) NVIDIA(GPU-0): Display (Acer G236HL (DFP-1)) does not support NVIDIA 3D
[   421.358] (II) NVIDIA(GPU-0):     Vision stereo.
[   694.262] (WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-0
[   694.262] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[   694.262] (**) NVIDIA(0):     device CRT-0 (Using EDID frequencies has been enabled on
[   694.262] (**) NVIDIA(0):     all display devices.)
[   694.282] (II) NVIDIA(GPU-0): Display (Acer G236HL (DFP-1)) does not support NVIDIA 3D
[   694.282] (II) NVIDIA(GPU-0):     Vision stereo.
[  1560.667] (WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-0
[  1560.667] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[  1560.667] (**) NVIDIA(0):     device CRT-0 (Using EDID frequencies has been enabled on
[  1560.667] (**) NVIDIA(0):     all display devices.)
[  1560.686] (II) NVIDIA(GPU-0): Display (Acer G236HL (DFP-1)) does not support NVIDIA 3D
[  1560.686] (II) NVIDIA(GPU-0):     Vision stereo.
[  1656.945] (WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-0
[  1656.945] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[  1656.945] (**) NVIDIA(0):     device CRT-0 (Using EDID frequencies has been enabled on
[  1656.945] (**) NVIDIA(0):     all display devices.)
[  1656.965] (II) NVIDIA(GPU-0): Display (Acer G236HL (DFP-1)) does not support NVIDIA 3D
[  1656.965] (II) NVIDIA(GPU-0):     Vision stereo.
[  1978.551] (WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-0
[  1978.551] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[  1978.551] (**) NVIDIA(0):     device CRT-0 (Using EDID frequencies has been enabled on
[  1978.551] (**) NVIDIA(0):     all display devices.)
[  1978.571] (II) NVIDIA(GPU-0): Display (Acer G236HL (DFP-1)) does not support NVIDIA 3D
[  1978.571] (II) NVIDIA(GPU-0):     Vision stereo.
```

The important lines I guess are : 

```

[     4.938] (WW) NVIDIA(0): No valid modes for
[     4.938] (WW) NVIDIA(0):     "CRT-0:1920x1080_60.00,DFP-1:1920x1080_60.00"; removing.
...
[    13.684] (II) NVIDIA(0): Setting mode "DVI-I-0: 1360x768 @1360x768 +1920+0 {ViewPortIn=1360x768, ViewPortOut=1360x768+0+0}, HDMI-0: nvidia-auto-select @1920x1080 +1024+0 {ViewPortIn=1920x1080, ViewPortOut=1920x1080+0+0}"
[    13.862] (II) NVIDIA(0): Setting mode "DVI-I-0: 1360x768 @1360x768 +1920+0 {ViewPortIn=1360x768, ViewPortOut=1360x768+0+0}, HDMI-0: nvidia-auto-select @1920x1080 +0+0 {ViewPortIn=1920x1080, ViewPortOut=1920x1080+0+0}"

```

I tried so many things, due to the thousands different "solutions" found on the internet, WITHOUT A SINGLE WORKING, that I may have messed up my configuration, and can't really say what I've tested so far.

Any kind of help is welcome...

---

### Post by dino99 on 2015-05-08
nowadays the kernel directly deal with X; meaning that xorg.conf is not needed, xconfig (nvidia) often badly disturb the system (so wrong definition, black screen, ...)
That said, please tell us wich ubuntu and graphic driver is used on which card/chipset

---

### Post by anthony61 on 2015-05-08
Thank you for the details on how X works now, and the fast answer.

For the spec details :
OS: Ubuntu 14.04 x64
Graphic card : GTX 680
NVIDIA driver : NVIDIA binary driver - version 331.113

Also, this is what I installed, but I may install something else if you tell me to do so :)

---

### Post by gordintoronto on 2015-05-08
You may be able to get the results you want by running Nvidia X Server Settings. Avoid the command line and editing config files if you can!

---

### Post by anthony61 on 2015-05-11
> **gordintoronto said:**
> You may be able to get the results you want by running Nvidia X Server Settings. Avoid the command line and editing config files if you can!

Without editing the config files, Nvidia X Server settings only allowed  me to set a 640x480 resolution. And I can't force the resolution to  higher due to the ViewPortOut setting set to the maximum resolution  available for this screen (ie: 640x480).

I would gladly only use it if it actually works, but it doesn't.

At least now (with the configuration file) I can go up to 1360x768 in the Nvidia X Settings (I don't know why this max resolution, since I explicitly set 1920x1080).

Do you think the issue comes from 14.04 ? Should I downgrade to 12.04 to solve the issue ? Or is it the same mess ?

---

### Post by gordintoronto on 2015-05-12
I'm 95% certain that your DVI to VGA adapter is the problem.

Can Nvidia X Server settings detect the monitor properly? (Detect Displays)

---

