---
title: "[SOLVED] Generic Kernel Booting into Blank Screen"
date: 2008-07-31
forum: New to Ubuntu
---

### Post by mach-schnell on 2008-07-31
I've been having technical problems installing/running ubuntu 8.04.1 amd64 on my desktop computer.  My hardware configuration consists of an Intel Core 2 Quad Processor Q6600, an Intel (Stoughton) G965 motherboard, an Nvidia 8800 gt video card, displaying on a Philips 109b 19&#8221; CRT monitor.

The problem is that I get a blank, flickering screen after selecting the Ubuntu linux generic option in the grub boot loader.  Imagine a black image displayed on a monitor set to a resolution and refresh rate it does not support and that's what it looks like.

I've read through a myriad of posts on these and other forums and tried everything I could find that seemed applicable to my problem.  I outline everything I did below, reproducing the exact commands I use and the output I get in chronological order leading to the present moment (I put "//" before my comments to help distinguish them from output).  I apologize for the disgusting length of this post; I wanted anyone willing to help me to have all the necessary info and I'm just too inexperienced with Linux to discount anything.  

Installing with the alternate cd for ubuntu 8.04.1 amd64 worked fine and I wound up with a roughly 61 gb &#8220;/&#8221; partition with a swap of about 3.5 gb.  Once the process was complete, it prompted me to remove the cd from the drive and boot into my new operating system.

After restarting, I saw the new grub bootloader with options to boot into Windows Vista a couple of times (one for the os and another for a recovery console for it) and options for booting into linux (generic kernel, recovery, and memtest).  Unfortunately, this is where the trouble begins.

Selecting linux generic produces a black/blank screen that sort of flashes every so often.  Pressing &#8220;e&#8221; on the linux generic option and modifying it with nosplash at grub loader failed to resolve the issue.  Pressing ctrl + alt + F1 (from the black screen) puts me into the command line (i.e. black background, generic white font, blinking cursor) where I see, 

Loading, please wait...
Kinit: name_to_dev_t (/dev/sda5) = sda5(8,5)
Kinit: trying to resume from /dev/sda5
Kinit: No resume image, doing normal boot...
Ubuntu8.0.04.1 test-box tty1
test-box login: entered username
Password: entered password
Linux test-box 2.6.24-19-generic #1_SMP Wed Jun 18 14:15:37 UTC 2008 x86_64
//It displays messages here about being free software, a lack of any warranty, where to go for documentation, and how to run commands as admin.
Kernel alive
username@test-box:`$

//The first thing I tried from this position was startx. 
username@test-box:`$ startx
xauth: creating authority file /home/username/.Xauthority
xauth: creating authority file /home/username/.Xauthority

Fatal server error:
Server is already active for display 0
	If this server is no longer running, remove /temp/.X0-lock and start again.

Invalid MIT-MAGIC-COOKIE-1 keygiving up
xinit: Interrupted system call (errno 4) : unable to connect to X server
xinit: No such process (errno 3); Server error.

//The next thing I tried was
username@test-box`$ sudo dpkg-reconfigure -phigh xserver-xorg
//I selected from the options the menu presented, opting to disable the frame buffer.
Xserver-xorg postinst warning: overwriting possibly customised configuration file; backup in /etc/X11/xorg.conf.20080730154216

//After restarting the machine, selecting the generic kernel from grub and facing a blank screen, I went back into command line (ctrl + alt + F1).
username@test-box:`$ gdm stop
Message says gnome is stopped.
username@test-box:`$ startx
//I hear the sound of Ubuntu starting up but I have a blank screen.
//Return to command line where I now see,
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9.2)
Current Operating System: Linux test-box 2.6.24-19-generic #1 SMP Wed Jun 18 14:15:37 UTC 2008 x86_64
Build Date: 13 June 2008 01:10:57AM

Before reporting problems, check [http://wiki.x.org](http://wiki.x.org) to make sure you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting, (++) from command line, (!!) notice, (II) informational, (WW) waring, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: &#8220;var/log/Xorg.0.log&#8221;, Time: Wed Jul 30 15:51:56 2008
(==) Using config file: &#8220;/etc/X11/xorg.conf&#8221;
(II) Module &#8220;i2c&#8221; already built-in
(II) Module "ddc" already built-in
(II) Module "ramdac" already built-in
expected keysum, got XF86KbdLightOnOff: line 70 of pc
expected keysum, got XF86KbdBrightnessDown: line 71 of pc
expected keysum, got XF86KbdBrightnessUp: line 72 of pc
expected keysum, got XF86KbdLightOnOff: line 70 of pc
expected keysum, got XF86KbdBrightnessDown: line 71 of pc
expected keysum, got XF86KbdBrightnessUp: line 72 of pc
SetClient Version: 0 9
SetGrabKeysState - disabled

//Restarted the machine.
//Ubuntu kernel generic, pressed e key, replace "quiet" with "nosplash" and press b.
//I get a blinking cursor in the upper left corner, otherwise blank screen.
//Restarted the machine.

//I try the recovery mode from grub boot loader.
xfix
resume normal boot
//I get a blank screen
//Go into command line

//Try username@test-box:~$ sudo apt-get install nividia-glx
Reading Package Lists...Done
Building dependency tree
Reading state information...Done
Suggested Packages: nvidia-kernel-source nvidia-settings
The following NEW packages will be installed: nvidia-glx
0 upgraded, 1 newly installed, 0 to remove and 52 not upgraded.
Need to get 7333kB of archives.
After this operation, 22.4MB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted nvidia-glx 1:96.43.05+2.6.24.13-19.45 [7333kB]
Fetched 7333 kB in 38s (191kB/s)
Selected previously deselected package nvidia-glx.
(Reading database...95147 files and directories currently installed.)
Unpacking nvidia-glx (from.../nvidia-glx_1%3a96.43.05+2.6.24.13-19.45_amd64.deb)...
Setting up nvidia-glx ( 1:96.43.05+2.6.24.13-19.45)...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place

//Now I try username@test-box:`$ gdm start
* Starting Gnome Display Maganger...			[OK]

