---
title: "To roll back X on Hardy?"
date: 2008-05-13
forum: New to Ubuntu
---

### Post by GepettoBR on 2008-05-13
I've been using Gutsy on my laptop since early January, and in spite of having some trouble to configure TV-Out, my ATI video card worked perfectly. Since the "upgrade" to Hardy, not only does the TV-Out not work, but now the X server randomly crashes every few dozen minutes, leaving me with a black screen and a mouse pointer. Running displayconfig-gtk (which was even removed from Hardy's System menu) causes X to revert to the generic VESA driver on the next login. In both versions I used the open "ati" driver, and absolutely nothing else changed: right before the update it worked, right after it didn't

The fgrlx driver never worked in Gutsy and still doesn't in Hardy. The "radeon" driver, in Gutsy, worked fine with everything but the TV-Out, now in Hardy it doesn't work at all. I've tried manually editing xorg.conf, but since I'm a world-class newbie, it only resulted in more crashing, so I've restored the original file. Google has provided me with no useful information. I even waited a few weeks in the hopes that a system update would fix this, but so far nothing has come to my aid.

So, can anyone help me with this?

P.S.: Just in case it matters, Firefox was open every time X crashed, and most of the crashes happened while Firefox was loading a new page, but other times I was in the middle of reading a web page and it crashed.

P.S.2: The vertical center of the screen goes lots of pixels down when it crashes. If I move the mouse all the way up, the pointer stops slightly above the middle of the screen, and if I move it to the bottom of the screen it reappears at the top, and goes down to the same spot where it stops going up.

Thanks in advance for all suggestions.

---

### Post by peitschie on 2008-05-13
Hmm.  Those sound frustrating!

For the graphics driver, I would recommend you use a utility called "Envy" which is now available from the repos:

```
sudo apt-get install envyng-gtk
```

This will put a short cut in Applications > System Tools.  This utility will download, compile and install the latest Ati graphics driver which may help some of your issues.

As for X crashing... that one seems odd.  Are there any messages in /var/log/messages or /var/log/debug or /var/log/syslog that seem relevant?
You can view these by running the following in a terminal
```
gedit /var/log/messages
```

Are you able to do a clean install of Hardy?  The X stability issues may be caused by the upgrade process.  I have often found upgrading between versions of Ubuntu to be very erratic at best, and usually end up reinstalling which seems to fix many of my issues.

---

### Post by GepettoBR on 2008-05-14
> **peitschie said:**
> Hmm.  Those sound frustrating!

For the graphics driver, I would recommend you use a utility called "Envy" which is now available from the repos:

```
sudo apt-get install envyng-gtk
```

This will put a short cut in Applications > System Tools.  This utility will download, compile and install the latest Ati graphics driver which may help some of your issues.

As for X crashing... that one seems odd.  Are there any messages in /var/log/messages or /var/log/debug or /var/log/syslog that seem relevant?
You can view these by running the following in a terminal
```
gedit /var/log/messages
```

Are you able to do a clean install of Hardy?  The X stability issues may be caused by the upgrade process.  I have often found upgrading between versions of Ubuntu to be very erratic at best, and usually end up reinstalling which seems to fix many of my issues.

Installing the driver through EnvyNG also crashed the X server, so I had to revert to the "ati" driver again. Here are the outputs of the three log files:

/var/log/messages:```
May  6 14:44:44 Dragonfly syslogd 1.5.0#1ubuntu1: restart.
May  6 15:13:40 Dragonfly -- MARK --
May  6 15:33:40 Dragonfly -- MARK --
May  6 15:44:50 Dragonfly gnome-power-manager: (paulo) Doing nothing. Reason: The lid has been closed on ac power.
May  6 16:13:40 Dragonfly -- MARK --
May  6 16:30:31 Dragonfly gnome-power-manager: (paulo) Doing nothing. Reason: The lid has been closed on ac power.
May  6 16:53:40 Dragonfly -- MARK --
May  6 17:13:40 Dragonfly -- MARK --
May  6 17:29:04 Dragonfly pcscd: pcscdaemon.c:578:signal_trap() Preparing for suicide
May  6 17:29:05 Dragonfly pcscd: readerfactory.c:1382:RFCleanupReaders() entering cleaning function
May  6 17:29:05 Dragonfly pcscd: pcscdaemon.c:538:at_exit() cleaning /var/run/pcscd
May  6 17:29:05 Dragonfly exiting on signal 15
```
/var/log/debug:```
May  6 16:18:40 Dragonfly NetworkManager: <debug> [1210101520.623245] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_62a_0_noserial_if0_logicaldev_input'). 
May  6 16:18:40 Dragonfly NetworkManager: <debug> [1210101520.634147] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_62a_0_noserial_if0'). 
May  6 16:18:40 Dragonfly NetworkManager: <debug> [1210101520.642352] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_62a_0_noserial'). 
May  6 16:18:45 Dragonfly NetworkManager: <debug> [1210101525.397066] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_79_6_noserial'). 
May  6 16:18:45 Dragonfly NetworkManager: <debug> [1210101525.851644] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_79_6_noserial_if0'). 
May  6 16:18:46 Dragonfly NetworkManager: <debug> [1210101526.251314] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_79_6_noserial_if0_logicaldev_input'). 
May  6 16:30:35 Dragonfly NetworkManager: <debug> [1210102235.861458] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_79_6_noserial_if0_logicaldev_input'). 
May  6 16:30:35 Dragonfly NetworkManager: <debug> [1210102235.882863] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_79_6_noserial_if0'). 
May  6 16:30:35 Dragonfly NetworkManager: <debug> [1210102235.897402] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_79_6_noserial'). 
May  6 16:30:57 Dragonfly NetworkManager: <debug> [1210102257.386583] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_62a_0_noserial'). 
May  6 16:30:57 Dragonfly NetworkManager: <debug> [1210102257.805659] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_62a_0_noserial_if0'). 
May  6 16:30:58 Dragonfly NetworkManager: <debug> [1210102258.185161] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_62a_0_noserial_if0_logicaldev_input'). 
```
/var/log/syslog:```
May  6 13:53:40 Dragonfly syslogd 1.5.0#1ubuntu1: restart.
May  6 13:53:40 Dragonfly anacron[9390]: Job `cron.daily' terminated (exit status: 1) (mailing output)
May  6 13:53:40 Dragonfly anacron[9390]: Job `cron.weekly' started
May  6 13:53:40 Dragonfly postfix/sendmail[1570]: fatal: open /etc/postfix/main.cf: No such file or directory
May  6 13:53:42 Dragonfly anacron[9390]: Tried to mail output of job `cron.daily', but mailer process (/usr/sbin/sendmail) exited with ststus 75
May  6 13:53:42 Dragonfly anacron[1574]: Updated timestamp for job `cron.weekly' to 2008-05-06
May  6 14:03:01 Dragonfly /USR/SBIN/CRON[8281]: (root) CMD (/usr/bin/test -x /usr/sbin/tz-brasil && /usr/sbin/tz-brasil)
May  6 14:13:40 Dragonfly -- MARK --
May  6 14:17:01 Dragonfly /USR/SBIN/CRON[18401]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May  6 14:33:01 Dragonfly /USR/SBIN/CRON[29826]: (root) CMD (/usr/bin/test -x /usr/sbin/tz-brasil && /usr/sbin/tz-brasil)
May  6 14:44:44 Dragonfly syslogd 1.5.0#1ubuntu1: restart.
May  6 14:44:44 Dragonfly anacron[9390]: Job `cron.weekly' terminated
May  6 14:44:44 Dragonfly anacron[9390]: Normal exit (2 jobs run)
May  6 15:03:02 Dragonfly /USR/SBIN/CRON[19262]: (root) CMD (/usr/bin/test -x /usr/sbin/tz-brasil && /usr/sbin/tz-brasil)
May  6 15:13:40 Dragonfly -- MARK --
May  6 15:17:01 Dragonfly /USR/SBIN/CRON[29289]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May  6 15:33:01 Dragonfly /USR/SBIN/CRON[8114]: (root) CMD (/usr/bin/test -x /usr/sbin/tz-brasil && /usr/sbin/tz-brasil)
May  6 15:44:50 Dragonfly gnome-power-manager: (paulo) Doing nothing. Reason: The lid has been closed on ac power.
May  6 16:03:05 Dragonfly /USR/SBIN/CRON[29784]: (root) CMD (/usr/bin/test -x /usr/sbin/tz-brasil && /usr/sbin/tz-brasil)
May  6 16:13:40 Dragonfly -- MARK --
May  6 16:17:01 Dragonfly /USR/SBIN/CRON[7224]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May  6 16:18:40 Dragonfly NetworkManager: <debug> [1210101520.623245] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_62a_0_noserial_if0_logicaldev_input'). 
May  6 16:18:40 Dragonfly NetworkManager: <debug> [1210101520.634147] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_62a_0_noserial_if0'). 
May  6 16:18:40 Dragonfly NetworkManager: <debug> [1210101520.642352] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_62a_0_noserial'). 
May  6 16:18:45 Dragonfly NetworkManager: <debug> [1210101525.397066] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_79_6_noserial'). 
May  6 16:18:45 Dragonfly NetworkManager: <debug> [1210101525.851644] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_79_6_noserial_if0'). 
May  6 16:18:46 Dragonfly NetworkManager: <debug> [1210101526.251314] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_79_6_noserial_if0_logicaldev_input'). 
May  6 16:30:31 Dragonfly gnome-power-manager: (paulo) Doing nothing. Reason: The lid has been closed on ac power.
May  6 16:30:35 Dragonfly NetworkManager: <debug> [1210102235.861458] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_79_6_noserial_if0_logicaldev_input'). 
May  6 16:30:35 Dragonfly NetworkManager: <debug> [1210102235.882863] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_79_6_noserial_if0'). 
May  6 16:30:35 Dragonfly NetworkManager: <debug> [1210102235.897402] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_79_6_noserial'). 
May  6 16:30:57 Dragonfly NetworkManager: <debug> [1210102257.386583] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_62a_0_noserial'). 
May  6 16:30:57 Dragonfly NetworkManager: <debug> [1210102257.805659] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_62a_0_noserial_if0'). 
May  6 16:30:58 Dragonfly NetworkManager: <debug> [1210102258.185161] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_62a_0_noserial_if0_logicaldev_input'). 
May  6 16:33:02 Dragonfly /USR/SBIN/CRON[18620]: (root) CMD (/usr/bin/test -x /usr/sbin/tz-brasil && /usr/sbin/tz-brasil)
May  6 16:49:37 Dragonfly ntpd[10510]: no servers reachable
May  6 16:58:10 Dragonfly ntpd[10510]: synchronized to 91.189.94.4, stratum 2
May  6 17:03:01 Dragonfly /USR/SBIN/CRON[7450]: (root) CMD (/usr/bin/test -x /usr/sbin/tz-brasil && /usr/sbin/tz-brasil)
May  6 17:06:44 Dragonfly ntpd[10510]: time reset -0.140107 s
May  6 17:15:42 Dragonfly ntpd[10510]: synchronized to 91.189.94.4, stratum 2
May  6 17:17:01 Dragonfly /USR/SBIN/CRON[17609]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May  6 17:28:50 Dragonfly console-kit-daemon[8631]: WARNING: Unable to activate console: No such device or address 
May  6 17:28:51 Dragonfly init: tty4 main process (7369) killed by TERM signal
May  6 17:28:51 Dragonfly init: tty5 main process (7370) killed by TERM signal
May  6 17:28:51 Dragonfly init: tty2 main process (7378) killed by TERM signal
May  6 17:28:51 Dragonfly init: tty3 main process (7383) killed by TERM signal
May  6 17:28:51 Dragonfly init: tty6 main process (7388) killed by TERM signal
May  6 17:28:51 Dragonfly init: tty1 main process (9521) killed by TERM signal
May  6 17:28:53 Dragonfly atieventsd[7971]: Closing acpid connection 
May  6 17:28:53 Dragonfly atieventsd[7971]: Closing control socket 
May  6 17:28:53 Dragonfly atieventsd[7971]: ATI External Events Daemon shutting down 
May  6 17:29:04 Dragonfly pcscd: pcscdaemon.c:578:signal_trap() Preparing for suicide
May  6 17:29:05 Dragonfly pcscd: readerfactory.c:1382:RFCleanupReaders() entering cleaning function
May  6 17:29:05 Dragonfly pcscd: pcscdaemon.c:538:at_exit() cleaning /var/run/pcscd
May  6 17:29:05 Dragonfly exiting on signal 15
```

Sorry for taking so long to reply, my day was really rushed today.

I don't think I can risk a clean install. My only DVD drive is on the verge of breaking, and when I first installed Gutsy I had to keep moving the laptop from cold stone surface to cold stone surface evey two or three minutes to keep the drive from overheating and stopping mid-read-cycle. It took me four tries, and I haven't used the drive since.

---

### Post by peitschie on 2008-05-14
Hmm..  that presents an interesting case.  From the current logs I can assert that it isn't some part of the computer shutting things down.  You can see in the syslog that the first event starting the shutdown is
```
May  6 17:28:50 Dragonfly console-kit-daemon[8631]: WARNING: Unable to activate console: No such device or address 
``` and the first in the message log is ```
May  6 17:29:04 Dragonfly pcscd: pcscdaemon.c:578:signal_trap() Preparing for suicide
``` which is almost 14s later (a long time in computer terms).  We need to look else where...

Can you grab the logs from the Xorg.0.log?  You should be able to post the full thing from that.  It'd be handy to see the log of the crashing Envy driver as well (I realise this is a bit of a pain but it might be worth it). 

If your primary issue is the dvd drive... are you able to boot from a USB?  If so, check out these instructions: [http://www.teamteabag.com/2008/03/07/install-ubuntu-804-hardy-heron-from-usb/](http://www.teamteabag.com/2008/03/07/install-ubuntu-804-hardy-heron-from-usb/), which cover how to install hardy from a USB drive ;)... Could be very handy!

---

### Post by GepettoBR on 2008-05-14
Here's my Xorg.0.log: ```
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
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9)
Current Operating System: Linux Dragonfly 2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686
Build Date: 15 April 2008  05:26:17PM
 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed May 14 22:09:17 2008
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
	Using the first mouse device.
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
(II) PCI: 00:00:0: chip 1002,cab2 card 0000,0000 rev 02 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 1002,7010 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:06:0: chip 10b9,5451 card 0e11,0056 rev 02 class 04,01,00 hdr 00
(II) PCI: 00:07:0: chip 10b9,1533 card 10b9,1533 rev 00 class 06,01,00 hdr 00
(II) PCI: 00:0a:0: chip 104c,ac41 card 1000,0000 rev 02 class 06,07,00 hdr 82
(II) PCI: 00:0a:1: chip 104c,8017 card 0e11,0056 rev 02 class 0c,00,10 hdr 80
(II) PCI: 00:0b:0: chip 10ec,8139 card 0e11,0056 rev 20 class 02,00,00 hdr 00
(II) PCI: 00:0c:0: chip 14f1,2f00 card 0e11,8d88 rev 01 class 07,80,00 hdr 00
(II) PCI: 00:10:0: chip 10b9,5229 card 10b9,5229 rev c4 class 01,01,fa hdr 00
(II) PCI: 00:11:0: chip 10b9,7101 card 10b9,7101 rev 00 class 06,80,00 hdr 00
(II) PCI: 00:13:0: chip 1033,0035 card 0e11,0056 rev 41 class 0c,03,10 hdr 80
(II) PCI: 00:13:1: chip 1033,0035 card 0e11,0056 rev 41 class 0c,03,10 hdr 00
(II) PCI: 00:13:2: chip 1033,00e0 card 0e11,0056 rev 02 class 0c,03,20 hdr 00
(II) PCI: 01:05:0: chip 1002,4337 card 0e11,0056 rev 00 class 03,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,2), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000c (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[1] -1	0	0x0000a400 - 0x0000a4ff (0x100) IX[B]
	[2] -1	0	0x0000a800 - 0x0000a8ff (0x100) IX[B]
	[3] -1	0	0x0000ac00 - 0x0000acff (0x100) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xf0300000 - 0xf03fffff (0x100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xf8000000 - 0xfbffffff (0x4000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:7:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) PCI-to-CardBus bridge:
(II) Bus 2: bridge is at (0:10:0), (0,2,5), BCTRL: 0x05c0 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[1] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0x44000000 - 0x47ffffff (0x4000000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0x40000000 - 0x43ffffff (0x4000000) MX[B]
(--) PCI:*(1:5:0) ATI Technologies Inc Radeon IGP 330M/340M/350M rev 0, Mem @ 0xf8000000/26, 0xf0300000/16, I/O @ 0xa000/8
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
(II) PCI Memory resource overlap reduced 0xf4000000 from 0xf7ffffff to 0xf3ffffff
(II) PCI Memory resource overlap reduced 0xf0600000 from 0xf0600fff to 0xf05fffff
(II) Active PCI resource ranges:
	[0] -1	0	0xf0018c00 - 0xf0018cff (0x100) MX[B]
	[1] -1	0	0xf0017000 - 0xf0017fff (0x1000) MX[B]
	[2] -1	0	0xf0016000 - 0xf0016fff (0x1000) MX[B]
	[3] -1	0	0xf0000000 - 0xf000ffff (0x10000) MX[B]
	[4] -1	0	0xf0018800 - 0xf00188ff (0x100) MX[B]
	[5] -1	0	0xf0010000 - 0xf0013fff (0x4000) MX[B]
	[6] -1	0	0xf0018000 - 0xf00187ff (0x800) MX[B]
	[7] -1	0	0xf0014000 - 0xf0014fff (0x1000) MX[B]
	[8] -1	0	0xf0600000 - 0xf05fffff (0x0) MX[B]O
	[9] -1	0	0xf4000000 - 0xf3ffffff (0x0) MX[B]O
	[10] -1	0	0xf0300000 - 0xf030ffff (0x10000) MX[B](B)
	[11] -1	0	0xf8000000 - 0xfbffffff (0x4000000) MX[B](B)
	[12] -1	0	0x00008080 - 0x0000808f (0x10) IX[B]
	[13] -1	0	0x00008090 - 0x00008097 (0x8) IX[B]
	[14] -1	0	0x00009000 - 0x000090ff (0x100) IX[B]
	[15] -1	0	0x00008400 - 0x000084ff (0x100) IX[B]
	[16] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xf0018c00 - 0xf0018cff (0x100) MX[B]
	[1] -1	0	0xf0017000 - 0xf0017fff (0x1000) MX[B]
	[2] -1	0	0xf0016000 - 0xf0016fff (0x1000) MX[B]
	[3] -1	0	0xf0000000 - 0xf000ffff (0x10000) MX[B]
	[4] -1	0	0xf0018800 - 0xf00188ff (0x100) MX[B]
	[5] -1	0	0xf0010000 - 0xf0013fff (0x4000) MX[B]
	[6] -1	0	0xf0018000 - 0xf00187ff (0x800) MX[B]
	[7] -1	0	0xf0014000 - 0xf0014fff (0x1000) MX[B]
	[8] -1	0	0xf0600000 - 0xf05fffff (0x0) MX[B]O
	[9] -1	0	0xf4000000 - 0xf3ffffff (0x0) MX[B]O
	[10] -1	0	0xf0300000 - 0xf030ffff (0x10000) MX[B](B)
	[11] -1	0	0xf8000000 - 0xfbffffff (0x4000000) MX[B](B)
	[12] -1	0	0x00008080 - 0x0000808f (0x10) IX[B]
	[13] -1	0	0x00008090 - 0x00008097 (0x8) IX[B]
	[14] -1	0	0x00009000 - 0x000090ff (0x100) IX[B]
	[15] -1	0	0x00008400 - 0x000084ff (0x100) IX[B]
	[16] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B](B)
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
	[4] -1	0	0xf0018c00 - 0xf0018cff (0x100) MX[B]
	[5] -1	0	0xf0017000 - 0xf0017fff (0x1000) MX[B]
	[6] -1	0	0xf0016000 - 0xf0016fff (0x1000) MX[B]
	[7] -1	0	0xf0000000 - 0xf000ffff (0x10000) MX[B]
	[8] -1	0	0xf0018800 - 0xf00188ff (0x100) MX[B]
	[9] -1	0	0xf0010000 - 0xf0013fff (0x4000) MX[B]
	[10] -1	0	0xf0018000 - 0xf00187ff (0x800) MX[B]
	[11] -1	0	0xf0014000 - 0xf0014fff (0x1000) MX[B]
	[12] -1	0	0xf0600000 - 0xf05fffff (0x0) MX[B]O
	[13] -1	0	0xf4000000 - 0xf3ffffff (0x0) MX[B]O
	[14] -1	0	0xf0300000 - 0xf030ffff (0x10000) MX[B](B)
	[15] -1	0	0xf8000000 - 0xfbffffff (0x4000000) MX[B](B)
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x00008080 - 0x0000808f (0x10) IX[B]
	[19] -1	0	0x00008090 - 0x00008097 (0x8) IX[B]
	[20] -1	0	0x00009000 - 0x000090ff (0x100) IX[B]
	[21] -1	0	0x00008400 - 0x000084ff (0x100) IX[B]
	[22] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B](B)
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "freetype" will be loaded by default.
(II) "record" will be loaded by default.
(II) "dri" will be loaded. This was enabled by default and also specified in the config file.
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "v4l"
(II) Loading /usr/lib/xorg/modules/drivers//v4l_drv.so
(II) Module v4l: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 0.1.1
	ABI class: X.Org Video Driver, version 2.0
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
(II) LoadModule: "ati"
(II) Loading /usr/lib/xorg/modules/drivers//ati_drv.so
(II) Module ati: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 6.8.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 2.0
(II) LoadModule: "radeon"
(II) Loading /usr/lib/xorg/modules/drivers//radeon_drv.so
(II) Module radeon: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 4.3.0
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
(II) v4l driver for Video4Linux
(II) RADEON: Driver for ATI Radeon chipsets:
	ATI Radeon Mobility X600 (M24) 3150 (PCIE),
	ATI Radeon Mobility X300 (M24) 3152 (PCIE),
	ATI FireGL M24 GL 3154 (PCIE), ATI Radeon X600 (RV380) 3E50 (PCIE),
	ATI FireGL V3200 (RV380) 3E54 (PCIE), ATI Radeon IGP320 (A3) 4136,
	ATI Radeon IGP330/340/350 (A4) 4137, ATI Radeon 9500 AD (AGP),
	ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
	ATI FireGL Z1 AG (AGP), ATI Radeon 9800SE AH (AGP),
	ATI Radeon 9800 AI (AGP), ATI Radeon 9800 AJ (AGP),
	ATI FireGL X2 AK (AGP), ATI Radeon 9600 AP (AGP),
	ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
	ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP), ATI Radeon 9650,
	ATI FireGL RV360 AV (AGP), ATI Radeon 7000 IGP (A4+) 4237,
	ATI Radeon 8500 AIW BB (AGP), ATI Radeon 8500 AIW BC (AGP),
	ATI Radeon IGP320M (U1) 4336, ATI Radeon IGP330M/340M/350M (U2) 4337,
	ATI Radeon Mobility 7000 IGP 4437, ATI Radeon 9000/PRO If (AGP/PCI),
	ATI Radeon 9000 Ig (AGP/PCI), ATI Radeon X800 (R420) JH (AGP),
	ATI Radeon X800PRO (R420) JI (AGP),
	ATI Radeon X800SE (R420) JJ (AGP), ATI Radeon X800 (R420) JK (AGP),
	ATI Radeon X800 (R420) JL (AGP), ATI FireGL X3 (R420) JM (AGP),
	ATI Radeon Mobility 9800 (M18) JN (AGP),
	ATI Radeon X800 SE (R420) (AGP), ATI Radeon X800XT (R420) JP (AGP),
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
	ATI Mobility Radeon X700 (M26) (PCIE), ATI Radeon 9100 IGP (A5) 5834,
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
	ATI Radeon X550XTX (RV370) 5657 (PCIE),
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
	ATI Mobility Radeon X1700, ATI  Radeon X2300HD,
	ATI Mobility Radeon HD 2300, ATI Mobility Radeon HD 2300,
	ATI Radeon X1950, ATI Radeon X1900, ATI Radeon X1950,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI AMD Stream Processor, ATI Radeon X1900, ATI Radeon X1950,
	ATI RV560, ATI RV560, ATI Mobility Radeon X1900, ATI RV560,
	ATI Radeon X1950 GT, ATI RV570, ATI RV570, ATI ATI FireGL V7400,
	ATI RV560, ATI Radeon X1650, ATI Radeon X1650, ATI RV560,
	ATI Radeon 9100 PRO IGP 7834, ATI Radeon Mobility 9200 IGP 7835,
	ATI Radeon X1200, ATI Radeon X1200, ATI RS740, ATI RS740M, ATI RS740,
	ATI RS740M, ATI Radeon HD 2900 XT, ATI Radeon HD 2900 XT,
	ATI Radeon HD 2900 XT, ATI Radeon HD 2900 Pro, ATI Radeon HD 2900 GT,
	ATI FireGL V8650, ATI FireGL V8600, ATI FireGL V7600, ATI RV610,
	ATI Radeon HD 2400 XT, ATI Radeon HD 2400 Pro,
	ATI ATI Radeon HD 2400 PRO AGP, ATI FireGL V4000, ATI RV610,
	ATI ATI Radeon HD 2350, ATI Mobility Radeon HD 2400 XT,
	ATI Mobility Radeon HD 2400, ATI ATI RADEON E2400, ATI RV610,
	ATI RV670, ATI Radeon HD3870, ATI Radeon HD3850, ATI RV670,
	ATI Radeon HD3870 X2, ATI FireGL V7700, ATI RV630,
	ATI Mobility Radeon HD 2600, ATI Mobility Radeon HD 2600 XT,
	ATI ATI Radeon HD 2600 XT AGP, ATI ATI Radeon HD 2600 Pro AGP,
	ATI Radeon HD 2600 XT, ATI Radeon HD 2600 Pro, ATI Gemini RV630,
	ATI Gemini ATI Mobility Radeon HD 2600 XT, ATI FireGL V5600,
	ATI FireGL V3600, ATI ATI Radeon HD 2600 LE
