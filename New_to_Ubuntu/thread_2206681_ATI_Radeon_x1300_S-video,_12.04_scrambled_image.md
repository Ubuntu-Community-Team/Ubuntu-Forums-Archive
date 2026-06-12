---
title: "ATI Radeon x1300 S-video, 12.04 scrambled image"
date: 2014-02-20
forum: New to Ubuntu
---

### Post by Jeremy_Gordy on 2014-02-20
sorry if i am posting this in the wrong section.

okay so i have a desktop I'm trying to turn into a media/HTPC box for watching videos on my TV. The only connection i have available is S-video and I am having some problems with the image.

so when i boot the computer the post message shows just fine. but when i get to the loging screen the image gets all scrambled and weird. I tell when I'm at the desktop but cant read anything on it. when I installed Ubuntu 12.04 everything worked fine, and displayed clear but after rebooting and getting back to the desktop everything was all scrambled.

I know that the ati radeon 1300 is no longer supported for new versions of ubuntu, but I don't get why it worked in the install but now it has stopped working all of the sudden,

I'm going to attach some images of what it looks like through the start up process and when it looks like when the image scrambles.

any help would be greatly appreciated thanks.

---

### Post by Bashing-om on 2014-02-20
Jeremy_Gordy; Hi ! Welcome to the forum .

Yeah, most likely a graphics driver is not loading up for the GUI.
Let's look at what is:
Post back the outputs - between code tags - of terminal commands:
```

uname -r
lspci -nnk | grep -iA3 vga
sudo lshw -C display

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

Of the top of my head, I would imagine that when you installed the operating system, you checked "install 3rd party software" and perhaps the wizard tried to install the "fglrx" graphics driver (??) that no longer supports your graphics card.
While booting up a lower level graphics driver is used, then a switch is made to the driver having the additional capabilities to drive graphics. Perhaps in this case it just ain't going to happen.
Or, maybe, you upgraded the kernel to have Hardware Enablement Stack, and thus lost the support for any proprietary driver for the graphics card.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

The above outputs will tell what the situation is and we can advise on a solution.

---

### Post by Jeremy_Gordy on 2014-02-20
Thanks for the Welcome to the forum and the help.

Okay so that was a bit of a nightmare trying to get those codes with a scrambled screen but i got it :)

```
media@MediaBox-Linux:~$ uname -r
3.5.0-23-generic

media@MediaBox-Linux:~$ lspci -nnk|grep -iA3 vga
02:00.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI RV515 PRO [Radeon X1300/X1550 Series] [1002:7142]
    Subsystem: Advanced Micro Devices [AMD] nee ATI Device [1002:0302]
    Kernel driver in use: radeon
    Kernel modules: radeon

media@MediaBox-Linux:~$ sudo lshw -C display
[sudo] password for media: 
  *-display:0             
       description: VGA compatible controller
       product: RV515 PRO [Radeon X1300/X1550 Series]
       vendor: Hynix Semiconductor (Hyundai Electronics)
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:16 memory:e0000000-efffffff memory:fddf0000-fddfffff ioport:ac00(size=256) memory:fddc0000-fdddffff
  *-display:1 UNCLAIMED
       description: Display controller
       product: RV515 PRO [Radeon X1300/X1550 Series] (Secondary)
       vendor: Hynix Semiconductor (Hyundai Electronics)
       physical id: 0.1
       bus info: pci@0000:02:00.1
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress cap_list
       configuration: latency=0
       resources: memory:fdde0000-fddeffff

media@MediaBox-Linux:~$
```

p.s. I don't believe I checked to install 3rd party software and I don't mess with [COLOR=#000000]kernels, I have no idea what I'm doing when it comes to that lol.[/COLOR]

---

### Post by Bashing-om on 2014-02-20
Jeremy_Gordy; Ummphh;

Well, what I thought might be the problem is not.
These:
> 
Kernel driver in use: radeon
    Kernel modules: radeon
//
configuration: driver=radeon latency=0

say the proper driver is installed for that card !
FYI, I run that same card - on a AMD platform -, open source radeon driver, and I have absolutely no problem with it. 

Let's see if there are any problems logged by the system:
Reboot, and at the GUI login do: -> key combo ctl+alt+F1 -> terminal;
Post the output of terminal command:
```

cat /var/log/Xorg.0.log

```

To reboot once more from the commnad like:
```

sudo shutdown -r now
##to shut the system down - Power Off ##
sudo shutdown -P now

``` 

Maybe consider upgrading the kernel to the "saucy" stack ??? Maybe, currently it is only a thought.

what we have there
[INDENT][INDENT]is a failure to communicate
[/INDENT][/INDENT]

---

### Post by Jeremy_Gordy on 2014-02-20
ok well i wasn't able to use my same trick for getting the last code but i got it through SSH.

also i dont know if it matters or not but in my X11 "/etc/X11" directory i dont have a xorg.conf file?

```
login as: mediamedia@192.168.0.32's password:
Welcome to Ubuntu 12.04.2 LTS (GNU/Linux 3.5.0-23-generic x86_64)


 * Documentation:  https://help.ubuntu.com/


Last login: Thu Feb 20 17:14:02 2014 from jeremy-hp.local
media@MediaBox-Linux:~$ cat /var/log/Xorg.0.log
[    12.084]
X.Org X Server 1.13.0
Release Date: 2012-09-05
[    12.084] X Protocol Version 11, Revision 0
[    12.084] Build Operating System: Linux 2.6.42-35-generic x86_64 Ubuntu
[    12.084] Current Operating System: Linux MediaBox-Linux 3.5.0-23-generic #35~precise1-Ubuntu SMP Fri Jan 25 17:13:26 UTC 2013 x86_64
[    12.084] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.5.0-23-generic root=UUID=29323c3c-8acf-4657-b70b-2cd4ef14cc51 ro quiet splash vt.handoff=7
[    12.084] Build Date: 19 January 2013  12:37:44PM
[    12.084] xorg-server 2:1.13.0-0ubuntu6.1~precise2 (For technical support please see http://www.ubuntu.com/support)
[    12.084] Current version of pixman: 0.24.4
[    12.084]    Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
[    12.084] Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    12.084] (==) Log file: "/var/log/Xorg.0.log", Time: Thu Feb 20 17:13:23 2014
[    12.116] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    12.117] (==) No Layout section.  Using the first Screen section.
[    12.117] (==) No screen section available. Using defaults.
[    12.117] (**) |-->Screen "Default Screen Section" (0)
[    12.117] (**) |   |-->Monitor "<default monitor>"
[    12.117] (==) No monitor specified for screen "Default Screen Section".
        Using a default monitor configuration.
[    12.117] (==) Automatically adding devices
[    12.117] (==) Automatically enabling devices
[    12.117] (==) Automatically adding GPU devices
[    12.117] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    12.117]    Entry deleted from font path.
[    12.117] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    12.117]    Entry deleted from font path.
[    12.117] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    12.117]    Entry deleted from font path.
[    12.117] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    12.117]    Entry deleted from font path.
[    12.117] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    12.117]    Entry deleted from font path.
[    12.117] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    12.117]    Entry deleted from font path.
[    12.117] (==) FontPath set to:
        /usr/share/fonts/X11/misc,
        /usr/share/fonts/X11/Type1,
        built-ins
[    12.117] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    12.117] (II) The server relies on udev to provide the list of input devices.
        If no devices become available, reconfigure udev or disable AutoAddDevices.
