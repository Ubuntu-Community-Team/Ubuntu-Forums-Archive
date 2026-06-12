---
title: "Generate a xorg.conf file."
date: 2012-09-22
forum: New to Ubuntu
---

### Post by vagelism on 2012-09-22
Hello to all.
I need to generate a xorg.conf file with the current settings of my pc.
This comes because I need to enforce my pc to use these settings when I boot.
I have a KVM switch and if the pc restart then I have low resolution and can not fix this problem till I direct connect my second screen to the laptop directly and not threw the KVM switch.

Thank you in advance!

---

### Post by bogan on 2012-09-22
**Hi!, **vagelism,

To create a new Xorg,conf file: ```
sudo Xorg -configure
```You will then need to move the file to /etc/X11.

I have never used this myself, and am merely repeating a Post I noted. The example I read gave a file with a lot of duplicate entries, so no guarantees it will do what you want.
 **Edit:*** I believe this result was because the system was unable to work out which was the correct driver*.

I assume that if you CD to /etc/X11, before you run the cmd,  you would not need to move the file.

Extract from 'man Xorg':     -configure
               When  this option is specified, the Xorg server loads all video
               driver modules, probes for available hardware, and  writes  out
               an  initial xorg.conf(5) file based on what was detected.  This
               option currently has some problems on some  platforms,  but  in
               most  cases  it  is  a  good way to bootstrap the configuration
               process.  This option is only available when the server is  run
               as root (i.e, with real-uid 0).

Chao!, **bogan**.

---

### Post by TheFu on 2012-09-22
if you are using either ATI or nvidia GPUs, those binary drivers include programs to create a default /etc/X11/xorg.conf file too.
* nvidia-xconfig
* aticonfig

Be certain you read the warnings and settings that each of these tools require.  I think the aticonfig tool requires that X/Windows **not** be running.

---

### Post by vagelism on 2012-09-22
Not my case , I have intel driver.
Also the Xorg-configure command comes with errors!

---

### Post by wojox on 2012-09-22
> **vagelism said:**
> Not my case , I have intel driver.
Also the Xorg-configure command comes with errors!

What errors?

---

### Post by vagelism on 2012-09-23
> **wojox said:**
> What errors?

First of all I can not run Xorg -configure while x runing so I type:

```
X :1 -configure
```

and the results are:


```
unknown@unknown-pc:~$ sudo X :1 -configure

X.Org X Server 1.11.3
Release Date: 2011-12-16
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.42-26-generic i686 Ubuntu
Current Operating System: Linux unknown-pc 3.2.0-30-generic #48-Ubuntu SMP Fri Aug 24 16:54:40 UTC 2012 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-30-generic root=UUID=edf149b6-89ee-4922-9f76-cfb42f36ff79 ro quiet splash vt.handoff=7
Build Date: 04 August 2012  01:51:24AM
xorg-server 2:1.11.4-0ubuntu10.7 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.24.4
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.1.log", Time: Sun Sep 23 09:44:10 2012
List of video drivers:
	r128
	s3
	vmware
	neomagic
	ati
	geode
	mga
	sisusb
	trident
	nouveau
	sis
	intel
	tdfx
	savage
	qxl
	openchrome
	mach64
	ztv
	siliconmotion
	radeon
	cirrus
	fbdev
	vesa
(++) Using config file: "/home/unknown/xorg.conf.new"
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
Number of created screens does not match number of detected devices.
  Configuration failed.
 ddxSigGiveUp: Closing log
Server terminated with error (2). Closing log file.

```

---

### Post by DenHeldert on 2013-02-12
Boot into recovery mode and select Root Shell. Then run:

```
X -configure
```

Then:

```
cp /root/xorg.conf.new /etc/X11/xorg.conf
```

Reboot and you can edit the new Xorg.conf

---

