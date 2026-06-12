---
title: "Howto: ATI Mobility Beryl/XGL FGLRX in Edgy"
date: 2006-11-02
forum: Outdated Tutorials &amp; Tips
---

### Post by Paerez on 2006-11-02
[size="5"]This Guide is Dead[/size]
I am no longer supporting this guide. I will leave it up for posterity but if you want compositing effects, please upgrade to feisty (and beyond) and use System->Preferences->Desktop Effects. This guide was a hack to get things running when this technology was new, and now the technology has been tested and made more official (and it works better than this guide).

That said, here is the original guide:


[size="4"]Howto: ATI Radeon Mobility 9000 + Edgy FGLRX ( 8.28 ) + Beryl[/size]
First I would like to thank Lennart Hansen and his guide, and also the Ubuntu Forums for helping me find the FGLRX solutions for suspend/hibernate.

Also I would like to thank my Computer Vision professor for having boring lectures, inspiring me to get beryl working instead of paying attention. Also my Computer Integrated surgery professor for being boring and giving me the motivation to write this guide instead of paying attention. Be cool stay in school!

This guide has 3 parts:
- FGLRX
- Beryl and XGL
- Tweaks & Optimizations

Just to clear things up, when I write:
```
$ echo hello
```
The "$" means to run this on the command line. You can open a terminal by going to Applications->Accessories->Terminal.

When I say Edit "file" I mean run: "$ sudo gedit file" or "$ sudo nano -w file", or any other way you want to edit it.

[size="3"]FGLRX[/size]
Update your packages:
```
$ sudo aptitude update
$ sudo aptitude dist-upgrade
```

Install the driver and module:
```
$ sudo aptitude install xorg-driver-fglrx
```

For some reason, linux-restricted modules will install the modules, but when you reboot they disappear. So what we do is install them, copy the fglrx module to a safe folder, and then uninstall them. **You will have to do this for every kernel update**. When I figure out a better way to do this, I'll update the guide.
```
$ sudo aptitude install linux-restricted-modules-`uname -r`
```

Now copy the module (the first line creates the directory, so if it is already there and there is an error, it is not a problem):
```
$ sudo mkdir /lib/modules/`uname -r`/misc
$ sudo cp /lib/modules/`uname -r`/volatile/fglrx.ko /lib/modules/`uname -r`/misc/fglrx.ko
```

Now uninstall the package:
```
$ sudo aptitude remove linux-restricted-modules-`uname -r`
```

Now update your module list:
```
$ sudo depmod -a
```

Now you've all seen this before if you've tried to use fglrx. If you know what you are doing, you can just edit xorg.conf manually to use fglrx, or just type this:
```
$ sudo aticonfig --initial 
$ sudo aticonfig --overlay-type=Xv
```

Add this to the end of xorg.conf ("$ sudo gedit /etc/X11/xorg.conf" to edit it):
```
Section "Extensions"
        Option      "Composite" "0"
EndSection
```

Now you have two choices to test fglrx.
1) The easy way: reboot
2) If you know what you are doing, log out, switch to a console, stop gdm, rmmod radeon and modprobe fglrx, then start gdm. Then you don't have to reboot.

Log in and make sure that fglrx is working:
```
$ fglrxinfo
```

Mine spits out:
```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY/RADEON 9000 DDR Generic
OpenGL version string: 1.3.1091 (X4.3.0-8.28.8)
```

Make sure it says ATI and not Mesa.

[size="3"]Beryl and XGL[/size]
Big thanks to this guide:
[http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html](http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html)

I pretty much copied what he did, but on the command line, because it is easier to do in a text-howto. You can also do things his way.

Edit /etc/apt/sources.list and add this:
```
# beryl
deb http://ubuntu.beryl-project.org edgy main
deb-src http://ubuntu.beryl-project.org edgy main

# beryl-svn
deb http://download.tuxfamily.org/3v1deb edgy beryl-svn
deb-src http://download.tuxfamily.org/3v1deb edgy beryl-svn

```
The second batch are for the svn releases. As of 2/7/2007 when I edited this, only the svn releases and old versions (<=1.4) are working, so naturally I want the svn because it has cool stuff.

So if you do not want to install the svn packages, you have to manually downgrade to 1.4 to get it to work.

Now update your repo:
```
$ sudo aptitude update
$ sudo aptitude dist-upgrade
```

Now install XGL and Beryl:
```
$ sudo aptitude install beryl emerald-themes xserver-xgl
```

Now create the XGL script. Edit "/usr/bin/startxgl" and paste in this:
```
#!/bin/sh
Xgl :1 -fullscreen -ac -accel xv:pbuffer -accel glx:pbuffer &
DISPLAY=:1
exec dbus-launch --exit-with-session gnome-session
```

Make it executable:
```
$ sudo chmod +x /usr/bin/startxgl
```

Now make a separate session for XGL. Edit "/usr/share/xsessions/xgl.desktop":
```
[Desktop Entry]
Encoding=UTF-8
Name=Xgl
Comment=Start an Xgl Session
Exec=/usr/bin/startxgl
Icon=
Type=Application
```

Now log out, and log in with the XGL session (click Sessions and choose XGL). Once you log in, run "beryl-manager" to start beryl. You can add this to your session start up programs if you want, but its good to test it first.

**If you try to move a window and it crashes, read the next section!!!**

[size="3"]Tweaks & Optimizations[/size]
**Read first**
You can always log in to normal gnome and run "beryl-manager" to edit settings without beryl being loaded. This is very useful.

**Start beryl-manager automatically**
Click System->Preferences->Sessions
Go to the Startup Programs tab and click Add, then type "beryl-manager".

**Crashes & Performance**
I had trouble with wobbly windows, and also since the Mobility 9000 isnt that great a card, I tuned some stuff down for good responsiveness. Download the attached beryl-settings.Profile and click the beryl-manager icon and click Beryl Settings Manager and click import and import the attached file (after unzipping).

Also check out this post:
[http://www.ubuntuforums.org/showthread.php?t=276498](http://www.ubuntuforums.org/showthread.php?t=276498)

**Dashing Good Looks**
I opened the emerald theme manager (right click the beryl icon) and chose the human theme, because I like it. Also I clicked the Emerald Settings tab and made the Titlebar Doubleclick Action = Maximize/Restore.

**Hey why don't my caps/skydome work?!**
If your caps don't work, try converting to PNG. Also, for skydome, make sure your resolution of your image is a power of two by a power of two. Like any of these dimensions:
512x512, 2048x1024, 4096x512, etc... Any combo of a power of two will work.

**FGLRX Suspend and Hibernate**
Edit "/etc/default/acpi-support" and change the following lines:
```
MODULES_WHITELIST="fglrx"
SAVE_VBE_STATE=false
POST_VIDEO=false
DOUBLE_CONSOLE_SWITCH=true
```

**Turn off the gnome-panel "launching box" that runs slow in xgl**
Run gconf-editor and go to:
/apps/panel/global
and uncheck "enable animations"

---

### Post by ethon on 2006-11-02
Thanks for writing this guide, unfortunately I cannot get past the first half of installing the fglrx drivers.

fglrxinfo gives me:

```

display: :0.0  screen: 0
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI R200 20060602 AGP 4x NO-TCL
OpenGL version string: 1.2 (1.3 Mesa 6.5.1)


```

Any help is appreciated :)

---

### Post by nevin on 2006-11-03
i get an error message that says:

XGL Absent, checking for NVIDIA
Nividia Absent, assuming AIGLX
beryl:  No composite extension



i have an ati card and the fglrx installed.  i have added:

Section "Extensions"
	Option	    "Composite" 	"0"
EndSection

to the bottom of my xorg.conf file.  (i had to do this to get edgy to give me anything graphical after 6.04 -> 6.10

but i have xserver-xgl installed, i even installed xserver-xorg-video-ati.
im not sure what's going on, but i did have compiz working on 6.04 and so i know beryl should work on my 6.10...

is anyone else having a similar problem?

---

### Post by horatiub on 2006-11-03
I don't see any attachement. Can you please re-attach the profile?

---

### Post by afffffff on 2006-11-03
hi, thanks for the guide, it worked with me but I cant play 3dgames with wine after beryl installed and running, is it possible to run games under beryl?
thx

---

### Post by Paerez on 2006-11-03
Hey all:

1) I attached the file, my bad...
2) I can't get 3d working in any applicaion within beryl, it says that DRI is not found. My mplayer is really slow using Xv, and gl2 doesn't work.
3) For those of you who can't get it to work, can you post your video card?

---

### Post by Anonii on 2006-11-03
So you, even, cant make Direct Rendering work. Can you run Beryl/Compiz without it?

---

### Post by Paerez on 2006-11-03
I get direct rendering working, and thus beryl working too. What I can't get to work is any 3d application *other than* beryl. So it's like beryl hogs the 3d, and whenever another app tries to do 3d, it crashes X.

---

### Post by ethon on 2006-11-03
I have an ATI Mobility Radeon 9000

I've followed numerous guides on this forum to try and get Direct Rendering to work, but it always reverts back to Mesa :(

---

### Post by Paerez on 2006-11-03
ok, go to a terminal and type in the following commands, and paste me the output:
```
$ sudo modprobe fglrx
$ lsmod | grep fglrx
$ lsmod | grep radeon

```

---

### Post by ethon on 2006-11-03
sudo modprobe fglrx produces: 
```
FATAL: Could not open '/lib/modules/2.6.17-10-generic/volatile/fglrx.ko': No such file or directory
```

lsmod grep | fglrx produces no output

lsmod grep | radeon produces:

```
radeon                118816  2 
drm                    74644  3 radeon

```

---

### Post by Anonii on 2006-11-03
Here is my output too:

```
$ lsmod | grep fglrx
fglrx                 405164  8 
agpgart                33456  2 fglrx,intel_agp

```

```

$ lsmod | grep radeon
**NOTHING**

```

```

$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)

```

