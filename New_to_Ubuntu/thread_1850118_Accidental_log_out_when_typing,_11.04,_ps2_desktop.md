---
title: "Accidental log out when typing, 11.04, ps2 desktop"
date: 2011-09-25
forum: New to Ubuntu
---

### Post by raequin on 2011-09-25
I have happily used Ubuntu on a laptop for years.  I recently installed it on an older desktop computer.  One very annoying thing has happened on this computer.  Several times when I'm typing x-windows has restarted --- I guess.  It has logged me off anyway, so I guess that means x has restarted.  I have no idea what keyboard combination is responsible.  Can you suggest some possibilities and a way I can disable it or avoid this behavior in the future?  Thanks.

ps --- It's a ps2 keyboard . . .  Also, I'm sure that I did not press any of these key combos, which reportedly restart X:

Alt+Sys Rq+K

Ctrl+Alt+Backspace

Alt+F7

pps --- This is my only install with 11.04, maybe that's pertinent.

---

### Post by raequin on 2011-09-27
I guess this is not very interesting to anyone, but I would surely appreciate a response since logging out discards all my current work.  Thanks.

---

### Post by MartyBuntu on 2011-09-27
If simply typing on your keyboard restarts your computer, you may have a more serious hardware failure at hand.

Can you plug in a different keyboard to test?

---

### Post by 2F4U on 2011-09-27
You should first rule out that X crashed. Look into your home folder and search for a file named ".xsession-errors" and see if it has any hints that point to a crash. Then look into /var/log/Xorg.0.log and see if that file has error messages in it. Do that immediately after you have been logged out because else these files may be overwritten with new content.

---

### Post by raequin on 2011-09-29
All right, thanks for the feedback.  The problem did not occur again for a few days.  It just did it though, and here's what's in ".xsession-errors".