[    12.117] (II) Loader magic: 0x7fea3e765c20
[    12.117] (II) Module ABI versions:
[    12.117]    X.Org ANSI C Emulation: 0.4
[    12.117]    X.Org Video Driver: 13.0
[    12.117]    X.Org XInput driver : 18.0
[    12.117]    X.Org Server Extension : 7.0
[    12.118] (II) config/udev: Adding drm device (/dev/dri/card0)
[    12.119] (--) PCI:*(0:2:0:0) 1002:7142:1002:0302 rev 0, Mem @ 0xe0000000/268435456, 0xfddf0000/65536, I/O @ 0x0000ac00/256, BIOS @ 0x????????/131072
[    12.119] (--) PCI: (0:2:0:1) 1002:7162:1002:0303 rev 0, Mem @ 0xfdde0000/65536
[    12.119] (II) Open ACPI successful (/var/run/acpid.socket)
[    12.119] Initializing built-in extension Generic Event Extension
[    12.119] Initializing built-in extension SHAPE
[    12.119] Initializing built-in extension MIT-SHM
[    12.119] Initializing built-in extension XInputExtension
[    12.119] Initializing built-in extension XTEST
[    12.119] Initializing built-in extension BIG-REQUESTS
[    12.119] Initializing built-in extension SYNC
[    12.119] Initializing built-in extension XKEYBOARD
[    12.119] Initializing built-in extension XC-MISC
[    12.119] Initializing built-in extension SECURITY
[    12.119] Initializing built-in extension XINERAMA
[    12.119] Initializing built-in extension XFIXES
[    12.119] Initializing built-in extension RENDER
[    12.119] Initializing built-in extension RANDR
[    12.119] Initializing built-in extension COMPOSITE
[    12.119] Initializing built-in extension DAMAGE
[    12.119] Initializing built-in extension MIT-SCREEN-SAVER
[    12.119] Initializing built-in extension DOUBLE-BUFFER
[    12.119] Initializing built-in extension RECORD
[    12.119] Initializing built-in extension DPMS
[    12.119] Initializing built-in extension X-Resource
[    12.119] Initializing built-in extension XVideo
[    12.119] Initializing built-in extension XVideo-MotionCompensation
[    12.119] Initializing built-in extension XFree86-VidModeExtension
[    12.119] Initializing built-in extension XFree86-DGA
[    12.119] Initializing built-in extension XFree86-DRI
[    12.119] Initializing built-in extension DRI2
[    12.119] (II) LoadModule: "glx"
[    12.140] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    12.140] (II) Module glx: vendor="X.Org Foundation"
[    12.140]    compiled for 1.13.0, module version = 1.0.0
[    12.140]    ABI class: X.Org Server Extension, version 7.0
[    12.140] (==) AIGLX enabled
[    12.140] Loading extension GLX
[    12.140] (==) Matched fglrx as autoconfigured driver 0
[    12.140] (==) Matched ati as autoconfigured driver 1
[    12.140] (==) Matched fglrx as autoconfigured driver 2
[    12.140] (==) Matched ati as autoconfigured driver 3
[    12.140] (==) Matched vesa as autoconfigured driver 4
[    12.140] (==) Matched modesetting as autoconfigured driver 5
[    12.140] (==) Matched fbdev as autoconfigured driver 6
[    12.140] (==) Assigned the driver to the xf86ConfigLayout
[    12.140] (II) LoadModule: "fglrx"
[    12.141] (WW) Warning, couldn't open module fglrx
[    12.141] (II) UnloadModule: "fglrx"
[    12.141] (II) Unloading fglrx
[    12.141] (EE) Failed to load module "fglrx" (module does not exist, 0)
[    12.141] (II) LoadModule: "ati"
[    12.141] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    12.141] (II) Module ati: vendor="X.Org Foundation"
[    12.141]    compiled for 1.13.0, module version = 6.99.99
[    12.141]    Module class: X.Org Video Driver
[    12.141]    ABI class: X.Org Video Driver, version 13.0
[    12.141] (II) LoadModule: "radeon"
[    12.141] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    12.142] (II) Module radeon: vendor="X.Org Foundation"
[    12.142]    compiled for 1.13.0, module version = 6.99.99
[    12.142]    Module class: X.Org Video Driver
[    12.142]    ABI class: X.Org Video Driver, version 13.0
[    12.142] (II) LoadModule: "vesa"
[    12.142] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    12.142] (II) Module vesa: vendor="X.Org Foundation"
[    12.142]    compiled for 1.13.0, module version = 2.3.2
[    12.142]    Module class: X.Org Video Driver
[    12.142]    ABI class: X.Org Video Driver, version 13.0
[    12.142] (II) LoadModule: "modesetting"
[    12.142] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    12.142] (II) Module modesetting: vendor="X.Org Foundation"
[    12.142]    compiled for 1.13.0, module version = 0.5.0
[    12.142]    Module class: X.Org Video Driver
[    12.142]    ABI class: X.Org Video Driver, version 13.0
[    12.142] (II) LoadModule: "fbdev"
[    12.142] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    12.142] (II) Module fbdev: vendor="X.Org Foundation"
[    12.142]    compiled for 1.13.0, module version = 0.4.3
[    12.142]    Module class: X.Org Video Driver
[    12.142]    ABI class: X.Org Video Driver, version 13.0
[    12.142] (==) Matched fglrx as autoconfigured driver 0
[    12.142] (==) Matched ati as autoconfigured driver 1
[    12.142] (==) Matched fglrx as autoconfigured driver 2
[    12.142] (==) Matched ati as autoconfigured driver 3
[    12.142] (==) Matched vesa as autoconfigured driver 4
[    12.142] (==) Matched modesetting as autoconfigured driver 5
[    12.142] (==) Matched fbdev as autoconfigured driver 6
[    12.142] (==) Assigned the driver to the xf86ConfigLayout
[    12.142] (II) LoadModule: "fglrx"
[    12.143] (WW) Warning, couldn't open module fglrx
[    12.143] (II) UnloadModule: "fglrx"
[    12.143] (II) Unloading fglrx
[    12.143] (EE) Failed to load module "fglrx" (module does not exist, 0)
[    12.143] (II) LoadModule: "ati"
[    12.143] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    12.143] (II) Module ati: vendor="X.Org Foundation"
[    12.143]    compiled for 1.13.0, module version = 6.99.99
[    12.143]    Module class: X.Org Video Driver
[    12.143]    ABI class: X.Org Video Driver, version 13.0
[    12.143] (II) LoadModule: "vesa"
[    12.143] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    12.143] (II) Module vesa: vendor="X.Org Foundation"
[    12.143]    compiled for 1.13.0, module version = 2.3.2
[    12.143]    Module class: X.Org Video Driver
[    12.143]    ABI class: X.Org Video Driver, version 13.0
[    12.143] (II) UnloadModule: "vesa"
[    12.143] (II) Unloading vesa
[    12.143] (II) Failed to load module "vesa" (already loaded, 0)
[    12.143] (II) LoadModule: "modesetting"
[    12.143] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    12.144] (II) Module modesetting: vendor="X.Org Foundation"
[    12.144]    compiled for 1.13.0, module version = 0.5.0
[    12.144]    Module class: X.Org Video Driver
[    12.144]    ABI class: X.Org Video Driver, version 13.0
[    12.144] (II) UnloadModule: "modesetting"
[    12.144] (II) Unloading modesetting
[    12.144] (II) Failed to load module "modesetting" (already loaded, 0)
[    12.144] (II) LoadModule: "fbdev"
[    12.144] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    12.144] (II) Module fbdev: vendor="X.Org Foundation"
[    12.144]    compiled for 1.13.0, module version = 0.4.3
[    12.144]    Module class: X.Org Video Driver
[    12.144]    ABI class: X.Org Video Driver, version 13.0
[    12.144] (II) UnloadModule: "fbdev"
[    12.144] (II) Unloading fbdev
[    12.144] (II) Failed to load module "fbdev" (already loaded, 0)
[    12.144] (II) RADEON: Driver for ATI Radeon chipsets:
        ATI Radeon Mobility X600 (M24) 3150 (PCIE), ATI FireMV 2400 (PCI),
        ATI Radeon Mobility X300 (M24) 3152 (PCIE),
        ATI FireGL M24 GL 3154 (PCIE), ATI FireMV 2400 3155 (PCI),
        ATI Radeon X600 (RV380) 3E50 (PCIE),
        ATI FireGL V3200 (RV380) 3E54 (PCIE), ATI Radeon IGP320 (A3) 4136,
        ATI Radeon IGP330/340/350 (A4) 4137, ATI Radeon 9500 AD (AGP),
        ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
        ATI FireGL Z1 AG (AGP), ATI Radeon 9800SE AH (AGP),
        ATI Radeon 9800 AI (AGP), ATI Radeon 9800 AJ (AGP),
        ATI FireGL X2 AK (AGP), ATI Radeon 9600 AP (AGP),
        ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
        ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP), ATI Radeon 9650,
        ATI FireGL RV360 AV (AGP), ATI Radeon 7000 IGP (A4+) 4237,
        ATI Radeon 8500 AIW BB (AGP), ATI Radeon IGP320M (U1) 4336,
        ATI Radeon IGP330M/340M/350M (U2) 4337,
        ATI Radeon Mobility 7000 IGP 4437, ATI Radeon 9000/PRO If (AGP/PCI),
        ATI Radeon 9000 Ig (AGP/PCI), ATI Radeon X800 (R420) JH (AGP),
        ATI Radeon X800PRO (R420) JI (AGP),
        ATI Radeon X800SE (R420) JJ (AGP), ATI Radeon X800 (R420) JK (AGP),
        ATI Radeon X800 (R420) JL (AGP), ATI FireGL X3 (R420) JM (AGP),
        ATI Radeon Mobility 9800 (M18) JN (AGP),
        ATI Radeon X800 SE (R420) (AGP), ATI Radeon X800XT (R420) JP (AGP),
        ATI Radeon X800 VE (R420) JT (AGP), ATI Radeon X850 (R480) (AGP),
        ATI Radeon X850 XT (R480) (AGP), ATI Radeon X850 SE (R480) (AGP),
        ATI Radeon X850 PRO (R480) (AGP), ATI Radeon X850 XT PE (R480) (AGP),
        ATI Radeon Mobility M7 LW (AGP),
        ATI Mobility FireGL 7800 M7 LX (AGP),
        ATI Radeon Mobility M6 LY (AGP), ATI Radeon Mobility M6 LZ (AGP),
        ATI FireGL Mobility 9000 (M9) Ld (AGP),
        ATI Radeon Mobility 9000 (M9) Lf (AGP),
        ATI Radeon Mobility 9000 (M9) Lg (AGP), ATI FireMV 2400 PCI,
        ATI Radeon 9700 Pro ND (AGP), ATI Radeon 9700/9500Pro NE (AGP),
        ATI Radeon 9600TX NF (AGP), ATI FireGL X1 NG (AGP),
        ATI Radeon 9800PRO NH (AGP), ATI Radeon 9800 NI (AGP),
        ATI FireGL X2 NK (AGP), ATI Radeon 9800XT NJ (AGP),
        ATI Radeon Mobility 9600/9700 (M10/M11) NP (AGP),
        ATI Radeon Mobility 9600 (M10) NQ (AGP),
        ATI Radeon Mobility 9600 (M11) NR (AGP),
        ATI Radeon Mobility 9600 (M10) NS (AGP),
        ATI FireGL Mobility T2 (M10) NT (AGP),
        ATI FireGL Mobility T2e (M11) NV (AGP), ATI Radeon QD (AGP),
        ATI Radeon QE (AGP), ATI Radeon QF (AGP), ATI Radeon QG (AGP),
        ATI FireGL 8700/8800 QH (AGP), ATI Radeon 8500 QL (AGP),
        ATI Radeon 9100 QM (AGP), ATI Radeon 7500 QW (AGP/PCI),
        ATI Radeon 7500 QX (AGP/PCI), ATI Radeon VE/7000 QY (AGP/PCI),
        ATI Radeon VE/7000 QZ (AGP/PCI), ATI ES1000 515E (PCI),
        ATI Radeon Mobility X300 (M22) 5460 (PCIE),
        ATI Radeon Mobility X600 SE (M24C) 5462 (PCIE),
        ATI FireGL M22 GL 5464 (PCIE), ATI Radeon X800 (R423) UH (PCIE),
        ATI Radeon X800PRO (R423) UI (PCIE),
        ATI Radeon X800LE (R423) UJ (PCIE),
        ATI Radeon X800SE (R423) UK (PCIE),
        ATI Radeon X800 XTP (R430) (PCIE), ATI Radeon X800 XL (R430) (PCIE),
        ATI Radeon X800 SE (R430) (PCIE), ATI Radeon X800 (R430) (PCIE),
        ATI FireGL V7100 (R423) (PCIE), ATI FireGL V5100 (R423) UQ (PCIE),
        ATI FireGL unknown (R423) UR (PCIE),
        ATI FireGL unknown (R423) UT (PCIE),
        ATI Mobility FireGL V5000 (M26) (PCIE),
        ATI Mobility FireGL V5000 (M26) (PCIE),
        ATI Mobility Radeon X700 XL (M26) (PCIE),
        ATI Mobility Radeon X700 (M26) (PCIE),
        ATI Mobility Radeon X700 (M26) (PCIE),
        ATI Radeon X550XTX 5657 (PCIE), ATI Radeon 9100 IGP (A5) 5834,
        ATI Radeon Mobility 9100 IGP (U3) 5835,
        ATI Radeon XPRESS 200 5954 (PCIE),
        ATI Radeon XPRESS 200M 5955 (PCIE), ATI Radeon 9250 5960 (AGP),
        ATI Radeon 9200 5961 (AGP), ATI Radeon 9200 5962 (AGP),
        ATI Radeon 9200SE 5964 (AGP), ATI FireMV 2200 (PCI),
        ATI ES1000 5969 (PCI), ATI Radeon XPRESS 200 5974 (PCIE),
        ATI Radeon XPRESS 200M 5975 (PCIE),
        ATI Radeon XPRESS 200 5A41 (PCIE),
        ATI Radeon XPRESS 200M 5A42 (PCIE),
        ATI Radeon XPRESS 200 5A61 (PCIE),
        ATI Radeon XPRESS 200M 5A62 (PCIE),
        ATI Radeon X300 (RV370) 5B60 (PCIE),
        ATI Radeon X600 (RV370) 5B62 (PCIE),
        ATI Radeon X550 (RV370) 5B63 (PCIE),
        ATI FireGL V3100 (RV370) 5B64 (PCIE),
        ATI FireMV 2200 PCIE (RV370) 5B65 (PCIE),
        ATI Radeon Mobility 9200 (M9+) 5C61 (AGP),
        ATI Radeon Mobility 9200 (M9+) 5C63 (AGP),
        ATI Mobility Radeon X800 XT (M28) (PCIE),
        ATI Mobility FireGL V5100 (M28) (PCIE),
        ATI Mobility Radeon X800 (M28) (PCIE), ATI Radeon X850 5D4C (PCIE),
        ATI Radeon X850 XT PE (R480) (PCIE),
        ATI Radeon X850 SE (R480) (PCIE), ATI Radeon X850 PRO (R480) (PCIE),
        ATI unknown Radeon / FireGL (R480) 5D50 (PCIE),
        ATI Radeon X850 XT (R480) (PCIE),
        ATI Radeon X800XT (R423) 5D57 (PCIE),
        ATI FireGL V5000 (RV410) (PCIE), ATI Radeon X700 XT (RV410) (PCIE),
        ATI Radeon X700 PRO (RV410) (PCIE),
        ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X700 (RV410) (PCIE),
        ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X1800,
        ATI Mobility Radeon X1800 XT, ATI Mobility Radeon X1800,
        ATI Mobility FireGL V7200, ATI FireGL V7200, ATI FireGL V5300,
        ATI Mobility FireGL V7100, ATI Radeon X1800, ATI Radeon X1800,
        ATI Radeon X1800, ATI Radeon X1800, ATI Radeon X1800,
        ATI FireGL V7300, ATI FireGL V7350, ATI Radeon X1600, ATI RV505,
        ATI Radeon X1300/X1550, ATI Radeon X1550, ATI M54-GL,
        ATI Mobility Radeon X1400, ATI Radeon X1300/X1550,
        ATI Radeon X1550 64-bit, ATI Mobility Radeon X1300,
        ATI Mobility Radeon X1300, ATI Mobility Radeon X1300,
        ATI Mobility Radeon X1300, ATI Radeon X1300, ATI Radeon X1300,
        ATI RV505, ATI RV505, ATI FireGL V3300, ATI FireGL V3350,
        ATI Radeon X1300, ATI Radeon X1550 64-bit, ATI Radeon X1300/X1550,
        ATI Radeon X1600, ATI Radeon X1300/X1550, ATI Mobility Radeon X1450,
        ATI Radeon X1300/X1550, ATI Mobility Radeon X2300,
        ATI Mobility Radeon X2300, ATI Mobility Radeon X1350,
        ATI Mobility Radeon X1350, ATI Mobility Radeon X1450,
        ATI Radeon X1300, ATI Radeon X1550, ATI Mobility Radeon X1350,
        ATI FireMV 2250, ATI Radeon X1550 64-bit, ATI Radeon X1600,
        ATI Radeon X1650, ATI Radeon X1600, ATI Radeon X1600,
        ATI Mobility FireGL V5200, ATI Mobility Radeon X1600,
        ATI Radeon X1650, ATI Radeon X1650, ATI Radeon X1600,
        ATI Radeon X1300 XT/X1600 Pro, ATI FireGL V3400,
        ATI Mobility FireGL V5250, ATI Mobility Radeon X1700,
        ATI Mobility Radeon X1700 XT, ATI FireGL V5200,
        ATI Mobility Radeon X1700, ATI Radeon X2300HD,
        ATI Mobility Radeon HD 2300, ATI Mobility Radeon HD 2300,
        ATI Radeon X1950, ATI Radeon X1900, ATI Radeon X1950,
        ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
        ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
        ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
        ATI AMD Stream Processor, ATI Radeon X1900, ATI Radeon X1950,
        ATI RV560, ATI RV560, ATI Mobility Radeon X1900, ATI RV560,
        ATI Radeon X1950 GT, ATI RV570, ATI RV570, ATI FireGL V7400,
        ATI RV560, ATI Radeon X1650, ATI Radeon X1650, ATI RV560,
        ATI Radeon 9100 PRO IGP 7834, ATI Radeon Mobility 9200 IGP 7835,
        ATI Radeon X1200, ATI Radeon X1200, ATI Radeon X1200,
        ATI Radeon X1200, ATI Radeon X1200, ATI RS740, ATI RS740M, ATI RS740,
        ATI RS740M, ATI Radeon HD 2900 XT, ATI Radeon HD 2900 XT,
        ATI Radeon HD 2900 XT, ATI Radeon HD 2900 Pro, ATI Radeon HD 2900 GT,
        ATI FireGL V8650, ATI FireGL V8600, ATI FireGL V7600,
        ATI Radeon 4800 Series, ATI Radeon HD 4870 x2,
        ATI Radeon 4800 Series, ATI Radeon HD 4850 x2,
        ATI FirePro V8750 (FireGL), ATI FirePro V7760 (FireGL),
        ATI Mobility RADEON HD 4850, ATI Mobility RADEON HD 4850 X2,
        ATI Radeon 4800 Series, ATI FirePro RV770, AMD FireStream 9270,
        AMD FireStream 9250, ATI FirePro V8700 (FireGL),
        ATI Mobility RADEON HD 4870, ATI Mobility RADEON M98,
        ATI Mobility RADEON HD 4870, ATI Radeon 4800 Series,
        ATI Radeon 4800 Series, ATI FirePro M7750, ATI M98, ATI M98, ATI M98,
        ATI Mobility Radeon HD 4650, ATI Radeon RV730 (AGP),
        ATI Mobility Radeon HD 4670, ATI FirePro M5750,
        ATI Mobility Radeon HD 4670, ATI Radeon RV730 (AGP),
        ATI RV730XT [Radeon HD 4670], ATI RADEON E4600,
        ATI Radeon HD 4600 Series, ATI RV730 PRO [Radeon HD 4650],
        ATI FirePro V7750 (FireGL), ATI FirePro V5700 (FireGL),
        ATI FirePro V3750 (FireGL), ATI Mobility Radeon HD 4830,
        ATI Mobility Radeon HD 4850, ATI FirePro M7740, ATI RV740,
        ATI Radeon HD 4770, ATI Radeon HD 4700 Series, ATI Radeon HD 4770,
        ATI FirePro M5750, ATI RV610, ATI Radeon HD 2400 XT,
        ATI Radeon HD 2400 Pro, ATI Radeon HD 2400 PRO AGP, ATI FireGL V4000,
        ATI RV610, ATI Radeon HD 2350, ATI Mobility Radeon HD 2400 XT,
        ATI Mobility Radeon HD 2400, ATI RADEON E2400, ATI RV610,
        ATI FireMV 2260, ATI RV670, ATI Radeon HD3870,
        ATI Mobility Radeon HD 3850, ATI Radeon HD3850,
        ATI Mobility Radeon HD 3850 X2, ATI RV670,
        ATI Mobility Radeon HD 3870, ATI Mobility Radeon HD 3870 X2,
        ATI Radeon HD3870 X2, ATI FireGL V7700, ATI Radeon HD3850,
        ATI Radeon HD3690, AMD Firestream 9170, ATI Radeon HD 4550,
        ATI Radeon RV710, ATI Radeon RV710, ATI Radeon RV710,
        ATI Radeon HD 4350, ATI Mobility Radeon 4300 Series,
        ATI Mobility Radeon 4500 Series, ATI Mobility Radeon 4500 Series,
        ATI FirePro RG220, ATI Mobility Radeon 4330, ATI RV630,
        ATI Mobility Radeon HD 2600, ATI Mobility Radeon HD 2600 XT,
        ATI Radeon HD 2600 XT AGP, ATI Radeon HD 2600 Pro AGP,
        ATI Radeon HD 2600 XT, ATI Radeon HD 2600 Pro, ATI Gemini RV630,
        ATI Gemini Mobility Radeon HD 2600 XT, ATI FireGL V5600,
        ATI FireGL V3600, ATI Radeon HD 2600 LE,
        ATI Mobility FireGL Graphics Processor, ATI Radeon HD 3470,
        ATI Mobility Radeon HD 3430, ATI Mobility Radeon HD 3400 Series,
        ATI Radeon HD 3450, ATI Radeon HD 3450, ATI Radeon HD 3430,
        ATI Radeon HD 3450, ATI FirePro V3700, ATI FireMV 2450,
        ATI FireMV 2260, ATI FireMV 2260, ATI Radeon HD 3600 Series,
        ATI Radeon HD 3650 AGP, ATI Radeon HD 3600 PRO,
        ATI Radeon HD 3600 XT, ATI Radeon HD 3600 PRO,
        ATI Mobility Radeon HD 3650, ATI Mobility Radeon HD 3670,
        ATI Mobility FireGL V5700, ATI Mobility FireGL V5725,
        ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
        ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
        ATI Radeon HD 3300 Graphics, ATI Radeon HD 3200 Graphics,
        ATI Radeon 3000 Graphics, SUMO, SUMO, SUMO2, SUMO2, SUMO2, SUMO2,
        SUMO, SUMO, SUMO, SUMO, SUMO, SUMO, SUMO, SUMO, ATI Radeon HD 4200,
        ATI Radeon 4100, ATI Mobility Radeon HD 4200,
        ATI Mobility Radeon 4100, ATI Radeon HD 4290, ATI Radeon HD 4250,
        AMD Radeon HD 6310 Graphics, AMD Radeon HD 6310 Graphics,
        AMD Radeon HD 6250 Graphics, AMD Radeon HD 6250 Graphics,
        AMD Radeon HD 6300 Series Graphics,
        AMD Radeon HD 6200 Series Graphics, PALM, PALM, PALM, CYPRESS,
        ATI FirePro (FireGL) Graphics Adapter,
        ATI FirePro (FireGL) Graphics Adapter,
        ATI FirePro (FireGL) Graphics Adapter, AMD Firestream 9370,
        AMD Firestream 9350, ATI Radeon HD 5800 Series,
        ATI Radeon HD 5800 Series, ATI Radeon HD 5800 Series,
        ATI Radeon HD 5800 Series, ATI Radeon HD 5900 Series,
        ATI Radeon HD 5900 Series, ATI Mobility Radeon HD 5800 Series,
        ATI Mobility Radeon HD 5800 Series,
        ATI FirePro (FireGL) Graphics Adapter,
        ATI FirePro (FireGL) Graphics Adapter,
        ATI Mobility Radeon HD 5800 Series, ATI Radeon HD 5700 Series,
        ATI Radeon HD 5700 Series, ATI Radeon HD 6700 Series,
        ATI Radeon HD 5700 Series, ATI Radeon HD 6700 Series,
        ATI Mobility Radeon HD 5000 Series,
        ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon HD 5570,
        ATI FirePro (FireGL) Graphics Adapter,
        ATI FirePro (FireGL) Graphics Adapter, ATI Radeon HD 5670,
        ATI Radeon HD 5570, ATI Radeon HD 5500 Series, REDWOOD,
        ATI Mobility Radeon HD 5000 Series,
        ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon Graphics,
        ATI Mobility Radeon Graphics, CEDAR,
        ATI FirePro (FireGL) Graphics Adapter,
        ATI FirePro (FireGL) Graphics Adapter, ATI FirePro 2270, CEDAR,
        ATI Radeon HD 5450, CEDAR, CEDAR, CAYMAN, CAYMAN, CAYMAN, CAYMAN,
        CAYMAN, CAYMAN, CAYMAN, CAYMAN, CAYMAN, CAYMAN,
        AMD Radeon HD 6900 Series, AMD Radeon HD 6900 Series, CAYMAN, CAYMAN,
        CAYMAN, AMD Radeon HD 6900M Series, Mobility Radeon HD 6000 Series,
        BARTS, BARTS, Mobility Radeon HD 6000 Series,
        Mobility Radeon HD 6000 Series, BARTS, BARTS, BARTS, BARTS,
        AMD Radeon HD 6800 Series, AMD Radeon HD 6800 Series,
        AMD Radeon HD 6700 Series, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
        TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
        TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
        CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS,
        CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, ARUBA, ARUBA,
        ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA,
        ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA,
        ARUBA, ARUBA, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI,
        TAHITI, TAHITI, TAHITI, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN,
        PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN,
        PITCAIRN, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE,
        VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE,
        VERDE, VERDE
