---
title: "LXDE Desktop doesn't start"
date: 2012-04-27
forum: New to Ubuntu
---

### Post by herbert tamayo on 2012-04-27
hi, I've recently installed lubuntu 11.10 alternate, the installation process was successful but in the first boot the X -LXDE- doesn't start, the system stops after activate the bluetooth module, I just can use lubuntu from console mode -ttys-

so, checking in the log file, in the syslog file these are the last lines:
```

Apr 26 04:25:47 imlmetapan NetworkManager[484]: <warn> bluez error getting default adapter: No such adapter
Apr 26 04:25:47 imlmetapan kernel: [   12.028406] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Apr 26 04:25:47 imlmetapan kernel: [   12.028412] Bluetooth: BNEP filters: protocol multicast
Apr 26 04:25:47 imlmetapan kernel: [   12.366623] init: plymouth-stop pre-start process (786) terminated with status 1
Apr 26 04:25:52 imlmetapan kernel: [   17.110998] init: lxdm main process (721) terminated with status 1

```

also, checking in the lxdm.log, this are the result:
```

X.Org X Server 1.10.4
Release Date: 2011-08-19
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-29-server i686 Ubuntu
Current Operating System: Linux imlmetapan 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:50:42 UTC 2011 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-12-generic root=UUID=7eceb984-97ca-4be0-95d7-3a35bb1fc4fc ro splash quiet vt.handoff=7
Build Date: 29 September 2011  12:48:48AM
xorg-server 2:1.10.4-1ubuntu4 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.22.2
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Apr 26 04:25:47 2012
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
(EE) Failed to load module "intel" (module does not exist, 0)
(EE) Failed to load module "vesa" (module does not exist, 0)
(EE) Failed to load module "fbdev" (module does not exist, 0)
(EE) No drivers available.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

 ddxSigGiveUp: Closing log
** Message: exit cb

** Message: free session


```

so, i don't know what it's wrong, anyone may give some advice to load the X?

regards

---

### Post by gordintoronto on 2012-04-27
"No screens found" sounds like the killer, but I could be wrong.

Please describe your video card and monitor (brand and model) and how they are connected (VGA cable?).

Was there some reason you used the alternate installer?

---

### Post by marinara on 2012-04-27
actually you might check your install cd for errors

---

