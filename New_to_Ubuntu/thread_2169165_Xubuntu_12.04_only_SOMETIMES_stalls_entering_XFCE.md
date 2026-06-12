---
title: "Xubuntu 12.04 only SOMETIMES stalls entering XFCE?"
date: 2013-08-20
forum: New to Ubuntu
---

### Post by Pako Pako on 2013-08-20
Just curious why my install of Xubuntu 12.04 on a DELL Lattitude D420 only *sometimes* hangs during login. It just displays the background of the login screen (after correct credentials are provided). I can move the mouse, but hitting CTRL+ALT+DEL does nothing.

I can still use ALT+CTRL+F1 to enter TTY1, login, and *sudo reboot now*. After as many as 3 reboots, I am finally allowed to enter the GUI desktop.

I thought it was the PHC kernel that was the culprit, but even the up-to-date 12.04 kernel sometimes won't enter the XFCE desktop. No SD card is inserted, nothing in the USB slots, battery is fully charged and units is connected via AC adapter. Can anyone clue me in?

---

### Post by rai_shu2 on 2013-08-21
Might be a problem with your network (or maybe a bug in Network Manager). Double-check that, because that's what that sounds like to me.

---

### Post by Toz on 2013-08-21
Hello pakopako2 and welcome to the forums.

In addition to what rai_shu2 notes:

The hidden log file .xsession-errors in your home folder might provide a clue as to what is happening. After you login successfully, post a copy of $HOME/.xsession-errors.old (the .old file is for the previous session that hung) so we can see what is going on. Since the file is hidden, you will have to "Ctrl+H" in thunar to show hidden files to be able to see it. If pastebinit is installed, the following command will post the contents of the file up to paste.ubuntu.com for easy reading:
```
pastebinit $HOME/.xsession-errors.old
```
...and post back the link that is generated.

The other thing you might want to try, before you log in, is to clear your saved sessions cache by going to the first tty and entering the following commands:
```
cd .cache
rm -rf sessions
```
...maybe the saved sessions cache is somehow corrupted.

---

### Post by Pako Pako on 2013-08-26
> **rai_shu2 said:**
> Might be a problem with your network (or maybe a  bug in Network Manager). Double-check that, because that's what that  sounds like to me.
Huh. How would I check my network? I ask specifically because the OS is installed on a laptop and is normally offline (with its wireless and bluetooth shut off in the BIOS).

> **Toz said:**
> The hidden log file .xsession-errors in your home folder might provide a clue as to what is happening. After you login successfully, post a copy of $HOME/.xsession-errors.old (the .old file is for the previous session that hung) so we can see what is going on.
...
The other thing you might want to try, before you log in, is to clear your saved sessions cache...maybe the saved sessions cache is somehow corrupted.
Hi Toz. (Dang it, I want my old name back.)
The command-line generated this url: [http://paste.ubuntu.com/6030416/](http://paste.ubuntu.com/6030416/)

It looks rather daunting with all the "resource unavailable" and "$home not available" phrases.

---

### Post by Toz on 2013-08-26
> **pakopako2 said:**
> 
Hi Toz. (Dang it, I want my old name back.)
Are you referring to your original username? If so, please create a thread in the Resolution Centre and one of the admins will take care of that for you.
> The command-line generated this url: [http://paste.ubuntu.com/6030416/](http://paste.ubuntu.com/6030416/)

It looks rather daunting with all the "resource unavailable" and "$home not available" phrases.
Yes, it doesn't look good. Have you tried clearing your sessions cache? Did it make a difference?

---

### Post by Pako Pako on 2013-08-27
I don't know. I had to reboot at some point yesterday and entered Xubuntu GUI with no problems.
Today, I might have hit something, but somehow I wound up in tty1 during log-in. I switched to tty7 only to see nothing, so another sudo reboot now and things work OK again.

If it ever happens again, I'll run pastebininit and compare it with my original to see what's overlapped. This isn't a "big" issue -- I am just curious why Xubuntu does this.

---

### Post by Toz on 2013-08-27
>  I am just curious why Xubuntu does this. Everytime that this has happened to me, its been because of a corrupt sessions cache. Deleting $HOME/.cache/sessions always cleared it up for me.

---

### Post by Pako Pako on 2013-08-30
Well, now all I get hit with are crashed account-manager errors every now and then upon login. (This is after the latest image update to x.x.52)
It doesn't stop anything, just that (!) in the corner showing up.

---

### Post by Toz on 2013-08-30
> **Pako Pako said:**
> Well, now all I get hit with are crashed account-manager errors every now and then upon login. (This is after the latest image update to x.x.52)
It doesn't stop anything, just that (!) in the corner showing up.

What exactly is the error message? A copy of $HOME/.xsession-errors might be helpful.

---

### Post by Pako Pako on 2013-09-01
> **Toz said:**
> What exactly is the error message? A copy of $HOME/.xsession-errors might be helpful.
Okie-doke. Much like the old log-in lock-ups, these "account-daemon" errors are random too. But at least they happen after a successful login. (Hm. When do record from paste.ubuntu.com expire? My name and IP address are included in some of these reports.)

Here is the .xsession-errors.old:
```
openConnection: connect: No such file or directory
cannot connect to brltty at :0

(polkit-gnome-authentication-agent-1:2223): GLib-CRITICAL **: g_variant_new_string: assertion `string != NULL' failed

(polkit-gnome-authentication-agent-1:2223): polkit-gnome-1-WARNING **: Failed to register client: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files
/usr/lib/pymodules/python2.7/fluxgui/fluxgui.py:162: GtkWarning: Cannot transform xsetting Net/IconThemeName of type gchararray to type GdkColor

  'gtk-icon-theme-name')
/usr/lib/pymodules/python2.7/fluxgui/fluxgui.py:162: Warning: g_value_unset: assertion `G_IS_VALUE (value)' failed
  'gtk-icon-theme-name')
/usr/lib/pymodules/python2.7/fluxgui/fluxgui.py:162: GtkWarning: Cannot transform xsetting Net/IconThemeName of type gchararray to type gint

  'gtk-icon-theme-name')
WARNING: gnome-keyring:: couldn't connect to: /tmp/keyring-VHLMwN/pkcs11: No such file or directory

(xfce4-settings-helper:2252): xfce4-settings-helper-WARNING **: Failed to get the _NET_NUMBER_OF_DESKTOPS property.
** Message: applet now removed from the notification area
/usr/lib/pymodules/python2.7/fluxgui/fluxgui.py:137: GtkWarning: IA__gdk_window_thaw_toplevel_updates_libgtk_only: assertion `private->update_and_descendants_freeze_count > 0' failed
  gtk.main()
** Message: using fallback from indicator to GtkStatusIcon
** Message: applet now embedded in the notification area

(xfce4-indicator-plugin:2303): libindicator-WARNING **: IndicatorObject class does not have an accessible description.

(xfce4-indicator-plugin:2303): libindicator-WARNING **: IndicatorObject class does not have an accessible description.
** Message: moving back from GtkStatusIcon to indicator
** Message: applet now removed from the notification area

(xfce4-indicator-plugin:2303): Gtk-CRITICAL **: IA__gtk_widget_realize: assertion `GTK_WIDGET_ANCHORED (widget) || GTK_IS_INVISIBLE (widget)' failed
Error: No running window found
thunar-volman: Unsupported USB device type.
thunar-volman: Unsupported USB device type.
thunar-volman: Unsupported USB device type.
thunar-volman: Unsupported USB device type.
thunar-volman: Unsupported USB device type.
thunar-volman: Unsupported USB device type.
thunar-volman: Unsupported USB device type.
thunar-volman: Unsupported USB device type.
thunar-volman: Unsupported USB device type.
thunar-volman: Unsupported USB device type.
thunar-volman: Unsupported USB device type.
thunar-volman: Unsupported USB device type.
thunar-volman: Unsupported USB device type.
thunar-volman: Unsupported USB device type.
thunar-volman: Unsupported USB device type.
thunar-volman: Unsupported USB device type.
```
Here's this session's error-long, though it doesn't seem to include the account-daemon crash that I reported.
```
openConnection: connect: No such file or directory
cannot connect to brltty at :0

(polkit-gnome-authentication-agent-1:2307): GLib-CRITICAL **: g_variant_new_string: assertion `string != NULL' failed

(polkit-gnome-authentication-agent-1:2307): polkit-gnome-1-WARNING **: Failed to register client: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files
WARNING: gnome-keyring:: couldn't connect to: /tmp/keyring-0W7SIO/pkcs11: No such file or directory
/usr/lib/pymodules/python2.7/fluxgui/fluxgui.py:162: GtkWarning: Cannot transform xsetting Net/IconThemeName of type gchararray to type GdkColor

  'gtk-icon-theme-name')
