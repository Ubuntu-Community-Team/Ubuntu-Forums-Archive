---
title: "Black login screen"
date: 2008-10-15
forum: New to Ubuntu
---

### Post by Bluebottel on 2008-10-15
The description kind of says it all. I have the problem on my Asus eee 900 running Ubuntu 8.04.1. 
The login screen is all black with a pointer saying that it loads.
I can switch to a different virtual terminal (is that a correct term? Ctrl + alt + F1 is the thing.) and login without any problems.

I have messed around with the xorg.conf in /etc/X11/xorg.conf and i have also tried using 'sudo dpkg-reconfigure xserver-xorg' without any change.
It runs fine, to my knowledge, but the questions only concern the keyboard.

At first i thought it was the [gnome time bug]("https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/124979") or some weird version of it, but the time seems right.

I suspect that the screen tries to push some screen resolution that it cant handle, but im not certain.
Anyone got experience with this kind of problem?

---

### Post by Nxion on 2008-10-15
> **Bluebottel said:**
> The description kind of says it all. I have the problem on my Asus eee 900 running Ubuntu 8.04.1. 
The login screen is all black with a pointer saying that it loads.
I can switch to a different virtual terminal (is that a correct term? Ctrl + alt + F1 is the thing.) and login without any problems.

I have messed around with the xorg.conf in /etc/X11/xorg.conf and i have also tried using 'sudo dpkg-reconfigure xserver-xorg' without any change.
It runs fine, to my knowledge, but the questions only concern the keyboard.

At first i thought it was the [gnome time bug]("https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/124979") or some weird version of it, but the time seems right.

I suspect that the screen tries to push some screen resolution that it cant handle, but im not certain.
Anyone got experience with this kind of problem?

It has been awhile since I have seen that issue but I have encountered it on my desktop before.

1. Before this happend did you update the machine?
2. How frequent is this issue? If your reboot is the screen still black?

ALSO..

If you reboot and still get the black screen, try going into another tty (CTRL+ALT+F1, F2, etc...) and run this command:

```
dmesg | tail
```

if you can, can you post the output here?

---

### Post by Bluebottel on 2008-10-15
1. I have done some updates to it, cant remember which ones though.
2. Always. As in, its not a sporadic issue.

Ran the dmesg | tail and heres the spitout:

[   27.814577] Bluetooth: HCI socket layer initialized
[   27.849007] Bluetooth: L2CAP ver 2.9
[   27.849014] Bluetooth: L2CAP socket layer initialized
[   27.929122] Bluetooth: RFCOMM socket layer initialized
[   27.929458] Bluetooth: RFCOMM TTY layer initialized
[   27.929466] Bluetooth: RFCOMM ver 1.8
[   31.224424] [drm] Initialized drm 1.1.0 20060810
[   31.232078] ACPI: PCI Interuppt 0000:00:02.0[A] -> GSI (level, low) -> IRQ 16
[   31.232092] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   31.232252] [drm] Initialized i915 1.6.0 20060119 on minor 0

It works fine to login by doing ctrl + alt + f1 and punching in the user/pass.

---

### Post by Nxion on 2008-10-15
> 1. I have done some updates to it, cant remember which ones though.So you are saying that after you updated the laptop, and rebooted, now you are presented with the black screen?

> 
It works fine to login by doing ctrl + alt + f1 and punching in the user/pass.After you login how do you start the GUI, or do you not?

---

### Post by Bluebottel on 2008-10-15
Im sorry im im not clear in my posts, im not that experienced and it messes things up.

I have updated the laptop since the installation of ubuntu but it have worked fine up until now. When the problem first occured, wine had just died on me and messed around with the gamma.

I resetted the gamma and later on turned off the computer. Next 
bootup i had the problem.
After i log i cant get to the GUI at all. Trying 'sudo startx' and it replies 
"server is already active for display 0
if this server is no longer running, remove /tmp/.X0-lock
and start again.

No protocol specified
giving up.[...]"

In short, yes i can login. No i dont have anything graphical (windows etc.)

Ps. I dont mean to sound rude or blunt, english isnt my native tounge so things get eaten in the translation.

---

### Post by unutbu on 2008-10-15
I may not know the answer to your problem, but perhaps it would be helpful if you post your

~/.xsession-errors 
/var/log/Xorg.0.log

files.

---

### Post by Bluebottel on 2008-10-16
Heres the .xsession-errors file:
```

/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
SESSION_MANAGER=local/Bluebox:/tmp/.ICE-unix/5247
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0
Shutdown failed or nothing to shut down.
xrdb:  "*Label.background" on line 220 overrides entry on line 150
xrdb:  "*Text.background" on line 226 overrides entry on line 191
xrdb:  "*Label.foreground" on line 232 overrides entry on line 151
xrdb:  "*Text.foreground" on line 238 overrides entry on line 192
Window manager warning: Failed to read saved session file /home/bluebottel/.metacity/sessions/default0.ms: Failed to open file '/home/bluebottel/.metacity/sessions/default0.ms': No such file or directory


Tracker version 0.6.6 Copyright (c) 2005-2007 by Jamie McCracken (jamiemcc@gnome.org)

This program is free software and comes without any warranty.
It is licensed under version 2 or later of the General Public License which can be viewed at http://www.gnu.org/licenses/gpl.txt

Initialising tracker...
Could not set idle IO priority...attempting best effort 7 priority
starting HAL detection for ac adaptors...found /org/freedesktop/Hal/devices/computer_power_supply_ac_adapter_AC0
11
Throttle level is 5
Initializing nautilus-share extension
seahorse nautilus module initialized

** (nautilus:5375): WARNING **: Unable to add monitor: Not supported
  PID TTY          TIME CMD
 5355 ?        00:00:00 pulseaudio
WARNING: modinfo for module b43 failed: modinfo: could not find module b43

WARNING: modinfo for module fglrx failed: modinfo: could not find module fglrx

WARNING: modinfo for module nvidia_new failed: modinfo: could not find module nvidia_new

WARNING: modinfo for module nvidia failed: modinfo: could not find module nvidia

WARNING: modinfo for module nvidia_legacy failed: modinfo: could not find module nvidia_legacy

ERROR: Only administrators can use this function.
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x18000cb (Mozilla Fi)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x2e00003 (Update Man)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x2e00003 (Update Man)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.

** (nm-applet:5414): WARNING **: <WARN>  hal_net_physdev_cb(): dbus returned an error.
  (org.freedesktop.Hal.NoSuchDevice) No device with id /org/freedesktop/Hal/devices/net_00_22_15_70_c9_d1



** (nm-applet:5414): WARNING **: <WARN>  nma_dbus_device_get_driver_cb(): dbus returned an error.
  (org.freedesktop.NetworkManager.DeviceNotFound) The requested network device does not exist.


/usr/lib/gnome-screensaver/gnome-screensaver-gl-helper: symbol lookup error: /usr/lib/libgdk-x11-2.0.so.0: undefined symbol: g_once_init_enter_impl
gksu: symbol lookup error: /usr/lib/libgdk-x11-2.0.so.0: undefined symbol: g_once_init_enter_impl
gksu: symbol lookup error: /usr/lib/libgdk-x11-2.0.so.0: undefined symbol: g_once_init_enter_impl
gnome-terminal: symbol lookup error: /usr/lib/libgdk-x11-2.0.so.0: undefined symbol: g_once_init_enter_impl
nautilus: symbol lookup error: /usr/lib/libgdk-x11-2.0.so.0: undefined symbol: g_once_init_enter_impl
gnome-session-save: symbol lookup error: /usr/lib/libgdk-x11-2.0.so.0: undefined symbol: g_once_init_enter_impl
Window manager warning: CurrentTime used to choose focus window; focus window may not be correct.
Window manager warning: Got a request to focus the no_focus_window with a timestamp of 0.  This shouldn't happen!
seahorse nautilus module shutdown
** Message: Got disconnected from the session message bus; retrying to reconnect every 10 seconds
DBus connection has been lost, trackerd will now shutdown
tracker has exited (reindex = 0)
tracker has exited (reindex = 0)

```

And heres Xorg.0.log

