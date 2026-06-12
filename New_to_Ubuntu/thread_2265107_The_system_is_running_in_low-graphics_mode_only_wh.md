---
title: "The system is running in low-graphics mode only when logging off user"
date: 2015-02-12
forum: New to Ubuntu
---

### Post by DavidSr on 2015-02-12
I&#8217;m working on setting up Ubuntu 12.04.5 in a classroom environment here in San Antonio, Texas.  We hope to replace several labs currently running Windows XP that connect to a Citrix farm.  This version of Ubuntu was selected to be compatible with NetSupport software that teachers use to monitor a classroom. 
 
The OS is installed on HP dc7700u and dc7600u computers.  I followed online directions for creating a Windows 7-style Ubuntu desktop (looks and works very nice too).  There are two user accounts on this system, one for Students without the rights to install applications (all games removed) and the other for Administrators with full access.  On boot up, the Student ID is logged in with the option to not require a password (as seen below). 

After having everything almost at the testing stage I came across a problem.  I get a graphics error when I log off the student user to try to use the Administrator account.  Up until this point, everything has been running great.  As soon as I log off, the system locks up with &#8220;The system is running in low-graphics mode&#8221;, input device settings could not be detected correctly.  The next option is &#8220;What would you like to do?&#8221;

[LIST=1]
[*]Run in low-graphics mode for just one session
[*]Reconfigure graphics
[*]Troubleshoot the error
[*]Exit to console login
[/LIST]
 
In most cases the mouse and keyboard do not work.  A couple of times when I could make a selection I have tried all options but nothing happened.  I can power down the system and it boots into Student user without any problems.

---

### Post by sandyd on 2015-02-12
Hi, and welcome to the forums.

Could you run the following commands in the terminal, and paste the output?
This will list your current hardware and allow us to diagnose the problem you have .
```

lshw -c Display
lspci
lsmod
```

---

### Post by DavidSr on 2015-02-12
lshw -c Display
  *-display              
       description: VGA compatible controller
       product: 82Q963/Q965 Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: [EMAIL="pci@0000:00:02.0"]pci@0000:00:02.0[/EMAIL]
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:43 memory:f0400000-f04fffff memory:e0000000-efffffff ioport:1110(size=8)
 