/usr/lib/pymodules/python2.7/fluxgui/fluxgui.py:162: Warning: g_value_unset: assertion `G_IS_VALUE (value)' failed
  'gtk-icon-theme-name')
/usr/lib/pymodules/python2.7/fluxgui/fluxgui.py:162: GtkWarning: Cannot transform xsetting Net/IconThemeName of type gchararray to type gint

  'gtk-icon-theme-name')
** Message: applet now removed from the notification area

(xfce4-settings-helper:2359): xfce4-settings-helper-WARNING **: Failed to get the _NET_NUMBER_OF_DESKTOPS property.
** Message: using fallback from indicator to GtkStatusIcon
** Message: applet now embedded in the notification area

(xfce4-indicator-plugin:2395): libindicator-WARNING **: IndicatorObject class does not have an accessible description.

(xfce4-indicator-plugin:2395): libindicator-WARNING **: IndicatorObject class does not have an accessible description.

(xfce4-indicator-plugin:2395): LIBDBUSMENU-GLIB-WARNING **: Getting layout failed: GDBus.Error:org.freedesktop.DBus.Error.UnknownMethod: No such interface `com.canonical.dbusmenu' on object at path /com/canonical/indicator/messages/menu
** Message: moving back from GtkStatusIcon to indicator
** Message: applet now removed from the notification area
```

---

### Post by Toz on 2013-09-01
Nothing but warnings in those files and nothing specific about account-daemon. Can you have a look in your /var/crash folder to see if there are some relevant log files there about account-daemon?

---

### Post by Pako Pako on 2013-09-02
This is what was submitted. I had to super-user open the file and take out the core-dump.
Also, is there a way to remove stuff I submit to paste.ubuntu.com?

```
ProblemType: Crash
Architecture: i386
CrashCounter: 1
DistroRelease: Ubuntu 12.04
ExecutablePath: /usr/lib/accountsservice/accounts-daemon
ProcCmdline: /usr/lib/accountsservice/accounts-daemon
ProcCwd: /
ProcEnviron: 
ProcMaps:
 00110000-00134000 r-xp 00000000 08:04 785072     /usr/lib/i386-linux-gnu/libdbus-glib-1.so.2.2.2
 00134000-00135000 r--p 00023000 08:04 785072     /usr/lib/i386-linux-gnu/libdbus-glib-1.so.2.2.2
 00135000-00136000 rw-p 00024000 08:04 785072     /usr/lib/i386-linux-gnu/libdbus-glib-1.so.2.2.2
 00136000-00289000 r-xp 00000000 08:04 789618     /usr/lib/i386-linux-gnu/libgio-2.0.so.0.3200.3
 00289000-0028b000 r--p 00153000 08:04 789618     /usr/lib/i386-linux-gnu/libgio-2.0.so.0.3200.3
 0028b000-0028c000 rw-p 00155000 08:04 789618     /usr/lib/i386-linux-gnu/libgio-2.0.so.0.3200.3
 0028c000-0028d000 rw-p 00000000 00:00 0 
 0028d000-00384000 r-xp 00000000 08:04 653764     /lib/i386-linux-gnu/libglib-2.0.so.0.3200.3
 00384000-00385000 r--p 000f6000 08:04 653764     /lib/i386-linux-gnu/libglib-2.0.so.0.3200.3
 00385000-00386000 rw-p 000f7000 08:04 653764     /lib/i386-linux-gnu/libglib-2.0.so.0.3200.3
 00386000-0038d000 r-xp 00000000 08:04 653119     /lib/i386-linux-gnu/librt-2.15.so
 0038d000-0038e000 r--p 00006000 08:04 653119     /lib/i386-linux-gnu/librt-2.15.so
 0038e000-0038f000 rw-p 00007000 08:04 653119     /lib/i386-linux-gnu/librt-2.15.so
 0038f000-00392000 r-xp 00000000 08:04 789630     /usr/lib/i386-linux-gnu/libgmodule-2.0.so.0.3200.3
 00392000-00393000 r--p 00002000 08:04 789630     /usr/lib/i386-linux-gnu/libgmodule-2.0.so.0.3200.3
 00393000-00394000 rw-p 00003000 08:04 789630     /usr/lib/i386-linux-gnu/libgmodule-2.0.so.0.3200.3
 00394000-003ce000 r-xp 00000000 08:04 653812     /lib/i386-linux-gnu/libpcre.so.3.12.1
 003ce000-003cf000 r--p 00039000 08:04 653812     /lib/i386-linux-gnu/libpcre.so.3.12.1
 003cf000-003d0000 rw-p 0003a000 08:04 653812     /lib/i386-linux-gnu/libpcre.so.3.12.1
 003d0000-003d3000 r-xp 00000000 08:04 653127     /lib/i386-linux-gnu/libdl-2.15.so
 003d3000-003d4000 r--p 00002000 08:04 653127     /lib/i386-linux-gnu/libdl-2.15.so
 003d4000-003d5000 rw-p 00003000 08:04 653127     /lib/i386-linux-gnu/libdl-2.15.so
 003d5000-003e0000 r-xp 00000000 08:04 653025     /lib/i386-linux-gnu/libnss_files-2.15.so
 003e0000-003e1000 r--p 0000a000 08:04 653025     /lib/i386-linux-gnu/libnss_files-2.15.so
 003e1000-003e2000 rw-p 0000b000 08:04 653025     /lib/i386-linux-gnu/libnss_files-2.15.so
 00450000-00467000 r-xp 00000000 08:04 653121     /lib/i386-linux-gnu/libpthread-2.15.so
 00467000-00468000 r--p 00016000 08:04 653121     /lib/i386-linux-gnu/libpthread-2.15.so
 00468000-00469000 rw-p 00017000 08:04 653121     /lib/i386-linux-gnu/libpthread-2.15.so
 00469000-0046b000 rw-p 00000000 00:00 0 
 0046b000-0060e000 r-xp 00000000 08:04 652873     /lib/i386-linux-gnu/libc-2.15.so
 0060e000-00610000 r--p 001a3000 08:04 652873     /lib/i386-linux-gnu/libc-2.15.so
 00610000-00611000 rw-p 001a5000 08:04 652873     /lib/i386-linux-gnu/libc-2.15.so
 00611000-00614000 rw-p 00000000 00:00 0 
 00629000-0062a000 r-xp 00000000 00:00 0          [vdso]
 0062d000-00643000 r-xp 00000000 08:04 653132     /lib/i386-linux-gnu/libnsl-2.15.so
 00643000-00644000 r--p 00015000 08:04 653132     /lib/i386-linux-gnu/libnsl-2.15.so
 00644000-00645000 rw-p 00016000 08:04 653132     /lib/i386-linux-gnu/libnsl-2.15.so
 00645000-00647000 rw-p 00000000 00:00 0 
 00890000-008a9000 r-xp 00000000 08:04 789841     /usr/lib/i386-linux-gnu/libpolkit-gobject-1.so.0.0.0
 008a9000-008aa000 r--p 00018000 08:04 789841     /usr/lib/i386-linux-gnu/libpolkit-gobject-1.so.0.0.0
 008aa000-008ab000 rw-p 00019000 08:04 789841     /usr/lib/i386-linux-gnu/libpolkit-gobject-1.so.0.0.0
 008cc000-008d6000 r-xp 00000000 08:04 653120     /lib/i386-linux-gnu/libnss_nis-2.15.so
 008d6000-008d7000 r--p 00009000 08:04 653120     /lib/i386-linux-gnu/libnss_nis-2.15.so
 008d7000-008d8000 rw-p 0000a000 08:04 653120     /lib/i386-linux-gnu/libnss_nis-2.15.so
 00b47000-00b94000 r-xp 00000000 08:04 789640     /usr/lib/i386-linux-gnu/libgobject-2.0.so.0.3200.3
 00b94000-00b95000 r--p 0004c000 08:04 789640     /usr/lib/i386-linux-gnu/libgobject-2.0.so.0.3200.3
 00b95000-00b96000 rw-p 0004d000 08:04 789640     /usr/lib/i386-linux-gnu/libgobject-2.0.so.0.3200.3
 00b96000-00b9b000 r-xp 00000000 08:04 789578     /usr/lib/i386-linux-gnu/libffi.so.6.0.0
 00b9b000-00b9c000 r--p 00004000 08:04 789578     /usr/lib/i386-linux-gnu/libffi.so.6.0.0
 00b9c000-00b9d000 rw-p 00005000 08:04 789578     /usr/lib/i386-linux-gnu/libffi.so.6.0.0
 00bbe000-00bd2000 r-xp 00000000 08:04 653850     /lib/i386-linux-gnu/libz.so.1.2.3.4
 00bd2000-00bd3000 r--p 00013000 08:04 653850     /lib/i386-linux-gnu/libz.so.1.2.3.4
 00bd3000-00bd4000 rw-p 00014000 08:04 653850     /lib/i386-linux-gnu/libz.so.1.2.3.4
 00c09000-00c50000 r-xp 00000000 08:04 653721     /lib/i386-linux-gnu/libdbus-1.so.3.5.8
 00c50000-00c51000 r--p 00047000 08:04 653721     /lib/i386-linux-gnu/libdbus-1.so.3.5.8
 00c51000-00c52000 rw-p 00048000 08:04 653721     /lib/i386-linux-gnu/libdbus-1.so.3.5.8
 00dc7000-00dda000 r-xp 00000000 08:04 653029     /lib/i386-linux-gnu/libresolv-2.15.so
 00dda000-00ddb000 ---p 00013000 08:04 653029     /lib/i386-linux-gnu/libresolv-2.15.so
 00ddb000-00ddc000 r--p 00013000 08:04 653029     /lib/i386-linux-gnu/libresolv-2.15.so
 00ddc000-00ddd000 rw-p 00014000 08:04 653029     /lib/i386-linux-gnu/libresolv-2.15.so
 00ddd000-00ddf000 rw-p 00000000 00:00 0 
 00eca000-00eea000 r-xp 00000000 08:04 653124     /lib/i386-linux-gnu/ld-2.15.so
 00eea000-00eeb000 r--p 0001f000 08:04 653124     /lib/i386-linux-gnu/ld-2.15.so
 00eeb000-00eec000 rw-p 00020000 08:04 653124     /lib/i386-linux-gnu/ld-2.15.so
 00f58000-00f5f000 r-xp 00000000 08:04 652875     /lib/i386-linux-gnu/libnss_compat-2.15.so
 00f5f000-00f60000 r--p 00006000 08:04 652875     /lib/i386-linux-gnu/libnss_compat-2.15.so
 00f60000-00f61000 rw-p 00007000 08:04 652875     /lib/i386-linux-gnu/libnss_compat-2.15.so
 00fd5000-00ff2000 r-xp 00000000 08:04 653827     /lib/i386-linux-gnu/libselinux.so.1
 00ff2000-00ff3000 r--p 0001c000 08:04 653827     /lib/i386-linux-gnu/libselinux.so.1
 00ff3000-00ff4000 rw-p 0001d000 08:04 653827     /lib/i386-linux-gnu/libselinux.so.1
 08048000-08059000 r-xp 00000000 08:04 787189     /usr/lib/accountsservice/accounts-daemon
 08059000-0805a000 r--p 00010000 08:04 787189     /usr/lib/accountsservice/accounts-daemon
 0805a000-0805b000 rw-p 00011000 08:04 787189     /usr/lib/accountsservice/accounts-daemon
 08a55000-08a98000 rw-p 00000000 00:00 0          [heap]
 b6e00000-b6e21000 rw-p 00000000 00:00 0 
 b6e21000-b6f00000 ---p 00000000 00:00 0 
 b6f4c000-b6f4d000 ---p 00000000 00:00 0 
 b6f4d000-b7752000 rw-p 00000000 00:00 0 
 b7760000-b7767000 r--s 00000000 08:04 791507     /usr/lib/i386-linux-gnu/gconv/gconv-modules.cache
 b7767000-b7769000 rw-p 00000000 00:00 0 
 bf8a7000-bf8c8000 rw-p 00000000 00:00 0          [stack]
