---
title: "I can't enter Ubuntu!"
date: 2015-08-05
forum: New to Ubuntu
---

### Post by theglamourgroup123 on 2015-08-05
I put in sudo startunity, but this shows up:


Entering /mnt/stateful_partition/crouton/chroots/precise...

_XSERVTransmkdir: Owner of /tmp/.X11-unix should be set to root

X.Org X Server 1.15.1
Release Date: 2014-04-13
X Protocol Version 11, Revision 0
Build Operating System: Linux 3.2.0-76-generic x86_64 Ubuntu
Current Operating System: Linux localhost 3.10.18 #1 SMP Tue Jul 28 16:40:25 PDT 2015 x86_64
Kernel command line: cros_secure console= loglevel=7 init=/sbin/init cros_secure oops=panic panic=-1 root=/dev/dm-0 rootwait ro dm_verity.error_behavior=3 dm_verity.max_bios=-1 dm_verity.dev_wait=1 dm="1 vroot none ro 1,0 2506752 verity payload=PARTUUID=fde9caaa-5c61-f844-a6aa-052c0c96ac89/PARTNROFF=1 hashtree=PARTUUID=fde9caaa-5c61-f844-a6aa-052c0c96ac89/PARTNROFF=1 hashstart=2506752 alg=sha1 root_hexdigest=013533867ffef583ea67c2f06f63bc1a10c4e460 salt=894ce6a3d93e70d9f118acb2e46101fff03feb300fb5dea247ba7aaa213fb810" noinitrd vt.global_cursor_default=0 kern_guid=fde9caaa-5c61-f844-a6aa-052c0c96ac89 add_efi_memmap boot=local noresume noswap i915.modeset=1 tpm_tis.force=1 tpm_tis.interrupts=0 nmi_watchdog=panic,lapic  
Build Date: 12 February 2015  02:49:29PM
xorg-server 2:1.15.1-0ubuntu2.7 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
Current version of pixman: 0.30.2
        Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
        to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(++) Log file: "/tmp/Xorg.crouton.1.log", Time: Wed Aug  5 19:42:09 2015
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
(EE) 
(EE) Backtrace:
(EE) 0: /usr/bin/Xorg (xorg_backtrace+0x48) [0x7fb3bb155848]
(EE) 1: /usr/bin/Xorg (0x7fb3bafac000+0x1ad539) [0x7fb3bb159539]
(EE) 2: /lib/x86_64-linux-gnu/libpthread.so.0 (0x7fb3b9ea5000+0x10340) [0x7fb3b9eb5340]
(EE) 3: /usr/bin/Xorg (0x7fb3bafac000+0xb57a6) [0x7fb3bb0617a6]
(EE) 4: /usr/bin/Xorg (xf86BusProbe+0x9) [0x7fb3bb035099]
(EE) 5: /usr/bin/Xorg (InitOutput+0x74d) [0x7fb3bb0436fd]
(EE) 6: /usr/bin/Xorg (0x7fb3bafac000+0x59bab) [0x7fb3bb005bab]
(EE) 7: /lib/x86_64-linux-gnu/libc.so.6 (__libc_start_main+0xf5) [0x7fb3b88e5ec5]
(EE) 8: /usr/bin/Xorg (0x7fb3bafac000+0x451ee) [0x7fb3baff11ee]
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
(EE) Please also check the log file at "/tmp/Xorg.crouton.1.log" for additional information.
(EE) 
(EE) Server terminated with error (1). Closing log file.
/usr/bin/xinit: giving up
/usr/bin/xinit: unable to connect to X server: Connection refused
/usr/bin/xinit: server error
Unmounting /mnt/stateful_partition/crouton/chroots/precise...

---

### Post by cariboo on 2015-08-05
It would help if you told us what it is you are trying to do.

---

### Post by ozzie1 on 2015-08-06
Is this a fresh install? Which flavor/version? Was it installed from a bootable CD or via wubi, the windows installer?

---

### Post by Vladlenin5000 on 2015-08-06
```
Entering /mnt/stateful_partition/[COLOR=#ff0000]crouton[/COLOR]/chroots/precise...
```

This suggests Chromebook...

---

