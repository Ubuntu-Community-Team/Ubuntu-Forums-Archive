---
title: "Boot process doesn't complete .Hangs at Bluetooth starting"
date: 2012-01-01
forum: New to Ubuntu
---

### Post by ask_ on 2012-01-01
I have installed Lubuntu11.10 on an old intel PC. It has 2GHz , 248 MB ram.6 GB free hard disk.


The boot process hangs indefinitely on 'Starting Bluetooth'.

I am able to load a terminal via Alt-F2.

What should I do?

---

### Post by ask_ on 2012-01-01
is there a way to start a GUI from the command line.

I tried using 'startx' command, but it didn't work.

Could you suggest any commands so as to help pinpoint my problem to you people.

My Status is as follows :-

I am able to load a console of Lubuntu, insted of a GUI.

(able to run apt-get commands, as internet is working from the terminal)

---

### Post by 2F4U on 2012-01-01
On GUI related problems I would first look into
- /var/log/Xorg.0.log
- .xsession-errors in your home folder

Is this behaviour from a liveCD or did you manage somehow to install the system. If you did not manage to install the system, it may be due to not having enough RAM for the graphical installer. Lubuntu provides an alternate install CD which should also work with your amount of RAM.

---

### Post by ask_ on 2012-01-02
I managed to install the system , I think. Because I am getting a GRUB menu at startup , which gives option to load to Lubuntu(although it is written Ubuntu 11.10 in GRUB menu) and Windows XP.

Lubuntu loading bar gives way to the "bluetooth starting" screen and it stops there indefinitely.

Pressing alt+F2 at this moment gives me a command line console.

I opened the file  - /var/log/Xorg.0.log . 
it says Fatal Server Error : No screens found. I will post detailed contents of the file below :-