ProcStatus:
 Name:    accounts-daemon
 State:    S (sleeping)
 Tgid:    1820
 Pid:    1820
 PPid:    1
 TracerPid:    0
 Uid:    0    0    0    0
 Gid:    0    0    0    0
 FDSize:    32
 Groups:    0 
 VmPeak:       16480 kB
 VmSize:       15832 kB
 VmLck:           0 kB
 VmPin:           0 kB
 VmHWM:        3388 kB
 VmRSS:        3388 kB
 VmData:        9560 kB
 VmStk:         136 kB
 VmExe:          68 kB
 VmLib:        5852 kB
 VmPTE:          36 kB
 VmSwap:           0 kB
 Threads:    2
 SigQ:    0/7773
 SigPnd:    0000000000000000
 ShdPnd:    0000000000000000
 SigBlk:    0000000000000000
 SigIgn:    0000000000001000
 SigCgt:    0000000180000000
 CapInh:    0000000000000000
 CapPrm:    ffffffffffffffff
 CapEff:    ffffffffffffffff
 CapBnd:    ffffffffffffffff
 Cpus_allowed:    3
 Cpus_allowed_list:    0-1
 Mems_allowed:    1
 Mems_allowed_list:    0
 voluntary_ctxt_switches:    72
 nonvoluntary_ctxt_switches:    31