[    12.148] (II) VESA: driver for VESA chipsets: vesa
[    12.148] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    12.148] (II) FBDEV: driver for framebuffer: fbdev
[    12.148] (++) using VT number 7


[    12.148] (II) [KMS] Kernel modesetting enabled.
[    12.148] (WW) Falling back to old probe method for vesa
[    12.148] (WW) Falling back to old probe method for modesetting
[    12.148] (WW) Falling back to old probe method for fbdev
[    12.148] (II) Loading sub module "fbdevhw"
[    12.148] (II) LoadModule: "fbdevhw"
[    12.149] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    12.149] (II) Module fbdevhw: vendor="X.Org Foundation"
[    12.149]    compiled for 1.13.0, module version = 0.0.2
[    12.149]    ABI class: X.Org Video Driver, version 13.0
[    12.149] (II) RADEON(0): Creating default Display subsection in Screen section
        "Default Screen Section" for depth/fbbpp 24/32
[    12.149] (==) RADEON(0): Depth 24, (--) framebuffer bpp 32
[    12.149] (II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    12.149] (==) RADEON(0): Default visual is TrueColor
[    12.149] (==) RADEON(0): RGB weight 888
[    12.149] (II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
[    12.149] (--) RADEON(0): Chipset: "ATI Radeon X1300/X1550" (ChipID = 0x7142)
[    12.149] (II) Loading sub module "dri2"
[    12.149] (II) LoadModule: "dri2"
[    12.149] (II) Module "dri2" already built-in
[    12.149] (II) Loading sub module "exa"
[    12.149] (II) LoadModule: "exa"
[    12.149] (II) Loading /usr/lib/xorg/modules/libexa.so
[    12.149] (II) Module exa: vendor="X.Org Foundation"
[    12.149]    compiled for 1.13.0, module version = 2.6.0
[    12.149]    ABI class: X.Org Video Driver, version 13.0
[    12.149] (II) RADEON(0): KMS Color Tiling: enabled
[    12.149] (II) RADEON(0): KMS Pageflipping: enabled
[    12.149] (II) RADEON(0): SwapBuffers wait for vsync: enabled
[    12.188] (II) RADEON(0): Output DVI-0 has no monitor section
[    12.208] (II) RADEON(0): Output S-video has no monitor section
[    12.248] (II) RADEON(0): Output VGA-0 has no monitor section
[    12.288] (II) RADEON(0): EDID for output DVI-0
[    12.308] (II) RADEON(0): EDID for output S-video
[    12.308] (II) RADEON(0): Printing probed modes for output S-video
[    12.308] (II) RADEON(0): Modeline "1024x768"x59.9   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync (47.8 kHz)
[    12.308] (II) RADEON(0): Modeline "800x600"x59.9   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz)
[    12.308] (II) RADEON(0): Modeline "848x480"x59.7   31.50  848 872 952 1056  480 483 493 500 -hsync +vsync (29.8 kHz)
[    12.308] (II) RADEON(0): Modeline "720x480"x59.7   26.75  720 744 808 896  480 483 493 500 -hsync +vsync (29.9 kHz)
[    12.308] (II) RADEON(0): Modeline "640x480"x59.4   23.75  640 664 720 800  480 483 487 500 -hsync +vsync (29.7 kHz)
[    12.348] (II) RADEON(0): EDID for output VGA-0
[    12.348] (II) RADEON(0): Output DVI-0 disconnected
[    12.348] (II) RADEON(0): Output S-video connected
[    12.348] (II) RADEON(0): Output VGA-0 disconnected
[    12.348] (II) RADEON(0): Using exact sizes for initial modes
[    12.348] (II) RADEON(0): Output S-video using initial mode 1024x768
[    12.348] (II) RADEON(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    12.348] (II) RADEON(0): mem size init: gart size :1fdff000 vram size: s:10000000 visible:fcc0000
[    12.348] (II) RADEON(0): EXA: Driver will allow EXA pixmaps in VRAM
[    12.348] (==) RADEON(0): DPI set to (96, 96)
[    12.348] (II) Loading sub module "fb"
[    12.348] (II) LoadModule: "fb"
[    12.348] (II) Loading /usr/lib/xorg/modules/libfb.so
[    12.349] (II) Module fb: vendor="X.Org Foundation"
[    12.349]    compiled for 1.13.0, module version = 1.0.0
[    12.349]    ABI class: X.Org ANSI C Emulation, version 0.4
[    12.349] (II) Loading sub module "ramdac"
[    12.349] (II) LoadModule: "ramdac"
[    12.349] (II) Module "ramdac" already built-in
[    12.349] (II) UnloadModule: "vesa"
[    12.349] (II) Unloading vesa
[    12.349] (II) UnloadModule: "modesetting"
[    12.349] (II) Unloading modesetting
[    12.349] (II) UnloadModule: "fbdev"
[    12.349] (II) Unloading fbdev
[    12.349] (II) UnloadSubModule: "fbdevhw"
[    12.349] (II) Unloading fbdevhw
[    12.349] (--) Depth 24 pixmap format is 32 bpp
[    12.349] (II) RADEON(0): [DRI2] Setup complete
[    12.349] (II) RADEON(0): [DRI2]   DRI driver: r300
[    12.349] (II) RADEON(0): [DRI2]   VDPAU driver: r300
[    12.349] (II) RADEON(0): Front buffer size: 3072K
[    12.349] (II) RADEON(0): VRAM usage limit set to 230169K
[    12.349] (==) RADEON(0): Backing store disabled
[    12.349] (II) RADEON(0): Direct rendering enabled
[    12.349] (II) RADEON(0): Render acceleration enabled for R300/R400/R500 type cards.
[    12.349] (II) RADEON(0): Setting EXA maxPitchBytes
[    12.349] (II) EXA(0): Driver allocated offscreen pixmaps
[    12.349] (II) EXA(0): Driver registered support for the following operations:
[    12.349] (II)         Solid
[    12.349] (II)         Copy
[    12.349] (II)         Composite (RENDER acceleration)
[    12.349] (II)         UploadToScreen
[    12.349] (II)         DownloadFromScreen
[    12.349] (II) RADEON(0): Acceleration enabled
[    12.349] (==) RADEON(0): DPMS enabled
[    12.349] (==) RADEON(0): Silken mouse enabled
[    12.349] (II) RADEON(0): Set up textured video
[    12.349] (II) RADEON(0): [XvMC] Associated with Radeon Textured Video.
[    12.349] (II) RADEON(0): [XvMC] Extension initialized.
[    12.349] (II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    12.359] (--) RandR disabled
[    12.385] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    12.385] (II) AIGLX: enabled GLX_INTEL_swap_event
[    12.385] (II) AIGLX: enabled GLX_ARB_create_context
[    12.385] (II) AIGLX: enabled GLX_ARB_create_context_profile
[    12.385] (II) AIGLX: enabled GLX_EXT_create_context_es2_profile
[    12.385] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    12.385] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    12.386] (II) AIGLX: Loaded and initialized r300
[    12.386] (II) GLX: Initialized DRI2 GL provider for screen 0
[    12.386] (II) RADEON(0): Setting screen physical size to 270 x 203
[    12.395] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    12.398] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    12.398] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    12.398] (II) LoadModule: "evdev"
[    12.398] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    12.398] (II) Module evdev: vendor="X.Org Foundation"
[    12.398]    compiled for 1.13.0, module version = 2.7.3
[    12.398]    Module class: X.Org XInput Driver
[    12.398]    ABI class: X.Org XInput driver, version 18.0
[    12.398] (II) Using input driver 'evdev' for 'Power Button'
[    12.399] (**) Power Button: always reports core events
[    12.399] (**) evdev: Power Button: Device: "/dev/input/event1"
[    12.399] (--) evdev: Power Button: Vendor 0 Product 0x1
[    12.399] (--) evdev: Power Button: Found keys
[    12.399] (II) evdev: Power Button: Configuring as keyboard
[    12.399] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    12.399] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    12.399] (**) Option "xkb_rules" "evdev"
[    12.399] (**) Option "xkb_model" "pc105"
[    12.399] (**) Option "xkb_layout" "us"
[    12.399] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    12.399] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    12.399] (II) Using input driver 'evdev' for 'Power Button'
[    12.399] (**) Power Button: always reports core events
[    12.399] (**) evdev: Power Button: Device: "/dev/input/event0"
[    12.400] (--) evdev: Power Button: Vendor 0 Product 0x1
[    12.400] (--) evdev: Power Button: Found keys
[    12.400] (II) evdev: Power Button: Configuring as keyboard
[    12.400] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    12.400] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    12.400] (**) Option "xkb_rules" "evdev"
[    12.400] (**) Option "xkb_model" "pc105"
[    12.400] (**) Option "xkb_layout" "us"
[    12.400] (II) config/udev: Adding input device Logitech USB Optical Mouse (/dev/input/event2)
[    12.400] (**) Logitech USB Optical Mouse: Applying InputClass "evdev pointer catchall"
[    12.400] (II) Using input driver 'evdev' for 'Logitech USB Optical Mouse'
[    12.400] (**) Logitech USB Optical Mouse: always reports core events
[    12.400] (**) evdev: Logitech USB Optical Mouse: Device: "/dev/input/event2"
[    12.400] (--) evdev: Logitech USB Optical Mouse: Vendor 0x46d Product 0xc05a
[    12.400] (--) evdev: Logitech USB Optical Mouse: Found 12 mouse buttons
[    12.400] (--) evdev: Logitech USB Optical Mouse: Found scroll wheel(s)
[    12.400] (--) evdev: Logitech USB Optical Mouse: Found relative axes
[    12.400] (--) evdev: Logitech USB Optical Mouse: Found x and y relative axes
[    12.400] (II) evdev: Logitech USB Optical Mouse: Configuring as mouse
[    12.400] (II) evdev: Logitech USB Optical Mouse: Adding scrollwheel support
[    12.400] (**) evdev: Logitech USB Optical Mouse: YAxisMapping: buttons 4 and 5
[    12.401] (**) evdev: Logitech USB Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    12.401] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:02.0/usb2/2-1/2-1:1.0/input/input2/event2"
[    12.401] (II) XINPUT: Adding extended input device "Logitech USB Optical Mouse" (type: MOUSE, id 8)
[    12.401] (II) evdev: Logitech USB Optical Mouse: initialized for relative axes.
[    12.401] (**) Logitech USB Optical Mouse: (accel) keeping acceleration scheme 1
[    12.401] (**) Logitech USB Optical Mouse: (accel) acceleration profile 0
[    12.401] (**) Logitech USB Optical Mouse: (accel) acceleration factor: 2.000
[    12.401] (**) Logitech USB Optical Mouse: (accel) acceleration threshold: 4
[    12.401] (II) config/udev: Adding input device Logitech USB Optical Mouse (/dev/input/mouse0)
[    12.401] (II) No input driver specified, ignoring this device.
[    12.401] (II) This device may have been added with another device file.
[    12.402] (II) config/udev: Adding input device Mitsumi Electric Apple USB Keyboard (/dev/input/event3)
[    12.402] (**) Mitsumi Electric Apple USB Keyboard: Applying InputClass "evdev keyboard catchall"
[    12.402] (II) Using input driver 'evdev' for 'Mitsumi Electric Apple USB Keyboard'
[    12.402] (**) Mitsumi Electric Apple USB Keyboard: always reports core events
[    12.402] (**) evdev: Mitsumi Electric Apple USB Keyboard: Device: "/dev/input/event3"
[    12.402] (--) evdev: Mitsumi Electric Apple USB Keyboard: Vendor 0x5ac Product 0x201
[    12.402] (--) evdev: Mitsumi Electric Apple USB Keyboard: Found keys
[    12.402] (II) evdev: Mitsumi Electric Apple USB Keyboard: Configuring as keyboard
[    12.402] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:02.0/usb2/2-2/2-2.1/2-2.1:1.0/input/input3/event3"
[    12.402] (II) XINPUT: Adding extended input device "Mitsumi Electric Apple USB Keyboard" (type: KEYBOARD, id 9)
[    12.402] (**) Option "xkb_rules" "evdev"
[    12.402] (**) Option "xkb_model" "pc105"
[    12.402] (**) Option "xkb_layout" "us"
[    12.402] (II) config/udev: Adding drm device (/dev/dri/card0)
[    24.834] (II) AIGLX: Suspending AIGLX clients for VT switch
media@MediaBox-Linux:~$