```
This is a pre-release version of the X server from The X.Org Foundation.
It is not supported in any way.
Bugs may be filed in the bugzilla at http://bugs.freedesktop.org/.
Select the "xorg" product for bugs you find in this release.
Before reporting bugs in pre-release versions please check the
latest version in the X.Org Foundation git repository.
See http://wiki.x.org/wiki/GitPage for git access instructions.

X.Org X Server 1.4.0.90
Release Date: 5 September 2007
X Protocol Version 11, Revision 0
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9.2)
Current Operating System: Linux Bluebox 2.6.24-21-eeepc #1 SMP Thu Aug 7 22:18:05 MDT 2008 i686
Build Date: 13 June 2008  01:08:21AM
 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Oct 16 19:03:33 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
(**) |-->Input Device "Synaptics Touchpad"
(==) Automatically adding devices
(==) Automatically enabling devices
(==) No FontPath specified.  Using compiled-in default.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(==) |-->Input Device "Configured Mouse"
(==) |-->Input Device "Generic Keyboard"
(==) The core pointer device wasn't specified explicitly in the layout.
	Using the first core pointer device.
(==) The core keyboard device wasn't specified explicitly in the layout.
	Using the first keyboard device.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81dc500
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 2.0
	X.Org XInput driver : 2.0
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,2590 card 1043,82d9 rev 04 class 06,00,00 hdr 00
(II) PCI: 00:02:0: chip 8086,2592 card 1043,82d9 rev 04 class 03,00,00 hdr 80
(II) PCI: 00:02:1: chip 8086,2792 card 1043,82d9 rev 04 class 03,80,00 hdr 80
(II) PCI: 00:1b:0: chip 8086,2668 card 1043,8337 rev 04 class 04,03,00 hdr 00
(II) PCI: 00:1c:0: chip 8086,2660 card 0000,0000 rev 04 class 06,04,00 hdr 81
(II) PCI: 00:1c:1: chip 8086,2662 card 0000,0000 rev 04 class 06,04,00 hdr 81
(II) PCI: 00:1c:2: chip 8086,2664 card 0000,0000 rev 04 class 06,04,00 hdr 81
(II) PCI: 00:1d:0: chip 8086,2658 card 1043,82d8 rev 04 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,2659 card 1043,82d8 rev 04 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,265a card 1043,82d8 rev 04 class 0c,03,00 hdr 00
(II) PCI: 00:1d:3: chip 8086,265b card 1043,82d8 rev 04 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,265c card 1043,82d8 rev 04 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,2448 card 0000,0000 rev d4 class 06,04,01 hdr 01
(II) PCI: 00:1f:0: chip 8086,2641 card 1043,82d8 rev 04 class 06,01,00 hdr 80
(II) PCI: 00:1f:2: chip 8086,2653 card 1043,82d8 rev 04 class 01,01,80 hdr 00
(II) PCI: 00:1f:3: chip 8086,266a card 1043,82d8 rev 04 class 0c,05,00 hdr 00
(II) PCI: 03:00:0: chip 1969,2048 card 1043,8233 rev a0 class 02,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,5), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 4: bridge is at (0:28:0), (0,4,4), BCTRL: 0x0006 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:28:1), (0,3,3), BCTRL: 0x0006 (VGA_EN is cleared)
(II) Bus 3 non-prefetchable memory range:
	[0] -1	0	0xfbf00000 - 0xfbffffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:28:2), (0,1,2), BCTRL: 0x0006 (VGA_EN is cleared)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xf8000000 - 0xfbefffff (0x3f00000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xf0000000 - 0xf6ffffff (0x7000000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 5: bridge is at (0:30:0), (0,5,5), BCTRL: 0x0006 (VGA_EN is cleared)
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(0:2:0) Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller rev 4, Mem @ 0xf7f00000/19, 0xd0000000/28, 0xf7ec0000/18, I/O @ 0xec00/3
(--) PCI: (0:2:1) Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller rev 4, Mem @ 0xf7f80000/19
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) Active PCI resource ranges:
	[0] -1	0	0xfbfc0000 - 0xfbffffff (0x40000) MX[B]
	[1] -1	0	0xf7eb7c00 - 0xf7eb7fff (0x400) MX[B]
	[2] -1	0	0xf7eb8000 - 0xf7ebbfff (0x4000) MX[B]
	[3] -1	0	0xf7f80000 - 0xf7ffffff (0x80000) MX[B](B)
	[4] -1	0	0xf7ec0000 - 0xf7efffff (0x40000) MX[B](B)
	[5] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[6] -1	0	0xf7f00000 - 0xf7f7ffff (0x80000) MX[B](B)
	[7] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[8] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[9] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[10] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[11] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[12] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[13] -1	0	0x0000e880 - 0x0000e89f (0x20) IX[B]
	[14] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[15] -1	0	0x0000e480 - 0x0000e49f (0x20) IX[B]
	[16] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[17] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xfbfc0000 - 0xfbffffff (0x40000) MX[B]
	[1] -1	0	0xf7eb7c00 - 0xf7eb7fff (0x400) MX[B]
	[2] -1	0	0xf7eb8000 - 0xf7ebbfff (0x4000) MX[B]
	[3] -1	0	0xf7f80000 - 0xf7ffffff (0x80000) MX[B](B)
	[4] -1	0	0xf7ec0000 - 0xf7efffff (0x40000) MX[B](B)
	[5] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[6] -1	0	0xf7f00000 - 0xf7f7ffff (0x80000) MX[B](B)
	[7] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[8] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[9] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[10] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[11] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[12] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[13] -1	0	0x0000e880 - 0x0000e89f (0x20) IX[B]
	[14] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[15] -1	0	0x0000e480 - 0x0000e49f (0x20) IX[B]
	[16] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[17] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B](B)
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfbfc0000 - 0xfbffffff (0x40000) MX[B]
	[5] -1	0	0xf7eb7c00 - 0xf7eb7fff (0x400) MX[B]
	[6] -1	0	0xf7eb8000 - 0xf7ebbfff (0x4000) MX[B]
	[7] -1	0	0xf7f80000 - 0xf7ffffff (0x80000) MX[B](B)
	[8] -1	0	0xf7ec0000 - 0xf7efffff (0x40000) MX[B](B)
	[9] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[10] -1	0	0xf7f00000 - 0xf7f7ffff (0x80000) MX[B](B)
	[11] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[12] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[13] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[14] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[15] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[16] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[17] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[18] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[19] -1	0	0x0000e880 - 0x0000e89f (0x20) IX[B]
	[20] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[21] -1	0	0x0000e480 - 0x0000e49f (0x20) IX[B]
	[22] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[23] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B](B)
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.4.0.90, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) Matched intel from file name intel.ids in autoconfig
(==) Matched intel for the autoconfigured driver
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "intel"
(II) Loading /usr/lib/xorg/modules/drivers//intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 2.2.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 2.0
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, 965G, G35, 965Q, 946GZ,
	965GM, 965GME/GLE, G33, Q35, Q33, Intel Integrated Graphics Device
(II) Primary Device is: PCI 00:02:0
(--) Assigning device section with no busID to primary device
(WW) intel: No matching Device section for instance (BusID PCI:0:2:1) found
(--) Chipset 915GM found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfbfc0000 - 0xfbffffff (0x40000) MX[B]
	[5] -1	0	0xf7eb7c00 - 0xf7eb7fff (0x400) MX[B]
	[6] -1	0	0xf7eb8000 - 0xf7ebbfff (0x4000) MX[B]
	[7] -1	0	0xf7f80000 - 0xf7ffffff (0x80000) MX[B](B)
	[8] -1	0	0xf7ec0000 - 0xf7efffff (0x40000) MX[B](B)
	[9] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[10] -1	0	0xf7f00000 - 0xf7f7ffff (0x80000) MX[B](B)
	[11] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[12] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[13] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[14] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[15] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[16] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[17] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[18] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[19] -1	0	0x0000e880 - 0x0000e89f (0x20) IX[B]
	[20] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[21] -1	0	0x0000e480 - 0x0000e49f (0x20) IX[B]
	[22] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[23] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B](B)
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfbfc0000 - 0xfbffffff (0x40000) MX[B]
	[5] -1	0	0xf7eb7c00 - 0xf7eb7fff (0x400) MX[B]
	[6] -1	0	0xf7eb8000 - 0xf7ebbfff (0x4000) MX[B]
	[7] -1	0	0xf7f80000 - 0xf7ffffff (0x80000) MX[B](B)
	[8] -1	0	0xf7ec0000 - 0xf7efffff (0x40000) MX[B](B)
	[9] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[10] -1	0	0xf7f00000 - 0xf7f7ffff (0x80000) MX[B](B)
	[11] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[12] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[13] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[17] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[18] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[19] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[20] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[22] -1	0	0x0000e880 - 0x0000e89f (0x20) IX[B]
	[23] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[24] -1	0	0x0000e480 - 0x0000e49f (0x20) IX[B]
	[25] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[26] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B](B)
	[27] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[28] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.1.0
	ABI class: X.Org Video Driver, version 2.0
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 0.1.0
	ABI class: X.Org Video Driver, version 2.0
(II) intel(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
(==) intel(0): Depth 24, (==) framebuffer bpp 32
(==) intel(0): RGB weight 888
(==) intel(0): Default visual is TrueColor
(II) intel(0): Integrated Graphics Chipset: Intel(R) 915GM
(--) intel(0): Chipset: "915GM"
(--) intel(0): Linear framebuffer at 0xD0000000
(--) intel(0): IO registers at addr 0xF7F00000
(II) intel(0): 2 display pipes available.
(==) intel(0): Using EXA for acceleration
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module "ddc" already built-in
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"(II) Module "i2c" already built-in
(II) intel(0): Output VGA using monitor section Configured Monitor
(II) intel(0): I2C bus "CRTDDC_A" initialized.
(II) intel(0): Output LVDS has no monitor section
(II) intel(0): I2C bus "LVDSDDC_C" initialized.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" removed.
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) intel(0): initializing int10
(WW) intel(0): Bad V_BIOS checksum
(II) intel(0): Primary V_BIOS segment is: 0xc000
(II) intel(0): VESA BIOS detected
(II) intel(0): VESA VBE Version 3.0
(II) intel(0): VESA VBE Total Mem: 7872 kB
(II) intel(0): VESA VBE OEM: Intel(r)915GM/910ML/915MS Graphics Chip Accelerated VGA BIOS
(II) intel(0): VESA VBE OEM Software Rev: 1.0
(II) intel(0): VESA VBE OEM Vendor: Intel Corporation
(II) intel(0): VESA VBE OEM Product: Intel(r)915GM/910ML/915MS Graphics Controller
(II) intel(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOB" initialized.
(II) intel(0): I2C device "SDVOCTRL_E for SDVOB:SDVO Controller B" registered at address 0x70.
(II) intel(0): No SDVO device found on SDVOB
(II) intel(0): I2C device "SDVOCTRL_E for SDVOB:SDVO Controller B" removed.
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOB" removed.
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOC" initialized.
(II) intel(0): I2C device "SDVOCTRL_E for SDVOC:SDVO Controller C" registered at address 0x72.
(II) intel(0): No SDVO device found on SDVOC
(II) intel(0): I2C device "SDVOCTRL_E for SDVOC:SDVO Controller C" removed.
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOC" removed.
(II) intel(0): Output TV has no monitor section
(II) intel(0): I2C device "LVDSDDC_C:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" removed.
(II) intel(0): Output VGA disconnected
(II) intel(0): Output LVDS connected
(II) intel(0): Output TV disconnected
(II) intel(0): Output LVDS using initial mode 1024x600
(II) intel(0): Monitoring connected displays enabled
(II) intel(0): detected 256 kB GTT.
(II) intel(0): detected 7932 kB stolen memory.
(==) intel(0): video overlay key set to 0x101fe
(==) intel(0): Will not try to enable page flipping
(==) intel(0): Triple buffering disabled
(==) intel(0): Using gamma correction (1.0, 1.0, 1.0)
(==) intel(0): DPI set to (96, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "exa"
(II) LoadModule: "exa"
(II) Loading /usr/lib/xorg/modules//libexa.so
(II) Module exa: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 2.2.0
	ABI class: X.Org Video Driver, version 2.0
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module "ramdac" already built-in
(II) intel(0): Comparing regs from server start up to After PreInit
(WW) intel(0): Register 0x68000 (TV_CTL) changed from 0x10000030 to 0x000c0c30
(WW) intel(0): Register 0x68010 (TV_CSC_Y) changed from 0x00000000 to 0x0332012d
(WW) intel(0): Register 0x68014 (TV_CSC_Y2) changed from 0x00000000 to 0x07d30104
(WW) intel(0): Register 0x68018 (TV_CSC_U) changed from 0x00000000 to 0x0733052d
(WW) intel(0): Register 0x6801c (TV_CSC_U2) changed from 0x00000000 to 0x05c70200
(WW) intel(0): Register 0x68020 (TV_CSC_V) changed from 0x00000000 to 0x0340030c
(WW) intel(0): Register 0x68024 (TV_CSC_V2) changed from 0x00000000 to 0x06d00200
(WW) intel(0): Register 0x68028 (TV_CLR_KNOBS) changed from 0x00000000 to 0x00606000
(WW) intel(0): Register 0x6802c (TV_CLR_LEVEL) changed from 0x00000000 to 0x010b00e1
(WW) intel(0): Register 0x68030 (TV_H_CTL_1) changed from 0x00000000 to 0x00400359
(WW) intel(0): Register 0x68034 (TV_H_CTL_2) changed from 0x00000000 to 0x80480022
(WW) intel(0): Register 0x68038 (TV_H_CTL_3) changed from 0x00000000 to 0x007c0344
(WW) intel(0): Register 0x6803c (TV_V_CTL_1) changed from 0x00000000 to 0x00f01415
(WW) intel(0): Register 0x68040 (TV_V_CTL_2) changed from 0x00000000 to 0x00060607
(WW) intel(0): Register 0x68044 (TV_V_CTL_3) changed from 0x00000000 to 0x80120001
(WW) intel(0): Register 0x68048 (TV_V_CTL_4) changed from 0x00000000 to 0x000900f0
(WW) intel(0): Register 0x6804c (TV_V_CTL_5) changed from 0x00000000 to 0x000a00f0
(WW) intel(0): Register 0x68050 (TV_V_CTL_6) changed from 0x00000000 to 0x000900f0
(WW) intel(0): Register 0x68054 (TV_V_CTL_7) changed from 0x00000000 to 0x000a00f0
(WW) intel(0): Register 0x68060 (TV_SC_CTL_1) changed from 0x00000000 to 0xc1710088
(WW) intel(0): Register 0x68064 (TV_SC_CTL_2) changed from 0x00000000 to 0x4e2d1dc8
(WW) intel(0): Register 0x68070 (TV_WIN_POS) changed from 0x00000000 to 0x00360024
(WW) intel(0): Register 0x68074 (TV_WIN_SIZE) changed from 0x00000000 to 0x02640198
(WW) intel(0): Register 0x68080 (TV_FILTER_CTL_1) changed from 0x00000000 to 0x80003ffc
(WW) intel(0): Register 0x68084 (TV_FILTER_CTL_2) changed from 0x00000000 to 0x00007fff
(WW) intel(0): Register 0x68088 (TV_FILTER_CTL_3) changed from 0x00000000 to 0x00003fff
(WW) intel(0): Register 0x68100 (TV_H_LUMA_0) changed from 0x00000000 to 0xb1403000
(WW) intel(0): Register 0x681ec (TV_H_LUMA_59) changed from 0x00000000 to 0x0000b060
(WW) intel(0): Register 0x68200 (TV_H_CHROMA_0) changed from 0x00000000 to 0xb1403000
(WW) intel(0): Register 0x682ec (TV_H_CHROMA_59) changed from 0x00000000 to 0x0000b060
(==) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xf7ec0000 - 0xf7efffff (0x40000) MS[B]
	[1] 0	0	0xd0000000 - 0xdfffffff (0x10000000) MS[B]
	[2] 0	0	0xf7f00000 - 0xf7f7ffff (0x80000) MS[B]
	[3] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0xfbfc0000 - 0xfbffffff (0x40000) MX[B]
	[8] -1	0	0xf7eb7c00 - 0xf7eb7fff (0x400) MX[B]
	[9] -1	0	0xf7eb8000 - 0xf7ebbfff (0x4000) MX[B]
	[10] -1	0	0xf7f80000 - 0xf7ffffff (0x80000) MX[B](B)
	[11] -1	0	0xf7ec0000 - 0xf7efffff (0x40000) MX[B](B)
	[12] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[13] -1	0	0xf7f00000 - 0xf7f7ffff (0x80000) MX[B](B)
	[14] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[15] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[16] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[17] 0	0	0x0000ec00 - 0x0000ec07 (0x8) IS[B]
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[21] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[22] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[26] -1	0	0x0000e880 - 0x0000e89f (0x20) IX[B]
	[27] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[28] -1	0	0x0000e480 - 0x0000e49f (0x20) IX[B]
	[29] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[30] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B](B)
	[31] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[32] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) intel(0): Kernel reported 238848 total, 1 used
(II) intel(0): I830CheckAvailableMemory: 955388 kB available
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(II) [drm] loaded kernel module for "i915" driver.
(II) [drm] DRM interface version 1.3
(II) [drm] DRM open master succeeded.
(II) intel(0): [drm] Using the DRM lock SAREA also for drawables.
(II) intel(0): [drm] framebuffer mapped by ddx driver
(II) intel(0): [drm] added 1 reserved context for kernel
(II) intel(0): X context handle = 0x1
(II) intel(0): [drm] installed DRM signal handler
(==) intel(0): VideoRam: 262144 KB
(**) intel(0): Framebuffer compression enabled
(**) intel(0): Tiling enabled
(II) intel(0): Attempting memory allocation with tiled buffers.
(II) intel(0): Success.
(II) intel(0): [drm] Registers = 0xf7f00000
(II) intel(0): [drm] ring buffer = 0xd0000000
(II) intel(0): [drm] mapped front buffer at 0xd0800000, handle = 0xd0800000
(II) intel(0): [drm] mapped back buffer at 0xd1800000, handle = 0xd1800000
(II) intel(0): [drm] mapped depth buffer at 0xd1c00000, handle = 0xd1c00000
(II) intel(0): [drm] mapped classic textures at 0xd2000000, handle = 0xd2000000
(II) intel(0): [drm] Initialized kernel agp heap manager, 33554432
(II) intel(0): [dri] visual configs initialized
(II) intel(0): Page Flipping disabled
(==) intel(0): Write-combining range (0xd0000000,0x10000000)
(II) intel(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(WW) intel(0): EXA greedy migration mode enabled.
(II) EXA(0): Forcing greedy migration option
(II) EXA(0): Offscreen pixmap area of 12582912 bytes
(II) EXA(0): Driver registered support for the following operations:
(II)         Solid
(II)         Copy
(II)         Composite (RENDER acceleration)
(==) intel(0): Backing store disabled
(==) intel(0): Silken mouse enabled
(II) intel(0): Initializing HW Cursor
(II) intel(0): [DRI] installation complete
(II) intel(0): xf86BindGARTMemory: bind key 0 at 0x00800000 (pgoffset 2048)
(II) intel(0): xf86BindGARTMemory: bind key 1 at 0x00c00000 (pgoffset 3072)
(II) intel(0): xf86BindGARTMemory: bind key 2 at 0x01800000 (pgoffset 6144)
(II) intel(0): xf86BindGARTMemory: bind key 3 at 0x01c00000 (pgoffset 7168)
(II) intel(0): xf86BindGARTMemory: bind key 4 at 0x02000000 (pgoffset 8192)
(II) intel(0): Fixed memory allocation layout:
(II) intel(0): 0x00000000-0x0001ffff: ring buffer (128 kB)
(II) intel(0): 0x00020000-0x0061ffff: compressed frame buffer (6144 kB, 0x000000003f820000 physical
)
(II) intel(0): 0x00620000-0x00620fff: compressed ll buffer (4 kB, 0x000000003fe20000 physical
)
(II) intel(0): 0x00621000-0x0062afff: HW cursors (40 kB, 0x000000003fe21000 physical
)
(II) intel(0): 0x0062b000-0x00632fff: logical 3D context (32 kB)
(II) intel(0): 0x00633000-0x00633fff: overlay registers (4 kB, 0x000000003fe33000 physical
)
(II) intel(0): 0x007bf000:            end of stolen memory
(II) intel(0): 0x00800000-0x00bfffff: front buffer (4096 kB) X tiled
(II) intel(0): 0x00c00000-0x017fffff: exa offscreen (12288 kB)
(II) intel(0): 0x01800000-0x01bfffff: back buffer (4096 kB) X tiled
(II) intel(0): 0x01c00000-0x01ffffff: depth buffer (4096 kB) X tiled
(II) intel(0): 0x02000000-0x03ffffff: classic textures (32768 kB)
(II) intel(0): 0x10000000:            end of aperture
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc enabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): Output configuration:
(II) intel(0):   Pipe A is off
(II) intel(0):   Display plane A is now disabled and connected to pipe A.
(II) intel(0):   Pipe B is on
(II) intel(0):   Display plane B is now enabled and connected to pipe B.
(II) intel(0):   Output VGA is connected to pipe none
(II) intel(0):   Output LVDS is connected to pipe B
(II) intel(0):   Output TV is connected to pipe none
(II) intel(0): [drm] dma control initialized, using IRQ 16
(II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(II) intel(0): DPMS enabled
(II) intel(0): Set up overlay video
(II) intel(0): direct rendering: Enabled
(--) RandR disabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: drmOpenMinor returns 9
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(WW) AIGLX: 3D driver claims to not support visual 0x23
(WW) AIGLX: 3D driver claims to not support visual 0x24
(WW) AIGLX: 3D driver claims to not support visual 0x25
(WW) AIGLX: 3D driver claims to not support visual 0x26
(WW) AIGLX: 3D driver claims to not support visual 0x27
(WW) AIGLX: 3D driver claims to not support visual 0x28
(WW) AIGLX: 3D driver claims to not support visual 0x29
(WW) AIGLX: 3D driver claims to not support visual 0x2a
(WW) AIGLX: 3D driver claims to not support visual 0x2b
(WW) AIGLX: 3D driver claims to not support visual 0x2c
(WW) AIGLX: 3D driver claims to not support visual 0x2d
(WW) AIGLX: 3D driver claims to not support visual 0x2e
(WW) AIGLX: 3D driver claims to not support visual 0x2f
(WW) AIGLX: 3D driver claims to not support visual 0x30
(WW) AIGLX: 3D driver claims to not support visual 0x31
(WW) AIGLX: 3D driver claims to not support visual 0x32
(II) AIGLX: Loaded and initialized /usr/lib/dri/i915_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
(II) intel(0): Setting screen physical size to 270 x 158
Atom 4, CARD32 4, unsigned long 4
(II) Synaptics touchpad driver version 0.14.6 (1406)
Synaptics Touchpad no synaptics event device found (checked 18 nodes)
(**) Option "Device" "/dev/psaux"
(**) Option "HorizEdgeScroll" "0"
Query no Synaptics: 6003C8
(EE) Synaptics Touchpad no synaptics touchpad detected and no repeater device
(EE) Synaptics Touchpad Unable to query/initialize Synaptics hardware.
(EE) PreInit failed for input device "Synaptics Touchpad"
(II) UnloadModule: "synaptics"
(WW) Configured Mouse: No Device specified, looking for one...
(II) Configured Mouse: Setting Device option to "/dev/input/mice"
(--) Configured Mouse: Device: "/dev/input/mice"
(==) Configured Mouse: Protocol: "Auto"
(**) Option "CorePointer"
(**) Configured Mouse: always reports core events
(**) Option "Device" "/dev/input/mice"
(==) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Configured Mouse: Sensitivity: 1
(**) Option "CoreKeyboard"
(**) Generic Keyboard: always reports core events
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "se"
(**) Generic Keyboard: XkbLayout: "se"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(II) evaluating device (Generic Keyboard)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) evaluating device (Configured Mouse)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(--) Configured Mouse: PnP-detected protocol: "ExplorerPS/2"
(II) Configured Mouse: ps2EnableDataReporting: succeeded
[config/hal] couldn't initialise context: (null) ((null))
(II) AIGLX: Suspending AIGLX clients for VT switch
(II) intel(0): fbc disabled on plane a
(II) intel(0): xf86UnbindGARTMemory: unbind key 0
(II) intel(0): xf86UnbindGARTMemory: unbind key 1
(II) intel(0): xf86UnbindGARTMemory: unbind key 2
(II) intel(0): xf86UnbindGARTMemory: unbind key 3
(II) intel(0): xf86UnbindGARTMemory: unbind key 4

```

---

### Post by seatownflyer on 2008-10-16
This won't solve your problem, but you might also check out this website.  this guy made a kernel specifically for the eee pc.  works great.  fast boot up.