Signal: 11
Uname: Linux 3.2.0-52-generic i686
UserGroups: 
CoreDump: base64
=omitted=
ApportVersion: 2.0.1-0ubuntu17.4
Dependencies:
 adduser 3.113ubuntu2
 base-passwd 3.5.24
 busybox-initramfs 1:1.18.5-1ubuntu4.1
 coreutils 8.13-3ubuntu3.2
 cpio 2.11-7ubuntu3
 dbus 1.4.18-1ubuntu1.4
 debconf 1.5.42ubuntu1
 debianutils 4.2.1ubuntu2
 dpkg 1.16.1.2ubuntu7.1
 findutils 4.4.2-4ubuntu1
 gcc-4.6-base 4.6.3-1ubuntu5
 ifupdown 0.7~beta2ubuntu8
 initramfs-tools 0.99ubuntu13.1
 initramfs-tools-bin 0.99ubuntu13.1
 initscripts 2.88dsf-13.10ubuntu11.1
 insserv 1.14.0-2.1ubuntu2
 iproute 20111117-1ubuntu2
 klibc-utils 1.5.25-1ubuntu2
 libaccountsservice0 0.6.15-2ubuntu9.6
 libacl1 2.2.51-5ubuntu1
 libattr1 1:2.4.46-5ubuntu1
 libblkid1 2.20.1-1ubuntu3
 libbz2-1.0 1.0.6-1
 libc-bin 2.15-0ubuntu10.4
 libc6 2.15-0ubuntu10.4
 libdb5.1 5.1.25-11build1
 libdbus-1-3 1.4.18-1ubuntu1.4
 libdbus-glib-1-2 0.98-1ubuntu1.1
 libdrm-intel1 2.4.43-0ubuntu0.0.2
 libdrm-nouveau1a 2.4.43-0ubuntu0.0.2
 libdrm-radeon1 2.4.43-0ubuntu0.0.2
 libdrm2 2.4.43-0ubuntu0.0.2
 libexpat1 2.0.1-7.2ubuntu1.1
 libffi6 3.0.11~rc1-5
 libgcc1 1:4.6.3-1ubuntu5
 libglib2.0-0 2.32.3-0ubuntu1
 libklibc 1.5.25-1ubuntu2
 liblzma5 5.1.1alpha+20110809-3
 libmount1 2.20.1-1ubuntu3
 libncurses5 5.9-4
 libncursesw5 5.9-4
 libnih-dbus1 1.0.3-4ubuntu9.1
 libnih1 1.0.3-4ubuntu9.1
 libpam-modules 1.1.3-7ubuntu2
 libpam-modules-bin 1.1.3-7ubuntu2
 libpam0g 1.1.3-7ubuntu2
 libpciaccess0 0.12.902-1ubuntu0.2
 libpcre3 8.12-4
 libplymouth2 0.8.2-2ubuntu31.1
 libpng12-0 1.2.46-3ubuntu4
 libpolkit-gobject-1-0 0.104-1ubuntu1
 libselinux1 2.1.0-4.1ubuntu1
 libslang2 2.2.4-3ubuntu1
 libtinfo5 5.9-4
 libudev0 175-0ubuntu9.4
 libuuid1 2.20.1-1ubuntu3
 lsb-base 4.0-0ubuntu20.3
 makedev 2.3.1-89ubuntu2
 module-init-tools 3.16-1ubuntu2
 mount 2.20.1-1ubuntu3
 mountall 2.36.4
 multiarch-support 2.15-0ubuntu10.4
 ncurses-bin 5.9-4
 netbase 4.47ubuntu1
 passwd 1:4.1.4.2+svn3283-3ubuntu5.1
 perl-base 5.14.2-6ubuntu2.3
 plymouth 0.8.2-2ubuntu31.1
 procps 1:3.2.8-11ubuntu6
 sed 4.2.1-9
 sensible-utils 0.0.6ubuntu2
 sysv-rc 2.88dsf-13.10ubuntu11.1
 sysvinit-utils 2.88dsf-13.10ubuntu11.1
 tar 1.26-4ubuntu1
 tzdata 2012e-0ubuntu0.12.04.1
 udev 175-0ubuntu9.4
 upstart 1.5-0ubuntu7.2
 util-linux 2.20.1-1ubuntu3
 xz-utils 5.1.1alpha+20110809-3
 zlib1g 1:1.2.3.4.dfsg-3ubuntu4
Disassembly:
 => 0x2d4a7d:    call   *%eax
    0x2d4a7f:    test   %eax,%eax
    0x2d4a81:    mov    %eax,%ebp
    0x2d4a83:    jne    0x2d4aa0
    0x2d4a85:    mov    %ebp,%eax
    0x2d4a87:    mov    0x1c(%esp),%ebx
    0x2d4a8b:    mov    0x20(%esp),%esi
    0x2d4a8f:    mov    0x24(%esp),%edi
    0x2d4a93:    mov    0x28(%esp),%ebp
    0x2d4a97:    add    $0x2c,%esp
    0x2d4a9a:    ret    
    0x2d4a9b:    nop
    0x2d4a9c:    lea    0x0(%esi,%eiz,1),%esi
    0x2d4aa0:    mov    0x30(%esp),%eax
    0x2d4aa4:    mov    %eax,(%esp)
    0x2d4aa7:    call   0x2d49a0 <g_source_get_time>
MarkForUpload: True
Package: accountsservice 0.6.15-2ubuntu9.6
PackageArchitecture: i386
ProcVersionSignature: Ubuntu 3.2.0-52.78-generic 3.2.48
Registers:
 eax            0x8a8aa50    145271376
 ecx            0x3    3
 edx            0x8a8a390    145269648
 ebx            0x384ff4    3690484
 esp            0xbf8c6b00    0xbf8c6b00
 ebp            0x8a6c120    0x8a6c120
 esi            0x8a67770    145127280
 edi            0x0    0
 eip            0x2d4a7d    0x2d4a7d
 eflags         0x10206    [ PF IF RF ]
 cs             0x73    115
 ss             0x7b    123
 ds             0x7b    123
 es             0x7b    123
 fs             0x0    0
 gs             0x33    51
SegvAnalysis:
 Segfault happened at: 0x2d4a7d:    call   *%eax
 PC (0x002d4a7d) ok
 source "*%eax" (0x08a8aa50) ok
 destination "(%esp)" (0xbf8c6b00) ok
 SP (0xbf8c6b00) ok
 Reason could not be automatically determined.
SourcePackage: accountsservice
Stacktrace:
 #0  0x002d4a7d in ?? () from /lib/i386-linux-gnu/libglib-2.0.so.0
 No symbol table info available.
 #1  0x002d3d86 in g_main_context_dispatch () from /lib/i386-linux-gnu/libglib-2.0.so.0
 No symbol table info available.
 #2  0x002d4125 in ?? () from /lib/i386-linux-gnu/libglib-2.0.so.0
 No symbol table info available.
 #3  0x002d456b in g_main_loop_run () from /lib/i386-linux-gnu/libglib-2.0.so.0
 No symbol table info available.
 #4  0x0804bcf0 in ?? ()
 No symbol table info available.
 #5  0x004844d3 in __libc_start_main () from /lib/i386-linux-gnu/libc.so.6
 No symbol table info available.
 #6  0x0804bd25 in ?? ()
 No symbol table info available.