```

ps i love your quote at the ender there.

---

### Post by Bashing-om on 2014-02-20
Jeremy_Gordy; Hey !

Apologize for the delay in responding, got called away .

Xorg.o.log file: no fault found !

/etc/X11/xorg.conf: That file is not used with ATI/radeon, And is not needed generally in this application.

As to what is going on presently, I just do not presently know. But let's think along the lines of a kernel issue.
What have we got to work with as far as kernels go ?
```

dpkg -l | grep linux-image

```

will try and boot an older image and see what results.

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

### Post by Jeremy_Gordy on 2014-02-20
It's fine there is no need to apologize, you're taking time out of your day to help me and i greatly appreciate it. and thanks for the info on the xorg file

ok so i ran dpkg -l | grep linux-image and got this

```
media@MediaBox-Linux:~$ dpkg -l | grep linux-image
ii  linux-image-3.5.0-23-generic                 3.5.0-23.35~precise1                             Linux kernel image for version 3.5.0 on 64 bit x86 SMP
ii  linux-image-generic-lts-quantal              3.5.0.23.30                                      Generic Linux kernel image

```

---

### Post by Bashing-om on 2014-02-20
Jeremy_Gordyl uuhh,

You been doing house cleaning, normally a real good thing.
OK, what happens if you boot with the quantal kernel (3.5.0.23.30) ?
Boot to the grub menu, and highlight this kernel, key combo ctl+x to continue the boot process.
Can you now boot to the GUI  desk top ?

HES I am not familiar with ->
[INDENT][INDENT]we will flounder through this
[INDENT][INDENT][INDENT]together
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Jeremy_Gordy on 2014-02-20
okay so this is what i have when i got to the grub menu.

GNU GRUB version 1.99-21ubuntu3.9

-Ubuntu, with Linux 3.5.0-23-generic
-Ubuntu, with Linux 3.5.0-23-generic (recovery mode)
-memtest86+
-memtest86+, serial console 115200

p.s. the GRUB menu displays just find on the S-video connection.

---

### Post by Bashing-om on 2014-02-20
Jeremy_Gordy; Huh !

Not at all what I expected. Maybe getting deeper now ?
What returns:
```

uname -r
ls -la /usr/src
ls -la /boot

```
see if I can understand why dpkg list the quantal kernel, but grub does not pick it up.
Looks like I best bone up on Hardware Enablement Stack (HES) to get us another kernel to boot.

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

### Post by Jeremy_Gordy on 2014-02-20
This is what was returned

```

media@MediaBox-Linux:~$ uname -r
3.5.0-23-generic

media@MediaBox-Linux:~$ ls -la /usr/src
total 16
drwxr-xr-x  4 root root 4096 Feb 13  2013 .
drwxr-xr-x 10 root root 4096 Feb 13  2013 ..
drwxr-xr-x 24 root root 4096 Feb 13  2013 linux-headers-3.5.0-23
drwxr-xr-x  7 root root 4096 Feb 13  2013 linux-headers-3.5.0-23-generic

media@MediaBox-Linux:~$ ls -la /boot
total 24560
drwxr-xr-x  3 root root     4096 Feb 20 02:04 .
drwxr-xr-x 24 root root     4096 Feb 20 02:02 ..
-rw-r--r--  1 root root   848290 Jan 25  2013 abi-3.5.0-23-generic
-rw-r--r--  1 root root   147880 Jan 25  2013 config-3.5.0-23-generic
drwxr-xr-x  3 root root    12288 Feb 20 02:03 grub
-rw-r--r--  1 root root 15544677 Feb 20 02:04 initrd.img-3.5.0-23-generic
-rw-r--r--  1 root root   176764 Nov 27  2011 memtest86+.bin
-rw-r--r--  1 root root   178944 Nov 27  2011 memtest86+_multiboot.bin
-rw-------  1 root root  3023265 Jan 25  2013 System.map-3.5.0-23-generic
-rw-r--r--  1 root root  5189248 Feb 20 01:56 vmlinuz-3.5.0-23-generic

```

---

### Post by Bashing-om on 2014-02-20
Jeremy_Gordy; nope !

Don't see it. Where is the quantal kernel being picked up from ?
```

grep -B3 -A10 "Package: linux-image" /var/lib/dpkg/status

```
Will bone up on HES and get us a later kernel; In my morrow.
Late here and I am past a consistent thinking stage.
Failing that we can (re-)install an earlier kernel and see what results.

[INDENT][INDENT]which way did he go
[INDENT][INDENT][INDENT]George
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Jeremy_Gordy on 2014-02-20
ok not a problem, did you want me to run that code?

---

### Post by Bashing-om on 2014-02-21
Jeremy_Gordy; yeah

Run the grep code and let's see what dpkg might be looking at.
I will focus in my morrow on updating your kernel to that of saucy.

We have a house dog that has come down sick, and must take her to the vet in the AM, scared she has contacted parvo !

[INDENT][INDENT]till we can do better
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2014-02-21
Jeremy_Gordy; Howdy,

OK I have a glimmer of what is going on !
Let's do this -> upgrade the kernel, xserver and mesa utilities to the saucy release.

These packages MUST all be of the same release, and this method insures it is so.
Do this from terminal -> at the GUI login -> key combo ctl+alt+F1, log in and enter password, then Terminal commands:
```