```
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
GNOME_KEYRING_CONTROL=/tmp/keyring-wF8X5D
SSH_AUTH_SOCK=/tmp/keyring-wF8X5D/ssh
GNOME_KEYRING_CONTROL=/tmp/keyring-wF8X5D
SSH_AUTH_SOCK=/tmp/keyring-wF8X5D/ssh
GNOME_KEYRING_CONTROL=/tmp/keyring-wF8X5D
SSH_AUTH_SOCK=/tmp/keyring-wF8X5D/ssh
Backend     : gconf
Integration : true
Profile     : default
Adding plugins
Initializing core options...done
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Initializing composite options...done
Failed to play sound: File or data not found
Initializing opengl options...done
Initializing decor options...done
Initializing move options...done
Initializing resizeinfo options...done
Initializing place options...done
Initializing vpswitch options...done
Initializing neg options...done
Initializing imgjpeg options...done
Initializing imgsvg options...done
Initializing mousepoll options...done
Initializing grid options...done
Initializing animation options...done
Initializing switcher options...done
Initializing wall options...done
Initializing nautilus-gdu extension
Initializing fade options...done
Initializing scale options...
(nautilus:1982): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
done
Starting unity-window-decorator
** (nm-applet:1994): DEBUG: old state indicates that this was not a disconnect 0
Setting Update "window_toggle_key"
Setting Update "put_center_key"
Setting Update "put_left_key"
Setting Update "put_right_key"
Setting Update "put_top_key"
Setting Update "put_bottom_key"
Setting Update "put_topleft_key"
Setting Update "put_topright_key"
Setting Update "put_bottomleft_key"
Setting Update "put_bottomright_key"
Setting Update "put_maximize_key"
Setting Update "minimize_effects"
Setting Update "zoom"
Setting Update "fullscreen_visual_bell"
** (nm-applet:1994): DEBUG: foo_client_state_changed_cb
** (nm-applet:1994): DEBUG: foo_client_state_changed_cb

(Do:2014): Wnck-CRITICAL **: wnck_set_client_type got called multiple times.

[Error 14:53:39.910] [AbstractKeyBindingService] Failed to bind "Summon in Text Mode" to ""
Could not locate Tomboy on D-Bus. Perhaps it's not running?
Firefox.PlacesItemSource "Firefox Places" encountered an error in UpdateItems: System.InvalidCastException: Cannot cast from source type to destination type.
  at Mono.Data.Sqlite.SqliteDataReader.VerifyType (Int32 i, DbType typ) [0x00000] in <filename unknown>:0 
  at Mono.Data.Sqlite.SqliteDataReader.GetString (Int32 i) [0x00000] in <filename unknown>:0 
  at Firefox.PlacesItemSource+<LoadPlaceItems>c__Iterator3.MoveNext () [0x00000] in <filename unknown>:0 
  at System.Collections.Generic.List`1[Firefox.PlaceItem].AddEnumerable (IEnumerable`1 enumerable) [0x00000] in <filename unknown>:0 
  at System.Collections.Generic.List`1[Firefox.PlaceItem]..ctor (IEnumerable`1 collection) [0x00000] in <filename unknown>:0 
  at System.Linq.Enumerable.ToArray[PlaceItem] (IEnumerable`1 source) [0x00000] in <filename unknown>:0 
  at Firefox.PlacesItemSource.UpdateItems () [0x00000] in <filename unknown>:0 
  at Do.Universe.Safe.SafeItemSource.UpdateItems () [0x00000] in <filename unknown>:0 .
Could not locate Tomboy on D-Bus. Perhaps it's not running?
Firefox.PlacesItemSource "Firefox Places" encountered an error in UpdateItems: System.InvalidCastException: Cannot cast from source type to destination type.
  at Mono.Data.Sqlite.SqliteDataReader.VerifyType (Int32 i, DbType typ) [0x00000] in <filename unknown>:0 
  at Mono.Data.Sqlite.SqliteDataReader.GetString (Int32 i) [0x00000] in <filename unknown>:0 
  at Firefox.PlacesItemSource+<LoadPlaceItems>c__Iterator3.MoveNext () [0x00000] in <filename unknown>:0 
  at System.Collections.Generic.List`1[Firefox.PlaceItem].AddEnumerable (IEnumerable`1 enumerable) [0x00000] in <filename unknown>:0 
  at System.Collections.Generic.List`1[Firefox.PlaceItem]..ctor (IEnumerable`1 collection) [0x00000] in <filename unknown>:0 
  at System.Linq.Enumerable.ToArray[PlaceItem] (IEnumerable`1 source) [0x00000] in <filename unknown>:0 
  at Firefox.PlacesItemSource.UpdateItems () [0x00000] in <filename unknown>:0 
  at Do.Universe.Safe.SafeItemSource.UpdateItems () [0x00000] in <filename unknown>:0 .

```

and Xorg.0.log.

```
[    14.839] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[    14.839] X Protocol Version 11, Revision 0
[    14.839] Build Operating System: Linux 2.6.24-29-server i686 Ubuntu
[    14.839] Current Operating System: Linux raeDesky 2.6.38-11-generic #50-Ubuntu SMP Mon Sep 12 21:18:14 UTC 2011 i686
[    14.865] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-11-generic root=UUID=1dbd9e64-e128-4a31-87a0-9d0ef8160e6b ro quiet splash vt.handoff=7
[    14.865] Build Date: 11 August 2011  03:47:56PM
[    14.865] xorg-server 2:1.10.1-1ubuntu1.2 (For technical support please see http://www.ubuntu.com/support) 
[    14.865] Current version of pixman: 0.20.2
[    14.865] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    14.865] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    14.866] (==) Log file: "/var/log/Xorg.0.log", Time: Thu Sep 29 13:52:57 2011
[    14.866] (==) Using config file: "/etc/X11/xorg.conf"
[    14.866] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    14.867] (==) ServerLayout "Layout0"
[    14.867] (**) |-->Screen "Screen0" (0)
[    14.867] (**) |   |-->Monitor "Monitor0"
[    14.867] (**) |   |-->Device "Device0"
[    14.867] (**) |-->Input Device "Keyboard0"
[    14.867] (**) |-->Input Device "Mouse0"
[    14.867] (==) Automatically adding devices
[    14.867] (==) Automatically enabling devices
[    14.867] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    14.867] 	Entry deleted from font path.
[    14.867] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    14.867] 	Entry deleted from font path.
[    14.873] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    14.873] 	Entry deleted from font path.
[    14.873] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    14.873] 	Entry deleted from font path.
[    14.873] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    14.874] 	Entry deleted from font path.
[    14.874] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    14.874] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    14.874] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[    14.874] (WW) Disabling Keyboard0
[    14.874] (WW) Disabling Mouse0
[    14.874] (II) Loader magic: 0x81ffde0
[    14.874] (II) Module ABI versions:
[    14.874] 	X.Org ANSI C Emulation: 0.4
[    14.874] 	X.Org Video Driver: 10.0
[    14.874] 	X.Org XInput driver : 12.3
[    14.874] 	X.Org Server Extension : 5.0
[    14.878] (--) PCI:*(0:1:0:0) 10de:0221:3842:a341 rev 161, Mem @ 0xe8000000/16777216, 0xd0000000/268435456, 0xe9000000/16777216, BIOS @ 0x????????/131072
[    14.879] (WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
[    14.879] (II) LoadModule: "extmod"
[    14.889] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    14.890] (II) Module extmod: vendor="X.Org Foundation"
[    14.890] 	compiled for 1.10.1, module version = 1.0.0
[    14.890] 	Module class: X.Org Server Extension
[    14.890] 	ABI class: X.Org Server Extension, version 5.0
[    14.890] (II) Loading extension MIT-SCREEN-SAVER
[    14.890] (II) Loading extension XFree86-VidModeExtension
[    14.890] (II) Loading extension XFree86-DGA
[    14.890] (II) Loading extension DPMS
[    14.890] (II) Loading extension XVideo
[    14.890] (II) Loading extension XVideo-MotionCompensation
[    14.890] (II) Loading extension X-Resource
[    14.890] (II) LoadModule: "dbe"
[    14.890] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    14.891] (II) Module dbe: vendor="X.Org Foundation"
[    14.891] 	compiled for 1.10.1, module version = 1.0.0
[    14.891] 	Module class: X.Org Server Extension
[    14.891] 	ABI class: X.Org Server Extension, version 5.0
[    14.891] (II) Loading extension DOUBLE-BUFFER
[    14.891] (II) LoadModule: "glx"
[    14.891] (II) Loading /usr/lib/xorg/extra-modules/libglx.so
[    15.093] (II) Module glx: vendor="NVIDIA Corporation"
[    15.093] 	compiled for 4.0.2, module version = 1.0.0
[    15.093] 	Module class: X.Org Server Extension
[    15.093] (II) NVIDIA GLX Module  270.41.06  Mon Apr 18 15:11:28 PDT 2011
[    15.093] (II) Loading extension GLX
[    15.093] (II) LoadModule: "record"
[    15.093] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    15.093] (II) Module record: vendor="X.Org Foundation"
[    15.093] 	compiled for 1.10.1, module version = 1.13.0
[    15.093] 	Module class: X.Org Server Extension
[    15.093] 	ABI class: X.Org Server Extension, version 5.0
[    15.093] (II) Loading extension RECORD
[    15.094] (II) LoadModule: "dri"
[    15.094] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    15.094] (II) Module dri: vendor="X.Org Foundation"
[    15.094] 	compiled for 1.10.1, module version = 1.0.0
[    15.094] 	ABI class: X.Org Server Extension, version 5.0
[    15.094] (II) Loading extension XFree86-DRI
[    15.094] (II) LoadModule: "dri2"
[    15.095] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    15.098] (II) Module dri2: vendor="X.Org Foundation"
[    15.098] 	compiled for 1.10.1, module version = 1.2.0
[    15.098] 	ABI class: X.Org Server Extension, version 5.0
[    15.098] (II) Loading extension DRI2
[    15.098] (II) LoadModule: "nvidia"
[    15.098] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[    15.099] (II) Module nvidia: vendor="NVIDIA Corporation"
[    15.099] 	compiled for 4.0.2, module version = 1.0.0
[    15.099] 	Module class: X.Org Video Driver
[    15.112] (EE) NVIDIA: Failed to load the NVIDIA kernel module. Please check your
[    15.112] (EE) NVIDIA:     system's kernel log for additional error messages.
[    15.112] (II) UnloadModule: "nvidia"
[    15.112] (II) Unloading nvidia
[    15.112] (EE) Failed to load module "nvidia" (module-specific error, 0)
[    15.112] (EE) No drivers available.
[    15.112] 
Fatal server error:
[    15.112] no screens found
[    15.112] 
Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
[    15.112] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[    15.112] 

```

If this means X crashed, can you propose any solutions?  Again, like I said, this is a six-year old computer.  Does that make a difference?

---

### Post by raequin on 2011-10-02
* bump

---

### Post by 2F4U on 2011-10-03
It seems to be an issue with your nVidia graphics card. What graphics driver are you currently using and is this the latest version that matches your kernel?

---

### Post by untusoft on 2011-10-03
Yes,
recently our ubuntu 11.04, USB keyboard always logout unxpectedly. This happens on some of our computer (almost all) that has install 11.04.

So weird and so annoying. This never happen on 10.10 or before. 
Anybody know how to fixed it ?

---

### Post by raequin on 2011-10-06
> It seems to be an issue with your nVidia graphics card. What graphics driver are you currently using and is this the latest version that matches your kernel?

The driver I'm using is "NVIDIA Driver Version: 270.41.06".  There is a newer driver for my card, the GeForce 6200, available from NVIDIA's website.  I do not know how to answer your question about the driver matching my kernel.

```
uname -r
2.6.38-11-generic

```

Thanks.

---

### Post by Krytarik on 2011-10-06
> **raequin said:**
> The driver I'm using is "NVIDIA Driver Version: 270.41.06".  There is a newer driver for my card, the GeForce 6200, available from NVIDIA's website.
Try upgrading your driver to the most recent packaged version, 280.13, through Ubuntu-X-Swat's PPA:

[http://www.tuxgarage.com/2011/07/upgrade-video-drivers-through-ppas.html](http://www.tuxgarage.com/2011/07/upgrade-video-drivers-through-ppas.html)

Hope that helps!

---

