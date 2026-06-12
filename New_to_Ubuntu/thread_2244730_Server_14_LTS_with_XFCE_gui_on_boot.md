---
title: "Server 14 LTS with XFCE gui on boot?"
date: 2014-09-18
forum: New to Ubuntu
---

### Post by chickov2 on 2014-09-18
Hi everyone,

I installed Ubuntu Server 14 LTS XFCE UI for my system, and am trying to access throuth putty as a console, while restarting it does not show a desktop with interface, can anyone help me how can I access the environment so that I can create a normal server desktop so I can configure my database and applications ? Thanks in advance, please look at the message below to resolve my problems...

> 
root@SPOSRVVM006:~# sudo startx

X.Org X Server 1.15.1
Release Date: 2014-04-13
X Protocol Version 11, Revision 0
Build Operating System: Linux 3.2.0-61-generic x86_64 Ubuntu
Current Operating System: Linux SPOSRVVM006 3.13.0-35-generic #62-Ubuntu SMP Fri                                                                              Aug 15 01:58:42 UTC 2014 x86_64
Kernel command line: BOOT_IMAGE=/vmlinuz-3.13.0-35-generic root=/dev/mapper/SPOS                                                                             RVVM006--vg-root ro
Build Date: 30 July 2014  12:21:54AM
xorg-server 2:1.15.1-0ubuntu2.1 (For technical support please see [http://www.ubu](http://www.ubu)                                                                             ntu.com/support)
Current version of pixman: 0.30.2
        Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
        to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.1.log", Time: Thu Sep 18 10:39:22 2014
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
Initializing built-in extension Generic Event Extension
Initializing built-in extension SHAPE
Initializing built-in extension MIT-SHM
Initializing built-in extension XInputExtension
Initializing built-in extension XTEST
Initializing built-in extension BIG-REQUESTS
Initializing built-in extension SYNC
Initializing built-in extension XKEYBOARD
Initializing built-in extension XC-MISC
Initializing built-in extension SECURITY
Initializing built-in extension XINERAMA
Initializing built-in extension XFIXES
Initializing built-in extension RENDER
Initializing built-in extension RANDR
Initializing built-in extension COMPOSITE
Initializing built-in extension DAMAGE
Initializing built-in extension MIT-SCREEN-SAVER
Initializing built-in extension DOUBLE-BUFFER
Initializing built-in extension RECORD
Initializing built-in extension DPMS
Initializing built-in extension Present
Initializing built-in extension DRI3
Initializing built-in extension X-Resource
Initializing built-in extension XVideo
Initializing built-in extension XVideo-MotionCompensation
Initializing built-in extension SELinux
Initializing built-in extension XFree86-VidModeExtension
Initializing built-in extension XFree86-DGA
Initializing built-in extension XFree86-DRI
Initializing built-in extension DRI2
Loading extension GLX
VMware: No 3D enabled (0, Success).
/usr/bin/startxfce4: X server already running on display :1

** (update-notifier:2044): WARNING **: not starting for system user

** (process:2065): WARNING **: volume-control.vala:227: pa_context_connect() fai                                                                             led: OK

process 2072: arguments to dbus_message_new_method_call() were incorrect, assert                                                                             ion "path != NULL" failed in file ../../dbus/dbus-message.c line 1262.
This is normally a bug in some application using the D-Bus library.

** (process:2065): CRITICAL **: volume_control_set_volume_internal: assertion '_                                                                             tmp1_ == PA_CONTEXT_READY' failed

(process:2090): Indicator-Power-WARNING **: Fail to query backlight devices.

** (process:2065): CRITICAL **: file /build/buildd/indicator-sound-12.10.2+14.04                                                                             .20140401/obj-x86_64-linux-gnu/src/volume-control.c: line 1775: uncaught error:                                                                              GDBus.Error:org.freedesktop.DBus.Error.InvalidArgs: No such interface (g-dbus-er                                                                             ror-quark, 16)
No protocol specified
xscreensaver: 10:39:24: Can't open display: :1.0
xscreensaver: 10:39:24: initial effective uid/gid was root/root (0/0)
xscreensaver: 10:39:24: running as nobody/nogroup (65534/65534)

xscreensaver: 10:39:24: This is probably because you're logging in as root.  You
              shouldn't log in as root: you should log in as a normal user,
              and then `su' as needed.  If you insist on logging in as
              root, you will have to turn off X's security features before
              xscreensaver will work.

              Please read the manual and FAQ for more information:

              [http://www.jwz.org/xscreensaver/faq.html](http://www.jwz.org/xscreensaver/faq.html)
              [http://www.jwz.org/xscreensaver/man.html](http://www.jwz.org/xscreensaver/man.html)

/usr/bin/start-pulseaudio-x11: 24: /usr/bin/start-pulseaudio-x11: /usr/bin/pactl                                                                             : not found

** (process:2135): CRITICAL **: bluez.vala:104: GDBus.Error:org.bluez.Error.NoSu                                                                             chAdapter: No such adapter

(xfce4-volumed:2139): xfce4-volumed-WARNING **: xvd_connect_to_pulse: failed to                                                                              connect context: OK

(xfce4-volumed:2139): xfce4-volumed-WARNING **: Unable to initialize pulseaudio                                                                              support, quitting

(xfce4-volumed:2139): GLib-GObject-CRITICAL **: g_object_unref: assertion 'G_IS_                                                                             OBJECT (object)' failed
initctl: UPSTART_SESSION isn't set in the environment. Unable to locate the Upst                                                                             art instance.

(polkit-gnome-authentication-agent-1:2098): polkit-gnome-1-WARNING **: Unable to                                                                              determine the session we are in: No session for pid 2098

** (nm-applet:2131): CRITICAL **: nm_secret_agent_register: assertion 'priv->reg                                                                             istered == FALSE' failed
init: indicator-bluetooth main process ended, respawning
init: indicator-power main process ended, respawning
init: indicator-sound main process ended, respawning
init: indicator-application main process ended, respawning
init: indicator-bluetooth main process ended, respawning
init: indicator-power main process ended, respawning
init: indicator-sound main process ended, respawning
init: indicator-application main process ended, respawning
init: indicator-power main process ended, respawning
init: indicator-bluetooth main process ended, respawning
init: indicator-sound respawning too fast, stopped
init: indicator-application respawning too fast, stopped
init: indicator-power main process ended, respawning
init: indicator-bluetooth main process ended, respawning
init: indicator-power main process ended, respawning
init: indicator-bluetooth main process ended, respawning
init: indicator-power main process ended, respawning
init: indicator-bluetooth main process ended, respawning
init: indicator-power main process ended, respawning
init: indicator-bluetooth main process ended, respawning
init: indicator-power main process ended, respawning
init: indicator-bluetooth main process ended, respawning
init: indicator-power main process ended, respawning
init: indicator-bluetooth main process ended, respawning
init: indicator-power main process ended, respawning
init: indicator-bluetooth main process ended, respawning
init: indicator-power respawning too fast, stopped
init: indicator-bluetooth respawning too fast, stopped
Loading configuration plugins
blueman-applet version 1.23 starting
Stale PID, overwriting
Using gconf config backend
Using gconf config backend
Using gconf config backend
Using gconf config backend
Using gconf config backend
Using gconf config backend
Using gconf config backend
Using gconf config backend
Using gconf config backend
Using gconf config backend



---

### Post by Bucky Ball on 2014-09-18
startxfce4

Try that. Is that the entire output you've posted? It ends there?

Just to clarify, you had Ubuntu 14.04 Server edition installed and you installed xfce4 desktop environment?

---