sudo apt-get install --install-recommends linux-generic-lts-saucy xserver-xorg-lts-saucy libgl1-mesa-glx-lts-saucy
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo update-grub 

```

Please make a note, that prior to saucy reaching End Of Life, You MUST upgrade the HWE stack (linux-generic, xserver-xorg and libfl1 stuff) to trusty !!!

Betcha when the saucy HWE is installed, all will be
[INDENT][INDENT][INDENT]hunky dory
[/INDENT][/INDENT][/INDENT]

---

### Post by Jeremy_Gordy on 2014-02-21
ok so i hooked up a spare monitor up to it last night and the monitor displays just fine, its only the S-video connection that is scrambled. plus when i have a vga monitor hooked up the S-video will disconnect and says that it is disconnected when running xrandr,

running xrandr --addmode S-video 800x600, doesn't display anything on the s-video. with vga being used.

another note, i had updates on the desktop so i updated it last night now its on a differnt kernel. i re-ran those codes as well.

uname -r
```
media@MediaBox-Linux:~$ uname -r3.5.0-46-generic
media@MediaBox-Linux:~$ lspci -nnk|grep -iA3 vga
02:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] RV515 PRO [Radeon X1300/X1550 Series] [1002:7142]
        Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] Device [1002:0302]
        Kernel driver in use: radeon
        Kernel modules: radeon
media@MediaBox-Linux:~$ sudo lshw -C display
  *-display:0
       description: VGA compatible controller
       product: RV515 PRO [Radeon X1300/X1550 Series]
       vendor: Hynix Semiconductor (Hyundai Electronics)
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:16 memory:e0000000-efffffff memory:fdef0000-fdefffff ioport:ac00(size=256) memory:fdec0000-fdedffff
  *-display:1 UNCLAIMED
       description: Display controller
       product: RV515 PRO [Radeon X1300/X1550 Series] (Secondary)
       vendor: Hynix Semiconductor (Hyundai Electronics)
       physical id: 0.1
       bus info: pci@0000:02:00.1
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress cap_list
       configuration: latency=0
       resources: memory:fdee0000-fdeeffff
media@MediaBox-Linux:~$
```

cat /var/log/Xorg.0.log
```
media@MediaBox-Linux:~$ cat /var/log/Xorg.0.log[    33.623]
X.Org X Server 1.13.0
Release Date: 2012-09-05
[    33.623] X Protocol Version 11, Revision 0
[    33.623] Build Operating System: Linux 2.6.42-37-generic x86_64 Ubuntu
[    33.623] Current Operating System: Linux MediaBox-Linux 3.5.0-46-generic #70~precise1-Ubuntu SMP Thu Jan 9 23:55:12 UTC 2014 x86_64
[    33.623] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.5.0-46-generic root=UUID=e2def354-0573-4d46-98c8-16bdf35e3c73 ro quiet splash vt.handoff=7
[    33.623] Build Date: 05 November 2013  03:18:29PM
[    33.623] xorg-server 2:1.13.0-0ubuntu6.5~precise1 (For technical support please see http://www.ubuntu.com/support)
[    33.623] Current version of pixman: 0.30.2
[    33.623]    Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
[    33.623] Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    33.623] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Feb 21 03:51:43 2014
[    34.011] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    34.299] (==) No Layout section.  Using the first Screen section.
[    34.299] (==) No screen section available. Using defaults.
[    34.299] (**) |-->Screen "Default Screen Section" (0)
[    34.299] (**) |   |-->Monitor "<default monitor>"
[    34.319] (==) No monitor specified for screen "Default Screen Section".
        Using a default monitor configuration.
[    34.319] (==) Automatically adding devices
[    34.319] (==) Automatically enabling devices
[    34.319] (==) Automatically adding GPU devices
[    34.377] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    34.377]    Entry deleted from font path.
[    34.377] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    34.377]    Entry deleted from font path.
[    34.377] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    34.377]    Entry deleted from font path.
[    34.394] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    34.394]    Entry deleted from font path.
[    34.394] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    34.394]    Entry deleted from font path.
[    34.394] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    34.394]    Entry deleted from font path.
[    34.394] (==) FontPath set to:
        /usr/share/fonts/X11/misc,
        /usr/share/fonts/X11/Type1,
        built-ins
[    34.394] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    34.394] (II) The server relies on udev to provide the list of input devices.
        If no devices become available, reconfigure udev or disable AutoAddDevices.