//I'm still in the command line, so I try username@test-box:`$ sudo gdm
gdm[6431]: Warning: GDM already running. Aborting!
GDM already running. Aborting!

//I restart the computer and still get the blank screen, go into command line, and try startx.
xauth: /home/username/.Xauthority not writable, changes will be ignored
xauth: error in locking authority file /home/username/.Xauthority
xauth: error in locking authority file /home/username/.Xauthority
xauth: error in locking authority file /home/username/.Xauthority

Fatal server error:
Server is already active for display 0
If this server is no longer running, remove /tmp/.X0-lock and start again.

No protocol specified
giving up.
xinit: Resource temporarily unavailable (errno 11): unable to connect to X server
xinit: No such process (errno 3): Server error.
xauth: error in locking authority file /home/username/.Xauthority

//I try sudo /etc/init.d/gdm restart
//Blank screen...ctrl+alt+F1 puts me back into command line
*Stopping GNOME Display Manager...	0 @ 8000-d000	[OK]
*Starting GNOME Display Manager...			[OK]

//Restart, and I'm still getting the blank screen when I select Ubuntu generic linux kernel.

I wasn't sure how to get at the xorg.conf file from the command line so I installed Ex2IFS in Windows and copied the xorg.conf file onto my desktop.  I used Firefox to open it using Unicode UTF-8 character encoding and pasted everything in it below:
------------------------------------------
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc104"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
EndSection
--------------------------------------
At this point, I feel like I've done as much as I can searching through forums.  Any help would be greatly appreciated.  Thanks for your time.

---

### Post by StageCraft on 2008-07-31
If you can try updateing and see if you can get access to some restricted drivers, that might solve the problem, but I'm not certain. (However, it can't hurt)

other than that, if all else fails, you could try to install with the standard install CD, it generally is more effective than the alternate.

Good luck

---

### Post by mach-schnell on 2008-07-31
Thanks for taking a look at it.  

I originally tried to install with the live cd but that didn't work after multiple attempts (using different cd images, each burned slowly) so I used the alternate instead (worked first try).  

As for installing restricted drivers, the only way to do that from the command line seemed to be with the "sudo apt-get install nividia-glx" (my attempt to do that is buried in the monolithic original post), which didn't seem to make any difference.

---

### Post by RomeReactor on 2008-07-31
Hi. You're getting errors on 'startx' because the X server is already running. Try rebooting into recovery mode and select XFIX.

If your motherboard has an integrated GPU, disable it in BIOS.

---

### Post by mach-schnell on 2008-07-31
I went into recovery and did xfix already; it's buried in the monstrous first post but thank you anyway.

---

### Post by mach-schnell on 2008-08-04
bump

---

### Post by Jack M. on 2008-08-05
This is just a shot in the dark, but you could try installing the "suggested packages" from when you installed the Nvidia driver (nvidia-glx).

```
sudo apt-get install nvidia-kernel-source nvidia-settings
```

Other than that, though, I have no idea other than reinstalling - it seems that you've taken all the usual troubleshooting steps.

---

### Post by mach-schnell on 2008-08-05
Thanks for the response Jack.  I tried "sudo apt-get install nvidia-kernel-source nvidia-settings" to no avail; it downloaded data and worked through a series of steps that culminated in an error.  