```
[  3049.517] 
X.Org X Server 1.10.4
Release Date: 2011-08-19
[  3049.517] X Protocol Version 11, Revision 0
[  3049.518] Build Operating System: Linux 2.6.24-29-server i686 Ubuntu
[  3049.518] Current Operating System: Linux ubuntuumesh 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:50:42 UTC 2011 i686
[  3049.518] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-12-generic root=UUID=b3e8235a-215b-469b-bc4a-aa97dcb0b9ac ro quiet splash vt.handoff=7
[  3049.518] Build Date: 19 October 2011  05:09:41AM
[  3049.518] xorg-server 2:1.10.4-1ubuntu4.2 (For technical support please see http://www.ubuntu.com/support) 
[  3049.518] Current version of pixman: 0.22.2
[  3049.518]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[  3049.519] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[  3049.519] (==) Log file: "/var/log/Xorg.0.log", Time: Mon Jan  2 14:11:36 2012
[  3049.520] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[  3049.520] (==) No Layout section.  Using the first Screen section.
[  3049.520] (==) No screen section available. Using defaults.
[  3049.520] (**) |-->Screen "Default Screen Section" (0)
[  3049.521] (**) |   |-->Monitor "<default monitor>"
[  3049.521] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[  3049.521] (==) Automatically adding devices
[  3049.521] (==) Automatically enabling devices
[  3049.521] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[  3049.521]     Entry deleted from font path.
[  3049.521] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[  3049.521]     Entry deleted from font path.
[  3049.521] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[  3049.521]     Entry deleted from font path.
[  3049.521] (WW) The directory "/usr/share/fonts/X11/Type1" does not exist.
[  3049.521]     Entry deleted from font path.
[  3049.521] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[  3049.521]     Entry deleted from font path.
[  3049.521] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[  3049.521]     Entry deleted from font path.
[  3049.521] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[  3049.521]     Entry deleted from font path.
[  3049.521] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    built-ins
[  3049.521] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[  3049.521] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[  3049.521] (II) Loader magic: 0x823ada0
[  3049.521] (II) Module ABI versions:
[  3049.522]     X.Org ANSI C Emulation: 0.4
[  3049.522]     X.Org Video Driver: 10.0
[  3049.522]     X.Org XInput driver : 12.3
[  3049.522]     X.Org Server Extension : 5.0
[  3049.523] (--) PCI:*(0:0:2:0) 8086:2562:1458:2562 rev 3, Mem @ 0xe0000000/134217728, 0xea000000/524288
[  3049.523] (WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
[  3049.523] (II) LoadModule: "extmod"
[  3049.523] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[  3049.524] (II) Module extmod: vendor="X.Org Foundation"
[  3049.524]     compiled for 1.10.4, module version = 1.0.0
[  3049.524]     Module class: X.Org Server Extension
[  3049.524]     ABI class: X.Org Server Extension, version 5.0
[  3049.524] (II) Loading extension MIT-SCREEN-SAVER
[  3049.524] (II) Loading extension XFree86-VidModeExtension
[  3049.524] (II) Loading extension XFree86-DGA
[  3049.524] (II) Loading extension DPMS
[  3049.524] (II) Loading extension XVideo
[  3049.524] (II) Loading extension XVideo-MotionCompensation
[  3049.524] (II) Loading extension X-Resource
[  3049.524] (II) LoadModule: "dbe"
[  3049.524] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[  3049.525] (II) Module dbe: vendor="X.Org Foundation"
[  3049.525]     compiled for 1.10.4, module version = 1.0.0
[  3049.525]     Module class: X.Org Server Extension
[  3049.525]     ABI class: X.Org Server Extension, version 5.0
[  3049.525] (II) Loading extension DOUBLE-BUFFER
[  3049.525] (II) LoadModule: "glx"
[  3049.525] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[  3049.525] (II) Module glx: vendor="X.Org Foundation"
[  3049.525]     compiled for 1.10.4, module version = 1.0.0
[  3049.525]     ABI class: X.Org Server Extension, version 5.0
[  3049.525] (==) AIGLX enabled
[  3049.525] (II) Loading extension GLX
[  3049.525] (II) LoadModule: "record"
[  3049.526] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[  3049.526] (II) Module record: vendor="X.Org Foundation"
[  3049.526]     compiled for 1.10.4, module version = 1.13.0
[  3049.526]     Module class: X.Org Server Extension
[  3049.526]     ABI class: X.Org Server Extension, version 5.0
[  3049.526] (II) Loading extension RECORD
[  3049.526] (II) LoadModule: "dri"
[  3049.526] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[  3049.527] (II) Module dri: vendor="X.Org Foundation"
[  3049.527]     compiled for 1.10.4, module version = 1.0.0
[  3049.527]     ABI class: X.Org Server Extension, version 5.0
[  3049.527] (II) Loading extension XFree86-DRI
[  3049.527] (II) LoadModule: "dri2"
[  3049.527] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[  3049.527] (II) Module dri2: vendor="X.Org Foundation"
[  3049.527]     compiled for 1.10.4, module version = 1.2.0
[  3049.527]     ABI class: X.Org Server Extension, version 5.0
[  3049.527] (II) Loading extension DRI2
[  3049.527] (==) Matched intel as autoconfigured driver 0
[  3049.527] (==) Matched vesa as autoconfigured driver 1
[  3049.527] (==) Matched fbdev as autoconfigured driver 2
[  3049.528] (==) Assigned the driver to the xf86ConfigLayout
[  3049.528] (II) LoadModule: "intel"
[  3049.528] (WW) Warning, couldn't open module intel
[  3049.528] (II) UnloadModule: "intel"
[  3049.528] (II) Unloading intel
[  3049.528] (EE) Failed to load module "intel" (module does not exist, 0)
[  3049.529] (II) LoadModule: "vesa"
[  3049.529] (WW) Warning, couldn't open module vesa
[  3049.529] (II) UnloadModule: "vesa"
[  3049.529] (II) Unloading vesa
[  3049.529] (EE) Failed to load module "vesa" (module does not exist, 0)
[  3049.529] (II) LoadModule: "fbdev"
[  3049.530] (WW) Warning, couldn't open module fbdev
[  3049.530] (II) UnloadModule: "fbdev"
[  3049.530] (II) Unloading fbdev
[  3049.530] (EE) Failed to load module "fbdev" (module does not exist, 0)
[  3049.530] (EE) No drivers available.
[  3049.530] 
Fatal server error:
[  3049.530] no screens found
[  3049.531] 
Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 
[  3049.531] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[  3049.531] 
```

I have installed alternate version of Lubuntu only. As it is said to work for below 160 MB Ram.

I couldn't find the file .xsession-errors in my home folder

---

### Post by ask_ on 2012-01-02
resolved :)

```
sudo apt-get install xserver-xorg-video-intel
```I found this from a separate thread for a similar problem.([http://ubuntuforums.org/showpost.php?p=6189009&postcount=3](http://ubuntuforums.org/showpost.php?p=6189009&postcount=3))
the above command did the trick.

startx works fine now.


Thanks. The xorg log file tip helped.

---