lspci
00:00.0 Host bridge: Intel Corporation 82Q963/Q965 Memory Controller Hub (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82Q963/Q965 Integrated Graphics Controller (rev 02)
00:03.0 Communication controller: Intel Corporation 82Q963/Q965 HECI Controller (rev 02)
00:03.2 IDE interface: Intel Corporation 82Q963/Q965 PT IDER Controller (rev 02)
00:03.3 Serial controller: Intel Corporation 82Q963/Q965 KT Controller (rev 02)
00:19.0 Ethernet controller: Intel Corporation 82566DM Gigabit Network Connection (rev 02)
00:1a.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1d.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HO (ICH8DO) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801H (ICH8 Family) 4 port SATA Controller [IDE mode] (rev 02)
 
lsmod
Module                  Size  Used by
rfcomm                 59026  0
bnep                   19107  2
bluetooth             356727  10 rfcomm,bnep
parport_pc             32114  0
ppdev                  17423  0
snd_hda_codec_realtek    59921  1
snd_hda_intel          43462  4
snd_hda_codec         169779  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                90501  2 snd_hda_intel,snd_hda_codec
i915                  733300  2
snd_seq_midi           13132  0
snd_rawmidi            25198  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                55716  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28971  2 snd_pcm,snd_seq
snd_seq_device         14137  3 snd_seq_midi,snd_rawmidi,snd_seq
drm_kms_helper         49282  1 i915
psmouse                97606  0
drm                   249595  3 i915,drm_kms_helper
gpio_ich               13278  0
hp_wmi                 17834  0
serio_raw              13230  0
snd                    61383  18 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_seq_midi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
sparse_keymap          13658  1 hp_wmi
soundcore              12600  1 snd
snd_page_alloc         18398  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13316  1 i915
mei_me                 18234  0
lpc_ich                16987  0
mac_hid                13077  0
mei                    71468  1 mei_me
wmi                    18827  1 hp_wmi
video                  19330  1 i915
lp                     13359  0
parport                40945  3 parport_pc,ppdev,lp
hid_generic            12492  0
e1000e                225784  0
ptp                    18488  1 e1000e
pps_core               18768  1 ptp
floppy                 60183  0
usbhid                 47442  0
hid                    92101  2 hid_generic,usbhid

I left the computer for some time after logging off and just noticed a video error, something about not supporting the gxi?? extension.  I went to get my pen to write down the error code but everything had rebooted and was back up to the desktop again.

---

### Post by DavidSr on 2015-02-12
After a couple of reboots, display worked (error after logging user out) and I was able to select first option: Run in low graphics for session
Could not write bytes:  Broke pipe
Then line after line after line (fills up the page) of > timer: connect/disconnect timeout.

---

### Post by DavidSr on 2015-02-12
Did a few more reboots and finally captured the error screen after a log off:

glschool:  display ":0.0" does not support the GLX extention
xscreensaver:  09:06:32 0: child pid 8192 (glschool) exited abnormally (code 1).

So looking at what is set for the screensaver now.

glschool was one of the Screen saver options, turned it off and rebooting

---

### Post by sandyd on 2015-02-12
Other then the graphics card being a bit weak, everything seems to be fine.

Can you attach Xorg.0.log from /var/log, it should have a record of why Xorg is doing that on logoff.

---

### Post by DavidSr on 2015-02-13
> **sandyd said:**
> Other then the graphics card being a bit weak, everything seems to be fine.

Can you attach Xorg.0.log from /var/log, it should have a record of why Xorg is doing that on logoff.

Thanks for looking at this, I tried to include as an attachment but get an error > Xorg.0.log.txt: Your file of 37.9 KB bytes exceeds the forum's limit of 19.5 KB for this filetype

[    19.093] 
X.Org X Server 1.11.3
Release Date: 2011-12-16
[    19.093] X Protocol Version 11, Revision 0
[    19.093] Build Operating System: Linux 2.6.42-37-generic i686 Ubuntu
[    19.093] Current Operating System: Linux ubuntuERC1234 3.13.0-45-generic #74~precise1-Ubuntu SMP Thu Jan 15 20:22:28 UTC 2015 i686
[    19.093] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-45-generic root=UUID=1b0f8017-a51a-42b4-9b7d-1c8ec35855e3 ro quiet splash vt.handoff=7
[    19.093] Build Date: 09 December 2014  11:11:05PM
[    19.093] xorg-server 2:1.11.4-0ubuntu10.16 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    19.093] Current version of pixman: 0.30.2
[    19.093]     Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
[    19.093] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    19.094] (==) Log file: "/var/log/Xorg.0.log", Time: Thu Feb 12 09:22:43 2015
[    19.182] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    19.294] (==) No Layout section.  Using the first Screen section.
[    19.294] (==) No screen section available. Using defaults.
[    19.294] (**) |-->Screen "Default Screen Section" (0)
[    19.294] (**) |   |-->Monitor "<default monitor>"
[    19.309] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    19.309] (==) Automatically adding devices
[    19.309] (==) Automatically enabling devices
[    19.396] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    19.396]     Entry deleted from font path.
[    19.396] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    19.396]     Entry deleted from font path.
[    19.396] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    19.396]     Entry deleted from font path.
[    19.396] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    19.396]     Entry deleted from font path.
[    19.396] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    19.396]     Entry deleted from font path.
[    19.396] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    19.396]     Entry deleted from font path.
[    19.396] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    19.396] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    19.397] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    19.411] (II) Loader magic: 0xb77915a0
[    19.411] (II) Module ABI versions:
[    19.411]     X.Org ANSI C Emulation: 0.4
[    19.411]     X.Org Video Driver: 11.0
[    19.411]     X.Org XInput driver : 16.0
[    19.412]     X.Org Server Extension : 6.0
[    19.413] (--) PCI:*(0:0:2:0) 8086:2992:103c:2803 rev 2, Mem @ 0xf0400000/1048576, 0xe0000000/268435456, I/O @ 0x00001110/8
[    19.413] (II) Open ACPI successful (/var/run/acpid.socket)
[    19.413] (II) LoadModule: "extmod"
[    19.708] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    19.741] (II) Module extmod: vendor="X.Org Foundation"
[    19.741]     compiled for 1.11.3, module version = 1.0.0
[    19.741]     Module class: X.Org Server Extension
[    19.741]     ABI class: X.Org Server Extension, version 6.0
[    19.741] (II) Loading extension MIT-SCREEN-SAVER
[    19.741] (II) Loading extension XFree86-VidModeExtension
[    19.741] (II) Loading extension XFree86-DGA
[    19.741] (II) Loading extension DPMS
[    19.742] (II) Loading extension XVideo
[    19.742] (II) Loading extension XVideo-MotionCompensation
[    19.742] (II) Loading extension X-Resource
[    19.742] (II) LoadModule: "dbe"
[    19.742] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    19.766] (II) Module dbe: vendor="X.Org Foundation"
[    19.766]     compiled for 1.11.3, module version = 1.0.0
[    19.766]     Module class: X.Org Server Extension
[    19.766]     ABI class: X.Org Server Extension, version 6.0
[    19.766] (II) Loading extension DOUBLE-BUFFER
[    19.766] (II) LoadModule: "glx"
[    19.767] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    19.851] (II) Module glx: vendor="X.Org Foundation"
[    19.851]     compiled for 1.11.3, module version = 1.0.0
[    19.851]     ABI class: X.Org Server Extension, version 6.0
[    19.851] (==) AIGLX enabled
[    19.851] (II) Loading extension GLX
[    19.851] (II) LoadModule: "record"
[    19.852] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    19.871] (II) Module record: vendor="X.Org Foundation"
[    19.871]     compiled for 1.11.3, module version = 1.13.0
[    19.871]     Module class: X.Org Server Extension
[    19.872]     ABI class: X.Org Server Extension, version 6.0
[    19.872] (II) Loading extension RECORD
[    19.872] (II) LoadModule: "dri"
[    19.872] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    19.920] (II) Module dri: vendor="X.Org Foundation"
[    19.920]     compiled for 1.11.3, module version = 1.0.0
[    19.920]     ABI class: X.Org Server Extension, version 6.0
[    19.920] (II) Loading extension XFree86-DRI
[    19.920] (II) LoadModule: "dri2"
[    19.921] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    19.956] (II) Module dri2: vendor="X.Org Foundation"
[    19.956]     compiled for 1.11.3, module version = 1.2.0
[    19.956]     ABI class: X.Org Server Extension, version 6.0
[    19.956] (II) Loading extension DRI2
[    19.956] (==) Matched intel as autoconfigured driver 0
[    19.956] (==) Matched vesa as autoconfigured driver 1
[    19.956] (==) Matched fbdev as autoconfigured driver 2
[    19.956] (==) Assigned the driver to the xf86ConfigLayout
[    19.956] (II) LoadModule: "intel"
[    19.956] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    20.046] (II) Module intel: vendor="X.Org Foundation"
[    20.046]     compiled for 1.11.3, module version = 2.17.0
[    20.046]     Module class: X.Org Video Driver
[    20.046]     ABI class: X.Org Video Driver, version 11.0
[    20.046] (II) LoadModule: "vesa"
[    20.046] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    20.097] (II) Module vesa: vendor="X.Org Foundation"
[    20.097]     compiled for 1.11.3, module version = 2.3.0
[    20.097]     Module class: X.Org Video Driver
[    20.097]     ABI class: X.Org Video Driver, version 11.0
[    20.097] (II) LoadModule: "fbdev"
[    20.098] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    20.119] (II) Module fbdev: vendor="X.Org Foundation"
[    20.119]     compiled for 1.11.3, module version = 0.4.2
[    20.119]     ABI class: X.Org Video Driver, version 11.0
[    20.119] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
    i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
    E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
    965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
    4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
    Sandybridge Desktop (GT1), Sandybridge Desktop (GT2),
    Sandybridge Desktop (GT2+), Sandybridge Mobile (GT1),
    Sandybridge Mobile (GT2), Sandybridge Mobile (GT2+),
    Sandybridge Server, Ivybridge Mobile (GT1), Ivybridge Mobile (GT2),
    Ivybridge Desktop (GT1), Ivybridge Desktop (GT2), Ivybridge Server,
    Ivybridge Server (GT2)
