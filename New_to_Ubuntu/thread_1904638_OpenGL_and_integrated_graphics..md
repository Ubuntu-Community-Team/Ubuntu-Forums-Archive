---
title: "OpenGL and integrated graphics."
date: 2012-01-05
forum: New to Ubuntu
---

### Post by Dastweeper on 2012-01-05
Greetings party peoples & the place to be!

I currently am in possession of an ACER Aspire 5735Z, an integrated graphics problem, Ubuntu 11.10, and a hole in the wall where my head used to be.

I was trying to play a game or three on my laptop, but strangely, none of them would run. After a fair amount of ticked-offedness over its lack of working, I gave up and watched cat videos. Then I...well, let's just skip ahead 3 or 4 hours.

After attempting to run Blender after installing it, I finally hit upon the idea that my integrated graphics card probably doesn't like Ubuntu very much, and that all the things that weren't working had to do with OpenGL and/or 3d hardware acceleration. 

So what does an ex-Windows user do when his hardware isn't playing nice with his software? That's right! Iiiiiiiiit's DRIVER TIME! Or so I thought. 

You see, I have an Intel GMA 4500MHD integrated graphics card/system/thingie included in my laptop. As such, I spent 2 fun hours rummaging around Intel's website until I finally found something that's *kind of *what I want. Do they support Ubuntu? Of course not. How silly of me. If I was running Fedora 10 or any Windows distribution under the sun, I'd be fine. But Nooooo. Yet another middle finger for me.

So what do I do? I've lurked and lurked until I can lurk no moar, and have finally resorted to posting a thread about this. The site that has the right drivers, (as far as I ca n tell) is [here]("http://www.intel.com/p/en_US/embedded/hwsw/software/iegd#download"). Am I even approaching this correctly?



And if you actually read my tome of a post, a heartfelt thank you and my greatest condolences go out to you.

---

### Post by SingingBush on 2012-01-05
Ubuntu would have auto detected the Intel graphics chip and installed the relevant drivers. The only time you are likely to manually install a graphics driver is if you want the official AMD or Nvidia drivers.

Run '[COLOR="DarkRed"]glxgears[/COLOR]' on the command line, if you see 3d gears turning then your GPU is working correctly. I suspect your problem is more likely down to trying to run 3d applications that your Intel chip does not support.

OpenGL has gone through many improvements over the years and not all graphics chips will support the features that some particular software may require

[COLOR="Blue"]edit[/COLOR]:
A quick google search will show that running the following in a terminal will let you know if direct rendering is enabled or not:
```
glxinfo | grep direct
```

The intel video card driver package is:
```
xserver-xorg-video-intel
```

---

### Post by Dastweeper on 2012-01-05
After running the aforementioned "glxgears" command, I recieved the following:
```

Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual

```

Yaay. Apparently, I don't have GLX. Whatever that is. 

At any rate, does this mean I no can haz OpenGL?
Does this mean that my Blending days are over? No more lovely 3-dimensoinal acceleration?
No more playing *like half the game I got from the humble Indie Bundle?*

Crap.

---

### Post by mcduck on 2012-01-05
GLX is the OpenGL extension for X window system.

Anyway, have you already tried updating your graphics drivers from the [X-Updates]("https://launchpad.net/~ubuntu-x-swat/+archive/x-updates") or [Xorg-Edgers]("https://launchpad.net/~xorg-edgers/+archive/ppa") PPA repository?

Looking for things you need from default repositories first, and then searching for a suitable third-party repository before even bothering to check the manufacturers/developers web page would pretty much be the way you want to deal with this kind of stuff on Ubuntu. :)

---

### Post by Dastweeper on 2012-01-05
Very helpful, mcduck. Thank you.

Alas, though, I feel like a nub yet again. How do I know which repository is right for me? Just get the fglrx installer for my system?

---

### Post by mcduck on 2012-01-05
> **Dastweeper said:**
> Very helpful, mcduck. Thank you.

Alas, though, I feel like a nub yet again. How do I know which repository is right for me? Just get the fglrx installer for my system?

Well, definitely not fglrx if you have an Intel graphics card like you said (fglrx is the Ati/AMD graphics driver ;))

The X-Updates doesn't seem to have anything for Intel currently, so go for Xorg-Edgers. Just add the repository using the instructions on the web site, and run a normal system update:

```
sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by Dastweeper on 2012-01-05
Ooh... So close. I followed your commands mcduck, but according to glxgears, I still don't have OpenGL.

Is that the right repository for me? I'm out of ideas.

---

### Post by anewguy on 2012-01-05
You can try installing glx via:

sudo apt-get install mesa-utils



I'm also curious - are any of the things you are having problems running flash based?


Dave ;)

---

### Post by mastablasta on 2012-01-05
did it install the repository? 
 
strange that you dont' have openGL as it should be supported for this card.
 
maybe you can find something here:
[https://wiki.ubuntu.com/X/Troubleshooting/IntelPerformance](https://wiki.ubuntu.com/X/Troubleshooting/IntelPerformance)

---

### Post by Dastweeper on 2012-01-05
> **mastablasta said:**
> did it install the repository? 
 
strange that you dont' have openGL as it should be supported for this card.
 
maybe you can find something here:
[https://wiki.ubuntu.com/X/Troubleshooting/IntelPerformance](https://wiki.ubuntu.com/X/Troubleshooting/IntelPerformance)
  As far as I can tell it did, I mean I waited for 2-4 minutes as a bunch of Terminal text whizzed by. I'm not a complete newbie, and what I read of it sounded encouraging.

I'll try installing the mesa utilities (although I'm more of an Aperture Science fan) and see if that helps, anewguy. And as far as I know, the things I'm trying to run are not flash based.

[UPDATE]
Knickers. The mesa utilities didn't work either. Any other ideas? What on earth is going on?

---

### Post by anewguy on 2012-01-06
Sorry that didn't work for you - I had tried glxgears and found I had to install the mesa-utils in order to get glxgears.  Oh well.  I'll keep looking and see if I can find anything.

I'm also wondering, since the glxgears message was about glx not being on display :0:0, perhaps we are going to need to add that part of of xorg.conf so that a display is defined using GLX.

Dave ;)

---

### Post by gsocker on 2012-01-06
Any setup from the last couple of years should have GLX/OpenGL enabled by default if your graphics chips is supported, which it should be. 
The X server creates a log file, which will contain any error messages from the driver.

Could you post the contents of ```
/var/log/Xorg.0.log
```

Use code tags - it will preserve the formatting.

---

### Post by anewguy on 2012-01-06
A search of the web finds that this problem is not new, nor is the hardware.  that's why I'm still looking.  I'm still leaning towards creating an xorg.conf with just the adapter definition in it with "use glx" or whatever the syntax is now.  I've been looking at xrandr to see if there is a way to test this first.

Dave ;)

---

### Post by Dastweeper on 2012-01-07
Here ya go gsocker, the contents of Xorg.0.log
```
[    21.535] 
X.Org X Server 1.11.2.902 (1.11.3 RC 2)
Release Date: 2011-12-09
[    21.535] X Protocol Version 11, Revision 0
[    21.535] Build Operating System: Linux 2.6.24-29-xen i686 Ubuntu
[    21.535] Current Operating System: Linux Lappy586 3.0.0-14-generic #23-Ubuntu SMP Mon Nov 21 20:34:47 UTC 2011 i686
[    21.535] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-14-generic root=UUID=3f0354ab-2553-483a-b948-530f477461d4 ro quiet splash vt.handoff=7
[    21.535] Build Date: 10 December 2011  11:17:47PM
[    21.535] xorg-server 2:1.11.2.902+git20111209+server-1.11-branch.0ca8869e-0ubuntu0sarvatt~oneiric (For technical support please see http://www.ubuntu.com/support) 
[    21.535] Current version of pixman: 0.24.0
[    21.535]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    21.535] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    21.535] (==) Log file: "/var/log/Xorg.0.log", Time: Sat Jan  7 00:22:45 2012
[    21.572] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    21.650] (==) No Layout section.  Using the first Screen section.
[    21.650] (==) No screen section available. Using defaults.
[    21.650] (**) |-->Screen "Default Screen Section" (0)
[    21.650] (**) |   |-->Monitor "<default monitor>"
[    21.651] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    21.651] (==) Automatically adding devices
[    21.651] (==) Automatically enabling devices
[    21.717] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    21.717]     Entry deleted from font path.
[    21.717] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    21.717]     Entry deleted from font path.
[    21.717] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    21.717]     Entry deleted from font path.
[    21.720] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    21.720]     Entry deleted from font path.
[    21.720] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    21.720]     Entry deleted from font path.
[    21.735] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    21.735] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    21.735] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    21.736] (II) Loader magic: 0x822a580
[    21.736] (II) Module ABI versions:
[    21.736]     X.Org ANSI C Emulation: 0.4
[    21.736]     X.Org Video Driver: 11.0
[    21.736]     X.Org XInput driver : 13.0
[    21.736]     X.Org Server Extension : 6.0
[    21.737] (--) PCI:*(0:0:2:0) 8086:2a42:1025:0176 rev 7, Mem @ 0xf8000000/4194304, 0xd0000000/268435456, I/O @ 0x00001800/8
[    21.737] (--) PCI: (0:0:2:1) 8086:2a43:1025:0176 rev 7, Mem @ 0xf8400000/1048576
[    21.737] (II) Open ACPI successful (/var/run/acpid.socket)
[    21.737] (II) LoadModule: "extmod"
[    21.839] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    21.857] (II) Module extmod: vendor="X.Org Foundation"
[    21.857]     compiled for 1.11.2.902, module version = 1.0.0
[    21.857]     Module class: X.Org Server Extension
[    21.857]     ABI class: X.Org Server Extension, version 6.0
[    21.857] (II) Loading extension MIT-SCREEN-SAVER
[    21.857] (II) Loading extension XFree86-VidModeExtension
[    21.857] (II) Loading extension XFree86-DGA
[    21.857] (II) Loading extension DPMS
[    21.857] (II) Loading extension XVideo
[    21.857] (II) Loading extension XVideo-MotionCompensation
[    21.857] (II) Loading extension X-Resource
[    21.857] (II) LoadModule: "dbe"
[    21.858] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    21.873] (II) Module dbe: vendor="X.Org Foundation"
[    21.873]     compiled for 1.11.2.902, module version = 1.0.0
[    21.873]     Module class: X.Org Server Extension
[    21.873]     ABI class: X.Org Server Extension, version 6.0
[    21.873] (II) Loading extension DOUBLE-BUFFER
[    21.873] (II) LoadModule: "glx"
[    21.873] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/libglx.so
[    22.852] (II) Module glx: vendor="NVIDIA Corporation"
[    22.852]     compiled for 4.0.2, module version = 1.0.0
[    22.852]     Module class: X.Org Server Extension
[    22.852] (II) NVIDIA GLX Module  290.10  Wed Nov 16 19:49:02 PST 2011
[    22.852] (II) Loading extension GLX
[    22.852] (II) LoadModule: "record"
[    22.852] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    22.863] (II) Module record: vendor="X.Org Foundation"
[    22.863]     compiled for 1.11.2.902, module version = 1.13.0
[    22.863]     Module class: X.Org Server Extension
[    22.863]     ABI class: X.Org Server Extension, version 6.0
[    22.863] (II) Loading extension RECORD
[    22.863] (II) LoadModule: "dri"
[    22.864] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    22.884] (II) Module dri: vendor="X.Org Foundation"
[    22.884]     compiled for 1.11.2.902, module version = 1.0.0
[    22.884]     ABI class: X.Org Server Extension, version 6.0
[    22.884] (II) Loading extension XFree86-DRI
[    22.884] (II) LoadModule: "dri2"
[    22.884] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    22.896] (II) Module dri2: vendor="X.Org Foundation"
[    22.896]     compiled for 1.11.2.902, module version = 1.2.0
[    22.896]     ABI class: X.Org Server Extension, version 6.0
[    22.896] (II) Loading extension DRI2
[    22.896] (==) Matched intel as autoconfigured driver 0
[    22.896] (==) Matched vesa as autoconfigured driver 1
[    22.896] (==) Matched fbdev as autoconfigured driver 2
[    22.896] (==) Assigned the driver to the xf86ConfigLayout
[    22.896] (II) LoadModule: "intel"
[    22.896] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    22.926] (II) Module intel: vendor="X.Org Foundation"
[    22.926]     compiled for 1.11.2.902, module version = 2.17.0
[    22.926]     Module class: X.Org Video Driver
[    22.926]     ABI class: X.Org Video Driver, version 11.0
[    22.926] (II) LoadModule: "vesa"
[    22.926] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    22.938] (II) Module vesa: vendor="X.Org Foundation"
[    22.938]     compiled for 1.11.2, module version = 2.3.0
[    22.938]     Module class: X.Org Video Driver
[    22.938]     ABI class: X.Org Video Driver, version 11.0
[    22.938] (II) LoadModule: "fbdev"
[    22.939] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    22.957] (II) Module fbdev: vendor="X.Org Foundation"
[    22.957]     compiled for 1.11.2, module version = 0.4.2
[    22.957]     Module class: X.Org Video Driver
[    22.957]     ABI class: X.Org Video Driver, version 11.0
[    22.957] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
    i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
    E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
    965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
    4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
    Sandybridge Desktop (GT1), Sandybridge Desktop (GT2),
    Sandybridge Desktop (GT2+), Sandybridge Mobile (GT1),
    Sandybridge Mobile (GT2), Sandybridge Mobile (GT2+),
    Sandybridge Server, Ivybridge Mobile (GT1), Ivybridge Mobile (GT2),
    Ivybridge Desktop (GT1), Ivybridge Desktop (GT2), Ivybridge Server