[    34.454] (II) Loader magic: 0x7f4e5e0e4c20
[    34.454] (II) Module ABI versions:
[    34.454]    X.Org ANSI C Emulation: 0.4
[    34.454]    X.Org Video Driver: 13.0
[    34.454]    X.Org XInput driver : 18.0
[    34.454]    X.Org Server Extension : 7.0
[    34.454] (II) config/udev: Adding drm device (/dev/dri/card0)
[    34.455] (--) PCI:*(0:2:0:0) 1002:7142:1002:0302 rev 0, Mem @ 0xe0000000/268435456, 0xfdef0000/65536, I/O @ 0x0000ac00/256, BIOS @ 0x????????/131072
[    34.455] (--) PCI: (0:2:0:1) 1002:7162:1002:0303 rev 0, Mem @ 0xfdee0000/65536
[    34.455] (II) Open ACPI successful (/var/run/acpid.socket)
[    34.531] Initializing built-in extension Generic Event Extension
[    34.531] Initializing built-in extension SHAPE
[    34.531] Initializing built-in extension MIT-SHM
[    34.531] Initializing built-in extension XInputExtension
[    34.531] Initializing built-in extension XTEST
[    34.531] Initializing built-in extension BIG-REQUESTS
[    34.531] Initializing built-in extension SYNC
[    34.531] Initializing built-in extension XKEYBOARD
[    34.531] Initializing built-in extension XC-MISC
[    34.531] Initializing built-in extension SECURITY
[    34.531] Initializing built-in extension XINERAMA
[    34.531] Initializing built-in extension XFIXES
[    34.531] Initializing built-in extension RENDER
[    34.531] Initializing built-in extension RANDR
[    34.531] Initializing built-in extension COMPOSITE
[    34.531] Initializing built-in extension DAMAGE
[    34.531] Initializing built-in extension MIT-SCREEN-SAVER
[    34.531] Initializing built-in extension DOUBLE-BUFFER
[    34.531] Initializing built-in extension RECORD
[    34.531] Initializing built-in extension DPMS
[    34.531] Initializing built-in extension X-Resource
[    34.531] Initializing built-in extension XVideo
[    34.531] Initializing built-in extension XVideo-MotionCompensation
[    34.531] Initializing built-in extension XFree86-VidModeExtension
[    34.531] Initializing built-in extension XFree86-DGA
[    34.531] Initializing built-in extension XFree86-DRI
[    34.531] Initializing built-in extension DRI2
[    34.531] (II) LoadModule: "glx"
[    34.881] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    35.018] (II) Module glx: vendor="X.Org Foundation"
[    35.018]    compiled for 1.13.0, module version = 1.0.0
[    35.018]    ABI class: X.Org Server Extension, version 7.0
[    35.018] (==) AIGLX enabled
[    35.026] Loading extension GLX
[    35.026] (==) Matched fglrx as autoconfigured driver 0
[    35.026] (==) Matched ati as autoconfigured driver 1
[    35.026] (==) Matched fglrx as autoconfigured driver 2
[    35.026] (==) Matched ati as autoconfigured driver 3
[    35.026] (==) Matched vesa as autoconfigured driver 4
[    35.026] (==) Matched modesetting as autoconfigured driver 5
[    35.026] (==) Matched fbdev as autoconfigured driver 6
[    35.026] (==) Assigned the driver to the xf86ConfigLayout
[    35.026] (II) LoadModule: "fglrx"
[    35.027] (WW) Warning, couldn't open module fglrx
[    35.027] (II) UnloadModule: "fglrx"
[    35.027] (II) Unloading fglrx
[    35.027] (EE) Failed to load module "fglrx" (module does not exist, 0)
[    35.027] (II) LoadModule: "ati"
[    35.027] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    35.064] (II) Module ati: vendor="X.Org Foundation"
[    35.064]    compiled for 1.13.0, module version = 6.99.99
[    35.064]    Module class: X.Org Video Driver
[    35.064]    ABI class: X.Org Video Driver, version 13.0
[    35.064] (II) LoadModule: "radeon"
[    35.064] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    35.186] (II) Module radeon: vendor="X.Org Foundation"
[    35.186]    compiled for 1.13.0, module version = 6.99.99
[    35.186]    Module class: X.Org Video Driver
[    35.186]    ABI class: X.Org Video Driver, version 13.0
[    35.186] (II) LoadModule: "vesa"
[    35.187] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    35.231] (II) Module vesa: vendor="X.Org Foundation"
[    35.231]    compiled for 1.13.0, module version = 2.3.2
[    35.231]    Module class: X.Org Video Driver
[    35.231]    ABI class: X.Org Video Driver, version 13.0
[    35.231] (II) LoadModule: "modesetting"
[    35.232] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    35.235] (II) Module modesetting: vendor="X.Org Foundation"
[    35.235]    compiled for 1.13.0, module version = 0.5.0
[    35.235]    Module class: X.Org Video Driver
[    35.235]    ABI class: X.Org Video Driver, version 13.0
[    35.235] (II) LoadModule: "fbdev"
[    35.235] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    35.238] (II) Module fbdev: vendor="X.Org Foundation"
[    35.238]    compiled for 1.13.0, module version = 0.4.3
[    35.238]    Module class: X.Org Video Driver
[    35.238]    ABI class: X.Org Video Driver, version 13.0
[    35.238] (==) Matched fglrx as autoconfigured driver 0
[    35.238] (==) Matched ati as autoconfigured driver 1
[    35.238] (==) Matched fglrx as autoconfigured driver 2
[    35.238] (==) Matched ati as autoconfigured driver 3
[    35.238] (==) Matched vesa as autoconfigured driver 4
[    35.238] (==) Matched modesetting as autoconfigured driver 5
[    35.238] (==) Matched fbdev as autoconfigured driver 6
[    35.238] (==) Assigned the driver to the xf86ConfigLayout
[    35.238] (II) LoadModule: "fglrx"
[    35.239] (WW) Warning, couldn't open module fglrx
[    35.239] (II) UnloadModule: "fglrx"
[    35.239] (II) Unloading fglrx
[    35.239] (EE) Failed to load module "fglrx" (module does not exist, 0)
[    35.239] (II) LoadModule: "ati"
[    35.239] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    35.239] (II) Module ati: vendor="X.Org Foundation"
[    35.239]    compiled for 1.13.0, module version = 6.99.99
[    35.239]    Module class: X.Org Video Driver
[    35.239]    ABI class: X.Org Video Driver, version 13.0
[    35.239] (II) LoadModule: "vesa"
[    35.239] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    35.239] (II) Module vesa: vendor="X.Org Foundation"
[    35.239]    compiled for 1.13.0, module version = 2.3.2
[    35.239]    Module class: X.Org Video Driver
[    35.239]    ABI class: X.Org Video Driver, version 13.0
[    35.239] (II) UnloadModule: "vesa"
[    35.239] (II) Unloading vesa
[    35.239] (II) Failed to load module "vesa" (already loaded, 0)
[    35.239] (II) LoadModule: "modesetting"
[    35.239] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    35.239] (II) Module modesetting: vendor="X.Org Foundation"
[    35.239]    compiled for 1.13.0, module version = 0.5.0
[    35.239]    Module class: X.Org Video Driver
[    35.239]    ABI class: X.Org Video Driver, version 13.0
[    35.239] (II) UnloadModule: "modesetting"
[    35.240] (II) Unloading modesetting
[    35.240] (II) Failed to load module "modesetting" (already loaded, 0)
[    35.240] (II) LoadModule: "fbdev"
[    35.240] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    35.240] (II) Module fbdev: vendor="X.Org Foundation"
[    35.240]    compiled for 1.13.0, module version = 0.4.3
[    35.240]    Module class: X.Org Video Driver
[    35.240]    ABI class: X.Org Video Driver, version 13.0
[    35.240] (II) UnloadModule: "fbdev"
[    35.240] (II) Unloading fbdev
[    35.240] (II) Failed to load module "fbdev" (already loaded, 0)
[    35.240] (II) RADEON: Driver for ATI Radeon chipsets:
        ATI Radeon Mobility X600 (M24) 3150 (PCIE), ATI FireMV 2400 (PCI),
        ATI Radeon Mobility X300 (M24) 3152 (PCIE),
        ATI FireGL M24 GL 3154 (PCIE), ATI FireMV 2400 3155 (PCI),
        ATI Radeon X600 (RV380) 3E50 (PCIE),
        ATI FireGL V3200 (RV380) 3E54 (PCIE), ATI Radeon IGP320 (A3) 4136,
        ATI Radeon IGP330/340/350 (A4) 4137, ATI Radeon 9500 AD (AGP),
        ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
        ATI FireGL Z1 AG (AGP), ATI Radeon 9800SE AH (AGP),
        ATI Radeon 9800 AI (AGP), ATI Radeon 9800 AJ (AGP),
        ATI FireGL X2 AK (AGP), ATI Radeon 9600 AP (AGP),
        ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
        ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP), ATI Radeon 9650,
        ATI FireGL RV360 AV (AGP), ATI Radeon 7000 IGP (A4+) 4237,
        ATI Radeon 8500 AIW BB (AGP), ATI Radeon IGP320M (U1) 4336,
        ATI Radeon IGP330M/340M/350M (U2) 4337,
        ATI Radeon Mobility 7000 IGP 4437, ATI Radeon 9000/PRO If (AGP/PCI),
        ATI Radeon 9000 Ig (AGP/PCI), ATI Radeon X800 (R420) JH (AGP),
        ATI Radeon X800PRO (R420) JI (AGP),
        ATI Radeon X800SE (R420) JJ (AGP), ATI Radeon X800 (R420) JK (AGP),
        ATI Radeon X800 (R420) JL (AGP), ATI FireGL X3 (R420) JM (AGP),
        ATI Radeon Mobility 9800 (M18) JN (AGP),
        ATI Radeon X800 SE (R420) (AGP), ATI Radeon X800XT (R420) JP (AGP),
        ATI Radeon X800 VE (R420) JT (AGP), ATI Radeon X850 (R480) (AGP),
        ATI Radeon X850 XT (R480) (AGP), ATI Radeon X850 SE (R480) (AGP),
        ATI Radeon X850 PRO (R480) (AGP), ATI Radeon X850 XT PE (R480) (AGP),
        ATI Radeon Mobility M7 LW (AGP),
        ATI Mobility FireGL 7800 M7 LX (AGP),
        ATI Radeon Mobility M6 LY (AGP), ATI Radeon Mobility M6 LZ (AGP),
        ATI FireGL Mobility 9000 (M9) Ld (AGP),
        ATI Radeon Mobility 9000 (M9) Lf (AGP),
        ATI Radeon Mobility 9000 (M9) Lg (AGP), ATI FireMV 2400 PCI,
        ATI Radeon 9700 Pro ND (AGP), ATI Radeon 9700/9500Pro NE (AGP),
        ATI Radeon 9600TX NF (AGP), ATI FireGL X1 NG (AGP),
        ATI Radeon 9800PRO NH (AGP), ATI Radeon 9800 NI (AGP),
        ATI FireGL X2 NK (AGP), ATI Radeon 9800XT NJ (AGP),
        ATI Radeon Mobility 9600/9700 (M10/M11) NP (AGP),
        ATI Radeon Mobility 9600 (M10) NQ (AGP),
        ATI Radeon Mobility 9600 (M11) NR (AGP),
        ATI Radeon Mobility 9600 (M10) NS (AGP),
        ATI FireGL Mobility T2 (M10) NT (AGP),
        ATI FireGL Mobility T2e (M11) NV (AGP), ATI Radeon QD (AGP),
        ATI Radeon QE (AGP), ATI Radeon QF (AGP), ATI Radeon QG (AGP),
        ATI FireGL 8700/8800 QH (AGP), ATI Radeon 8500 QL (AGP),
        ATI Radeon 9100 QM (AGP), ATI Radeon 7500 QW (AGP/PCI),
        ATI Radeon 7500 QX (AGP/PCI), ATI Radeon VE/7000 QY (AGP/PCI),
        ATI Radeon VE/7000 QZ (AGP/PCI), ATI ES1000 515E (PCI),
        ATI Radeon Mobility X300 (M22) 5460 (PCIE),
        ATI Radeon Mobility X600 SE (M24C) 5462 (PCIE),
        ATI FireGL M22 GL 5464 (PCIE), ATI Radeon X800 (R423) UH (PCIE),
        ATI Radeon X800PRO (R423) UI (PCIE),
        ATI Radeon X800LE (R423) UJ (PCIE),
        ATI Radeon X800SE (R423) UK (PCIE),
        ATI Radeon X800 XTP (R430) (PCIE), ATI Radeon X800 XL (R430) (PCIE),
        ATI Radeon X800 SE (R430) (PCIE), ATI Radeon X800 (R430) (PCIE),
        ATI FireGL V7100 (R423) (PCIE), ATI FireGL V5100 (R423) UQ (PCIE),
        ATI FireGL unknown (R423) UR (PCIE),
        ATI FireGL unknown (R423) UT (PCIE),
        ATI Mobility FireGL V5000 (M26) (PCIE),
        ATI Mobility FireGL V5000 (M26) (PCIE),
        ATI Mobility Radeon X700 XL (M26) (PCIE),
        ATI Mobility Radeon X700 (M26) (PCIE),
        ATI Mobility Radeon X700 (M26) (PCIE),
        ATI Radeon X550XTX 5657 (PCIE), ATI Radeon 9100 IGP (A5) 5834,
        ATI Radeon Mobility 9100 IGP (U3) 5835,
        ATI Radeon XPRESS 200 5954 (PCIE),
        ATI Radeon XPRESS 200M 5955 (PCIE), ATI Radeon 9250 5960 (AGP),
        ATI Radeon 9200 5961 (AGP), ATI Radeon 9200 5962 (AGP),
        ATI Radeon 9200SE 5964 (AGP), ATI FireMV 2200 (PCI),
        ATI ES1000 5969 (PCI), ATI Radeon XPRESS 200 5974 (PCIE),
        ATI Radeon XPRESS 200M 5975 (PCIE),
        ATI Radeon XPRESS 200 5A41 (PCIE),
        ATI Radeon XPRESS 200M 5A42 (PCIE),
        ATI Radeon XPRESS 200 5A61 (PCIE),
        ATI Radeon XPRESS 200M 5A62 (PCIE),
        ATI Radeon X300 (RV370) 5B60 (PCIE),
        ATI Radeon X600 (RV370) 5B62 (PCIE),
        ATI Radeon X550 (RV370) 5B63 (PCIE),
        ATI FireGL V3100 (RV370) 5B64 (PCIE),
        ATI FireMV 2200 PCIE (RV370) 5B65 (PCIE),
        ATI Radeon Mobility 9200 (M9+) 5C61 (AGP),
        ATI Radeon Mobility 9200 (M9+) 5C63 (AGP),
        ATI Mobility Radeon X800 XT (M28) (PCIE),
        ATI Mobility FireGL V5100 (M28) (PCIE),
        ATI Mobility Radeon X800 (M28) (PCIE), ATI Radeon X850 5D4C (PCIE),
        ATI Radeon X850 XT PE (R480) (PCIE),
        ATI Radeon X850 SE (R480) (PCIE), ATI Radeon X850 PRO (R480) (PCIE),
        ATI unknown Radeon / FireGL (R480) 5D50 (PCIE),
        ATI Radeon X850 XT (R480) (PCIE),
        ATI Radeon X800XT (R423) 5D57 (PCIE),
        ATI FireGL V5000 (RV410) (PCIE), ATI Radeon X700 XT (RV410) (PCIE),
        ATI Radeon X700 PRO (RV410) (PCIE),
        ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X700 (RV410) (PCIE),
        ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X1800,
        ATI Mobility Radeon X1800 XT, ATI Mobility Radeon X1800,
        ATI Mobility FireGL V7200, ATI FireGL V7200, ATI FireGL V5300,
        ATI Mobility FireGL V7100, ATI Radeon X1800, ATI Radeon X1800,
        ATI Radeon X1800, ATI Radeon X1800, ATI Radeon X1800,
        ATI FireGL V7300, ATI FireGL V7350, ATI Radeon X1600, ATI RV505,
        ATI Radeon X1300/X1550, ATI Radeon X1550, ATI M54-GL,
        ATI Mobility Radeon X1400, ATI Radeon X1300/X1550,
        ATI Radeon X1550 64-bit, ATI Mobility Radeon X1300,
        ATI Mobility Radeon X1300, ATI Mobility Radeon X1300,
        ATI Mobility Radeon X1300, ATI Radeon X1300, ATI Radeon X1300,
        ATI RV505, ATI RV505, ATI FireGL V3300, ATI FireGL V3350,
        ATI Radeon X1300, ATI Radeon X1550 64-bit, ATI Radeon X1300/X1550,
        ATI Radeon X1600, ATI Radeon X1300/X1550, ATI Mobility Radeon X1450,
        ATI Radeon X1300/X1550, ATI Mobility Radeon X2300,
        ATI Mobility Radeon X2300, ATI Mobility Radeon X1350,
        ATI Mobility Radeon X1350, ATI Mobility Radeon X1450,
        ATI Radeon X1300, ATI Radeon X1550, ATI Mobility Radeon X1350,
        ATI FireMV 2250, ATI Radeon X1550 64-bit, ATI Radeon X1600,
        ATI Radeon X1650, ATI Radeon X1600, ATI Radeon X1600,
        ATI Mobility FireGL V5200, ATI Mobility Radeon X1600,
        ATI Radeon X1650, ATI Radeon X1650, ATI Radeon X1600,
        ATI Radeon X1300 XT/X1600 Pro, ATI FireGL V3400,
        ATI Mobility FireGL V5250, ATI Mobility Radeon X1700,
        ATI Mobility Radeon X1700 XT, ATI FireGL V5200,
        ATI Mobility Radeon X1700, ATI Radeon X2300HD,
        ATI Mobility Radeon HD 2300, ATI Mobility Radeon HD 2300,
        ATI Radeon X1950, ATI Radeon X1900, ATI Radeon X1950,
        ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
        ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
        ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
        ATI AMD Stream Processor, ATI Radeon X1900, ATI Radeon X1950,
        ATI RV560, ATI RV560, ATI Mobility Radeon X1900, ATI RV560,
        ATI Radeon X1950 GT, ATI RV570, ATI RV570, ATI FireGL V7400,
        ATI RV560, ATI Radeon X1650, ATI Radeon X1650, ATI RV560,
        ATI Radeon 9100 PRO IGP 7834, ATI Radeon Mobility 9200 IGP 7835,
        ATI Radeon X1200, ATI Radeon X1200, ATI Radeon X1200,
        ATI Radeon X1200, ATI Radeon X1200, ATI RS740, ATI RS740M, ATI RS740,
        ATI RS740M, ATI Radeon HD 2900 XT, ATI Radeon HD 2900 XT,
        ATI Radeon HD 2900 XT, ATI Radeon HD 2900 Pro, ATI Radeon HD 2900 GT,
        ATI FireGL V8650, ATI FireGL V8600, ATI FireGL V7600,
        ATI Radeon 4800 Series, ATI Radeon HD 4870 x2,
        ATI Radeon 4800 Series, ATI Radeon HD 4850 x2,
        ATI FirePro V8750 (FireGL), ATI FirePro V7760 (FireGL),
        ATI Mobility RADEON HD 4850, ATI Mobility RADEON HD 4850 X2,
        ATI Radeon 4800 Series, ATI FirePro RV770, AMD FireStream 9270,
        AMD FireStream 9250, ATI FirePro V8700 (FireGL),
        ATI Mobility RADEON HD 4870, ATI Mobility RADEON M98,
        ATI Mobility RADEON HD 4870, ATI Radeon 4800 Series,
        ATI Radeon 4800 Series, ATI FirePro M7750, ATI M98, ATI M98, ATI M98,
        ATI Mobility Radeon HD 4650, ATI Radeon RV730 (AGP),
        ATI Mobility Radeon HD 4670, ATI FirePro M5750,
        ATI Mobility Radeon HD 4670, ATI Radeon RV730 (AGP),
        ATI RV730XT [Radeon HD 4670], ATI RADEON E4600,
        ATI Radeon HD 4600 Series, ATI RV730 PRO [Radeon HD 4650],
        ATI FirePro V7750 (FireGL), ATI FirePro V5700 (FireGL),
        ATI FirePro V3750 (FireGL), ATI Mobility Radeon HD 4830,
        ATI Mobility Radeon HD 4850, ATI FirePro M7740, ATI RV740,
        ATI Radeon HD 4770, ATI Radeon HD 4700 Series, ATI Radeon HD 4770,
        ATI FirePro M5750, ATI RV610, ATI Radeon HD 2400 XT,
        ATI Radeon HD 2400 Pro, ATI Radeon HD 2400 PRO AGP, ATI FireGL V4000,
        ATI RV610, ATI Radeon HD 2350, ATI Mobility Radeon HD 2400 XT,
        ATI Mobility Radeon HD 2400, ATI RADEON E2400, ATI RV610,
        ATI FireMV 2260, ATI RV670, ATI Radeon HD3870,
        ATI Mobility Radeon HD 3850, ATI Radeon HD3850,
        ATI Mobility Radeon HD 3850 X2, ATI RV670,
        ATI Mobility Radeon HD 3870, ATI Mobility Radeon HD 3870 X2,
        ATI Radeon HD3870 X2, ATI FireGL V7700, ATI Radeon HD3850,
        ATI Radeon HD3690, AMD Firestream 9170, ATI Radeon HD 4550,
        ATI Radeon RV710, ATI Radeon RV710, ATI Radeon RV710,
        ATI Radeon HD 4350, ATI Mobility Radeon 4300 Series,
        ATI Mobility Radeon 4500 Series, ATI Mobility Radeon 4500 Series,
        ATI FirePro RG220, ATI Mobility Radeon 4330, ATI RV630,
        ATI Mobility Radeon HD 2600, ATI Mobility Radeon HD 2600 XT,
        ATI Radeon HD 2600 XT AGP, ATI Radeon HD 2600 Pro AGP,
        ATI Radeon HD 2600 XT, ATI Radeon HD 2600 Pro, ATI Gemini RV630,
        ATI Gemini Mobility Radeon HD 2600 XT, ATI FireGL V5600,
        ATI FireGL V3600, ATI Radeon HD 2600 LE,
        ATI Mobility FireGL Graphics Processor, ATI Radeon HD 3470,
        ATI Mobility Radeon HD 3430, ATI Mobility Radeon HD 3400 Series,
        ATI Radeon HD 3450, ATI Radeon HD 3450, ATI Radeon HD 3430,
        ATI Radeon HD 3450, ATI FirePro V3700, ATI FireMV 2450,
        ATI FireMV 2260, ATI FireMV 2260, ATI Radeon HD 3600 Series,
        ATI Radeon HD 3650 AGP, ATI Radeon HD 3600 PRO,
        ATI Radeon HD 3600 XT, ATI Radeon HD 3600 PRO,
        ATI Mobility Radeon HD 3650, ATI Mobility Radeon HD 3670,
        ATI Mobility FireGL V5700, ATI Mobility FireGL V5725,
        ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
        ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
        ATI Radeon HD 3300 Graphics, ATI Radeon HD 3200 Graphics,
        ATI Radeon 3000 Graphics, SUMO, SUMO, SUMO2, SUMO2, SUMO2, SUMO2,
        SUMO, SUMO, SUMO, SUMO, SUMO, SUMO, SUMO, SUMO, ATI Radeon HD 4200,
        ATI Radeon 4100, ATI Mobility Radeon HD 4200,
        ATI Mobility Radeon 4100, ATI Radeon HD 4290, ATI Radeon HD 4250,
        AMD Radeon HD 6310 Graphics, AMD Radeon HD 6310 Graphics,
        AMD Radeon HD 6250 Graphics, AMD Radeon HD 6250 Graphics,
        AMD Radeon HD 6300 Series Graphics,
        AMD Radeon HD 6200 Series Graphics, PALM, PALM, PALM, CYPRESS,
        ATI FirePro (FireGL) Graphics Adapter,
        ATI FirePro (FireGL) Graphics Adapter,
        ATI FirePro (FireGL) Graphics Adapter, AMD Firestream 9370,
        AMD Firestream 9350, ATI Radeon HD 5800 Series,
        ATI Radeon HD 5800 Series, ATI Radeon HD 5800 Series,
        ATI Radeon HD 5800 Series, ATI Radeon HD 5900 Series,
        ATI Radeon HD 5900 Series, ATI Mobility Radeon HD 5800 Series,
        ATI Mobility Radeon HD 5800 Series,
        ATI FirePro (FireGL) Graphics Adapter,
        ATI FirePro (FireGL) Graphics Adapter,
        ATI Mobility Radeon HD 5800 Series, ATI Radeon HD 5700 Series,
        ATI Radeon HD 5700 Series, ATI Radeon HD 6700 Series,
        ATI Radeon HD 5700 Series, ATI Radeon HD 6700 Series,
        ATI Mobility Radeon HD 5000 Series,
        ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon HD 5570,
        ATI FirePro (FireGL) Graphics Adapter,
        ATI FirePro (FireGL) Graphics Adapter, ATI Radeon HD 5670,
        ATI Radeon HD 5570, ATI Radeon HD 5500 Series, REDWOOD,
        ATI Mobility Radeon HD 5000 Series,
        ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon Graphics,
        ATI Mobility Radeon Graphics, CEDAR,
        ATI FirePro (FireGL) Graphics Adapter,
        ATI FirePro (FireGL) Graphics Adapter, ATI FirePro 2270, CEDAR,
        ATI Radeon HD 5450, CEDAR, CEDAR, CAYMAN, CAYMAN, CAYMAN, CAYMAN,
        CAYMAN, CAYMAN, CAYMAN, CAYMAN, CAYMAN, CAYMAN,
        AMD Radeon HD 6900 Series, AMD Radeon HD 6900 Series, CAYMAN, CAYMAN,
        CAYMAN, AMD Radeon HD 6900M Series, Mobility Radeon HD 6000 Series,
        BARTS, BARTS, Mobility Radeon HD 6000 Series,
        Mobility Radeon HD 6000 Series, BARTS, BARTS, BARTS, BARTS,
        AMD Radeon HD 6800 Series, AMD Radeon HD 6800 Series,
        AMD Radeon HD 6700 Series, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
        TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
        TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
        CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS,
        CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, ARUBA, ARUBA,
        ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA,
        ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA,
        ARUBA, ARUBA, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI,
        TAHITI, TAHITI, TAHITI, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN,
        PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN,
        PITCAIRN, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE,
        VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE,
        VERDE, VERDE