[http://www.array.org/ubuntu/index.html]("http://www.array.org/ubuntu/index.html")

---

### Post by unutbu on 2008-10-16
Please post the output of 
```

ls -l /etc/X11/
```

---

### Post by Bluebottel on 2008-10-16
Heres the spitout from ls -ls /etc/X11

```

total 120
drwxr-xr-x 2 root root  4096 2008-08-22 22:07 app-defaults
drwxr-xr-x 2 root root  4096 2008-08-22 22:07 cursors
-rw-r--r-- 1 root root    14 2008-08-22 22:07 default-display-manager
drwxr-xr-x 6 root root  4096 2008-08-22 22:07 fonts
-rw-r--r-- 1 root root 17394 2008-08-22 22:07 rgb.txt
lrwxrwxrwx 1 root root    13 2008-10-05 17:56 X -> /usr/bin/Xorg
drwxr-xr-x 3 root root  4096 2008-08-22 22:07 xinit
drwxr-xr-x 2 root root  4096 2008-08-22 22:07 xkb
-rw-r--r-- 1 root root  1475 2008-10-15 01:41 xorg.conf
-rw-r--r-- 1 root root  1475 2008-10-12 13:31 xorg.conf.20081012133149
-rw-r--r-- 1 root root  1475 2008-10-12 13:37 xorg.conf.20081012133713
-rw-r--r-- 1 root root  1475 2008-10-12 14:14 xorg.conf.20081012141405
-rw-r--r-- 1 root root  1503 2008-10-12 21:39 xorg.conf.20081012213910
-rw-r--r-- 1 root root  1475 2008-10-12 21:42 xorg.conf.20081012214249
-rw-r--r-- 1 root root  1493 2008-10-12 21:57 xorg.conf.20081012215736
-rw-r--r-- 1 root root  1475 2008-10-12 21:59 xorg.conf.20081012215930
-rw-r--r-- 1 root root  1475 2008-10-12 22:15 xorg.conf.20081012221503
-rw-r--r-- 1 root root  1512 2008-10-15 01:16 xorg.conf.20081015011604
-rw-r--r-- 1 root root  1627 2008-10-15 01:41 xorg.conf.20081015014106
-rw-r--r-- 1 root root  1238 2008-10-15 01:37 xorg.conf.failsafe
-rw-r--r-- 1 root root  1238 2008-10-15 01:23 xorg.conf.failsafe.bak
drwxr-xr-x 2 root root  4096 2008-08-22 22:07 Xresources
drwxr-xr-x 2 root root  4096 2008-08-22 22:07 xserver
-rwxr-xr-x 1 root root  3730 2008-08-22 22:07 Xsession
drwxr-xr-x 2 root root  4096 2008-08-22 22:07 Xsession.d
-rw-r--r-- 1 root root   265 2008-08-22 22:07 Xsession.options
-rw------- 1 root root   614 2008-08-22 22:07 Xwrapper.config

```

---

### Post by unutbu on 2008-10-16
It appears you have some backup copies of xorg.conf which date back prior to the accident. Perhaps we can use one of these backups to restore the X server. Try this:

```
cd /etc/X11
sudo cp xorg.conf xorg.conf.20081016-broken   # backup just in case
sudo cp xorg.conf.20081015014106 xorg.conf    # copy a backup version to xorg.conf
```

Then try rebooting. 

If it doesn't work, try each of these in succession (rebooting after each try)
```

sudo cp xorg.conf.20081015011604 xorg.conf
sudo cp xorg.conf.failsafe xorg.conf
sudo cp xorg.conf.20081012221503 xorg.conf
```

---

### Post by Bluebottel on 2008-10-16
Tried all of the above with full reboots in between (as in a complete shutdown and starting up again).
There is no difference that i can see at all with the exception of a few bug-ish looking green lines on the top of the screen when the ubuntu logo should be while logging in.

---

### Post by unutbu on 2008-10-16
Ok, let's restore your old xorg.conf:
```

cd /etc/X11
sudo cp xorg.conf.20081016-broken xorg.conf

```

I thought I had a way to solve this problem, but apparently not. 

Hm. Well, perhaps someone will get an idea if you post your /etc/X11/xorg.conf.

---

### Post by Bluebottel on 2008-10-16
Sounds like a good idea. In other words; heres the xorg.conf
```

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"se"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
EndSection


Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection
Section "Device"
	Identifier	"Configured Video Device"
	Driver		"vesa"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection

```

---

### Post by unutbu on 2008-10-16
Please also post the output of 
```

lspci
```

---

### Post by Bluebottel on 2008-10-16
Heres the lspci output:
```

00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 04)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 04)
00:1c.2 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
03:00.0 Ethernet controller: Attansic Technology Corp. L2 100 Mbit Ethernet Adapter (rev a0)

```

---

### Post by Wickd on 2008-10-17
Hi there!

Had exactly this error and easily resolved it with a re-installation of my graphics drivers. I also got the black screen after an update of my Kerenl headers. What graphics adapter do you use?

Chz

---

### Post by Bluebottel on 2008-10-17
Its a intel graphics media accelerator 900 which barely qualifies as a graphicscard to my knowledge. Stock one that comes with the asus eee 900.

---

### Post by unutbu on 2008-10-17
There is an intel video driver. You could try enabling it this way:
```

sudo nano /etc/X11/xorg.conf
```
Find the line that says```

Driver "vesa"
```
and change it to```

Driver "intel"
```

If that does not work, would you do the following:
```
mkdir ~/xorgs
cp /etc/X11/xorg* ~/xorgs
tar cjf xorgs.tar.bz2 ~/xorgs
```
Then post xorgs.tar.bz2 as an attachment.

---

### Post by Bluebottel on 2008-10-17
Not that pretty, but hopefully it works.

---

### Post by unutbu on 2008-10-17
This post seems very similar to yours:
[http://ubuntuforums.org/showthread.php?t=797264](http://ubuntuforums.org/showthread.php?t=797264)

The solution, Nycticorax used involved reseting the gnome screen resolution. 

Perhaps try this: When you get to the login window, press F10. Choose "Select Session". Change the session type to "Failsafe GNOME". See if you can log in to a graphical environment this way. Then go to System>Preferences>Screen Resolution and see if you can reset the screen resolution as Nycticorax mentions.

---

### Post by Bluebottel on 2008-10-17
Its slightly similiar to mine but key details are different. I cant see anything and pressing F10 yields nothing.
All ive got is a black screen with cursor that i can move around.

---

### Post by unutbu on 2008-10-17
When you typed
```

sudo startx

```
and got 
> 
server is already active for display 0
if this server is no longer running, remove /tmp/.X0-lock

I interpret this to mean that gdm successfully launched the X server. You got this error message because the X server was already running. But there is some error resulting in a black screen. I did not realize you could not see the GDM login screen however.

Hm. Perhaps try this:
```

ps axuw | grep /usr/bin/X
```

If the X server is running, you will see something like
```

root     15545  1.6  3.7  45084 38948 tty7     RLs+ 19:42   3:31 /usr/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth vt7
```

Stop it with 
```

sudo kill -9 PID

```
In the above example, you would replace PID with 15545:
```

sudo kill -9 15545
```

(The PID, 15545, is the number in the second column of the output of the "ps auxw" command).

Now type
```

sudo startx 2>~/startx.txt 1>&2 
```

Please post what you see at this point. Do you see a grey checkered pattern? 
Whatever the case, please post the contents of startx.txt.

---

### Post by Bluebottel on 2008-10-18
I killed the process and the... "focus"... switches to the view where x is supposed to be showing.
The screen is black with a pointer in the middle so i switch back to view one (what do i call that? Virtual terminal 1?)  
and run this:
```

sudo startx 2>~/startx.txt 1>&2

```

And heres startx.txt
```
X: warning; process set to priority -1 instead of requested priority 0

Fatal server error:
Server is already active for display 0
	If this server is no longer running, remove /tmp/.X0-lock
	and start again.

Invalid MIT-MAGIC-COOKIE-1 keygiving up.
xinit:  Resource temporarily unavailable (errno 11):  unable to connect to X server
xinit:  No such process (errno 3):  Server error.
```

---

### Post by unutbu on 2008-10-18
Hm. Perhaps try the following:
```

chown -R $USER:$USER ~          # Sudo might have changed the ownership of your .Xauthority. chown will change it back.
startx -- :1 2> startx.txt
```
Then post startx.txt again.

---

### Post by Bluebottel on 2008-10-19
Running this 
```
chown -R $USER:$USER ~          # Sudo might have changed the ownership of your .Xauthority. chown will change it back.
startx -- :1 2> startx.txt
```

Produces this
```
This is a pre-release version of the X server from The X.Org Foundation.
It is not supported in any way.
Bugs may be filed in the bugzilla at http://bugs.freedesktop.org/.
Select the "xorg" product for bugs you find in this release.
Before reporting bugs in pre-release versions please check the
latest version in the X.Org Foundation git repository.
See http://wiki.x.org/wiki/GitPage for git access instructions.

X.Org X Server 1.4.0.90
Release Date: 5 September 2007
X Protocol Version 11, Revision 0
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9.2)
Current Operating System: Linux Bluebox 2.6.24-21-eeepc #1 SMP Thu Aug 7 22:18:05 MDT 2008 i686
Build Date: 13 June 2008  01:08:21AM
 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.1.log", Time: Sun Oct 19 11:32:24 2008
(==) Using config file: "/etc/X11/xorg.conf"
(WW) intel: No matching Device section for instance (BusID PCI:0:2:1) found
(II) Module "ddc" already built-in
(II) Module "i2c" already built-in
(II) Module "ramdac" already built-in
(EE) [drm] Could not set DRM device bus ID.
(EE) intel(0): [dri] DRIScreenInit failed. Disabling DRI.
expected keysym, got XF86KbdLightOnOff: line 70 of pc
expected keysym, got XF86KbdBrightnessDown: line 71 of pc
expected keysym, got XF86KbdBrightnessUp: line 72 of pc
Atom 4, CARD32 4, unsigned long 4
Synaptics Touchpad no synaptics event device found (checked 18 nodes)
Query no Synaptics: 6003C8
(EE) Synaptics Touchpad no synaptics touchpad detected and no repeater device
(EE) Synaptics Touchpad Unable to query/initialize Synaptics hardware.
(EE) PreInit failed for input device "Synaptics Touchpad"
expected keysym, got XF86KbdLightOnOff: line 70 of pc
expected keysym, got XF86KbdBrightnessDown: line 71 of pc
expected keysym, got XF86KbdBrightnessUp: line 72 of pc
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
[config/hal] couldn't initialise context: (null) ((null))

waiting for X server to shut down .FreeFontPath: FPE "/usr/share/fonts/X11/misc" refcount is 2, should be 1; fixing.
```

I also get the checkered pattern with alternating black and white pixels on the screen along with a mousepointer looking like a X.

---

### Post by unutbu on 2008-10-19
Well, it looks like there is nothing wrong with your X server. That's good news. However, it begs the question why your gdm login screen is not working.

If your internet connection is working, perhaps try
```

sudo apt-get install gdm --reinstall

```
Then reboot. If that does not work, please post the output of 
```
ps auxww
```
after the reboot.

---

### Post by Bluebottel on 2008-10-22
Some school related stuff caught my attention and delayed my reply, sorry about that.
For no apparent reason my internet connection wont work so I figured that it would be equivalent with a .deb file. 
I downloaded the gdm2_.20.7-0ubuntu1.1_i386.deb file that apt-get failed to fetch for me and intalled it.

Heres the output from ps auxww
```

USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.4  0.1   2844  1688 ?        Ss   16:22   0:00 /sbin/init
root         2  0.0  0.0      0     0 ?        S<   16:22   0:00 [kthreadd]
root         3  0.0  0.0      0     0 ?        S<   16:22   0:00 [migration/0]
root         4  0.0  0.0      0     0 ?        S<   16:22   0:00 [ksoftirqd/0]
root         5  0.0  0.0      0     0 ?        S<   16:22   0:00 [watchdog/0]
root         6  0.0  0.0      0     0 ?        S<   16:22   0:00 [events/0]
root         7  0.0  0.0      0     0 ?        S<   16:22   0:00 [khelper]
root        35  0.0  0.0      0     0 ?        S<   16:22   0:00 [kblockd/0]
root        38  0.0  0.0      0     0 ?        S<   16:22   0:00 [kacpid]
root        39  0.0  0.0      0     0 ?        S<   16:22   0:00 [kacpi_notify]
root       122  0.0  0.0      0     0 ?        S<   16:22   0:00 [kseriod]
root       156  0.0  0.0      0     0 ?        S    16:22   0:00 [pdflush]
root       157  0.0  0.0      0     0 ?        S    16:22   0:00 [pdflush]
root       158  0.0  0.0      0     0 ?        S<   16:22   0:00 [kswapd0]
root       199  0.0  0.0      0     0 ?        S<   16:22   0:00 [aio/0]
root      1425  0.0  0.0      0     0 ?        S<   16:22   0:00 [ksuspend_usbd]
root      1428  0.0  0.0      0     0 ?        S<   16:22   0:00 [khubd]
root      1455  0.0  0.0      0     0 ?        S<   16:22   0:00 [ata/0]
root      1457  0.0  0.0      0     0 ?        S<   16:22   0:00 [ata_aux]
root      1762  0.0  0.0      0     0 ?        S<   16:22   0:00 [scsi_eh_0]
root      1764  0.0  0.0      0     0 ?        S<   16:22   0:00 [scsi_eh_1]
root      2212  0.0  0.0      0     0 ?        S<   16:22   0:00 [scsi_eh_2]
root      2214  0.0  0.0      0     0 ?        S<   16:22   0:00 [usb-storage]
root      2330  0.0  0.0      0     0 ?        S<   16:22   0:00 [kjournald]
root      2498  0.2  0.0   2412   960 ?        S<s  16:22   0:00 /sbin/udevd --daemon
root      2854  0.0  0.0      0     0 ?        S<   16:22   0:00 [kpsmoused]
root      3721  0.0  0.0      0     0 ?        S<   16:22   0:00 [pciehpd]
root      4173  0.0  0.0   1716   504 tty4     Ss+  16:22   0:00 /sbin/getty 38400 tty4
root      4174  0.0  0.0   1716   508 tty5     Ss+  16:22   0:00 /sbin/getty 38400 tty5
root      4180  0.0  0.0   1716   512 tty2     Ss+  16:22   0:00 /sbin/getty 38400 tty2
root      4184  0.0  0.0   1716   512 tty3     Ss+  16:22   0:00 /sbin/getty 38400 tty3
root      4185  0.0  0.0   1716   508 tty6     Ss+  16:22   0:00 /sbin/getty 38400 tty6
root      4348  0.0  0.1   2352  1312 ?        Ss   16:22   0:00 /usr/sbin/acpid -c /etc/acpi/events -s /var/run/acpid.socket
root      4390  0.0  0.0      0     0 ?        S<   16:22   0:00 [kondemand/0]
syslog    4452  0.0  0.0   1936   648 ?        Rs   16:22   0:00 /sbin/syslogd -u syslog
root      4508  0.0  0.0   1872   540 ?        S    16:22   0:00 /bin/dd bs 1 if /proc/kmsg of /var/run/klogd/kmsg
klog      4510  0.1  0.2   3276  2112 ?        Ss   16:22   0:00 /sbin/klogd -P /var/run/klogd/kmsg
108       4557  7.6  0.1   2688  1068 ?        Ss   16:22   0:15 /usr/bin/dbus-daemon --system
root      4586  0.0  0.1   3104  1124 ?        Ss   16:22   0:00 /usr/sbin/NetworkManagerDispatcher --pid-file /var/run/NetworkManager/NetworkManagerDispatcher.pid
avahi     4622  0.8  0.1   2760  1352 ?        Ss   16:22   0:01 avahi-daemon: running [Bluebox.local]
avahi     4623  0.0  0.0   2760   464 ?        Ss   16:22   0:00 avahi-daemon: chroot helper
root      4662  0.0  0.2   5920  2140 ?        Ss   16:22   0:00 /usr/sbin/cupsd
root      4708  0.0  0.1   8084  1284 ?        Ss   16:22   0:00 /usr/sbin/winbindd
root      4721  0.0  0.1   8084  1056 ?        S    16:22   0:00 /usr/sbin/winbindd
root      4744  0.0  0.0   2020   764 ?        Ss   16:22   0:00 /usr/sbin/dhcdbd --system
root      4785  0.0  0.1   2780  1124 ?        Ss   16:22   0:00 /usr/sbin/hcid -x -s
root      4791  0.0  0.0      0     0 ?        S<   16:22   0:00 [btaddconn]
root      4792  0.0  0.0      0     0 ?        S<   16:22   0:00 [btdelconn]
root      4798  0.0  0.1   2692  1148 ?        S    16:22   0:00 /usr/lib/bluetooth/bluetoothd-service-audio
root      4800  0.0  0.0   2628   984 ?        S    16:22   0:00 /usr/lib/bluetooth/bluetoothd-service-input
root      4807  0.0  0.0      0     0 ?        S<   16:22   0:00 [krfcommd]
root      4845  0.1  0.1  13764  1488 ?        Ss   16:22   0:00 /usr/sbin/gdm
root      4846  5.6  1.4  25948 14388 ?        S    16:22   0:10 /usr/sbin/gdm
root      4852  2.9  0.5  11160  5944 tty7     Ss+  16:22   0:05 /usr/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7
root      4886  0.0  0.0   1712   632 ?        Ss   16:22   0:00 /usr/sbin/anacron -s
root      4913  0.0  0.0   2104   888 ?        Ss   16:22   0:00 /usr/sbin/cron
root      5022  0.0  0.1   2568  1208 tty1     Ss   16:22   0:00 /bin/login --           
1000      5164  0.2  0.2   5568  2952 tty1     S    16:23   0:00 -bash
root      6927  0.0  0.0      0     0 ?        S<   16:23   0:00 [scsi_eh_3]
root      6928  0.0  0.0      0     0 ?        S<   16:23   0:00 [usb-storage]
root     20896  0.0  0.0   2644  1008 tty1     R+   16:26   0:00 ps auxww

```

---

### Post by unutbu on 2008-10-22
Hm. I'm really quite stumped by this.
When you boot up, do you see any text at all? Do you see the orange bar that moves back and forth? 

When you get to the black login screen, is the mouse cursor a nice looking graphical cursor, or is it a chunky square?

It might be helpful to me or others if you type this:
```

tail -n 500 /var/log/messages > ~/messages.txt
tail -n 500 /var/log/dmesg > ~/dmesg.txt
```

and post messages.txt and dmesg.txt.

We've worked on this for a few days now and are no closer to a solution than when you first posted. It only takes about 30 minutes to do a fresh install. Do you have some way to backup your data? Although it would be nice to figure out the problem and fix it the "proper" way, as a practical matter, it might be faster to backup your data and re-install.

---

### Post by Bluebottel on 2008-10-22
I agree that formatting is starting to be worth it. I wanted to give it a shot at asking here first though. 
I reasoned that i might just learn something or that i could deal with it myself if the problem ever ocurred again. 

Anyway, thank you for your time. I appretiate it alot and have even picked up a few things here and there because of it.

Heres dmesg.txt
```

[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-21-eeepc (root@adamm-laptop) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Thu Aug 7 22:18:05 MDT 2008 (Ubuntu 2.6.24-4.6-eeepc)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003f780000 (usable)
[    0.000000]  BIOS-e820: 000000003f780000 - 000000003f790000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003f790000 - 000000003f7d0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003f7d0000 - 000000003f7de000 (reserved)
[    0.000000]  BIOS-e820: 000000003f7e0000 - 000000003f800000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] 119MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000ff780
[    0.000000] Entering add_active_range(0, 0, 259968) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   259968
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   259968
[    0.000000] On node 0 totalpages: 259968
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 239 pages used for memmap
[    0.000000]   HighMem zone: 30353 pages, LIFO batch:7
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP signature @ 0xC00FBE60 checksum 0
[    0.000000] ACPI: RSDP 000FBE60, 0014 (r0 ACPIAM)
[    0.000000] ACPI: RSDT 3F780000, 0034 (r1 A M I  OEMRSDT   7000807 MSFT       97)
[    0.000000] ACPI: FACP 3F780200, 0081 (r1 A M I  OEMFACP   7000807 MSFT       97)
[    0.000000] ACPI: DSDT 3F780400, 6105 (r1  A0979 A0979029       29 INTL 20060113)
[    0.000000] ACPI: FACS 3F790000, 0040
[    0.000000] ACPI: APIC 3F780390, 0068 (r1 A M I  OEMAPIC   7000807 MSFT       97)
[    0.000000] ACPI: OEMB 3F790040, 0046 (r1 A M I  AMI_OEM   7000807 MSFT       97)
[    0.000000] ACPI: MCFG 3F786510, 003C (r1 A M I  OEMMCFG   7000807 MSFT       97)
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:13 APIC version 20
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 3f800000:bf600000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e4000
[    0.000000] swsusp: Registered nosave memory region: 00000000000e4000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 257937
[    0.000000] Kernel command line: root=UUID=dee2a292-e990-4687-9061-47bc844bf7d4 ro quiet splash
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 900.132 MHz processor.
[   10.025805] Console: colour VGA+ 80x25
[   10.025811] console [tty0] enabled
[   10.026244] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   10.027044] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   10.080225] Memory: 1021216k/1039872k available (2123k kernel code, 17880k reserved, 984k data, 264k init, 122368k highmem)
[   10.080240] virtual kernel memory layout:
[   10.080242]     fixmap  : 0xfff9a000 - 0xfffff000   ( 404 kB)
[   10.080245]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   10.080247]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   10.080250]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   10.080252]       .init : 0xc040f000 - 0xc0451000   ( 264 kB)
[   10.080254]       .data : 0xc0312c2a - 0xc0408ca4   ( 984 kB)
[   10.080257]       .text : 0xc0100000 - 0xc0312c2a   (2123 kB)
[   10.080263] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   10.080340] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   10.160329] Calibrating delay using timer specific routine.. 1802.04 BogoMIPS (lpj=3604081)
[   10.160381] Security Framework initialized
[   10.160394] SELinux:  Disabled at boot.
[   10.160424] AppArmor: AppArmor initialized
[   10.160431] Failure registering capabilities with primary security module.
[   10.160446] Mount-cache hash table entries: 512
[   10.160669] Initializing cgroup subsys ns
[   10.160680] Initializing cgroup subsys cpuacct
[   10.160698] CPU: After generic identify, caps: afe9fbff 00100000 00000000 00000000 00000000 00000000 00000000 00000000
[   10.160717] CPU: L1 I cache: 32K, L1 D cache: 32K
[   10.160721] CPU: L2 cache: 512K
[   10.160726] CPU: After all inits, caps: afe9fbff 00100000 00000000 00042040 00000000 00000000 00000000 00000000
[   10.160743] Compat vDSO mapped to ffffe000.
[   10.160765] Checking 'hlt' instruction... OK.
[   10.176893] SMP alternatives: switching to UP code
[   10.180120] Freeing SMP alternatives: 11k freed
[   10.180310] Early unpacking initramfs... done
[   10.645014] ACPI: Core revision 20070126
[   10.645135] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   10.791076] CPU0: Intel(R) Celeron(R) M processor          900MHz stepping 08
[   10.791110] Total of 1 processors activated (1802.04 BogoMIPS).
[   10.791270] ENABLING IO-APIC IRQs
[   10.791467] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   10.936006] Brought up 1 CPUs
[   10.936039] CPU0 attaching NULL sched-domain.
[   10.936302] net_namespace: 64 bytes
[   10.936322] Booting paravirtualized kernel on bare hardware
[   10.937136] Time: 15:50:30  Date: 10/22/08
[   10.937179] NET: Registered protocol family 16
[   10.937511] ACPI: bus type pci registered
[   10.937859] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=5
[   10.937864] PCI: Using configuration type 1
[   10.937898] Setting up standard PCI resources
[   10.953691] ACPI: EC: Look up EC in DSDT
[   10.992984] ACPI: Interpreter enabled
[   10.992990] ACPI: (supports S0 S1 S3 S4 S5)
[   10.993021] ACPI: Using IOAPIC for interrupt routing
[   11.004490] ACPI: EC: GPE = 0x18, I/O: command/status = 0x66, data = 0x62
[   11.004497] ACPI: EC: driver started in poll mode
[   11.004721] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   11.005474] Force enabled HPET at base address 0xfed00000
[   11.005483] PCI quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO
[   11.005489] PCI quirk: region 0480-04bf claimed by ICH6 GPIO
[   11.006089] PCI: Transparent bridge - 0000:00:1e.0
[   11.006142] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   11.006445] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P3._PRT]
[   11.006609] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P5._PRT]
[   11.006769] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P6._PRT]
[   11.014169] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[   11.014414] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[   11.014665] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[   11.014904] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 *7 10 11 12 14 15)
[   11.015144] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   11.015384] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   11.015625] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   11.015865] ACPI: PCI Interrupt Link [LNKH] (IRQs *3 4 5 6 7 10 11 12 14 15)
[   11.016227] Linux Plug and Play Support v0.97 (c) Adam Belay
[   11.016290] pnp: PnP ACPI init
[   11.016305] ACPI: bus type pnp registered
[   11.019877] pnp: PnP ACPI: found 13 devices
[   11.019882] ACPI: ACPI bus type pnp unregistered
[   11.020321] PCI: Using ACPI for IRQ routing
[   11.020327] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   11.043892] NET: Registered protocol family 8
[   11.043896] NET: Registered protocol family 20
[   11.044193] hpet clockevent registered
[   11.044202] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   11.044209] hpet0: 3 64-bit timers, 14318180 Hz
[   11.045275] AppArmor: AppArmor Filesystem Enabled
[   11.047879] Time: tsc clocksource has been installed.
[   11.055949] system 00:01: iomem range 0xfed13000-0xfed19fff has been reserved
[   11.055969] system 00:08: ioport range 0x380-0x383 has been reserved
[   11.055974] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[   11.055979] system 00:08: ioport range 0x800-0x87f has been reserved
[   11.055985] system 00:08: ioport range 0x480-0x4bf has been reserved
[   11.055990] system 00:08: iomem range 0xfed1c000-0xfed1ffff has been reserved
[   11.055996] system 00:08: iomem range 0xfed20000-0xfed8ffff has been reserved
[   11.056002] system 00:08: iomem range 0xfff00000-0xffffffff could not be reserved
[   11.056012] system 00:09: iomem range 0xfec00000-0xfec00fff has been reserved
[   11.056018] system 00:09: iomem range 0xfee00000-0xfee00fff could not be reserved
[   11.056028] system 00:0a: iomem range 0xe0000000-0xefffffff has been reserved
[   11.056038] system 00:0b: iomem range 0xe0000000-0xefffffff has been reserved
[   11.056050] system 00:0c: iomem range 0x0-0x9ffff could not be reserved
[   11.056056] system 00:0c: iomem range 0x0-0x0 could not be reserved
[   11.056061] system 00:0c: iomem range 0xe0000-0xfffff could not be reserved
[   11.056067] system 00:0c: iomem range 0x100000-0x3f7fffff could not be reserved
[   11.056072] system 00:0c: iomem range 0x0-0x0 could not be reserved
[   11.086813] PCI: Bridge: 0000:00:1c.0
[   11.086816]   IO window: disabled.
[   11.086823]   MEM window: disabled.
[   11.086828]   PREFETCH window: disabled.
[   11.086834] PCI: Bridge: 0000:00:1c.1
[   11.086836]   IO window: disabled.
[   11.086843]   MEM window: fbf00000-fbffffff
[   11.086848]   PREFETCH window: disabled.
[   11.086854] PCI: Bridge: 0000:00:1c.2
[   11.086856]   IO window: disabled.
[   11.086862]   MEM window: f8000000-fbefffff
[   11.086868]   PREFETCH window: f0000000-f6ffffff
[   11.086874] PCI: Bridge: 0000:00:1e.0
[   11.086876]   IO window: disabled.
[   11.086882]   MEM window: disabled.
[   11.086887]   PREFETCH window: disabled.
[   11.086923] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
[   11.086935] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   11.086956] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 17 (level, low) -> IRQ 17
[   11.086964] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   11.086985] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 18
[   11.086993] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   11.087006] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   11.087027] NET: Registered protocol family 2
[   11.123934] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   11.124348] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   11.126021] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   11.126809] TCP: Hash tables configured (established 131072 bind 65536)
[   11.126815] TCP reno registered
[   11.136103] Unpacking initramfs...<7>Switched to high resolution mode on CPU 0
[   11.601468]  done
[   11.607387] Freeing initrd memory: 4987k freed
[   11.608361] audit: initializing netlink socket (disabled)
[   11.608385] audit(1224690630.256:1): initialized
[   11.608652] highmem bounce pool size: 64 pages
[   11.612169] VFS: Disk quotas dquot_6.5.1
[   11.612312] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   11.612549] io scheduler noop registered
[   11.612553] io scheduler anticipatory registered
[   11.612557] io scheduler deadline registered
[   11.612580] io scheduler cfq registered (default)
[   11.612598] Boot video device is 0000:00:02.0
[   11.612863] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   11.612909] assign_interrupt_mode Found MSI capability
[   11.612914] Allocate Port Service[0000:00:1c.0:pcie00]
[   11.612979] Allocate Port Service[0000:00:1c.0:pcie02]
[   11.613097] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   11.613142] assign_interrupt_mode Found MSI capability
[   11.613146] Allocate Port Service[0000:00:1c.1:pcie00]
[   11.613208] Allocate Port Service[0000:00:1c.1:pcie02]
[   11.613323] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   11.613367] assign_interrupt_mode Found MSI capability
[   11.613372] Allocate Port Service[0000:00:1c.2:pcie00]
[   11.613430] Allocate Port Service[0000:00:1c.2:pcie02]
[   11.684081] Real Time Clock Driver v1.12ac
[   11.684247] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   11.685577] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   11.718279] serio: i8042 KBD port at 0x60,0x64 irq 1
[   11.718287] serio: i8042 AUX port at 0x60,0x64 irq 12
[   11.718537] mice: PS/2 mouse device common for all mice
[   11.718633] cpuidle: using governor ladder
[   11.718637] cpuidle: using governor menu
[   11.718780] NET: Registered protocol family 1
[   11.718827] Using IPI No-Shortcut mode
[   11.718874] registered taskstats version 1
[   11.719022]   Magic number: 12:57:842
[   11.719124]   hash matches device ptyu8
[   11.719136]   hash matches device ptyrb
[   11.719192] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   11.719195] EDD information not available.
[   11.719371] Freeing unused kernel memory: 264k freed
[   11.751487] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input0
[   13.072245] fuse init (API version 7.9)
[   13.091239] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   13.091250] ACPI: Processor [CPU1] (supports 8 throttling states)
[   13.096000] ACPI: EC: non-query interrupt received, switching to interrupt mode
[   13.097343] Marking TSC unstable due to: TSC halts in idle.
[   13.098650] Time: hpet clocksource has been installed.
[   13.099302] ACPI: Thermal Zone [TZ00] (42 C)
[   13.798220] usbcore: registered new interface driver usbfs
[   13.798259] usbcore: registered new interface driver hub
[   13.804862] usbcore: registered new device driver usb
[   13.821744] USB Universal Host Controller Interface driver v3.0
[   13.821836] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 19
[   13.821852] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   13.821859] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   13.822271] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   13.822310] uhci_hcd 0000:00:1d.0: irq 19, io base 0x0000e400
[   13.822535] usb usb1: configuration #1 chosen from 1 choice
[   13.822575] hub 1-0:1.0: USB hub found
[   13.822585] hub 1-0:1.0: 2 ports detected
[   13.907584] SCSI subsystem initialized
[   13.924053] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 20
[   13.924072] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   13.924079] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   13.924126] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   13.924162] uhci_hcd 0000:00:1d.1: irq 20, io base 0x0000e480
[   13.924357] usb usb2: configuration #1 chosen from 1 choice
[   13.924397] hub 2-0:1.0: USB hub found
[   13.924407] hub 2-0:1.0: 2 ports detected
[   13.948908] libata version 3.00 loaded.
[   14.027954] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   14.027973] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   14.027980] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   14.028021] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   14.028058] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000e800
[   14.028250] usb usb3: configuration #1 chosen from 1 choice
[   14.028292] hub 3-0:1.0: USB hub found
[   14.028302] hub 3-0:1.0: 2 ports detected
[   14.131933] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 16
[   14.131950] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   14.131957] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   14.131998] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[   14.132033] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000e880
[   14.132225] usb usb4: configuration #1 chosen from 1 choice
[   14.132265] hub 4-0:1.0: USB hub found
[   14.132275] hub 4-0:1.0: 2 ports detected
[   14.236058] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 19
[   14.236077] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   14.236084] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   14.236131] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[   14.240041] ehci_hcd 0000:00:1d.7: debug port 1
[   14.240049] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   14.240060] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xf7eb7c00
[   14.255694] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   14.255908] usb usb5: configuration #1 chosen from 1 choice
[   14.255950] hub 5-0:1.0: USB hub found
[   14.255961] hub 5-0:1.0: 8 ports detected
[   14.359882] ata_piix 0000:00:1f.2: version 2.12
[   14.359894] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[   14.359935] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 20
[   14.359988] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   14.362161] scsi0 : ata_piix
[   14.363378] scsi1 : ata_piix
[   14.365809] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[   14.365815] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[   14.627452] usb 5-5: new high speed USB device using ehci_hcd and address 2
[   14.699772] ata2.00: ATA-5: ASUS-PHISON SSD, TST2.04P, max UDMA/66
[   14.699780] ata2.00: 31522176 sectors, multi 0: LBA 
[   14.707750] ata2.00: configured for UDMA/66
[   14.707968] scsi 1:0:0:0: Direct-Access     ATA      ASUS-PHISON SSD  TST2 PQ: 0 ANSI: 5
[   14.760711] usb 5-5: configuration #1 chosen from 1 choice
[   14.919161] Driver 'sd' needs updating - please use bus_type methods
[   14.919312] sd 1:0:0:0: [sda] 31522176 512-byte hardware sectors (16139 MB)
[   14.919333] sd 1:0:0:0: [sda] Write Protect is off
[   14.919338] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   14.919367] sd 1:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[   14.919441] sd 1:0:0:0: [sda] 31522176 512-byte hardware sectors (16139 MB)
[   14.919458] sd 1:0:0:0: [sda] Write Protect is off
[   14.919463] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   14.919489] sd 1:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[   14.919496]  sda: sda1 sda2 < sda5 >
[   14.921849] sd 1:0:0:0: [sda] Attached SCSI disk
[   14.932147] sd 1:0:0:0: Attached scsi generic sg0 type 0
[   14.959165] usbcore: registered new interface driver libusual
[   14.971054] Initializing USB Mass Storage driver...
[   14.973576] scsi2 : SCSI emulation for USB Mass Storage devices
[   14.974202] usbcore: registered new interface driver usb-storage
[   14.974210] USB Mass Storage support registered.
[   14.974355] usb-storage: device found at 2
[   14.974359] usb-storage: waiting for device to settle before scanning
[   15.083662] Attempting manual resume
[   15.083668] swsusp: Resume From Partition 8:5
[   15.083671] PM: Checking swsusp image.
[   15.083907] PM: Resume from disk failed.
[   15.109114] kjournald starting.  Commit interval 5 seconds
[   15.109136] EXT3-fs: mounted filesystem with ordered data mode.
[   15.328074] Clocksource tsc unstable (delta = -199680276 ns)
[   17.092128] asus_eee module requires i2c-i801 module at load time if you like to access pll via proc too
[   17.092145] asus_eee version 0.3 init sucessfully
[   17.431434] Linux agpgart interface v0.102
[   17.569119] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   17.620401] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   17.663759] agpgart: Detected an Intel 915GM Chipset.
[   17.664001] agpgart: Detected 7932K stolen memory.
[   17.684826] agpgart: AGP aperture is 256M @ 0xd0000000
[   17.719877] input: Power Button (FF) as /devices/virtual/input/input1
[   17.733307] ACPI: Power Button (FF) [PWRF]
[   17.733546] input: Lid Switch as /devices/virtual/input/input2
[   17.740783] ACPI: Lid Switch [LID]
[   17.740981] input: Sleep Button (CM) as /devices/virtual/input/input3
[   17.755571] ACPI: Sleep Button (CM) [SLPB]
[   17.755718] input: Power Button (CM) as /devices/virtual/input/input4
[   17.767561] ACPI: Power Button (CM) [PWRB]
[   17.831698] Asus EeePC Hotkey Driver
[   17.831928] [eeepc hotk] Hotkey init flags 0x41.
[   17.833095] [eeepc hotk] Get control methods supported: 0x101711
[   19.090731] usb-storage: device scan complete
[   19.091270] scsi 2:0:0:0: Direct-Access     USB2.0   CardReader SD0   0100 PQ: 0 ANSI: 0
[   19.092944] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[   19.093010] sd 2:0:0:0: Attached scsi generic sg1 type 0
[   19.207604] ACPI: AC Adapter [AC0] (off-line)
[   19.375273] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input5
[   19.386543] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   20.123800] Atheros(R) L2 Ethernet Driver - version 2.0.5
[   20.123807] Copyright (c) 2007 Atheros Corporation.
[   20.124605] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   20.124622] PCI: Setting latency timer of device 0000:03:00.0 to 64
[   20.196419] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 16 (level, low) -> IRQ 16
[   20.196453] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   20.219846] hda_codec: Unknown model for ALC662, trying auto-probe from BIOS...
[   20.689736] iTCO_vendor_support: vendor-support=0
[   20.737703] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   20.737915] iTCO_wdt: Found a ICH6-M TCO device (Version=2, TCOBASE=0x0860)
[   20.737992] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   21.494302] input: PC Speaker as /devices/platform/pcspkr/input/input6
[   22.290313] ACPI: Battery Slot [BAT0] (battery present)
[   23.547629] repeat_elantech == 1
[   23.547634] repeat_elantech == 2
[   23.726886] input: ImPS/2 Logitech Wheel Mouse as /devices/platform/i8042/serio1/input/input7
[   24.908592] lp: driver loaded but no devices found
[   24.930032] ath_hal: module license 'Proprietary' taints kernel.
[   24.940453] AR5210, AR5211, AR5212, AR5416, RF5111, RF5112, RF2413, RF5413, RF2133, RF2425, RF2417)
[   25.112375] pciehp: pcie_init: hotplug controller vendor id 0x8086 device id 0x2660
[   25.112389] pciehp: pcie_init: pcie_cap_base 40
[   25.112394] pciehp: pcie_init: CAPREG offset 42 cap_reg 141
[   25.112400] pciehp: pcie_init: SLOTCAP offset 54 slot_cap 80560
[   25.112405] pciehp: pcie_init: SLOTSTATUS offset 5a slot_status 0
[   25.112410] pciehp: pcie_init: SLOTCTRL offset 58 slot_ctrl 0
[   25.112415] pciehp: HPC vendor_id 8086 device_id 2660 ss_vid 0 ss_did 0
[   25.112421] pciehp: pcie_init: SLOTCTRL 58 value read 0
[   25.112437] pciehp: pcie_init: request_irq 16 for hpc0 (returns 0)
[   25.112441] pciehp: pciehp ctrl b:d:f:irq=0x0:1c:0:10
[   25.113866] pciehp: Bypassing BIOS check for pciehp use on 0000:00:1c.0
[   25.113876] pciehp: pciehp_probe: ctrl bus=0x0, device=1c, function=0, irq=10
[   25.113883] pciehp: get_power_status - physical_slot = 0004_0001
[   25.113889] pciehp: hpc_get_power_status: SLOTCTRL 58 value read 28
[   25.113894] pciehp: get_attention_status - physical_slot = 0004_0001
[   25.113899] pciehp: hpc_get_attention_status: SLOTCTRL 58, value read 28
[   25.113904] pciehp: get_latch_status - physical_slot = 0004_0001
[   25.113909] pciehp: get_adapter_status - physical_slot = 0004_0001
[   25.113915] pciehp: Registering bus=4 dev=0 hp_slot=0 sun=1 slot_device_offset=0
[   25.113956] Load service driver hpdriver on pcie device 0000:00:1c.0:pcie02
[   25.113973] pciehp: pcie_init: hotplug controller vendor id 0x8086 device id 0x2662
[   25.113982] pciehp: pcie_init: pcie_cap_base 40
[   25.113987] pciehp: pcie_init: CAPREG offset 42 cap_reg 141
[   25.113992] pciehp: pcie_init: SLOTCAP offset 54 slot_cap 100560
[   25.113998] pciehp: pcie_init: SLOTSTATUS offset 5a slot_status 48
[   25.114003] pciehp: pcie_init: SLOTCTRL offset 58 slot_ctrl 0
[   25.114008] pciehp: pci resource[8] start=0xfbf00000(len=0x100000)
[   25.114013] pciehp: HPC vendor_id 8086 device_id 2662 ss_vid 0 ss_did 0
[   25.114018] pciehp: pcie_init: SLOTCTRL 58 value read 0
[   25.114037] pciehp: pcie_init: request_irq 17 for hpc1 (returns 0)
[   25.114042] pciehp: pciehp ctrl b:d:f:irq=0x0:1c:1:11
[   25.114050] pciehp: Bypassing BIOS check for pciehp use on 0000:00:1c.1
[   25.114055] pciehp: pciehp_probe: ctrl bus=0x0, device=1c, function=1, irq=11
[   25.114061] pciehp: get_power_status - physical_slot = 0003_0002
[   25.114066] pciehp: hpc_get_power_status: SLOTCTRL 58 value read 28
[   25.114070] pciehp: get_attention_status - physical_slot = 0003_0002
[   25.114076] pciehp: hpc_get_attention_status: SLOTCTRL 58, value read 28
[   25.114080] pciehp: get_latch_status - physical_slot = 0003_0002
[   25.114085] pciehp: get_adapter_status - physical_slot = 0003_0002
[   25.114091] pciehp: Registering bus=3 dev=0 hp_slot=0 sun=2 slot_device_offset=0
[   25.114117] Load service driver hpdriver on pcie device 0000:00:1c.1:pcie02
[   25.114128] pciehp: pcie_init: hotplug controller vendor id 0x8086 device id 0x2664
[   25.114135] pciehp: pcie_init: pcie_cap_base 40
[   25.114140] pciehp: pcie_init: CAPREG offset 42 cap_reg 141
[   25.114145] pciehp: pcie_init: SLOTCAP offset 54 slot_cap 180560
[   25.114151] pciehp: pcie_init: SLOTSTATUS offset 5a slot_status 8
[   25.114156] pciehp: pcie_init: SLOTCTRL offset 58 slot_ctrl 0
[   25.114161] pciehp: pci resource[8] start=0xf8000000(len=0x3f00000)
[   25.114166] pciehp: pci resource[9] start=0xf0000000(len=0x7000000)
[   25.114170] pciehp: HPC vendor_id 8086 device_id 2664 ss_vid 0 ss_did 0
[   25.114176] pciehp: pcie_init: SLOTCTRL 58 value read 0
[   25.114185] pciehp: pcie_init: request_irq 18 for hpc2 (returns 0)
[   25.114190] pciehp: pciehp ctrl b:d:f:irq=0x0:1c:2:12
[   25.114198] pciehp: Bypassing BIOS check for pciehp use on 0000:00:1c.2
[   25.114203] pciehp: pciehp_probe: ctrl bus=0x0, device=1c, function=2, irq=12
[   25.114209] pciehp: get_power_status - physical_slot = 0001_0003
[   25.114214] pciehp: hpc_get_power_status: SLOTCTRL 58 value read 28
[   25.114218] pciehp: get_attention_status - physical_slot = 0001_0003
[   25.114224] pciehp: hpc_get_attention_status: SLOTCTRL 58, value read 28
[   25.114228] pciehp: get_latch_status - physical_slot = 0001_0003
[   25.114233] pciehp: get_adapter_status - physical_slot = 0001_0003
[   25.114239] pciehp: Registering bus=1 dev=0 hp_slot=0 sun=3 slot_device_offset=0
[   25.114263] Load service driver hpdriver on pcie device 0000:00:1c.2:pcie02
[   25.114273] pciehp: pcie_port_service_register = 0
[   25.114277] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[   25.213260] p4-clockmod: P4/Xeon(TM) CPU On-Demand Clock Modulation available
[   25.281336] Adding 706820k swap on /dev/sda5.  Priority:-1 extents:1 across:706820k
[   25.319666] EXT3 FS on sda1, internal journal
[   25.995142] ip_tables: (C) 2000-2006 Netfilter Core Team

```

And heres messages.txt
```

Oct 22 17:22:16 Bluebox kernel: [   25.578299] EXT3 FS on sda1, internal journal
Oct 22 17:22:16 Bluebox kernel: [   26.250175] ip_tables: (C) 2000-2006 Netfilter Core Team
Oct 22 17:22:16 Bluebox kernel: [   26.789192] No dock devices found.
Oct 22 17:22:17 Bluebox kernel: [   28.138000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
Oct 22 17:22:17 Bluebox kernel: [   28.138009] apm: overridden by ACPI.
Oct 22 17:22:17 Bluebox kernel: [   28.254885] ppdev: user-space parallel port driver
Oct 22 17:22:17 Bluebox kernel: [   28.287287] audit(1224688937.446:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4663 profile="/usr/sbin/cupsd" namespace="default"
Oct 22 17:22:17 Bluebox dhcdbd: Started up.
Oct 22 17:22:17 Bluebox kernel: [   28.661606] Bluetooth: Core ver 2.11
Oct 22 17:22:17 Bluebox kernel: [   28.662467] NET: Registered protocol family 31
Oct 22 17:22:17 Bluebox kernel: [   28.662475] Bluetooth: HCI device and connection manager initialized
Oct 22 17:22:17 Bluebox kernel: [   28.662481] Bluetooth: HCI socket layer initialized
Oct 22 17:22:17 Bluebox kernel: [   28.695622] Bluetooth: L2CAP ver 2.9
Oct 22 17:22:17 Bluebox kernel: [   28.695630] Bluetooth: L2CAP socket layer initialized
Oct 22 17:22:18 Bluebox kernel: [   28.786131] Bluetooth: RFCOMM socket layer initialized
Oct 22 17:22:18 Bluebox kernel: [   28.786158] Bluetooth: RFCOMM TTY layer initialized
Oct 22 17:22:18 Bluebox kernel: [   28.786161] Bluetooth: RFCOMM ver 1.8
Oct 22 17:22:25 Bluebox kernel: [   31.294272] [drm] Initialized drm 1.1.0 20060810
Oct 22 17:22:25 Bluebox kernel: [   31.390389] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
Oct 22 17:22:25 Bluebox kernel: [   31.395511] [drm] Initialized i915 1.6.0 20060119 on minor 0
Oct 22 17:28:00 Bluebox kernel: [  334.623320] ACPI: PCI interrupt for device 0000:03:00.0 disabled
Oct 22 17:47:48 Bluebox kernel: [  336.941126] Syncing filesystems ... done.
Oct 22 17:47:48 Bluebox kernel: [  336.967840] Freezing user space processes ... (elapsed 0.01 seconds) done.
Oct 22 17:47:48 Bluebox kernel: [  336.979905] Freezing remaining freezable tasks ... (elapsed 0.00 seconds) done.
Oct 22 17:47:48 Bluebox kernel: [  336.980139] Suspending console(s)
Oct 22 17:47:48 Bluebox kernel: [  336.983017] ACPI: PCI interrupt for device 0000:00:02.0 disabled
Oct 22 17:47:48 Bluebox kernel: [  336.983792] sd 1:0:0:0: [sda] Stopping disk
Oct 22 17:47:48 Bluebox kernel: [  336.991338] pciehp_suspend ENTRY
Oct 22 17:47:48 Bluebox kernel: [  336.991362] pciehp_suspend ENTRY
Oct 22 17:47:48 Bluebox kernel: [  336.991381] pciehp_suspend ENTRY
Oct 22 17:47:48 Bluebox kernel: [  336.992489] ACPI: PCI interrupt for device 0000:00:1f.2 disabled
Oct 22 17:47:48 Bluebox kernel: [  336.993208] ACPI: PCI interrupt for device 0000:00:1d.7 disabled
Oct 22 17:47:48 Bluebox kernel: [  336.993627] ACPI: PCI interrupt for device 0000:00:1d.3 disabled
Oct 22 17:47:48 Bluebox kernel: [  336.993758] ACPI: PCI interrupt for device 0000:00:1d.2 disabled
Oct 22 17:47:48 Bluebox kernel: [  336.993889] ACPI: PCI interrupt for device 0000:00:1d.1 disabled
Oct 22 17:47:48 Bluebox kernel: [  336.994017] ACPI: PCI interrupt for device 0000:00:1d.0 disabled
Oct 22 17:47:48 Bluebox kernel: [  336.994049] pciehp_suspend ENTRY
Oct 22 17:47:48 Bluebox kernel: [  336.994227] pciehp_suspend ENTRY
Oct 22 17:47:48 Bluebox kernel: [  336.994401] pciehp_suspend ENTRY
Oct 22 17:47:48 Bluebox kernel: [  336.995001] ACPI: PCI interrupt for device 0000:00:1b.0 disabled
Oct 22 17:47:48 Bluebox kernel: [  337.019904] Disabling non-boot CPUs ...
Oct 22 17:47:48 Bluebox kernel: [    1.412105] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 16 (level, low) -> IRQ 16
Oct 22 17:47:48 Bluebox kernel: [    1.412180] pciehp_resume ENTRY
Oct 22 17:47:48 Bluebox kernel: [    1.412224] pciehp_resume ENTRY
Oct 22 17:47:48 Bluebox kernel: [    1.412268] pciehp_resume ENTRY
Oct 22 17:47:48 Bluebox kernel: [    1.412275] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 19
Oct 22 17:47:48 Bluebox kernel: [    1.412323] usb usb1: root hub lost power or was reset
Oct 22 17:47:48 Bluebox kernel: [    1.412341] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 20
Oct 22 17:47:48 Bluebox kernel: [    1.412386] usb usb2: root hub lost power or was reset
Oct 22 17:47:49 Bluebox kernel: [    1.412403] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
Oct 22 17:47:49 Bluebox kernel: [    1.412447] usb usb3: root hub lost power or was reset
Oct 22 17:47:49 Bluebox kernel: [    1.412463] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 16
Oct 22 17:47:49 Bluebox kernel: [    1.412508] usb usb4: root hub lost power or was reset
Oct 22 17:47:49 Bluebox kernel: [    1.412589] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 19
Oct 22 17:47:49 Bluebox kernel: [    1.412784] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 20
Oct 22 17:47:49 Bluebox kernel: [    1.416330] pciehp_resume ENTRY
Oct 22 17:47:49 Bluebox kernel: [    1.416333] pciehp_resume ENTRY
Oct 22 17:47:49 Bluebox kernel: [    1.416335] pciehp_resume ENTRY
Oct 22 17:47:49 Bluebox kernel: [    1.504745] ata2.00: ACPI cmd ef/03:44:00:00:00:a0 filtered out
Oct 22 17:47:49 Bluebox kernel: [    1.504758] ata2.00: ACPI cmd ef/03:0c:00:00:00:a0 filtered out
Oct 22 17:47:49 Bluebox kernel: [    1.505639] ata2.00: configured for UDMA/66
Oct 22 17:47:49 Bluebox kernel: [    1.505729] sd 1:0:0:0: [sda] 31522176 512-byte hardware sectors (16139 MB)
Oct 22 17:47:49 Bluebox kernel: [    1.505767] sd 1:0:0:0: [sda] Write Protect is off
Oct 22 17:47:49 Bluebox kernel: [    1.505821] sd 1:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
Oct 22 17:47:49 Bluebox kernel: [    1.601021] sd 1:0:0:0: [sda] Starting disk
Oct 22 17:47:49 Bluebox kernel: [    1.602826] usb 5-5: reset high speed USB device using ehci_hcd and address 2
Oct 22 17:47:49 Bluebox kernel: [    1.639392] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
Oct 22 17:47:49 Bluebox kernel: [    1.643030] Restarting tasks ... done.
Oct 22 17:47:51 Bluebox kernel: [    3.315418] Atheros(R) L2 Ethernet Driver - version 2.0.5
Oct 22 17:47:51 Bluebox kernel: [    3.315427] Copyright (c) 2007 Atheros Corporation.
Oct 22 17:47:51 Bluebox kernel: [    3.316133] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 17
Oct 22 17:47:50 Bluebox kernel: [    3.563504] input: Power Button (FF) as /devices/virtual/input/input8
Oct 22 17:47:50 Bluebox kernel: [    3.582100] ACPI: Power Button (FF) [PWRF]
Oct 22 17:47:50 Bluebox kernel: [    3.582230] input: Lid Switch as /devices/virtual/input/input9
Oct 22 17:47:50 Bluebox kernel: [    3.598582] ACPI: Lid Switch [LID]
Oct 22 17:47:50 Bluebox kernel: [    3.598692] input: Sleep Button (CM) as /devices/virtual/input/input10
Oct 22 17:47:50 Bluebox kernel: [    3.612902] ACPI: Sleep Button (CM) [SLPB]
Oct 22 17:47:50 Bluebox kernel: [    3.613009] input: Power Button (CM) as /devices/virtual/input/input11
Oct 22 17:47:50 Bluebox kernel: [    3.635263] ACPI: Power Button (CM) [PWRB]
Oct 22 17:47:50 Bluebox kernel: [    3.954794] ACPI: Thermal Zone [TZ00] (35 C)
Oct 22 17:47:51 Bluebox kernel: [    4.063959] ACPI: AC Adapter [AC0] (off-line)
Oct 22 17:47:52 Bluebox kernel: [    4.652289] ACPI: Battery Slot [BAT0] (battery present)
Oct 22 17:49:44 Bluebox kernel: [   42.567218] NET: Registered protocol family 10
Oct 22 17:49:44 Bluebox kernel: [   42.567947] lo: Disabled Privacy Extensions
Oct 22 17:49:44 Bluebox kernel: [   42.588845] ip6_tables: (C) 2000-2006 Netfilter Core Team
Oct 22 17:49:46 Bluebox exiting on signal 15
Oct 22 17:50:47 Bluebox syslogd 1.5.0#1ubuntu1: restart.
Oct 22 17:50:47 Bluebox kernel: Inspecting /boot/System.map-2.6.24-21-eeepc
Oct 22 17:50:47 Bluebox kernel: Loaded 27128 symbols from /boot/System.map-2.6.24-21-eeepc.
Oct 22 17:50:47 Bluebox kernel: Symbols match kernel version 2.6.24.
Oct 22 17:50:47 Bluebox kernel: Loaded 17539 symbols from 77 modules.
Oct 22 17:50:47 Bluebox kernel: [    0.000000] Initializing cgroup subsys cpu
Oct 22 17:50:47 Bluebox kernel: [    0.000000] Linux version 2.6.24-21-eeepc (root@adamm-laptop) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Thu Aug 7 22:18:05 MDT 2008 (Ubuntu 2.6.24-4.6-eeepc)
Oct 22 17:50:47 Bluebox kernel: [    0.000000] BIOS-provided physical RAM map:
Oct 22 17:50:47 Bluebox kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Oct 22 17:50:47 Bluebox kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Oct 22 17:50:47 Bluebox kernel: [    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
Oct 22 17:50:47 Bluebox kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000003f780000 (usable)
Oct 22 17:50:47 Bluebox kernel: [    0.000000]  BIOS-e820: 000000003f780000 - 000000003f790000 (ACPI data)
Oct 22 17:50:47 Bluebox kernel: [    0.000000]  BIOS-e820: 000000003f790000 - 000000003f7d0000 (ACPI NVS)
Oct 22 17:50:47 Bluebox kernel: [    0.000000]  BIOS-e820: 000000003f7d0000 - 000000003f7de000 (reserved)
Oct 22 17:50:47 Bluebox kernel: [    0.000000]  BIOS-e820: 000000003f7e0000 - 000000003f800000 (reserved)
Oct 22 17:50:47 Bluebox kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Oct 22 17:50:47 Bluebox kernel: [    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
Oct 22 17:50:47 Bluebox kernel: [    0.000000] 119MB HIGHMEM available.
Oct 22 17:50:47 Bluebox kernel: [    0.000000] 896MB LOWMEM available.
Oct 22 17:50:47 Bluebox kernel: [    0.000000] found SMP MP-table at 000ff780
Oct 22 17:50:47 Bluebox kernel: [    0.000000] Zone PFN ranges:
Oct 22 17:50:47 Bluebox kernel: [    0.000000]   DMA             0 ->     4096
Oct 22 17:50:47 Bluebox kernel: [    0.000000]   Normal       4096 ->   229376
Oct 22 17:50:47 Bluebox kernel: [    0.000000]   HighMem    229376 ->   259968
Oct 22 17:50:47 Bluebox kernel: [    0.000000] Movable zone start PFN for each node
Oct 22 17:50:47 Bluebox kernel: [    0.000000] early_node_map[1] active PFN ranges
Oct 22 17:50:47 Bluebox kernel: [    0.000000]     0:        0 ->   259968
Oct 22 17:50:47 Bluebox kernel: [    0.000000] DMI present.
Oct 22 17:50:47 Bluebox kernel: [    0.000000] ACPI: RSDP signature @ 0xC00FBE60 checksum 0
Oct 22 17:50:47 Bluebox kernel: [    0.000000] ACPI: RSDP 000FBE60, 0014 (r0 ACPIAM)
Oct 22 17:50:47 Bluebox kernel: [    0.000000] ACPI: RSDT 3F780000, 0034 (r1 A M I  OEMRSDT   7000807 MSFT       97)
Oct 22 17:50:47 Bluebox kernel: [    0.000000] ACPI: FACP 3F780200, 0081 (r1 A M I  OEMFACP   7000807 MSFT       97)
Oct 22 17:50:47 Bluebox kernel: [    0.000000] ACPI: DSDT 3F780400, 6105 (r1  A0979 A0979029       29 INTL 20060113)
Oct 22 17:50:47 Bluebox kernel: [    0.000000] ACPI: FACS 3F790000, 0040
Oct 22 17:50:47 Bluebox kernel: [    0.000000] ACPI: APIC 3F780390, 0068 (r1 A M I  OEMAPIC   7000807 MSFT       97)
Oct 22 17:50:47 Bluebox kernel: [    0.000000] ACPI: OEMB 3F790040, 0046 (r1 A M I  AMI_OEM   7000807 MSFT       97)
Oct 22 17:50:47 Bluebox kernel: [    0.000000] ACPI: MCFG 3F786510, 003C (r1 A M I  OEMMCFG   7000807 MSFT       97)
Oct 22 17:50:47 Bluebox kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x808
Oct 22 17:50:47 Bluebox kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Oct 22 17:50:47 Bluebox kernel: [    0.000000] Processor #0 6:13 APIC version 20
Oct 22 17:50:47 Bluebox kernel: [    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
Oct 22 17:50:47 Bluebox kernel: [    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
Oct 22 17:50:47 Bluebox kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Oct 22 17:50:47 Bluebox kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Oct 22 17:50:47 Bluebox kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Oct 22 17:50:47 Bluebox kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Oct 22 17:50:47 Bluebox kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Oct 22 17:50:47 Bluebox kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Oct 22 17:50:47 Bluebox kernel: [    0.000000] Allocating PCI resources starting at 40000000 (gap: 3f800000:bf600000)
Oct 22 17:50:47 Bluebox kernel: [    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
Oct 22 17:50:47 Bluebox kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e4000
Oct 22 17:50:47 Bluebox kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000e4000 - 0000000000100000
Oct 22 17:50:47 Bluebox kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 257937
Oct 22 17:50:47 Bluebox kernel: [    0.000000] Kernel command line: root=UUID=dee2a292-e990-4687-9061-47bc844bf7d4 ro quiet splash
Oct 22 17:50:47 Bluebox kernel: [    0.000000] Enabling fast FPU save and restore... done.
Oct 22 17:50:47 Bluebox kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Oct 22 17:50:47 Bluebox kernel: [    0.000000] Initializing CPU#0
Oct 22 17:50:47 Bluebox kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Oct 22 17:50:47 Bluebox kernel: [    0.000000] Detected 900.132 MHz processor.
Oct 22 17:50:47 Bluebox kernel: [   10.025805] Console: colour VGA+ 80x25
Oct 22 17:50:47 Bluebox kernel: [   10.025811] console [tty0] enabled
Oct 22 17:50:47 Bluebox kernel: [   10.026244] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Oct 22 17:50:47 Bluebox kernel: [   10.027044] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Oct 22 17:50:47 Bluebox kernel: [   10.080225] Memory: 1021216k/1039872k available (2123k kernel code, 17880k reserved, 984k data, 264k init, 122368k highmem)
Oct 22 17:50:47 Bluebox kernel: [   10.080240] virtual kernel memory layout:
Oct 22 17:50:47 Bluebox kernel: [   10.080242]     fixmap  : 0xfff9a000 - 0xfffff000   ( 404 kB)
Oct 22 17:50:47 Bluebox kernel: [   10.080245]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Oct 22 17:50:47 Bluebox kernel: [   10.080247]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
Oct 22 17:50:47 Bluebox kernel: [   10.080250]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
Oct 22 17:50:47 Bluebox kernel: [   10.080252]       .init : 0xc040f000 - 0xc0451000   ( 264 kB)
Oct 22 17:50:47 Bluebox kernel: [   10.080254]       .data : 0xc0312c2a - 0xc0408ca4   ( 984 kB)
Oct 22 17:50:47 Bluebox kernel: [   10.080257]       .text : 0xc0100000 - 0xc0312c2a   (2123 kB)
Oct 22 17:50:47 Bluebox kernel: [   10.080263] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Oct 22 17:50:47 Bluebox kernel: [   10.080340] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
Oct 22 17:50:47 Bluebox kernel: [   10.160329] Calibrating delay using timer specific routine.. 1802.04 BogoMIPS (lpj=3604081)
Oct 22 17:50:47 Bluebox kernel: [   10.160381] Security Framework initialized
Oct 22 17:50:47 Bluebox kernel: [   10.160394] SELinux:  Disabled at boot.
Oct 22 17:50:47 Bluebox kernel: [   10.160424] AppArmor: AppArmor initialized
Oct 22 17:50:47 Bluebox kernel: [   10.160431] Failure registering capabilities with primary security module.
Oct 22 17:50:47 Bluebox kernel: [   10.160446] Mount-cache hash table entries: 512
Oct 22 17:50:47 Bluebox kernel: [   10.160669] Initializing cgroup subsys ns
Oct 22 17:50:47 Bluebox kernel: [   10.160680] Initializing cgroup subsys cpuacct
Oct 22 17:50:47 Bluebox kernel: [   10.160717] CPU: L1 I cache: 32K, L1 D cache: 32K
Oct 22 17:50:47 Bluebox kernel: [   10.160721] CPU: L2 cache: 512K
Oct 22 17:50:47 Bluebox kernel: [   10.160743] Compat vDSO mapped to ffffe000.
Oct 22 17:50:47 Bluebox kernel: [   10.160765] Checking 'hlt' instruction... OK.
Oct 22 17:50:47 Bluebox kernel: [   10.176893] SMP alternatives: switching to UP code
Oct 22 17:50:47 Bluebox kernel: [   10.180120] Freeing SMP alternatives: 11k freed
Oct 22 17:50:47 Bluebox kernel: [   10.180310] Early unpacking initramfs... done
Oct 22 17:50:47 Bluebox kernel: [   10.645014] ACPI: Core revision 20070126
Oct 22 17:50:47 Bluebox kernel: [   10.645135] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Oct 22 17:50:47 Bluebox kernel: [   10.791076] CPU0: Intel(R) Celeron(R) M processor          900MHz stepping 08
Oct 22 17:50:47 Bluebox kernel: [   10.791110] Total of 1 processors activated (1802.04 BogoMIPS).
Oct 22 17:50:47 Bluebox kernel: [   10.791270] ENABLING IO-APIC IRQs
Oct 22 17:50:47 Bluebox kernel: [   10.791467] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Oct 22 17:50:47 Bluebox kernel: [   10.936006] Brought up 1 CPUs
Oct 22 17:50:47 Bluebox kernel: [   10.936302] net_namespace: 64 bytes
Oct 22 17:50:47 Bluebox kernel: [   10.936322] Booting paravirtualized kernel on bare hardware
Oct 22 17:50:47 Bluebox kernel: [   10.937136] Time: 15:50:30  Date: 10/22/08
Oct 22 17:50:47 Bluebox kernel: [   10.937179] NET: Registered protocol family 16
Oct 22 17:50:47 Bluebox kernel: [   10.937511] ACPI: bus type pci registered
Oct 22 17:50:47 Bluebox kernel: [   10.937859] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=5
Oct 22 17:50:47 Bluebox kernel: [   10.937864] PCI: Using configuration type 1
Oct 22 17:50:47 Bluebox kernel: [   10.937898] Setting up standard PCI resources
Oct 22 17:50:47 Bluebox kernel: [   10.992984] ACPI: Interpreter enabled
Oct 22 17:50:47 Bluebox kernel: [   10.992990] ACPI: (supports S0 S1 S3 S4 S5)
Oct 22 17:50:47 Bluebox kernel: [   10.993021] ACPI: Using IOAPIC for interrupt routing
Oct 22 17:50:47 Bluebox kernel: [   11.004490] ACPI: EC: GPE = 0x18, I/O: command/status = 0x66, data = 0x62
Oct 22 17:50:47 Bluebox kernel: [   11.004497] ACPI: EC: driver started in poll mode
Oct 22 17:50:47 Bluebox kernel: [   11.004721] ACPI: PCI Root Bridge [PCI0] (0000:00)
Oct 22 17:50:47 Bluebox kernel: [   11.005483] PCI quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO
Oct 22 17:50:47 Bluebox kernel: [   11.005489] PCI quirk: region 0480-04bf claimed by ICH6 GPIO
Oct 22 17:50:47 Bluebox kernel: [   11.006089] PCI: Transparent bridge - 0000:00:1e.0
Oct 22 17:50:47 Bluebox kernel: [   11.014169] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 6 7 10 11 12 14 15)
Oct 22 17:50:47 Bluebox kernel: [   11.014414] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 *11 12 14 15)
Oct 22 17:50:47 Bluebox kernel: [   11.014665] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *10 11 12 14 15)
Oct 22 17:50:47 Bluebox kernel: [   11.014904] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 *7 10 11 12 14 15)
Oct 22 17:50:47 Bluebox kernel: [   11.015144] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
Oct 22 17:50:47 Bluebox kernel: [   11.015384] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
Oct 22 17:50:47 Bluebox kernel: [   11.015625] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
Oct 22 17:50:47 Bluebox kernel: [   11.015865] ACPI: PCI Interrupt Link [LNKH] (IRQs *3 4 5 6 7 10 11 12 14 15)
Oct 22 17:50:47 Bluebox kernel: [   11.016227] Linux Plug and Play Support v0.97 (c) Adam Belay
Oct 22 17:50:47 Bluebox kernel: [   11.016290] pnp: PnP ACPI init
Oct 22 17:50:47 Bluebox kernel: [   11.016305] ACPI: bus type pnp registered
Oct 22 17:50:47 Bluebox kernel: [   11.019877] pnp: PnP ACPI: found 13 devices
Oct 22 17:50:47 Bluebox kernel: [   11.019882] ACPI: ACPI bus type pnp unregistered
Oct 22 17:50:47 Bluebox kernel: [   11.020321] PCI: Using ACPI for IRQ routing
Oct 22 17:50:47 Bluebox kernel: [   11.020327] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Oct 22 17:50:47 Bluebox kernel: [   11.043892] NET: Registered protocol family 8
Oct 22 17:50:47 Bluebox kernel: [   11.043896] NET: Registered protocol family 20
Oct 22 17:50:47 Bluebox kernel: [   11.044202] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
Oct 22 17:50:47 Bluebox kernel: [   11.044209] hpet0: 3 64-bit timers, 14318180 Hz
Oct 22 17:50:47 Bluebox kernel: [   11.045275] AppArmor: AppArmor Filesystem Enabled
Oct 22 17:50:47 Bluebox kernel: [   11.047879] Time: tsc clocksource has been installed.
Oct 22 17:50:47 Bluebox kernel: [   11.055949] system 00:01: iomem range 0xfed13000-0xfed19fff has been reserved
Oct 22 17:50:47 Bluebox kernel: [   11.055969] system 00:08: ioport range 0x380-0x383 has been reserved
Oct 22 17:50:47 Bluebox kernel: [   11.055974] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
Oct 22 17:50:47 Bluebox kernel: [   11.055979] system 00:08: ioport range 0x800-0x87f has been reserved
Oct 22 17:50:47 Bluebox kernel: [   11.055985] system 00:08: ioport range 0x480-0x4bf has been reserved
Oct 22 17:50:47 Bluebox kernel: [   11.055990] system 00:08: iomem range 0xfed1c000-0xfed1ffff has been reserved
Oct 22 17:50:47 Bluebox kernel: [   11.055996] system 00:08: iomem range 0xfed20000-0xfed8ffff has been reserved
Oct 22 17:50:47 Bluebox kernel: [   11.056002] system 00:08: iomem range 0xfff00000-0xffffffff could not be reserved
Oct 22 17:50:47 Bluebox kernel: [   11.056012] system 00:09: iomem range 0xfec00000-0xfec00fff has been reserved
Oct 22 17:50:47 Bluebox kernel: [   11.056018] system 00:09: iomem range 0xfee00000-0xfee00fff could not be reserved
Oct 22 17:50:47 Bluebox kernel: [   11.056028] system 00:0a: iomem range 0xe0000000-0xefffffff has been reserved
Oct 22 17:50:47 Bluebox kernel: [   11.056038] system 00:0b: iomem range 0xe0000000-0xefffffff has been reserved
Oct 22 17:50:47 Bluebox kernel: [   11.056050] system 00:0c: iomem range 0x0-0x9ffff could not be reserved
Oct 22 17:50:47 Bluebox kernel: [   11.056056] system 00:0c: iomem range 0x0-0x0 could not be reserved
Oct 22 17:50:47 Bluebox kernel: [   11.056061] system 00:0c: iomem range 0xe0000-0xfffff could not be reserved
Oct 22 17:50:47 Bluebox kernel: [   11.056067] system 00:0c: iomem range 0x100000-0x3f7fffff could not be reserved
Oct 22 17:50:47 Bluebox kernel: [   11.056072] system 00:0c: iomem range 0x0-0x0 could not be reserved
Oct 22 17:50:47 Bluebox kernel: [   11.086813] PCI: Bridge: 0000:00:1c.0
Oct 22 17:50:47 Bluebox kernel: [   11.086816]   IO window: disabled.
Oct 22 17:50:47 Bluebox kernel: [   11.086823]   MEM window: disabled.
Oct 22 17:50:47 Bluebox kernel: [   11.086828]   PREFETCH window: disabled.
Oct 22 17:50:47 Bluebox kernel: [   11.086834] PCI: Bridge: 0000:00:1c.1
Oct 22 17:50:47 Bluebox kernel: [   11.086836]   IO window: disabled.
Oct 22 17:50:47 Bluebox kernel: [   11.086843]   MEM window: fbf00000-fbffffff
Oct 22 17:50:47 Bluebox kernel: [   11.086848]   PREFETCH window: disabled.
Oct 22 17:50:47 Bluebox kernel: [   11.086854] PCI: Bridge: 0000:00:1c.2
Oct 22 17:50:47 Bluebox kernel: [   11.086856]   IO window: disabled.
Oct 22 17:50:47 Bluebox kernel: [   11.086862]   MEM window: f8000000-fbefffff
Oct 22 17:50:47 Bluebox kernel: [   11.086868]   PREFETCH window: f0000000-f6ffffff
Oct 22 17:50:47 Bluebox kernel: [   11.086874] PCI: Bridge: 0000:00:1e.0
Oct 22 17:50:47 Bluebox kernel: [   11.086876]   IO window: disabled.
Oct 22 17:50:47 Bluebox kernel: [   11.086882]   MEM window: disabled.
Oct 22 17:50:47 Bluebox kernel: [   11.086887]   PREFETCH window: disabled.
Oct 22 17:50:47 Bluebox kernel: [   11.086923] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
Oct 22 17:50:47 Bluebox kernel: [   11.086956] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 17 (level, low) -> IRQ 17
Oct 22 17:50:47 Bluebox kernel: [   11.086985] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 18
Oct 22 17:50:47 Bluebox kernel: [   11.087027] NET: Registered protocol family 2
Oct 22 17:50:47 Bluebox kernel: [   11.123934] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Oct 22 17:50:47 Bluebox kernel: [   11.124348] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Oct 22 17:50:47 Bluebox kernel: [   11.126021] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Oct 22 17:50:47 Bluebox kernel: [   11.126809] TCP: Hash tables configured (established 131072 bind 65536)
Oct 22 17:50:47 Bluebox kernel: [   11.126815] TCP reno registered
Oct 22 17:50:47 Bluebox kernel: [   11.136103] Unpacking initramfs...<7>Switched to high resolution mode on CPU 0
Oct 22 17:50:47 Bluebox kernel: [   11.601468]  done
Oct 22 17:50:47 Bluebox kernel: [   11.607387] Freeing initrd memory: 4987k freed
Oct 22 17:50:47 Bluebox kernel: [   11.608361] audit: initializing netlink socket (disabled)
Oct 22 17:50:47 Bluebox kernel: [   11.608385] audit(1224690630.256:1): initialized
Oct 22 17:50:47 Bluebox kernel: [   11.608652] highmem bounce pool size: 64 pages
Oct 22 17:50:47 Bluebox kernel: [   11.612169] VFS: Disk quotas dquot_6.5.1
Oct 22 17:50:47 Bluebox kernel: [   11.612312] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Oct 22 17:50:47 Bluebox kernel: [   11.612549] io scheduler noop registered
Oct 22 17:50:47 Bluebox kernel: [   11.612553] io scheduler anticipatory registered
Oct 22 17:50:47 Bluebox kernel: [   11.612557] io scheduler deadline registered
Oct 22 17:50:47 Bluebox kernel: [   11.612580] io scheduler cfq registered (default)
Oct 22 17:50:47 Bluebox kernel: [   11.612909] assign_interrupt_mode Found MSI capability
Oct 22 17:50:47 Bluebox kernel: [   11.613142] assign_interrupt_mode Found MSI capability
Oct 22 17:50:47 Bluebox kernel: [   11.613367] assign_interrupt_mode Found MSI capability
Oct 22 17:50:47 Bluebox kernel: [   11.684081] Real Time Clock Driver v1.12ac
Oct 22 17:50:47 Bluebox kernel: [   11.684247] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Oct 22 17:50:47 Bluebox kernel: [   11.685577] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Oct 22 17:50:47 Bluebox kernel: [   11.718279] serio: i8042 KBD port at 0x60,0x64 irq 1
Oct 22 17:50:47 Bluebox kernel: [   11.718287] serio: i8042 AUX port at 0x60,0x64 irq 12
Oct 22 17:50:47 Bluebox kernel: [   11.718537] mice: PS/2 mouse device common for all mice
Oct 22 17:50:47 Bluebox kernel: [   11.718633] cpuidle: using governor ladder
Oct 22 17:50:47 Bluebox kernel: [   11.718637] cpuidle: using governor menu
Oct 22 17:50:47 Bluebox kernel: [   11.718780] NET: Registered protocol family 1
Oct 22 17:50:47 Bluebox kernel: [   11.718827] Using IPI No-Shortcut mode
Oct 22 17:50:47 Bluebox kernel: [   11.718874] registered taskstats version 1
Oct 22 17:50:47 Bluebox kernel: [   11.719022]   Magic number: 12:57:842
Oct 22 17:50:47 Bluebox kernel: [   11.719124]   hash matches device ptyu8
Oct 22 17:50:47 Bluebox kernel: [   11.719136]   hash matches device ptyrb
Oct 22 17:50:47 Bluebox kernel: [   11.719192] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Oct 22 17:50:47 Bluebox kernel: [   11.719195] EDD information not available.
Oct 22 17:50:47 Bluebox kernel: [   11.719371] Freeing unused kernel memory: 264k freed
Oct 22 17:50:47 Bluebox kernel: [   11.751487] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input0
Oct 22 17:50:47 Bluebox kernel: [   13.072245] fuse init (API version 7.9)
Oct 22 17:50:47 Bluebox kernel: [   13.091239] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
Oct 22 17:50:47 Bluebox kernel: [   13.091250] ACPI: Processor [CPU1] (supports 8 throttling states)
Oct 22 17:50:47 Bluebox kernel: [   13.096000] ACPI: EC: non-query interrupt received, switching to interrupt mode
Oct 22 17:50:47 Bluebox kernel: [   13.097343] Marking TSC unstable due to: TSC halts in idle.
Oct 22 17:50:47 Bluebox kernel: [   13.098650] Time: hpet clocksource has been installed.
Oct 22 17:50:47 Bluebox kernel: [   13.099302] ACPI: Thermal Zone [TZ00] (42 C)
Oct 22 17:50:47 Bluebox kernel: [   13.798220] usbcore: registered new interface driver usbfs
Oct 22 17:50:47 Bluebox kernel: [   13.798259] usbcore: registered new interface driver hub
Oct 22 17:50:47 Bluebox kernel: [   13.804862] usbcore: registered new device driver usb
Oct 22 17:50:47 Bluebox kernel: [   13.821744] USB Universal Host Controller Interface driver v3.0
Oct 22 17:50:47 Bluebox kernel: [   13.821836] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 19
Oct 22 17:50:47 Bluebox kernel: [   13.821859] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Oct 22 17:50:47 Bluebox kernel: [   13.822271] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
Oct 22 17:50:47 Bluebox kernel: [   13.822310] uhci_hcd 0000:00:1d.0: irq 19, io base 0x0000e400
Oct 22 17:50:47 Bluebox kernel: [   13.822535] usb usb1: configuration #1 chosen from 1 choice
Oct 22 17:50:47 Bluebox kernel: [   13.822575] hub 1-0:1.0: USB hub found
Oct 22 17:50:47 Bluebox kernel: [   13.822585] hub 1-0:1.0: 2 ports detected
Oct 22 17:50:47 Bluebox kernel: [   13.907584] SCSI subsystem initialized
Oct 22 17:50:47 Bluebox kernel: [   13.924053] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 20
Oct 22 17:50:47 Bluebox kernel: [   13.924079] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Oct 22 17:50:47 Bluebox kernel: [   13.924126] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
Oct 22 17:50:47 Bluebox kernel: [   13.924162] uhci_hcd 0000:00:1d.1: irq 20, io base 0x0000e480
Oct 22 17:50:47 Bluebox kernel: [   13.924357] usb usb2: configuration #1 chosen from 1 choice
Oct 22 17:50:47 Bluebox kernel: [   13.924397] hub 2-0:1.0: USB hub found
Oct 22 17:50:47 Bluebox kernel: [   13.924407] hub 2-0:1.0: 2 ports detected
Oct 22 17:50:47 Bluebox kernel: [   14.027954] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
Oct 22 17:50:47 Bluebox kernel: [   14.027980] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Oct 22 17:50:47 Bluebox kernel: [   14.028021] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
Oct 22 17:50:47 Bluebox kernel: [   14.028058] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000e800
Oct 22 17:50:47 Bluebox kernel: [   14.028250] usb usb3: configuration #1 chosen from 1 choice
Oct 22 17:50:47 Bluebox kernel: [   14.028292] hub 3-0:1.0: USB hub found
Oct 22 17:50:47 Bluebox kernel: [   14.028302] hub 3-0:1.0: 2 ports detected
Oct 22 17:50:47 Bluebox kernel: [   14.131933] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 16
Oct 22 17:50:47 Bluebox kernel: [   14.131957] uhci_hcd 0000:00:1d.3: UHCI Host Controller
Oct 22 17:50:47 Bluebox kernel: [   14.131998] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
Oct 22 17:50:47 Bluebox kernel: [   14.132033] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000e880
Oct 22 17:50:47 Bluebox kernel: [   14.132225] usb usb4: configuration #1 chosen from 1 choice
Oct 22 17:50:47 Bluebox kernel: [   14.132265] hub 4-0:1.0: USB hub found
Oct 22 17:50:47 Bluebox kernel: [   14.132275] hub 4-0:1.0: 2 ports detected
Oct 22 17:50:47 Bluebox kernel: [   14.236058] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 19
Oct 22 17:50:47 Bluebox kernel: [   14.236084] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Oct 22 17:50:47 Bluebox kernel: [   14.236131] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
Oct 22 17:50:47 Bluebox kernel: [   14.240041] ehci_hcd 0000:00:1d.7: debug port 1
Oct 22 17:50:47 Bluebox kernel: [   14.240060] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xf7eb7c00
Oct 22 17:50:47 Bluebox kernel: [   14.255694] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Oct 22 17:50:47 Bluebox kernel: [   14.255908] usb usb5: configuration #1 chosen from 1 choice
Oct 22 17:50:47 Bluebox kernel: [   14.255950] hub 5-0:1.0: USB hub found
Oct 22 17:50:47 Bluebox kernel: [   14.255961] hub 5-0:1.0: 8 ports detected
Oct 22 17:50:47 Bluebox kernel: [   14.359894] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
Oct 22 17:50:47 Bluebox kernel: [   14.359935] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 20
Oct 22 17:50:47 Bluebox kernel: [   14.362161] scsi0 : ata_piix
Oct 22 17:50:47 Bluebox kernel: [   14.363378] scsi1 : ata_piix
Oct 22 17:50:47 Bluebox kernel: [   14.365809] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
Oct 22 17:50:47 Bluebox kernel: [   14.365815] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
Oct 22 17:50:47 Bluebox kernel: [   14.627452] usb 5-5: new high speed USB device using ehci_hcd and address 2
Oct 22 17:50:47 Bluebox kernel: [   14.699772] ata2.00: ATA-5: ASUS-PHISON SSD, TST2.04P, max UDMA/66
Oct 22 17:50:47 Bluebox kernel: [   14.699780] ata2.00: 31522176 sectors, multi 0: LBA 
Oct 22 17:50:47 Bluebox kernel: [   14.707750] ata2.00: configured for UDMA/66
Oct 22 17:50:47 Bluebox kernel: [   14.707968] scsi 1:0:0:0: Direct-Access     ATA      ASUS-PHISON SSD  TST2 PQ: 0 ANSI: 5
Oct 22 17:50:47 Bluebox kernel: [   14.760711] usb 5-5: configuration #1 chosen from 1 choice
Oct 22 17:50:47 Bluebox kernel: [   14.919161] Driver 'sd' needs updating - please use bus_type methods
Oct 22 17:50:47 Bluebox kernel: [   14.919312] sd 1:0:0:0: [sda] 31522176 512-byte hardware sectors (16139 MB)
Oct 22 17:50:47 Bluebox kernel: [   14.919333] sd 1:0:0:0: [sda] Write Protect is off
Oct 22 17:50:47 Bluebox kernel: [   14.919367] sd 1:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
Oct 22 17:50:47 Bluebox kernel: [   14.919441] sd 1:0:0:0: [sda] 31522176 512-byte hardware sectors (16139 MB)
Oct 22 17:50:47 Bluebox kernel: [   14.919458] sd 1:0:0:0: [sda] Write Protect is off
Oct 22 17:50:47 Bluebox kernel: [   14.919489] sd 1:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
Oct 22 17:50:47 Bluebox kernel: [   14.919496]  sda: sda1 sda2 < sda5 >
Oct 22 17:50:47 Bluebox kernel: [   14.921849] sd 1:0:0:0: [sda] Attached SCSI disk
Oct 22 17:50:47 Bluebox kernel: [   14.932147] sd 1:0:0:0: Attached scsi generic sg0 type 0
Oct 22 17:50:47 Bluebox kernel: [   14.959165] usbcore: registered new interface driver libusual
Oct 22 17:50:47 Bluebox kernel: [   14.971054] Initializing USB Mass Storage driver...
Oct 22 17:50:47 Bluebox kernel: [   14.973576] scsi2 : SCSI emulation for USB Mass Storage devices
Oct 22 17:50:47 Bluebox kernel: [   14.974202] usbcore: registered new interface driver usb-storage
Oct 22 17:50:47 Bluebox kernel: [   14.974210] USB Mass Storage support registered.
Oct 22 17:50:47 Bluebox kernel: [   15.083662] Attempting manual resume
Oct 22 17:50:47 Bluebox kernel: [   15.109114] kjournald starting.  Commit interval 5 seconds
Oct 22 17:50:47 Bluebox kernel: [   15.109136] EXT3-fs: mounted filesystem with ordered data mode.
Oct 22 17:50:47 Bluebox kernel: [   15.328074] Clocksource tsc unstable (delta = -199680276 ns)
Oct 22 17:50:47 Bluebox kernel: [   17.092128] asus_eee module requires i2c-i801 module at load time if you like to access pll via proc too
Oct 22 17:50:47 Bluebox kernel: [   17.092145] asus_eee version 0.3 init sucessfully
Oct 22 17:50:47 Bluebox kernel: [   17.431434] Linux agpgart interface v0.102
Oct 22 17:50:47 Bluebox kernel: [   17.569119] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Oct 22 17:50:47 Bluebox kernel: [   17.620401] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Oct 22 17:50:47 Bluebox kernel: [   17.663759] agpgart: Detected an Intel 915GM Chipset.
Oct 22 17:50:47 Bluebox kernel: [   17.664001] agpgart: Detected 7932K stolen memory.
Oct 22 17:50:47 Bluebox kernel: [   17.684826] agpgart: AGP aperture is 256M @ 0xd0000000
Oct 22 17:50:47 Bluebox kernel: [   17.719877] input: Power Button (FF) as /devices/virtual/input/input1
Oct 22 17:50:47 Bluebox kernel: [   17.733307] ACPI: Power Button (FF) [PWRF]
Oct 22 17:50:47 Bluebox kernel: [   17.733546] input: Lid Switch as /devices/virtual/input/input2
Oct 22 17:50:47 Bluebox kernel: [   17.740783] ACPI: Lid Switch [LID]
Oct 22 17:50:47 Bluebox kernel: [   17.740981] input: Sleep Button (CM) as /devices/virtual/input/input3
Oct 22 17:50:47 Bluebox kernel: [   17.755571] ACPI: Sleep Button (CM) [SLPB]
Oct 22 17:50:47 Bluebox kernel: [   17.755718] input: Power Button (CM) as /devices/virtual/input/input4
Oct 22 17:50:47 Bluebox kernel: [   17.767561] ACPI: Power Button (CM) [PWRB]
Oct 22 17:50:47 Bluebox kernel: [   17.831698] Asus EeePC Hotkey Driver
Oct 22 17:50:47 Bluebox kernel: [   17.831928] [eeepc hotk] Hotkey init flags 0x41.
Oct 22 17:50:47 Bluebox kernel: [   17.833095] [eeepc hotk] Get control methods supported: 0x101711
Oct 22 17:50:47 Bluebox kernel: [   19.091270] scsi 2:0:0:0: Direct-Access     USB2.0   CardReader SD0   0100 PQ: 0 ANSI: 0
Oct 22 17:50:47 Bluebox kernel: [   19.092944] sd 2:0:0:0: [sdb] Attached SCSI removable disk
Oct 22 17:50:47 Bluebox kernel: [   19.093010] sd 2:0:0:0: Attached scsi generic sg1 type 0
Oct 22 17:50:47 Bluebox kernel: [   19.207604] ACPI: AC Adapter [AC0] (off-line)
Oct 22 17:50:47 Bluebox kernel: [   19.375273] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input5
Oct 22 17:50:47 Bluebox kernel: [   19.386543] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
Oct 22 17:50:47 Bluebox kernel: [   20.123800] Atheros(R) L2 Ethernet Driver - version 2.0.5
Oct 22 17:50:47 Bluebox kernel: [   20.123807] Copyright (c) 2007 Atheros Corporation.
Oct 22 17:50:47 Bluebox kernel: [   20.124605] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 17
Oct 22 17:50:47 Bluebox kernel: [   20.196419] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 16 (level, low) -> IRQ 16
Oct 22 17:50:47 Bluebox kernel: [   20.219846] hda_codec: Unknown model for ALC662, trying auto-probe from BIOS...
Oct 22 17:50:47 Bluebox kernel: [   20.689736] iTCO_vendor_support: vendor-support=0
Oct 22 17:50:47 Bluebox kernel: [   20.737703] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
Oct 22 17:50:47 Bluebox kernel: [   20.737915] iTCO_wdt: Found a ICH6-M TCO device (Version=2, TCOBASE=0x0860)
Oct 22 17:50:47 Bluebox kernel: [   20.737992] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
Oct 22 17:50:47 Bluebox kernel: [   21.494302] input: PC Speaker as /devices/platform/pcspkr/input/input6
Oct 22 17:50:47 Bluebox kernel: [   22.290313] ACPI: Battery Slot [BAT0] (battery present)
Oct 22 17:50:47 Bluebox kernel: [   23.726886] input: ImPS/2 Logitech Wheel Mouse as /devices/platform/i8042/serio1/input/input7
Oct 22 17:50:47 Bluebox kernel: [   24.908592] lp: driver loaded but no devices found
Oct 22 17:50:47 Bluebox kernel: [   24.930032] ath_hal: module license 'Proprietary' taints kernel.
Oct 22 17:50:47 Bluebox kernel: [   24.940453] AR5210, AR5211, AR5212, AR5416, RF5111, RF5112, RF2413, RF5413, RF2133, RF2425, RF2417)
Oct 22 17:50:47 Bluebox kernel: [   25.112375] pciehp: pcie_init: hotplug controller vendor id 0x8086 device id 0x2660
Oct 22 17:50:47 Bluebox kernel: [   25.112389] pciehp: pcie_init: pcie_cap_base 40
Oct 22 17:50:47 Bluebox kernel: [   25.112394] pciehp: pcie_init: CAPREG offset 42 cap_reg 141
Oct 22 17:50:47 Bluebox kernel: [   25.112400] pciehp: pcie_init: SLOTCAP offset 54 slot_cap 80560
Oct 22 17:50:47 Bluebox kernel: [   25.112405] pciehp: pcie_init: SLOTSTATUS offset 5a slot_status 0
Oct 22 17:50:47 Bluebox kernel: [   25.112410] pciehp: pcie_init: SLOTCTRL offset 58 slot_ctrl 0
Oct 22 17:50:47 Bluebox kernel: [   25.112415] pciehp: HPC vendor_id 8086 device_id 2660 ss_vid 0 ss_did 0
Oct 22 17:50:47 Bluebox kernel: [   25.112421] pciehp: pcie_init: SLOTCTRL 58 value read 0
Oct 22 17:50:47 Bluebox kernel: [   25.112437] pciehp: pcie_init: request_irq 16 for hpc0 (returns 0)
Oct 22 17:50:47 Bluebox kernel: [   25.112441] pciehp: pciehp ctrl b:d:f:irq=0x0:1c:0:10
Oct 22 17:50:47 Bluebox kernel: [   25.113866] pciehp: Bypassing BIOS check for pciehp use on 0000:00:1c.0
Oct 22 17:50:47 Bluebox kernel: [   25.113876] pciehp: pciehp_probe: ctrl bus=0x0, device=1c, function=0, irq=10
Oct 22 17:50:47 Bluebox kernel: [   25.113883] pciehp: get_power_status - physical_slot = 0004_0001
Oct 22 17:50:47 Bluebox kernel: [   25.113889] pciehp: hpc_get_power_status: SLOTCTRL 58 value read 28
Oct 22 17:50:47 Bluebox kernel: [   25.113894] pciehp: get_attention_status - physical_slot = 0004_0001
Oct 22 17:50:47 Bluebox kernel: [   25.113899] pciehp: hpc_get_attention_status: SLOTCTRL 58, value read 28
Oct 22 17:50:47 Bluebox kernel: [   25.113904] pciehp: get_latch_status - physical_slot = 0004_0001
Oct 22 17:50:47 Bluebox kernel: [   25.113909] pciehp: get_adapter_status - physical_slot = 0004_0001
Oct 22 17:50:47 Bluebox kernel: [   25.113915] pciehp: Registering bus=4 dev=0 hp_slot=0 sun=1 slot_device_offset=0
Oct 22 17:50:47 Bluebox kernel: [   25.113973] pciehp: pcie_init: hotplug controller vendor id 0x8086 device id 0x2662
Oct 22 17:50:47 Bluebox kernel: [   25.113982] pciehp: pcie_init: pcie_cap_base 40
Oct 22 17:50:47 Bluebox kernel: [   25.113987] pciehp: pcie_init: CAPREG offset 42 cap_reg 141
Oct 22 17:50:47 Bluebox kernel: [   25.113992] pciehp: pcie_init: SLOTCAP offset 54 slot_cap 100560
Oct 22 17:50:47 Bluebox kernel: [   25.113998] pciehp: pcie_init: SLOTSTATUS offset 5a slot_status 48
Oct 22 17:50:47 Bluebox kernel: [   25.114003] pciehp: pcie_init: SLOTCTRL offset 58 slot_ctrl 0
Oct 22 17:50:47 Bluebox kernel: [   25.114008] pciehp: pci resource[8] start=0xfbf00000(len=0x100000)
Oct 22 17:50:47 Bluebox kernel: [   25.114013] pciehp: HPC vendor_id 8086 device_id 2662 ss_vid 0 ss_did 0
Oct 22 17:50:47 Bluebox kernel: [   25.114018] pciehp: pcie_init: SLOTCTRL 58 value read 0
Oct 22 17:50:47 Bluebox kernel: [   25.114037] pciehp: pcie_init: request_irq 17 for hpc1 (returns 0)
Oct 22 17:50:47 Bluebox kernel: [   25.114042] pciehp: pciehp ctrl b:d:f:irq=0x0:1c:1:11
Oct 22 17:50:47 Bluebox kernel: [   25.114050] pciehp: Bypassing BIOS check for pciehp use on 0000:00:1c.1
Oct 22 17:50:47 Bluebox kernel: [   25.114055] pciehp: pciehp_probe: ctrl bus=0x0, device=1c, function=1, irq=11
Oct 22 17:50:47 Bluebox kernel: [   25.114061] pciehp: get_power_status - physical_slot = 0003_0002
Oct 22 17:50:47 Bluebox kernel: [   25.114066] pciehp: hpc_get_power_status: SLOTCTRL 58 value read 28
Oct 22 17:50:47 Bluebox kernel: [   25.114070] pciehp: get_attention_status - physical_slot = 0003_0002
Oct 22 17:50:47 Bluebox kernel: [   25.114076] pciehp: hpc_get_attention_status: SLOTCTRL 58, value read 28
Oct 22 17:50:47 Bluebox kernel: [   25.114080] pciehp: get_latch_status - physical_slot = 0003_0002
Oct 22 17:50:47 Bluebox kernel: [   25.114085] pciehp: get_adapter_status - physical_slot = 0003_0002
Oct 22 17:50:47 Bluebox kernel: [   25.114091] pciehp: Registering bus=3 dev=0 hp_slot=0 sun=2 slot_device_offset=0
Oct 22 17:50:47 Bluebox kernel: [   25.114128] pciehp: pcie_init: hotplug controller vendor id 0x8086 device id 0x2664
Oct 22 17:50:47 Bluebox kernel: [   25.114135] pciehp: pcie_init: pcie_cap_base 40
Oct 22 17:50:47 Bluebox kernel: [   25.114140] pciehp: pcie_init: CAPREG offset 42 cap_reg 141
Oct 22 17:50:47 Bluebox kernel: [   25.114145] pciehp: pcie_init: SLOTCAP offset 54 slot_cap 180560
Oct 22 17:50:47 Bluebox kernel: [   25.114151] pciehp: pcie_init: SLOTSTATUS offset 5a slot_status 8
Oct 22 17:50:47 Bluebox kernel: [   25.114156] pciehp: pcie_init: SLOTCTRL offset 58 slot_ctrl 0
Oct 22 17:50:47 Bluebox kernel: [   25.114161] pciehp: pci resource[8] start=0xf8000000(len=0x3f00000)
Oct 22 17:50:47 Bluebox kernel: [   25.114166] pciehp: pci resource[9] start=0xf0000000(len=0x7000000)
Oct 22 17:50:47 Bluebox kernel: [   25.114170] pciehp: HPC vendor_id 8086 device_id 2664 ss_vid 0 ss_did 0
Oct 22 17:50:47 Bluebox kernel: [   25.114176] pciehp: pcie_init: SLOTCTRL 58 value read 0
Oct 22 17:50:47 Bluebox kernel: [   25.114185] pciehp: pcie_init: request_irq 18 for hpc2 (returns 0)
Oct 22 17:50:47 Bluebox kernel: [   25.114190] pciehp: pciehp ctrl b:d:f:irq=0x0:1c:2:12
Oct 22 17:50:47 Bluebox kernel: [   25.114198] pciehp: Bypassing BIOS check for pciehp use on 0000:00:1c.2
Oct 22 17:50:47 Bluebox kernel: [   25.114203] pciehp: pciehp_probe: ctrl bus=0x0, device=1c, function=2, irq=12
Oct 22 17:50:47 Bluebox kernel: [   25.114209] pciehp: get_power_status - physical_slot = 0001_0003
Oct 22 17:50:47 Bluebox kernel: [   25.114214] pciehp: hpc_get_power_status: SLOTCTRL 58 value read 28
Oct 22 17:50:47 Bluebox kernel: [   25.114218] pciehp: get_attention_status - physical_slot = 0001_0003
Oct 22 17:50:47 Bluebox kernel: [   25.114224] pciehp: hpc_get_attention_status: SLOTCTRL 58, value read 28
Oct 22 17:50:47 Bluebox kernel: [   25.114228] pciehp: get_latch_status - physical_slot = 0001_0003
Oct 22 17:50:47 Bluebox kernel: [   25.114233] pciehp: get_adapter_status - physical_slot = 0001_0003
Oct 22 17:50:47 Bluebox kernel: [   25.114239] pciehp: Registering bus=1 dev=0 hp_slot=0 sun=3 slot_device_offset=0
Oct 22 17:50:47 Bluebox kernel: [   25.114273] pciehp: pcie_port_service_register = 0
Oct 22 17:50:47 Bluebox kernel: [   25.114277] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Oct 22 17:50:47 Bluebox kernel: [   25.213260] p4-clockmod: P4/Xeon(TM) CPU On-Demand Clock Modulation available
Oct 22 17:50:47 Bluebox kernel: [   25.281336] Adding 706820k swap on /dev/sda5.  Priority:-1 extents:1 across:706820k
Oct 22 17:50:47 Bluebox kernel: [   25.319666] EXT3 FS on sda1, internal journal
Oct 22 17:50:47 Bluebox kernel: [   25.995142] ip_tables: (C) 2000-2006 Netfilter Core Team
Oct 22 17:50:47 Bluebox kernel: [   26.535575] No dock devices found.
Oct 22 17:50:48 Bluebox kernel: [   27.889942] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
Oct 22 17:50:48 Bluebox kernel: [   27.889950] apm: overridden by ACPI.
Oct 22 17:50:48 Bluebox kernel: [   28.007340] ppdev: user-space parallel port driver
Oct 22 17:50:48 Bluebox kernel: [   28.040423] audit(1224690648.469:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4618 profile="/usr/sbin/cupsd" namespace="default"
Oct 22 17:50:48 Bluebox dhcdbd: Started up.
Oct 22 17:50:48 Bluebox kernel: [   28.412921] Bluetooth: Core ver 2.11
Oct 22 17:50:48 Bluebox kernel: [   28.413763] NET: Registered protocol family 31
Oct 22 17:50:48 Bluebox kernel: [   28.413770] Bluetooth: HCI device and connection manager initialized
Oct 22 17:50:48 Bluebox kernel: [   28.413777] Bluetooth: HCI socket layer initialized
Oct 22 17:50:48 Bluebox kernel: [   28.450067] Bluetooth: L2CAP ver 2.9
Oct 22 17:50:48 Bluebox kernel: [   28.450075] Bluetooth: L2CAP socket layer initialized
Oct 22 17:50:49 Bluebox kernel: [   28.526214] Bluetooth: RFCOMM socket layer initialized
Oct 22 17:50:49 Bluebox kernel: [   28.526548] Bluetooth: RFCOMM TTY layer initialized
Oct 22 17:50:49 Bluebox kernel: [   28.526557] Bluetooth: RFCOMM ver 1.8
Oct 22 17:50:56 Bluebox kernel: [   31.594952] [drm] Initialized drm 1.1.0 20060810
Oct 22 17:50:57 Bluebox kernel: [   31.616646] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
Oct 22 17:50:57 Bluebox kernel: [   31.616790] [drm] Initialized i915 1.6.0 20060119 on minor 0

```

And a recap of what happens when i boot, from the moment i press the powerbutton:
The asus logo flashes by and grub prints a message and waits a few seconds for me to push esc in case i want to enter its menu.
If i dont it will dissapear and be replaced by loading... and then by 
Loading...
Starting, please wait...
(or something very close to it, memory might fail me).

The text changes slightly before the screen turns black (becomes bold, thinner and then dissapears).
At first it turns black, but i can see that the backlights are on. 
After that it turns inc black, as in the blackest it can get while turned off. 
Lastly it turns backlight-on black and shows the Ubuntu logo with a progress bar underneath.
The logo and progressbar disappears and the cursors shows up as a black X with white border. The cursor then changes to the loading-something circle and stays like that.

Even though i am free to do what i want with other virtual terminals, it wont show anything visual.

---

### Post by unutbu on 2008-10-23
Could it be that GDM has been set to autologin, and that for some reason GNOME fails to run after you've been logged in?

If you haven't reinstalled yet, perhaps try this:
```

sudo nano /etc/gdm/gdm.conf
```

Make sure that you have the lines
```

AutomaticLoginEnable=false
AutomaticLogin=
```
Save, exit, reboot. 
When you get to the GDM login window, press F10 and set your session type to 'GNOME'. Then try logging in again. If you see the black screen, try changing the session type to 'Failsafe GNOME'. Tell us what you see at this point and maybe we'll know how to fix things.

---

### Post by timjohn7 on 2008-10-23
I used to have this problem and solved it by adding vga=791 to the kernel line in the Grub entry.

---