However, after some more looking around I figured out a solution.  It's taken quite a bit of time pulling together various commands from different posts and guides, but I found something that worked for me.  After everything listed in my first post and subsequent suggestions, I followed the steps outlined below:

1.  Installed "Ext2 Installable File System 1.11" to be able to copy nvidia drivers downloaded on a windows partition and paste them into the /home/username/Desktop/ folder of my Linux partition.  Those not dual-booting will need another way of getting the nvidia*.run drivers file to install from into their Linux partition.
2.  Back-up the almighty xorg.conf file with this command: "sudo cp /etc/X11/xorg.conf ./xorg.conf.backup"
3.  I'm not sure what this step actually does, but one of the hundreds of posts I've read says it's necessary for installing nvidia drivers so I did it: "sudo apt-get install build-essential gcc-3.3-base"
4.  At this point, I needed to get rid of any remnants of nvidia drivers to prevent possible conflicts while installing new ones.  Not all of these commands will be necessary depending on which methods previous installs used.
"sudo envy --uninstall-all"
"sudo dpkg -P evy"
"sudo apt-get remove --purge nvidia*"
"sudo rm /lib/restricted-modules/.nvidia*"
"sudo nvidia-installer --uninstall"
5.  Stop gnome with "sudo /etc/init.d/gdm stop"
6.  Change the working directory with "cd /home/yourusername/Desktop"
7.  No idea what this command does, though another guide describes it as necessary so in it goes, "sudo telinit 3"
8.  Make the nvidia driver file executable with "sudo chmod a+x .nvidia*.run"
9.  Start the Nvidia installer with "sudo ./nvidia*run"
Navigate the options and make sure to have the nvidia installer create a new xorg file.
10. Finally, after logging in and seeing that everything works, make one last change.  Use the "gksudo gedit /etc/default/linux-restricted-modules-common" command and edit the DISABLED_MODULES line to read DISABLED_MODULES="nv nvidia_new"  Following this step helps prevent problems on system restart.

I'd like to finish by thanking everyone who tried to help and all those who contribute to the community.  Thanks.

---

### Post by venkat526 on 2012-12-29
[FONT=&quot]X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-30-server x86_64 Ubuntu
Current Operating System: Linux bt 3.2.6 #1 SMP Fri Feb 17 10:34:20 EST 2012 x86_64
Kernel command line: BOOT_IMAGE=/vmlinuz-3.2.6 root=UUID=b5c637f8-0d63-48b8-8390-7a8807849b16 ro i915.i915_enable_rc6=1 i915.lvds_downclock=1 i915.i915_enable_fbc=1 pcie_aspm=force
Build Date: 25 February 2012  06:57:33AM
xorg-server 2:1.7.6-2ubuntu7.11 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
Current version of pixman: 0.16.4
      Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
      to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
      (++) from command line, (!!) notice, (II) informational,
      (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Dec 29 11:27:03 2012
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) No Layout section.  Using the first Screen section.
(==) No screen section available. Using defaults.
(**) |-->Screen "Default Screen Section" (0)
(**) |   |-->Monitor "<default monitor>"
(==) No monitor specified for screen "Default Screen Section".
      Using a default monitor configuration.
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
      Entry deleted from font path.
(WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
      Entry deleted from font path.
(WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
      Entry deleted from font path.
(WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
      Entry deleted from font path.
(WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
      Entry deleted from font path.
(==) FontPath set to:
      /usr/share/fonts/X11/misc,
      /usr/share/fonts/X11/Type1,
      /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
      built-ins
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(II) The server relies on udev to provide the list of input devices.
      If no devices become available, reconfigure udev or disable AutoAddDevices.
(II) Loader magic: 0x7cb840
(II) Module ABI versions:
      X.Org ANSI C Emulation: 0.4
      X.Org Video Driver: 6.0
      X.Org XInput driver : 7.0
      X.Org Server Extension : 2.0
(--) using VT number 8

(--) PCI:*(0:0:2:0) 8086:0116:17aa:5000 Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller rev 9, Mem @ 0xf0000000/4194304, 0xe0000000/268435456, I/O @ 0x00005000/64
(WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
      compiled for 1.7.6, module version = 1.0.0
      Module class: X.Org Server Extension
      ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
      compiled for 1.7.6, module version = 1.0.0
      Module class: X.Org Server Extension
      ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="X.Org Foundation"
      compiled for 1.7.6, module version = 1.0.0
      ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
      compiled for 1.7.6, module version = 1.13.0
      Module class: X.Org Server Extension
      ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
      compiled for 1.7.6, module version = 1.0.0
      ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
      compiled for 1.7.6, module version = 1.1.0
      ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(==) Matched intel as autoconfigured driver 0
(==) Matched vesa as autoconfigured driver 1
(==) Matched fbdev as autoconfigured driver 2
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "intel"
(II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
      compiled for 1.7.6, module version = 2.9.1
      Module class: X.Org Video Driver
      ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "vesa"
(II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
      compiled for 1.7.6, module version = 2.3.0
      Module class: X.Org Video Driver
      ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "fbdev"
(II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
(II) Module fbdev: vendor="X.Org Foundation"
      compiled for 1.7.6, module version = 0.4.1
      ABI class: X.Org Video Driver, version 6.0
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
      i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
      E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
      965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
      4 Series, G45/G43, Q45/Q43, G41, B43, Clarkdale, Arrandale
(II) VESA: driver for VESA chipsets: vesa
(II) FBDEV: driver for framebuffer: fbdev
(II) Primary Device is: PCI 00@00:02:0
(EE) VESA: Kernel modesetting driver in use, refusing to load
(WW) Falling back to old probe method for vesa
(II) Loading sub module "fbdevhw"
(II) LoadModule: "fbdevhw"
(II) Loading /usr/lib/xorg/modules/linux/libfbdevhw.so
(II) Module fbdevhw: vendor="X.Org Foundation"
      compiled for 1.7.6, module version = 0.0.2
      ABI class: X.Org Video Driver, version 6.0
(**) FBDEV(0): claimed PCI slot 0@0:2:0
(II) FBDEV(0): using default device
(II) FBDEV(0): Creating default Display subsection in Screen section
      "Default Screen Section" for depth/fbbpp 24/32
(==) FBDEV(0): Depth 24, (==) framebuffer bpp 32
(==) FBDEV(0): RGB weight 888
(==) FBDEV(0): Default visual is TrueColor
(==) FBDEV(0): Using gamma correction (1.0, 1.0, 1.0)
(II) FBDEV(0): hardware: inteldrmfb (video memory: 4128kB)
(II) FBDEV(0): checking modes against framebuffer device...
(II) FBDEV(0): checking modes against monitor...
(--) FBDEV(0): Virtual size is 1366x768 (pitch 1366)
(**) FBDEV(0):  Built-in mode "current"
(==) FBDEV(0): DPI set to (96, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
      compiled for 1.7.6, module version = 1.0.0
      ABI class: X.Org ANSI C Emulation, version 0.4
(**) FBDEV(0): using shadow framebuffer
(II) Loading sub module "shadow"
(II) LoadModule: "shadow"
(II) Loading /usr/lib/xorg/modules/libshadow.so
(II) Module shadow: vendor="X.Org Foundation"
      compiled for 1.7.6, module version = 1.1.0
      ABI class: X.Org ANSI C Emulation, version 0.4
(II) UnloadModule: "intel"
(II) Unloading /usr/lib/xorg/modules/drivers/intel_drv.so
(==) Depth 24 pixmap format is 32 bpp
(==) FBDEV(0): Backing store disabled
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
(==) FBDEV(0): DPMS enabled
(==) RandR enabled
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) AIGLX: Screen 0 is not DRI2 capable
(II) AIGLX: Screen 0 is not DRI capable
(II) AIGLX: Loaded and initialized /usr/lib/dri/swrast_dri.so
(II) GLX: Initialized DRISWRAST GL provider for screen 0
(II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
(II) config/udev: Adding input device Power Button (/dev/input/event2)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
      compiled for 1.7.6, module version = 2.3.2
      Module class: X.Org XInput Driver
      ABI class: X.Org XInput driver, version 7.0
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event2"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device Video Bus (/dev/input/event9)
(**) Video Bus: Applying InputClass "evdev keyboard catchall"
(**) Video Bus: always reports core events
(**) Video Bus: Device: "/dev/input/event9"
(II) Video Bus: Found keys
(II) Video Bus: Configuring as keyboard
(II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device Power Button (/dev/input/event0)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device Lid Switch (/dev/input/event1)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=3 (/dev/input/event7)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Integrated Camera (/dev/input/event4)
(**) Integrated Camera: Applying InputClass "evdev keyboard catchall"
(**) Integrated Camera: always reports core events
(**) Integrated Camera: Device: "/dev/input/event4"
(II) Integrated Camera: Found keys
(II) Integrated Camera: Configuring as keyboard
(II) XINPUT: Adding extended input device "Integrated Camera" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
(**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event6)
(**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
(**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
      compiled for 1.7.6, module version = 1.2.2
      Module class: X.Org XInput Driver
      ABI class: X.Org XInput driver, version 7.0
(II) Synaptics touchpad driver version 1.2.2
(**) Option "Device" "/dev/input/event6"
(II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5702
(II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4838
(II) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
(II) SynPS/2 Synaptics TouchPad: finger width range 0 - 15
(II) SynPS/2 Synaptics TouchPad: buttons: left double triple
(--) SynPS/2 Synaptics TouchPad: touchpad found
(**) SynPS/2 Synaptics TouchPad: always reports core events
(II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
(**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
(**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 0
(**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
(**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
(--) SynPS/2 Synaptics TouchPad: touchpad found
(II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device TPPS/2 IBM TrackPoint (/dev/input/event8)
(**) TPPS/2 IBM TrackPoint: Applying InputClass "evdev pointer catchall"
(**) TPPS/2 IBM TrackPoint: Applying InputClass "Trackpoint Wheel Emulation"
(**) TPPS/2 IBM TrackPoint: always reports core events
(**) TPPS/2 IBM TrackPoint: Device: "/dev/input/event8"
(II) TPPS/2 IBM TrackPoint: Found 3 mouse buttons
(II) TPPS/2 IBM TrackPoint: Found relative axes
(II) TPPS/2 IBM TrackPoint: Found x and y relative axes
(II) TPPS/2 IBM TrackPoint: Configuring as mouse
(**) Option "Emulate3Buttons" "false"
(II) TPPS/2 IBM TrackPoint: Forcing middle mouse button emulation off.
(**) Option "EmulateWheel" "true"
(**) Option "EmulateWheelButton" "2"
(**) Option "YAxisMapping" "4 5"
(**) TPPS/2 IBM TrackPoint: YAxisMapping: buttons 4 and 5
(**) Option "XAxisMapping" "6 7"
(**) TPPS/2 IBM TrackPoint: XAxisMapping: buttons 6 and 7
(**) TPPS/2 IBM TrackPoint: EmulateWheelButton: 2, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "TPPS/2 IBM TrackPoint" (type: MOUSE)
(II) TPPS/2 IBM TrackPoint: initialized for relative axes.
(II) config/udev: Adding input device TPPS/2 IBM TrackPoint (/dev/input/mouse1)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device ThinkPad Extra Buttons (/dev/input/event5)
(**) ThinkPad Extra Buttons: Applying InputClass "evdev keyboard catchall"
(**) ThinkPad Extra Buttons: always reports core events
(**) ThinkPad Extra Buttons: Device: "/dev/input/event5"
(II) ThinkPad Extra Buttons: Found keys
(II) ThinkPad Extra Buttons: Configuring as keyboard
(II) XINPUT: Adding extended input device "ThinkPad Extra Buttons" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) ThinkPad Extra Buttons: Close
(II) UnloadModule: "evdev"
(II) TPPS/2 IBM TrackPoint: Close
(II) UnloadModule: "evdev"
(II) UnloadModule: "synaptics"
(II) AT Translated Set 2 keyboard: Close
(II) UnloadModule: "evdev"
(II) Integrated Camera: Close
(II) UnloadModule: "evdev"
(II) Power Button: Close
(II) UnloadModule: "evdev"
(II) Video Bus: Close
(II) UnloadModule: "evdev"
(II) Power Button: Close
(II) UnloadModule: "evdev"

Backtrace:
0: /usr/bin/X (xorg_backtrace+0x28) [0x45fcc8]
1: /usr/bin/X (0x400000+0x5dfbd) [0x45dfbd]
2: /lib/libpthread.so.0 (0x7f586418d000+0xf8f0) [0x7f586419c8f0]
3: /usr/bin/X (DamageUnregister+0x53) [0x4d7a23]
4: /usr/lib/xorg/modules/libshadow.so (shadowRemove+0x33) [0x7f58604003c3]
5: /usr/lib/xorg/modules/libshadow.so (0x7f58603ff000+0x1884) [0x7f5860400884]
6: /usr/bin/X (0x400000+0xb56a9) [0x4b56a9]
7: /usr/bin/X (0x400000+0xd2cac) [0x4d2cac]
8: /usr/bin/X (0x400000+0x2624c) [0x42624c]
9: /lib/libc.so.6 (__libc_start_main+0xfd) [0x7f5862e82c4d]
10: /usr/bin/X (0x400000+0x25d59) [0x425d59]
Segmentation fault at address (nil)

Caught signal 11 (Segmentation fault). Server aborting

Please consult the The X.Org Foundation support 
       at [http://wiki.x.org](http://wiki.x.org)
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

 ddxSigGiveUp: Closing log
 [/FONT]

---