[    35.244] (II) VESA: driver for VESA chipsets: vesa
[    35.244] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    35.244] (II) FBDEV: driver for framebuffer: fbdev
[    35.244] (++) using VT number 7


[    35.279] (II) [KMS] Kernel modesetting enabled.
[    35.279] (WW) Falling back to old probe method for vesa
[    35.279] (WW) Falling back to old probe method for modesetting
[    35.279] (WW) Falling back to old probe method for fbdev
[    35.279] (II) Loading sub module "fbdevhw"
[    35.279] (II) LoadModule: "fbdevhw"
[    35.279] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    35.299] (II) Module fbdevhw: vendor="X.Org Foundation"
[    35.299]    compiled for 1.13.0, module version = 0.0.2
[    35.299]    ABI class: X.Org Video Driver, version 13.0
[    35.299] (II) RADEON(0): Creating default Display subsection in Screen section
        "Default Screen Section" for depth/fbbpp 24/32
[    35.299] (==) RADEON(0): Depth 24, (--) framebuffer bpp 32
[    35.299] (II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    35.299] (==) RADEON(0): Default visual is TrueColor
[    35.299] (==) RADEON(0): RGB weight 888
[    35.299] (II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
[    35.299] (--) RADEON(0): Chipset: "ATI Radeon X1300/X1550" (ChipID = 0x7142)
[    35.299] (II) Loading sub module "dri2"
[    35.299] (II) LoadModule: "dri2"
[    35.299] (II) Module "dri2" already built-in
[    35.299] (II) Loading sub module "exa"
[    35.299] (II) LoadModule: "exa"
[    35.299] (II) Loading /usr/lib/xorg/modules/libexa.so
[    35.323] (II) Module exa: vendor="X.Org Foundation"
[    35.323]    compiled for 1.13.0, module version = 2.6.0
[    35.323]    ABI class: X.Org Video Driver, version 13.0
[    35.323] (II) RADEON(0): KMS Color Tiling: enabled
[    35.323] (II) RADEON(0): KMS Pageflipping: enabled
[    35.323] (II) RADEON(0): SwapBuffers wait for vsync: enabled
[    35.364] (II) RADEON(0): Output DVI-0 has no monitor section
[    35.384] (II) RADEON(0): Output S-video has no monitor section
[    35.424] (II) RADEON(0): Output VGA-0 has no monitor section
[    35.464] (II) RADEON(0): EDID for output DVI-0
[    35.484] (II) RADEON(0): EDID for output S-video
[    35.484] (II) RADEON(0): Printing probed modes for output S-video
[    35.484] (II) RADEON(0): Modeline "1024x768"x59.9   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync (47.8 kHz)
[    35.484] (II) RADEON(0): Modeline "800x600"x59.9   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz)
[    35.484] (II) RADEON(0): Modeline "848x480"x59.7   31.50  848 872 952 1056  480 483 493 500 -hsync +vsync (29.8 kHz)
[    35.484] (II) RADEON(0): Modeline "720x480"x59.7   26.75  720 744 808 896  480 483 493 500 -hsync +vsync (29.9 kHz)
[    35.484] (II) RADEON(0): Modeline "640x480"x59.4   23.75  640 664 720 800  480 483 487 500 -hsync +vsync (29.7 kHz)
[    35.524] (II) RADEON(0): EDID for output VGA-0
[    35.524] (II) RADEON(0): Output DVI-0 disconnected
[    35.524] (II) RADEON(0): Output S-video connected
[    35.524] (II) RADEON(0): Output VGA-0 disconnected
[    35.524] (II) RADEON(0): Using exact sizes for initial modes
[    35.524] (II) RADEON(0): Output S-video using initial mode 1024x768
[    35.524] (II) RADEON(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    35.524] (II) RADEON(0): mem size init: gart size :1fdff000 vram size: s:10000000 visible:fcc0000
[    35.524] (II) RADEON(0): EXA: Driver will allow EXA pixmaps in VRAM
[    35.524] (==) RADEON(0): DPI set to (96, 96)
[    35.524] (II) Loading sub module "fb"
[    35.524] (II) LoadModule: "fb"
[    35.524] (II) Loading /usr/lib/xorg/modules/libfb.so
[    35.532] (II) Module fb: vendor="X.Org Foundation"
[    35.532]    compiled for 1.13.0, module version = 1.0.0
[    35.532]    ABI class: X.Org ANSI C Emulation, version 0.4
[    35.532] (II) Loading sub module "ramdac"
[    35.532] (II) LoadModule: "ramdac"
[    35.532] (II) Module "ramdac" already built-in
[    35.532] (II) UnloadModule: "vesa"
[    35.532] (II) Unloading vesa
[    35.532] (II) UnloadModule: "modesetting"
[    35.532] (II) Unloading modesetting
[    35.532] (II) UnloadModule: "fbdev"
[    35.532] (II) Unloading fbdev
[    35.532] (II) UnloadSubModule: "fbdevhw"
[    35.532] (II) Unloading fbdevhw
[    35.532] (--) Depth 24 pixmap format is 32 bpp
[    35.538] (II) RADEON(0): [DRI2] Setup complete
[    35.538] (II) RADEON(0): [DRI2]   DRI driver: r300
[    35.538] (II) RADEON(0): [DRI2]   VDPAU driver: r300
[    35.538] (II) RADEON(0): Front buffer size: 3072K
[    35.538] (II) RADEON(0): VRAM usage limit set to 230169K
[    35.539] (==) RADEON(0): Backing store disabled
[    35.539] (II) RADEON(0): Direct rendering enabled
[    35.539] (II) RADEON(0): Render acceleration enabled for R300/R400/R500 type cards.
[    35.539] (II) RADEON(0): Setting EXA maxPitchBytes
[    35.539] (II) EXA(0): Driver allocated offscreen pixmaps
[    35.539] (II) EXA(0): Driver registered support for the following operations:
[    35.539] (II)         Solid
[    35.539] (II)         Copy
[    35.539] (II)         Composite (RENDER acceleration)
[    35.539] (II)         UploadToScreen
[    35.539] (II)         DownloadFromScreen
[    35.539] (II) RADEON(0): Acceleration enabled
[    35.539] (==) RADEON(0): DPMS enabled
[    35.539] (==) RADEON(0): Silken mouse enabled
[    35.539] (II) RADEON(0): Set up textured video
[    35.539] (II) RADEON(0): [XvMC] Associated with Radeon Textured Video.
[    35.539] (II) RADEON(0): [XvMC] Extension initialized.
[    35.539] (II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    35.556] (--) RandR disabled
[    36.512] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    36.512] (II) AIGLX: enabled GLX_INTEL_swap_event
[    36.512] (II) AIGLX: enabled GLX_ARB_create_context
[    36.512] (II) AIGLX: enabled GLX_ARB_create_context_profile
[    36.512] (II) AIGLX: enabled GLX_EXT_create_context_es2_profile
[    36.512] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    36.512] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    36.513] (II) AIGLX: Loaded and initialized r300
[    36.513] (II) GLX: Initialized DRI2 GL provider for screen 0
[    36.513] (II) RADEON(0): Setting screen physical size to 270 x 203
[    36.706] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    36.715] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    36.715] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    36.715] (II) LoadModule: "evdev"
[    36.715] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    36.769] (II) Module evdev: vendor="X.Org Foundation"
[    36.769]    compiled for 1.13.0, module version = 2.7.3
[    36.769]    Module class: X.Org XInput Driver
[    36.769]    ABI class: X.Org XInput driver, version 18.0
[    36.769] (II) Using input driver 'evdev' for 'Power Button'
[    36.769] (**) Power Button: always reports core events
[    36.769] (**) evdev: Power Button: Device: "/dev/input/event1"
[    36.769] (--) evdev: Power Button: Vendor 0 Product 0x1
[    36.769] (--) evdev: Power Button: Found keys
[    36.769] (II) evdev: Power Button: Configuring as keyboard
[    36.769] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    36.769] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    36.769] (**) Option "xkb_rules" "evdev"
[    36.769] (**) Option "xkb_model" "pc105"
[    36.769] (**) Option "xkb_layout" "us"
[    36.770] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    36.770] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    36.770] (II) Using input driver 'evdev' for 'Power Button'
[    36.770] (**) Power Button: always reports core events
[    36.770] (**) evdev: Power Button: Device: "/dev/input/event0"
[    36.770] (--) evdev: Power Button: Vendor 0 Product 0x1
[    36.770] (--) evdev: Power Button: Found keys
[    36.770] (II) evdev: Power Button: Configuring as keyboard
[    36.770] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
[    36.770] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    36.770] (**) Option "xkb_rules" "evdev"
[    36.770] (**) Option "xkb_model" "pc105"
[    36.770] (**) Option "xkb_layout" "us"
[    36.771] (II) config/udev: Adding input device Logitech USB Optical Mouse (/dev/input/event2)
[    36.771] (**) Logitech USB Optical Mouse: Applying InputClass "evdev pointer catchall"
[    36.771] (II) Using input driver 'evdev' for 'Logitech USB Optical Mouse'
[    36.771] (**) Logitech USB Optical Mouse: always reports core events
[    36.771] (**) evdev: Logitech USB Optical Mouse: Device: "/dev/input/event2"
[    36.771] (--) evdev: Logitech USB Optical Mouse: Vendor 0x46d Product 0xc05a
[    36.771] (--) evdev: Logitech USB Optical Mouse: Found 12 mouse buttons
[    36.771] (--) evdev: Logitech USB Optical Mouse: Found scroll wheel(s)
[    36.771] (--) evdev: Logitech USB Optical Mouse: Found relative axes
[    36.771] (--) evdev: Logitech USB Optical Mouse: Found x and y relative axes
[    36.771] (II) evdev: Logitech USB Optical Mouse: Configuring as mouse
[    36.771] (II) evdev: Logitech USB Optical Mouse: Adding scrollwheel support
[    36.771] (**) evdev: Logitech USB Optical Mouse: YAxisMapping: buttons 4 and 5
[    36.771] (**) evdev: Logitech USB Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    36.771] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:02.0/usb2/2-1/2-1:1.0/input/input2/event2"
[    36.771] (II) XINPUT: Adding extended input device "Logitech USB Optical Mouse" (type: MOUSE, id 8)
[    36.771] (II) evdev: Logitech USB Optical Mouse: initialized for relative axes.
[    36.771] (**) Logitech USB Optical Mouse: (accel) keeping acceleration scheme 1
[    36.771] (**) Logitech USB Optical Mouse: (accel) acceleration profile 0
[    36.771] (**) Logitech USB Optical Mouse: (accel) acceleration factor: 2.000
[    36.771] (**) Logitech USB Optical Mouse: (accel) acceleration threshold: 4
[    36.772] (II) config/udev: Adding input device Logitech USB Optical Mouse (/dev/input/mouse0)
[    36.772] (II) No input driver specified, ignoring this device.
[    36.772] (II) This device may have been added with another device file.
[    36.772] (II) config/udev: Adding input device Mitsumi Electric Apple USB Keyboard (/dev/input/event3)
[    36.772] (**) Mitsumi Electric Apple USB Keyboard: Applying InputClass "evdev keyboard catchall"
[    36.772] (II) Using input driver 'evdev' for 'Mitsumi Electric Apple USB Keyboard'
[    36.772] (**) Mitsumi Electric Apple USB Keyboard: always reports core events
[    36.772] (**) evdev: Mitsumi Electric Apple USB Keyboard: Device: "/dev/input/event3"
[    36.772] (--) evdev: Mitsumi Electric Apple USB Keyboard: Vendor 0x5ac Product 0x201
[    36.772] (--) evdev: Mitsumi Electric Apple USB Keyboard: Found keys
[    36.772] (II) evdev: Mitsumi Electric Apple USB Keyboard: Configuring as keyboard
[    36.772] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:02.0/usb2/2-2/2-2.1/2-2.1:1.0/input/input3/event3"
[    36.772] (II) XINPUT: Adding extended input device "Mitsumi Electric Apple USB Keyboard" (type: KEYBOARD, id 9)
[    36.772] (**) Option "xkb_rules" "evdev"
[    36.772] (**) Option "xkb_model" "pc105"
[    36.772] (**) Option "xkb_layout" "us"
[    36.773] (II) config/udev: Adding drm device (/dev/dri/card0)
media@MediaBox-Linux:~$
```

dpkg -l | grep linux-image
```
media@MediaBox-Linux:~$ dpkg -l | grep linux-imageii  linux-image-3.5.0-23-generic                 3.5.0-23.35~precise1                             Linux kernel image for version 3.5.0 on 64 bit x86 SMP
ii  linux-image-3.5.0-46-generic                 3.5.0-46.70~precise1                             Linux kernel image for version 3.5.0 on 64 bit x86 SMP
ii  linux-image-generic-lts-quantal              3.5.0.46.52                                      Generic Linux kernel image
```

ls -la /usr/src    ls -la /boot

```
media@MediaBox-Linux:~$ uname -r3.5.0-46-generic