(II) Primary Device is: PCI 01:05:0
(--) Chipset ATI Radeon IGP330M/340M/350M (U2) 4337 found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xf0018c00 - 0xf0018cff (0x100) MX[B]
	[5] -1	0	0xf0017000 - 0xf0017fff (0x1000) MX[B]
	[6] -1	0	0xf0016000 - 0xf0016fff (0x1000) MX[B]
	[7] -1	0	0xf0000000 - 0xf000ffff (0x10000) MX[B]
	[8] -1	0	0xf0018800 - 0xf00188ff (0x100) MX[B]
	[9] -1	0	0xf0010000 - 0xf0013fff (0x4000) MX[B]
	[10] -1	0	0xf0018000 - 0xf00187ff (0x800) MX[B]
	[11] -1	0	0xf0014000 - 0xf0014fff (0x1000) MX[B]
	[12] -1	0	0xf0600000 - 0xf05fffff (0x0) MX[B]O
	[13] -1	0	0xf4000000 - 0xf3ffffff (0x0) MX[B]O
	[14] -1	0	0xf0300000 - 0xf030ffff (0x10000) MX[B](B)
	[15] -1	0	0xf8000000 - 0xfbffffff (0x4000000) MX[B](B)
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x00008080 - 0x0000808f (0x10) IX[B]
	[19] -1	0	0x00008090 - 0x00008097 (0x8) IX[B]
	[20] -1	0	0x00009000 - 0x000090ff (0x100) IX[B]
	[21] -1	0	0x00008400 - 0x000084ff (0x100) IX[B]
	[22] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B](B)
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xf0018c00 - 0xf0018cff (0x100) MX[B]
	[5] -1	0	0xf0017000 - 0xf0017fff (0x1000) MX[B]
	[6] -1	0	0xf0016000 - 0xf0016fff (0x1000) MX[B]
	[7] -1	0	0xf0000000 - 0xf000ffff (0x10000) MX[B]
	[8] -1	0	0xf0018800 - 0xf00188ff (0x100) MX[B]
	[9] -1	0	0xf0010000 - 0xf0013fff (0x4000) MX[B]
	[10] -1	0	0xf0018000 - 0xf00187ff (0x800) MX[B]
	[11] -1	0	0xf0014000 - 0xf0014fff (0x1000) MX[B]
	[12] -1	0	0xf0600000 - 0xf05fffff (0x0) MX[B]O
	[13] -1	0	0xf4000000 - 0xf3ffffff (0x0) MX[B]O
	[14] -1	0	0xf0300000 - 0xf030ffff (0x10000) MX[B](B)
	[15] -1	0	0xf8000000 - 0xfbffffff (0x4000000) MX[B](B)
	[16] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[17] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[18] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x00008080 - 0x0000808f (0x10) IX[B]
	[22] -1	0	0x00008090 - 0x00008097 (0x8) IX[B]
	[23] -1	0	0x00009000 - 0x000090ff (0x100) IX[B]
	[24] -1	0	0x00008400 - 0x000084ff (0x100) IX[B]
	[25] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B](B)
	[26] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[27] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) RADEON(0): MMIO registers at 0x00000000f0300000: size 64KB
(II) RADEON(0): PCI bus 1 card 5 func 0
(**) RADEON(0): Depth 24, (--) framebuffer bpp 32
(II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) RADEON(0): Default visual is TrueColor
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 0.1.0
	ABI class: X.Org Video Driver, version 2.0