```

$ glxinfo | grep direct
direct rendering: No
OpenGL renderer string: Mesa GLX Indirect

```
:[
I "installed" fglrx with another guide. I'd like to follow yours,but I dont know the correct way to uninstall the fglrx from the previous one.

---

### Post by Paerez on 2006-11-03
Ethon: You need to follow the linux-restricted-modules steps. If installing does nothing, do a reinstall. You need to copy the module out of the "volatile" folder and into "misc" then run depmod. Just follow the guide, but use "reinstall" instead of "install" if "sudo aptitude install linux-restricted-modules`uname -r`" does nothing.

Anonil: Did you switch your xorg.conf to use fglrx? If so, please post the following:
```
$ grep EE /var/log/Xorg.0.log
$ grep WW /var/log/Xorg.0.log
$ grep fglrx /var/log/Xorg.0.log
```

---

### Post by Anonii on 2006-11-03
```

$ grep EE /var/log/Xorg.0.log
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER
(EE) AIGLX error: dlsym for __driCreateNewScreen_20050727 failed (/usr/lib/dri/fglrx_dri.so: undefined symbol: __driCreateNewScreen_20050727)
(EE) AIGLX: reverting to software rendering
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom

```

```

$ grep WW /var/log/Xorg.0.log
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(WW) `fonts.dir' not found (or not valid) in "/usr/share/X11/fonts/misc".
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
(WW) The directory "/usr/share/X11/fonts/100dpi/" does not exist.
(WW) The directory "/usr/share/X11/fonts/75dpi/" does not exist.
(WW) The directory "/usr/share/X11/fonts/Type1" does not exist.
(WW) The directory "/usr/share/X11/fonts/100dpi" does not exist.
(WW) The directory "/usr/share/X11/fonts/75dpi" does not exist.
(WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType".
(WW) fglrx: No matching Device section for instance (BusID PCI:1:0:1) found
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(WW) fglrx(0): Option "VendorName" is not used
(WW) fglrx(0): Option "ModelName" is not used

(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/modules/drivers/fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
(WW) fglrx: No matching Device section for instance (BusID PCI:1:0:1) found
(II) fglrx(0): pEnt->device->identifier=0x81e18b0
(II) fglrx(0): === [atiddxPreInit] === begin, [s]
(II) fglrx(0): PCI bus 1 card 0 func 0
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(**) fglrx(0): Option "OpenGLOverlay" "off"
(**) fglrx(0): Option "VideoOverlay" "on"
(**) fglrx(0): Option "DPMS" "true"
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB (8 bit DAC)
(==) fglrx(0): Gamma Correction for I is 0x06419064
(==) fglrx(0): Gamma Correction for II is 0x06419064
(==) fglrx(0): Buffer Tiling is ON
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(--) fglrx(0): Chipset: "RADEON 9600 PRO (RV360 4152)" (Chipset = 0x4152)
(--) fglrx(0): (PciSubVendor = 0x196d, PciSubDevice = 0x1058)
(--) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
(--) fglrx(0): Linear framebuffer (phys) at 0xe0000000
(--) fglrx(0): MMIO registers at 0xff8f0000
(==) fglrx(0): ROM-BIOS at 0x000c0000
(II) fglrx(0): VESA BIOS detected
(II) fglrx(0): VESA VBE Version 2.0
(II) fglrx(0): VESA VBE Total Mem: 16384 kB
(II) fglrx(0): VESA VBE OEM: ATI RADEON 9600 PRO
(II) fglrx(0): VESA VBE OEM Software Rev: 1.0
(II) fglrx(0): VESA VBE OEM Vendor: ATI Technologies Inc.
(II) fglrx(0): VESA VBE OEM Product: V350
(II) fglrx(0): VESA VBE OEM Product Rev: 01.00
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/lib/xorg/modules/linux/libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
(--) fglrx(0): VideoRAM: 131072 kByte, Type: DDR SGRAM / SDRAM
(II) fglrx(0): AGP card detected
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(II) fglrx(0): Connected Display1: CRT on primary DAC
(II) fglrx(0): Display1 EDID data ---------------------------
(II) fglrx(0): Manufacturer: NEC  Model: 665a  Serial#: 16843009
(II) fglrx(0): Year: 2006  Week: 2
(II) fglrx(0): EDID Version: 1.3
(II) fglrx(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) fglrx(0): Sync:  Separate
(II) fglrx(0): Max H-Image Size [cm]: horiz.: 38  vert.: 30
(II) fglrx(0): Gamma: 2.20
(II) fglrx(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) fglrx(0): First detailed timing is preferred mode
(II) fglrx(0): redX: 0.642 redY: 0.345   greenX: 0.295 greenY: 0.622
(II) fglrx(0): blueX: 0.144 blueY: 0.074   whiteX: 0.312 whiteY: 0.330
(II) fglrx(0): Supported VESA Video Modes:
(II) fglrx(0): 720x400@70Hz
(II) fglrx(0): 640x480@60Hz
(II) fglrx(0): 640x480@67Hz
(II) fglrx(0): 640x480@72Hz
(II) fglrx(0): 640x480@75Hz
(II) fglrx(0): 800x600@56Hz
(II) fglrx(0): 800x600@60Hz
(II) fglrx(0): 800x600@72Hz
(II) fglrx(0): 800x600@75Hz
(II) fglrx(0): 832x624@75Hz
(II) fglrx(0): 1024x768@60Hz
(II) fglrx(0): 1024x768@70Hz
(II) fglrx(0): 1024x768@75Hz
(II) fglrx(0): 1280x1024@75Hz
(II) fglrx(0): 1152x870@75Hz
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported Future Video Modes:
(II) fglrx(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) fglrx(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 108.0 MHz   Image Size:  376 x 301 mm
(II) fglrx(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) fglrx(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) fglrx(0): Ranges: V min: 56  V max: 75 Hz, H min: 31  H max: 81 kHz, PixClock max 140 MHz
(II) fglrx(0): Monitor name: LCD92VM
(II) fglrx(0): Serial No: 61D28528NB
(II) fglrx(0): End of Display1 EDID data --------------------
(II) fglrx(0): Primary Controller - CRT on primary DAC
(II) fglrx(0): Internal Desktop Setting: 0x00000008
(II) fglrx(0): POWERplay version 3.  4 power states available:
(II) fglrx(0):   1. 500/297MHz @ 50Hz [enable load balancing, overdrive]
(II) fglrx(0):   2. 398/297MHz @ 50Hz [enable load balancing, overdrive]
(II) fglrx(0):   3. 513/297MHz @ 50Hz [overclocked, enable load balancing, overdrive]
(II) fglrx(0):   4. 527/297MHz @ 50Hz [overclocked, enable load balancing, overdrive]
(==) fglrx(0): Qbs disabled
(==) fglrx(0): FAST_SWAP disabled
(==) fglrx(0):  PseudoColor visuals disabled
(==) fglrx(0): Using gamma correction (1.0, 1.0, 1.0)
(==) fglrx(0): Center Mode is disabled 
(==) fglrx(0): TMDS coherent mode is enabled 
(II) fglrx(0): Total of 32 modes found for primary display.
(--) fglrx(0): Virtual size is 1280x1024 (pitch 0)
(**) fglrx(0): *Mode "1280x1024": 135.0 MHz (scaled from 0.0 MHz), 80.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1280x1024"  135.00  1280 1296 1440 1688  1024 1025 1028 1066
(**) fglrx(0):  Default mode "1280x1024": 128.9 MHz (scaled from 0.0 MHz), 74.6 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1280x1024"  128.94  1280 1368 1504 1728  1024 1025 1028 1066 +hsync
(**) fglrx(0):  Default mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x1024"  108.00  1280 1328 1440 1688  1024 1025 1028 1066
(**) fglrx(0): *Mode "1152x864": 108.0 MHz (scaled from 0.0 MHz), 67.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1152x864"  108.00  1152 1216 1344 1600  864 865 868 900
(**) fglrx(0):  Default mode "1152x864": 96.8 MHz (scaled from 0.0 MHz), 63.0 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1152x864"   96.76  1152 1224 1344 1536  864 865 868 900 +hsync
(**) fglrx(0):  Default mode "1152x864": 81.6 MHz (scaled from 0.0 MHz), 53.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1152x864"   81.62  1152 1216 1336 1520  864 865 868 895 +hsync
(**) fglrx(0): *Mode "1024x768": 78.8 MHz (scaled from 0.0 MHz), 60.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1024x768"   78.75  1024 1040 1136 1312  768 769 772 800
(**) fglrx(0):  Default mode "1024x768": 78.4 MHz (scaled from 0.0 MHz), 57.7 kHz, 72.0 Hz
(II) fglrx(0): Modeline "1024x768"   78.43  1024 1080 1192 1360  768 769 772 801 +hsync
(**) fglrx(0):  Default mode "1024x768": 75.0 MHz (scaled from 0.0 MHz), 56.5 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 +hsync +vsync
(**) fglrx(0):  Default mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync
(**) fglrx(0): *Mode "1024x480": 38.2 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x480"   38.16  1024 1048 1152 1280  480 481 484 497 +hsync
(**) fglrx(0): *Mode "848x480": 31.5 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "848x480"   31.48  848 864 952 1056  480 481 484 497 +hsync
(**) fglrx(0): *Mode "800x600": 49.5 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz
(II) fglrx(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625
(**) fglrx(0):  Default mode "800x600": 50.0 MHz (scaled from 0.0 MHz), 48.1 kHz, 72.0 Hz
(II) fglrx(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666
(**) fglrx(0):  Default mode "800x600": 45.5 MHz (scaled from 0.0 MHz), 43.8 kHz, 70.0 Hz
(II) fglrx(0): Modeline "800x600"   45.50  800 840 920 1040  600 601 604 625 +hsync
(**) fglrx(0):  Default mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628
(**) fglrx(0):  Default mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.0 Hz
(II) fglrx(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625
(**) fglrx(0):  Default mode "800x600": 29.6 MHz (scaled from 0.0 MHz), 29.8 kHz, 47.0 Hz (I)
(II) fglrx(0): Modeline "800x600"   29.60  800 816 896 992  600 601 604 635 interlace +hsync
(**) fglrx(0): *Mode "720x576": 32.7 MHz (scaled from 0.0 MHz), 35.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x576"   32.66  720 744 816 912  576 577 580 597 +hsync
(**) fglrx(0): *Mode "720x480": 26.7 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480"   26.71  720 736 808 896  480 481 484 497 +hsync
(**) fglrx(0): *Mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.9 kHz, 72.0 Hz
(II) fglrx(0): Modeline "640x480"   31.50  640 664 704 832  480 489 492 520 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"   25.18  640 656 752 800  480 490 492 525 +hsync +vsync
(**) fglrx(0):  Default mode "640x400": 28.1 MHz (scaled from 0.0 MHz), 33.7 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x400"   28.07  640 696 736 832  400 413 415 449
(**) fglrx(0):  Default mode "640x400": 24.9 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"   24.92  640 664 760 792  400 460 462 525
(**) fglrx(0):  Default mode "512x384": 19.8 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"   19.81  512 544 624 664  384 451 453 497
(**) fglrx(0):  Default mode "400x300": 24.8 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   24.75  400 408 448 528  300 601 602 625 doublescan
(**) fglrx(0):  Default mode "400x300": 22.3 MHz (scaled from 0.0 MHz), 45.0 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   22.33  400 416 480 496  300 601 605 742 doublescan
(**) fglrx(0):  Default mode "320x240": 15.8 MHz (scaled from 0.0 MHz), 37.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   15.75  320 328 360 416  240 481 482 501 doublescan
(**) fglrx(0):  Default mode "320x240": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   12.59  320 328 376 400  240 491 493 525 doublescan
(**) fglrx(0):  Default mode "320x200": 13.1 MHz (scaled from 0.0 MHz), 31.5 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   13.10  320 352 368 416  200 406 407 417 doublescan
(**) fglrx(0):  Default mode "320x200": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   12.59  320 336 384 400  200 457 459 524 doublescan
(--) fglrx(0): Display dimensions: (380, 300) mm
(--) fglrx(0): DPI set to (85, 86)
(--) fglrx(0): Virtual size is 1280x1024 (pitch 1280)
(**) fglrx(0): *Mode "1280x1024": 135.0 MHz (scaled from 0.0 MHz), 80.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1280x1024"  135.00  1280 1296 1440 1688  1024 1025 1028 1066
(**) fglrx(0):  Default mode "1280x1024": 128.9 MHz (scaled from 0.0 MHz), 74.6 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1280x1024"  128.94  1280 1368 1504 1728  1024 1025 1028 1066 +hsync
(**) fglrx(0):  Default mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x1024"  108.00  1280 1328 1440 1688  1024 1025 1028 1066
(**) fglrx(0): *Mode "1152x864": 108.0 MHz (scaled from 0.0 MHz), 67.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1152x864"  108.00  1152 1216 1344 1600  864 865 868 900
(**) fglrx(0):  Default mode "1152x864": 96.8 MHz (scaled from 0.0 MHz), 63.0 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1152x864"   96.76  1152 1224 1344 1536  864 865 868 900 +hsync
(**) fglrx(0):  Default mode "1152x864": 81.6 MHz (scaled from 0.0 MHz), 53.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1152x864"   81.62  1152 1216 1336 1520  864 865 868 895 +hsync
(**) fglrx(0): *Mode "1024x768": 78.8 MHz (scaled from 0.0 MHz), 60.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1024x768"   78.75  1024 1040 1136 1312  768 769 772 800
(**) fglrx(0):  Default mode "1024x768": 78.4 MHz (scaled from 0.0 MHz), 57.7 kHz, 72.0 Hz
(II) fglrx(0): Modeline "1024x768"   78.43  1024 1080 1192 1360  768 769 772 801 +hsync
(**) fglrx(0):  Default mode "1024x768": 75.0 MHz (scaled from 0.0 MHz), 56.5 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 +hsync +vsync
(**) fglrx(0):  Default mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync
(**) fglrx(0): *Mode "1024x480": 38.2 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x480"   38.16  1024 1048 1152 1280  480 481 484 497 +hsync
(**) fglrx(0): *Mode "848x480": 31.5 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "848x480"   31.48  848 864 952 1056  480 481 484 497 +hsync
(**) fglrx(0): *Mode "800x600": 49.5 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz
(II) fglrx(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625
(**) fglrx(0):  Default mode "800x600": 50.0 MHz (scaled from 0.0 MHz), 48.1 kHz, 72.0 Hz
(II) fglrx(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666
(**) fglrx(0):  Default mode "800x600": 45.5 MHz (scaled from 0.0 MHz), 43.8 kHz, 70.0 Hz
(II) fglrx(0): Modeline "800x600"   45.50  800 840 920 1040  600 601 604 625 +hsync
(**) fglrx(0):  Default mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628
(**) fglrx(0):  Default mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.0 Hz
(II) fglrx(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625
(**) fglrx(0):  Default mode "800x600": 29.6 MHz (scaled from 0.0 MHz), 29.8 kHz, 47.0 Hz (I)
(II) fglrx(0): Modeline "800x600"   29.60  800 816 896 992  600 601 604 635 interlace +hsync
(**) fglrx(0): *Mode "720x576": 32.7 MHz (scaled from 0.0 MHz), 35.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x576"   32.66  720 744 816 912  576 577 580 597 +hsync
(**) fglrx(0): *Mode "720x480": 26.7 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480"   26.71  720 736 808 896  480 481 484 497 +hsync
(**) fglrx(0): *Mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.9 kHz, 72.0 Hz
(II) fglrx(0): Modeline "640x480"   31.50  640 664 704 832  480 489 492 520 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"   25.18  640 656 752 800  480 490 492 525 +hsync +vsync
(**) fglrx(0):  Default mode "640x400": 28.1 MHz (scaled from 0.0 MHz), 33.7 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x400"   28.07  640 696 736 832  400 413 415 449
(**) fglrx(0):  Default mode "640x400": 24.9 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"   24.92  640 664 760 792  400 460 462 525
(**) fglrx(0):  Default mode "512x384": 19.8 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"   19.81  512 544 624 664  384 451 453 497
(**) fglrx(0):  Default mode "400x300": 24.8 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   24.75  400 408 448 528  300 601 602 625 doublescan
(**) fglrx(0):  Default mode "400x300": 22.3 MHz (scaled from 0.0 MHz), 45.0 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   22.33  400 416 480 496  300 601 605 742 doublescan
(**) fglrx(0):  Default mode "320x240": 15.8 MHz (scaled from 0.0 MHz), 37.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   15.75  320 328 360 416  240 481 482 501 doublescan
(**) fglrx(0):  Default mode "320x240": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   12.59  320 328 376 400  240 491 493 525 doublescan
(**) fglrx(0):  Default mode "320x200": 13.1 MHz (scaled from 0.0 MHz), 31.5 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   13.10  320 352 368 416  200 406 407 417 doublescan
(**) fglrx(0):  Default mode "320x200": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   12.59  320 336 384 400  200 457 459 524 doublescan
(==) fglrx(0): NoAccel = NO
(==) fglrx(0): HPV inactive
(==) fglrx(0): FSAA enabled: NO
(==) fglrx(0): FSAA Gamma enabled
(==) fglrx(0): FSAA Multisample Position is fix
(==) fglrx(0): NoDRI = NO
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Reloading /usr/lib/xorg/modules/linux/libfglrxdrm.so
(II) fglrx(0): Depth moves disabled by default
(==) fglrx(0): Capabilities: 0x00000000
(==) fglrx(0): CapabilitiesEx: 0x00000000
(==) fglrx(0): cpuFlags: 0x8000001d
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(==) fglrx(0): UseFastTLS=0
(==) fglrx(0): BlockSignalsOnLock=1
(==) fglrx(0): EnablePrivateBackZ = NO
(II) fglrx(0): UMM Bus area:     0xe0701000 (size=0x078ff000)
(II) fglrx(0): UMM area:     0xe0701000 (size=0x078ff000)
(II) fglrx(0): driver needs X.org 7.1.x.y with x.y >= 0.0
(II) fglrx(0): detected X.org 7.1.1.0
(II) fglrx(0): doing DRIScreenInit
(II) fglrx(0): [drm] DRM interface version 1.0
(II) fglrx(0): [drm] created "fglrx" driver at busid "PCI:1:0:0"
(II) fglrx(0): [drm] added 8192 byte SAREA at 0x2000
(II) fglrx(0): [drm] mapped SAREA 0x2000 to 0xb7337000
(II) fglrx(0): [drm] framebuffer handle = 0x3000
(II) fglrx(0): [drm] added 1 reserved context for kernel
(II) fglrx(0): DRIScreenInit done
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.29.6
(II) fglrx(0):     Date: Sep 19 2006
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(II) fglrx(0): Kernel Module version matches driver.
(II) fglrx(0): Kernel Module Build Time Information:
(II) fglrx(0):     Build-Kernel UTS_RELEASE:        2.6.17-10-386
(II) fglrx(0):     Build-Kernel MODVERSIONS:        no
(II) fglrx(0):     Build-Kernel __SMP__:            no
(II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
(II) fglrx(0): [drm] register handle = 0x00004000
(II) fglrx(0): [agp] Mode=0x1f004a1b bridge: 0x8086/0x2570
(II) fglrx(0): [agp] AGP v1/2 disable mask 0x00000000
(II) fglrx(0): [agp] AGP v3 disable mask   0x00000000
(II) fglrx(0): [agp] enabling AGP with mode=0x1f004b1a
(II) fglrx(0): [agp] Remapping MC AGP space (new MCAGPBase = 0xf8000000)
(II) fglrx(0): [agp] AGP protocol is enabled for graphics board. (cmd=0x1f004312)
(II) fglrx(0): [agp] graphics chipset has AGP v3.0 (native mode)
(II) fglrx(0): [drm] ringbuffer size = 0x00100000 bytes
(II) fglrx(0): [drm] DRM buffer queue setup: nbufs = 100 bufsize = 65536
(II) fglrx(0): [drm] texture shared area handle = 0x00008000
(II) fglrx(0): shared FSAAScale=1
(II) fglrx(0): DRI initialization successfull!
(II) fglrx(0): FBADPhys: 0xe0000000 FBMappedSize: 0x00701000
(II) fglrx(0): Splitting WC range: base: 0xe0000000, size: 0x701000
(II) fglrx(0): Splitting WC range: base: 0xe0400000, size: 0x301000
(II) fglrx(0): Splitting WC range: base: 0xe0600000, size: 0x101000
(==) fglrx(0): Write-combining range (0xe0700000,0x1000)
(==) fglrx(0): Write-combining range (0xe0600000,0x101000)
(==) fglrx(0): Write-combining range (0xe0400000,0x301000)
(==) fglrx(0): Write-combining range (0xe0000000,0x701000)
(II) fglrx(0): FBMM initialized for area (0,0)-(1280,1434)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1280,1024) (front color buffer - assumption)
(==) fglrx(0): Backing store disabled
(==) fglrx(0): Silken mouse enabled
(**) fglrx(0): DPMS enabled
(WW) fglrx(0): Option "VendorName" is not used
(WW) fglrx(0): Option "ModelName" is not used
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
(II) fglrx(0): Acceleration enabled
(II) fglrx(0): X context handle = 0x1
(II) fglrx(0): [DRI] installation complete
(II) fglrx(0): Direct rendering enabled
(==) fglrx(0): Using hardware cursor
(II) fglrx(0): Largest offscreen area available: 1280 x 410
(**) fglrx(0): Video overlay enabled on CRTC1
(II) fglrx(0): Interrupt handler installed at IRQ 177.
(II) fglrx(0): Exposed events to the /proc interface
(EE) AIGLX error: dlsym for __driCreateNewScreen_20050727 failed (/usr/lib/dri/fglrx_dri.so: undefined symbol: __driCreateNewScreen_20050727)

```

```

$ grep WW /var/log/Xorg.0.log
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(WW) `fonts.dir' not found (or not valid) in "/usr/share/X11/fonts/misc".
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
(WW) The directory "/usr/share/X11/fonts/100dpi/" does not exist.
(WW) The directory "/usr/share/X11/fonts/75dpi/" does not exist.
(WW) The directory "/usr/share/X11/fonts/Type1" does not exist.
(WW) The directory "/usr/share/X11/fonts/100dpi" does not exist.
(WW) The directory "/usr/share/X11/fonts/75dpi" does not exist.
(WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType".
(WW) fglrx: No matching Device section for instance (BusID PCI:1:0:1) found
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(WW) fglrx(0): Option "VendorName" is not used
(WW) fglrx(0): Option "ModelName" is not used

```

---

### Post by ethon on 2006-11-03
Alrighty reinstalled restricted modules as you requested.

Now I can modprobe fglrx.

lsmod | grep radeon produces no output.

lsmod | grep fglrx produces:
```

fglrx                 406988  8 
agpgart                34888  2 fglrx,ati_agp

```

```

fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)

```

---

### Post by NTolerance on 2006-11-03
This how-to works well for me with the exception of GTK themes.  The default Ubuntu themes work fine, but any custom themes don't display correctly and look like the ugly GTK1 style.

---

### Post by Anonii on 2006-11-03
Dammit I'm always getting Mesa on the fglrxinfo and never ATI. Check this:

```

$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)

```

Why? Also, my xorg.conf:

```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	FontPath	"/usr/share/fonts/X11/misc"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

---

### Post by hed on 2006-11-03
I get the DRI working fine :D but I've other problem :confused: 
I select the Xgl session in the login screen and when it is entering, there is an error (session during less than 10 seconds...), I see the xsession-errors and I see the problem: screen not found :S
I made a copy/paste of your starxgl script but it doesn't works. When I start a Gnome session all works fine... any idea?

---

### Post by katgfan on 2006-11-03
I tried all suggested but I also cannot get past mesa. Any suggestions?

```

$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)

$ sudo modprobe fglrx
$ lsmod | grep fglrx
fglrx                 405164  8 
agpgart                33456  2 fglrx,ati_agp
$ lsmod | grep radeon

```

---

### Post by Paerez on 2006-11-03
Anonil: You dont have the Option Composite Disable in your xorg.conf.

Ethon: Make sure to log out and press control-alt-backspace, or reboot, before you try doing fglrxinfo to check to see if you have ati.

katgfan: Same as Ethon. Also, post the results of "grep EE /var/log/Xorg.0.log".

---

### Post by 51mmz0rz on 2006-11-03
I am also having trouble, running a Radeon Mobility 9200.  What do I need to uninstall in order to start from scratch? (xorg-driver-fglrx?) I've tried the tutorial but I'm afraid previous attempts might be interfering.

Thanks for a tutorial, I hope it works for me eventually...

---

### Post by katgfan on 2006-11-03
Here is the output.

```

$ grep EE /var/log/Xorg.0.log
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER
(EE) AIGLX error: dlopen of /usr/lib/dri/on_igp9x00_we_do_not_support_dri.so failed (/usr/lib/dri/on_igp9x00_we_do_not_support_dri.so: cannot open shared object file: No such file or directory)
(EE) AIGLX: reverting to software rendering
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom

```

---

### Post by ethon on 2006-11-03
Here is my output:

```

(II) Loading extension MIT-SCREEN-SAVER
(EE) AIGLX error: dlopen of /usr/lib/dri/on_igp9x00_we_do_not_support_dri.so failed (/usr/lib/dri/on_igp9x00_we_do_not_support_dri.so: cannot open shared object file: No such file or directory)
(EE) AIGLX: reverting to software rendering
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom

```

---

### Post by 51mmz0rz on 2006-11-04
Well, I totally reinstalled tonight and followed the tutorial. The install didn't generate any errors, but when I boot up, the screen is 'messed up'.  Pretty much random colors.  I can type my username and pass and hear the sounds letting me know the login was successful. What's the next step? ](*,)

EDIT: I've gotten the screen back after running 'dpkg-reconfigure xserver-xorg'. I chose the 'ati' driver at the beginning of this process. However, my output of fglrxinfo is as follows:

```
display: :0.0  screen: 0
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI R200 20060602 AGP 1x TCL
OpenGL version string: 1.2 (1.3 Mesa 6.5.1)

```

Output of 'modprobe fglrx':

```
modprobe fglrx
```

I think I probably messed that up by running dpkg-reconfigure xserver-xorg. 

Output of lsmod | grep fglrx: Nothing

Output of lsmod | grep radeon:
```
radeon                118816  2 
drm                    74644  3 radeon
```

I am going to run dpkg-reconfigure again looking for fglrx now.

EDIT2: Done, and anytime I choose fglrx my screen is always "messed up" on boot.

I tried lowering the resolution, and could see a 'double image'.  Messed up, but i could make out the text.  I ran fglxinfo and it came back MESA...

The only thing I wasn't sure of in the dpkg-reconfigure was the video card BUS ID.

Please help me configure these ATI drivers. They are killing me.

PS - My ultimate goal is really to install beryl, so if there is a way to do that without FGLRX, I'll go for it.

---

### Post by zasf on 2006-11-04
> **Paerez said:**
> 2) I can't get 3d working in any applicaion within beryl, it says that DRI is not found. My mplayer is really slow using Xv, and gl2 doesn't work.

if you do fglrxinfo with beryl running, what do you get?

```
matteo@burnt:~$ fglrxinfo 
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON X700 Generic
OpenGL version string: 2.0.6119 (8.30.3)
```

I see that you're using a older version of fglrx, you should try the latest one, they're improving the driver even if very slowly

mplayer works fine here using Xv, but that's a very recent fix in fglrx, I reccomend you to upgrade

I can't run 3d apps properly (see screenshot of tremulous), but in the past they didn't run at all, I guess it still depends on fglrx.

Matteo

---

### Post by Paerez on 2006-11-04
51mmz0rz: Check "/etc/modules" and make sure that "radeon" is not listed. Now make sure that you have fglrx in your xorg.conf. Then go to a terminal and do the "lsmod | grep radeon". If radeon shows up, run:
```
$ sudo /etc/init.d/gdm stop
$ sudo rmmod radeon
$ sudo modprobe fglrx
$ sudo /etc/init.d/gdm start

```

For people with:
dlopen of /usr/lib/dri/on_igp9x00_we_do_not_support_dri.so failed

I have no clue what this is... sorry. Ask google.


Zasf: I know I am running an "old" version. This is because I don't want to compile my own module from ati.com, I want to use edgy's repos because it is easier. I can get mplayer to work with Xv, but when I fullscreen it, it is way too slow to watch.

---

### Post by hed on 2006-11-04
I installed the last version of the ATI driver to see if there was the problem but not. I'm still having direct rendering but now I have other error:

```
/etc/gdm/Xsession: Beginning session setup...
_XSERVTransSocketUNIXCreateListener: ...SocketCreateListener() failed
_XSERVTransMakeAllCOTSServerListeners: server already running

Fatal server error:
Cannot establish any listening sockets - Make sure an X server isn't already running

(gnome-session:14744): Gtk-WARNING **: cannot open display: 
```

In response to Paerez I can say that install ATI's driver is very easy. Just download the installer, select unknown X, then automatic install (or something like that) and restart. That's all...

---

### Post by breuerp on 2006-11-04
The guide worked well for me but whenever I start typing text into a window (newsgroups, web-based email, open office) I get random crashes that send me back to the login screen.  Any ideas?
```
fglrxinfo:
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9800 Pro Generic
OpenGL version string: 2.0.6119 (8.30.3)
```

---

### Post by NTolerance on 2006-11-04
> **breuerp said:**
> The guide worked well for me but whenever I start typing text into a window (newsgroups, web-based email, open office) I get random crashes that send me back to the login screen.  Any ideas?
```
fglrxinfo:
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9800 Pro Generic
OpenGL version string: 2.0.6119 (8.30.3)
```

[http://forum.beryl-project.org/topic-1199-solved-shift-backspace-crashes-compiz](http://forum.beryl-project.org/topic-1199-solved-shift-backspace-crashes-compiz)

---

### Post by odelay on 2006-11-05
Hey...I followed the first FGLRX part of your thread (verbatim) and now my computer is running at 100% with absolutely no trace of what's using it.  Top and System Manager show nothing.

I'm almost positive it has something to do with the part where you copy and remove the modules.  I didn't really understand this step and copied everything verbatim...it resulted in no errors.  After restarting I now have this.  I even tried installing the original module again to no avail.  My computer is completely screwed now (and will probably melt itself).  How do I undo the copy/remove step?  I'm guessing there's still this module sitting around in /misc but I don't know how to tackle the problem...thanks.

---

### Post by odelay on 2006-11-05
[COLOR="Red"]**Update**[/COLOR]
Well that was pretty scary.  It consistently showed the problem after about 10 different restarts, so I figured it wasn't going to fix itself anytime soon.

Now I know practically nothing about linux, but making the copy of the fglrx.ko seemed to cause a problem.  And when I reinstalled the new modules it was still there.  So I decided to run
```
sudo rm /lib/modules/`uname -r`/misc/fglrx.ko
``` and then reinstall the modules once more.

After restarting back into Gnome again the problem was still there and my windows were acting funky.  So I booted into Fail Safe Gnome and the CPU problem disappeared.  Next I tried booting into XGL and the problem wasn't there.  Finally I booted into regular Gnome again and it disappeared this time.  Weird.  I'll post back when I understand this more.

[COLOR="Red"]**Update 2**[/COLOR]
Well it looks like I was very wrong.  Restarting into either Gnome or XGL still gives me the error.  It only works when I first log into Fail-Safe Gnome.  That's when I get an error about the gnome-settings-daemon which I have set to automatically run at login.  This daemon is probably whats using all the CPU up and not showing any trace at all.  This seems to be a big problem that several people have...and I still don't know of a solution.  I'm going to keep messing around with my settings until I catch a break.

---

### Post by breuerp on 2006-11-05
> **NTolerance said:**
> [http://forum.beryl-project.org/topic-1199-solved-shift-backspace-crashes-compiz](http://forum.beryl-project.org/topic-1199-solved-shift-backspace-crashes-compiz)

I must be putting that in the wrong place because it outright disables my keyboard once Xgl loads.  Is this supposed to go in /usr/local/bin/startxgl.sh ?

Thanks.

---

### Post by -Chi.0 on 2006-11-05
When I Restart my X session all I have is a blank spot where "XGL" should be do I do some thing worng?

I currently running Edgy Kubuntu I have every thing else installed
Beryl, FGLRX, Emerald, I check Adept & is show "XGL" installed.

What I think happened is I ****** up on the scripting some where ](*,) 
Can any one give more details on the scripting part sorry I'm a bit of a noob to Bash scripting. 

If you can help me out can I get some links to help me learn more about Bash & scripting in Bash? :mrgreen:

---

### Post by kpolice on 2006-11-05
> **zasf said:**
> I see that you're using a older version of fglrx, you should try the latest one, they're improving the driver even if very slowly

He shouldn't update if his card is old:

As of driver version 8.29.6 support for the following products is no longer included:

    * Radeon® 8500/9000/9100/9200/9250
    * Mobility™ Radeon® 9000/9100/9200
    * Radeon® IGP 9000/9100/9200

---

### Post by svetj on 2006-11-05
Hi all.
I followed this good guide, starting from the beryl installation,
because I've already had the fglrx working fine.
I can start Xgl whit its session,
but when I launch beryl-manager
I keep an error, and I loose the bars on my windows

svetj@svetlap:~$ beryl-manager
svetj@svetlap:~$ XGL Present
compiz: Couldn't load plugin 'gconf'

This is the ouput of fglrxinfo:
svetj@svetlap:~$ fglrxinfo 
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY/RADEON 9000 DDR Generic
OpenGL version string: 1.3.1091 (X4.3.0-8.28.8)
Is that right?
Where am I wrong?

Thanks a lot

---

### Post by Paerez on 2006-11-05
Odelay:

Removing the module like that was correct. Now go into your "/etc/X11/xorg.conf" and change the "fglrx" to "ati". Now boot into normal gnome and make sure that beryl-manager is not starting.

A question: how do you know cpu is 100% if no process is running at 90-100% in top or system monitor? Remember, you may have to click View->All Processes in system monitor in order to see what is running. Also try sorting on memory.

---

### Post by odelay on 2006-11-05
Hey.  This is for the people that have the beryl-manager problem causing the cpu to go to 100%.

First, I would start by uninstalling beryl and emerald (I just used synaptic to remove them).  Go into terminal and issue
```
locate beryl
```
Now remove the setting files and extras you see.
```
locate emerald
```
Do the same for emerald

Now once you have everything uninstalled, I would follow this [COLOR="Red"]**[/COLOR]([http://wiki.cchtml.com/index.php/XGL-Ubuntu](http://wiki.cchtml.com/index.php/XGL-Ubuntu)) guide once you have fglrx up and running (to check, issue fglrxinfo).  Before restarting though, you have to make a messy script to fix the CPU problem.  This is taken from [http://forum.beryl-project.org/topic-5682-titlebar-blinks](http://forum.beryl-project.org/topic-5682-titlebar-blinks)

Make the script
```
sudo gedit /usr/local/bin/start-xgl.sh
```

Add this to the script
```
cat /usr/local/bin/start-xgl
#!/bin/sh
beryl-manager &
killall emerald
emerald &
```

Go to Prefs>Sessions>StartUp and add "sh /usr/local/bin/start-xgl.sh"

There's probably a better way to do the script thing (maybe making it an exec) but this worked for me at least.

[COLOR="Red"]**[/COLOR] The only reason I mention the other guide is for consistency with what I did.  I imagine you can just follow this guide, make sure gnome-sessions-daemon is a startup item, and do the script thing.

---

### Post by n3Cre0 on 2006-11-05
Worked for me :D 

Haha I'm going to convince some ppl to get linux with this ;)

Only downside: makes my computer buggy when in xgl :(

But other then that : pwns vista ;)

Big thnx

---

### Post by kpolice on 2006-11-05
> **svetj said:**
> Hi all.
I followed this good guide, starting from the beryl installation,
because I've already had the fglrx working fine.
I can start Xgl whit its session,
but when I launch beryl-manager
I keep an error, and I loose the bars on my windows

svetj@svetlap:~$ beryl-manager
svetj@svetlap:~$ XGL Present
compiz: Couldn't load plugin 'gconf'

This is the ouput of fglrxinfo:
svetj@svetlap:~$ fglrxinfo 
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY/RADEON 9000 DDR Generic
OpenGL version string: 1.3.1091 (X4.3.0-8.28.8)
Is that right?
Where am I wrong?

Thanks a lot

DO you have any compiz package installed? If you have any then remove it first.

---

### Post by odelay on 2006-11-05
I read at the official [Edgy/ATI/Beryl Guide]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Xgl.2FBeryl_.28ATI.29") that having fglrxinfo spit back problems with direct rendering is normal.  I get the exact same output as **svetj**...but I don't have the beryl-manager problem anymore (see my above post).

Right now everything seems to be working.  It feels a little unstable and I'm not entirely convinced my computer won't come crumbling apart after the million and one things I did to get Edgy working.  I guess this is what beta-testing feels like.  The way I see it, we're all just making sure Feisty will be the best yet. ;)

---

### Post by shoyer on 2006-11-06
I just wanted to say thanks. I've struggled to enable Compiz/Beryl like effects before on my card (radeon mobility 9000) and had yet to succeed, but it works now.

---

### Post by svetj on 2006-11-06
> **kpolice said:**
> DO you have any compiz package installed? If you have any then remove it first.

Yes, it was installed (maybe due to some tests)..
Now I can start beryl-manager, but there are still some problems,
as reported by odelay.
e.g. if I move a windows, beryl crashes,
so I had to disable this features,
but in this way, I can't move any window!!!
In the next weekend I'll try to solve this problem

Anyway thanks for your support..

bye ;-)

---

### Post by odelay on 2006-11-06
Did you make the script I posted above?  For many people it fixes this problem too.

---

### Post by -Chi.0 on 2006-11-07
Some thing happed when i rebooted now when I run "*fglrxinfo*"

I get this now
```
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

Error: unable to open display :0
```

Is their a way I can fix this? ](*,)
Or can any one tell me the problem :confused:

---

### Post by nevin on 2006-11-07
Yeah, my fglrxinfo used to work, but now it says

Error:  unable to open display :0


i dont know what happened, but this whole thing is becoming a pain.
and also, now when i boot up, i get a blue screen that says something about how X can't load up, so it falls back to the prior setting or something...
did i do something wrong?

---

### Post by n3Cre0 on 2006-11-08
Any way how I can add "restart" and "shutdown" buttons to my xgl session?

+ This session seems to disable my alt gr keys. Now I can't type the symbols for "at" and for a pipe.

Sorry for these newbquestions

---

### Post by odelay on 2006-11-08
I'd also like to know how to add "restart" and "shutdown" to xgl.

---

### Post by Paerez on 2006-11-08
Me too :D

---

### Post by Rob2687 on 2006-11-08
You have to start GDM on XGL in order to get the Shutdown and Restart to show up.

---

### Post by n3Cre0 on 2006-11-08
Can you please explain it to me more extensively? :confused: 

I did some research on google and found out many ppl use their own scripts to shutdown now.

---

### Post by Technoviking on 2006-11-09
I got Beryl running and the effects work great but, windows do not re-draw unless I move one.

Any one seen this problem?
```

dbasinge@tardis:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1600 Generic
OpenGL version string: 2.0.6119 (8.30.3)
```

My xorg.conf
```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool,using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "i2c"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
	Option	    "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "Color LCD"
	HorizSync    30-111
	VertRefresh  50-160
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. ATI Default Card"
	Driver      "vesa"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. ATI Default Card"
	Monitor    "Color LCD"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1440x900"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1440x900"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1440x900"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1440x900"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1440x900"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1440x900"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "Composite" "0"
EndSection
```

---

### Post by Paerez on 2006-11-09
keep in mind ati drivers >=8.29 no longer support the 9000 mobility family, among others. They may still work, but I am scared to try. I am using the edgy 8.28 drivers. Besides, 8.30 only has bugfixes, no new features. And I think the only feature of 8.29 is removed support (may be an incorrect statement). Give 8.28 a shot.

---

### Post by txhellkat138 on 2006-11-09
Just an fyi to some of you radeon 9200 se or damn near any radeon i've tried so far the aiglx drivers that come with edgy out of the box along with this guide []("http://wiki.ubuntu.beryl-project.org/index.php/Install/Ubuntu/Edgy/Aiglx")
have worked flawlessly on the 3 cards i've tried them on Radeon 9200 se Radeon (200 Pci 256mb 3rd party hardware and Radeon 9500 i used this post and 3 others so far trying before i used the one from the wiki with horrid failure 4 installs and lots of hell later i stumbled acros sthat wiki and it was running in 5 mins .

---

### Post by Technoviking on 2006-11-09
> **Paerez said:**
> keep in mind ati drivers >=8.29 no longer support the 9000 mobility family, among others. They may still work, but I am scared to try. I am using the edgy 8.28 drivers. Besides, 8.30 only has bugfixes, no new features. And I think the only feature of 8.29 is removed support (may be an incorrect statement). Give 8.28 a shot.

That fixed it.

Mike

---

### Post by Rob2687 on 2006-11-09
> **Mike said:**
> I got Beryl running and the effects work great but, windows do not re-draw unless I move one.

Any one seen this problem?


I have the exact same problem since the 8.30.3 drivers on my x1900. I'm gonna go back to 8.29 when I get the chance. Sometimes it takes several restarts of Xgl to get it working right.

---

### Post by n3Cre0 on 2006-11-11
Is this normal?

> W: GPG error: [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 31A5F97FED8A569E

---

### Post by titaniumlou on 2006-11-11
I'm getting some similar behavior where the GTK theme looks like an old non-Ubuntu version, any ideas on how I can change this?

But I did get Beryl working finally  :-)

---

### Post by Paerez on 2006-11-11
n3Cre0: That just means you didnt verify the repository. Its no big deal.

titaniumlou: Click the red diamond in your notification area and click Emerald Theme Manager, then find the ubuntu one and click it. Or choose any other theme. I like the ubuntu one though.

---

### Post by n3Cre0 on 2006-11-12
Thanks Paerez, figured that out as well.

Any idea which key I have to add to my repos in order to make the "error" message go away?

Thanks again

---

### Post by svetj on 2006-11-12
> **odelay said:**
> Did you make the script I posted above?  For many people it fixes this problem too.

Hi, sorry for the delay..
Are you talking about the post #31 or #37?
I tried the last one (beryl-manager &
killall emerald
emerald &)
Without any change..
For sure, I sent the debug report to launchpad.

Has someone solved the problem of moving windows?

bye ;-)

---

### Post by odelay on 2006-11-12
#37
Sorry to hear that didn't work.  You can always keep an eye out on the beryl forums for new solutions...that's where I first found the script solution.

You do have gnome-sessions-daemon set as a startup item, right?

---

### Post by davebed on 2006-11-12
Great post. Thank you.

I've got Beryl running now on my Radeon x1400 (Inspiron e1505) and it looks great. I've got a couple of main issues I could really use help on though:

_Issue #1_
In XGL/Beryl I cannot get my DPMS to work - I want my laptop screen to a)Blank on close b) blank after 10min on AC and c)blank on 2 min on battery. I've seen some posts on a workaround by using ```
DISPLAY=:0 xset dpms X
``` where X = seconds before off, ([http://ubuntuforums.org/showthread.php?t=282229&highlight=dpms](http://ubuntuforums.org/showthread.php?t=282229&highlight=dpms)) but I can't figure out how to implement that into my situation (or if it's the best solution for me...)

Running **xset q** gives:```
DPMS (Energy Star):
  Display is not capable of DPMS

```

_Issue #2_
When loading XGL the Beryl "Select Window Manger" *always* defaults to Compiz (i never got *that* working and thought I had removed it) instead of Beryl. I have to manually change it every time](*,) .

Further, I find that the settings made in **gconf-editor** to power management stuff don't seem to take hold either... Is there any way to get all my power managment things to work with XGL/Beryl?

BTW, **fglrxinfo** gives:
```
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1400 Generic
OpenGL version string: 2.0.6065 (8.29.6)

```
Thanks for any help you can offer. The relevant section of my Xorg.conf is beleow (are there dual entries for Device and Monitor? or is it supposed to be like that?)
```
Section "Monitor"
	Identifier   "Generic Monitor"
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. ATI Default Card"
	Driver      "vesa"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. ATI Default Card"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection


```

---

### Post by Paerez on 2006-11-13
Even though GDM and X run on display 0, we set XGL to run on display 1 because ATI has issues running it on display 0. So keep in mind when you are making changes to settings, your display is 1. Try that.

---

### Post by neaxtech on 2006-11-14
*[COLOR="Cyan"]Even though GDM and X run on display 0, we set XGL to run on display 1 because ATI has issues running it on display 0. So keep in mind when you are making changes to settings, your display is 1. Try that.[/COLOR]*


Sorry for the dumb question. Exactly how would you do this?

---

### Post by VCSkier on 2006-11-15
I currently use the open source "radeon" driver with AIGLX, and performance seems quite acceptable.  What advantages or disadvantages would there be to this "fglrx"/XGL method.

I'm on an IBM Thinkpad T41 with a ATi Radeon Mobility 9000 card.  :)

---

### Post by Paerez on 2006-11-15
neaxtech/davebed: you mentioned the workaround:
```
DISPLAY=:0 xset dpms X
```
So change that to:
```
DISPLAY=:1 xset dpms X
```

VCSkier: I used to use Radeon/XGL, and the jump to FGLRX/XGL was an increase in performance of 200-300%. I have not tried AIGLX/Radeon though.

---

### Post by n3Cre0 on 2006-11-15
> **n3Cre0 said:**
> Thanks Paerez, figured that out as well.

Any idea which key I have to add to my repos in order to make the "error" message go away?

Thanks again

Anyone knows?

Yes I know it does not matter at all but I just don't like msgboxes with a red sign on it ;)

---

### Post by Paerez on 2006-11-15
here is the key:
[http://ubuntu.beryl-project.org/quinn.key.asc](http://ubuntu.beryl-project.org/quinn.key.asc)

---

### Post by ounn on 2006-11-15
Thanks, this work perfectly in my radeon 7200 :-D

---

### Post by xlash on 2006-11-15
Hi, I've been following this thread for some time, and tried to do use the tutorial to set everything. However, some issues seems not to work on my computer and I can't figure out why... I'll post my settings, if anyboby can give me a hand it would be really appreciated.

First my setup is dual screen, one LCL 19" on the left, and one CRT 17" on the right. My LCD is on my ATI Radeon 9800 on the DVI output while the other is on the VGA port. 

My Edgy installation is amd64.

Here is fglrxinfo
```
$ fglrxinfo 
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)

```

Here is my xorg.conf
```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg
#Section "ServerLayout"
#	Identifier	"Default Layout"
#	Screen		"Default Screen"
#	InputDevice	"Generic Keyboard"
#	InputDevice	"Configured Mouse"
#	InputDevice     "stylus" "SendCoreEvents"
#	InputDevice     "cursor" "SendCoreEvents"
#	InputDevice     "eraser" "SendCoreEvents"
#EndSection

Section "ServerLayout"
	Identifier     "Multihead"
	Screen         "Default Screen" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
	Option	    "Xinerama"
EndSection

Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "i2c"
	Load  "bitmap"
	Load  "ddc"
	Load	"dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "ca"
	Option	    "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "Generic Monitor"
	HorizSync    28.0 - 64.0
	VertRefresh  43.0 - 60.0
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "Generic Monitor1"
	HorizSync    28.0 - 64.0
	VertRefresh  43.0 - 60.0
	Option	    "DPMS"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. Radeon R350 NH [Radeon 9800 Pro]"
	Driver      "fglrx"
	Option	    "/etc/X11/xorg.conf" "Multihead"
	Option	    "DesktopSetup" "horizontal"
	Option	    "OverlayOnCRTC2" "0"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. Radeon R350 NH [Radeon 9800 Pro]1"
	Driver      "fglrx"
	BusID       "PCI:1:0:1"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. Radeon R350 NH [Radeon 9800 Pro]"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480" "1x1"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480" "1x1"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480" "1x1"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480" "1x1"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480" "1x1"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480" "1x1"
	EndSubSection
EndSection

Section "Screen"
	Identifier "Default Screen1"
	Device     "ATI Technologies, Inc. Radeon R350 NH [Radeon 9800 Pro]1"
	Monitor    "Generic Monitor1"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480" "1x1"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480" "1x1"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480" "1x1"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480" "1x1"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480" "1x1"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480" "1x1"
	EndSubSection
EndSection

Section "Extensions"
        Option      "Composite" "0"
EndSection

```


Loaded fglrx
```
lsmod | grep fglrx
fglrx                 481012  0 

```

grep EE /var/log/Xorg.0.log
```
grep EE /var/log/Xorg.0.log
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER
(EE) AIGLX: Screen 0 is not DRI capable
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom

```

grep WW /var/log/Xorg.0.log
```
grep WW /var/log/Xorg.0.log
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(WW) The directory "/usr/share/X11/fonts/misc" does not exist.
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
(WW) The directory "/usr/share/X11/fonts/100dpi/" does not exist.
(WW) The directory "/usr/share/X11/fonts/75dpi/" does not exist.
(WW) The directory "/usr/share/X11/fonts/Type1" does not exist.
(WW) The directory "/usr/share/X11/fonts/100dpi" does not exist.
(WW) The directory "/usr/share/X11/fonts/75dpi" does not exist.
(WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType".
(WW) fglrx: No matching Device section for instance (BusID PCI:1:0:1) found
(WW) fglrx(0): Bad V_BIOS checksum
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(WW) fglrx(0): ***********************************
(WW) fglrx(0): * DRI initialization disabled!    *
(WW) fglrx(0): * 2D acceleraton available (MMIO) *
(WW) fglrx(0): * no 3D acceleration available    *
(WW) fglrx(0): ***********************************
(WW) fglrx(0): Option "/etc/X11/xorg.conf" is not used

```

Beryl-manager is installed and upon start up, I get this error msg as well
```
beryl-manager doesn't autostart window-manager/decorator
any more. Please consult: man beryl-manager

Xlib:  extension "XFree86-DRI" missing on display ":0.0".

```

And when choosing BERYL as Select Window Manager I get ...
```
XGL Absent, checking for NVIDIA
Nvidia Absent, assuming AIGLX
beryl: No composite extension
compiz.real: No composite extension

```

Thanks for any help, I'd really like to get XGL running!
](*,)

---

### Post by Paerez on 2006-11-15
xlash:
1) This is for the mobility line of cards, not the 9800.
2) I am pretty sure XGL and compiz doesn't work on dual screens. I couldnt get it to work on my desktop with a radeon 9600 using bigdesktop.

So this thread isn't the place, sorry. I would search for topics better fitting your problem, or creating your own thread.

---

### Post by -Chi.0 on 2006-11-20
Does Beryl & XGL work on KDE w/ this card?

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON XPRESS Series Generic
OpenGL version string: 2.0.6011 (8.28.8)

Im running a noetbook w/ 1 1/2 gb of ram w/ 128 mb of vidcard mem

---

### Post by Average Joe on 2006-11-25
Paerez, thank you very much for this nice Howto. I have an ATI Mobility Radeon 9000 card too, and by following your guide I got Beryl working without any problem. At first I even got the crashes you described when I moved a window, but now I am using your Profile file, and it works fine. Thanks a lot man, it looks very nice. :)

---

### Post by adds2one on 2006-11-26
When I log into a XGL session (created as per all the tutorials) I have some problems even before I start beryl.

The first thing I notice is that when I open any panel app a red border slowly comes up from where I clicked the app and then the app opens. I really dislike this red border and am wondering if there is a way to get rid of it. It has nothing to do with Beryl because I haven't even started Beryl when I first see it.

The next problem, and this one is much more serious, is that if I open any app that I want to enter some text in, be it a terminal or to post on this forum, there is a delay of about 20 seconds from when I type and when the text appears on the screen. I looked in system monitor and found that XGL is hogging almost the entire cpu. This makes my system basically unusable with XGL.

This is my fglrxinfo when in a normal Gnome session:

```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY/RADEON 9000 DDR Generic
OpenGL version string: 1.3.1091 (X4.3.0-8.28.8)

```

and this is my fglrxinfo when in an XGL session:

```
Xlib:  extension "XFree86-DRI" missing on display "localhost:1.0".
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY/RADEON 9000 DDR Generic
OpenGL version string: 1.3.1091 (X4.3.0-8.28.8)

```

Any hints to help get XGL working better so that I can enjoy Beryl?

I have tried to get Beryl working with AIGLX but when I use the radeon or ati drivers I don't have direct rendering....:-?

---

### Post by Paerez on 2006-11-26
adds2one: I only have an answer for your less serious problem :(

open Applications->System Tools->Configuration editor. Click Edit->Find and type in "enable_animations" and check the "Search also in key names" box. It will give you a bunch of results. Its one of those. I think it is the global panel one. If you disable it then you wont get that rectangle any more. I turned it off and it really sped up launching apps from the bar :D

---

### Post by BOBSONATOR on 2006-12-07
> **ethon said:**
> Thanks for writing this guide, unfortunately I cannot get past the first half of installing the fglrx drivers.

fglrxinfo gives me:

```

display: :0.0  screen: 0
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI R200 20060602 AGP 4x NO-TCL
OpenGL version string: 1.2 (1.3 Mesa 6.5.1)


```

Any help is appreciated :)


i get the same thing, and i have tried almost everything!

I had beryl working fine in my previous install, i don't know what happened here...

---

### Post by misha680 on 2006-12-07
Great guide. If you guys want to get rid of all Xgl crashes (including being able to run OpenGL apps and having no crashes of any kind with wobbly windows or anything else without tweaking with Beryl settings) on Mobility Radeon 9000 I made a howto with a patched version of Xgl and one change in the Xgl command line:

[http://www.ubuntuforums.org/showthread.php?t=276498&highlight=radeon+9000](http://www.ubuntuforums.org/showthread.php?t=276498&highlight=radeon+9000)

Hope this helps.

Misha

EDIT: My bad, it's already linked. I'm just still amazed that the OpenGL thing is solved, when I had assumed for many months that I would never be able to have OpenGL apps running with Xgl on Radeon 9000.

p.s. adds2one: from what I gather from your post you are having these problems when you start Xgl but not Beryl. The slowness is a known xgl bug on fglrx, and once you start Beryl it will be a lot smoother (except window resizing).

bobsonator: I had _a lot_ of problems with fglrx + Edgy, although this was still in the Betas. I would try doing something like the following. Reboot, and in GRUB select recovery mode. When you get to the command-line, type:
```
modprobe fglrx
```
To load the fglrx driver. If it complains, post the messages here. If it doesn't, just type:
```
exit
```
It will finish booting and start the X server. Hopefully, this way the X server will not give you the "mesa error" so to speak. If this works, I can advise you of a permanent solution. If not, then it is probably a different problem.

---

### Post by BOBSONATOR on 2006-12-07
thanks, it tells me nothing when i modprobe fglrx.

and when i exit, it tells me that no processes are running.

---

### Post by misha680 on 2006-12-07
Good, that is what is supposed to happen. Now the question is when X starts afterwards and you type fglrxinfo what do you see?

Misha

> **BOBSONATOR said:**
> thanks, it tells me nothing when i modprobe fglrx.

and when i exit, it tells me that no processes are running.

---

### Post by BOBSONATOR on 2006-12-07
same thing again...

Misha, can you post your X11.conf?

---

### Post by misha680 on 2006-12-07
Sure, here's my X11.conf

```


# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen         "Default Screen" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
	InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"

	# RGB path
	#RGBPath      "/etc/X11/rgb"
EndSection

Section "Module"
	Load  "i2c"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "inspiron"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "HorizScrollDelta" "0"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "Generic Monitor"
	Option	    "DPMS"
# Dell Inspiron 600m Display Inches    Pixels   Dots per inch
# Height 8.4                           1050     125
# Width 11.3                           1400     125
# To calculate: pixels * 25 / dpi
        DisplaySize   280.0  210.0
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[1]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. Radeon R250 Lf [Radeon Mobility 9000 M9]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	Option      "UseInternalAGPGART" "no"
        Option      "KernelModuleParm" "locked-userpages=0"
# if lockups continue, try uncommenting the next line???
#       Option      "mtrr" "false"
# For XGl/Compiz
	Option	    "DesktopSetup" "clone"
	Option	    "Mode2" "1400x1050,1280x1024,1024x768"
# ForceMonitors consumes extra battery power
#       Option      "ForceMonitors" "lvds,crt1"
# Enable for S-Video Out
#       Option      "ForceMonitors" "lvds,tv"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[1]"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
	Screen      1
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. Radeon R250 Lf [Radeon Mobility 9000 M9]"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1400x1050"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1400x1050"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1400x1050"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1400x1050"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1400x1050"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1400x1050"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[1]"
	Device     "aticonfig-Device[1]"
	Monitor    "aticonfig-Monitor[1]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option "Composite" "Disable"
EndSection

```

Misha

> **BOBSONATOR said:**
> same thing again...

Misha, can you post your X11.conf?

---

### Post by BOBSONATOR on 2006-12-07
EDIT: NVM! Got it all to work with this code.

sudo gedit /etc/modules

then add fglrx!

SO SIMPLE!

You are welcome other people in this thread that are scratching their heads!

---

### Post by misha680 on 2006-12-08
That is great. Its weird because that is the same effect that the modprobe fglrx was supposed to have only temporarily.

Misha

> **BOBSONATOR said:**
> EDIT: NVM! Got it all to work with this code.

sudo gedit /etc/modules

then add fglrx!

SO SIMPLE!

You are welcome other people in this thread that are scratching their heads!

---

### Post by dpesce on 2006-12-09
First few days using Ubuntu, but not new to Linux.  I have a Dell Smartstep 250N laptop with the 32mb ATI Mobility M6 in it.  Using Ubuntu 6.10 fresh install.

I can follow the steps up until the ```
sudo aptitude install linux-restricted-modules-`uname -r`
```

At that point I receive this message:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
```


Which appears to complete successfully but not do anything.  So I continue to the next step of copying the fglrx.ko file to a safe location.  I get this error: 
```
cp: cannot create regular file `/lib/modules/2.6.17-10-generic/misc/fglrx.ko': No such file or directory
```

fglrxinfo displays:

```
display: :0.0  screen: 0
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI Radeon 20060327 AGP 1x NO-TCL
OpenGL version string: 1.2 (1.3 Mesa 6.5.1)
```


and here is my xorg.conf:
```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	FontPath	"/usr/share/fonts/X11/misc"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon Mobility M6 LY [Radeon Mobility 9000]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon Mobility M6 LY [Radeon Mobility 9000]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1400x1050"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection
```


Any help would be greatly appreciated as to what to do/try next.

Thank you!
Dave

---

### Post by jcrnan on 2006-12-11
Okey, so I managed to get an ati info string, but I can't get beryl starting properly.

andre@laptop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY/RADEON 9000 DDR Generic
OpenGL version string: 1.3.1091 (X4.3.0-8.28.8)

andre@laptop:~$ beryl-manager
andre@laptop:~$ XGL Absent, checking for NVIDIA
Nvidia Absent, assuming AIGLX
beryl: No composite extension

---

### Post by jcrnan on 2006-12-11
nevermind. I forgot running it in the xgl session.

---

### Post by misha680 on 2006-12-11
I would try testing beryl by using beryl-xgl instead of beryl-manager. I remember I had some problems starting beryl-manager from Terminal. Also you can try adding beryl-manager to your startup programs in Gnome sessions (I know this all shouldn't make a difference but in my experience it does).

Misha

> **jcrnan said:**
> Okey, so I managed to get an ati info string, but I can't get beryl starting properly.

andre@laptop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY/RADEON 9000 DDR Generic
OpenGL version string: 1.3.1091 (X4.3.0-8.28.8)

andre@laptop:~$ beryl-manager
andre@laptop:~$ XGL Absent, checking for NVIDIA
Nvidia Absent, assuming AIGLX
beryl: No composite extension

---

### Post by BOBSONATOR on 2006-12-12
Thanks misha!

Anywho, i cant enable wobbly windows, and when i do it crashes, does anyone have a fix for that? Cause i used to run beryl fine with wobbly windows before using someone elses HOWTO when edgy first came out.

---

### Post by misha680 on 2006-12-13
If you use the patched deb from my howto [http://ubuntuforums.org/showthread.php?t=276498](http://ubuntuforums.org/showthread.php?t=276498) it will not crash no matter what your beryl settings. Then you can optimize the wobbly windows for best speed/quality.

Misha

> **BOBSONATOR said:**
> Thanks misha!

Anywho, i cant enable wobbly windows, and when i do it crashes, does anyone have a fix for that? Cause i used to run beryl fine with wobbly windows before using someone elses HOWTO when edgy first came out.

---

### Post by eustace on 2006-12-18
Hi there,

I wonder how you people deal with the suspend/hibernation after you configure DRI on Radeon Mobility 9000? From my experience and from what I could google out, the combination of this card + fglrx + DRI + suspend never works. 

> **Paerez said:**
> **FGLRX Suspend and Hibernate**
Edit "/etc/default/acpi-support" and change the following lines:
```
MODULES_WHITELIST="fglrx"
SAVE_VBE_STATE=false
POST_VIDEO=false
DOUBLE_CONSOLE_SWITCH=true
```


I did that, and I also tried "noapic" parameter to the kernel, all to no avail. The laptop goes into sleep, but on return it always freezes with black screen. I'm running Edgy, fglrx version is 8.28.8. 

What tricks are you using beside these to make suspend work?

Thanks.

PS. Oh yeah, without DRI suspend works like a charm.

---

### Post by misha680 on 2006-12-18
I use:

```

SAVE_VBE_STATE=false
POST_VIDEO=false
USE_DPMS=false

```

Works well for me.

Misha

p.s. Also I think it matters if you suspend by closing the lid or not, specifically if you are using fglrx powermode. If you are, I would recommend _not_ suspending by closing the lid because I had problems with that.

> **eustace said:**
> Hi there,

I wonder how you people deal with the suspend/hibernation after you configure DRI on Radeon Mobility 9000? From my experience and from what I could google out, the combination of this card + fglrx + DRI + suspend never works. 



I did that, and I also tried "noapic" parameter to the kernel, all to no avail. The laptop goes into sleep, but on return it always freezes with black screen. I'm running Edgy, fglrx version is 8.28.8. 

What tricks are you using beside these to make suspend work?

Thanks.

PS. Oh yeah, without DRI suspend works like a charm.

---

### Post by Mateo on 2006-12-28
Hey guys.  This guide worked great.... except that now when I go to System -> Quit, there isn't a "restart"  or "shut down".  Where did they go?

---

### Post by AgenT on 2006-12-28
It should be known that Beryl works great using the freedom software AIGLX xorg extension with ATI Mobility. AIGLX is much easier to use because it already comes with the stock xorg. Using AIGLX, all the kernel compiling, xorg.conf editing, etc. can be avoided.

And there is one other advantage: by using AIGLX, you are using and supporting freedom software. Those other drivers are proprietary and non-freedom software.

Also, for some reason the AIGLX drivers give better performance on the ATI Mobility. AIGLX also works with DRI and other xorg extensions.

To use Beryl with AIGLX just do this (assuming you did not edit your xorg.conf):[LIST=1]
[*] add the bery repository by adding the following line to /etc/apt/sources.list: ```
deb http://ubuntu.beryl-project.org edgy main
``` (notice: the author of this article is wrong, it should be "edgy main" and not "edgy main-edgy")
[*]In the terminal, type: ```
sudo apt-get install beryl beryl-manager emerald emerald-themes
```[/LIST]Done! Now just restart X and start beryl-manager. If Beryl crashes or does not run, the chances are your xorg.conf is not configured correctly. This is mostly due to you changing your default xorg.conf either by hand or because you installed no-freedom (proprietary) drivers.

---

### Post by Paerez on 2006-12-28
cool! I was wondering when AIGLX was gonna work with the ati drivers. What version fglrx do you need for aiglx to work? Or the open source radeon ones?

---

### Post by -Chi.0 on 2007-01-14
Does any one Know how to use AIGLX on ATI cards w/ KDE?

---

### Post by Mr_Congeniality on 2007-01-26
```
Couldn't find any package whose name or description matched "linux-restricted-modules2.6.17-10-generic"
```
I tried reinstalling the modules so I could do one of the steps but it says it doesn't exist.

---

### Post by Mr_Congeniality on 2007-01-26
Oh and the XGL session boots Beryl and everything, but default GNOME session just goes to a gray screen when it tries to start XGL.  It disappears when I hit Shift + Backspace (The magic key to killing XGL.)

This is what comes up when I try to start XGL.

randy@randy3-linux:~$ startxgl
Could not init font path element /usr/share/fonts/X11/TTF/, removing from list!
Could not init font path element /usr/share/fonts/X11/OTF, removing from list!
Could not init font path element /usr/share/fonts/X11/CID/, removing from list!
gnome-session: you're already running a session manager
randy@randy3-linux:~$ FreeFontPath: FPE "/usr/share/fonts/X11/misc/" refcount is 2, should be 1; fixing.

---

### Post by total wormage on 2007-01-31
wonderful guide! thanks a bundle :D

there is one thing (i don't know if it is mentioned earlier, i did scan this thread but could have overlooked a post like this one)

i had to create the misc/ folder in /lib/modules/ by hand before the:
```
$ sudo cp /lib/modules/`uname -r`/volatile/fglrx.ko /lib/modules/`uname -r`/misc/fglrx.ko
```
would work :]

:KS :KS

---

### Post by Pedric on 2007-02-01
Today's update to 0.1.9999 from the ubuntu repo ([http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/)) segfaults  on start.

see:
[http://bugs.beryl-project.org/ticket/1092](http://bugs.beryl-project.org/ticket/1092)
[http://forum.beryl-project.org/viewtopic.php?f=36&t=2977](http://forum.beryl-project.org/viewtopic.php?f=36&t=2977)

---

### Post by linex on 2007-02-01
i installed it but i get a message telling me that i logged out within 10 seconds of logging in and this might be the sessions fault. i also get "can't open /usr/bin/startxgl"

what might be happening?

---

### Post by sn0m on 2007-02-02
hi
i am extremly newbe and got stuck here

sn0m@sn0m-laptop:~$ sudo aptitude update
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Translation-en_US             
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg [191B]               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Translation-en_US       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Translation-en_US         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Translation-en_US       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_US             
Get:3 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy Release.gpg [191B]                      
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/main Translation-en_US                    
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security Release.gpg [191B]                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/main Translation-en_US              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/restricted Translation-en_US        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_US       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/universe Translation-en_US          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/multiverse Translation-en_US        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release                            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-en_US         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Translation-en_US       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release                            
Get:5 [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release.gpg [191B]         
Ign [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Translation-en_US       
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/restricted Translation-en_US              
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/universe Translation-en_US                
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/multiverse Translation-en_US              
Get:6 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates Release.gpg [191B]              
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates/main Translation-en_US            
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates/restricted Translation-en_US      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security Release                             
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates/universe Translation-en_US        
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates/multiverse Translation-en_US      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy Release                                   
Get:7 [http://wine.lowvoice.nl](http://wine.lowvoice.nl) edgy Release.gpg [191B]                           
Ign [http://wine.lowvoice.nl](http://wine.lowvoice.nl) edgy/main Translation-en_US                         
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Packages                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Packages                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Packages                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Packages                
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates Release                           
Hit [http://wine.lowvoice.nl](http://wine.lowvoice.nl) edgy Release                                        
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Packages                
Get:8 [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release.gpg [189B]                       
Ign [http://www.getautomatix.com](http://www.getautomatix.com) edgy/main Translation-en_US                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/main Packages                       
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/main Packages                             
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/restricted Packages                       
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/universe Packages                         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/multiverse Packages                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/restricted Packages                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/universe Packages                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/multiverse Packages                 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/main Sources                              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/restricted Sources                        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/universe Sources                          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/multiverse Sources                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Sources                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Sources                 
Ign [http://wine.lowvoice.nl](http://wine.lowvoice.nl) edgy/main Packages                                  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates/main Packages                     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates/restricted Packages    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates/universe Packages      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates/multiverse Packages    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates/main Sources           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates/restricted Sources     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates/universe Sources       
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy-updates/multiverse Sources     
Hit [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release                         
Hit [http://wine.lowvoice.nl](http://wine.lowvoice.nl) edgy/main Packages                       
Hit [http://www.getautomatix.com](http://www.getautomatix.com) edgy/main Packages                   
Fetched 8B in 0s (10B/s)
Reading package lists... Done
sn0m@sn0m-laptop:~$ sudo aptitude dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
sn0m@sn0m-laptop:~$ sudo aptitude install xorg-driver-fglrx
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
sn0m@sn0m-laptop:~$ $ sudo aptitude install xorg-driver-fglrx
bash: $: command not found
sn0m@sn0m-laptop:~$  sudo aptitude install xorg-driver-fglrx
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
sn0m@sn0m-laptop:~$ sudo aptitude install linux-restricted-madules-'uname-r'
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
Couldn't find any package whose name or description matched "linux-restricted-madules-uname-r"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
sn0m@sn0m-laptop:~$ $ sudo aptitude install linux-restricted-modules-`uname -r`
bash: $: command not found
sn0m@sn0m-laptop:~$  sudo aptitude install linux-restricted-modules-`uname -r`
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
sn0m@sn0m-laptop:~$ sudo cp/lib/modules/`uname-r`/volatile/fglrx.ko /lib/modules/`uname-r`/misc/fglrx.ko
bash: uname-r: command not found
bash: uname-r: command not found
sudo: cp/lib/modules//volatile/fglrx.ko: command not found
sn0m@sn0m-laptop:~$ sudo cp /lib/modules/`uname -r`/volatile/fglrx.ko /lib/modules/`uname -r`/misc/fglrx.ko
sn0m@sn0m-laptop:~$ sudo aptitude remove linux-restricted-modules-`uname-r`
bash: uname-r: command not found
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
Couldn't find package "linux-restricted-modules".  However, the following
packages contain "linux-restricted-modules" in their name:
  linux-restricted-modules-686 
  linux-restricted-modules-2.6.17-10-generic 
  linux-restricted-modules-2.6.17-10-386 
  linux-restricted-modules-common 
  linux-restricted-modules-generic 
  linux-restricted-modules-k7 linux-restricted-modules-386 
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
sn0m@sn0m-laptop:~$ sudo cp /lib/modules/`uname -r`/volatile/fglrx.ko /lib/modules/`uname -r`/misc/fglrx.ko
sn0m@sn0m-laptop:~$ sudo aptitude remove linux-restricted-modules-`uname -r`
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
The following packages are BROKEN:
  linux-restricted-modules-generic 
The following packages will be REMOVED:
  linux-restricted-modules-2.6.17-10-generic 
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 20.9MB will be freed.
The following packages have unmet dependencies:
  linux-restricted-modules-generic: Depends: linux-restricted-modules-2.6.17-10-generic but it is not installable
Resolving dependencies...
The following actions will resolve these dependencies:

Downgrade the following packages:
linux-restricted-modules-2.6.17-10-generic [2.6.17.7-10.1
(edgy-security, edgy-security, now) -> 2.6.17.5-11 (edgy)]

Score is -39

Accept this solution? [Y/n/q/?] y
The following packages will be DOWNGRADED:
  linux-restricted-modules-2.6.17-10-generic 
0 packages upgraded, 0 newly installed, 1 downgraded, 0 to remove and 0 not upgraded.
Need to get 7682kB of archives. After unpacking 0B will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Get:1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/restricted linux-restricted-modules-2.6.17-10-generic 2.6.17.5-11 [7682kB]
Fetched 7682kB in 30s (253kB/s)                                   
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
DESTROY created new reference to dead object ' Qt::VBoxLayout', <> line 1 during global destruction.
dpkg - warning: downgrading linux-restricted-modules-2.6.17-10-generic from 2.6.17.7-10.1 to 2.6.17.5-11.
(Reading database ... 134817 files and directories currently installed.)
Preparing to replace linux-restricted-modules-2.6.17-10-generic 2.6.17.7-10.1 (using .../linux-restricted-modules-2.6.17-10-generic_2.6.17.5-11_i386.deb) ...
Unpacking replacement linux-restricted-modules-2.6.17-10-generic ...
Setting up linux-restricted-modules-2.6.17-10-generic (2.6.17.5-11) ...

sn0m@sn0m-laptop:~$ sudo depmond -a
sudo: depmond: command not found
sn0m@sn0m-laptop:~$ sudo depmod -a
sn0m@sn0m-laptop:~$ sudo aticonfig --initial
Uninitialised file found, configuring.
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.original-0
sn0m@sn0m-laptop:~$ sudi aticonfig --overlay-type=Xv
bash: sudi: command not found
sn0m@sn0m-laptop:~$ sudo aticonfig --overlay-type=Xv
Warning: Option 'VideoOverlay' doesn't affect running session.
Warning: Option 'OpenGLOverlay' doesn't affect running session.
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.fglrx-0
sn0m@sn0m-laptop:~$ sudo gedit /etc/X11/xorg.conf
sudo: gedit: command not found
sn0m@sn0m-laptop:~$ sudo gedit /etx/X11/xorg.con
sudo: gedit: command not found
sn0m@sn0m-laptop:~$ "$ sudo gedit /etx/X11/xorg.conf"
bash: $ sudo gedit /etx/X11/xorg.conf: No such file or directory
sn0m@sn0m-laptop:~$ sudo gedit /etx/X11/xorg.conf
sudo: gedit: command not found
sn0m@sn0m-laptop:~$ cd /etx/X11
bash: cd: /etx/X11: No such file or directory
sn0m@sn0m-laptop:~$ find xorg.com
find: xorg.com: No such file or directory
sn0m@sn0m-laptop:~$ find xorg.conf
find: xorg.conf: No such file or directory
sn0m@sn0m-laptop:~$ 



I need some help

---

### Post by parradux on 2007-02-02
Imma need some basic help here. 

I cant even get the packages. I have my direct rendering work from before, so I dont need to screw around with the drivers. 

When I try to do apt-get install beryl, etc I get this: 

sudo aptitude install beryl emerald-themes xserver-xgl
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
Couldn't find any package whose name or description matched "beryl"
Couldn't find any package whose name or description matched "emerald-themes"
The following NEW packages will be automatically installed:
  libglitz-glx1 libglitz1 
The following NEW packages will be installed:
  libglitz-glx1 libglitz1 xserver-xgl 
0 packages upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 1691kB of archives. After unpacking 4567kB will be used.
Do you want to continue? [Y/n/?] n
Abort.
boris@boris-laptop:~$ sudo aptitude install beryl emerald-themes xserver-xgl
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
Couldn't find any package whose name or description matched "beryl"
Couldn't find any package whose name or description matched "emerald-themes"
The following NEW packages will be automatically installed:
  libglitz-glx1 libglitz1 
The following NEW packages will be installed:
  libglitz-glx1 libglitz1 xserver-xgl 
0 packages upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 1691kB of archives. After unpacking 4567kB will be used.
Do you want to continue? [Y/n/?] n
Abort.


My sources file is this: 

```
 



deb http://us.archive.ubuntu.com/ubuntu/ edgy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ edgy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu edgy-security main restricted
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted
deb http://security.ubuntu.com/ubuntu edgy-security universe
deb-src http://security.ubuntu.com/ubuntu edgy-security universe


## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

deb http://us.archive.ubuntu.com/ubuntu/ edgy main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy main restricted universe multiverse

deb http://us.archive.ubuntu.com/ubuntu/ edgy-proposed main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://packages.freecontrib.org/plf edgy-plf free non-free
deb-src http://packages.freecontrib.org/plf edgy-plf free non-free
                                                                                                                                         
## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera, DesktopSecure and more to come.) 
deb http://archive.canonical.com/ubuntu edgy-commercial main

## Listen
deb http://theli.free.fr/packages/ edgy listen


## Automatix repo
deb http://www.getautomatix.com/apt edgy main
deb http://www.getautomatix.com/apt edgy main

#AUTOMATIX REPOS START

deb http://wine.lowvoice.nl/apt dapper main

deb http://archive.canonical.com/ubuntu dapper-commercial main

deb http://us.archive.ubuntu.com/ubuntu/ edgy-security main restricted universe multiverse
#AUTOMATIX REPOS END

deb http://ubuntu.beryl-project.org edgy main-edgy
deb http://ubuntu.beryl-project.org edgy main

``` 

As can be seen i've added in the repo's + used to key. 

Whats the problem here?

---

### Post by Paerez on 2007-02-02
Sn0m: instead of "gedit" use "nano -w" so:
$ sudo nano -w /etc/X11/xorg.conf

You just don't have Gedit. I am guessing you are on kubuntu?


parradux: Run "sudo aptitude update" first to load the beryl repositories.

---

### Post by Frostmourne on 2007-02-02
> **Mateo said:**
> Hey guys.  This guide worked great.... except that now when I go to System -> Quit, there isn't a "restart"  or "shut down".  Where did they go?

Add this to your XGL start script:

```
cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
xauth -i add :1 . "$cookie"
```

---

### Post by parradux on 2007-02-02
nope that doesnt work it still wont download.

---

### Post by Patrick-Ruff on 2007-02-02
I don't see anything new here. but thanks for your effort ;).

---

### Post by finferflu on 2007-02-03
I followed the howto, and got stuck at the reboot. X won't start and when I check the log, at the end of it, I get the message:

```

No screens found

```

And have to revert to the previous xorg configuration to have X working again.

Any ideas?

Thanks a lot for your help!

---

### Post by Paerez on 2007-02-03
finferflu, can you post the /etc/X11/xorg.conf that was broken?

---

### Post by finferflu on 2007-02-03
> **Paerez said:**
> finferflu, can you post the /etc/X11/xorg.conf that was broken?

Sure, it's attached.

Moreover I tried to use the advanced mode (i.e. no reboot), and I got the following output when I run the command modprobe fglrx:

```
FATAL: Error running install command for fglrx
```

Thanks!

---

### Post by Paerez on 2007-02-03
did you then try to reboot?

p.s. your xorg.conf looked fine.

---

### Post by finferflu on 2007-02-04
> **Paerez said:**
> did you then try to reboot?

p.s. your xorg.conf looked fine.

Yes, I tried both methods.

---

### Post by 290 on 2007-02-04
Im having the same problem. Somthing i noticed while doing the dist-update is that the package "linux-restricted-modules-2.6.17-10-generic" is installed for you. And uninstalling it just downgrades it to a previous version. I also noticed that even after reboot the file "fglrx.ko" remains in the volatile folder.

Edit:
Ignoring the install and uninstall of linux-restricted-module i still come up with a No Screens Found error

out of the garbled text on the boarders of the screen i get the error

(--) Assigning device section with no bus ID to primary device
(EE) No devices detected

Dell Latitude C610
Radeon Mobility M6 LY (9000)

---

### Post by SexyStud on 2007-02-05
Hi,

I followed your howto but faced some problems. Perhaps you can give me a hand on this?

1st, when doing:
```
$ sudo cp /lib/modules/`uname -r`/volatile/fglrx.ko /lib/modules/`uname -r`/misc/fglrx.ko
```
I fail, because such directory doesn't exist (the destination one). Should I copy it someplace else?
Note: the restricted modules were already installed before I started the howto. This was on a fresh and updated version of Edgy.

The current situation is, fglrx is being used and X appears to be working OK. However, if I disable Compositing on xorg.conf, I can't log in anymore. The computer stops right after I put my login/password. (I can move the mouse and I can see the background color loaded, but nothing else happens, not even the usplash)
Plus, I get this output from fglrxinfo:```

Xlib: extension "XFree86-DRI" missing on display ":0.0".
display: :0.0 screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)
```

I'm using a laptop with ATi Mobility Radeon 9700, by the way.

---

### Post by finferflu on 2007-02-05
I created that folder, actually, but I don't know if that's the right thing to do...

---

### Post by mmendez on 2007-02-05
I am having this bit of a problem. I originally followed the instructions from the link you gave then found this howto when that didnt work.

everything seemed to be going ok until when I started the xgl session it reverted back to gnome as it has done before and when i type ```
beryl
``` i get this output 
~$ beryl
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : XGL

Checking Display :1.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
Checking for non power of two texture support   : failed

Support for non power of two textures missing

I also noticed that when i type ```
fglrxinfo
``` while in the xgl session I get the following

$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON X700 Generic
OpenGL version string: 2.0.6011 (8.28.8)


any ideas?

---

### Post by Paerez on 2007-02-07
Hey everyone, I updated the guide to include the SVN packages, which are now working on our cards. I also included a new beryl settings profile that is tweaked towards performance (since the 9000 is pretty crappy) and also doesn't have any features that crash our cards (like wobbly windows and skydome).

Have fun.


Another note: those of you having trouble getting fglrx to work, maybe look around at other threads, since this guide only has fglrx at the beginning to get most people started, and is mostly about getting xgl and beryl to work.

---

### Post by finferflu on 2007-02-07
> **Paerez said:**
> 
Another note: those of you having trouble getting fglrx to work, maybe look around at other threads, since this guide only has fglrx at the beginning to get most people started, and is mostly about getting xgl and beryl to work.

Actually that's the very problem of those with an ATI Radeon 9000, to get fglrx working. I've been looking around for months now, and I was hoping this post would bring up a solution for me... it's very weird it works with your card, but not with mine...

---

### Post by Paerez on 2007-02-08
try reinstalling the libGL file by running this:
sudo aptitude reinstall libgl1-mesa-dri

some guides make you mess with that file, maybe it messed you up.

---

### Post by finferflu on 2007-02-08
> **Paerez said:**
> try reinstalling the libGL file by running this:
sudo aptitude reinstall libgl1-mesa-dri

some guides make you mess with that file, maybe it messed you up.

No luck, thanks for the hint anyway..

---

### Post by ASUndevil on 2007-02-09
So I have Xgl working, however my woobly windows cause my desktop to crash.  Anyone else expeirience this issue?


# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
	InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "i2c"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
	Option	    "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "HorizScrollDelta" "0"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "Generic Monitor"
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. Radeon R250 Lf [Radeon Mobility 9000 M9]"
	Driver      "fglrx"
	Option "OpenGLOverlay" "off" #this isn't necessary for me
	Option "UseInternalAGPGART" "no"
	Option "KernelModuleParm" "agplock=0"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
        Option "OpenGLOverlay" "off" #this isn't necessary for me
        Option "UseInternalAGPGART" "no"
        Option "KernelModuleParm" "agplock=0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. Radeon R250 Lf [Radeon Mobility 9000 M9]"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1400x1050"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1400x1050"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1400x1050"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1400x1050"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1400x1050"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1400x1050"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
        Option  "Composite" "Disable"
EndSection

#Section "ServerFlags"
#        Option  "AIGLX" "off"
#EndSection

---

### Post by parradux on 2007-02-09
Ok i've managed to install beryl but i'am still having problems. 

When I boot into XGL I cant do anything. Both of the panels are locked in place, I cant access anything on the screen etc. I can move my mouse and everything, but nothing will open. Basically a freeze. 

What do I do about this?

---

### Post by misha680 on 2007-02-09
I have a patched version of Xgl that does not crash like this (this is an fglrx bug):

[http://www.ubuntuforums.org/showthread.php?t=276498](http://www.ubuntuforums.org/showthread.php?t=276498)

misha

> **ASUndevil said:**
> So I have Xgl working, however my woobly windows cause my desktop to crash.  Anyone else expeirience this issue?


# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
	InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "i2c"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
	Option	    "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "HorizScrollDelta" "0"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "Generic Monitor"
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. Radeon R250 Lf [Radeon Mobility 9000 M9]"
	Driver      "fglrx"
	Option "OpenGLOverlay" "off" #this isn't necessary for me
	Option "UseInternalAGPGART" "no"
	Option "KernelModuleParm" "agplock=0"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
        Option "OpenGLOverlay" "off" #this isn't necessary for me
        Option "UseInternalAGPGART" "no"
        Option "KernelModuleParm" "agplock=0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. Radeon R250 Lf [Radeon Mobility 9000 M9]"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1400x1050"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1400x1050"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1400x1050"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1400x1050"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1400x1050"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1400x1050"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
        Option  "Composite" "Disable"
EndSection

#Section "ServerFlags"
#        Option  "AIGLX" "off"
#EndSection

---

### Post by Paerez on 2007-02-09
Regarding wobbly windows, see the bottom of the howto.

---

### Post by parradux on 2007-02-10
I've tried all your tweaks and nothing.

---

### Post by Paerez on 2007-02-10
the bottom of the howto says that you can't use wobbly windows b/c it crashes :D

---

### Post by parradux on 2007-02-10
Ok I've installed the non opengl patch still doesnt work. I just get the panels and some checkered  white and black screen with an x as my cursor. 

How do I install the opengl patch if I cant get into Xgl?

---

### Post by Jose Catre-Vandis on 2007-02-11
The howto was pretty successful for me, on a Shuttle XPC SN45G with an ATi 9550 card, on Edgy. The only problem I have is that when I CTRL+ALT+BACKSPACE out of my XGL session, and then try to log in in a normal Gnome session, I just get a wallpaper screen and the login sound. I do not see the Ubuntu load up panel and icons, nor do my panel app panels come up. Have to CTRL+ALT+BACKSPACE again and then reboot to get back to a normal (non XGL) session. Any clues? This didn't happen under dapper on the same machine.

---

### Post by Paerez on 2007-02-11
My login screen gets jammed up too. It does this on my desktop which has a non-mobility card and no XGL. The only similarity is that they both use the fglrx driver, which is what I think is causing the loading hang.

---

### Post by dracomordag on 2007-02-11
david@desktop:~$ sudo cp /lib/modules/`uname -r`/volatile/fglrx.ko /lib/modules/`uname -r`/misc/fglrx.ko
cp: cannot create regular file `/lib/modules/2.6.17-11-generic/misc/fglrx.ko': No such file or directory

---

### Post by Paerez on 2007-02-11
you may need to create the misc directory:

sudo mkdir /lib/modules/`uname -r`/misc

---

### Post by dracomordag on 2007-02-11
Building tag database... Done      
The following packages are BROKEN:
  linux-restricted-modules-generic 
The following packages will be REMOVED:
  linux-restricted-modules-2.6.17-11-generic 
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 20.9MB will be freed.
The following packages have unmet dependencies:
  linux-restricted-modules-generic: Depends: linux-restricted-modules-2.6.17-11-generic but it is not installable
Resolving dependencies...
The following actions will resolve these dependencies:

Downgrade the following packages:
linux-restricted-modules-generic [2.6.17.11 (edgy-security, now) -> 2.6.17.10
(edgy)]

Score is -40

Accept this solution? [Y/n/q/?]

---

### Post by dracomordag on 2007-02-11
i figured "y", can always return to .11 later



anyway, now when i get to editing the xorg.conf file 
> Add this to the end of xorg.conf ("$ sudo gedit /etx/X11/xorg.conf" to edit it):
Code:

Section "Extensions" Option "Composite" "0" EndSection

it opens xorg.conf fine, but the file is blank and when i save it, it tells me the file cannot be found


EDIT: turns out it should be etC/X11/yaddayaddayadda, not etX.

---

### Post by dracomordag on 2007-02-11
got it working........


thanks a lot!

---

### Post by Paerez on 2007-02-11
ah thanks for catching the etX typo. It's fixed now.

---

### Post by dracomordag on 2007-02-11
alright, i got it all working... beryl's installed, i can open the manager... but how do i make it use beryl instead of metacity? when i right-click the ruby and select window manager -> beryl, it just goes right back to metacity.

---

### Post by Paerez on 2007-02-11
ah, there is something crashing. Right click the ruby and click Quit, then open a terminal and run "beryl-manager". This will run the ruby in the terminal. Then right click and select window manager -> beryl. Then once it blinks, copy the terminals output here.

---

### Post by dracomordag on 2007-02-11
**************************************************************
* Beryl system compatibility check                           *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : failed

No composite extension
beryl: No composite extension

---

### Post by Paerez on 2007-02-12
When you are logging in, click Session and choose XGL, then try again.

---

### Post by dracomordag on 2007-02-12
edit: alright, got that done


now i was able to get to this thread in firefox, then it got an hourglass cursor and wouldnt move

---

### Post by dracomordag on 2007-02-12
rebooted, now when i start it up it all works, but when i switch the window manager to beryl, everything freezes.


EDIT: im able to post here through my laptop, even though the desktop w/Ubuntu isnt working out right now, in case you were wondering


EDIT 2: rebooted again, now nothing loads other than the cursor after i login an xgl session (cursor still moves, btw, but panels, desktop background, etc. are all gone)

---

### Post by Paerez on 2007-02-12
[http://debcentral.org/uploads/photos/23.jpg](http://debcentral.org/uploads/photos/23.jpg)

look right below and to the right of the typing box.

---

### Post by dracomordag on 2007-02-12
ah, check my edits


i actually still dont have those options, however. i had to go into options in the bottom left and hit "select session"

---

### Post by dracomordag on 2007-02-12
alright, i removed beryl-manager from the startup apps, and now i can at least do things

however, it gets to

"************************************************** ************
* Beryl system compatibility check *
************************************************** ************

Detected xserver : XGL

Checking Display :1.0 ...

Checking for XComposite extension : passed (v0.3)
Checking for XDamage extension : passed
Checking for RandR extension : passed
Checking for XSync extension : passed
"


then freezes

---

### Post by Paerez on 2007-02-12
ok try running beryl-xgl in the terminal instead of beryl-manager

---

### Post by dracomordag on 2007-02-12
exact same results

except this time the panels dissapeared (along with the window frame and desktop icons)

---

### Post by Paerez on 2007-02-12
Have you tried loading my beryl profile and then running beryl?

---

### Post by dracomordag on 2007-02-12
huh?

---

### Post by Paerez on 2007-02-12
I attached a berylprofile file to the end of the howto. Download it, open beryl manager's settings, and click import, then import the file.

That will overwrite your beryl settings with mine, which have all the functions that freeze removed.

---

### Post by dracomordag on 2007-02-12
doesnt help.

i think the problem stems all the way back to the fglrx driver install making me downgrade to 2.6.17-10 instead of 2.6.17-11

wouldnt that hurt?

---

### Post by dracomordag on 2007-02-12
im looking at the site you said you got your terminal-based guide from, and he seems to fix the problem i had of getting the regkeys.

i also looked into that thread about detailed crash situations and took its first step.



everything's working a lot better, but its running extremely slow, and i cant open any windows.

---

### Post by dracomordag on 2007-02-12
is it just not possible to have Beryl run on Edgy with a Radeon 9200 Pro? nothing seems to be working at all.

---

### Post by misha680 on 2007-02-12
> **dracomordag said:**
> is it just not possible to have Beryl run on Edgy with a Radeon 9200 Pro? nothing seems to be working at all.

Btw, I am pretty sure beryl (latest version) is broken with Xgl right now. And I hear that fglrx has broken with restricted-modules, but I'm not sure about the latter as I haven't yet updated my kernel and actually have been not using Beryl recently for a couple weeks. But certainly if you look on forums.beryl-project.org it looks like latest beryl is screwed up with Xgl, so either downgrade (in Synpatic->Force Version if it will let you) or just wait for the final 0.2.0

Misha

---

### Post by Paerez on 2007-02-13
I have updated to the latest svn beryl, and it works, but I am still using an old fglrx.

---

### Post by misha680 on 2007-02-13
> **Paerez said:**
> I have updated to the latest svn beryl, and it works, but I am still using an old fglrx.

Yes, sorry I am talking about the "official" version from ubuntu.beryl-project.org, not svn version.

Misha

---

### Post by Paerez on 2007-02-13
In the guide I outline steps to use the svn from trevino, which is what I am having fun with.

If you want to use the official packages, older versions are still in the repos, just downgrade beryl to 1.4 and it will work fine.

---

### Post by dracomordag on 2007-02-13
i tried doing the old versions (the ones linked to in this guide that are not the -svn versions) and got the exact same results

i'm using the latest fglrx driver (8.28.8) and the latest kernel (2.6.17-11)

---

### Post by Paerez on 2007-02-13
the ones link to in the guide are bad, but the old versions of the one in the guide are good. Just downgrade them to 1.4 instead of 1.9999. Also, svn works well.

---

### Post by dracomordag on 2007-02-13
how do i downgrade them?

---

### Post by likeatim on 2007-02-13
just works for me. great!

Specs: Dell Inspiron 8600, ATI Radeon 9600. 
Did as was written, worked as was promised. thank you

---

### Post by Paerez on 2007-02-13
To downgrade you can use synaptic. Find the package then its package->force version.

---

### Post by dracomordag on 2007-02-13
would that possibly help? are the svn's that unreliable?

---

### Post by dracomordag on 2007-02-13
i figure maybe if you looked at my config files, youd see a problem.

xorg.conf
```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
	Option	    "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "DELL E773c"
	HorizSync    30.0 - 70.0
	VertRefresh  50.0 - 160.0
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "Intel Corporation 82865G Integrated Graphics Controller"
	Driver      "vesa"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Intel Corporation 82865G Integrated Graphics Controller"
	Monitor    "DELL E773c"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "Composite" "0"
EndSection

```

sources.list
```

## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

deb http://archive.ubuntu.com/ubuntu edgy main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu edgy-proposed main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb http://archive.ubuntu.com/ubuntu edgy-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://medibuntu.sos-sts.com/repo/ edgy free
deb http://medibuntu.sos-sts.com/repo/ edgy non-free
deb-src http://medibuntu.sos-sts.com/repo/ edgy free
deb-src http://medibuntu.sos-sts.com/repo/ edgy non-free
                                                                                                                                         
## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera, DesktopSecure and more to come.) 
deb http://archive.canonical.com/ubuntu edgy-commercial main

## Listen
# deb http://theli.free.fr/packages/ edgy listen

# beryl-svn
deb http://download.tuxfamily.org/3v1deb edgy beryl-svn
deb-src http://download.tuxfamily.org/3v1deb edgy beryl-svn

## E17 repository "edevelop.org"
deb http://edevelop.org/pkg-e/ubuntu edgy e17
deb-src http://edevelop.org/pkg-e/ubuntu edgy e17
deb http://www.getautomatix.com/apt edgy main

## Automatix repo
deb http://www.getautomatix.com/apt edgy main

#AUTOMATIX REPOS START

deb http://archive.ubuntu.com/ubuntu edgy-security main restricted universe multiverse
#AUTOMATIX REPOS END

```



anything that's wrong/missing? i'm on 2.6.17-11

---

### Post by dracomordag on 2007-02-13
it wont allow me to force emerald to 1.4, either.

i tried it anyway, and...

```

************************************************* * ************
* Beryl system compatibility check *
************************************************** ************

Detected xserver : XGL

Checking Display :1.0 ...

Checking for XComposite extension : passed (v0.3)
Checking for XDamage extension : passed
Checking for RandR extension : passed
Checking for XSync extension : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig : passed
Checking for GLX_EXT_texture_from_pixmap : passed

** (beryl-manager:6762): Warning **: Beryl caught deadly signal 11
```


at least its farther than it used to get

---

### Post by finferflu on 2007-02-13
I got direct rendering working using AIGLX, with [this guide]("https://help.ubuntu.com/community/RadeonDriver") (finally)!!!

It came out, after reconfiguring my xserver-xorg, that my graphics card was a Mobility Radeon 7500... maybe it was all an issue with the default xorg configuration...

---

### Post by dracomordag on 2007-02-13
> **finferflu said:**
> I got direct rendering working using AIGLX, with [this guide]("https://help.ubuntu.com/community/RadeonDriver") (finally)!!!

It came out, after reconfiguring my xserver-xorg, that my graphics card was a Mobility Radeon 7500... maybe it was all an issue with the default xorg configuration...
working that one through...

i typed in
$ sudo apt-get build-dep xserver-xorg-driver-ati

and recieved as a response
E: Unable to find a source package for xserver-xorg-driver-ati

---

### Post by linex on 2007-02-13
i installed everything properly and right after installation, it worked. i had a cube and everything. but, once i restarted and logged in using xgl many problems appreared. i oppened up command prompt and typed in beryl, the outcome is posted below. none of the effects work and everytime i open an app the screen gets messed up. can you please help? thanks

> lin@Terminal777:~$ beryl
**************************************************************
* Beryl system compatibility check                           *
**************************************************************

Detected xserver                                : XGL

Checking Display localhost:1.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

beryl: GLX_EXT_texture_from_pixmap is missing
beryl: Using non-tfp mode
beryl: GLX_SGIX_fbconfig is missing
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display localhost:1.0

---

### Post by linex on 2007-02-13
plus here are two more things that might help
> lin@Terminal777:~$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display "localhost:1.0".
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON XPRESS Series Generic
OpenGL version string: 2.0.6011 (8.28.8)


xorg.conf
> 
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
	InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "i2c"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
EndSection

Section "ServerFlags"
	Option	    "AIGLX" "off"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
	Option	    "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "HorizScrollDelta" "0"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "Generic Monitor"
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. Radeon Xpress 200M (RS482)"
	Driver      "ati"
	BusID       "PCI:1:5:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. Radeon Xpress 200M (RS482)"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1280x800"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1280x800"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1280x800"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1280x800"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1280x800"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1280x800"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "Composite" "Disable"
EndSection

Section "Extensions"
        Option      "Composite" "0"
EndSection



---

### Post by Paerez on 2007-02-13
dracomordag: can you post the output of "lspci" in the terminal?

---

### Post by finferflu on 2007-02-13
> **dracomordag said:**
> working that one through...

i typed in
$ sudo apt-get build-dep xserver-xorg-driver-ati

and recieved as a response
E: Unable to find a source package for xserver-xorg-driver-ati

I don't know what you're working on, but if you want to reconfigure xserver-xorg, you have to type in:

```
sudo dpkg-reconfigure xserver-xorg
```

Hope it helps..

---

### Post by dracomordag on 2007-02-13
alright... im getting places

this is my new error report

**********************************************************
* Beryl system compatibility check                       *
**********************************************************

Detected xserver : XGL

Checking Display :1.0

Checking for XComposite extension : passed (v0.3)
Checking for XDamage extension : passed
Checking for RandR extension : passed
Checking for XSync extension : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig : passed
Checking for GLX_EXT_texture_from_pixmap : passed
Xlib: extension &#8220;Xfree86-DRI&#8221; missing on display &#8220;:1.0&#8221;.
Checking for non power of two texture support : failed

Support for non power of two textures missing

---

### Post by dracomordag on 2007-02-13
> **Paerez said:**
> dracomordag: can you post the output of "lspci" in the terminal?
while in my xgl session?

---

### Post by Paerez on 2007-02-13
it doesn't matter.

---

### Post by dracomordag on 2007-02-13
```

00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:02.0 Display controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (rev 01)
01:00.1 Display controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (Secondary) (rev 01)
01:01.0 Communication controller: Conexant Unknown device 2702 (rev 01)
01:02.0 Multimedia audio controller: Creative Labs [SB Live! Value] EMU10k1X
01:02.1 Input device controller: Creative Labs [SB Live! Value] Input device controller
01:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 02)

```

---

### Post by meander on 2007-02-14
so i did all this, and it seemed to work perfectly, except when i select the xgl session from the list and login, the screen goes blank for a second and brings me right back to the login prompt.
ive got the radeon mobility x1600, it was in teh list of cards that supposedly work, and i dont have the mesa or anything in the fglrxinfo.

```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1600 Generic
OpenGL version string: 2.0.6011 (8.28.8)

```

---

### Post by Akegata on 2007-02-14
I am having HUGE issues getting 3d acceleration working. Any kind of help would 
be highly appreciated.
To make a long story short (as short as possible at least), this is what I've do
ne:
I managed to get 3D acceleration going after installing Ubuntu. Then I built my 
own kernel and tried to get it working again. For various reasons, I reverted to
 the stock kernel, and found out 3D acceleration was no longer working.
After messing around with it for hours, following numerous guides, it finally st
arted working.
Then, the next day, it didn't work anymore. I hadn't even rebooted the system. N
ow I've done too many things to figure out where the problem is, and I really ne
ed help.

The last thing I did was follow the howto in this thread, after removing various
 packages I figured could be messing things up.

As of now, fglrxinfo gives me:
```

display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)

```

cat /var/log/Xorg.0.log | grep EE:
```

        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER
(EE) AIGLX error: dlsym for __driCreateNewScreen_20050727 failed (/usr/lib/dri/f
glrx_dri.so: undefined symbol: __driCreateNewScreen_20050727)
(EE) AIGLX: reverting to software rendering
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom

```

cat /var/log/Xorg.0.log | grep WW:
```

        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(WW) `fonts.dir' not found (or not valid) in "/usr/share/X11/fonts/misc".
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
(WW) The directory "/usr/share/X11/fonts/100dpi/" does not exist.
(WW) The directory "/usr/share/X11/fonts/75dpi/" does not exist.
(WW) The directory "/usr/share/X11/fonts/Type1" does not exist.
(WW) The directory "/usr/share/X11/fonts/100dpi" does not exist.
(WW) The directory "/usr/share/X11/fonts/75dpi" does not exist.
(WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d
/dirs/TrueType".
(WW) fglrx: No matching Device section for instance (BusID PCI:3:0:1) found
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(WW) fglrx(0): Option "VendorName" is not used
(WW) fglrx(0): Option "ModelName" is not used

```

dmesg | grep fglrx:
```

[17179602.956000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologie
s, Starnberg, GERMANY' taints kernel.
[17179602.956000] [fglrx] Maximum main memory to use for locked dma buffers: 928
 MBytes.
[17179602.956000] [fglrx] module loaded - fglrx 8.28.8 [Aug 17 2006] on minor 0
[17179604.200000] [fglrx] total      GART = 134217728
[17179604.200000] [fglrx] free       GART = 118226944
[17179604.200000] [fglrx] max single GART = 118226944
[17179604.200000] [fglrx] total      LFB  = 124305408
[17179604.200000] [fglrx] free       LFB  = 108843008
[17179604.200000] [fglrx] max single LFB  = 108843008
[17179604.200000] [fglrx] total      Inv  = 134217728
[17179604.200000] [fglrx] free       Inv  = 134217728
[17179604.200000] [fglrx] max single Inv  = 134217728
[17179604.200000] [fglrx] total      TIM  = 0

```

lsmod | grep fglrx:
```

fglrx                 406988  8 
agpgart                34888  2 fglrx,sis_agp

```

And, finally (this is probably the only place I actually see a problem, though I
 don't know how to fix it), glxinfo | grep direct:
```

direct rendering: No
OpenGL renderer string: Mesa GLX Indirect

```

My xorg.conf:
```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
        Identifier     "Default Layout"
        Screen      0  "aticonfig-Screen[0]" 0 0
        InputDevice    "Generic Keyboard"
        InputDevice    "Configured Mouse"
        InputDevice    "stylus" "SendCoreEvents"
        InputDevice    "cursor" "SendCoreEvents"
        InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

        # path to defoma fonts
        FontPath     "/usr/share/X11/fonts/misc"
        FontPath     "/usr/share/X11/fonts/cyrillic"
        FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath     "/usr/share/X11/fonts/Type1"
        FontPath     "/usr/share/X11/fonts/100dpi"
        FontPath     "/usr/share/X11/fonts/75dpi"
        FontPath     "/usr/share/fonts/X11/misc"
        FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load  "bitmap"
        Load  "ddc"
        Load  "dri"
        Load  "extmod"
        Load  "freetype"
        Load  "glx"
        Load  "int10"
        Load  "type1"
        Load  "vbe"
EndSection

Section "InputDevice"
        Identifier  "Generic Keyboard"
        Driver      "kbd"
        Option      "CoreKeyboard"
        Option      "XkbRules" "xorg"
        Option      "XkbModel" "pc105"
        Option      "XkbLayout" "se"
        Option      "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
        Identifier  "Configured Mouse"
        Driver      "mouse"
        Option      "CorePointer"
        Option      "Device" "/dev/input/mice"
        Option      "Protocol" "ExplorerPS/2"
        Option      "ZAxisMapping" "4 5"
        Option      "Buttons" "7"
        Option      "ButtonMapping" "1 2 3 6 7"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
        Identifier  "stylus"
        Driver      "wacom"
        Option      "Device" "/dev/wacom"          # Change to 
        Option      "Type" "stylus"
        Option      "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
        Identifier  "eraser"
        Driver      "wacom"
        Option      "Device" "/dev/wacom"          # Change to 
        Option      "Type" "eraser"
        Option      "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
        Identifier  "cursor"
        Driver      "wacom"
        Option      "Device" "/dev/wacom"          # Change to 
        Option      "Type" "cursor"
        Option      "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
        Identifier   "Generic Monitor"
        HorizSync    28.0 - 80.0
        VertRefresh  43.0 - 60.0
        Option      "DPMS"
Section "Monitor"
        Identifier   "aticonfig-Monitor[0]"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

Section "Device"
        Identifier  "ATI Technologies, Inc. Radeon X800 (R430 UO)"
        Driver      "vesa"
        BusID       "PCI:3:0:0"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[0]"
        Driver      "fglrx"
        Option      "VideoOverlay" "on"
        Option      "OpenGLOverlay" "off"
EndSection

Section "Screen"
        Identifier "Default Screen"
        Device     "ATI Technologies, Inc. Radeon X800 (R430 UO)"
        Monitor    "Generic Monitor"
        DefaultDepth     24
        SubSection "Display"
                Depth     1
                Modes    "1600x1200" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     4
                Modes    "1600x1200" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     8
                Modes    "1600x1200" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     15
                Modes    "1600x1200" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     16
                Modes    "1600x1200" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     24
                Modes    "1600x1200" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "Screen"
        Identifier "aticonfig-Screen[0]"
        Device     "aticonfig-Device[0]"
        Monitor    "aticonfig-Monitor[0]"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection

Section "DRI"
        Mode         0666
EndSection

Section "Extensions"
        Option      "Composite" "0"
EndSection

```

Sorry for the huge post.

---

### Post by dracomordag on 2007-02-14
code box that, please... ["code]





anyway, XGL would not work for me, so im attempting to switch to AIGLX. i've gotten so close!

when i type "beryl-manager" into the terminal, everything says "passed", but then it all freezes and logs me out.

---

### Post by linex on 2007-02-14
can someone please reply:( 

why does it say:
> beryl: GLX_EXT_texture_from_pixmap is missing
beryl: Using non-tfp mode
beryl: GLX_SGIX_fbconfig is missing
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display localhost:1.0

---

### Post by gloscherrybomb on 2007-02-16
I have the exact same problem as you ^^^. 

My Beryl used to work fine on the .10 kernel with a slightly older version of beryl but now i get this error.

---

### Post by Paerez on 2007-02-16
I think the new linux-restricted-modules installed a new fglrx that isn't working..... maybe try downgrading your linux-restricted-modules package.

---

### Post by Paerez on 2007-02-16
ok when you install the updates, log in, open the terminal and run:
```
sudo depmod -a
sudo modprobe fglrx
```

then CTRL ALT BACKSPACE

---

### Post by adam.tropics on 2007-02-16
> **gloscherrybomb said:**
> I have the exact same problem as you ^^^. 

My Beryl used to work fine on the .10 kernel with a slightly older version of beryl but now i get this error.

For me, with the .10 kernel, i could only run Beryl with the 386 linux-image, but since .11 can only use the generic linux-image! This is not the first time this has happened either, I have no clue why, but it may be worth trying.

---

### Post by Somenoob on 2007-02-20
I have the newest fglrx driver from ATI. Xgl and Beryl are installed properly, however everytime i run beryl in the xgl session I get this error msg.

> beryl: Support for non power of two textures missing
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :1.0

---

### Post by dbott67 on 2007-02-20
I was not able to run the stable version of Beryl.  I had to use Trevino's repos:

```
deb http://download.tuxfamily.org/3v1deb edgy beryl-svn
```

-Dave

---

### Post by Paerez on 2007-02-21
currently both SVN and stable are non-functioning (as of noon or so on 2/20/07). Please refrain from posting with problems until the next svn release.

---

### Post by Somenoob on 2007-02-21
I have used beryl before, somehow I could not launch the stable version so I uninstalled it and installed the one from Trevino's repos, same problem. Xgl is runing properly i don't see what the cause is, Any known fix?

---

### Post by Paerez on 2007-02-21
read my post right before yours

---

### Post by Zuhaira on 2007-02-22
Thanks a lot Paerez for the tutorial 

I followed your tips and my ATI Mobility Radeon 9000 works fine with Direct Rendering & 3D Acceleration. 

But I have a problem. When I start XGL session, then starting Beryl I get white screen. I used shortcuts to move the desktop everything working but I can't see anything in my desktop. I can move the cubic desktop, spinning and I can see Beryl Jewel logo up and down but nothing else. 

here my detailed information

```

$ glxinfo | grep direct
direct rendering: Yes
```

```
$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig, GLX_MESA_copy_sub_buffer
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context, 
    GLX_ARB_get_proc_address, GLX_SGI_video_sync, GLX_ARB_multisample, 
    GLX_ATI_pixel_format_float, GLX_ATI_render_texture
GLX version: 1.2
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context, 
    GLX_ARB_multisample
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY/RADEON 9000 DDR Generic
OpenGL version string: 1.3.1091 (X4.3.0-8.28.8)
OpenGL extensions:
    GL_ARB_multitexture, GL_EXT_texture_env_add, GL_EXT_compiled_vertex_array, 
    GL_S3_s3tc, GL_ARB_occlusion_query, GL_ARB_point_parameters, 
    GL_ARB_texture_border_clamp, GL_ARB_texture_compression, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_transpose_matrix, GL_ARB_vertex_blend, GL_ARB_vertex_buffer_object, 
    GL_ARB_vertex_program, GL_ARB_window_pos, GL_ATI_element_array, 
    GL_ATI_envmap_bumpmap, GL_ATI_fragment_shader, GL_ATI_map_object_buffer, 
    GL_ATI_texture_env_combine3, GL_ATI_texture_mirror_once, 
    GL_ATI_vertex_array_object, GL_ATI_vertex_attrib_array_object, 
    GL_ATI_vertex_streams, GL_ATIX_texture_env_combine3, 
    GL_ATIX_texture_env_route, GL_ATIX_vertex_shader_output_point_size, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, GL_EXT_blend_func_separate, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_clip_volume_hint, 
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_pixels, GL_EXT_point_parameters, GL_EXT_rescale_normal, 
    GL_EXT_secondary_color, GL_EXT_separate_specular_color, 
    GL_EXT_stencil_wrap, GL_EXT_texgen_reflection, GL_EXT_texture3D, 
    GL_EXT_texture_compression_s3tc, GL_EXT_texture_cube_map, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp, 
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_vertex_array, 
    GL_EXT_vertex_shader, GL_HP_occlusion_test, GL_NV_blend_square, 
    GL_NV_occlusion_query, GL_NV_texgen_reflection, GL_SGI_color_matrix, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SUN_multi_draw_arrays
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 Slow
0x24 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 Slow
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 Slow
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 Slow
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x29 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x2b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 Slow
0x2c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 Slow
0x2d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 Slow
0x2e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 Slow
0x2f 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x30 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x31 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x32 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
```

```
$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY/RADEON 9000 DDR Generic
OpenGL version string: 1.3.1091 (X4.3.0-8.2

```

```
$ beryl
**************************************************************
* Beryl system compatibility check                           *
**************************************************************

Detected xserver                                : XGL

Checking Display :1.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

beryl: GLX_EXT_texture_from_pixmap is missing
beryl: Using non-tfp mode
beryl: GLX_SGIX_fbconfig is missing
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :1.0

```

Thanks for the tips again

---

### Post by Paerez on 2007-02-22
[SIZE="7"]PLEASE READ THIS POST[/SIZE]

I am also getting the white screen errors. In the past couple days the SVN packages are not working on our hardware. If you have problems please don't post!!

Of course, if you have a solution, post away.

Right now, please be patient. I am sure this will clear up in a few days. You can downgrade back to beryl 1.4 stable and that will work.

---

### Post by dracomordag on 2007-02-23
ive never succeeded in being able to downgrade emerald to 1.4. is that necessary?


EDIT: yea, i get whitescreen disease... can still rotate cube, etc.

my synaptic package manager lists beryl and emerald-themes as being 1.4 and i locked version there, but all the lib and beryl-settings, etc. are version 1.9999999, and it wont let me change them.

---

### Post by mwolfe on 2007-02-24
back at the very beginning of feb a messed up release was put in the repository. I figured i'd wait awhile before looking into fixing it, thinking a new update would come up. finally i find this thread and the first post says that with the svn version it is fixed.. but that was a few days or weeks ago and so now the svn is messed up also.. I really don't understand the beryl developers. I'm very tempted to go back to compiz (although development there wasnt too much better). They surely do have a great product if they could limit the releases to working versions. Hopefully a stable release will be out soon.. thanks for your hard work developers, sorry to moan and groan it just seems everytime i decide to check in on beryl its broken.. My old version worked just fine before the update, a bit resource intensive but worked good none the less. I'm tempted to buy an nvidea card since the aiglx works great for my computer at work.

---

### Post by Chupa on 2007-02-24
> **Zuhaira said:**
> I have a problem. When I start XGL session, then starting Beryl I get white screen. I used shortcuts to move the desktop everything working but I can't see anything in my desktop. I can move the cubic desktop, spinning and I can see Beryl Jewel logo up and down but nothing else.

I have the same problem. Launching beryl-xgl doesn't help. I've tried to set different types of rendering in Beryl but with no results. Can someone help us?

---

### Post by dracomordag on 2007-02-24
everyone's been saying downgrade to 1.4 to fix this


however, i can only downgrade beryl and emerald-themes to 1.4, not beryl-core, beryl-manager, beryl-plugins, beryl-plugins-data, libemeraldengine0, emerald, etc.

---

### Post by misha680 on 2007-02-24
I think it is definitely fair to criticize the beryl developers for not keeping up good Xgl support in their product. On the other hand, though, having worked on fixing two crashes with our card in beryl (well Xgl), I have to say that beryl with the mobility radeon 9000 using fglrx is really going to be a dead end. The fglrx drivers have bugs which are directly responsible for almost all the beryl/Xgl crashes I have seen, and although workarounds can be made for a lot of the problems with these drivers, it is tedious and not at all satisfying as the bug itself can never be fixed, as not only are the drivers proprietary but not even updated at all because they have dropped support for the 9000.

I would suggest either buying an Nvidia card if you can, or if, like me, you are on a laptop, trying somehow to get people to get more work done on the open source drivers (although if i understand correctly the specs to our cards aren't available either, which is a big problem). Or get ATI to open source their legacy drivers. Personally, I've given up on beryl and compiz for a while, hoping that the open source drivers will get a bit speedier.

Just my two cents.
MIsha

> **mwolfe said:**
> back at the very beginning of feb a messed up release was put in the repository. I figured i'd wait awhile before looking into fixing it, thinking a new update would come up. finally i find this thread and the first post says that with the svn version it is fixed.. but that was a few days or weeks ago and so now the svn is messed up also.. I really don't understand the beryl developers. I'm very tempted to go back to compiz (although development there wasnt too much better). They surely do have a great product if they could limit the releases to working versions. Hopefully a stable release will be out soon.. thanks for your hard work developers, sorry to moan and groan it just seems everytime i decide to check in on beryl its broken.. My old version worked just fine before the update, a bit resource intensive but worked good none the less. I'm tempted to buy an nvidea card since the aiglx works great for my computer at work.

---

### Post by dracomordag on 2007-02-24
basically the way i feel

---

### Post by dracomordag on 2007-02-24
found a solution to the white-screen error:

beryl-xgl --use-copy




only problem is, now i have no window borders.

---

### Post by Chupa on 2007-02-24
> **dracomordag said:**
> only problem is, now i have no window borders.

launch emerald separately

---

### Post by dracomordag on 2007-02-24
found out a better way:

beryl-manager --no-force-window-manager

right click the ruby, under advanced beryl options, rendering path, select "copy"

then select window manager, beryl





now my problem is that i cant open any new windows

---

### Post by cocoia on 2007-02-25
dracomordag, I used this guide;
[http://forum.beryl-project.org/viewtopic.php?f=36&t=4046&start=0]("http://forum.beryl-project.org/viewtopic.php?f=36&t=4046&start=0")

and inputting this in a terminal;
```
LD_PRELOAD=/usr/lib/fglrx/libGL.so.1.2.xlibmesa beryl
```

makes it all work like a charm. I got the most recent non-svn beryl, a Mobility Radeon X1600 with Fglrx. After this, I just set Beryl as window manager and it goes well from there.

---

### Post by adam.tropics on 2007-02-25
> **Paerez said:**
> [SIZE=7][/SIZE]

Of course, if you have a solution, post away.

Right now, please be patient. I am sure this will clear up in a few days. You can downgrade back to beryl 1.4 stable and that will work.

Ok, so I know this may get a little resistance, but anyway. For me, the white screen, and any other problems, except a couple log out issues, which are not killers for me, have been cured.

My solution was to use svn (Trevinos rep), and his script to compile it myself. (yesterday as it happens) This means I no longer have to start with 'copy' which was horrible for speed and 'fluidity'.

If compiling and such is new you may want to wait, else why not take it as an opportunity to learn. It may just cure what ails ya'!!

---

### Post by mwolfe on 2007-02-25
> I think it is definitely fair to criticize the beryl developers for not keeping up good Xgl support in their product. On the other hand, though, having worked on fixing two crashes with our card in beryl (well Xgl), I have to say that beryl with the mobility radeon 9000 using fglrx is really going to be a dead end. The fglrx drivers have bugs which are directly responsible for almost all the beryl/Xgl crashes I have seen, and although workarounds can be made for a lot of the problems with these drivers, it is tedious and not at all satisfying as the bug itself can never be fixed, as not only are the drivers proprietary but not even updated at all because they have dropped support for the 9000.

I would suggest either buying an Nvidia card if you can, or if, like me, you are on a laptop, trying somehow to get people to get more work done on the open source drivers (although if i understand correctly the specs to our cards aren't available either, which is a big problem). Or get ATI to open source their legacy drivers. Personally, I've given up on beryl and compiz for a while, hoping that the open source drivers will get a bit speedier.

Thanks for the explanation. That makes a lot of sense now. I can understand this really well as I am  a developer and i know how creating software for something that works incorrectly is very difficult. (good example is building webpages that work in IE). I'll give them a break for awhile. Maybe i can find someone with an nvidea card that will give it away for cheap. I usually prefer ati but they really should have an open source driver..

---

### Post by Paerez on 2007-02-25
> **adam.tropics said:**
> Ok, so I know this may get a little resistance, but anyway. For me, the white screen, and any other problems, except a couple log out issues, which are not killers for me, have been cured.

My solution was to use svn (Trevinos rep), and his script to compile it myself. (yesterday as it happens) This means I no longer have to start with 'copy' which was horrible for speed and 'fluidity'.

If compiling and such is new you may want to wait, else why not take it as an opportunity to learn. It may just cure what ails ya'!!

I won't resist you :D. If anything you are offering a solution. I was just trying to prevent 8 billion messages like this:

"WTF I uz this guide and I get white box?! ur guide sox!"

I am back to gnome for the time being. I was actually thinking of not using beryl just because of battery life. Also I like my CTRL+ALT+LEFT and RIGHT to be *very* fast.

---

### Post by Brooklyn on 2007-02-25
Is it normal for during Xgl startup for the screen to go gray and your pointer to become an "X"?  

My full post is here:  [http://www.ubuntuforums.org/showthread.php?t=369845&highlight=9600+pro+turbo]("http://www.ubuntuforums.org/showthread.php?t=369845&highlight=9600+pro+turbo")

---

### Post by Paerez on 2007-02-25
@Brooklyn: yes.

---

### Post by Brooklyn on 2007-02-25
OK! I'm getting somewhere.  Typing "LD_PRELOAD=/usr/lib/fglrx/libGL.so.1.2.xlibmesa beryl &" in the terminal, I can get beryl to run and run decently smoothly.  But, as soon as I close the terminal window, beryl crashes.  Is there anyway to fix this, and get Beryl to startup on system startup using the above command?  I am using the latest SVN of Beryl by the way.

EDIT: I forgot, I had to type beryl-manager --noforce-window-manager first and then  LD_PRELOAD=/usr/lib/fglrx/libGL.so.1.2.xlibmesa beryl &.

---

### Post by dracomordag on 2007-02-25
i followed this new guide, and now all i get is beryl-xgl: Support for non power of two textures missing
beryl-xgl: Failed to manage screen: 0
beryl-xgl: No manageable screens found on display :1.0

---

### Post by Brooklyn on 2007-02-25
Try what I did, I had the same problem.

In terminal, without beryl started, type:

beryl-manager --noforce-window-manager

and then:

LD_PRELOAD=/usr/lib/fglrx/libGL.so.1.2.xlibmesa beryl &


I also made an executable script with those commands, and set it to run on startup.  Now Beryl starts on startup and everything works!  Hurray!

EDIT: If you want, you can try typing "beryl-xgl L--use-copy" as the second command instead of the LD_PRELOAD one.  This also worked for me, but was sluggish.

---

### Post by dracomordag on 2007-02-26
yea, im doing that... and i get the error

---

### Post by Brooklyn on 2007-02-27
Well now I managed to screw up everything.  I installed ProEngineer as root in a gnome session, and now Beryl doesnt work, and I get mesa stuff when I type fglrxinfo.  I would just uninstall pro/e, but I don't know how.  It did not come with any uninstall instructions.  Does anyone have any idea what pro/e mightve done??

My xorg.conf has not changed...

---

### Post by newagelancelot on 2007-02-28
I am so close to getting Beryl/Xgl to work on Ubuntu with my ATI radeon mobility 9000 video card.

I've been fighting it out for a long time, scathing the forums for advice, tips and fixes.  I'm no guru with linux, but I've been dabbling in it here and there.

Here is where I am at now:

I can log into an XGL session from the login screen, and all things work fine.  Firefox runs really slowly, and glxgears is noticeably choppier than when logged into a Gnome session.

When I switch to the Beryl Window Manager but right-clicking the Beryl Manager and switching from Metacity to Beryl.

Next I see an entirely white screen.  As I proceed to rotating the cube via Ctrl-Alt click & drag.  I see that the white screen is actually a side of the cube.  My desktop is not seen at all.  I can see the Beryl screen on the top and bottom of the cube.  All other sides of the cube are black.  However, is a dialog box was open (i.e., to say that my battery is recharged, or that I have updates to install, or that I had a crash recently... that sort of thing) then that dialog box's outline will be white on the black sides of the cube.

I'm finding all of this a bit difficult to debug.  I'm not sure if its an XGL problem or a Beryl problem.  Or worst of all...if its a problem with my system specs (Dell inspiron 600m, 1.7 Ghz Pentium M-processor, 512 MB ram, ATI Radeon Mobililty 9000).

Any help at all would be greatly appreciated.  None of the forums that I've checked seem to address the problem that I'm encountering, since neither XGL nor Beryl is actually crashing.  It's just not working the way I want it to.:( 

Thanks
- J

---

### Post by Paerez on 2007-02-28
newagelancelot: The packages are broken. You are at the best point that the rest of us could get to. This is a very new problem. The previous versions worked using this guide, but it is currently broken. Hopefully new packages will fix it.

Try going back to version 1.4 in the stable repositories.

---

### Post by Ek0nomik on 2007-02-28
I appreciate all the hard work Paerez.

"Also I would like to thank my Computer Vision professor for having boring lectures, inspiring me to get beryl working instead of paying attention. Also my Computer Integrated surgery professor for being boring and giving me the motivation to write this guide instead of paying attention. Be cool stay in school!"

I should be in lecture right now.  :)

I have been having some issues getting Beryl to run.  I am new to Linux (I'm sure you haven't heard anyone on these forums say that before).  I plan on sticking with Linux however.  I plan on completely getting rid of Windows on my laptop, and using strictly Ubuntu, so I am willing to learn it.

I originally followed this guide:  [http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL_and_ATI](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL_and_ATI)

I didn't have any errors while installing.  I have had my fglrx drivers working for weeks.  I just not decided to step into the Beryl issue though.

Below, I posted some output (NOT in the Xgl session).

When I run the Xgl session, I get a gray screen with a black X, which, to my knowledge is perfectly normal, so I am not worried about that.

However, I can't seem to get anything to work.  I think it's all THERE, but it's just not working.

```
fleur@fleur-laptop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1400 Generic
OpenGL version string: 2.0.6011 (8.28.8)

fleur@fleur-laptop:~$ beryl-xgl
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : failed

No composite extension
beryl-xgl: No composite extension
fleur@fleur-laptop:~$ 

```

```
fleur@fleur-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc Unknown device 7145
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832
03:01.1 Class 0805: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
03:01.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
0b:00.0 Network controller: Broadcom Corporation Unknown device 4328 (rev 01)
fleur@fleur-laptop:~$ 

```

Xorg.conf:
```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
	InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "i2c"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
	Option	    "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "HorizScrollDelta" "0"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "Generic Monitor"
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. ATI Default Card"
	Driver      "vesa"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. ATI Default Card"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
        Option  "Composite" "Disable"
EndSection

Section "ServerFlags"
        Option  "AIGLX" "off"
EndSection

```

Again, all of this was posted while in the Gnome session, NOT XGL.  When I boot into Xgl, sometimes the internet doesn't work, but does at the same time.  (Google.com works, and I can search, but Ubuntuforums will NEVER load, along with some other sites... it's kinda weird...)  I can see Beryl in my Applications/System Tools, and the little Gem appears in my Panel.  I can load the Beryl Manager, but I can't get any of the effects to work.  None of the windows appear differently when I go into XGL, and I can't seem to change any themes.

Basically I think it's all there, something is just wrong and isn't utilizing it.

I'd appreciate any help you guys can offer me.  Thanks a lot!

Cheers!

---

### Post by Ek0nomik on 2007-02-28
Also note:  I did follow your guide too... the guide I listed didn't work (again, it installed fine, but just didn't seem to make use of it).  I didn't uninstall anything (I don't think I really needed to) before I tried your guide.  If you think something from the last guide is screwing it up, let me know how I can fix that.  Otherwise any ideas would be appreciated!

**Edit**:

A bit more info.  While in the XGL session, fglrxinfo reveals this:

```
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1400 Generic
OpenGL version string: 2.0.6011 (8.28.8)
```

When I type "beryl" in the terminal, it seems to die.  I can see some output in the Terminal, but it goes by so quickly that I can't read it.  Firefox stays open, but my panels disappear, and the Terminal disappears, and I can't close Firefox or open anything else.

When I type "beryl-xgl", I get a white screen, which I saw some talk about earlier.  I don't know if that issue was resolved, but I don't want to dabble around that until I am sure I won't screw anything else up.  However, after typing beryl-xgl, I Control+Alt+Clicked, and I could see the 3D Box.  All sites were white except 1, which has Gems all over it.  So that's a sign it **works!**

Any ideas?

Cheers!

---

### Post by Paerez on 2007-02-28
The white screen you mentioned at the end is it. It is "working". Right now the beryl developers need to fix some bugs, but once they do, the white screen will turn into functioning beryl.

---

### Post by jbmech006 on 2007-02-28
Paerez  - I've been searching these forums for weeks trying different "how to's" on installing fglrx so that my ATI card was listed in fglrxinfo. Your method worked, so thanks a bunch for posting it. A side note when I uninstalled the restricted modules my wireless card stopped working, so I had to reinstall them. Cheers

---

### Post by Ek0nomik on 2007-02-28
> **Brooklyn said:**
> Try what I did, I had the same problem.

In terminal, without beryl started, type:

beryl-manager --noforce-window-manager

and then:

LD_PRELOAD=/usr/lib/fglrx/libGL.so.1.2.xlibmesa beryl &


I also made an executable script with those commands, and set it to run on startup.  Now Beryl starts on startup and everything works!  Hurray!

EDIT: If you want, you can try typing "beryl-xgl L--use-copy" as the second command instead of the LD_PRELOAD one.  This also worked for me, but was sluggish.

What Brooklyn wrote got it working.  Beryl definitely seems buggy though.  It all works rather nicely, but I don't know if it's really for me.  It's just kinda "cool", but doesn't make anything easier really.  It's kinda fun to putz with.

How does one go about uninstalling it in the future if you decide you don't want it anymore?

Thanks for the good guide and responses fellas.

Cheers!

---

### Post by rpasell on 2007-02-28
I too am having all kinds of problems with Beryl.  I've followed the guide here as well as 3 of the guides posts link too with the same results.  here are some of the outputs I am receiving.

[B]rob@ubuntu-laptop:~$ sudo apt-get install linux-restricted-modules-$(uname -r)
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-restricted-modules-2.6.19.2[/B]

rob@ubuntu-laptop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)

[B]rob@ubuntu-laptop:~$ beryl-xgl
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : failed

No composite extension
beryl-xgl: No composite extension
[/B]

rob@ubuntu-laptop:~$  lspci
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc Unknown device 5a36
00:05.0 PCI bridge: ATI Technologies Inc Unknown device 5a37
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 83)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI (rev 80)
00:14.2 Audio device: ATI Technologies Inc Unknown device 437b (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS482 [Radeon Xpress 200M]
06:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
06:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
06:04.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
06:04.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
06:04.2 Class 0805: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01)
06:04.3 FLASH memory: ENE Technology Inc FLASH memory: ENE Technology Inc: (rev 01)
06:04.4 FLASH memory: ENE Technology Inc Unknown device 0551 (rev 01)

[B]# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
	InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "i2c"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
EndSection

Section "ServerFlags"
	Option	    "AIGLX" "off"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
	Option	    "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "HorizScrollDelta" "0"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "Generic Monitor"
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. Radeon Xpress 200M (RS482)"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID       "PCI:1:5:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. Radeon Xpress 200M (RS482)"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1280x800"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1280x800"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1280x800"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1280x800"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1280x800"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1280x800"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "Composite" "Disable"
EndSection[/B]

If there is anything else I can post that would be helpful let me know. To me Beryl is the candy that sells the Dist.  I would love to get it working to show it off.  I've goten to a point where it appears to load, I can see the Beryl control panel, and configure options, but it just crashes and reverts to default.

---

### Post by wncben on 2007-02-28
Howdy, 
  I tried this method, and also tselliots envy script but to no avail...
Unfortunately, I have an amd64 processor *and* a broadcom 4318 wifi card, and the 2.6.17 generic kernel doesn't like that combo, so I had to run a newer kernel to get wifi up and running.  I am running a 2.6.19.2 kernel (and have wif) but it seems like all the howto's  require the older kernel to get fgrlx up and running right, so right now I am marooned on the mesa... I am enough of a noob that I don't know how to get the needed components compiled into the newer kernel... any ideas?  Any help would be greatly appreciated. Thanks
~Ben

---

### Post by nathan12343 on 2007-03-05
Hi, I'm a complete Linux newbie, so bear with me please.

I've been trying to get Beryl running for a few days now, I stumbled on your howto, and I think you might be able to help me out.

I'm running Edgy on a thinkpad r52 with an x300 graphics card.

I've followed your install instructions, but when I enter fglrxinfo it still says it's using the mesa drivers.

Any ideas?

---

### Post by Viper Daimao on 2007-03-06
I get much the same output as you ek0nomic. 

When I log in with xgl and type fglrxinfo I get:

```
chris@Megatron:~$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display "localhost:1.0".
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON X300 Generic
OpenGL version string: 2.0.6011 (8.28.8)
```

when I try to run beryl from the command line I get
```
chris@Megatron:~$ beryl
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : XGL

Checking Display localhost:1.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

beryl: GLX_EXT_texture_from_pixmap is missing
beryl: Using non-tfp mode
beryl: GLX_SGIX_fbconfig is missing
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display localhost:1.0

```

Trying with 
> beryl-manager --noforce-window-manager

and then:

LD_PRELOAD=/usr/lib/fglrx/libGL.so.1.2.xlibmesa beryl &

It works! But I have to keep the terminal open for it to work. If I close it, I lose the ability to move any windows and have to log out. Also, I can't start the beryl manager up in the top panel with this work around.

I followed the ati wiki's installation guide. I think there might be a problem with my xorg.conf. 

```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
	InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "i2c"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
EndSection

Section "ServerFlags"
	Option	    "AIGLX" "off"
EndSection

Section "Monitor"
	Identifier   "Generic Monitor"
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. M22 [Radeon Mobility M300]"
	Driver      "fglrx"
	Option	    "XAANoOffscreenPixmaps"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. M22 [Radeon Mobility M300]"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1280x800"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1280x800"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1280x800"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1280x800"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1280x800"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1280x800"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "Composite" "0"
EndSection

Section "ServerFlags"
        Option  "AIGLX" "off"
EndSection

```

any help would be appreciated.

---

### Post by Ek0nomik on 2007-03-07
Well, the one thing I could think of Viper is if you put those commands into a script that starts on startup.  This way when you load Ubuntu, it will automatically run those for you.  I think that may solve your issue with closing the terminal and losing it.

I could be wrong though.  But it may be worth giving a try.

Cheers!

---

### Post by rune_kg on 2007-03-10
Yes!!!

Worked perfectly on MOBILITY RADEON 9700. You are my hero!

Rune Kaagaard
[http://runelyd.dk](http://runelyd.dk)

---

### Post by n1tro on 2007-03-14
I got this tutorial working on the first try too but heres the problem.  So I left the laptop on all day and when I got back it or Beryl had crashed so I rebooted and relogged into XGL session.  So the problem is beryl didn't automatically start...it was just gnome.  In order to start, I have to open a terminal screen and run "beryl-xgl" to get it started.  Manually running "startxgl" in a terminal windows just comes up with a crash.  Can anyone help fix this problem so I don't have to manually type in beryl-xgl each time I log in.  Thanks.

---

### Post by dracomordag on 2007-03-15
beryl 0.2.0 is out now


hopefully they fixed these compatibility issues?

---

### Post by Viper Daimao on 2007-03-15
It seems to have fixed my issues so far.

---

### Post by suprPHREAK on 2007-03-19
Hi there!

First off, this is my first time ever using Linux of any flavour, and I'm running Ubuntu 6.10 for 64bit. I really have NO CLUE what all this terminal stuff is about, and I just want to get my machine running smoothly.

I have an Acer Ferrari 4003 laptop: Turion64 @1.6, 1GB Ram, ATI x700 128MB, and 10GB allocated to the Linux partition. Despite this is a decent running WIndows System, its running Linux like putting XP on a 486...Firefox wont even scroll smooth. As well, I cannot use the proper resolution for my monitor, as it isnt an option. Naturally, I turned to ATI for help, and of course, things dont work like easy-to-use double click of XP to install a driver :-)

Anyway, cam across this guide, and it seems to help ohers (and be the same as others on the web) and I get stuck.

When I get to this step:

```

$ sudo aptitude install linux-restricted-modules-'uname-r'
```

I get:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
Couldn't find any package whose name or description matched "linux-restricted-modules-uname-r"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.

```

So it appears something maybe didnt work in the step before, but it did look like it completed successfully. If I run "sudo gedit /etc/x11/xorg.conf" to see whats in there, it comes up completely blank.

Can anyone assist? Thanks!

---

### Post by dracomordag on 2007-03-19
it needs to be sudo gedit etc/X11/xorg.conf

its very picky that way



also, if its not changing anything (No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.)

that means you already have it installed!

---

### Post by suprPHREAK on 2007-03-19
> **dracomordag said:**
> it needs to be sudo gedit etc/X11/xorg.conf

its very picky that way



Still just shows as blank, no matter what I type, even case sensitive.

As well, I was more concerned with the line "Couldn't find any package whose name or description matched "linux-restricted-modules-uname-r""

Where do I get said package, if needed?

---

### Post by dracomordag on 2007-03-19
did you try both /etc and etc/ ?


try manually navigating your way to xorg.conf

---

### Post by Paerez on 2007-03-19
it needs to have the / at the beginning. Copy and paste it from the howto.

Also, for the linux-restricted-modules, you have to use a backquote ` not a single quote ' to do the `uname -r` thing to get it to work.

---

### Post by suprPHREAK on 2007-03-19
Yes, it was the quote type that was messing me up. OK, so I got to the point where I run fglrxinfo, and it still says the Mesa driver

```
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)

```

any thoughts? i noticed a previous poster had this, but no response was given.

---

### Post by suprPHREAK on 2007-03-19
Attached here is the output from xorg.conf, as I noticed it was requested in other posts

---

### Post by Shibby73 on 2007-03-20
PLEASE HELP A STEWPID NEWB:

I recently put Ubuntu 6.10 on my laptop (dual boot XP/Ubuntu).
I thought I'd get all fancy and put beryl on etc...
Been following the many posts and now I am in a real bind.

I have the ATI Mobility Radeon 9000 3D Graphic/64MB RAM card built-in
I thought I followed instructions to use the ATI card (before I found this thread)

I updated to XORG 7.2, things went ok at first, but then I started to notice windows only showing their borders, unless I refreshed them by minimizing and maximizing a few times - very annoying.  Changing settings in Beryl Manager didn't seem to help much.  NOW... I am in bigger trouble, I don't know how to undo anything and when I boot into ubuntu after the little graphics bar showing everything loading (including beryl) I then only see my background, no task bars, nothing, can't access anything only can see the mouse move around.

What can I do to get back into my system and get rid of emerald, beryl, and the xorg7.2 ?

Please give me explicit instructions... I am way over my head and need to keep booting into winxp just to check the forums.  I think I can get into a terminal only mode but don't know what commands to enter to get me back running.  This is interesting, but frustrating - hope to learn a lot.

Best regards,

Steve (shibby73)

---

### Post by huygens on 2007-03-20
> **Paerez said:**
> Also, for the linux-restricted-modules, you have to use a backquote ` not a single quote ' to do the `uname -r` thing to get it to work.

Tips: To avoid confusion you could use $(uname -r) instead of `uname -r` in your howto ;-)

---

### Post by dracomordag on 2007-03-21
> **Shibby73 said:**
> PLEASE HELP A STEWPID NEWB:

I recently put Ubuntu 6.10 on my laptop (dual boot XP/Ubuntu).
I thought I'd get all fancy and put beryl on etc...
Been following the many posts and now I am in a real bind.

I have the ATI Mobility Radeon 9000 3D Graphic/64MB RAM card built-in
I thought I followed instructions to use the ATI card (before I found this thread)

I updated to XORG 7.2, things went ok at first, but then I started to notice windows only showing their borders, unless I refreshed them by minimizing and maximizing a few times - very annoying.  Changing settings in Beryl Manager didn't seem to help much.  NOW... I am in bigger trouble, I don't know how to undo anything and when I boot into ubuntu after the little graphics bar showing everything loading (including beryl) I then only see my background, no task bars, nothing, can't access anything only can see the mouse move around.

What can I do to get back into my system and get rid of emerald, beryl, and the xorg7.2 ?

Please give me explicit instructions... I am way over my head and need to keep booting into winxp just to check the forums.  I think I can get into a terminal only mode but don't know what commands to enter to get me back running.  This is interesting, but frustrating - hope to learn a lot.

Best regards,

Steve (shibby73)
sudo apt-get remove beryl

perchance

---

### Post by Eothred on 2007-03-23
I use kde instead of gnome, and had to tweak some of the instructions a bit. I also have the 9000 mobile card, but I have to say, it's not really working, just not totally crashing.. I can't get any of the features like the cube or the wobbling or anything else work while using xgl, checked that glxgears worked fine and checked that fglrxinfo was as normal. Any hints? Should I install gnome instead (I'm very new to linux generally, so I don't know if that's a stupid question or not..)

---

### Post by carlwh123 on 2007-03-23
Hey people, sorry i'm a n00b.

I can't even get fglrx working, i still get mesa.
First I followed this tutorial - [http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html](http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html)

Everything worked except for window resizing (it was incredibly laggy). So I removed beryl and then I found your tutorial....I followed it exactly and I still get mesa. I even did "reinstall" for the $ sudo aptitude install linux-restricted-modules-`uname -r` line.

Any help is appreciated.

```
carlw@carlw-desktop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)
```

```
carlw@carlw-desktop:~$ lsmod | grep fglrx
fglrx                 534616  9 
agpgart                34888  2 fglrx,intel_agp
```

$ sudo modprobe fglrx
$ lsmod | grep radeon
these 2 give nothing.

I definitely changed the device to fglrx in the xorg.conf file and added the
```
Section "Extensions"
	Option	    "Composite" "false"
EndSection
```

I have an old radeon 9600XT on a P4 3.2 running edgy.
cheers for any help.

---

### Post by Eothred on 2007-03-24
> **carlwh123 said:**
> Hey people, sorry i'm a n00b.

I can't even get fglrx working, i still get mesa.
First I followed this tutorial - [http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html](http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html)


I had the same problem, and it might be that you have to uninstall the modules before you install the new ones according to this tutorial (that did it for me anyway).

Add this line:
$ sudo aptitude remove linux-restricted-modules-`uname -r`

Before you do this:

$ sudo aptitude install linux-restricted-modules-`uname -r`
Now copy the module (the first line creates the directory, so if it is already there and there is an error, it is not a problem):
Code:
$ sudo mkdir /lib/modules/`uname -r`/misc
$ sudo cp /lib/modules/`uname -r`/volatile/fglrx.ko /lib/modules/`uname -r`/misc/fglrx.ko
Now uninstall the package:
Code:
$ sudo aptitude remove linux-restricted-modules-`uname -r`

---

### Post by wncben on 2007-03-27
I fixed my fglrx/edgy problems painlessly.... I INSTALLED FEISTY beta!  lol
feisty's awesome restricted drivers app loaded fglrx with one simple mouse click (maybe two) ;) and I now have 3d acceleration!  glxgears would not run for me in edgy, but I now get 1600fps, and for the first time ever, I can run tuxcart and planet penguin racer, smoothly full screen.... 

 the only problem, was that it did reset my resolution, but I simply added it back to /etc/X11/xorg.conf and am back in fightin' form.... but considering that I waiseted over 40 hours trying to fix edgy....

Happy Happy Joy Joy!

---

### Post by dracomordag on 2007-03-29
it says that "my hardware does not require any restricted drivers"

:'(

---

### Post by kade on 2007-04-01
After giving up on using Beryl on my Dell Latitude D600, this thread has shown me the light.  Many thanks.  I'm loving beryl.  

Cheers

---

### Post by owhno on 2007-04-02
Well i posted my problem on this forum but i haven't got a reply for 2 weeks so maybe you guys in this post can help me

[Here is the old post]("http://ubuntuforums.org/showthread.php?t=385112")

Today instead of 8.34.8 i now have 8.35.8.
This driver also works fine except the weird glitch.
i suppose its a sync error, but the beryl options would not work great to solve this. 
I have tried to install the open source radeon driver and uses aiglx but that went wrong so I sticked to xgl.

If i dont start XGL and just use a normal session the driver works great. Except for that damn amdcccle but via terminal everything works. No glitches or any weird behavior.
With XGL (beryl not loaded yet) i get a diagonal refresh line, when moving windows fast. (upper part is faster then lower part) or a rectangle. It aint slow only that line. with beryl i get it when doing some rotate actions like in the video.

Please help me, i loved beryl (used it fine on old mandriva installation)
Or tell me where i can  find a good solution to use the radeon drivers and aiglx

---

### Post by jhenager on 2007-04-06
> **Paerez said:**
> keep in mind ati drivers >=8.29 no longer support the 9000 mobility family, among others. They may still work, but I am scared to try. I am using the edgy 8.28 drivers. Besides, 8.30 only has bugfixes, no new features. And I think the only feature of 8.29 is removed support (may be an incorrect statement). Give 8.28 a shot.

Can you offer directions on how to install the 8.28 drivers? My Beryl install stopped working after I got to the step where I restarted and tested flgrx. It would hang at about 97% on the Ubuntu splash screen with a double line of little misc colored objects just below the progress bar. I booted back into Recovery Mode and renamed xorg.conf to xorg.conf.bad, and xorg.conf.original back to xorg.conf, and that's where I am now.

BTW, I am doing this through VMware, as if this isn't tricky enough to start. :)

---

### Post by Paerez on 2007-04-06
grab the ati driver installer from here:
[http://ati.amd.com/support/drivers/linux/linux-radeon-prer200.html](http://ati.amd.com/support/drivers/linux/linux-radeon-prer200.html)

Then follow these instructions:
[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#Method_2:_Install_the_8.35.5_Driver_Manually](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#Method_2:_Install_the_8.35.5_Driver_Manually)

That tells you how to install the latest fglrx, except you are going to have to use the 8.28 file from the ati site instead of the 8.35 one.

---

### Post by shoyer on 2007-04-24
Any luck updating this guide to Feisty Fawn?

---

### Post by s0undt3ch on 2007-04-25
To Those Interested, ie, WE:
[http://www.petitiononline.com/xSeAILGX/petition.html](http://www.petitiononline.com/xSeAILGX/petition.html)

Sign the petition online so that AMD knows that users wish for AIGLX Support for their Mobility cards.

---

### Post by xlr8ed on 2007-04-25
I got a fun error if anyone wants to take a look ...9800 Pro with dual screens, set as "Big Desktop"

fglrxinfo

```
root@Grover:/var/log# fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9800 PRO
OpenGL version string: 2.0.6400 (8.35.5)

```

Xorg

```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "i2c"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
	Option	    "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "SyncMaster"
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. Radeon R350 NH [Radeon 9800 Pro]"
	Driver      "ati"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. Radeon R350 NH [Radeon 9800 Pro]"
	Monitor    "SyncMaster"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
  Option "Composite" "0" 
EndSection

```

And the error I get about 10 seconds after logging in...I get booted right back to the login screen when I am done reading it.

```
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "jason"
/etc/gmd/Xsession: Beginning session setup...

Fatal server error:
no screens found
xauth: (argv):1: bad "add" command line

(gnome-panel:11245): Gtk-WARNING **: cannot open dispay:

```

---

### Post by Paerez on 2007-04-27
Wow there is a lot of weird stuff going on there.

According to your Xorg.conf, you have two screens:

Monitor+ati driver+ati screen
Monitor+fglrx driver+fglrx screen

I really doubt that using two drivers at the same time will work.

Also, you have not enabled bigdesktop anywhere in the file.

---

### Post by xlr8ed on 2007-04-27
> **Paerez said:**
> Wow there is a lot of weird stuff going on there.

According to your Xorg.conf, you have two screens:

Monitor+ati driver+ati screen
Monitor+fglrx driver+fglrx screen

I really doubt that using two drivers at the same time will work.

Also, you have not enabled bigdesktop anywhere in the file.

Used the method [here]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide") for installing my ATI Drivers and simply enabled Bigdesktop in the ATI Control Center

---

### Post by zaxor0 on 2007-08-10
I have this card with a Fiesty Fawn installation. Should I still use the 8.28 version of the fglrx drivers? If so how do I install them with aptitude, or will aptitude already instal the 8.28 version. I tried using the .run file to install but i would always get some sort of error. To solve this error I read i had to replace something about the symlink and bash and dash in edgy. I cant remember but if needed I can find all this information.

Mainly, I just need to know if the version of the driver I need has to be specifically 8.28 for FGLRX to work on my mobility 9000.

---

### Post by Paerez on 2007-08-12
Hey zaxor0, this guide is no longer alive. You can use the restricted drivers manager to install fglx in feisty, then use "Desktop Effects" under System->Preferences to use Compiz (which is like beryl). If you want lots of effects, check out trevino's compiz fusion SVN repository (just search the forum for compiz fusion).

---

### Post by linuxnewbie1113 on 2007-08-12
Cant get past the first part of the setup can ne one please help me this is the output i get.
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)
 All help is greatly appreciated

---

### Post by Paerez on 2007-08-13
See my previous post. This guide is dead. If you want compositing effects, upgrade to feisty and follow the more official and less hack-ish methods.

---