[    22.968] (II) VESA: driver for VESA chipsets: vesa
[    22.968] (II) FBDEV: driver for framebuffer: fbdev
[    22.969] (++) using VT number 7

[    22.972] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    22.972] (WW) Falling back to old probe method for vesa
[    22.972] (WW) Falling back to old probe method for fbdev
[    22.972] (II) Loading sub module "fbdevhw"
[    22.972] (II) LoadModule: "fbdevhw"
[    22.972] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    22.989] (II) Module fbdevhw: vendor="X.Org Foundation"
[    22.989]     compiled for 1.11.2.902, module version = 0.0.2
[    22.989]     ABI class: X.Org Video Driver, version 11.0
[    22.989] drmOpenDevice: node name is /dev/dri/card0
[    22.989] drmOpenDevice: open result is 12, (OK)
[    22.989] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[    22.989] drmOpenDevice: node name is /dev/dri/card0
[    22.989] drmOpenDevice: open result is 12, (OK)
[    22.989] drmOpenByBusid: drmOpenMinor returns 12
[    22.989] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    22.989] (II) intel(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    22.989] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    22.989] (==) intel(0): RGB weight 888
[    22.989] (==) intel(0): Default visual is TrueColor
[    22.989] (II) intel(0): Integrated Graphics Chipset: Intel(R) GM45
[    22.989] (--) intel(0): Chipset: "GM45"
[    22.989] (**) intel(0): Relaxed fencing enabled
[    22.989] (**) intel(0): Wait on SwapBuffers? enabled
[    22.989] (**) intel(0): Triple buffering? enabled
[    22.989] (**) intel(0): Framebuffer tiled
[    22.989] (**) intel(0): Pixmaps tiled
[    22.989] (**) intel(0): 3D buffers tiled
[    22.989] (**) intel(0): SwapBuffers wait enabled
[    22.989] (==) intel(0): video overlay key set to 0x101fe
[    22.990] (II) intel(0): Output LVDS1 has no monitor section
[    22.993] (II) intel(0): found backlight control interface /sys/class/backlight/acpi_video0
[    23.012] (II) intel(0): Output VGA1 has no monitor section
[    23.013] (II) intel(0): Output DP1 has no monitor section
[    23.013] (II) intel(0): EDID for output LVDS1
[    23.013] (II) intel(0): Manufacturer: AUO  Model: 10ec  Serial#: 0
[    23.013] (II) intel(0): Year: 2008  Week: 1
[    23.013] (II) intel(0): EDID Version: 1.3
[    23.013] (II) intel(0): Digital Display Input
[    23.013] (II) intel(0): Max Image Size [cm]: horiz.: 34  vert.: 19
[    23.013] (II) intel(0): Gamma: 2.20
[    23.013] (II) intel(0): No DPMS capabilities specified
[    23.013] (II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    23.013] (II) intel(0): First detailed timing is preferred mode
[    23.013] (II) intel(0): redX: 0.640 redY: 0.342   greenX: 0.310 greenY: 0.580
[    23.013] (II) intel(0): blueX: 0.150 blueY: 0.120   whiteX: 0.313 whiteY: 0.329
[    23.013] (II) intel(0): Manufacturer's mask: 0
[    23.013] (II) intel(0): Supported detailed timing:
[    23.013] (II) intel(0): clock: 72.0 MHz   Image Size:  344 x 193 mm
[    23.013] (II) intel(0): h_active: 1366  h_sync: 1414  h_sync_end 1446 h_blank_end 1486 h_border: 0
[    23.013] (II) intel(0): v_active: 768  v_sync: 771  v_sync_end 775 v_blanking: 806 v_border: 0
[    23.013] (II) intel(0): Unknown vendor-specific block f
[    23.013] (II) intel(0):  AUO
[    23.013] (II) intel(0):  B156XW01 V0
[    23.013] (II) intel(0): EDID (in hex):
[    23.013] (II) intel(0):     00ffffffffffff0006afec1000000000
[    23.013] (II) intel(0):     01120103802213780ae6b5a3574f9426
[    23.013] (II) intel(0):     1e505400000001010101010101010101
[    23.013] (II) intel(0):     010101010101201c5678500026303020
[    23.013] (II) intel(0):     340058c1100000180000000f00000000
[    23.013] (II) intel(0):     00000000000000000020000000fe0041
[    23.013] (II) intel(0):     554f0a202020202020202020000000fe
[    23.013] (II) intel(0):     004231353658573031205630200a002a
[    23.013] (II) intel(0): EDID vendor "AUO", prod id 4332
[    23.013] (II) intel(0): Printing DDC gathered Modelines:
[    23.013] (II) intel(0): Modeline "1366x768"x0.0   72.00  1366 1414 1446 1486  768 771 775 806 -hsync -vsync (48.5 kHz)
[    23.013] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[    23.013] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    23.013] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    23.013] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[    23.013] (II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
[    23.013] (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
[    23.013] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[    23.013] (II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
[    23.013] (II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
[    23.013] (II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
[    23.013] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    23.013] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    23.013] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    23.013] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[    23.013] (II) intel(0): Not using default mode "720x450" (doublescan mode not supported)
[    23.013] (II) intel(0): Not using default mode "800x512" (doublescan mode not supported)
[    23.013] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    23.013] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    23.013] (II) intel(0): Not using default mode "960x540" (doublescan mode not supported)
[    23.013] (II) intel(0): Not using default mode "960x600" (doublescan mode not supported)
[    23.013] (II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
[    23.013] (II) intel(0): Printing probed modes for output LVDS1
[    23.013] (II) intel(0): Modeline "1366x768"x60.1   72.00  1366 1414 1446 1486  768 771 775 806 -hsync -vsync (48.5 kHz)
[    23.014] (II) intel(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
[    23.014] (II) intel(0): Modeline "1360x768"x60.0   72.00  1360 1408 1440 1520  768 771 781 790 +hsync -vsync (47.4 kHz)
[    23.014] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    23.014] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    23.014] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    23.014] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    23.036] (II) intel(0): EDID for output VGA1
[    23.037] (II) intel(0): EDID for output DP1
[    23.037] (II) intel(0): Output LVDS1 connected
[    23.037] (II) intel(0): Output VGA1 disconnected
[    23.037] (II) intel(0): Output DP1 disconnected
[    23.037] (II) intel(0): Using exact sizes for initial modes
[    23.037] (II) intel(0): Output LVDS1 using initial mode 1366x768
[    23.037] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    23.037] (II) intel(0): Kernel page flipping support detected, enabling
[    23.037] (**) intel(0): Display dimensions: (340, 190) mm
[    23.037] (**) intel(0): DPI set to (102, 102)
[    23.037] (II) Loading sub module "fb"
[    23.037] (II) LoadModule: "fb"
[    23.037] (II) Loading /usr/lib/xorg/modules/libfb.so
[    23.061] (II) Module fb: vendor="X.Org Foundation"
[    23.061]     compiled for 1.11.2.902, module version = 1.0.0
[    23.061]     ABI class: X.Org ANSI C Emulation, version 0.4
[    23.061] (II) Loading sub module "dri2"
[    23.061] (II) LoadModule: "dri2"
[    23.062] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    23.062] (II) Module dri2: vendor="X.Org Foundation"
[    23.062]     compiled for 1.11.2.902, module version = 1.2.0
[    23.062]     ABI class: X.Org Server Extension, version 6.0
[    23.062] (II) UnloadModule: "vesa"
[    23.062] (II) Unloading vesa
[    23.062] (II) UnloadModule: "fbdev"
[    23.062] (II) Unloading fbdev
[    23.062] (II) UnloadModule: "fbdevhw"
[    23.062] (II) Unloading fbdevhw
[    23.062] (==) Depth 24 pixmap format is 32 bpp
[    23.062] (II) intel(0): [DRI2] Setup complete
[    23.062] (II) intel(0): [DRI2]   DRI driver: i965
[    23.062] (II) intel(0): Allocated new frame buffer 1408x768 stride 5632, tiled
[    23.101] (II) UXA(0): Driver registered support for the following operations:
[    23.101] (II)         solid
[    23.101] (II)         copy
[    23.101] (II)         composite (RENDER acceleration)
[    23.101] (II)         put_image
[    23.101] (II)         get_image
[    23.101] (==) intel(0): Backing store disabled
[    23.101] (==) intel(0): Silken mouse enabled
[    23.101] (II) intel(0): Initializing HW Cursor
[    23.116] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    23.131] (==) intel(0): DPMS enabled
[    23.131] (==) intel(0): Intel XvMC decoder enabled
[    23.131] (II) intel(0): Set up textured video
[    23.131] (II) intel(0): [XvMC] xvmc_vld driver initialized.
[    23.131] (II) intel(0): direct rendering: DRI2 Enabled
[    23.131] (==) intel(0): hotplug detection: "enabled"
[    23.132] (--) RandR disabled
[    23.132] (II) Initializing built-in extension Generic Event Extension
[    23.132] (II) Initializing built-in extension SHAPE
[    23.132] (II) Initializing built-in extension MIT-SHM
[    23.132] (II) Initializing built-in extension XInputExtension
[    23.132] (II) Initializing built-in extension XTEST
[    23.132] (II) Initializing built-in extension BIG-REQUESTS
[    23.132] (II) Initializing built-in extension SYNC
[    23.132] (II) Initializing built-in extension XKEYBOARD
[    23.132] (II) Initializing built-in extension XC-MISC
[    23.132] (II) Initializing built-in extension SECURITY
[    23.132] (II) Initializing built-in extension XINERAMA
[    23.132] (II) Initializing built-in extension XFIXES
[    23.132] (II) Initializing built-in extension RENDER
[    23.132] (II) Initializing built-in extension RANDR
[    23.132] (II) Initializing built-in extension COMPOSITE
[    23.132] (II) Initializing built-in extension DAMAGE
[    23.144] (EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
[    23.153] (II) intel(0): Setting screen physical size to 361 x 203
[    23.279] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    23.298] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    23.298] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    23.298] (II) LoadModule: "evdev"
[    23.298] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    23.312] (II) Module evdev: vendor="X.Org Foundation"
[    23.312]     compiled for 1.11.2.902, module version = 2.6.99
[    23.312]     Module class: X.Org XInput Driver
[    23.312]     ABI class: X.Org XInput driver, version 13.0
[    23.312] (II) Using input driver 'evdev' for 'Power Button'
[    23.312] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    23.312] (**) Power Button: always reports core events
[    23.312] (**) evdev: Power Button: Device: "/dev/input/event2"
[    23.312] (--) evdev: Power Button: Vendor 0 Product 0x1
[    23.312] (--) evdev: Power Button: Found keys
[    23.312] (II) evdev: Power Button: Configuring as keyboard
[    23.312] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[    23.312] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    23.312] (**) Option "xkb_rules" "evdev"
[    23.312] (**) Option "xkb_model" "pc105"
[    23.312] (**) Option "xkb_layout" "us"
[    23.313] (II) config/udev: Adding input device Video Bus (/dev/input/event4)
[    23.326] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    23.326] (II) Using input driver 'evdev' for 'Video Bus'
[    23.326] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    23.326] (**) Video Bus: always reports core events
[    23.326] (**) evdev: Video Bus: Device: "/dev/input/event4"
[    23.326] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    23.326] (--) evdev: Video Bus: Found keys
[    23.326] (II) evdev: Video Bus: Configuring as keyboard
[    23.326] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input4/event4"
[    23.326] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[    23.326] (**) Option "xkb_rules" "evdev"
[    23.326] (**) Option "xkb_model" "pc105"
[    23.326] (**) Option "xkb_layout" "us"
[    23.327] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    23.327] (II) No input driver/identifier specified (ignoring)
[    23.327] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
[    23.327] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    23.327] (II) Using input driver 'evdev' for 'Sleep Button'
[    23.327] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    23.327] (**) Sleep Button: always reports core events
[    23.327] (**) evdev: Sleep Button: Device: "/dev/input/event1"
[    23.327] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[    23.327] (--) evdev: Sleep Button: Found keys
[    23.327] (II) evdev: Sleep Button: Configuring as keyboard
[    23.327] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1/event1"
[    23.327] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 8)
[    23.327] (**) Option "xkb_rules" "evdev"
[    23.327] (**) Option "xkb_model" "pc105"
[    23.327] (**) Option "xkb_layout" "us"
[    23.328] (II) config/udev: Adding input device HDA Intel Mic (/dev/input/event6)
[    23.328] (II) No input driver/identifier specified (ignoring)
[    23.328] (II) config/udev: Adding input device HDA Intel Headphone (/dev/input/event7)
[    23.328] (II) No input driver/identifier specified (ignoring)
[    23.329] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    23.329] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    23.329] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    23.329] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    23.329] (**) AT Translated Set 2 keyboard: always reports core events
[    23.329] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    23.329] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    23.329] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    23.329] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    23.329] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[    23.329] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 9)
[    23.329] (**) Option "xkb_rules" "evdev"
[    23.329] (**) Option "xkb_model" "pc105"
[    23.329] (**) Option "xkb_layout" "us"
[    23.329] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event5)
[    23.329] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    23.329] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    23.329] (II) LoadModule: "synaptics"
[    23.330] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    23.465] (II) Module synaptics: vendor="X.Org Foundation"
[    23.465]     compiled for 1.11.2, module version = 1.5.99
[    23.465]     Module class: X.Org XInput Driver
[    23.465]     ABI class: X.Org XInput driver, version 13.0
[    23.465] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[    23.465] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    23.465] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    23.465] (**) Option "Device" "/dev/input/event5"
[    23.520] (--) synaptics: SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5720
[    23.520] (--) synaptics: SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4780
[    23.520] (--) synaptics: SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    23.520] (--) synaptics: SynPS/2 Synaptics TouchPad: finger width range 0 - 0
[    23.520] (--) synaptics: SynPS/2 Synaptics TouchPad: buttons: left right double triple scroll-buttons
[    23.520] (--) synaptics: SynPS/2 Synaptics TouchPad: Vendor 0x2 Product 0x7
[    23.524] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    23.524] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    23.528] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input5/event5"
[    23.528] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD, id 10)
[    23.528] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[    23.528] (**) synaptics: SynPS/2 Synaptics TouchPad: MaxSpeed is now 1.75
[    23.528] (**) synaptics: SynPS/2 Synaptics TouchPad: AccelFactor is now 0.037
[    23.528] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    23.528] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[    23.528] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    23.528] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    23.528] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    23.528] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[    23.528] (**) SynPS/2 Synaptics TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"
[    30.234] (II) intel(0): EDID vendor "AUO", prod id 4332
[    30.235] (II) intel(0): Printing DDC gathered Modelines:
[    30.235] (II) intel(0): Modeline "1366x768"x0.0   72.00  1366 1414 1446 1486  768 771 775 806 -hsync -vsync (48.5 kHz)
[    37.818] (II) intel(0): EDID vendor "AUO", prod id 4332
[    37.819] (II) intel(0): Printing DDC gathered Modelines:
[    37.819] (II) intel(0): Modeline "1366x768"x0.0   72.00  1366 1414 1446 1486  768 771 775 806 -hsync -vsync (48.5 kHz)
[    41.776] (II) XKB: reuse xkmfile /var/lib/xkb/server-A77BBE312A49C9FE89948D38B2A8CB84C3CBB410.xkm
[    56.298] (II) intel(0): EDID vendor "AUO", prod id 4332
[    56.298] (II) intel(0): Printing DDC gathered Modelines:
[    56.298] (II) intel(0): Modeline "1366x768"x0.0   72.00  1366 1414 1446 1486  768 771 775 806 -hsync -vsync (48.5 kHz)
[   197.445] (II) XKB: reuse xkmfile /var/lib/xkb/server-A77BBE312A49C9FE89948D38B2A8CB84C3CBB410.xkm
[  1781.623] (II) intel(0): EDID vendor "AUO", prod id 4332
[  1781.645] (II) intel(0): Printing DDC gathered Modelines:
[  1781.645] (II) intel(0): Modeline "1366x768"x0.0   72.00  1366 1414 1446 1486  768 771 775 806 -hsync -vsync (48.5 kHz)
[  5019.569] (II) intel(0): EDID vendor "AUO", prod id 4332
[  5019.569] (II) intel(0): Printing DDC gathered Modelines:
[  5019.569] (II) intel(0): Modeline "1366x768"x0.0   72.00  1366 1414 1446 1486  768 771 775 806 -hsync -vsync (48.5 kHz)
```
After a bit of experimentation, I also found that Blender, which as you all know uses OpenGL, works just fine on Vista, which I also have stowed away on my lappy. So at least we know it's possible.

---

### Post by anewguy on 2012-01-07
Note 23.144

---

### Post by Dastweeper on 2012-01-07
> **anewguy said:**
> Note 23.144
AH-HA! 
```
[    23.144] (EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found) 
```But I installed the Mesa utils and the Xorg edgers packages. Were those incorrect or not enough?

---

### Post by gsocker on 2012-01-07
Well, you seem to have somehow ended up with NVIDIA's GLX library even though you have an intel chip.  Further down, I see [DRI2]: Setup complete, so the driver is loading correctly. All we need to do is fix the GLX problem and you should be set.
 
Open up the terminal. 

Run 
```

