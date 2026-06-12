---
title: "Machine with Radeon HD 6970 will not boot"
date: 2011-10-09
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by blinxwang on 2011-10-09
Hello,

I've done a fresh install of the latest daily build of Oneiric, and every time it boots purple rectangles replace the display every time. I've tried installing fglrx via recovery console and then booting, but this fails as well since I can't log in. Is there any way to fix this?

---

### Post by xgt001 on 2011-10-09
try adding nomodeset in the grub options and then boot.....

---

### Post by blinxwang on 2011-10-09
Tried that, still doesn't load to login screen.

---

### Post by ratcheer on 2011-10-09
Can you log in to Unity 2D?

This used to be a known problem, but it was fixed several weeks ago.

[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/819144](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/819144)

Tim

---

### Post by effenberg0x0 on 2011-10-09
I'm not sure if you can switch to a VT or not (don't know where your boot process is stuck). 

**1) Getting to a console**
-Try Ctrl+Alt+F1 to F6 to switch to a VT.
-If you cant, reboot and hold shift to see Grub and go to a recovery. Press "e" to edit the recovery kernel line. Make sure you don't have things like "splash" and "quiet" set there. "nomodeset" is OK. Proceed. Choose a prompt with networking

**2) Logging in:**
Login and run:
```

sudo service lightdm stop
sudo killall -s KILL /usr/bin/X
```As I mentioned, I don't know whether you'll do it from a VT or from recovery, so run these commands anyway. They are meant to stop GUI sessions so you have more chance of a stable enough system. 

At this point you should fully update / upgrade your system as this is supposedly already fixed. You can do that if you want to. But I say we remove fglrx first and install AMDs proprietary driver (Catalyst) for now to reduce risk.
[B]
3) Uninstall previous driver:[/B]
```
sudo apt-get remove --purge fglrx*
```Download Catalyst install:
```
cd
mkdir ati
cd ati
wget http://www2.ati.com/drivers/linux/ati-driver-installer-11-9-x86.x86_64.run
```Wait for the download to finish and run:
```
sudo sh ati-driver-installer-11-9-x86.x86_64.run --buildpkg Ubuntu/oneiric
sudo dpkg -i ati*.deb
sudo aticonfig --initial -f
```**4) Disable Plymouth, safer "text" grub.**
I've seen reports that it is a good idea to disable plymouth and graphic grub after ATI first install / conflicts. I would trust them now and tune my system later when everything is working better. If you concur, do this:

```
sudo nano /etc/default/grub
```Remove "splash" and "quiet" and add "text" to the line GRUB_CMDLINE_LINUX_DEFAULT=""

Press this to save the file and exit nano:
Ctrl+X, Y, <enter>

Update grub:
```
sudo update-grub
```Reboot your system:
```


sudo reboot now
```Hold shift to see the Grub menu and get to recovery. Choose a prompt with networking.
[B]
5)First boot with new VGA driver / Upgrade Ubuntu on recovery[/B]
Update & upgrade your setup:
```
sudo apt-get update && sudo apt-get upgrade

```Reboot your system:

[B]
6)Reboot / Make sure Grub line for main Kernel is OK before proceeding[/B]
```
sudo reboot now
```Hold shift to see grub. Press "e" over the main kernel line to edit it. Make sure there are no weird options at the end of the kernel line (you might have added some options when trying to fix it, they might still be there. "Splash", "quiet", should be avoided in this first boot (we want to see eventual error messages). I would remove "nomodeset" too at this point. Better play it safe. If they are there, delete and continue the boot process. 

I believe that would be enough to give you a working system.
Report back.

Good luck.

Effenberg

[B]EDIT: 
No Graphical user interface after boot (stuck at console)[/B]
- Reboot. Seriously, reboot at least once to see if it works.
- Make sure you cannot manually start a GUI session using "sudo service lightdm start".
- Switch to another VT using Ctrl+Alt+F1 to F6 if your current one don't offer you a login prompt. 
- After login, run these commands and report back the results at a new thread:
```
DISPLAY=:0.0 /usr/lib/nux/unity_support_test -p
glxinfo | grep -i "direct rendering"
sudo cat /var/log/Xorg.0.log 
dmesg | grep -i ati
```
Try to get the error message(s) you see to here so we have something to work with.

**No panel / launcher on Unity** **after Video Driver install**
- Try to follow the instructions posted here: [http://ubuntuforums.org/showthread.php?t=1856053](http://ubuntuforums.org/showthread.php?t=1856053)

**ATI Performance Glitches and potential Fixes**
Some users report small fixes that might help improve performance in your install. If you feel a sluggish performance in Unity or Gnome-Shell, try this fixes:

For Unity: [http://ubuntuforums.org/showpost.php?p=11323947&postcount=2](http://ubuntuforums.org/showpost.php?p=11323947&postcount=2)
For Gnome-Shell: [http://ubuntuforums.org/showpost.php?p=11327532&postcount=8](http://ubuntuforums.org/showpost.php?p=11327532&postcount=8)

---

### Post by alphacrucis2 on 2011-10-09
I can't get my Radeon HD3400 to work properly with the Catalyst 11.9 whereas it works fine with 11.8 from the Oneiric repos. 11.9 gives weird graphic artifacts for me.

---

### Post by ratcheer on 2011-10-10
effenburg0x0, your post #5 should be made into a permanent FAQ for anyone having severe ATI problems.

Tim

---

### Post by effenberg0x0 on 2011-10-10
Thanks Tim. Instead of constantly rewriting the same stuff, I though of writing one "more complete" post and redirect users there to save time. But Ubuntu, and even Gentoo, Arch wikis have such information and processes well documented. So it's not a unique contribution.

I've been working on a more complex piece of code, that should be able to run on console (curses) or GUI (GTK). It will be able to analyze the system, automatically locate flaws and and fix some stuff: Grub, Plymouth, Framebuffer, Apt sources, conflicting packages, video (Nvidia/ATI) and OpenGL, audio (Alsa/Pulseaudio) and apply some other workarounds for system with known glitches. It is proprietary right now, as its developed for the company I work for, but hopefully I'll be allowed to make it opensource by December.

Regards,
Effenberg

---

### Post by blinxwang on 2011-10-10
thanks for the help, guys Still can't make it past boot even with  nomodeset and a verbose boot. Dmesg always says Ubuntu fails to load my  GPU as well as fallback graphics. Here's what my Xorg.0.log has to  say about it:
```
[    10.719] 
X.Org X Server 1.10.4
Release Date: 2011-08-19
[    10.719] X Protocol Version 11, Revision 0
[    10.719] Build Operating System: Linux 2.6.24-29-server x86_64 Ubuntu
[    10.719] Current Operating System: Linux peter-MS-7640 3.0.0-12-generic #19-Ubuntu SMP Fri Sep 23 21:23:39 UTC 2011 x86_64
[    10.719] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-12-generic root=UUID=71c64fe2-a38d-46fd-b1db-e783e6f90965 ro nomodeset
[    10.719] Build Date: 29 September 2011  02:45:13AM
[    10.719] xorg-server 2:1.10.4-1ubuntu4 (For technical support please see http://www.ubuntu.com/support) 
[    10.719] Current version of pixman: 0.22.2
[    10.719]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    10.719] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    10.719] (==) Log file: "/var/log/Xorg.0.log", Time: Mon Oct 10 15:40:44 2011
[    10.729] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    10.729] (==) No Layout section.  Using the first Screen section.
[    10.729] (==) No screen section available. Using defaults.
[    10.729] (**) |-->Screen "Default Screen Section" (0)
[    10.729] (**) |   |-->Monitor "<default monitor>"
[    10.729] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    10.729] (==) Automatically adding devices
[    10.729] (==) Automatically enabling devices
[    10.841] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    10.841]     Entry deleted from font path.
[    10.841] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    10.841]     Entry deleted from font path.
[    10.841] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    10.841]     Entry deleted from font path.
[    10.841] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    10.841]     Entry deleted from font path.
[    10.841] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    10.841]     Entry deleted from font path.
[    10.856] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    10.856] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    10.856] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    10.856] (II) Loader magic: 0x7e0220
[    10.856] (II) Module ABI versions:
[    10.856]     X.Org ANSI C Emulation: 0.4
[    10.856]     X.Org Video Driver: 10.0
[    10.856]     X.Org XInput driver : 12.3
[    10.856]     X.Org Server Extension : 5.0
[    10.857] (--) PCI:*(0:8:0:0) 1002:6718:1002:0b00 rev 0, Mem @ 0xd0000000/268435456, 0xfe9c0000/131072, I/O @ 0x0000e000/256, BIOS @ 0x????????/131072
[    10.857] (II) Open ACPI successful (/var/run/acpid.socket)
[    10.857] (II) LoadModule: "extmod"
[    10.909] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    10.910] (II) Module extmod: vendor="X.Org Foundation"
[    10.910]     compiled for 1.10.4, module version = 1.0.0
[    10.910]     Module class: X.Org Server Extension
[    10.910]     ABI class: X.Org Server Extension, version 5.0
[    10.910] (II) Loading extension MIT-SCREEN-SAVER
[    10.910] (II) Loading extension XFree86-VidModeExtension
[    10.910] (II) Loading extension XFree86-DGA
[    10.910] (II) Loading extension DPMS
[    10.910] (II) Loading extension XVideo
[    10.910] (II) Loading extension XVideo-MotionCompensation
[    10.910] (II) Loading extension X-Resource
[    10.910] (II) LoadModule: "dbe"
[    10.910] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    10.910] (II) Module dbe: vendor="X.Org Foundation"
[    10.910]     compiled for 1.10.4, module version = 1.0.0
[    10.910]     Module class: X.Org Server Extension
[    10.910]     ABI class: X.Org Server Extension, version 5.0
[    10.910] (II) Loading extension DOUBLE-BUFFER
[    10.910] (II) LoadModule: "glx"
[    10.910] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    10.910] (II) Module glx: vendor="X.Org Foundation"
[    10.910]     compiled for 1.10.4, module version = 1.0.0
[    10.910]     ABI class: X.Org Server Extension, version 5.0
[    10.910] (==) AIGLX enabled
[    10.910] (II) Loading extension GLX
[    10.910] (II) LoadModule: "record"
[    10.910] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    10.910] (II) Module record: vendor="X.Org Foundation"
[    10.910]     compiled for 1.10.4, module version = 1.13.0
[    10.910]     Module class: X.Org Server Extension
[    10.910]     ABI class: X.Org Server Extension, version 5.0
[    10.910] (II) Loading extension RECORD
[    10.910] (II) LoadModule: "dri"
[    10.910] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    10.910] (II) Module dri: vendor="X.Org Foundation"
[    10.910]     compiled for 1.10.4, module version = 1.0.0
[    10.910]     ABI class: X.Org Server Extension, version 5.0
[    10.910] (II) Loading extension XFree86-DRI
[    10.910] (II) LoadModule: "dri2"
[    10.910] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    10.911] (II) Module dri2: vendor="X.Org Foundation"
[    10.911]     compiled for 1.10.4, module version = 1.2.0
[    10.911]     ABI class: X.Org Server Extension, version 5.0
[    10.911] (II) Loading extension DRI2
[    10.911] (==) Matched fglrx as autoconfigured driver 0
[    10.911] (==) Matched ati as autoconfigured driver 1
[    10.911] (==) Matched vesa as autoconfigured driver 2
[    10.911] (==) Matched fbdev as autoconfigured driver 3
[    10.911] (==) Assigned the driver to the xf86ConfigLayout
[    10.911] (II) LoadModule: "fglrx"
[    10.911] (WW) Warning, couldn't open module fglrx
[    10.911] (II) UnloadModule: "fglrx"
[    10.911] (II) Unloading fglrx
[    10.911] (EE) Failed to load module "fglrx" (module does not exist, 0)
[    10.911] (II) LoadModule: "ati"
[    10.911] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    10.911] (II) Module ati: vendor="X.Org Foundation"
[    10.911]     compiled for 1.10.2.902, module version = 6.14.99
[    10.911]     Module class: X.Org Video Driver
[    10.911]     ABI class: X.Org Video Driver, version 10.0
[    10.911] (II) LoadModule: "radeon"
[    10.912] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    10.912] (II) Module radeon: vendor="X.Org Foundation"
[    10.912]     compiled for 1.10.2.902, module version = 6.14.99
[    10.912]     Module class: X.Org Video Driver
[    10.912]     ABI class: X.Org Video Driver, version 10.0
[    10.912] (II) LoadModule: "vesa"
[    10.912] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    10.912] (II) Module vesa: vendor="X.Org Foundation"
[    10.912]     compiled for 1.10.2, module version = 2.3.0
[    10.912]     Module class: X.Org Video Driver
[    10.912]     ABI class: X.Org Video Driver, version 10.0
[    10.912] (II) LoadModule: "fbdev"
[    10.912] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    10.912] (II) Module fbdev: vendor="X.Org Foundation"
[    10.912]     compiled for 1.10.0, module version = 0.4.2
[    10.912]     ABI class: X.Org Video Driver, version 10.0
[    10.912] (II) RADEON: Driver for ATI Radeon chipsets:
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
    ATI Radeon Mobility 9000 (M9) Lg (AGP), ATI Radeon 9700 Pro ND (AGP),
    ATI Radeon 9700/9500Pro NE (AGP), ATI Radeon 9600TX NF (AGP),
    ATI FireGL X1 NG (AGP), ATI Radeon 9800PRO NH (AGP),
    ATI Radeon 9800 NI (AGP), ATI FireGL X2 NK (AGP),
    ATI Radeon 9800XT NJ (AGP),
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
    SUMO, SUMO, SUMO, SUMO, SUMO, ATI Radeon HD 4200, ATI Radeon 4100,
    ATI Mobility Radeon HD 4200, ATI Mobility Radeon 4100,
    ATI Radeon HD 4290, ATI Radeon HD 4250, AMD Radeon HD 6310 Graphics,
    AMD Radeon HD 6310 Graphics, AMD Radeon HD 6250 Graphics,
    AMD Radeon HD 6250 Graphics, AMD Radeon HD 6300 Series Graphics,
    AMD Radeon HD 6200 Series Graphics, CYPRESS,
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
    ATI Radeon HD 5450, CEDAR, CAYMAN, CAYMAN, CAYMAN, CAYMAN, CAYMAN,
    CAYMAN, CAYMAN, CAYMAN, CAYMAN, CAYMAN, AMD Radeon HD 6900 Series,
    AMD Radeon HD 6900 Series, CAYMAN, CAYMAN, CAYMAN,
    AMD Radeon HD 6900M Series, Mobility Radeon HD 6000 Series, BARTS,
    BARTS, Mobility Radeon HD 6000 Series,
    Mobility Radeon HD 6000 Series, BARTS, BARTS, BARTS, BARTS,
    AMD Radeon HD 6800 Series, AMD Radeon HD 6800 Series,
    AMD Radeon HD 6700 Series, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
    TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, CAICOS,
    CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS,
    CAICOS, CAICOS, CAICOS
[    10.914] (II) VESA: driver for VESA chipsets: vesa
[    10.914] (II) FBDEV: driver for framebuffer: fbdev
[    10.914] (++) using VT number 7

[    10.914] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    10.914] (II) [KMS] drm report modesetting isn't supported.
[    10.914] (WW) Falling back to old probe method for vesa
[    10.914] (WW) Falling back to old probe method for fbdev
[    10.914] (II) Loading sub module "fbdevhw"
[    10.914] (II) LoadModule: "fbdevhw"
[    10.914] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    10.914] (II) Module fbdevhw: vendor="X.Org Foundation"
[    10.914]     compiled for 1.10.4, module version = 0.0.2
[    10.914]     ABI class: X.Org Video Driver, version 10.0
[    10.915] (II) RADEON(0): TOTO SAYS 00000000fe9c0000
[    10.915] (II) RADEON(0): MMIO registers at 0x00000000fe9c0000: size 128KB
[    10.915] (II) RADEON(0): PCI bus 8 card 0 func 0
[    10.915] (II) RADEON(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    10.915] (==) RADEON(0): Depth 24, (--) framebuffer bpp 32
[    10.915] (II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    10.915] (==) RADEON(0): Default visual is TrueColor
[    10.915] (II) Loading sub module "vgahw"
[    10.915] (II) LoadModule: "vgahw"
[    10.915] (II) Loading /usr/lib/xorg/modules/libvgahw.so
[    10.915] (II) Module vgahw: vendor="X.Org Foundation"
[    10.915]     compiled for 1.10.4, module version = 0.1.0
[    10.915]     ABI class: X.Org Video Driver, version 10.0
[    10.915] (II) RADEON(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
[    10.915] (==) RADEON(0): RGB weight 888
[    10.915] (II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
[    10.915] (--) RADEON(0): Chipset: "AMD Radeon HD 6900 Series" (ChipID = 0x6718)
[    10.915] (EE) RADEON(0): Chipset: "AMD Radeon HD 6900 Series" (ChipID = 0x6718) requires KMS
[    10.915] (II) UnloadModule: "radeon"
[    10.915] (II) Unloading radeon
[    10.915] (II) UnloadModule: "vgahw"
[    10.915] (II) Unloading vgahw
[    10.915] (EE) Screen(s) found, but none have a usable configuration.
[    10.915] 
Fatal server error:
[    10.915] no screens found
[    10.915] 
Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 
[    10.915] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[    10.915] 
[    10.918]  ddxSigGiveUp: Closing log
```

---

### Post by blinxwang on 2011-10-10
The funny thing is, though, Everything works flawlessly on the LiveCD.

---

### Post by blinxwang on 2011-10-10
> **effenberg0x0 said:**
> I'm not sure if you can switch to a VT or not (don't know where your boot process is stuck). 

**1) Getting to a console**
-Try Ctrl+Alt+F1 to F6 to switch to a VT.
-If you cant, reboot and hold shift to see Grub and go to a recovery. Press "e" to edit the recovery kernel line. Make sure you don't have things like "splash" and "quiet" set there. "nomodeset" is OK. Proceed. Choose a prompt with networking

**2) Logging in:**
Login and run:
```

sudo service lightdm stop
sudo killall -s KILL /usr/bin/X
```As I mentioned, I don't know whether you'll do it from a VT or from recovery, so run these commands anyway. They are meant to stop GUI sessions so you have more chance of a stable enough system. 

At this point you should fully update / upgrade your system as this is supposedly already fixed. You can do that if you want to. But I say we remove fglrx first and install AMDs proprietary driver (Catalyst) for now to reduce risk.
[B]
3) Uninstall previous driver:[/B]
```
sudo apt-get remove --purge fglrx*
```Download Catalyst install:
```
cd
mkdir ati
cd ati
wget http://www2.ati.com/drivers/linux/ati-driver-installer-11-9-x86.x86_64.run
```Wait for the download to finish and run:
```
sudo sh ati-driver-installer-11-9-x86.x86_64.run --buildpkg Ubuntu/oneiric
sudo dpkg -i ati*.deb
sudo aticonfig --initial -f
```**4) Disable Plymouth, safer "text" grub.**
I've seen reports that it is a good idea to disable plymouth and graphic grub after ATI first install / conflicts. I would trust them now and tune my system later when everything is working better. If you concur, do this:

```
sudo nano /etc/default/grub
```Remove "splash" and "quiet" and add "text" to the line GRUB_CMDLINE_LINUX_DEFAULT=""

Press this to save the file and exit nano:
Ctrl+X, Y, <enter>

Update grub:
```
sudo update-grub
```Reboot your system:
```


sudo reboot now
```Hold shift to see the Grub menu and get to recovery. Choose a prompt with networking.
[B]
5)First boot with new VGA driver / Upgrade Ubuntu on recovery[/B]
Update & upgrade your setup:
```
sudo apt-get update && sudo apt-get upgrade

```Reboot your system:

[B]
6)Reboot / Make sure Grub line for main Kernel is OK before proceeding[/B]
```
sudo reboot now
```Hold shift to see grub. Press "e" over the main kernel line to edit it. Make sure there are no weird options at the end of the kernel line (you might have added some options when trying to fix it, they might still be there. "Splash", "quiet", should be avoided in this first boot (we want to see eventual error messages). I would remove "nomodeset" too at this point. Better play it safe. If they are there, delete and continue the boot process. 

I believe that would be enough to give you a working system.
Report back.

Good luck.

Effenberg

[B]EDIT: 
No Graphical user interface after boot (stuck at console)[/B]
- Reboot. Seriously, reboot at least once to see if it works.
- Make sure you cannot manually start a GUI session using "sudo service lightdm start".
- Switch to another VT using Ctrl+Alt+F1 to F6 if your current one don't offer you a login prompt. 
- After login, run these commands and report back the results at a new thread:
```
DISPLAY=:0.0 /usr/lib/nux/unity_support_test -p
glxinfo | grep -i "direct rendering"
sudo cat /var/log/Xorg.0.log 
dmesg | grep -i ati
```
Try to get the error message(s) you see to here so we have something to work with.

**No panel / launcher on Unity** **after Video Driver install**
- Try to follow the instructions posted here: [http://ubuntuforums.org/showthread.php?t=1856053](http://ubuntuforums.org/showthread.php?t=1856053)

**ATI Performance Glitches and potential Fixes**
Some users report small fixes that might help improve performance in your install. If you feel a sluggish performance in Unity or Gnome-Shell, try this fixes:

For Unity: [http://ubuntuforums.org/showpost.php?p=11323947&postcount=2](http://ubuntuforums.org/showpost.php?p=11323947&postcount=2)
For Gnome-Shell: [http://ubuntuforums.org/showpost.php?p=11327532&postcount=8](http://ubuntuforums.org/showpost.php?p=11327532&postcount=8)

Aha! Fixed my install using your instructions on building FGLRX (on the LiveCD)! Many thanks, effenberg0x0!

---