StacktraceAddressSignature: /usr/lib/accountsservice/accounts-daemon:11:i686:/lib/i386-linux-gnu/libglib-2.0.so.0.3200.3+47a7d:/lib/i386-linux-gnu/libglib-2.0.so.0.3200.3+46d86:/lib/i386-linux-gnu/libglib-2.0.so.0.3200.3+47125:/lib/i386-linux-gnu/libglib-2.0.so.0.3200.3+4756b:/usr/lib/accountsservice/accounts-daemon+3cf0:/lib/i386-linux-gnu/libc-2.15.so+194d3:/usr/lib/accountsservice/accounts-daemon+3d25
StacktraceTop:
 ?? () from /lib/i386-linux-gnu/libglib-2.0.so.0
 g_main_context_dispatch () from /lib/i386-linux-gnu/libglib-2.0.so.0
 ?? () from /lib/i386-linux-gnu/libglib-2.0.so.0
 g_main_loop_run () from /lib/i386-linux-gnu/libglib-2.0.so.0
 ?? ()
Tags:  precise
ThreadStacktrace:
 .
 Thread 2 (Thread 0xb774cb40 (LWP 1837)):
 #0  0x00629416 in __kernel_vsyscall ()
 No symbol table info available.
 #1  0x0054b690 in poll () from /lib/i386-linux-gnu/libc.so.6
 No symbol table info available.
 #2  0x002e1a7b in g_poll () from /lib/i386-linux-gnu/libglib-2.0.so.0
 No symbol table info available.
 #3  0x002d40ae in ?? () from /lib/i386-linux-gnu/libglib-2.0.so.0
 No symbol table info available.
 #4  0x002d456b in g_main_loop_run () from /lib/i386-linux-gnu/libglib-2.0.so.0
 No symbol table info available.
 #5  0x002051ba in ?? () from /usr/lib/i386-linux-gnu/libgio-2.0.so.0
 No symbol table info available.
 #6  0x002f76b3 in ?? () from /lib/i386-linux-gnu/libglib-2.0.so.0
 No symbol table info available.
 #7  0x00456d4c in start_thread () from /lib/i386-linux-gnu/libpthread.so.0
 No symbol table info available.
 #8  0x00559dde in clone () from /lib/i386-linux-gnu/libc.so.6
 No symbol table info available.
 .
 Thread 1 (Thread 0xb774d740 (LWP 1820)):
 #0  0x002d4a7d in ?? () from /lib/i386-linux-gnu/libglib-2.0.so.0
 No symbol table info available.
 #1  0x002d3d86 in g_main_context_dispatch () from /lib/i386-linux-gnu/libglib-2.0.so.0
 No symbol table info available.
 #2  0x002d4125 in ?? () from /lib/i386-linux-gnu/libglib-2.0.so.0
 No symbol table info available.
 #3  0x002d456b in g_main_loop_run () from /lib/i386-linux-gnu/libglib-2.0.so.0
 No symbol table info available.
 #4  0x0804bcf0 in ?? ()
 No symbol table info available.
 #5  0x004844d3 in __libc_start_main () from /lib/i386-linux-gnu/libc.so.6
 No symbol table info available.
 #6  0x0804bd25 in ?? ()
 No symbol table info available.