dpkg --search /usr/lib/i386-linux-gnu/xorg/extra-modules/libglx.so

```

This will tell us what package installed the NVIDIA version.

Post the output here before removing so we can make sure it won't break your system when removed.

---

### Post by Dastweeper on 2012-01-07
It took some doing, (oddly enough) but anyways, here you go:

```
nvidia-current: /usr/lib/nvidia-current/xorg/libglx.so.290.10
nvidia-current: /usr/lib/nvidia-current/xorg/libglx.so
fglrx: /usr/lib/fglrx/xorg/modules/extensions/libglx.so
xserver-xorg-core: /usr/lib/xorg/modules/extensions/libglx.so

```

For some reason, I had to navigate straight to the directory to do the search command. Go figure.

---

### Post by I_can_see_the_light on 2012-01-07
Well apparently you have both the nvidia and ati proprietary drivers installed. Could you please post the output of the following commands:
```
lspci | grep -i vga
```
```
glxinfo | grep -i opengl
```
```
glxinfo | grep -i direct
```

---

### Post by gsocker on 2012-01-07
As the previous poster said, you have the proprietary drivers installed for hardware you don't have. If you remove both nvidia-current and fglrx, Xorg should end up using the default GLX module.

Since you don't have the hardware, I'm not sure the proprietary drivers tool will work for removal, although you can try. If it won't allow you to remove them, or you can't find it, you can remove using the software center - search for nvidia-current and fglrx and remove.

---

### Post by Dastweeper on 2012-01-07
Well, I removed the packages flgrx and nvidia-current. Should I remove packages associated with them as well?

Here's the output of lspci -i vga:
```
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)

