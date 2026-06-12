---
title: "Ubuntu 12.04 (?) wont start after i restarted chromebook"
date: 2016-11-27
forum: New to Ubuntu
---

### Post by solaremoon on 2016-11-27
Okay, I've never used a Chromebook before or Linux or Ubuntu whatever, but I installed Ubuntu unity through the console/crouton like it told me to and I started it just fine. I added things like steam, and I started to add terraria and I added opera. I rebooted the computer because it started lagging and for the second time, now it wont start Linux when i put the command in the console. I installed kde before and tried installing steam on that which failed, so i thought if i restart the computer it might work. Then it wouldn't reopen with the console when i put in sudo startkde, so i reset the computer and installed unity instead. Steam installed perfectly on unity, i could message friends, install games. But then i restarted the computer because it was laggy and wouldn't continue downloading. Now it wont open when i put in the console sudo startunity. It brings up this error.
Also, in my opinion i kind of think steam might be the problem.

```
[COLOR=#000000]crosh> shell
[/COLOR]chronos@localhost / $ sudo startunity
Entering /mnt/stateful_partition/crouton/chroots/precise...

_XSERVTransmkdir: ERROR: euid != 0,directory /tmp/.X11-unix will not be created.

X.Org X Server 1.11.3
Release Date: 2011-12-16
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.42-61-generic x86_64 Ubuntu
Current Operating System: Linux localhost 3.10.18 #1 SMP Tue Nov 15 03:05:12 PST 2016 x86_64
Kernel command line: cros_secure console= loglevel=7 init=/sbin/init cros_secure oops=panic panic=-1 root=/dev/dm-0 rootwait ro dm_verity.error_behavior=3 dm_verity.max_bios=-1 dm_verity.dev_wait=1 dm="1 vroot none ro 1,0 2539520 verity payload=PARTUUID=e3809605-25b1-ae47-8883-9c14c8bb5df1/PARTNROFF=1 hashtree=PARTUUID=e3809605-25b1-ae47-8883-9c14c8bb5df1/PARTNROFF=1 hashstart=2539520 alg=sha1 root_hexdigest=88aa7c671f1ce0ae0af67892df20f8d2257e23b8 salt=44de902dc32a6bd4684eac63294e61f88fc50c0057248dfcc684f0c52f918bd2" noinitrd vt.global_cursor_default=0 kern_guid=e3809605-25b1-ae47-8883-9c14c8bb5df1 add_efi_memmap boot=local noresume noswap i915.modeset=1 tpm_tis.force=1 tpm_tis.interrupts=0 nmi_watchdog=panic,lapic  
Build Date: 12 February 2015  02:49:01PM
xorg-server 2:1.11.4-0ubuntu10.17 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.30.2
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(++) Log file: "/tmp/Xorg.crouton.1.log", Time: Sun Nov 27 17:33:58 2016
(==) Using system config directory "/usr/share/X11/xorg.conf.d"

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
         at http://wiki.x.org
 for help. 
Please also check the log file at "/tmp/Xorg.crouton.1.log" for additional information.

 ddxSigGiveUp: Closing log
Server terminated with error (1). Closing log file.
/usr/bin/xinit: giving up
/usr/bin/xinit: unable to connect to X server: No such file or directory
/usr/bin/xinit: server error [COLOR=#000000]Unmounting /mnt/stateful_partition/crouton/chroots/precise...[/COLOR]
chronos@localhost / $ sudo startunity
Entering /mnt/stateful_partition/crouton/chroots/precise...

_XSERVTransmkdir: ERROR: euid != 0,directory /tmp/.
```

---

### Post by mörgæs on 2016-11-28
Why did you pick 12.04 when several newer releases exist?

---

### Post by solaremoon on 2016-11-28
i didn't pick 12.04, it gave me that, idk how to pick a version

---

### Post by solaremoon on 2016-11-28
[FONT=arial][FONT=georgia]when i download crouton and do[/FONT]:[/FONT] [COLOR=#a9a9a9][FONT=Consolas]sudo sh ~/Downloads/crouton -t xfce[/FONT][/COLOR][COLOR=#333333][FONT=Consolas]
[/FONT][/COLOR][FONT=Consolas][FONT=georgia]or unity or kde, it keeps installing precise pangolin or 12.04, i want to install 16.04 but i can't find anywhere how to do that without doing the impossible with downloading it directly from the site, its 25gb, i'm on a chromebook and it doesn't have that much space.[/FONT][/FONT][COLOR=#333333][FONT=Consolas][/FONT][/COLOR]

---

### Post by mörgæs on 2016-12-03
Sorry, I don't know enough about Crouton. 
Hoping someone else is able to point you in the right direction.

---