(II) RADEON(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(==) RADEON(0): RGB weight 888
(II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(II) RADEON(0): initializing int10
(II) RADEON(0): Primary V_BIOS segment is: 0xc000
(--) RADEON(0): Chipset: "ATI Radeon IGP330M/340M/350M (U2) 4337" (ChipID = 0x4337)
(--) RADEON(0): Linear framebuffer at 0x00000000f8000000
(II) RADEON(0): AGP card detected
(II) RADEON(0): Legacy BIOS detected
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenByBusid: Searching for BusID pci:0000:01:05.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: drmOpenMinor returns 7
drmOpenByBusid: drmGetBusid reports pci:0000:01:05.0
(II) RADEON(0): [dri] Found DRI library version 1.3.0 and kernel module version 1.28.0
(==) RADEON(0): Page Flipping disabled
(II) RADEON(0): Will try to use DMA for Xv image transfers
(II) RADEON(0): Detected total video RAM=32768K, accessible=32768K (PCI BAR=65536K)
(--) RADEON(0): Mapped VideoRAM: 32768 kByte (64 bit DDR SDRAM)
(II) RADEON(0): Color tiling enabled by default
(II) RADEON(0): Max desktop size set to 1024x768
(II) RADEON(0): For a larger or smaller max desktop size, add a Virtual line to your xorg.conf
(II) RADEON(0): If you are having trouble with 3D, reduce the desktop size by adjusting the Virtual line to your xorg.conf
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module "ddc" already built-in
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"(II) Module "i2c" already built-in
(II) RADEON(0): ref_freq: 19186, min_out_pll: 12000, max_out_pll: 35000, min_in_pll: 40, max_in_pll: 3000, xclk: 13330, sclk: 133.300003, mclk: 183.000000
(II) RADEON(0): PLL parameters: rf=19186 rd=426 min=12000 max=35000; xclk=13330
(WW) RADEON(0): LCD DDC Info Table found!
(II) RADEON(0): Bios Connector table: 
(II) RADEON(0): Port0: DDCType-0x60, DACType-2, TMDSType-1, ConnectorType-1
(II) RADEON(0): Port4: DDCType-0x1a0, DACType-0, TMDSType-0, ConnectorType-7
(II) RADEON(0): Port5: DDCType-0x0, DACType-2, TMDSType-0, ConnectorType-5
(II) RADEON(0): Output VGA-0 using monitor section Configured Monitor
(II) RADEON(0): I2C bus "VGA-0" initialized.
(II) RADEON(0): Output LVDS has no monitor section
(II) RADEON(0): Panel ID string: AUO B141XG03
(II) RADEON(0): Panel Size from BIOS: 1024x768
(II) RADEON(0): BIOS provided dividers will be used.
(WW) RADEON(0): LVDS Info:
XRes: 1024, YRes: 768, DotClock: 65000
HBlank: 296, HOverPlus: 16, HSyncWidth: 136
VBlank: 35, VOverPlus: 3, VSyncWidth: 6
(II) RADEON(0): I2C bus "LVDS" initialized.
(II) RADEON(0): Output S-video has no monitor section
(II) RADEON(0): Default TV standard: NTSC
(II) RADEON(0): TV standards supported by chip: NTSC PAL PAL-M NTSC-J 
(II) RADEON(0): Port0:
 Monitor   -- AUTO
 Connector -- VGA
 DAC Type  -- TVDAC/ExtDAC
 TMDS Type -- None
 DDC Type  -- 0x60
(II) RADEON(0): Port1:
 Monitor   -- AUTO
 Connector -- LVDS
 DAC Type  -- None
 TMDS Type -- None
 DDC Type  -- 0x1a0
(II) RADEON(0): Port2:
 Monitor   -- AUTO
 Connector -- STV
 DAC Type  -- TVDAC/ExtDAC
 TMDS Type -- None
 DDC Type  -- 0x0
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): EDID vendor "SNY", prod id 13056
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1053 1189 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "1280x768"x0.0   79.50  1280 1344 1472 1664  768 771 778 798 -hsync +vsync (47.8 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Modeline "1024x768"x74.9   82.00  1024 1088 1192 1360  768 771 775 805 -hsync +vsync (60.3 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: SNY  Model: 3300  Serial#: 0
(II) RADEON(0): Year: 2006  Week: 35
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate
(II) RADEON(0): Max H-Image Size [cm]: H-Size may change,  V-Size may change
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.640 redY: 0.333   greenX: 0.275 greenY: 0.595
(II) RADEON(0): blueX: 0.143 blueY: 0.064   whiteX: 0.280 whiteY: 0.290
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1024  vsize 768  refresh: 75  vid: 20321
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 65.0 MHz   Image Size:  0 x 0 mm
(II) RADEON(0): h_active: 1024  h_sync: 1053  h_sync_end 1189 h_blank_end 1344 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 79.5 MHz   Image Size:  0 x 0 mm
(II) RADEON(0): h_active: 1280  h_sync: 1344  h_sync_end 1472 h_blank_end 1664 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 778 v_blanking: 798 v_border: 0
(II) RADEON(0): Ranges: V min: 58  V max: 62 Hz, H min: 30  H max: 50 kHz, PixClock max 80 MHz
(II) RADEON(0): Monitor name: KLV-S23A10T
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff004dd9003300000000
(II) RADEON(0): 	23100103080000780ad9ada355469824
(II) RADEON(0): 	10474aadc800614f0101010101010101
(II) RADEON(0): 	01010101010164190040410026301d88
(II) RADEON(0): 	36000000000000180e1f008051001e30
(II) RADEON(0): 	4080370000000000001c000000fd003a
(II) RADEON(0): 	3e1e3208000a202020202020000000fc
(II) RADEON(0): 	004b4c562d533233413130540a20006d
finished output detect: 0
(II) RADEON(0): I2C device "LVDS:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "LVDS:ddc2" removed.
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 0
(II) RADEON(0): Detected non-DDC Monitor Type: 2
finished output detect: 1
finished output detect: 2
finished all detect
before xf86InitialConfiguration
(II) RADEON(0): EDID vendor "SNY", prod id 13056
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1053 1189 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "1280x768"x0.0   79.50  1280 1344 1472 1664  768 771 778 798 -hsync +vsync (47.8 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Modeline "1024x768"x74.9   82.00  1024 1088 1192 1360  768 771 775 805 -hsync +vsync (60.3 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: SNY  Model: 3300  Serial#: 0
(II) RADEON(0): Year: 2006  Week: 35
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate
(II) RADEON(0): Max H-Image Size [cm]: H-Size may change,  V-Size may change
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.640 redY: 0.333   greenX: 0.275 greenY: 0.595
(II) RADEON(0): blueX: 0.143 blueY: 0.064   whiteX: 0.280 whiteY: 0.290
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1024  vsize 768  refresh: 75  vid: 20321
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 65.0 MHz   Image Size:  0 x 0 mm
(II) RADEON(0): h_active: 1024  h_sync: 1053  h_sync_end 1189 h_blank_end 1344 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 79.5 MHz   Image Size:  0 x 0 mm
(II) RADEON(0): h_active: 1280  h_sync: 1344  h_sync_end 1472 h_blank_end 1664 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 778 v_blanking: 798 v_border: 0
(II) RADEON(0): Ranges: V min: 58  V max: 62 Hz, H min: 30  H max: 50 kHz, PixClock max 80 MHz
(II) RADEON(0): Monitor name: KLV-S23A10T
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff004dd9003300000000
(II) RADEON(0): 	23100103080000780ad9ada355469824
(II) RADEON(0): 	10474aadc800614f0101010101010101
(II) RADEON(0): 	01010101010164190040410026301d88
(II) RADEON(0): 	36000000000000180e1f008051001e30
(II) RADEON(0): 	4080370000000000001c000000fd003a
(II) RADEON(0): 	3e1e3208000a202020202020000000fc
(II) RADEON(0): 	004b4c562d533233413130540a20006d
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "SNY", prod id 13056
(II) RADEON(0): I2C device "LVDS:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "LVDS:ddc2" removed.
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 0
(II) RADEON(0): Detected non-DDC Monitor Type: 2
in RADEONProbeOutputModes
(II) RADEON(0): Added native panel mode: 1024x768
(II) RADEON(0): Adding Screen mode: 800x600
(II) RADEON(0): Adding Screen mode: 800x600
(II) RADEON(0): Adding Screen mode: 640x480
(II) RADEON(0): Total number of valid Screen mode(s) added: 3
(II) RADEON(0): Output VGA-0 connected
(II) RADEON(0): Output LVDS connected
(II) RADEON(0): Output S-video disconnected
(II) RADEON(0): Output VGA-0 using initial mode 800x600@60
(II) RADEON(0): Output LVDS using initial mode 1024x768
after xf86InitialConfiguration
(==) RADEON(0): DPI set to (96, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(**) RADEON(0): Using gamma correction (1.0, 1.0, 1.0)
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module "ramdac" already built-in
(==) RADEON(0): Using XAA acceleration architecture
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.2.0
	ABI class: X.Org Video Driver, version 2.0
(==) RADEON(0): Assuming overlay scaler buffer width is 1536
(II) RADEON(0): No MM_TABLE found - assuming CARD is not TV-in capable.
(!!) RADEON(0): For information on using the multimedia capabilities
	of this adapter, please see http://gatos.sf.net.
(!!) RADEON(0): MergedFB support has been removed and replaced with xrandr 1.2 support
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xf0300000 - 0xf030ffff (0x10000) MX[B]
	[1] 0	0	0xf8000000 - 0xfbffffff (0x4000000) MX[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xf0018c00 - 0xf0018cff (0x100) MX[B]
	[7] -1	0	0xf0017000 - 0xf0017fff (0x1000) MX[B]
	[8] -1	0	0xf0016000 - 0xf0016fff (0x1000) MX[B]
	[9] -1	0	0xf0000000 - 0xf000ffff (0x10000) MX[B]
	[10] -1	0	0xf0018800 - 0xf00188ff (0x100) MX[B]
	[11] -1	0	0xf0010000 - 0xf0013fff (0x4000) MX[B]
	[12] -1	0	0xf0018000 - 0xf00187ff (0x800) MX[B]
	[13] -1	0	0xf0014000 - 0xf0014fff (0x1000) MX[B]
	[14] -1	0	0xf0600000 - 0xf05fffff (0x0) MX[B]O
	[15] -1	0	0xf4000000 - 0xf3ffffff (0x0) MX[B]O
	[16] -1	0	0xf0300000 - 0xf030ffff (0x10000) MX[B](B)
	[17] -1	0	0xf8000000 - 0xfbffffff (0x4000000) MX[B](B)
	[18] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[19] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[20] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[21] 0	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[22] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[23] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[24] -1	0	0x00008080 - 0x0000808f (0x10) IX[B]
	[25] -1	0	0x00008090 - 0x00008097 (0x8) IX[B]
	[26] -1	0	0x00009000 - 0x000090ff (0x100) IX[B]
	[27] -1	0	0x00008400 - 0x000084ff (0x100) IX[B]
	[28] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B](B)
	[29] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[30] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) RADEON(0): RADEONScreenInit f8000000 0 0
(==) RADEON(0): Write-combining range (0xf8000000,0x2000000)
(WW) RADEON(0): Cannot read colourmap from VGA.  Will restore with default
Entering TV Save
Save TV timing tables
saveTimingTables: reading timing tables
TV Save done
disable montype: 2
disable montype: 1
(II) RADEON(0): Dynamic Clock Scaling Disabled
(==) RADEON(0): Using 24 bit depth buffer
(II) RADEON(0): RADEONInitMemoryMap() : 
(II) RADEON(0):   mem_size         : 0x02000000
(II) RADEON(0):   MC_FB_LOCATION   : 0x2fff2e00
(II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
(II) RADEON(0): Depth moves disabled by default
(II) RADEON(0): CP in BM mode
(II) RADEON(0): Using 8 MB GART aperture
(II) RADEON(0): Using 1 MB for the ring buffer
(II) RADEON(0): Using 2 MB for vertex/indirect buffers
(II) RADEON(0): Using 5 MB for GART textures
(II) RADEON(0): Memory manager initialized to (0,0) (1024,8191)
(II) RADEON(0): Reserved area from (0,768) to (1024,770)
(II) RADEON(0): Largest offscreen area available: 1024 x 7421
(II) RADEON(0): Will use front buffer at offset 0x0
(II) RADEON(0): Will use back buffer at offset 0x900000
(II) RADEON(0): Will use depth buffer at offset 0xc00000
(II) RADEON(0): Will use 17408 kb for textures at offset 0xf00000
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:05.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: drmOpenMinor returns 7
drmOpenByBusid: drmGetBusid reports pci:0000:01:05.0
(II) [drm] DRM interface version 1.3
(II) [drm] DRM open master succeeded.
(II) RADEON(0): [drm] Using the DRM lock SAREA also for drawables.
(II) RADEON(0): [drm] framebuffer handle = 0xf8000000
(II) RADEON(0): [drm] added 1 reserved context for kernel
(II) RADEON(0): X context handle = 0x1
(II) RADEON(0): [drm] installed DRM signal handler
(==) RADEON(0): Using AGP 4x
(II) RADEON(0): [agp] Mode 0x0f000207 [AGP 0x1002/0xcab2; Card 0x1002/0x4337]
(II) RADEON(0): [agp] 8192 kB allocated with handle 0x00000001
(II) RADEON(0): [agp] ring handle = 0xf4000000
(II) RADEON(0): [agp] Ring mapped at 0xb5839000
(II) RADEON(0): [agp] ring read ptr handle = 0xf4101000
(II) RADEON(0): [agp] Ring read ptr mapped at 0xb7fb6000
(II) RADEON(0): [agp] vertex/indirect buffers handle = 0xf4102000
(II) RADEON(0): [agp] Vertex/indirect buffers mapped at 0xb5639000
(II) RADEON(0): [agp] GART texture map handle = 0xf4302000
(II) RADEON(0): [agp] GART Texture map mapped at 0xb5159000
(II) RADEON(0): [drm] register handle = 0xf0300000
(II) RADEON(0): [dri] Visual configs initialized
disable montype: 2
init memmap
init common
init crtc1
init pll1
restore memmap
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0x2fff2e00 0x2fff2e00
(II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
restore common
restore crtc1
restore pll1
restore LVDS
enable montype: 2
disable montype: 1
init memmap
init common
init crtc2
init pll2
freq: 40000000
best_freq: 40004212
best_feedback_div: 799
best_ref_div: 479
best_post_div: 8
restore memmap
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0x2fff2e00 0x2fff2e00
(II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
restore common
restore crtc2
restore pll2
finished PLL2
restore dac
enable montype: 1
disable montype: 2
disable montype: 1
(==) RADEON(0): Backing store disabled
(II) RADEON(0): [DRI] installation complete
(II) RADEON(0): [drm] Added 32 65536 byte vertex/indirect buffers
(II) RADEON(0): [drm] Mapped 32 vertex/indirect buffers
(II) RADEON(0): [drm] dma control initialized, using IRQ 5
(II) RADEON(0): [drm] Initialized kernel GART heap manager, 5111808
(WW) RADEON(0): DRI init changed memory map, adjusting ...
(WW) RADEON(0):   MC_FB_LOCATION  was: 0x2fff2e00 is: 0x2fff2e00
(WW) RADEON(0):   MC_AGP_LOCATION was: 0xffffffc0 is: 0xf47ff400
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0x2fff2e00 0x2fff2e00
(II) RADEON(0):   MC_AGP_LOCATION  : 0xf47ff400
(II) RADEON(0): Direct rendering enabled
(II) RADEON(0): Render acceleration enabled
(II) RADEON(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Indirect CPU to Screen color expansion
	Solid Lines
	Scanline Image Writes
	Setting up tile and stipple cache:
		32 128x128 slots
		32 256x256 slots
		16 512x512 slots
(II) RADEON(0): Acceleration enabled
(II) RADEON(0): DPMS enabled
(==) RADEON(0): Silken mouse enabled
(II) RADEON(0): Using hardware cursor 0 (scanline 770)
(II) RADEON(0): Using hardware cursor 1 (scanline 774)
(II) RADEON(0): Largest offscreen area available: 1024 x 7413
(II) RADEON(0): No video input capabilities detected and no information is provided - disabling multimedia i2c
(II) Loading sub module "theatre_detect"
(II) LoadModule: "theatre_detect"
(II) Loading /usr/lib/xorg/modules/multimedia//theatre_detect_drv.so
(II) Module theatre_detect: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(II) RADEON(0): no multimedia table present, disabling Rage Theatre.
(II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(WW) RADEON(0): Option "MergedFB" is not used
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
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:05.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports pci:0000:01:05.0
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
(II) AIGLX: Loaded and initialized /usr/lib/dri/radeon_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
(II) RADEON(0): Setting screen physical size to 270 x 203
Atom 4, CARD32 4, unsigned long 4
(II) Synaptics touchpad driver version 0.14.6 (1406)
Synaptics Touchpad no synaptics event device found (checked 20 nodes)
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
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
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
(**) Option "XkbModel" "abnt2"
(**) Generic Keyboard: XkbModel: "abnt2"
(**) Option "XkbLayout" "br"
(**) Generic Keyboard: XkbLayout: "br"
(**) Option "XkbOptions" "lv3:ralt_switch"
(**) Generic Keyboard: XkbOptions: "lv3:ralt_switch"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(II) evaluating device (Generic Keyboard)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) evaluating device (Configured Mouse)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(--) Configured Mouse: PnP-detected protocol: "ExplorerPS/2"
(II) Configured Mouse: ps2EnableDataReporting: succeeded
enable montype: 2
enable montype: 1
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: SNY  Model: 3300  Serial#: 0
(II) RADEON(0): Year: 2006  Week: 35
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate
(II) RADEON(0): Max H-Image Size [cm]: H-Size may change,  V-Size may change
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.640 redY: 0.333   greenX: 0.275 greenY: 0.595
(II) RADEON(0): blueX: 0.143 blueY: 0.064   whiteX: 0.280 whiteY: 0.290
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1024  vsize 768  refresh: 75  vid: 20321
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 65.0 MHz   Image Size:  0 x 0 mm
(II) RADEON(0): h_active: 1024  h_sync: 1053  h_sync_end 1189 h_blank_end 1344 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 79.5 MHz   Image Size:  0 x 0 mm
(II) RADEON(0): h_active: 1280  h_sync: 1344  h_sync_end 1472 h_blank_end 1664 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 778 v_blanking: 798 v_border: 0
(II) RADEON(0): Ranges: V min: 58  V max: 62 Hz, H min: 30  H max: 50 kHz, PixClock max 80 MHz
(II) RADEON(0): Monitor name: KLV-S23A10T
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff004dd9003300000000
(II) RADEON(0): 	23100103080000780ad9ada355469824
(II) RADEON(0): 	10474aadc800614f0101010101010101
(II) RADEON(0): 	01010101010164190040410026301d88
(II) RADEON(0): 	36000000000000180e1f008051001e30
(II) RADEON(0): 	4080370000000000001c000000fd003a
(II) RADEON(0): 	3e1e3208000a202020202020000000fc
(II) RADEON(0): 	004b4c562d533233413130540a20006d
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "SNY", prod id 13056
(II) RADEON(0): I2C device "LVDS:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "LVDS:ddc2" removed.
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 0
(II) RADEON(0): Detected non-DDC Monitor Type: 2
in RADEONProbeOutputModes
(II) RADEON(0): Added native panel mode: 1024x768
(II) RADEON(0): Adding Screen mode: 800x600
(II) RADEON(0): Adding Screen mode: 800x600
(II) RADEON(0): Adding Screen mode: 640x480
(II) RADEON(0): Total number of valid Screen mode(s) added: 3
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: SNY  Model: 3300  Serial#: 0
(II) RADEON(0): Year: 2006  Week: 35
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate
(II) RADEON(0): Max H-Image Size [cm]: H-Size may change,  V-Size may change
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.640 redY: 0.333   greenX: 0.275 greenY: 0.595
(II) RADEON(0): blueX: 0.143 blueY: 0.064   whiteX: 0.280 whiteY: 0.290
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1024  vsize 768  refresh: 75  vid: 20321
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 65.0 MHz   Image Size:  0 x 0 mm
(II) RADEON(0): h_active: 1024  h_sync: 1053  h_sync_end 1189 h_blank_end 1344 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 79.5 MHz   Image Size:  0 x 0 mm
(II) RADEON(0): h_active: 1280  h_sync: 1344  h_sync_end 1472 h_blank_end 1664 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 778 v_blanking: 798 v_border: 0
(II) RADEON(0): Ranges: V min: 58  V max: 62 Hz, H min: 30  H max: 50 kHz, PixClock max 80 MHz
(II) RADEON(0): Monitor name: KLV-S23A10T
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff004dd9003300000000
(II) RADEON(0): 	23100103080000780ad9ada355469824
(II) RADEON(0): 	10474aadc800614f0101010101010101
(II) RADEON(0): 	01010101010164190040410026301d88
(II) RADEON(0): 	36000000000000180e1f008051001e30
(II) RADEON(0): 	4080370000000000001c000000fd003a
(II) RADEON(0): 	3e1e3208000a202020202020000000fc
(II) RADEON(0): 	004b4c562d533233413130540a20006d
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "SNY", prod id 13056
(II) RADEON(0): I2C device "LVDS:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "LVDS:ddc2" removed.
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 0
(II) RADEON(0): Detected non-DDC Monitor Type: 2
in RADEONProbeOutputModes
(II) RADEON(0): Added native panel mode: 1024x768
(II) RADEON(0): Adding Screen mode: 800x600
(II) RADEON(0): Adding Screen mode: 800x600
(II) RADEON(0): Adding Screen mode: 640x480
(II) RADEON(0): Total number of valid Screen mode(s) added: 3
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: SNY  Model: 3300  Serial#: 0
(II) RADEON(0): Year: 2006  Week: 35
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate
(II) RADEON(0): Max H-Image Size [cm]: H-Size may change,  V-Size may change
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.640 redY: 0.333   greenX: 0.275 greenY: 0.595
(II) RADEON(0): blueX: 0.143 blueY: 0.064   whiteX: 0.280 whiteY: 0.290
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1024  vsize 768  refresh: 75  vid: 20321
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 65.0 MHz   Image Size:  0 x 0 mm
(II) RADEON(0): h_active: 1024  h_sync: 1053  h_sync_end 1189 h_blank_end 1344 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 79.5 MHz   Image Size:  0 x 0 mm
(II) RADEON(0): h_active: 1280  h_sync: 1344  h_sync_end 1472 h_blank_end 1664 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 778 v_blanking: 798 v_border: 0
(II) RADEON(0): Ranges: V min: 58  V max: 62 Hz, H min: 30  H max: 50 kHz, PixClock max 80 MHz
(II) RADEON(0): Monitor name: KLV-S23A10T
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff004dd9003300000000
(II) RADEON(0): 	23100103080000780ad9ada355469824
(II) RADEON(0): 	10474aadc800614f0101010101010101
(II) RADEON(0): 	01010101010164190040410026301d88
(II) RADEON(0): 	36000000000000180e1f008051001e30
(II) RADEON(0): 	4080370000000000001c000000fd003a
(II) RADEON(0): 	3e1e3208000a202020202020000000fc
(II) RADEON(0): 	004b4c562d533233413130540a20006d
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "SNY", prod id 13056
(II) RADEON(0): I2C device "LVDS:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "LVDS:ddc2" removed.
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 0
(II) RADEON(0): Detected non-DDC Monitor Type: 2
in RADEONProbeOutputModes
(II) RADEON(0): Added native panel mode: 1024x768
(II) RADEON(0): Adding Screen mode: 800x600
(II) RADEON(0): Adding Screen mode: 800x600
(II) RADEON(0): Adding Screen mode: 640x480
(II) RADEON(0): Total number of valid Screen mode(s) added: 3
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: SNY  Model: 3300  Serial#: 0
(II) RADEON(0): Year: 2006  Week: 35
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate
(II) RADEON(0): Max H-Image Size [cm]: H-Size may change,  V-Size may change
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.640 redY: 0.333   greenX: 0.275 greenY: 0.595
(II) RADEON(0): blueX: 0.143 blueY: 0.064   whiteX: 0.280 whiteY: 0.290
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1024  vsize 768  refresh: 75  vid: 20321
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 65.0 MHz   Image Size:  0 x 0 mm
(II) RADEON(0): h_active: 1024  h_sync: 1053  h_sync_end 1189 h_blank_end 1344 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 79.5 MHz   Image Size:  0 x 0 mm
(II) RADEON(0): h_active: 1280  h_sync: 1344  h_sync_end 1472 h_blank_end 1664 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 778 v_blanking: 798 v_border: 0
(II) RADEON(0): Ranges: V min: 58  V max: 62 Hz, H min: 30  H max: 50 kHz, PixClock max 80 MHz
(II) RADEON(0): Monitor name: KLV-S23A10T
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff004dd9003300000000
(II) RADEON(0): 	23100103080000780ad9ada355469824
(II) RADEON(0): 	10474aadc800614f0101010101010101
(II) RADEON(0): 	01010101010164190040410026301d88
(II) RADEON(0): 	36000000000000180e1f008051001e30
(II) RADEON(0): 	4080370000000000001c000000fd003a
(II) RADEON(0): 	3e1e3208000a202020202020000000fc
(II) RADEON(0): 	004b4c562d533233413130540a20006d
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "SNY", prod id 13056
(II) RADEON(0): I2C device "LVDS:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "LVDS:ddc2" removed.
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 0
(II) RADEON(0): Detected non-DDC Monitor Type: 2
in RADEONProbeOutputModes
(II) RADEON(0): Added native panel mode: 1024x768
(II) RADEON(0): Adding Screen mode: 800x600
(II) RADEON(0): Adding Screen mode: 800x600
(II) RADEON(0): Adding Screen mode: 640x480
(II) RADEON(0): Total number of valid Screen mode(s) added: 3
disable montype: 1
disable montype: 5
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: SNY  Model: 3300  Serial#: 0
(II) RADEON(0): Year: 2006  Week: 35
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate
(II) RADEON(0): Max H-Image Size [cm]: H-Size may change,  V-Size may change
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.640 redY: 0.333   greenX: 0.275 greenY: 0.595
(II) RADEON(0): blueX: 0.143 blueY: 0.064   whiteX: 0.280 whiteY: 0.290
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1024  vsize 768  refresh: 75  vid: 20321
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 65.0 MHz   Image Size:  0 x 0 mm
(II) RADEON(0): h_active: 1024  h_sync: 1053  h_sync_end 1189 h_blank_end 1344 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 79.5 MHz   Image Size:  0 x 0 mm
(II) RADEON(0): h_active: 1280  h_sync: 1344  h_sync_end 1472 h_blank_end 1664 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 778 v_blanking: 798 v_border: 0
(II) RADEON(0): Ranges: V min: 58  V max: 62 Hz, H min: 30  H max: 50 kHz, PixClock max 80 MHz
(II) RADEON(0): Monitor name: KLV-S23A10T
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff004dd9003300000000
(II) RADEON(0): 	23100103080000780ad9ada355469824
(II) RADEON(0): 	10474aadc800614f0101010101010101
(II) RADEON(0): 	01010101010164190040410026301d88
(II) RADEON(0): 	36000000000000180e1f008051001e30
(II) RADEON(0): 	4080370000000000001c000000fd003a
(II) RADEON(0): 	3e1e3208000a202020202020000000fc
(II) RADEON(0): 	004b4c562d533233413130540a20006d
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "SNY", prod id 13056
(II) RADEON(0): I2C device "LVDS:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "LVDS:ddc2" removed.
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 0
(II) RADEON(0): Detected non-DDC Monitor Type: 2
in RADEONProbeOutputModes
(II) RADEON(0): Added native panel mode: 1024x768
(II) RADEON(0): Adding Screen mode: 800x600
(II) RADEON(0): Adding Screen mode: 800x600
(II) RADEON(0): Adding Screen mode: 640x480
(II) RADEON(0): Total number of valid Screen mode(s) added: 3
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: SNY  Model: 3300  Serial#: 0
(II) RADEON(0): Year: 2006  Week: 35
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate
(II) RADEON(0): Max H-Image Size [cm]: H-Size may change,  V-Size may change
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.640 redY: 0.333   greenX: 0.275 greenY: 0.595
(II) RADEON(0): blueX: 0.143 blueY: 0.064   whiteX: 0.280 whiteY: 0.290
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1024  vsize 768  refresh: 75  vid: 20321
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 65.0 MHz   Image Size:  0 x 0 mm
(II) RADEON(0): h_active: 1024  h_sync: 1053  h_sync_end 1189 h_blank_end 1344 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 79.5 MHz   Image Size:  0 x 0 mm
(II) RADEON(0): h_active: 1280  h_sync: 1344  h_sync_end 1472 h_blank_end 1664 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 778 v_blanking: 798 v_border: 0
(II) RADEON(0): Ranges: V min: 58  V max: 62 Hz, H min: 30  H max: 50 kHz, PixClock max 80 MHz
(II) RADEON(0): Monitor name: KLV-S23A10T
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff004dd9003300000000
(II) RADEON(0): 	23100103080000780ad9ada355469824
(II) RADEON(0): 	10474aadc800614f0101010101010101
(II) RADEON(0): 	01010101010164190040410026301d88
(II) RADEON(0): 	36000000000000180e1f008051001e30
(II) RADEON(0): 	4080370000000000001c000000fd003a
(II) RADEON(0): 	3e1e3208000a202020202020000000fc
(II) RADEON(0): 	004b4c562d533233413130540a20006d
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "SNY", prod id 13056
(II) RADEON(0): I2C device "LVDS:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "LVDS:ddc2" removed.
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 0
(II) RADEON(0): Detected non-DDC Monitor Type: 2
in RADEONProbeOutputModes
(II) RADEON(0): Added native panel mode: 1024x768
(II) RADEON(0): Adding Screen mode: 800x600
(II) RADEON(0): Adding Screen mode: 800x600
(II) RADEON(0): Adding Screen mode: 640x480
(II) RADEON(0): Total number of valid Screen mode(s) added: 3
```

As for the Envy installer, autodetecting my video card failed. When I chose the manual installation (and there was only one ATI driver version available anyway) it installed successfully, prompted for a restart and X crashed on restart. This is the text in /var/log/envy-installer.log:```
python pulse.py ati latest 
root@Dragonfly:/usr/share/envy# python pulse.py ati latest
/usr/lib/python2.5/site-packages/apt/__init__.py:18: FutureWarning: apt API not stable yet
  warnings.warn("apt API not stable yet", FutureWarning)
EnvyNG - Version 1.1.1
Ubuntu Hardy 32bit
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
EnvyNG: The following packages will be removed:
fglrx-control
xorg-driver-fglrx

EnvyNG: attempting to remove the packages
EnvyNG: Updating the packages list
Ign http://apt.wicd.net hardy Release.gpg                                      
Ign http://apt.wicd.net hardy/extras Translation-en_US
Get:1 http://archive.ubuntu.com hardy-security Release.gpg [191B]              
Ign http://archive.ubuntu.com hardy-security/main Translation-en_US
Get:2 http://apt.wicd.net hardy Release [29.1kB]
Ign http://archive.ubuntu.com hardy-security/restricted Translation-en_US      
Ign http://archive.ubuntu.com hardy-security/universe Translation-en_US
Ign http://archive.ubuntu.com hardy-security/multiverse Translation-en_US
Hit http://archive.ubuntu.com hardy Release.gpg                      
Ign http://archive.ubuntu.com hardy/universe Translation-en_US       
Ign http://archive.ubuntu.com hardy/main Translation-en_US           
Ign http://archive.ubuntu.com hardy/restricted Translation-en_US
Hit http://packages.medibuntu.org hardy Release.gpg                  
Hit http://apt.wicd.net hardy/extras Packages
Ign http://archive.ubuntu.com hardy/multiverse Translation-en_US
Get:3 http://archive.ubuntu.com hardy-updates Release.gpg [191B]
Ign http://archive.ubuntu.com hardy-updates/universe Translation-en_US
Ign http://archive.ubuntu.com hardy-updates/main Translation-en_US
Ign http://archive.ubuntu.com hardy-updates/multiverse Translation-en_US
Ign http://archive.ubuntu.com hardy-updates/restricted Translation-en_US
Get:4 http://archive.ubuntu.com hardy-security Release [44.0kB]
Ign http://packages.medibuntu.org hardy/free Translation-en_US
Ign http://packages.medibuntu.org hardy/non-free Translation-en_US
Hit http://packages.medibuntu.org hardy Release
Hit http://archive.ubuntu.com hardy Release         
Get:5 http://archive.ubuntu.com hardy-updates Release [51.2kB]
Hit http://packages.medibuntu.org hardy/free Packages
Get:6 http://archive.ubuntu.com hardy-security/main Packages [11.4kB]
Get:7 http://archive.ubuntu.com hardy-security/restricted Packages [14B]
Get:8 http://archive.ubuntu.com hardy-security/main Sources [4020B]
Get:9 http://archive.ubuntu.com hardy-security/restricted Sources [14B]
Get:10 http://archive.ubuntu.com hardy-security/universe Packages [8140B]
Get:11 http://archive.ubuntu.com hardy-security/universe Sources [1725B]
Get:12 http://archive.ubuntu.com hardy-security/multiverse Packages [14B]
Get:13 http://archive.ubuntu.com hardy-security/multiverse Sources [14B]
Hit http://archive.ubuntu.com hardy/universe Packages
Hit http://packages.medibuntu.org hardy/non-free Packages
Hit http://archive.ubuntu.com hardy/main Packages
Hit http://archive.ubuntu.com hardy/restricted Packages
Hit http://archive.ubuntu.com hardy/multiverse Packages
Hit http://archive.ubuntu.com hardy/universe Sources
Hit http://archive.ubuntu.com hardy/multiverse Sources
Get:14 http://archive.ubuntu.com hardy-updates/universe Packages [22.4kB]
Get:15 http://archive.ubuntu.com hardy-updates/main Packages [44.7kB]
Get:16 http://archive.ubuntu.com hardy-updates/multiverse Packages [14B]
Get:17 http://archive.ubuntu.com hardy-updates/restricted Packages [14B]
Fetched 188kB in 4s (42.3kB/s)
Reading package lists... Done
EnvyNG: Ubuntu stock kernel detected (2.6.24-16-generic)
OK: All the packages are installed
OK: All the packages are installed
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.
EnvyNG: The following packages are not installed:
fglrx-kernel-source
xorg-driver-fglrx
xorg-driver-fglrx-dev
fglrx-control
fglrx-amdcccle

EnvyNG: attempting to install the packages
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  debhelper dpatch html2text intltool-debian po-debconf
Suggested packages:
  dh-make
Recommended packages:
  fakeroot patchutils devscripts kernel-package libmail-sendmail-perl
  libmail-box-perl
The following NEW packages will be installed:
  debhelper dpatch fglrx-amdcccle fglrx-control fglrx-kernel-source html2text
  intltool-debian po-debconf xorg-driver-fglrx xorg-driver-fglrx-dev
0 upgraded, 10 newly installed, 0 to remove and 6 not upgraded.
Need to get 1232kB/16.6MB of archives.
After this operation, 43.5MB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  html2text intltool-debian po-debconf debhelper dpatch xorg-driver-fglrx
  fglrx-control fglrx-amdcccle fglrx-kernel-source xorg-driver-fglrx-dev
Authentication warning overridden.
Get:1 http://archive.ubuntu.com hardy/main html2text 1.3.2a-3build2 [87.6kB]
Get:2 http://archive.ubuntu.com hardy/main intltool-debian 0.35.0+20060710.1 [31.6kB]
Get:3 http://archive.ubuntu.com hardy/main po-debconf 1.0.10 [232kB]
Get:4 http://archive.ubuntu.com hardy/main debhelper 6.0.4ubuntu1 [516kB]
Get:5 http://archive.ubuntu.com hardy/main dpatch 2.0.28 [87.1kB]
Get:6 http://archive.ubuntu.com hardy/restricted fglrx-amdcccle 2.6.24.12-16.34 [37.4kB]
Get:7 http://archive.ubuntu.com hardy/multiverse fglrx-kernel-source 1:8-3+2.6.24.12-16.34 [169kB]
Get:8 http://archive.ubuntu.com hardy/restricted xorg-driver-fglrx-dev 1:7.1.0-8-3+2.6.24.12-16.34 [72.1kB]
Fetched 1232kB in 5s (230kB/s)
Selecting previously deselected package html2text.
(Reading database ... 189756 files and directories currently installed.)
Unpacking html2text (from .../html2text_1.3.2a-3build2_i386.deb) ...
Selecting previously deselected package intltool-debian.
Unpacking intltool-debian (from .../intltool-debian_0.35.0+20060710.1_all.deb) ...
Selecting previously deselected package po-debconf.
Unpacking po-debconf (from .../po-debconf_1.0.10_all.deb) ...
Selecting previously deselected package debhelper.
Unpacking debhelper (from .../debhelper_6.0.4ubuntu1_all.deb) ...
Selecting previously deselected package dpatch.
Unpacking dpatch (from .../archives/dpatch_2.0.28_all.deb) ...
Selecting previously deselected package xorg-driver-fglrx.
Unpacking xorg-driver-fglrx (from .../xorg-driver-fglrx_1%3a7.1.0-8-3+2.6.24.12-16.34_i386.deb) ...
Selecting previously deselected package fglrx-control.
Unpacking fglrx-control (from .../fglrx-control_1%3a8-3+2.6.24.12-16.34_i386.deb) ...
Selecting previously deselected package fglrx-amdcccle.
Unpacking fglrx-amdcccle (from .../fglrx-amdcccle_2.6.24.12-16.34_i386.deb) ...
Selecting previously deselected package fglrx-kernel-source.
Unpacking fglrx-kernel-source (from .../fglrx-kernel-source_1%3a8-3+2.6.24.12-16.34_i386.deb) ...
Selecting previously deselected package xorg-driver-fglrx-dev.
Unpacking xorg-driver-fglrx-dev (from .../xorg-driver-fglrx-dev_1%3a7.1.0-8-3+2.6.24.12-16.34_i386.deb) ...
Setting up html2text (1.3.2a-3build2) ...
Setting up intltool-debian (0.35.0+20060710.1) ...
Setting up po-debconf (1.0.10) ...
Setting up debhelper (6.0.4ubuntu1) ...
Setting up dpatch (2.0.28) ...
Setting up xorg-driver-fglrx (1:7.1.0-8-3+2.6.24.12-16.34) ...
* Starting atieventsd                                                   [ OK ] 

Setting up fglrx-control (1:8-3+2.6.24.12-16.34) ...
Setting up fglrx-amdcccle (2.6.24.12-16.34) ...
Setting up fglrx-kernel-source (1:8-3+2.6.24.12-16.34) ...
Setting up xorg-driver-fglrx-dev (1:7.1.0-8-3+2.6.24.12-16.34) ...
EnvyNG: Operation Complete
```

I updated my BIOS from the HP website (since now Compaq is owned by HP) about two months ago, and still it didn't support booting from USB. This *is* a 6-year-old laptop, after all. Is there any way to make my BIOS support USB booting, or any alternative BIOS I can use? Just in case it's relevant, I dual-boot Windows XP.

By the way, thanks a lot for helping me make sense of this; I really appreciate it.

---

### Post by peitschie on 2008-05-14
Hmm... That's an old laptop!  Its no longer supported by the latest Ati drivers which explains why Envy doesn't work ([https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_84_linux.html](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_84_linux.html) for the supported list).  It appears you are running an IGP330M/340M/350M (from the Xorg.0.log file, line 432).

I still can't provide any insight into the crashes.  Is it just the Xserver that crashes or the whole computer?  Can you have a look at the /var/log/gdm/* files?  All of mine seem pretty standard, but it's possible that a crash will be recorded there...

Another thing to try is this.  Once you are presented with the login screen, hit Ctrl+Alt+F1 to get to a virtual terminal (hit Ctrl+Alt+F7 to get back to the login screen).

Log in using your normal user/pass.  Once you are logged in, run the following commands:
```

sudo /etc/init.d/gdm stop # Stop the existing GDM server... this might take a bit
startx # Launch a new X server... this won't ask you to log in

```

Hopefully, if the Xserver crashes, this should dump the information out to the console which might give us a clue.  If its the whole computer crashing... well... we'll need to try other approaches.

As for booting USB on a computer that doesn't support it, Grub can do it :D.  See here for an awesomely helpful article: [https://help.ubuntu.com/community/BootFromUSB](https://help.ubuntu.com/community/BootFromUSB) .  You are specifically looking at [https://help.ubuntu.com/community/BootFromUSB#head-5938e2f2bd2f35c1361bd9c633df4b954e5029cd](https://help.ubuntu.com/community/BootFromUSB#head-5938e2f2bd2f35c1361bd9c633df4b954e5029cd) for the information on how to add the entry to grub to get it to boot.

---

### Post by peitschie on 2008-05-14
Also, I found this posting on another thread which may provide some tips: [http://ubuntuforums.org/showpost.php?p=4572303&postcount=48](http://ubuntuforums.org/showpost.php?p=4572303&postcount=48)

The whole thread is dealing with the IGP345M ati which is likely similar to yours, so reading through there might give you some insights perhaps...  You might try posting your question in there even :)... not that I'm trying to get rid of you lol.

---

### Post by GepettoBR on 2008-05-15
The crashing is really random, when I get one I'll post it here. I know it's X because when the scrren goes black, Ctrl+Alt+Backspace works. I'm off to play tennis right after lunch, as soon as I get back I'll backup my /home (which is currently not on a separate partition; I'll fix that as well) and try installing Hardy via USB, then checking my Xorg.conf with the one from the post you linked to. Hopefully a clean install will fix my problems, and if it doesn't and nothing else does, I can use the USB trick to install Gutsy again, which worked.

Thank you very very much, you've been extremely helpful so far. I'm willing to bet your advice will fix these issues.

---

### Post by GepettoBR on 2008-05-15
Gah, I've been trying all day to boot from my USB stick, so far no cigar. It looks like GRUB doesn't even know it exists.

I checked my xorg.conf against the quote from the post you linked to, I made a few changes and it crashed again. This time, I had forgotten to backup the file, so I had to enter recovery mode and restore it (I didn't even know that was an option) and it hasn't crashed since, though I've been logged on for only a few minutes at a time, then trying to figure out GRUB again.

I'm going to risk the "Booting the kernel from a bootable CD" boot option on the documentation page you sent now. My fingers are crossed.

---

### Post by peitschie on 2008-05-15
Sounds like a plan! 

Good luck with it all... let us know if it ends up resolving the issues for you :)

---

### Post by peitschie on 2008-05-15
Just out of interest with the grub... were you manually changing the root (i.e., root (hd0,0)), or did you use the find /FILENAME command?

A useful link (and utility) that you might look into if your interested... [http://www.supergrubdisk.org/wiki/USB_Boot](http://www.supergrubdisk.org/wiki/USB_Boot)

If you back up your drives and such properly, I'm pretty sure we can figure out how to install from the hard drive if you want ;)

---

### Post by GepettoBR on 2008-05-16
I tried both the root and the find commands. find gave me nothing, and I used root all the way from hd1 through 9 (hd0 is my only internal hard drive), partitions 0, 1 and 2 (and my pendrive only has one partition) but nothing worked. Super GRUB Disk booted, taking a long time and making a lot of noise (I half-expected my disk drive to combust) but when I thought it was booting from USB (the CD stopped spinning and the little light on my pendrive started flashing), an error message informed me that it was falling back into shell because /dev/sdb1 wasn't found. I have no idea why that is, since it should be mounting the pendrive as / AND in my hard-drive installed Hardy the pendrive mounts as /dev/sda.

I think maybe the problem is that all these methods are for booting an installed OS from the USB drive, while I'm trying to boot into an altered LiveCD (as per the link you provided) in a USB pendrive.

I thought I could try installing via Wubi, since all I'd have to do then would be mount the iso in Windows, but then I found out that it doesn't really install into a separate partition, but a virtual one managed by the Windows bootloader. So if Windows dies (an all too common occurrence) I would be unable to boot into Ubuntu as well. If there was a way to do a normal install from within Windows or transport the Wubi install to a regular logical partition, this would be easier.

Can I just downgrade the X server back to the Gutsy version, or would that compromise anything else that depends on it?

P.S.: In grub, I also used the find command with (sd0,0) and so forth, to no avail. using the fromusb argument in the kernel line also did not work. I found a blog post ([http://danmarner.blogspot.com/2008/05/installing-ubuntu-hardy-heron-from-hard.html](http://danmarner.blogspot.com/2008/05/installing-ubuntu-hardy-heron-from-hard.html)) on installing from an ISO on my hard drive, and am now downloading the Alternative CD to test it.

---

### Post by GepettoBR on 2008-05-16
YESSS!!!

Booting from the Alternative CD image in another partition worked!

Now I just need to let the computer cool down a little so I can run the GParted LiveCD and take out a part of my Ubuntu partition for /home.

If X still crashes after all this, I'm going to need a LOT of chocolate to keep from killing myself.

Thanks a million for the help so far! I'll keep you posted.

---

### Post by peitschie on 2008-05-16
Heheh.  I'll try and get some chocolate standing by lol.  Oh the joys of Ubuntu *sigh*.    Sounds like your doing good work though :).  Congratulations on getting this far!

---

### Post by GepettoBR on 2008-05-17
> **peitschie said:**
> Heheh.  I'll try and get some chocolate standing by lol.  Oh the joys of Ubuntu *sigh*.    Sounds like your doing good work though :).  Congratulations on getting this far!

Thanks! It took me long (first time through I accidentally installed without the graphical interface, and had no idea how to log onto my network via command line, so I reinstalled) but I'm finally on a fresh Hardy install with a dedicated /home partition which, so far, has been a lot faster than my previous upgraded install and hasn't yet crashed. The Tv-Out still doesn't work, though, and it did work in Gutsy. All the little post-install problems have been cleared (PS/2 mouse is working alongside Synaptics, GDesklets is working, et cetera).

On a sidenote, playing around with GRUB is *fun*! Breaking Ubuntu is a lot more pleasing than breaking Windows.

---

### Post by peitschie on 2008-05-18
Congratulations on getting this far :).  Glad to hear I can horde the chocolate myself!!!

There seems to be a package called 'atitvout' available in the hardy repo's which you can sudo apt-get install in theory... I wonder if maybe that might help you?  It may also be possible to use Xrandr to help.
Check out this link for some non-ubuntu-specific tips: [http://www.thinkwiki.org/wiki/How_to_get_TV-Out_working_on_ATI_graphic_cards](http://www.thinkwiki.org/wiki/How_to_get_TV-Out_working_on_ATI_graphic_cards)

I can't provide much help on the atitvout unfortunately (unable to browse package info at the moment for some reason), but there are a few threads around it seems ([http://ubuntuforums.org/archive/index.php/t-152884.html](http://ubuntuforums.org/archive/index.php/t-152884.html))

This link seems to have some possibly useful info
[quote=http://radagast.bglug.ca/laptop/ubuntu_on_latitude_c600.html#vgaout]
There are three tricks to getting TV-out working on this machine. The first is to download the atitvout program:

bash# apt-get install atitvout

The second trick is to have the TV on and connected to the laptop before you turn the laptop on. This is very important because atitvout uses BIOS data that initialize when the laptop boots. If the TV isn't detected when your laptop boots, then no BIOS TV data and no TV Out.

The third trick is to use this command (as root):

bash# atitvout -f t

This command changes video output to the TV. To change back to the LCD, use this command:

bash# atitvout -f l
[/quote]

---

### Post by GepettoBR on 2008-05-18
atitvout is the package I used in Gutsy to get my TV working. It no longer works. I've also already tried Xrandr to no avail. Maybe the new X server just can't do it - and that's bad, because updates that remove functionality aren't exactly useful. The good news is the crashes appear to have stopped altogether.

And I'm still eating chocolate anyway :lol:

---

### Post by GepettoBR on 2008-05-18
We have celebrated too soon. I just had another crash, and I wasn't running GDM through the tty1 interface like you suggested. Apparently, this has to do with too many tabs being open in Firefox. I'm going tobed now, tomorrow I'll reproduce the problem to get an output.

How do I save whatever error message comes up to a text file? Will echo do the trick?

If all else fails, I can just take a picture of the screen :lolflag:

---

### Post by peitschie on 2008-05-18
the error message may be saved in on of the log files (/var/log/ [debug, messages, daemon, Xorg.0 ...etc]

To do it from the tty you start X using the following command:
```

startx &> log.txt

```

The "&>" sign redirects all outputs (stdout & stderr) to the log.txt file rather than printing on screen.

Can you post up outputs from atitvout detect & tvout etc.?  I've never had much luck with Xrandr either... but I'm surprised atitvout doesn't work anymore...

---

### Post by GepettoBR on 2008-05-19
For the life of me, I can't get this to crash... why does this bother me? :lol:
Still trying. The crashes are less frequent, but not gone.

---

### Post by GepettoBR on 2008-05-19
This is the first time I've ever been happy to see X crash. Interestingly, when it crashed I switched to tty1 to see the output, but it was only logged to the text file. Upon returning to tty7, my screen came back to normal. This was without Ctrl+Alt+Backspace.

I couldn't make anything of this text. Hopefully you can: ```
xauth:  creating new authority file /home/paulo/.Xauthority
xauth:  creating new authority file /home/paulo/.Xauthority


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
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9)
Current Operating System: Linux DragonflyMK2 2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686
Build Date: 15 April 2008  05:26:17PM
 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon May 19 19:28:22 2008
(==) Using config file: "/etc/X11/xorg.conf"
(II) Module "ddc" already built-in
(II) Module "i2c" already built-in
NTSC PAL PAL-M NTSC-J 
finished output detect: 0
finished output detect: 1
finished output detect: 2
finished all detect
before xf86InitialConfiguration
in RADEONProbeOutputModes
in RADEONProbeOutputModes
after xf86InitialConfiguration
(II) Module "ramdac" already built-in
Entering TV Save
Save TV timing tables
saveTimingTables: reading timing tables
TV Save done
disable montype: 2
disable montype: 1
disable montype: 2
init memmap
init common
init crtc1
init pll1
restore memmap
restore common
restore crtc1
restore pll1
restore LVDS
enable montype: 2
disable montype: 1
init memmap
init common
init crtc2
init pll2
freq: 65000000
best_freq: 64999299
best_feedback_div: 580
best_ref_div: 428
best_post_div: 4
restore memmap
restore common
restore crtc2
restore pll2
finished PLL2
restore dac
enable montype: 1
disable montype: 2
disable montype: 1
expected keysym, got XF86KbdLightOnOff: line 70 of pc
expected keysym, got XF86KbdBrightnessDown: line 71 of pc
expected keysym, got XF86KbdBrightnessUp: line 72 of pc
Atom 4, CARD32 4, unsigned long 4
Synaptics Touchpad no synaptics event device found (checked 20 nodes)
Query no Synaptics: 6003C8
(EE) Synaptics Touchpad no synaptics touchpad detected and no repeater device
(EE) Synaptics Touchpad Unable to query/initialize Synaptics hardware.
(EE) PreInit failed for input device "Synaptics Touchpad"
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Duplicate shape name "RTRN"
>                   Using last definition
> Warning:          Duplicate shape name "RTSH"
>                   Using last definition
> Warning:          Don't know how to merge sections yet
> Warning:          Don't know how to merge sections yet
> Warning:          Don't know how to merge sections yet
> Warning:          Don't know how to merge sections yet
expected keysym, got XF86KbdLightOnOff: line 70 of pc
expected keysym, got XF86KbdBrightnessDown: line 71 of pc
expected keysym, got XF86KbdBrightnessUp: line 72 of pc
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
enable montype: 2
enable montype: 1
in RADEONProbeOutputModes
in RADEONProbeOutputModes
in RADEONProbeOutputModes
in RADEONProbeOutputModes
in RADEONProbeOutputModes
in RADEONProbeOutputModes
in RADEONProbeOutputModes
in RADEONProbeOutputModes
SetGrabKeysState - disabled
SetGrabKeysState - enabled
disable montype: 2
disable montype: 1
finished PLL2
finished PLL1
Entering Restore TV
Restore TV PLL
Restore TVHV
Restore TV Restarts
Restore Timing Tables
Restore TV standard
Leaving Restore TV
disable montype: 2
init memmap
init common
init crtc1
init pll1
restore memmap
restore common
restore crtc1
restore pll1
restore LVDS
enable montype: 2
disable montype: 1
init memmap
init common
init crtc2
init pll2
freq: 65000000
best_freq: 64999299
best_feedback_div: 580
best_ref_div: 428
best_post_div: 4
restore memmap
restore common
restore crtc2
restore pll2
finished PLL2
restore dac
enable montype: 1
enable montype: 2
enable montype: 1
```

---

### Post by GepettoBR on 2008-05-20
Bump

---

### Post by peitschie on 2008-05-20
Sorry my delayed reply.  I didn't get the most recent update.

Hmm... the output at the command line all looks fine.  There are no errors reported after the X-server starts...

Are you using any desktop effects on your system?  

I'm chasing up the strange effect that switching tty's.  When you mean that X came back up... was it still in your current session or waiting at the login screen?

---

### Post by GepettoBR on 2008-05-20
I'm not using desktop effects. In fact, if I try to enable them, I can't. Before I managed to enable ATITVOUT in Gutsy, they worked. Since then (even after the clean Hardy install) they haven't.

X returns normally, as if I had switched tty's any other time during my session. It happened again today, but I wasn't logging it.

Maybe I'm hallucinating? :lolflag:

---

### Post by GepettoBR on 2008-05-23
BUMP zwei

---

### Post by peitschie on 2008-05-25
Hrmm...

So where are things currently standing in terms of stability and use?

Is X still crashing... how frequently?
We still haven't gotten the tv-out working yet either have we...

---

### Post by GepettoBR on 2008-05-25
At this point, I'm ot really concerned about the TV-Out. If I need it that badly, I'll just log into Windows for a few minutes. The crashes aren't as frequent as before I reinstalled, I'd say once a day, or twice if I use the computer a lot. Firefox has been open all the times this happened, and probably Thunderbird too, though I can't say for sure. Switching to any tty from 1 to 6, then back to tty7 has been enough to get me back up and running, with all my programs still working, so this looks like it's just a display issue. It still annoys the life out of me, though.


Thanks a lot for giving me so much of your time, by the way. You're a great person.

---