[    20.120] (II) VESA: driver for VESA chipsets: vesa
[    20.120] (II) FBDEV: driver for framebuffer: fbdev
[    20.120] (++) using VT number 7

[    20.140] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    20.140] (WW) Falling back to old probe method for vesa
[    20.140] (WW) Falling back to old probe method for fbdev
[    20.140] (II) Loading sub module "fbdevhw"
[    20.140] (II) LoadModule: "fbdevhw"
[    20.140] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    20.160] (II) Module fbdevhw: vendor="X.Org Foundation"
[    20.160]     compiled for 1.11.3, module version = 0.0.2
[    20.160]     ABI class: X.Org Video Driver, version 11.0
[    20.160] drmOpenDevice: node name is /dev/dri/card0
[    20.160] drmOpenDevice: open result is 9, (OK)
[    20.161] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[    20.161] drmOpenDevice: node name is /dev/dri/card0
[    20.161] drmOpenDevice: open result is 9, (OK)
[    20.161] drmOpenByBusid: drmOpenMinor returns 9
[    20.161] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    20.161] (II) intel(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    20.161] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    20.161] (==) intel(0): RGB weight 888
[    20.161] (==) intel(0): Default visual is TrueColor
[    20.161] (II) intel(0): Integrated Graphics Chipset: Intel(R) 965Q
[    20.161] (--) intel(0): Chipset: "965Q"
[    20.161] (**) intel(0): Relaxed fencing enabled
[    20.161] (**) intel(0): Wait on SwapBuffers? enabled
[    20.161] (**) intel(0): Triple buffering? enabled
[    20.161] (**) intel(0): Framebuffer tiled
[    20.161] (**) intel(0): Pixmaps tiled
[    20.161] (**) intel(0): 3D buffers tiled
[    20.161] (**) intel(0): SwapBuffers wait enabled
[    20.161] (==) intel(0): video overlay key set to 0x101fe
[    20.260] (II) intel(0): Output VGA1 has no monitor section
[    20.360] (II) intel(0): EDID for output VGA1
[    20.360] (II) intel(0): Manufacturer: DEL  Model: a087  Serial#: 844254549
[    20.360] (II) intel(0): Year: 2013  Week: 25
[    20.360] (II) intel(0): EDID Version: 1.3
[    20.360] (II) intel(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
[    20.360] (II) intel(0): Sync:  Separate  Composite  SyncOnGreen
[    20.360] (II) intel(0): Max Image Size [cm]: horiz.: 41  vert.: 26
[    20.360] (II) intel(0): Gamma: 2.20
[    20.360] (II) intel(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
[    20.360] (II) intel(0): First detailed timing is preferred mode
[    20.360] (II) intel(0): redX: 0.642 redY: 0.340   greenX: 0.314 greenY: 0.618
[    20.360] (II) intel(0): blueX: 0.154 blueY: 0.061   whiteX: 0.313 whiteY: 0.329
[    20.360] (II) intel(0): Supported established timings:
[    20.360] (II) intel(0): 720x400@70Hz
[    20.360] (II) intel(0): 640x480@60Hz
[    20.360] (II) intel(0): 640x480@75Hz
[    20.360] (II) intel(0): 800x600@60Hz
[    20.360] (II) intel(0): 800x600@75Hz
[    20.360] (II) intel(0): 1024x768@60Hz
[    20.360] (II) intel(0): 1024x768@75Hz
[    20.360] (II) intel(0): 1280x1024@75Hz
[    20.360] (II) intel(0): Manufacturer's mask: 0
[    20.360] (II) intel(0): Supported standard timings:
[    20.360] (II) intel(0): #0: hsize: 1440  vsize 900  refresh: 60  vid: 149
[    20.360] (II) intel(0): #1: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[    20.360] (II) intel(0): #2: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    20.360] (II) intel(0): #3: hsize: 1440  vsize 900  refresh: 75  vid: 3989
[    20.360] (II) intel(0): #4: hsize: 1280  vsize 800  refresh: 60  vid: 129
[    20.360] (II) intel(0): Supported detailed timing:
[    20.360] (II) intel(0): clock: 106.5 MHz   Image Size:  408 x 255 mm
[    20.360] (II) intel(0): h_active: 1440  h_sync: 1520  h_sync_end 1672 h_blank_end 1904 h_border: 0
[    20.360] (II) intel(0): v_active: 900  v_sync: 903  v_sync_end 909 v_blanking: 934 v_border: 0
[    20.361] (II) intel(0): Serial No: DT0PH36K2RMU
[    20.361] (II) intel(0): Monitor name: DELL P1913
[    20.361] (II) intel(0): Ranges: V min: 56 V max: 76 Hz, H min: 30 H max: 81 kHz, PixClock max 145 MHz
[    20.361] (II) intel(0): EDID (in hex):
[    20.361] (II) intel(0):     00ffffffffffff0010ac87a0554d5232
[    20.361] (II) intel(0):     191701030e291a78ea49a5a457509e27
[    20.361] (II) intel(0):     0f5054a54b009500714f8180950f8100
[    20.361] (II) intel(0):     0101010101019a29a0d0518422305098
[    20.361] (II) intel(0):     360098ff1000001c000000ff00445430
[    20.361] (II) intel(0):     504833364b32524d550a000000fc0044
[    20.361] (II) intel(0):     454c4c2050313931330a2020000000fd
[    20.361] (II) intel(0):     00384c1e510e000a2020202020200009
[    20.361] (II) intel(0): EDID vendor "DEL", prod id 41095
[    20.361] (II) intel(0): Using EDID range info for horizontal sync
[    20.361] (II) intel(0): Using EDID range info for vertical refresh
[    20.361] (II) intel(0): Printing DDC gathered Modelines:
[    20.361] (II) intel(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    20.361] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    20.361] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    20.361] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    20.361] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    20.361] (II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    20.361] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    20.361] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    20.361] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    20.361] (II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    20.361] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    20.361] (II) intel(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
[    20.361] (II) intel(0): Modeline "1280x800"x0.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz)
[    20.361] (II) intel(0): Printing probed modes for output VGA1
[    20.361] (II) intel(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    20.361] (II) intel(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    20.361] (II) intel(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    20.361] (II) intel(0): Modeline "1440x900"x75.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
[    20.361] (II) intel(0): Modeline "1280x800"x59.8   83.50  1280 1352 1480 1680  800 803 809 831 +hsync -vsync (49.7 kHz)
[    20.361] (II) intel(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    20.362] (II) intel(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
[    20.362] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    20.362] (II) intel(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    20.362] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    20.362] (II) intel(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    20.362] (II) intel(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    20.362] (II) intel(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    20.362] (II) intel(0): Output VGA1 connected
[    20.362] (II) intel(0): Using exact sizes for initial modes
[    20.362] (II) intel(0): Output VGA1 using initial mode 1440x900
[    20.362] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    20.362] (II) intel(0): Kernel page flipping support detected, enabling
[    20.362] (**) intel(0): Display dimensions: (410, 260) mm
[    20.362] (**) intel(0): DPI set to (89, 87)
[    20.362] (II) Loading sub module "fb"
[    20.362] (II) LoadModule: "fb"
[    20.362] (II) Loading /usr/lib/xorg/modules/libfb.so
[    20.380] (II) Module fb: vendor="X.Org Foundation"
[    20.380]     compiled for 1.11.3, module version = 1.0.0
[    20.380]     ABI class: X.Org ANSI C Emulation, version 0.4
[    20.380] (II) Loading sub module "dri2"
[    20.380] (II) LoadModule: "dri2"
[    20.380] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    20.380] (II) Module dri2: vendor="X.Org Foundation"
[    20.381]     compiled for 1.11.3, module version = 1.2.0
[    20.381]     ABI class: X.Org Server Extension, version 6.0
[    20.381] (II) UnloadModule: "vesa"
[    20.381] (II) Unloading vesa
[    20.381] (II) UnloadModule: "fbdev"
[    20.381] (II) Unloading fbdev
[    20.381] (II) UnloadModule: "fbdevhw"
[    20.381] (II) Unloading fbdevhw
[    20.381] (==) Depth 24 pixmap format is 32 bpp
[    20.381] (II) intel(0): [DRI2] Setup complete
[    20.381] (II) intel(0): [DRI2]   DRI driver: i965
[    20.381] (II) intel(0): Allocated new frame buffer 1472x900 stride 6144, tiled
[    20.420] (II) UXA(0): Driver registered support for the following operations:
[    20.420] (II)         solid
[    20.420] (II)         copy
[    20.421] (II)         composite (RENDER acceleration)
[    20.421] (II)         put_image
[    20.421] (II)         get_image
[    20.421] (==) intel(0): Backing store disabled
[    20.421] (==) intel(0): Silken mouse enabled
[    20.421] (II) intel(0): Initializing HW Cursor
[    20.444] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    20.444] (==) intel(0): DPMS enabled
[    20.444] (==) intel(0): Intel XvMC decoder enabled
[    20.444] (II) intel(0): Set up textured video
[    20.444] (II) intel(0): Set up overlay video
[    20.444] (II) intel(0): [XvMC] i965_xvmc driver initialized.
[    20.444] (II) intel(0): direct rendering: DRI2 Enabled
[    20.444] (==) intel(0): hotplug detection: "enabled"
[    20.444] (--) RandR disabled
[    20.444] (II) Initializing built-in extension Generic Event Extension
[    20.444] (II) Initializing built-in extension SHAPE
[    20.444] (II) Initializing built-in extension MIT-SHM
[    20.444] (II) Initializing built-in extension XInputExtension
[    20.444] (II) Initializing built-in extension XTEST
[    20.444] (II) Initializing built-in extension BIG-REQUESTS
[    20.444] (II) Initializing built-in extension SYNC
[    20.445] (II) Initializing built-in extension XKEYBOARD
[    20.445] (II) Initializing built-in extension XC-MISC
[    20.445] (II) Initializing built-in extension SECURITY
[    20.445] (II) Initializing built-in extension XINERAMA
[    20.445] (II) Initializing built-in extension XFIXES
[    20.445] (II) Initializing built-in extension RENDER
[    20.445] (II) Initializing built-in extension RANDR
[    20.445] (II) Initializing built-in extension COMPOSITE
[    20.445] (II) Initializing built-in extension DAMAGE
[    20.474] (EE) AIGLX error: dlopen of /usr/lib/i386-linux-gnu/dri/i965_dri.so failed (/usr/lib/i386-linux-gnu/dri/i965_dri.so: cannot open shared object file: No such file or directory)
[    20.474] (EE) AIGLX: reverting to software rendering
[    20.474] (II) AIGLX: Screen 0 is not DRI capable
[    20.474] (EE) AIGLX error: dlopen of /usr/lib/i386-linux-gnu/dri/swrast_dri.so failed (/usr/lib/i386-linux-gnu/dri/swrast_dri.so: cannot open shared object file: No such file or directory)
[    20.474] (EE) GLX: could not load software renderer
[    20.474] (II) GLX: no usable GL providers found for screen 0
[    20.475] (II) intel(0): Setting screen physical size to 380 x 238
[    20.615] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    20.631] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    20.631] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    20.631] (II) LoadModule: "evdev"
[    20.631] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    20.653] (II) Module evdev: vendor="X.Org Foundation"
[    20.653]     compiled for 1.11.3, module version = 2.7.0
[    20.653]     Module class: X.Org XInput Driver
[    20.653]     ABI class: X.Org XInput driver, version 16.0
[    20.653] (II) Using input driver 'evdev' for 'Power Button'
[    20.653] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    20.653] (**) Power Button: always reports core events
[    20.653] (**) evdev: Power Button: Device: "/dev/input/event1"
[    20.653] (--) evdev: Power Button: Vendor 0 Product 0x1
[    20.653] (--) evdev: Power Button: Found keys
[    20.653] (II) evdev: Power Button: Configuring as keyboard
[    20.653] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    20.653] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    20.653] (**) Option "xkb_rules" "evdev"
[    20.653] (**) Option "xkb_model" "pc105"
[    20.653] (**) Option "xkb_layout" "us"
[    20.654] (II) config/udev: Adding input device Video Bus (/dev/input/event5)
[    20.654] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    20.654] (II) Using input driver 'evdev' for 'Video Bus'
[    20.654] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    20.655] (**) Video Bus: always reports core events
[    20.655] (**) evdev: Video Bus: Device: "/dev/input/event5"
[    20.655] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    20.655] (--) evdev: Video Bus: Found keys
[    20.655] (II) evdev: Video Bus: Configuring as keyboard
[    20.655] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input8/event5"
[    20.655] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[    20.655] (**) Option "xkb_rules" "evdev"
[    20.655] (**) Option "xkb_model" "pc105"
[    20.655] (**) Option "xkb_layout" "us"
[    20.656] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    20.656] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    20.656] (II) Using input driver 'evdev' for 'Power Button'
[    20.656] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    20.656] (**) Power Button: always reports core events
[    20.656] (**) evdev: Power Button: Device: "/dev/input/event0"
[    20.656] (--) evdev: Power Button: Vendor 0 Product 0x1
[    20.656] (--) evdev: Power Button: Found keys
[    20.656] (II) evdev: Power Button: Configuring as keyboard
[    20.656] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    20.656] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 8)
[    20.656] (**) Option "xkb_rules" "evdev"
[    20.656] (**) Option "xkb_model" "pc105"
[    20.656] (**) Option "xkb_layout" "us"
[    20.657] (II) config/udev: Adding input device PixArt USB Optical Mouse (/dev/input/event2)
[    20.658] (**) PixArt USB Optical Mouse: Applying InputClass "evdev pointer catchall"
[    20.658] (II) Using input driver 'evdev' for 'PixArt USB Optical Mouse'
[    20.658] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    20.658] (**) PixArt USB Optical Mouse: always reports core events
[    20.658] (**) evdev: PixArt USB Optical Mouse: Device: "/dev/input/event2"
[    20.658] (--) evdev: PixArt USB Optical Mouse: Vendor 0x461 Product 0x4d0f
[    20.658] (--) evdev: PixArt USB Optical Mouse: Found 3 mouse buttons
[    20.658] (--) evdev: PixArt USB Optical Mouse: Found scroll wheel(s)
[    20.658] (--) evdev: PixArt USB Optical Mouse: Found relative axes
[    20.658] (--) evdev: PixArt USB Optical Mouse: Found x and y relative axes
[    20.658] (II) evdev: PixArt USB Optical Mouse: Configuring as mouse
[    20.658] (II) evdev: PixArt USB Optical Mouse: Adding scrollwheel support
[    20.658] (**) evdev: PixArt USB Optical Mouse: YAxisMapping: buttons 4 and 5
[    20.658] (**) evdev: PixArt USB Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    20.658] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1:1.0/input/input4/event2"
[    20.658] (II) XINPUT: Adding extended input device "PixArt USB Optical Mouse" (type: MOUSE, id 9)
[    20.658] (II) evdev: PixArt USB Optical Mouse: initialized for relative axes.
[    20.658] (**) PixArt USB Optical Mouse: (accel) keeping acceleration scheme 1
[    20.658] (**) PixArt USB Optical Mouse: (accel) acceleration profile 0
[    20.658] (**) PixArt USB Optical Mouse: (accel) acceleration factor: 2.000
[    20.658] (**) PixArt USB Optical Mouse: (accel) acceleration threshold: 4
[    20.659] (II) config/udev: Adding input device PixArt USB Optical Mouse (/dev/input/mouse0)
[    20.659] (II) No input driver specified, ignoring this device.
[    20.659] (II) This device may have been added with another device file.
[    20.659] (II) config/udev: Adding input device HDA Intel Line (/dev/input/event8)
[    20.659] (II) No input driver specified, ignoring this device.
[    20.660] (II) This device may have been added with another device file.
[    20.660] (II) config/udev: Adding input device HDA Intel Line Out (/dev/input/event7)
[    20.660] (II) No input driver specified, ignoring this device.
[    20.660] (II) This device may have been added with another device file.
[    20.661] (II) config/udev: Adding input device HDA Intel Front Headphone (/dev/input/event6)
[    20.661] (II) No input driver specified, ignoring this device.
[    20.661] (II) This device may have been added with another device file.
[    20.661] (II) config/udev: Adding input device HDA Intel Mic (/dev/input/event9)
[    20.661] (II) No input driver specified, ignoring this device.
[    20.661] (II) This device may have been added with another device file.
[    20.662] (II) config/udev: Adding input device DELL Dell USB Entry Keyboard (/dev/input/event3)
[    20.662] (**) DELL Dell USB Entry Keyboard: Applying InputClass "evdev keyboard catchall"
[    20.662] (II) Using input driver 'evdev' for 'DELL Dell USB Entry Keyboard'
[    20.662] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    20.662] (**) DELL Dell USB Entry Keyboard: always reports core events
[    20.662] (**) evdev: DELL Dell USB Entry Keyboard: Device: "/dev/input/event3"
[    20.662] (--) evdev: DELL Dell USB Entry Keyboard: Vendor 0x413c Product 0x2107
[    20.662] (--) evdev: DELL Dell USB Entry Keyboard: Found keys
[    20.662] (II) evdev: DELL Dell USB Entry Keyboard: Configuring as keyboard
[    20.662] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.1/usb6/6-1/6-1:1.0/input/input5/event3"
[    20.662] (II) XINPUT: Adding extended input device "DELL Dell USB Entry Keyboard" (type: KEYBOARD, id 10)
[    20.662] (**) Option "xkb_rules" "evdev"
[    20.662] (**) Option "xkb_model" "pc105"
[    20.662] (**) Option "xkb_layout" "us"
[    20.667] (II) config/udev: Adding input device HP WMI hotkeys (/dev/input/event4)
[    20.667] (**) HP WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[    20.667] (II) Using input driver 'evdev' for 'HP WMI hotkeys'
[    20.667] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    20.667] (**) HP WMI hotkeys: always reports core events
[    20.667] (**) evdev: HP WMI hotkeys: Device: "/dev/input/event4"
[    20.667] (--) evdev: HP WMI hotkeys: Vendor 0 Product 0
[    20.667] (--) evdev: HP WMI hotkeys: Found keys
[    20.667] (II) evdev: HP WMI hotkeys: Configuring as keyboard
[    20.667] (**) Option "config_info" "udev:/sys/devices/virtual/input/input6/event4"
[    20.667] (II) XINPUT: Adding extended input device "HP WMI hotkeys" (type: KEYBOARD, id 11)
[    20.667] (**) Option "xkb_rules" "evdev"
[    20.667] (**) Option "xkb_model" "pc105"
[    20.667] (**) Option "xkb_layout" "us"
[    28.488] (II) intel(0): EDID vendor "DEL", prod id 41095
[    28.488] (II) intel(0): Using hsync ranges from config file
[    28.488] (II) intel(0): Using vrefresh ranges from config file
[    28.488] (II) intel(0): Printing DDC gathered Modelines:
[    28.488] (II) intel(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    28.488] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    28.488] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    28.488] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    28.488] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    28.488] (II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    28.488] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    28.488] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    28.488] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    28.488] (II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    28.488] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    28.488] (II) intel(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
[    28.488] (II) intel(0): Modeline "1280x800"x0.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz)
[    28.588] (II) intel(0): EDID vendor "DEL", prod id 41095
[    28.588] (II) intel(0): Using hsync ranges from config file
[    28.588] (II) intel(0): Using vrefresh ranges from config file
[    28.588] (II) intel(0): Printing DDC gathered Modelines:
[    28.588] (II) intel(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    28.588] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    28.588] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    28.588] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    28.588] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    28.588] (II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    28.588] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    28.588] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    28.588] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    28.588] (II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    28.588] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    28.588] (II) intel(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
[    28.588] (II) intel(0): Modeline "1280x800"x0.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz)
[    30.520] (II) XKB: reuse xkmfile /var/lib/xkb/server-06D88AAF5356C6CF875D73CED515513D3FEA00ED.xkm
[    33.420] (II) intel(0): EDID vendor "DEL", prod id 41095
[    33.420] (II) intel(0): Using hsync ranges from config file
[    33.420] (II) intel(0): Using vrefresh ranges from config file
[    33.420] (II) intel(0): Printing DDC gathered Modelines:
[    33.420] (II) intel(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    33.420] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    33.420] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    33.420] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    33.420] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    33.420] (II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    33.420] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    33.420] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    33.420] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    33.420] (II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    33.420] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    33.420] (II) intel(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
[    33.420] (II) intel(0): Modeline "1280x800"x0.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz)
[    33.520] (II) intel(0): EDID vendor "DEL", prod id 41095
[    33.520] (II) intel(0): Using hsync ranges from config file
[    33.520] (II) intel(0): Using vrefresh ranges from config file
[    33.520] (II) intel(0): Printing DDC gathered Modelines:
[    33.520] (II) intel(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    33.520] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    33.520] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    33.520] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    33.520] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    33.520] (II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    33.520] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    33.520] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    33.520] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    33.520] (II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    33.520] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    33.520] (II) intel(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
[    33.520] (II) intel(0): Modeline "1280x800"x0.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz)
[    33.620] (II) intel(0): EDID vendor "DEL", prod id 41095
[    33.620] (II) intel(0): Using hsync ranges from config file
[    33.620] (II) intel(0): Using vrefresh ranges from config file
[    33.620] (II) intel(0): Printing DDC gathered Modelines:
[    33.620] (II) intel(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    33.620] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    33.620] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    33.620] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    33.620] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    33.620] (II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    33.620] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    33.620] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    33.620] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    33.620] (II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    33.620] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    33.620] (II) intel(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
[    33.620] (II) intel(0): Modeline "1280x800"x0.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz)
[    46.579] (II) XKB: reuse xkmfile /var/lib/xkb/server-06D88AAF5356C6CF875D73CED515513D3FEA00ED.xkm
[ 38255.508] (II) evdev: Power Button: Close
[ 38255.508] (II) UnloadModule: "evdev"
[ 38255.508] (II) Unloading evdev
[ 38255.540] (II) evdev: Video Bus: Close
[ 38255.540] (II) UnloadModule: "evdev"
[ 38255.540] (II) Unloading evdev
[ 38255.580] (II) evdev: Power Button: Close
[ 38255.580] (II) UnloadModule: "evdev"
[ 38255.580] (II) Unloading evdev
[ 38255.608] (II) evdev: PixArt USB Optical Mouse: Close
[ 38255.608] (II) UnloadModule: "evdev"
[ 38255.608] (II) Unloading evdev
[ 38255.648] (II) evdev: DELL Dell USB Entry Keyboard: Close
[ 38255.654] (II) UnloadModule: "evdev"
[ 38255.654] (II) Unloading evdev
[ 38255.692] (II) evdev: HP WMI hotkeys: Close
[ 38255.692] (II) UnloadModule: "evdev"
[ 38255.692] (II) Unloading evdev
[ 38255.790]  ddxSigGiveUp: Closing log
[ 38255.790] Server terminated successfully (0). Closing log file.

---