media@MediaBox-Linux:~$ ls -la /usr/src
total 24
drwxr-xr-x  6 root root 4096 Feb 21 02:32 .
drwxr-xr-x 10 root root 4096 Feb 13  2013 ..
drwxr-xr-x 24 root root 4096 Feb 13  2013 linux-headers-3.5.0-23
drwxr-xr-x  7 root root 4096 Feb 13  2013 linux-headers-3.5.0-23-generic
drwxr-xr-x 24 root root 4096 Feb 21 02:32 linux-headers-3.5.0-46
drwxr-xr-x  7 root root 4096 Feb 21 02:32 linux-headers-3.5.0-46-generic


media@MediaBox-Linux:~$ ls -la /boot
total 48900
drwxr-xr-x  3 root root     4096 Feb 21 02:39 .
drwxr-xr-x 24 root root     4096 Feb 21 02:38 ..
-rw-r--r--  1 root root   848290 Jan 25  2013 abi-3.5.0-23-generic
-rw-r--r--  1 root root   853401 Jan  9 19:17 abi-3.5.0-46-generic
-rw-r--r--  1 root root   147880 Jan 25  2013 config-3.5.0-23-generic
-rw-r--r--  1 root root   148157 Jan  9 19:17 config-3.5.0-46-generic
drwxr-xr-x  3 root root    12288 Feb 21 02:39 grub
-rw-r--r--  1 root root 15544243 Feb 21 02:23 initrd.img-3.5.0-23-generic
-rw-r--r--  1 root root 15697393 Feb 21 02:39 initrd.img-3.5.0-46-generic
-rw-r--r--  1 root root   176764 Nov 27  2011 memtest86+.bin
-rw-r--r--  1 root root   178944 Nov 27  2011 memtest86+_multiboot.bin
-rw-------  1 root root  3023265 Jan 25  2013 System.map-3.5.0-23-generic
-rw-------  1 root root  3024310 Jan  9 19:17 System.map-3.5.0-46-generic
-rw-r--r--  1 root root  5189248 Feb 21 01:58 vmlinuz-3.5.0-23-generic
-rw-------  1 root root  5191168 Jan  9 19:17 vmlinuz-3.5.0-46-generic
```

grep -B3 -A10 "Package: linux-image" /var/lib/dpkg/status
```
media@MediaBox-Linux:~$ grep -B3 -A10 "Package: linux-image" /var/lib/dpkg/statusHomepage: http://code.google.com/p/ibus/
Original-Maintainer: IME Packaging Team <pkg-ime-devel@lists.alioth.debian.org>


Package: linux-image-3.5.0-46-generic
Status: install ok installed
Priority: optional
Section: kernel
Installed-Size: 153942
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Architecture: amd64
Source: linux-lts-quantal
Version: 3.5.0-46.70~precise1
Provides: fuse-module, ivtv-modules, kvm-api-4, linux-image, linux-image-3.0, ndiswrapper-modules-1.9, redhat-cluster-modules
Depends: initramfs-tools (>= 0.36ubuntu6), module-init-tools (>= 3.3-pre11-4ubuntu3), crda (>= 1.1.1-1ubuntu2) | wireless-crda
--
Original-Maintainer: Masayuki Hatta (mhatta) <mhatta@debian.org>
Homepage: http://www.ghostscript.com/


Package: linux-image-generic-lts-quantal
Status: install ok installed
Priority: optional
Section: metapackages
Installed-Size: 28
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Architecture: amd64
Source: linux-meta-lts-quantal
Version: 3.5.0.46.52
Depends: linux-image-3.5.0-46-generic, linux-firmware
Description: Generic Linux kernel image
--
Original-Maintainer: Debian LibreOffice Maintainers <debian-openoffice@lists.debian.org>
Homepage: http://hunspell.sourceforge.net/


Package: linux-image-3.5.0-23-generic
Status: install ok installed
Priority: optional
Section: kernel
Installed-Size: 152477
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Architecture: amd64
Source: linux-lts-quantal
Version: 3.5.0-23.35~precise1
Depends: initramfs-tools (>= 0.36ubuntu6), module-init-tools (>= 3.3-pre11-4ubuntu3), crda (>= 1.1.1-1ubuntu2) | wireless-crda
Pre-Depends: dpkg (>= 1.10.24)
```

I hope that your dog is okay

ps do you still want me to run that last code for installing the saucy kernel?

---

### Post by Bashing-om on 2014-02-21
Jeremy_Gordy; Hey,

Yeah, I still think we ought to upgrade the HWE stack to suacy (quantal is End Of Life next April). See then if there continues an issue with s-video.

Our dog: somewhat livelier this AM and we are holding off on taking her to the vet, she is able to eat a bit and drink a little water so that situation has improved. I guess she expelled all the contents of her stomach - what messes ! -. Today there has been no discharges, so we are hopping for the best.

when all else fails ->
[INDENT][INDENT]blame the kernel (not !)
[/INDENT][/INDENT]

---

### Post by Jeremy_Gordy on 2014-02-21
sorry I have been away since my last post, I had to go shopping. I'm glad that your dog doing better, hope he continues to get better as well.

okay i just starting running those codes shouldn't be to long and i will be able to give an update

---

### Post by Jeremy_Gordy on 2014-02-21
ok so i ran all of those commands and im still having scrambled S-video

```

media@MediaBox-Linux:~$ uname -r
3.11.0-17-generic

```

---

### Post by coldraven on 2014-02-22
Would that be in any way connected to this X1250 bug? It should not affect 12.04 but maybe some Compiz setting has been corrupted or changed.
[http://askubuntu.com/questions/285525/dash-background-blur-problem](http://askubuntu.com/questions/285525/dash-background-blur-problem)

I have the useless X1250 card myself, currently in 2D mode because 3D scrambles the text in text boxes in Ubuntu 12.04.

---

### Post by Bashing-om on 2014-02-22
Jeremy_Gordy; A disappointment !

coldraven has a good point - input most appreciated !- ,
Might try the graphics in 2D mode ? and see what results ?

Others may have a better solution, but, Ya want to revert back to the 12.04 kernel ?
Doing so, might be a chore to maintain grub in the future at this point.

I do not know that there is a means to remove the HES once enabled (??).

sometimes,
[INDENT][INDENT]there just ain't a good solution
[/INDENT][/INDENT]

---

### Post by Jeremy_Gordy on 2014-02-23
Thanks coldraven but no, the problem is only on S-video scrambling the whole desktop, like everything is unreadable, but nothing is messed up when i have a regular computer monitor hooked up to it. switching to 2D mode doesn't change anything either.

as sad as it make me say this i might just have to switch the pc back over to windows ](*,) :cry:

---

### Post by Bashing-om on 2014-02-26
Jeremy_Gordy; Hey !

Sorry to have left ya high and dry. I have lost internet connectivity to my machine, soon as I get it resolved I will be back.

In the meantime, what results from the liveDVD environment ? (preferably 12.04.1, the legacy release that has the old x-server).

Trial troubles and tribulations
[INDENT][INDENT]keeps things interesting
[/INDENT][/INDENT]

---

