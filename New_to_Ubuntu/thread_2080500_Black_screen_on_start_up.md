---
title: "Black screen on start up"
date: 2012-11-04
forum: New to Ubuntu
---

### Post by DaveMouse on 2012-11-04
Hi,

Am getting black screen when booting up. Started in 11.04 but upgraded to 11.10 and am gettting same problem.

startx from terminal also results in blank screen. Think that it is linked to nvidia drivers. Have posted previously on Launchpad and followed advice but this did not work and think system is broken beyond my ability. Is the best option to download os to cd and install from this or do I need to remove existing os first?
All help appreciated and happy to provide further info.:(

---

### Post by grahammechanical on 2012-11-04
This does not tell us much:

> getting black screen when booting up

That could indicate that the computer itself is broken. It could also indicate other things depending on where in the boot process you get the black screen and what errors messages you get at the same time or just before.

You do not even say if you are dual booting and getting a boot menu. You really need to give us that extra information. We cannot see what you are seeing as you boot. You have to tell us. Otherwise we cannot help.

Regards.

---

### Post by DaveMouse on 2012-11-04
I can boot to a command line in recovery mode. 
But running startx results in a black screen. 
When I try to boot to GUI I get the purple ubuntu screen then the monitor goes black and the keyboard lights go out. 

Suspected that it may be a driver problem so typed in :
sudo apt-cache policy nvidia-current

and got

nvidia-current:
   Installed: 304.51-0ubuntu1~oneiric~xup1
   Candidate: 304.60-0ubuntu1~oneiric~xup1

Happy to provide any other info.

---

### Post by Bashing-om on 2012-11-04
DaveMouse; Hi ! Welcome to the forum .

As you can boot to the text login, agree it seems to be a graphics driver issue.
lets see what results from disabling kernel mode setting by invoking the "nomodeset" boot parameter.

boot the install to the grub menu -> top entry is highlighted-> type "e" for edit :
arrow down to the entry similar to this :linux /boot/vmlinuz-3.2.0-24-generic root=UUID=dbd69ed2-530c-4409-8f5a-a3f1ea41fc67 ro quiet splash "" :
arrow across and insert the term "nomodeset" -without the quotes- direcly after "quiet splash'  -- use a space as a delimiter. 
ctl+x to continue to boot.

If you now boot to a "degraded" GUI -> System Settings -> Additional Drivers and install the recommended driver ....

reboot ===>> All good now ?[INDENT]just try'n to help <== BDQ

[/INDENT]

---

### Post by DaveMouse on 2012-11-04
Thanks for the welcome.
Added nomodeset to the line. Then booted. From comand line I entered startx and got :
xinit: giving up
xinit: unable to connect to X server: Connection refused
xinit: server error

---

### Post by Bashing-om on 2012-11-04
in recent versions the command "startx" is no longer supported.  To start the GUI interface from the command line use the upstart conventional "```
sudo service lightdm start 
```" . This assumes that your desk top manager is lightdm.

I had expected the gui to load from the grub menu's "ctl+x" function. No ??
[INDENT]just try'n to help <== BDQ

[/INDENT]

---

### Post by DaveMouse on 2012-11-05
sudo service lightdm start
tried this in recovery mode from grub menu
Just got blank screen with cursor flashing in bottom left corner.

Tried again in non-recovery mode from grub menu
Got prompted for sudo password then got blank screen with cursor flashing halfway down left edge of screen.:(

---

### Post by Bashing-om on 2012-11-05
Welp, It is time to see what is going on...
after you log on from the text login do in terminal:
```
sudo lshw -C display
```and also:
```
lspci | grep VGA 
```1st code list hardware in regards to the monitor
2nd code list pci devices in particular graphics.

and post the results.

 Panic not. Just proceed in a calm and orderly fashion.  ==> BDQ

---

### Post by DaveMouse on 2012-11-05
*-display
       description: VGA compatible controller
       product: G86 [GeForce 8500 GT]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:fd000000-fdffffff memory:d0000000-dfffffff memor
y:fa000000-fbffffff ioport:bc00(size=128) memory:fe9e0000-fe9fffff


Output from next command to follow shortly :)

---

### Post by DaveMouse on 2012-11-05
The emoticon following size = 12 was an '8' followed by ')'.

lspci | grep VGA

01:00.0 VGA compatible controller: nVidia Corporation G86 [GeForce 8500 GT] (rev
 a1)


Hope that this helps.

---

### Post by Bashing-om on 2012-11-05
Shheeeshhh// looks to me like it should be working;
display indicates Nvidia driver module is loaded and VGA says Nvidia GEForce 8500 GT card is recognized. 
Lets see what the kernel has to say..post the output of the log file from:
```
cat /var/log/Xorg.0.log 
```I am but a one-step-at-a-time kinda guy <== BDQ

---

### Post by DaveMouse on 2012-11-05
Will take a while to type out the whole log but the last few lines look interesting:

Segmentation fault at address 0x2047d
Caught signal 11 (Segmentation fault). Server aborting

Please consult the The X.Org Foundation support 
             at [http://wiki.x.org](http://wiki.x.org)
for help.
   ddxSigGiveUp: Closing log

---

### Post by Bashing-om on 2012-11-05
Yeah the seg fault is of greater concern...

no typing output ===> use copy and paste ->place the paste content between code tags (the "#" at the top of the post)
use the same procedure to copy commands from the post to your terminal command line -preventing typo's on your part--..
please use this copy/paste procedure and post the complete /var/log/Xorg.0.log output ..

then we see what we can do about the seg fault error.
[INDENT][INDENT]try'n to help <== BDQ

[/INDENT][/INDENT]

---

### Post by DaveMouse on 2012-11-06
I'm posting from a different pc as don't know how to connect from ubuntu pc in it's present state so have to cut n paste.

(==) Using system config directory "/usr/share/X11/xorg.conf.d"
(==) No layout section. Using the first Screen section.
(==) No screen section available. Using defaults.
(**) |-->Screen "Default Screen Section" (0)
(**) |     |-->Monitor "<default monitor>"
(==) No monitor specified for screen "Default Screen Section".
Using a default monitor configuration.
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
Entry deleted from font path.
(==) FontPath set to:
/usr/share/fonts/X11/misc,
/usr/share/fonts/X11/100dpi/:unscaled,
/usr/share/fonts/X11/75dpi/:unscaled,
/usr/share/fonts/X11/Type1,
/usr/share/fonts/X11/100dpi,
/usr/share/fonts/X11/75dpi.
/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
built-ins
(==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,
/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(II) The server relies on udev to provide the list of input devices.
If no devices become available, reconfigure udev or disable AutoAddDevices.
(II) Loader magic: 0x823ada0
(II) Module ABI versions:
X.0rg ANSI C Emulation: 0.4
X.0rg Video Driver: 10.0
X.0rg XInput driver : 12.3
X.0rg Server Extension :5.0
(--) PCI:*(0:1:0:0) 10de:0421:1458:3445 rev 161, Mem @ 0xfd000000/1
6777216, 0xd0000000/268435456, 0xfa000000/33554432, I/O @ 0x0000bc00/128, BIOS @ 0x????????/131072
(II) Open ACPI successful (/var/run/acpid.socket)
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.0rg Foundation"
compiled for 1.10.4, module version = 1.0.0
Module class: X.0rg Server Extension
ABI class: X.0rg Server Extension, version 5.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.0rg Foundation"
compiled for 1.10.4, module version = 1.0.0
Module class: X.0rg Server Extension
ABI class: X.0rg Server Extension, version 5.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule:"glx"
(II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
compiled for 4.0.2, module version = 1.0.0
Module class: X.0rg Server Extension
(II) NVIDIA GLX Module  304.51  Tue Sep 18 17:58:56 PDT 2012
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.0rg Foundation"
compiled for 1.10.4, module version = 1.13.0
Module class: X.0rg Server Extension
ABI class: X.0rg Server Extension, version 5.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.0rg Foundation
compiled for 1.10.4, module version = 1.0.0
ABI class: X.0rg Server Extension, version 5.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.0rg Foundation"
compiled for 1.10.4, module version = 1.2.0
ABI class: X.0rg Server Extension, version 5.0
(II) Loading extension DRI2
(==) Matched nvidia as autoconfigured driver 0 
(==) Matched nouveau as autoconfigured driver 1
(==) Matched nv as autoconfigured driver 2
(==) Matched vesa as autoconfigured driver 3
(==) Matched fbdev as autorconfigured driver 4
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/nvidia_drv..so
(II) Module nvidia: vendor="NVIDIA Corporation"
compiled for 4.0.2, module version = 1.0.0
Module class: X.0rg Video Driver
(II) LoadModule: "nouveau"
(II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
(II) Module nouveau: vendor="X.0rg Foundation"
compiled for 1.10.1, module version = 0.0.16
Module class: X.0rg Video Driver
ABI class: X.0rg Video Driver, version 10.0
(II) LoadModule: "nv"
(WW) Warning, couldn't open module nv
(II) UnloadModule "nv"
(II) Unloading nv
(EE) Failed to load module "nv" (module does not exist, 0)
(II) LoadModule: "vesa"
(II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
(II) Module vesa: vendor="X.0rg Foundation"
compiled for 1.10.2, module version = 2.3.0
Module class: X.0rg Video Driver
ABI class: X.0rg Video Driver, version 10.0
(II) LoadModule: "fbdev"
(II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
(II) Module fbdev: vendor="X.0rg Foundation"
compiled for 1.10.0, module version = 0.4.2
ABI class: X.0rg Video Driver, version 10.0
(II) NVIDIA dlloader X Driver  304.51  Tue Sep 18 17:38:03 PDT 2012
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) NOUVEAU driver Date: Thu Mar 24 02:13:12 2011 +1000
(II) NOUVEAU driver for NVIDIA chipset families :
   RIVA TNT             (NV04)
   RIVA TNT2           (NV05)
   GeForce 256         (NV10)
   GeForce 2            (NV11, NV15)
   GeForce 4MX       (NV17, NV18)
   GeForce 3            (NV20)
   GeForce 4Ti         (NV25, NV28)
   GeForce FX          (NV3x)
   GeForce 6            (NV4x)
   GeForce 7            (G7x)
   Geforce 8             (G8x)
   GeForce GTX 200  (NVA0)
   GeForce GTX 400  (NVC0)
(II) VESA: driver for VESA chipsets: vesa
(II) FBDEV: driver for framebuffer: fbdev
(++) using VT number 7

(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.0rg Foundation"
compiled for 1.10.4, module version = 1.0.0
ABI class: X.0rg ANSI C Emulation, version 0.4
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules/libwfb.so
(II) Module wfb: vendor="X.0rg Foundation"
compiled for 1.10.4, module version = 1.0.0
ABI class: X.0rg ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) Module "ramdac" already built-in
(II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/nvidia_drv.so
(II) Loading /usr/lib/xorg/modules/libwfb.so
(II) Loading /usr/lib/xorg/modules/libfb.so
(WW) Falling back to old probe method for vesa
(WW) Falling back to old probe method for fbdev
(II) Loading sub module "fbdevhw"
(II) LoadModule: "fbdevhw"
(II) Loading /usr/lib/xorg/modules/libfbdevhw.so
(II) Module fbdevhw: vendor="X.0rg Foundation"
compiled for 1.10.4, module version = 0.0.2
ABI class: X.0rg Video Driver, version 10.0
(EE) open /dev/fb0: No such file or directory
(II) NVIDIA(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
(==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TruColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Enabling 2D acceleration
(II)   NVIDIA(GPU-0): Display (Idek Iiyama PLE2208HDS (DFP-0)) does not support
(II)   NVIDIA(GPU-0):      NVIDIA 3D Vision stereo.
(II)  NVIDIA(0): NVIDIA GPU GeForce 8500 GT (G86) at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 524288 kBytes
(--) NVIDIA(0): VideoBIOS: 60.86.50.00.00
(II) NVIDIA(0): Detected PCI Express Link width:16X
(--) NVIDIA(0): Interlaced video modules are supported on this GPU
(--) NVIDIA(0): Valid display device(s) on GeForce 8500 GT at PCI:1:0:0
(--) NVIDIA(0):      CRT-0
(--) NVIDIA(0):      CRT-1
(--) NVIDIA(0):      TV-0
(--) NVIDIA(0):       Idek Iiyama PLE2208HDS (DFP-0) (connected)
(--) NVIDIA(0): CRT-0: 400.0 MHz maximum pixel clock
(--) NVIDIA(0): CRT-1: 400.0 MHz maximum pixel clock
(--) NVIDIA(0): TV-0
(--) NVIDIA(0): TV encoder: (null)
(--) NVIDIA(0): Idek Iiyama PLE2208HDS (DFP-0): 330.0 MHz maximum pixel clock 
(--) NVIDIA(0): Idek Iiyama PLE2208HDS (DFP-0): Internal Dual Link TMDS
(**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
(**) NVIDIA(0):       device Idek Iiyama PLE2208HDS (DFP-0) (Using EDID
(**) NVIDIA(0):       frequencies has been enabled on all display devices.)
(==) NVIDIA(0):
(==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
(==) NVIDIA(0):       will be used as the requested mode.
(==) NVIDIA(0):
(II) NVIDIA(0):  Validated MetaModes:
(II) NVIDIA(0):       "DFP-0:nvidia-auto-select"
(II) NVIDIA(0): Virtual screen size determined to be 1920 x 1080
(--) NVIDIA(0): DPI set to (101, 101); computed from "UseEdidDpi" Xconfig
(--) NVIDIA(0):      option
(II) UnloadModule: "nouveau"
(II) Unloading nouveau
(II) UnloadModule: "vesa"
(II) Unloading vesa
(II) UnloadModule: "fbdev"
(II) Unloading fbdev
(II) UnloadModule: "fbdevhw"
(II) Unloading fbdevhw
(--) Depth 24 pixmap format is 32 bpp
(II) NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
(II) NVIDIA(0): Setting mode "DFP-0:nvidia-auto-select"
Backtrace:
    0: /usr/bin/X (xorg_backtrace+0x37) [0x80a66f7]
    1: /usr/bin/X (0x8048000+0x62b3a) [0x80aab3a]
    2: (vdso) (__kernel_rt_sigreturn+0x0)  [0xda540c]
    3: /usr/lib/i386-linux-gnu/xorg/extra-modules/nvidia_drv.so (0x7385000+0xea0e6) [0x746f0e6]
Segmentation fault at address 0x2047d ..... 


Apologies for any typos in the above but I've tried my best !

---

### Post by Bashing-om on 2012-11-06
Hey, I do not really understand what I am seeing....
3 or 4 monitors set up ? -> crt-0, crt-1, tv-0 and tv encoder (???)..
but all looks good until  "Setting mode "DFP-0:nvidia-auto-select" is done again ..why ??
then comes the segfault [memory access violation].....

lets try this and see what results:
1. remove the current Xorg file, a new one will be created upon reboot if required:
```
sudo rm /etc/X11/xorg.conf 
```2. Completely power down even to unplugging the power cord to your cpu:
3. Disconnect all monitors except the primary monitor:
4. Power back up (how far do you get ?) -> GUI ???
5. Compare the new /var/log/Xorg.0.log to the posted log -> see what has changed.
[INDENT]hope this helps to isolate <== BDQ

[/INDENT]

---

### Post by DaveMouse on 2012-11-06
Will do. Only got one monitor by the way. :)

---

### Post by DaveMouse on 2012-11-06
Getting 'No such file or directory' message.

Have run:
locate xorg.conf

which finds:
etc/X11/xorg.conf.backup
etc/X11/xorg.conf.dist_upgrade-variousdates (6 of these)
etc/X11/xorg.conf.failsafe
etc/X11/xorg.conf.nvidia-xconfig-original
 
Also various results in /usr/share/X11 directory.

---

### Post by Bashing-om on 2012-11-06
one monitor ..the log file then makes no sense at this time to me ...the question now is where are those entries concerning the other monitors coming from ???? Will see what I can come up with (look at my other system running Nvidia)

The xorg file may not exist ...no longer strictly required, but can be generated and used .

lemme look about and scratch my head, see what solutions I can come up with.
[INDENT]look'n ==> BDQ
[/INDENT]I looked on my stable Nvidia system -one monitor- no other entries for additional monitors...hummm.

---

### Post by Bashing-om on 2012-11-07
DaveMouse;
Let's see if this helps to find the reason for the mis-probe of monitors.
post the output of :
```
 xrandr
```and down  load and install this utility:
```
sudo apt-get install read-edid
```and post the output of:
```
 sudo get-edid|parse-edid
```and see if the probe matches  with xrandr or if any errors are generated.
[INDENT]lookin ==>BDQ
 
[/INDENT]

---

### Post by DaveMouse on 2012-11-07
Output from xrandr

Can't open display

---

### Post by DaveMouse on 2012-11-07
sudo get-edid|parse-edid

parse-edid: parse-edid version 2.0.0
get-edid: get-edid version 2.0.0

    Performing real mode VBE call
    Interrupt 0x10 ax=0x4f00 bx=0x0 cx=0x0
    Function supported
    Call successful

    VBE version 300
    VBE string at 0x2110 "NVIDIA"

VBE/DDC service about to be called
    Report DDC capabilities

    Performing real mode VBE call
    Interrupt 0x10 ax+0x4f15 bx=0x0 cx=0x0
    Function supported
    Call successful

    Monitor and video card combination does not support DDC1 transfers
    Monitor and video card combination supports DDC2 transfers
    0 seconds per 128 byte EDID block transfer
    Screen is not blanked during DDC transfer

Reading next EDID block

VBE/DDC service about to be called
    Read EDID
    
    Performing real mode VBE call
    Interrupt 0x10 ax=0x4f15 bx=0x1 cx=0x0
    Function supported
    Call failed

The EDID data should not be trusted as the VBE call failed
EDID claims 255 more blocks left
EDID blocks left is wrong.
Your EDID is probably invalid.
parse-edid: EDID checksum failed - data is corrupt. Continuing anyway.
parse-edid: first bytes don't match EDID version 1 header
parse-edid: do not trust output (if any).

    #EDID version 255 revision 255
Section "Monitor"
    Identifier "---:ffff"
    VendorName "---"
    ModelName "---:ffff"
    # DPMS capabilities: Active off:yes  Suspend:yes  Standby:yes

    Mode    "4095x4095"     # vfreq 9.770Hz, hfreq 80.018kHz
        DotClock    655.350000
        HTimings    4095 4350 4605 8190
        VTimings    4095 4158 4221 8190
        Flags   "Interlace" "+HSync" "+VSync"
    EndMode
    Mode    "4095x4095    # vfreq 9.770Hz, hfreq 80.018kHz
        DotClock    655.350000
        HTimings    4095 4350 4605 8190
        VTimings    4095 4158 4221 8190
        Flags   "Interlace" "+HSync" "+VSync"
    EndMode   
    Mode    "4095x4095"     # vfreq 9.770Hz, hfreq 80.018kHz
        DotClock    655.350000
        HTimings    4095 4350 4605 8190
        VTimings    4095 4158 4221 8190
        Flags   "Interlace" "+HSync" "+VSync"
    EndMode
    Mode    "4095x4095    # vfreq 9.770Hz, hfreq 80.018kHz
        DotClock    655.350000
        HTimings    4095 4350 4605 8190
        VTimings    4095 4158 4221 8190
        Flags   "Interlace" "+HSync" "+VSync"
    EndMode   
EndSection

---

### Post by Bashing-om on 2012-11-07
can't open display !!!!Whooee// xrandr does not "see" the monitor ! X server probing->
That could explain the numerous entries for a monitor in the log file..

check your pins at each end of the monitor cable, and if at all possible take that cable to another system and see if the cable is good. Then I would swap out the monitor with a known good one( monitors do die ).
[INDENT]we will see what we will see <== BDQ

[/INDENT]

---

### Post by DaveMouse on 2012-11-08
Have used suspect monitor & cable on another pc and they are fine. Have used different, working, cable & monitor on suspect pc and did not make any difference.
So the issue is not with the cable or monitor :(

---

### Post by Bashing-om on 2012-11-08
All not to the good though..
> 
    Performing real mode VBE call
    Interrupt 0x10 ax=0x4f15 bx=0x1 cx=0x0
    Function supported
    Call failed

The EDID data should not be trusted as the VBE call failed
EDID claims 255 more blocks left
EDID blocks left is wrong.
Your EDID is probably invalid.
parse-edid: EDID checksum failed - data is corrupt. Continuing anyway.
parse-edid: first bytes don't match EDID version 1 header
parse-edid: do not trust output (if any).
says there is a serious problem...May be able to work around it by using the Xorg.conf file; I am weak in this area.. I am aware will have to exercise some degree of caution NOT to over amp the monitor...and at this time I am not too sure how to obtain good/valid data to set the resolution and frequency. 

I have ran across an example Xorg.conf file that should get you up with some GUI at a reasonable resolution...will probably take some additional "tweaking" to optimize it.
It will take me a bit of time to find that one I want again....back to look'n -> as I would not trust what the system generated Xorg.conf file would be.

Also, I remain highly disturbed that xrandr does not see the display.
[INDENT]I'll be back ==> BDQ

[/INDENT]

---

### Post by Bashing-om on 2012-11-09
status update: still looking, have not found a template I am comfortable with.

---

### Post by DaveMouse on 2012-11-10
Thanks for the update, really appreciate your help :)

---

### Post by NikTh on 2012-11-10
Hi , 

have you tried to remove completely the nvidia-driver ? Maybe this driver is incompatible with your card.

Boot from recovery mode and give these commands (you will need an active Internet connection).

First **remove the X - Swat ppa** and revert the packages to original state please. 
```
sudo apt-get install ppa-purge
sudo ppa-purge ppa:ubuntu-x-swat/x-updates
sudo apt-get update ; sudo apt-get upgrade
```

**Remove nvidia driver completely and try to use nouveau** (open source nvidia driver)
```
sudo apt-get remove --purge nvidia-*
sudo apt-get install ubuntu-desktop nvidia-common
sudo apt-get install --reinstall xserver-xorg-video-nouveau
sudo dpkg-reconfigure xserver-xorg
echo 'nouveau' | sudo tee -a /etc/modules
sudo reboot
```

Thanks

---

### Post by HiImTye on 2012-11-10
```
apt-cache policy linux-headers-generic
```should output something with an 'Installed: ' line. for instance:
> tye@T:~$ apt-cache policy linux-headers-generic
linux-headers-generic:
  Installed: 3.5.0.18.21
  Candidate: 3.5.0.18.21
  Version table:
 *** 3.5.0.18.21 0
        500 [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) quantal-updates/main amd64 Packages
        100 /var/lib/dpkg/status
     3.5.0.17.19 0
        500 [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) quantal/main amd64 Packages
it it doesn't, then
```
sudo apt-get install linux-headers-generic; sudo apt-get install --reinstall nvidia-current
```

---

### Post by Bashing-om on 2012-11-11
@DaveMouse;
I am back and found the "xorg.conf" template I was seeking. Before proceeding-> I have a great deal of respect for NikTh's knowledge, skills and ability: have you tried his advise ?
On a similar note see what results from the advise of HiImTye.

@NikTh; Please to advise/educate me. As I understand it ...both get-edid and xrandr are properties of the Xserver, how does this relate with a driver/card incompatibility as edid probes the monitor for data and gets a failed response, and xrandr does not see the display.
[INDENT]I await responses ==> BDQ

[/INDENT]

---

### Post by DaveMouse on 2012-11-12
Have tried Nikth advice and got Ubuntu 11.10 purple splash screen with following text   [  9.573069] [drm] nouveau 0000:01:00.0: Mthd 0x0088 Data 0x00fe0000 (0x0000 0x07)


The text is in orange as are the last 3 dots following Ubuntu 11.10.

---

### Post by DaveMouse on 2012-11-12
When pressing ctl alt dlt the text changes to white and says:
[FONT=&quot][   13.264618] [drm] nouveau 0000:01:00.0: EvoCh 0 Mthd 0x0088 Data 0x00fe0000 (0x0000 0x07)

Tried again and message is same but first block says:
[/FONT][FONT=&quot][   13.123560]
then
[/FONT][FONT=&quot][   12.913971]
then
[/FONT][FONT=&quot][   13.175685][/FONT]
then 
[FONT=&quot][   13.304682]
then 
[/FONT]  [   13.140542]
  
Can't even get command line now as it seems to be hanging :(
[FONT=&quot]
[/FONT]

---

### Post by Bashing-om on 2012-11-12
drm=direct rendering mode in reference to the driver  nouveau ..the error tells us what is going on ..I wish I could read it ! 
-Any advise is welcome-

Let's see if the driver is loaded, if you can get "recovery mode" from the grub menu;
terminal code :
```
sudo lshw -C display 
```While we are awaiting for NikTh's response I propose to continue setting up the xorg.conf file. To set up the modlines for hardcoding ...will require your display's name and model and use the "cvt" tool to generate the needed modlines (seeing as how xrandr is not available).
[INDENT]we are trying to get there <== BDQ

[/INDENT]

---

### Post by DaveMouse on 2012-11-12
Looks like I can only boot up to command line with last kernel in the list.
Ubuntu 11.10, kernel 2.6.27-17-generic (recovery mode)
Code
lshw -C display

*-display UNCLAIMED
     description: VGA compatible controller
     product: G86 [GeForce 8500 GT]
     vendor: nVidia Corporation
     physical id: 0
     bus info: pci@0000:01:00.0
     version: a1
     width: 64 bits
     clock: 33MHz
     capabilities: pm msi pciexpress vga_controller bus_master cap_list
     configuration: latency=0
     resources: memory:fd000000-fdffffff memory:d0000000-dfffffff(prefectchable
) memory:fa000000-fbffffff ioport:bc00(size=128) memory:fe9e0000-fe9fffff(prefet
chable)

---

### Post by Bashing-om on 2012-11-12
Yuk, the driver failed to load... let's try and see why it does not load.
1. Does the file /etc/X11/xorg.conf exist ?
2.Is all the Nvidia files removed ?[INDENT]```
sudo apt-cache policy nvidia-current
sudo apt-cache policy nvidia*
 
```[/INDENT]3. Is the module listed in /etc/modules ?[INDENT]```
cat /etc/modules
```[/INDENT]///
Will re-focus on booting the latest kernel when we have a graphics driver in-place.
[INDENT]where there is a will, there is a way <== BDQ

[/INDENT]

---

### Post by DaveMouse on 2012-11-13
sudo apt-cache policy nvidia-current
output:

nvidia-current:
 Installed: (none)
 Candidate: 280.13-0ubuntu6.2
 Version table:
    280.13-0ubuntu.2.0
       500 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) oneiric-updates/restricted i386
 Packages
       500 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) oneiric-security/restricted i386
Packages
     280.13-0ubuntu6 0
       500 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) oneiric/restricted i386 Packages
     
sudo apt-cache policy nvidia*
Probably take me all night to type the output, please let me know if full output is required, but key part is lots of entries saying:
Installed: (none)
Candidate: (none)
Version table: 

cat /etc/modules 
output:

#This file contains the names of kernel modules that should be loaded
#at boot time, one per line. Lines beginning with "#" are ignored.

lp
sbp2
nouveau

Thanks again.

---

### Post by Bashing-om on 2012-11-13
Dave, I do not comprehend why the open source module did not load. All looks clear ! Let's see if we can force it to load:
```
sudo modprobe[FONT=&quot] -v nouveau[/FONT] 
```(lower case "v")

what happens now ? <== BDQ

---

### Post by DaveMouse on 2012-11-13
WARNING@ All config files need .conf: /etc/modprobe/.d/blacklist.conf.backup, it 
will be ignored in a future release.
FATAL: Module nouveau not found.

---

### Post by DaveMouse on 2012-11-13
Slight correction:

WARNING: All config files need .conf: /etc/modprobe.d/blacklist.conf.backup, it will be ignored in a future release.
FATAL: Module nouveau not found.

---

### Post by Bashing-om on 2012-11-13
All I can figure is that when the Nvidia driver was installed, the Nvidia installer blacklisted the open source driver. See if in fact the  "Module nouveau" is indeed in either 
 /etc/modprobe.d/blacklist.conf.backup or  /etc/modprobe.d/blacklist.conf
code:
```
cat /etc/modprobe.d/blacklist.conf.backup
 cat /etc/modprobe.d/blacklist.conf
 
```if so will require editing the files to remove the entries.
```
gksudo gedit /etc/modprobe.d/blacklist.conf.backup
gksudo gedit /etc/modprobe.d/blacklist.conf
 
```note: "gksudo" for graphical application to use "sudo" authority.

are we there yet ? ==> BDQ

---

### Post by DaveMouse on 2012-11-13
Nouveau not blacklisted in either of the files. :(

---

### Post by Bashing-om on 2012-11-13
dave, I am drawing a blank right now... I lookied also on my system (radeon) for a nouveau driver ---expecting to find it in /sys/module/. Does not exist on my system either.

ok ...lemme look about and see what it is going to take to install the open source driver nouveau. ( to see if it sees your display ?)

```
sudo apt-get install xserver-xorg-video-nouveau
```What does this get you ? 
in the mean time I am looking at :
[https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection?action=show&redirect=X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem%3a__Need_to_fully_remove_-nvidia_and_reinstall_-nouveau_from_scratch](https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection?action=show&redirect=X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem%3a__Need_to_fully_remove_-nvidia_and_reinstall_-nouveau_from_scratch)
[INDENT]maybe tomorrow before I am done with that: BDQ

[/INDENT]

---

### Post by NikTh on 2012-11-14
> **Bashing-om said:**
> @NikTh; Please to advise/educate me. As I understand it ...both get-edid and xrandr are properties of the Xserver, how does this relate with a driver/card incompatibility as edid probes the monitor for data and gets a failed response, and xrandr does not see the display.

Lot of bugs are out there. The things are not so easy to resolve , when multiple programs involved. An incompatibility of the driver with the card could exists due to graphics driver bug  (closed source = nvidia's responsibility). X-server can be corrupted if the driver not read correct the card or the module cannot be loaded due to kernel's fault. 
> **DaveMouse said:**
> Looks like I can only boot up to command line with last kernel in the list.
Ubuntu 11.10, kernel 2.6.27-17-generic (recovery mode)

Something is not right here. 
Ubuntu 11.10 has not the 2.6 kernel , but 3.0-xxx kernel. 
Have you tried to boot from the 3.xxxx kernel  in recovery mode ? 

We can try to see if this is a fault of display manager (lightdm) with bellow 
**Install another display manager**
```
sudo apt-get install gdm
```**Configure the X to use this display manager**
```
sudo dpkg-reconfigure gdm
```and choose gdm for display manager . [ARROW] keys to select , [ENTER] to confirm.

Then do , 
```
sudo service lightdm stop 
sudo dpkg --confiugre -a
sudo service gdm start
```Working ? 

Also we can examine some log files for errors .
```
cat /var/log/Xorg.0.log | grep -e EE -e WW
sudo cat /var/log/lightdm/lightdm.log
sudo cat /var/log/lightdm/x-0-greeter.log
```Thanks

---

### Post by DaveMouse on 2012-11-14
Code:
sudo apt-get install xserver-xorg-video-nouveau

output:
xserver-xorg-video-nouveau is already the newest version

---

### Post by DaveMouse on 2012-11-14
gdm got me to GUI log on screen but keyboard & mouse don't do anything so can't go any further. 
I'll look at the logs that you suggested.

---

### Post by DaveMouse on 2012-11-14
Tried to boot normally (not from grub) but still blank screen), then went back to grub.

cat /var/log/Xorg.0.log | grep -e EE -e WW

output:
(WW) The directory "usr/share/fonts/X11/cryllic" does not exist.
(II) Loading extension MIT-SCREEN-SAVER
(ww) Warning, couldn't open module nvidia
(EE) Failed to load module "nvidia" (module does not exist, 0)
(II) Loading extension MIT-SCREEN-SAVER
(ww) Warning, couldn't open module nv
(EE) Failed to load module "nv" (module does not exist, 0)
(WW) Falling back to old probe method for vesa
(WW) Falling back to old proble method for fbdev

sudo cat /var/log/lightdm/lightdm.log

output: (all DEBUG):
Logging to /var/log/lightdm/lightdm.log
Starting Light Display Manager 1.0.6, UID=0 PID=4960
Loaded configuration from /etc/lightdm/lightdm.conf
Using D-Bus name org.freedesktop.DisplayManager
Registered seat module xlocal
Registered seat module xremote
Adding default seat
Starting seat
Starting new display for greeter
Starting local X display
Using VT 7
Activating VT 7
Logging to /var/log/lightdm/x-0.log
Writing X server authority to /var/run/lightdm/root/:0
Launching X Server
Launching process 4997: /usr/bin/X :0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
Waiting for ready signal from X server :0
Acquired bus name org.freedesktop.DisplayManager
Registering seat with bus path /org/freedesktop/DislayManager/Seat0
Got signal 10 from process 4997
Got signal from X server :0
Connecting to XServer :0
Error connecting to XServer :0
Process 4997 exited with return value 0
X server stopped
Removing X server authority /var/run/lightdm/root/:0
Releasing VT 7
Display server stopped
Stopping display
Display stopped
Stopping X local seat, failed to start a display
Stopping seat
Seat stopped
Stopping lightdm, required seat has stopped
Stopping display manager
Display manager stopped
Stopping Light Display Manager

sudo cat /var/log/lightdm/x-0-greeter.log

output: command not found (sure I've entered it correctly!)

---

### Post by Bashing-om on 2012-11-14
Ok ,,,this is getting deep and over my head ..

Consider NikTh's view of Xserver possibly corrupted ?
Conditions:[INDENT]*-video-nouveau latest version installed -> not loading
GDM -> keyboard and mouse unresponsive
Why is Nvidia still attempting to load with all related files removed ?
why "can not open ""nv""" (fall back) ?
XServer is seen but "cannot connect" !
(assume) EDID-read still fails.
(assume) xrandr still not seeing the display device. 

[/INDENT]Nothing done to this time do I perceive with a positive effect. I can appreciate it as a learning experience, but now I am stalled for any ideas to further trouble shoot.

For now -just a thought- How much trouble would it be to (re)install from scratch ,, new .iso file and new burn ? Start all over with a clean slate ????[INDENT]Thoughts ? 

[/INDENT]

---

### Post by DaveMouse on 2012-11-14
Yes, I did mention a complete reinstall in my original post. I'm happy to try that if it is the best option. It's certainly been a learning experience for me also!

---

### Post by Bashing-om on 2012-11-14
That is an option however, I would appreciate NikTh's input, and additional advise, selfishly for my edification. It just hurts to put forth an effort only to be stonewalled by my ignorance !
[INDENT]still learning after all these years ==> BDQ

[/INDENT]

---

### Post by NikTh on 2012-11-15
> **DaveMouse said:**
> 

sudo cat /var/log/lightdm/x-0-greeter.log

output: command not found (sure I've entered it correctly!)

Maybe the output was "file not found" , because command is correct 100%. Cat command exists , but there is a case where we activated gdm and lightdm greeter has not any logs to keep because is not running. 

You can try these commands from console mode (no Display Manager should be running)

```
sudo service gdm stop
sudo apt-get autoremove --purge nvidia-* 
sudo apt-get install ubuntu-desktop
sudo apt-get install --reinstall xserver-xorg xserver-xorg-video-all xserver-xorg-video-nouveau gsettings-desktop-schemas
sudo rm /etc/X11/xorg.conf
sudo X --configure 
sudo mv xorg.conf.new /etc/X11/xorg.conf
sudo dpkg-reconfigure xserver-xorg
sudo reboot
```Remove any deprecated file inside /etc/modprobe.d/ 
all files must end with .conf , if you see any file without .conf at the end , remove it , is deprecated and useless. 

Waiting for results. 
Thanks

---

### Post by DaveMouse on 2012-11-15
code
sudo rm /etc/X11/xorg.conf
output:
cannot remove '/etc/X11/xorg.conf': No such file or directory

code
sudo X --configure
output:
Unrecognized option: --configure

Have stopped there as assume following commands are dependant on previous ones?

---

### Post by NikTh on 2012-11-15
> **DaveMouse said:**
> 
code
sudo X --configure
output:
Unrecognized option: --configure

Have stopped there as assume following commands are dependant on previous ones?

Try with one dash 
```
sudo X -configure
``` 

The xorg.conf file is OK , if not exist , not removed.

---

### Post by DaveMouse on 2012-11-15
Yes, one dash works.

code
sudo X -configure
output: List of video drivers, will provide if required, followed by 


(EE) Failed to load module "vmwgfx" (module does not exist, 0)
(EE) vmware: Please ignore the above warnings about not being able to load module/driver vmwgfx
(EE) vmware: Unexpected failure while loading the "vmwlegacy" driver. Giving up.
(EE) Failed to load module "vmware" (a required submodule could not be loaded, 134912947)
(++) Using config file: "/root/xorg.conf.new"
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
(EE) [drm] No DRICreatePCIBusID symbol
(EE) open /dev/fb0: No such file or directory
Number of created screens does not match number of detected devices.
  Configuration failed.
 ddxSigGiveUp: Closing log

---

### Post by NikTh on 2012-11-15
Hi,
Have you tried the rest of commands ? Have you rebooted ? 
:)

---

### Post by DaveMouse on 2012-11-16
Have executed other commands including reboot.

Reboot gives purple screen displaying Ubuntu 11.10 with 4 dots (the first one is a different colour).
There is text on the screen:
[    13.340809] [drm] nouveau 0000:01:00.0 EvoCh 0 Mthd 0x0088 Data 0x00fe0000 (0x0000 0x07)

Text dissapears after a couple of minutes leaving black screen. Lights on keyboard are not working at this point. :(

---

### Post by NikTh on 2012-11-16
OK , 
last effort (by me). 

Be careful and execute the commands with order. 
```
sudo apt-get purge xserver-xorg-video-nouveau 
echo 'blacklist nouveau' | sudo tee -a /etc/modprobe.d/blacklist.conf
sudo apt-get install linux-source linux-headers-generic 
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update ; sudo apt-get dist-upgrade
sudo apt-get install nvidia-current nvidia-settings 
echo 'nvidia' | sudo tee -a /etc/modules
``` 

Reboot. 

If above not working , sorry but I haven't any other suggestion. Only to boot from a LiveCD-USB and collect your important data , copy to an external HDD and install from scratch and I suggest [Ubuntu 12.04 LTS](http://releases.ubuntu.com/precise/) this time. 

Thanks

---

### Post by Bashing-om on 2012-11-16
no input: just advisory -> I continue to try and keep up.

[INDENT][INDENT]BDQ
[/INDENT][/INDENT]

---

### Post by DaveMouse on 2012-11-17
Have executed all the suggested commands and am getting similar [drm] error to last time.
Guess it's time to reinstall. 

Do I need to remove anything prior to the install? 
Really appreciate all of your help & time guys. I've learned a lot and hopefully will have everything up and running later today. :)

---

### Post by Bashing-om on 2012-11-17
It is possible I am out in left field.... but, I look at it like unto this:
If Xorg and XServer are possibly corrupt, What else is corrupt ???
Now we could  (re)install both on this install, but in my humblest opinion would be quicker- and I would have greater confidence in my operating system- with a new install.
(verify the md5sum of a new .iso)

That said, I remain completely open to a continued learning experience; Trouble shoot this fault to resolution. (in spite of all my errors and faults!)
[INDENT]'nuff said, what do yall want to do ? <-== BDQ

[/INDENT]

---

### Post by DaveMouse on 2012-11-17
Just some background that may help. I was on 11.04 and all was well until one day problem occurred. Darling daughter left usb in pc after charging ipod and have heard that that can cause problems but don't know if this is genuine or not. 
Upgraded to 11.10 from command line in hope that this would fix problem but it did not. 
Open to suggestions but really appreciate the help that I am getting from people on this forum.

---

### Post by Bashing-om on 2012-11-18
In reference to the "charging a ipod" with usb in use, maybe undesired charge into the system; unable to advise what effects that might have had.

However, it appears the only issue is graphics related.
1. Can you boot up to the gui with the liveCD in "try" mode ? Is the "nomodeset" option in "try" mode required ? Does any of the other options in "try" mode have any affect ?
2. Food for thought: -> My system utilizes a real cheap ($15) graphics card (ATI)..Works very well for what I need/want (no intensive graphic applications used). Might consider swapping that graphics card out with a cheap card and see if that points to a resolution.

Thought process: If the system boots up in try mode-> config situation in the install; else looking more and more like a hardware problem.

[INDENT]I remain open to suggestions ==> BDQ

[/INDENT]

---

### Post by DaveMouse on 2012-11-21
I've got 12.04 on a USB but am struggling to find step by step instructions on how to install from it. Would appreciate any help to get my system up and running again :)

---

### Post by Bashing-om on 2012-11-21
dave; Good.
Never done it myself..but, these guides should suffice:
[http://ubuntuforums.org/showthread.php?t=2042965](http://ubuntuforums.org/showthread.php?t=2042965)
[http://www.ubuntu.com/download/help/create-a-usb-stick-on-ubuntu](http://www.ubuntu.com/download/help/create-a-usb-stick-on-ubuntu)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[INDENT]hth <== BDQ

[/INDENT]

---

### Post by NikTh on 2012-11-21
If you stuck somewhere in progress , we are here. I'm watching this thread :) 

Answer Bashing-Om gave is good. 
Have a little read and we are here for further help. 

Thanks

---

### Post by DaveMouse on 2012-11-21
Problem I am having is when I put the usb stick in pc port then it doesn't boot up from it. Think that I need to edit grub menu to default to usb port but I don't know the code for this.

---

### Post by windscape on 2012-11-21
You have to configure the PC to boot from the USB drive. Different PCs have different keys to press during boot to either go into the BIOS setup or display the boot menu. It could be Delete, F1, F10, F12, Esc, or something else. Look at the initial text on the screen when rebooting the PC and it usually says what key to press to go into the BIOS setup or display the boot menu. If we knew the manufacturer and model of your PC, that would help.

---

### Post by Bashing-om on 2012-11-21
not ever booting from usb I am at a disadvantage, my response is limited to what little knowledge I have:
When you initially installed ubuntu, you had a choice as to where to place grub, Default is the first hard drive, bet grub was installed there. What ya want (perhaps ?) is grub installed onto the usb device.
See if this link helps :
[https://help.ubuntu.com/community/Grub2/Troubleshooting](https://help.ubuntu.com/community/Grub2/Troubleshooting)

As I do not know how you want to set your system up, this is the best I can do at this time.
Setting grub up where required is no great big deal, but is dependent on system configuration.
[INDENT][INDENT][INDENT]hth <==BDQ

[/INDENT][/INDENT][/INDENT]

---

### Post by DaveMouse on 2012-11-21
pc is asus v3 p5g33 
esc takes me into boot menu but don't know how, or what, to add to it :(

---

### Post by windscape on 2012-11-21
With your USB drive connected, in the boot menu, is there an option for USB device or USB HDD, or something with USB in the name? If there is, then arrow down to that option, hit Enter, and see if Ubuntu starts from the USB drive.

---

### Post by DaveMouse on 2012-11-21
Hi Windscape, no I've tried that and there is no usb entry. Presumably, I need to edit the file containing the menu entries?

---

### Post by Bashing-om on 2012-11-21
dave;
If your last was in reference to the "menu entry" in bios, no can change, only select the available options.
If in regards to the grub menu, no changes at this time, have to get grub installed where bios/bootloading can find it. Again as I do not know how your system is configured and do not know how usb install works, not much else I can add presently.
except:
booting from hard drive with ubuntu installed on hard drive-> grub sda, bios set to boot from hard drive
booting from usb with ubuntu installed anywhere -> grub on usb device ...can only boot then if usb device is connected and grub is installed on usb --> bios set to boot from usb.
[INDENT][INDENT]still try'n to help <== BDQ

[/INDENT][/INDENT]

---

### Post by NikTh on 2012-11-22
Hi , 

your computer's manual is here : [http://support.asus.com/download.aspx?SLanguage=en&p=8&s=15&m=V3-P5G33&os=25&hashedid=biwC5cR1KFeHkbEL](http://support.asus.com/download.aspx?SLanguage=en&p=8&s=15&m=V3-P5G33&os=25&hashedid=biwC5cR1KFeHkbEL)

I downloaded the manual and I've searched for USB boot support , but I think this computer supports USB flash boot only if you want to update the BIOS. 

If you don't have the abillity to boot from USB-Flash , hmmm then you have another problem. 
The easiest way is to burn a CD of Ubuntu 12.04 and boot from there to install Ubuntu. 

Here is the BIOS configuration page => Boot section

---

### Post by DaveMouse on 2012-11-24
Hi,
I have got 12.04 on dvd but am not sure if I have done it correctly.
File I have on dvd is 'ubuntu-12.04.1-dvd-amd64.iso' in winzip format.
Could somebody please clarify if this is correct, apologies for my ignorance.

---

### Post by NikTh on 2012-11-24
> **DaveMouse said:**
> Hi,
I have got 12.04 on dvd but am not sure if I have done it correctly.
File I have on dvd is 'ubuntu-12.04.1-dvd-amd64.iso' in winzip format.
Could somebody please clarify if this is correct, apologies for my ignorance.

No need to apologize . 

This iso file, you have to burn it (with a program) in the dvd to work. Is not exactly winzip format , is an iso format (image) that you should burn it to the dvd. For that you must use a program. Several programs are on the Web (free programs). 

Just search in Google with "burn iso <operating system>" tags. Where <operating system> replace it with the operating system you have access (Windows or Ubuntu(Linux)" and you will find an easy way on how to burn the iso. 
Do not forget ALWAYS to burn the iso to the lower speed.
After a successful burn the only thing you have to do, is to boot from this DVD and install Ubuntu. 

Thanks

---

### Post by DaveMouse on 2012-11-24
Thanks for your help. The file I have is winzip format. Do I need to unzip it or do I burn the winzip file?

---

### Post by NikTh on 2012-11-24
> **DaveMouse said:**
> Thanks for your help. The file I have is winzip format. Do I need to unzip it or do I burn the winzip file?

Where did you get this file ? 
One of trusted sources to get the Ubuntu image file (iso) is here: [http://releases.ubuntu.com/precise/](http://releases.ubuntu.com/precise/)

If the file has an extension **.zip** , then probably you need to unzip it first. If the file has an extension of **.iso** , then no , just burn it as it is. 

Thanks

---

### Post by DaveMouse on 2012-11-24
I have downloaded the file twice from the link that you have posted.
Both times the file downloaded is:
ubuntu-12.04.1-dvd-amd64.iso and it is winzipped.
When I unzip it I get the following folder structure:
.disc
boot
casper
dists
efi
install
isolinux
pics
pool
preseed
also 4 stand alone files.

I'm not clear exactly what I should be burning to the DVD.

---

### Post by NikTh on 2012-11-24
> **DaveMouse said:**
> I have downloaded the file twice from the link that you have posted.
Both times the file downloaded is:
ubuntu-12.04.1-dvd-amd64.iso 

Then proceed with burning. No need to unzip anything. 
What OS you have now ? Windows or  Linux (if Linux , what distro? ) 
Read here of what an **.iso** image is : => [http://en.wikipedia.org/wiki/ISO_image](http://en.wikipedia.org/wiki/ISO_image)

Thanks

---

### Post by DaveMouse on 2012-11-25
Ok, I have the dvd burned. So now I need to work out how to update the bios to boot from cd drive. I can't see anything obvious on start up to give me a clue with this. I'll go through the manual, hopefully there will be something in there.

---

### Post by DaveMouse on 2012-11-25
Delete takes me into the BIOS. Entries are: 1st Boot Device      [CDROM:5M-HL-DT-STD] 2nd Boot Device      [HDD:P1-SAMSUNG HD1] 3rd Boot Device      [Disabled]  On the rhs there is text saying 'A device enclosed in parenthesis has been disabled in the corresponding type menu.'  I'm wondering if this means that all of the entries are disabled or just one or two? Presumably the 1st is disabled as it is not booting from cd drive. I'm assuming that I need to locate the 'corresponding type menu' and enable this?  Onwards we go.

---

### Post by DaveMouse on 2012-11-25
I don't think that the 1st boot option (cd drive) is disabled as it is in brackets rather than parenthesis. So I'm not clear why it's not booting from cd drive as first option. I've tried pressing any key whilst booting but that does is not doing anything.

---

### Post by Noor1101 on 2012-11-25
Hi, I've been reading this thread with interest, and have learnt a lot :) But please note I'm still quite a newbie in regard to Linux. I'm just trying to help with the feeble ideas that come to mind.

**Firstly**, I'm wondering, are you sure you burned the CD the right way? Did you choose the option to "Burn image" (or "Burn .iso")? Because if you chose the option "Burn data" or something like that, the CD won't work, and the PC would thus not be able to boot from it.

I don't think you need to update your BIOS in order to boot from CD, because the CD drive does not seem to be disabled as it is listed in square brackets: [   ]  .    Parentheses =  (    )
 Booting from USB is not possible at this moment (as it isn't in the list). You need to update BIOS to do that. But I advise you to only do that if the CD really doesn't work. I've been told it's complicated. Booting from CD should be much easier. 

**Secondly**, is it possible to manually select the CD-drive in boot-menu (or "boot-order" or something alike) and hit enter to make it boot from there instantly? In my BIOS there are two options before booting: 
- enter BIOS (F2 in my case) (and navigate to Boot tab), and 
- enter Boot-order (F8 on my laptop). 
If I go to Boot order, select the location I want to boot from and hit enter, it directly goes to booting from there. Is that possible on your PC?


Good luck!


edit: where I wrote CD it obviously should have been DVD
editedit: another thought, are you sure your CD-Rom drive supports DVD's?

---

### Post by NikTh on 2012-11-25
> **DaveMouse said:**
> I don't think that the 1st boot option (cd drive) is disabled as it is in brackets rather than parenthesis. So I'm not clear why it's not booting from cd drive as first option. I've tried pressing any key whilst booting but that does is not doing anything.

Have you burned the  **.iso** at lower speed ? The lowest .. 2x . 
If not , then do it again and be careful with the speed burning. 
Thanks

---

### Post by DaveMouse on 2012-11-26
I've used InfraRecorder to burn the dvd at slowest speed (x4). 
When I try this in my Windows pc, the ubuntu prompt comes up so I assume it's ok.

Still won't boot from dvd drive so went into BIOS and manually selected CD drive and it seemed to be working, started with asking me to select default language but then screen has gone blank and cursor flashing in top left corner, cd drive light is flashing but not much happening. 

I'm thinking that my best option might be to purchase an istallation disc.

---

### Post by Bashing-om on 2012-11-26
Try this: and see what results:
Boot the install dvd;
As soon as the bios screen clears, hold down the shift key -> language screen->press the escape key ==> options screen.
At this options screen press the f6 key-> boot options; select,with the arrow key, the 'nomodeset" option and enter key to activate.
Press the f10 key to continue to boot.
Advise at this time if you boot to the desk top.
Additional advise pending.

try'n to help <== BDQ

---

### Post by DaveMouse on 2012-11-26
It seems to be struggling to read the dvd. Tries to boot from the cd and have got to the ubuntu menu and selected 'Check disc for errors' option but nothing happening other than green drive light flashing.  Have tried select option that you suggested but this does not do anything. As soon as I take the dvd out it boots from hard drive to 11.10 purple screen with [drm] error. dvd seems to work fine in Windows pc and ubuntu menu comes up with options to 'Demo and full installation' and 'Learn more'.

---

### Post by Bashing-om on 2012-11-27
A number of cuases jumps to mind.
1. Bios: When you boot from a "cold" start (from all power off condition) ..is the bios screen good and legible ? If You go into your bios "setup" options menus are all screens/options legible ?
2. DVD drive: Check it with any other boot disk (suggest at least 2 others) does it boot these disk ?
3. As the ubuntu installDVD boots up in another machine, we can safely assume that the disk is good as copied.


That leaves only 2 things:
A. Bios is corrupted
B. Disk drive is bad.

got another thing might that you might try;
disconnect the monitor (from cold), leave the monitor disconnected, try to boot up ubuntu, watch your led indicators, and when all activity had ceased, then connect the monitor....what results ? (maybe the monitor's EDID is wicked, and driving the ubuntu KMS nuts ????.....) 
[INDENT][INDENT]seeking solutions <== BDQ

[/INDENT][/INDENT]

---

### Post by DaveMouse on 2012-11-28
Bios menu looks ok. Have ordered a Live boot cd so will try that when it arrives. If that doesn't work then will fit a new drive and see if that works. Have tried with different monitors so don't think that that is the problem. Will update when boot cd arrives.
Really appreciate the help.

---

### Post by Bashing-om on 2012-11-28
Open Source, we are all in this together ! And I welcome an ocassion to learn more about my operating system of choice, Not to mention a little payback for this wonderful os.


[INDENT]it is all good, just a matter of time ==> BDQ

[/INDENT]

---

### Post by cwf1 on 2012-11-29
Similar errors running ASUS F1 board with AMD processor.. same silly failure... when we are running the SATA drives in RAID1.  When set to IDE, following install the reboot brings up the system!  We finally left the RAID1 on and went to the Server.. which will suit us better ...

---

### Post by Bashing-om on 2012-11-29
@cwf1;

Good Input, Well worth while looking in bios and checking that the modes set  agree with the hardware !

---

### Post by DaveMouse on 2012-12-12
Just got the 12.10 disk.
 Took a few minutes trying to read drive? Then got following output:


  EDD: Error 1000 reading sector 388054
  No DEFAULT or UI configuration directive found!
  boot:

---

### Post by Bashing-om on 2012-12-12
DaveMouse;

I feel for you.
All I can think of is to look at booting options in bios (is UEFI booting a factor ?, is AHCI an option ?)
OR back to a bad drive, But I do suggest to boot the disk up in another computer, verifying that the disk it's self is good.

Another thought, pae; as 12.04 and 12.10 require that the operating system support it. (I do not know what errors are generated in the event that pae is not available).

[INDENT]hth <== BDQ

[/INDENT]

---

### Post by DaveMouse on 2013-04-01
Hi again, replaced dvd drive and installed 12.10 from start up disc. System up and running but clearly still a problem with graphics card. 
Ran system test and got following failures:

graphics/compiz_check FAILED
OpenGL vendor string: VMware, Inc. OpenGL renderer string: Gallium 0.4 on llvmpipe (LLVM 0x301) OpenGL version string: 2.1 Mesa 9.0 Not software rendered: no Not blacklisted: yes GLX fbconfig: yes GLX texture from pixmap: yes GL npot or rect textures: yes Compiz supported: no 


graphics/driver_version FAILED
ERROR: No video driver loaded! Possibly in failsafe mode!

graphics/VESA_drivers_not_in_use FAILED

So tried:
sudo apt-get purge nvidia-current
sudo apt-get install nvidia-current

Then
sudo dpkg -l nvidia-current

Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
ii  nvidia-current 304.51.reall amd64        NVIDIA binary Xorg driver, kernel


It seems that I have a problem with the nvidia drivers but am not sure how to resolve it. 
Any advice much apreciated :)

---