Title: accounts-daemon crashed with SIGSEGV in g_main_context_dispatch()
UpgradeStatus: No upgrade log present (probably fresh install)
```

---

### Post by Toz on 2013-09-02
> Also, is there a way to remove stuff I submit to paste.ubuntu.com?
I'm sorry, but I don't know. I did find [this thread]("http://ubuntuforums.org/showthread.php?t=1976776"), but it doesn't really answer how to delete the entry. According to the link to the launchpad entry, they last a few days only.

> **Pako Pako said:**
> This is what was submitted. I had to super-user open the file and take out the core-dump.


```
ProblemType: Crash
Architecture: i386
CrashCounter: 1
DistroRelease: Ubuntu 12.04
ExecutablePath: /usr/lib/accountsservice/accounts-daemon
ProcCmdline: /usr/lib/accountsservice/accounts-daemon
ProcCwd: /
ProcEnviron: 
ProcMaps:
 00110000-00134000 r-xp 00000000 08:04 785072     /usr/lib/i386-linux-gnu/libdbus-glib-1.so.2.2.2
 00134000-00135000 r--p 00023000 08:04 785072     /usr/lib/i386-linux-gnu/libdbus-glib-1.so.2.2.2
 00135000-00136000 rw-p 00024000 08:04 785072     /usr/lib/i386-linux-gnu/libdbus-glib-1.so.2.2.2
 00136000-00289000 r-xp 00000000 08:04 789618     /usr/lib/i386-linux-gnu/libgio-2.0.so.0.3200.3
 00289000-0028b000 r--p 00153000 08:04 789618     /usr/lib/i386-linux-gnu/libgio-2.0.so.0.3200.3
 0028b000-0028c000 rw-p 00155000 08:04 789618     /usr/lib/i386-linux-gnu/libgio-2.0.so.0.3200.3
 0028c000-0028d000 rw-p 00000000 00:00 0 
 0028d000-00384000 r-xp 00000000 08:04 653764     /lib/i386-linux-gnu/libglib-2.0.so.0.3200.3
 00384000-00385000 r--p 000f6000 08:04 653764     /lib/i386-linux-gnu/libglib-2.0.so.0.3200.3
 00385000-00386000 rw-p 000f7000 08:04 653764     /lib/i386-linux-gnu/libglib-2.0.so.0.3200.3
 00386000-0038d000 r-xp 00000000 08:04 653119     /lib/i386-linux-gnu/librt-2.15.so
 0038d000-0038e000 r--p 00006000 08:04 653119     /lib/i386-linux-gnu/librt-2.15.so
 0038e000-0038f000 rw-p 00007000 08:04 653119     /lib/i386-linux-gnu/librt-2.15.so
 0038f000-00392000 r-xp 00000000 08:04 789630     /usr/lib/i386-linux-gnu/libgmodule-2.0.so.0.3200.3
 00392000-00393000 r--p 00002000 08:04 789630     /usr/lib/i386-linux-gnu/libgmodule-2.0.so.0.3200.3
 00393000-00394000 rw-p 00003000 08:04 789630     /usr/lib/i386-linux-gnu/libgmodule-2.0.so.0.3200.3
 00394000-003ce000 r-xp 00000000 08:04 653812     /lib/i386-linux-gnu/libpcre.so.3.12.1
 003ce000-003cf000 r--p 00039000 08:04 653812     /lib/i386-linux-gnu/libpcre.so.3.12.1
 003cf000-003d0000 rw-p 0003a000 08:04 653812     /lib/i386-linux-gnu/libpcre.so.3.12.1
 003d0000-003d3000 r-xp 00000000 08:04 653127     /lib/i386-linux-gnu/libdl-2.15.so
 003d3000-003d4000 r--p 00002000 08:04 653127     /lib/i386-linux-gnu/libdl-2.15.so
 003d4000-003d5000 rw-p 00003000 08:04 653127     /lib/i386-linux-gnu/libdl-2.15.so
 003d5000-003e0000 r-xp 00000000 08:04 653025     /lib/i386-linux-gnu/libnss_files-2.15.so
 003e0000-003e1000 r--p 0000a000 08:04 653025     /lib/i386-linux-gnu/libnss_files-2.15.so
 003e1000-003e2000 rw-p 0000b000 08:04 653025     /lib/i386-linux-gnu/libnss_files-2.15.so
 00450000-00467000 r-xp 00000000 08:04 653121     /lib/i386-linux-gnu/libpthread-2.15.so
 00467000-00468000 r--p 00016000 08:04 653121     /lib/i386-linux-gnu/libpthread-2.15.so
 00468000-00469000 rw-p 00017000 08:04 653121     /lib/i386-linux-gnu/libpthread-2.15.so
 00469000-0046b000 rw-p 00000000 00:00 0 
 0046b000-0060e000 r-xp 00000000 08:04 652873     /lib/i386-linux-gnu/libc-2.15.so
 0060e000-00610000 r--p 001a3000 08:04 652873     /lib/i386-linux-gnu/libc-2.15.so
 00610000-00611000 rw-p 001a5000 08:04 652873     /lib/i386-linux-gnu/libc-2.15.so
 00611000-00614000 rw-p 00000000 00:00 0 
 00629000-0062a000 r-xp 00000000 00:00 0          [vdso]
 0062d000-00643000 r-xp 00000000 08:04 653132     /lib/i386-linux-gnu/libnsl-2.15.so
 00643000-00644000 r--p 00015000 08:04 653132     /lib/i386-linux-gnu/libnsl-2.15.so
 00644000-00645000 rw-p 00016000 08:04 653132     /lib/i386-linux-gnu/libnsl-2.15.so
 00645000-00647000 rw-p 00000000 00:00 0 
 00890000-008a9000 r-xp 00000000 08:04 789841     /usr/lib/i386-linux-gnu/libpolkit-gobject-1.so.0.0.0
 008a9000-008aa000 r--p 00018000 08:04 789841     /usr/lib/i386-linux-gnu/libpolkit-gobject-1.so.0.0.0
 008aa000-008ab000 rw-p 00019000 08:04 789841     /usr/lib/i386-linux-gnu/libpolkit-gobject-1.so.0.0.0
 008cc000-008d6000 r-xp 00000000 08:04 653120     /lib/i386-linux-gnu/libnss_nis-2.15.so
 008d6000-008d7000 r--p 00009000 08:04 653120     /lib/i386-linux-gnu/libnss_nis-2.15.so
 008d7000-008d8000 rw-p 0000a000 08:04 653120     /lib/i386-linux-gnu/libnss_nis-2.15.so
 00b47000-00b94000 r-xp 00000000 08:04 789640     /usr/lib/i386-linux-gnu/libgobject-2.0.so.0.3200.3
 00b94000-00b95000 r--p 0004c000 08:04 789640     /usr/lib/i386-linux-gnu/libgobject-2.0.so.0.3200.3
 00b95000-00b96000 rw-p 0004d000 08:04 789640     /usr/lib/i386-linux-gnu/libgobject-2.0.so.0.3200.3
 00b96000-00b9b000 r-xp 00000000 08:04 789578     /usr/lib/i386-linux-gnu/libffi.so.6.0.0
 00b9b000-00b9c000 r--p 00004000 08:04 789578     /usr/lib/i386-linux-gnu/libffi.so.6.0.0
 00b9c000-00b9d000 rw-p 00005000 08:04 789578     /usr/lib/i386-linux-gnu/libffi.so.6.0.0
 00bbe000-00bd2000 r-xp 00000000 08:04 653850     /lib/i386-linux-gnu/libz.so.1.2.3.4
 00bd2000-00bd3000 r--p 00013000 08:04 653850     /lib/i386-linux-gnu/libz.so.1.2.3.4
 00bd3000-00bd4000 rw-p 00014000 08:04 653850     /lib/i386-linux-gnu/libz.so.1.2.3.4
 00c09000-00c50000 r-xp 00000000 08:04 653721     /lib/i386-linux-gnu/libdbus-1.so.3.5.8
 00c50000-00c51000 r--p 00047000 08:04 653721     /lib/i386-linux-gnu/libdbus-1.so.3.5.8
 00c51000-00c52000 rw-p 00048000 08:04 653721     /lib/i386-linux-gnu/libdbus-1.so.3.5.8
 00dc7000-00dda000 r-xp 00000000 08:04 653029     /lib/i386-linux-gnu/libresolv-2.15.so
 00dda000-00ddb000 ---p 00013000 08:04 653029     /lib/i386-linux-gnu/libresolv-2.15.so
 00ddb000-00ddc000 r--p 00013000 08:04 653029     /lib/i386-linux-gnu/libresolv-2.15.so
 00ddc000-00ddd000 rw-p 00014000 08:04 653029     /lib/i386-linux-gnu/libresolv-2.15.so
 00ddd000-00ddf000 rw-p 00000000 00:00 0 
 00eca000-00eea000 r-xp 00000000 08:04 653124     /lib/i386-linux-gnu/ld-2.15.so
 00eea000-00eeb000 r--p 0001f000 08:04 653124     /lib/i386-linux-gnu/ld-2.15.so
 00eeb000-00eec000 rw-p 00020000 08:04 653124     /lib/i386-linux-gnu/ld-2.15.so
 00f58000-00f5f000 r-xp 00000000 08:04 652875     /lib/i386-linux-gnu/libnss_compat-2.15.so
 00f5f000-00f60000 r--p 00006000 08:04 652875     /lib/i386-linux-gnu/libnss_compat-2.15.so
 00f60000-00f61000 rw-p 00007000 08:04 652875     /lib/i386-linux-gnu/libnss_compat-2.15.so
 00fd5000-00ff2000 r-xp 00000000 08:04 653827     /lib/i386-linux-gnu/libselinux.so.1
 00ff2000-00ff3000 r--p 0001c000 08:04 653827     /lib/i386-linux-gnu/libselinux.so.1
 00ff3000-00ff4000 rw-p 0001d000 08:04 653827     /lib/i386-linux-gnu/libselinux.so.1
 08048000-08059000 r-xp 00000000 08:04 787189     /usr/lib/accountsservice/accounts-daemon
 08059000-0805a000 r--p 00010000 08:04 787189     /usr/lib/accountsservice/accounts-daemon
 0805a000-0805b000 rw-p 00011000 08:04 787189     /usr/lib/accountsservice/accounts-daemon
 08a55000-08a98000 rw-p 00000000 00:00 0          [heap]
 b6e00000-b6e21000 rw-p 00000000 00:00 0 
 b6e21000-b6f00000 ---p 00000000 00:00 0 
 b6f4c000-b6f4d000 ---p 00000000 00:00 0 
 b6f4d000-b7752000 rw-p 00000000 00:00 0 
 b7760000-b7767000 r--s 00000000 08:04 791507     /usr/lib/i386-linux-gnu/gconv/gconv-modules.cache
 b7767000-b7769000 rw-p 00000000 00:00 0 
 bf8a7000-bf8c8000 rw-p 00000000 00:00 0          [stack]
ProcStatus:
 Name:    accounts-daemon
 State:    S (sleeping)
 Tgid:    1820
 Pid:    1820
 PPid:    1
 TracerPid:    0
 Uid:    0    0    0    0
 Gid:    0    0    0    0
 FDSize:    32
 Groups:    0 
 VmPeak:       16480 kB
 VmSize:       15832 kB
 VmLck:           0 kB
 VmPin:           0 kB
 VmHWM:        3388 kB
 VmRSS:        3388 kB
 VmData:        9560 kB
 VmStk:         136 kB
 VmExe:          68 kB
 VmLib:        5852 kB
 VmPTE:          36 kB
 VmSwap:           0 kB
 Threads:    2
 SigQ:    0/7773
 SigPnd:    0000000000000000
 ShdPnd:    0000000000000000
 SigBlk:    0000000000000000
 SigIgn:    0000000000001000
 SigCgt:    0000000180000000
 CapInh:    0000000000000000
 CapPrm:    ffffffffffffffff
 CapEff:    ffffffffffffffff
 CapBnd:    ffffffffffffffff
 Cpus_allowed:    3
 Cpus_allowed_list:    0-1
 Mems_allowed:    1
 Mems_allowed_list:    0
 voluntary_ctxt_switches:    72
 nonvoluntary_ctxt_switches:    31