```
The output of Glxinfo OpenGL, (an error):
```
Error: couldn't find RGB GLX visual or fbconfig

```

And the output of glxinfo direct, the exact same:
```
Error: couldn't find RGB GLX visual or fbconfig

```

---

### Post by MrSpike16 on 2012-01-07
Its weird, but Nvidia drivers getting installed too for Intel graphics sometimes happens.
The Nvidia stuff needs to be purged and the Intel drivers, 3D (mesa) and Xorg need to be reinstalled.

These are the commands:

[FONT=monospace]```
sudo apt-get purge nvidia*
sudo apt-get install --reinstall xserver-xorg-video-intel  libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
sudo dpkg-reconfigure xserver-xorg
sudo update-alternatives --remove gl_conf /usr/lib/nvidia-current/ld.so.conf
```

Restart the computer then try glxgears again and it should work.
[/FONT]

---

### Post by Dastweeper on 2012-01-08
And with a parting of the clouds and a chorus of angels, (and by angels I mean 3-d gears rotating,), The Lappy said unto its user: Yea! Indeed I shall implement OpenGL!

I'd like to thank all the little people who could make this happen, starting with the leprechauns. Also, a big thank you to you guys. You were awesome too.

I can't express just how grateful i am that you guys too time out of your day to help troubleshoot a stranger's computer. Thanks!

Now if you'll excuse me, somebody's gonna be doing a little modeling for me. And her name is Blender.

---

