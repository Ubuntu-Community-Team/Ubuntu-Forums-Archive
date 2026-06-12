---
title: "I tried to do update and now when I type sudo start unity it says:"
date: 2015-05-12
forum: New to Ubuntu
---

### Post by alliecat122333 on 2015-05-12
Entering /usr/local/chroots/precise...


X.Org X Server 1.15.1
Release Date: 2014-04-13
X Protocol Version 11, Revision 0
Build Operating System: Linux 3.2.0-76-generic x86_64 Ubuntu
Current Operating System: Linux localhost 3.10.18 #1 SMP Mon Apr 27 10:23:37 PDT 2015 x86_64
Kernel command line: cros_secure console= loglevel=7 init=/sbin/init cros_secure oops=panic panic=-1 root=/dev/dm-0 rootwait ro dm_verity.error_behavior=3 dm_verity.max_bios=-1 dm_verity.dev_wait=1 dm="1 vroot none ro 1,0 2506752 verity payload=PARTUUID=5872824d-a795-2b48-b857-f9ee802c406e/PARTNROFF=1 hashtree=PARTUUID=5872824d-a795-2b48-b857-f9ee802c406e/PARTNROFF=1 hashstart=2506752 alg=sha1 root_hexdigest=6181af1357991b3b9bdc63c62200c9c8f43ed73c salt=3122153d7cd99fa26e7db14046aeb06c369dfc94b7095714eb0ffcdb337de7ab" noinitrd vt.global_cursor_default=0 kern_guid=5872824d-a795-2b48-b857-f9ee802c406e add_efi_memmap boot=local noresume noswap i915.modeset=1 tpm_tis.force=1 tpm_tis.interrupts=0 nmi_watchdog=panic,lapic  
Build Date: 12 February 2015  02:49:29PM
xorg-server 2:1.15.1-0ubuntu2.7 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
Current version of pixman: 0.30.2
        Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
        to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.1.log", Time: Mon May 11 23:19:58 2015
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
(EE) 
(EE) Backtrace:
(EE) 0: /usr/bin/X (xorg_backtrace+0x48) [0x7f94ef0cc848]
(EE) 1: /usr/bin/X (0x7f94eef23000+0x1ad539) [0x7f94ef0d0539]
(EE) 2: /lib/x86_64-linux-gnu/libpthread.so.0 (0x7f94ee01f000+0x10340) [0x7f94ee02f340]
(EE) 3: /usr/bin/X (0x7f94eef23000+0xb57a6) [0x7f94eefd87a6]
(EE) 4: /usr/bin/X (xf86BusProbe+0x9) [0x7f94eefac099]
(EE) 5: /usr/bin/X (InitOutput+0x74d) [0x7f94eefba6fd]
(EE) 6: /usr/bin/X (0x7f94eef23000+0x59bab) [0x7f94eef7cbab]
(EE) 7: /lib/x86_64-linux-gnu/libc.so.6 (__libc_start_main+0xf5) [0x7f94eca5fec5]
(EE) 8: /usr/bin/X (0x7f94eef23000+0x451ee) [0x7f94eef681ee]
(EE) 
(EE) Segmentation fault at address 0x0
(EE) 
Fatal server error:
(EE) Caught signal 11 (Segmentation fault). Server aborting
(EE) 
(EE) 
Please consult the The X.Org Foundation support 
         at [http://wiki.x.org](http://wiki.x.org)
 for help. 
(EE) Please also check the log file at "/var/log/Xorg.1.log" for additional information.
(EE) 
(EE) Server terminated with error (1). Closing log file.
/usr/bin/xinit: giving up
/usr/bin/xinit: unable to connect to X server: Connection refused
/usr/bin/xinit: server error
Not unmounting /usr/local/chroots/precise as another instance is using it.

While ubuntu was updating it said Could not install initscripts. Subprocess installed post-installation script returned error exit status 1

Later the updating stuff on screen disappeared and then ubuntu froze.  That was the last of ubuntu.

---

### Post by sandyd on 2015-05-12
Is this a chromebook?

---

### Post by alliecat122333 on 2015-05-12
Yes

---