Signal: 11
Uname: Linux 3.2.0-52-generic i686
UserGroups: 
CoreDump: base64
=omitted=
ApportVersion: 2.0.1-0ubuntu17.4
Dependencies:
 adduser 3.113ubuntu2
 base-passwd 3.5.24
 busybox-initramfs 1:1.18.5-1ubuntu4.1
 coreutils 8.13-3ubuntu3.2
 cpio 2.11-7ubuntu3
 dbus 1.4.18-1ubuntu1.4
 debconf 1.5.42ubuntu1
 debianutils 4.2.1ubuntu2
 dpkg 1.16.1.2ubuntu7.1
 findutils 4.4.2-4ubuntu1
 gcc-4.6-base 4.6.3-1ubuntu5
 ifupdown 0.7~beta2ubuntu8
 initramfs-tools 0.99ubuntu13.1
 initramfs-tools-bin 0.99ubuntu13.1
 initscripts 2.88dsf-13.10ubuntu11.1
 insserv 1.14.0-2.1ubuntu2
 iproute 20111117-1ubuntu2
 klibc-utils 1.5.25-1ubuntu2
 libaccountsservice0 0.6.15-2ubuntu9.6
 libacl1 2.2.51-5ubuntu1
 libattr1 1:2.4.46-5ubuntu1
 libblkid1 2.20.1-1ubuntu3
 libbz2-1.0 1.0.6-1
 libc-bin 2.15-0ubuntu10.4
 libc6 2.15-0ubuntu10.4
 libdb5.1 5.1.25-11build1
 libdbus-1-3 1.4.18-1ubuntu1.4
 libdbus-glib-1-2 0.98-1ubuntu1.1
 libdrm-intel1 2.4.43-0ubuntu0.0.2
 libdrm-nouveau1a 2.4.43-0ubuntu0.0.2
 libdrm-radeon1 2.4.43-0ubuntu0.0.2
 libdrm2 2.4.43-0ubuntu0.0.2
 libexpat1 2.0.1-7.2ubuntu1.1
 libffi6 3.0.11~rc1-5
 libgcc1 1:4.6.3-1ubuntu5
 libglib2.0-0 2.32.3-0ubuntu1
 libklibc 1.5.25-1ubuntu2
 liblzma5 5.1.1alpha+20110809-3
 libmount1 2.20.1-1ubuntu3
 libncurses5 5.9-4
 libncursesw5 5.9-4
 libnih-dbus1 1.0.3-4ubuntu9.1
 libnih1 1.0.3-4ubuntu9.1
 libpam-modules 1.1.3-7ubuntu2
 libpam-modules-bin 1.1.3-7ubuntu2
 libpam0g 1.1.3-7ubuntu2
 libpciaccess0 0.12.902-1ubuntu0.2
 libpcre3 8.12-4
 libplymouth2 0.8.2-2ubuntu31.1
 libpng12-0 1.2.46-3ubuntu4
 libpolkit-gobject-1-0 0.104-1ubuntu1
 libselinux1 2.1.0-4.1ubuntu1
 libslang2 2.2.4-3ubuntu1
 libtinfo5 5.9-4
 libudev0 175-0ubuntu9.4
 libuuid1 2.20.1-1ubuntu3
 lsb-base 4.0-0ubuntu20.3
 makedev 2.3.1-89ubuntu2
 module-init-tools 3.16-1ubuntu2
 mount 2.20.1-1ubuntu3
 mountall 2.36.4
 multiarch-support 2.15-0ubuntu10.4
 ncurses-bin 5.9-4
 netbase 4.47ubuntu1
 passwd 1:4.1.4.2+svn3283-3ubuntu5.1
 perl-base 5.14.2-6ubuntu2.3
 plymouth 0.8.2-2ubuntu31.1
 procps 1:3.2.8-11ubuntu6
 sed 4.2.1-9
 sensible-utils 0.0.6ubuntu2
 sysv-rc 2.88dsf-13.10ubuntu11.1
 sysvinit-utils 2.88dsf-13.10ubuntu11.1
 tar 1.26-4ubuntu1
 tzdata 2012e-0ubuntu0.12.04.1
 udev 175-0ubuntu9.4
 upstart 1.5-0ubuntu7.2
 util-linux 2.20.1-1ubuntu3
 xz-utils 5.1.1alpha+20110809-3
 zlib1g 1:1.2.3.4.dfsg-3ubuntu4
Disassembly:
 => 0x2d4a7d:    call   *%eax
    0x2d4a7f:    test   %eax,%eax
    0x2d4a81:    mov    %eax,%ebp
    0x2d4a83:    jne    0x2d4aa0
    0x2d4a85:    mov    %ebp,%eax
    0x2d4a87:    mov    0x1c(%esp),%ebx
    0x2d4a8b:    mov    0x20(%esp),%esi
    0x2d4a8f:    mov    0x24(%esp),%edi
    0x2d4a93:    mov    0x28(%esp),%ebp
    0x2d4a97:    add    $0x2c,%esp
    0x2d4a9a:    ret    
    0x2d4a9b:    nop
    0x2d4a9c:    lea    0x0(%esi,%eiz,1),%esi
    0x2d4aa0:    mov    0x30(%esp),%eax
    0x2d4aa4:    mov    %eax,(%esp)
    0x2d4aa7:    call   0x2d49a0 <g_source_get_time>
MarkForUpload: True
Package: accountsservice 0.6.15-2ubuntu9.6
PackageArchitecture: i386
ProcVersionSignature: Ubuntu 3.2.0-52.78-generic 3.2.48
Registers:
 eax            0x8a8aa50    145271376
 ecx            0x3    3
 edx            0x8a8a390    145269648
 ebx            0x384ff4    3690484
 esp            0xbf8c6b00    0xbf8c6b00
 ebp            0x8a6c120    0x8a6c120
 esi            0x8a67770    145127280
 edi            0x0    0
 eip            0x2d4a7d    0x2d4a7d
 eflags         0x10206    [ PF IF RF ]
 cs             0x73    115
 ss             0x7b    123
 ds             0x7b    123
 es             0x7b    123
 fs             0x0    0
 gs             0x33    51
SegvAnalysis:
 Segfault happened at: 0x2d4a7d:    call   *%eax
 PC (0x002d4a7d) ok
 source "*%eax" (0x08a8aa50) ok
 destination "(%esp)" (0xbf8c6b00) ok
 SP (0xbf8c6b00) ok
 Reason could not be automatically determined.
SourcePackage: accountsservice
Stacktrace:
 #0  0x002d4a7d in ?? () from /lib/i386-linux-gnu/libglib-2.0.so.0
 No symbol table info available.
 #1  0x002d3d86 in g_main_context_dispatch () from /lib/i386-linux-gnu/libglib-2.0.so.0
 No symbol table info available.
 #2  0x002d4125 in ?? () from /lib/i386-linux-gnu/libglib-2.0.so.0
 No symbol table info available.
 #3  0x002d456b in g_main_loop_run () from /lib/i386-linux-gnu/libglib-2.0.so.0
 No symbol table info available.
 #4  0x0804bcf0 in ?? ()
 No symbol table info available.
 #5  0x004844d3 in __libc_start_main () from /lib/i386-linux-gnu/libc.so.6
 No symbol table info available.
 #6  0x0804bd25 in ?? ()
 No symbol table info available.
StacktraceAddressSignature: /usr/lib/accountsservice/accounts-daemon:11:i686:/lib/i386-linux-gnu/libglib-2.0.so.0.3200.3+47a7d:/lib/i386-linux-gnu/libglib-2.0.so.0.3200.3+46d86:/lib/i386-linux-gnu/libglib-2.0.so.0.3200.3+47125:/lib/i386-linux-gnu/libglib-2.0.so.0.3200.3+4756b:/usr/lib/accountsservice/accounts-daemon+3cf0:/lib/i386-linux-gnu/libc-2.15.so+194d3:/usr/lib/accountsservice/accounts-daemon+3d25
StacktraceTop:
 ?? () from /lib/i386-linux-gnu/libglib-2.0.so.0
 g_main_context_dispatch () from /lib/i386-linux-gnu/libglib-2.0.so.0
 ?? () from /lib/i386-linux-gnu/libglib-2.0.so.0
 g_main_loop_run () from /lib/i386-linux-gnu/libglib-2.0.so.0
 ?? ()
Tags:  precise
ThreadStacktrace:
 .
 Thread 2 (Thread 0xb774cb40 (LWP 1837)):
 #0  0x00629416 in __kernel_vsyscall ()
 No symbol table info available.
 #1  0x0054b690 in poll () from /lib/i386-linux-gnu/libc.so.6
 No symbol table info available.
 #2  0x002e1a7b in g_poll () from /lib/i386-linux-gnu/libglib-2.0.so.0
 No symbol table info available.
 #3  0x002d40ae in ?? () from /lib/i386-linux-gnu/libglib-2.0.so.0
 No symbol table info available.
 #4  0x002d456b in g_main_loop_run () from /lib/i386-linux-gnu/libglib-2.0.so.0
 No symbol table info available.
 #5  0x002051ba in ?? () from /usr/lib/i386-linux-gnu/libgio-2.0.so.0
 No symbol table info available.
 #6  0x002f76b3 in ?? () from /lib/i386-linux-gnu/libglib-2.0.so.0
 No symbol table info available.
 #7  0x00456d4c in start_thread () from /lib/i386-linux-gnu/libpthread.so.0
 No symbol table info available.
 #8  0x00559dde in clone () from /lib/i386-linux-gnu/libc.so.6
 No symbol table info available.
 .
 Thread 1 (Thread 0xb774d740 (LWP 1820)):
 #0  0x002d4a7d in ?? () from /lib/i386-linux-gnu/libglib-2.0.so.0
 No symbol table info available.
 #1  0x002d3d86 in g_main_context_dispatch () from /lib/i386-linux-gnu/libglib-2.0.so.0
 No symbol table info available.
 #2  0x002d4125 in ?? () from /lib/i386-linux-gnu/libglib-2.0.so.0
 No symbol table info available.
 #3  0x002d456b in g_main_loop_run () from /lib/i386-linux-gnu/libglib-2.0.so.0
 No symbol table info available.
 #4  0x0804bcf0 in ?? ()
 No symbol table info available.
 #5  0x004844d3 in __libc_start_main () from /lib/i386-linux-gnu/libc.so.6
 No symbol table info available.
 #6  0x0804bd25 in ?? ()
 No symbol table info available.
Title: accounts-daemon crashed with SIGSEGV in g_main_context_dispatch()
UpgradeStatus: No upgrade log present (probably fresh install)
```
Seems to be a known bug. See: [https://bugs.launchpad.net/ubuntu/+source/accountsservice/+bug/1212337]("https://bugs.launchpad.net/ubuntu/+source/accountsservice/+bug/1212337"). Is your system fully updated?

---

### Post by Pako Pako on 2013-09-03
> **Toz said:**
> I'm sorry, but I don't know. I did find [this thread]("http://ubuntuforums.org/showthread.php?t=1976776"), but it doesn't really answer how to delete the entry. According to the link to the launchpad entry, they last a few days only.
I did some digging and found out that, at least with pastebin.ubuntu.com, [posts last an *entire year*](http://ubuntuforums.org/showthread.php?t=2144024). This is a little disturbing.

> **Toz said:**
> Seems to be a known bug. See: [https://bugs.launchpad.net/ubuntu/+source/accountsservice/+bug/1212337](https://bugs.launchpad.net/ubuntu/+source/accountsservice/+bug/1212337). Is your system fully updated?
Of course. Not really sure what account-daemon is supposed to do, but the crashing doesn't really seem that bad and I can even tick "choose to ignore" if I want to avoid seeing the error.

Heck, I have another error report being sent now. (I wonder why the Crash Counter is still at '1?')

On the upshot, I have an older kernel installed (PHC, for lower voltage tweaks) and that gets the same account-daemon crashes instead of the post-login freeze, so hey, this bug is a much improved scenario. (Although it is still a bug...)

---

### Post by Pako Pako on 2013-09-13
Is there any way to see what was specifically updated when I last checked "update system?"

The latest 12.04 Xubuntu updates gave my system back to the "hang after login screen" (and removed the TTY1 reboot work-around; TTY2~TTY5 are still available, along with TTY6 now).

The latest-old xsession-errors log end with this a few dozen times:
```
(update-manager:6754): Gtk-WARNING **: /build/buildd/gtk+3.0-3.4.2/./gtk/gtkliststore.c:851: Unable to convert from glong to gint
```


Along with these familiar errors:
```
debconf: DbDriver "passwords" warning: could not open /var/cache/debconf/passwords.dat: Permission denied
xfwm4: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
xfsettingsd: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.
xfce4-session: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.
** (zeitgeist-datahub:2090): WARNING **: zeitgeist-datahub.vala:227: Unable to get name "org.gnome.zeitgeist.datahub" on the bus!
(xfdesktop:2063): GVFS-RemoteVolumeMonitor-WARNING **: Owner :1.47 of volume monitor org.gtk.Private.GduVolumeMonitor disconnected from the bus; removing drives/volumes/mounts
(xfdesktop:2063): GVFS-RemoteVolumeMonitor-WARNING **: Owner :1.48 of volume monitor org.gtk.Private.GPhoto2VolumeMonitor disconnected from the bus; removing drives/volumes/mounts
(xfdesktop:2063): GVFS-RemoteVolumeMonitor-WARNING **: Owner :1.49 of volume monitor org.gtk.Private.AfcVolumeMonitor disconnected from the bus; removing drives/volumes/mounts

** Message: PID 2084 (we are 2084) sent signal 15, shutting down...

(pglgui:3562): GConf-WARNING **: Got Disconnected from DBus.
ICE default IO error handler doing an exit(), pid = 3562, errno = 11
(nm-applet:2084): libappindicator-WARNING **: Unable to send signal for NewStatus: The connection is closed
The application 'wrapper' lost its connection to the display :0.0;
most likely the X server was shut down or you killed/destroyed
the application.
The application 'wrapper' lost its connection to the display :0.0;
most likely the X server was shut down or you killed/destroyed
the application.
wrapper: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
wrapper: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
wrapper: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
xfce4-battery-plugin: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
xfce4-cpugraph-plugin: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
xfce4-cpufreq-plugin: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
```

---

### Post by Toz on 2013-09-13
> **Pako Pako said:**
> Is there any way to see what was specifically updated when I last checked "update system?"
Have a look at the /var/log/apt/history.log log file.

---

### Post by HugoJJ on 2014-03-19
I have similar issue, running 13.10 ubuntu studio on AMD64. Have to logout of X by doing à Ctrl-Alt-F1 then when I log back in with Ctrl-Alt-F7 mouse works fine.

---

