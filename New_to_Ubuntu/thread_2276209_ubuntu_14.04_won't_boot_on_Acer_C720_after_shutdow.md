---
title: "ubuntu 14.04 won't boot on Acer C720 after shutdown"
date: 2015-04-30
forum: New to Ubuntu
---

### Post by Jayfin on 2015-04-30
I installed ubuntu on my son's Acer c720. He always turns of his computer by pressing and holding the power button. Ubuntu always bits up fine after this. I used his computer tonight and shut it down from the start menu. Ubuntu would not bout after this and I get the following error. 

```
crosh> shell chronos@localhost / $ sudo startunity Password: Enter encryption passphrase for trusty: Entering /usr/local/chroots/trusty... ERROR: ld.so: object '/usr/local/lib/croutonfreon.so' from LD_PRELOAD cannot be preloaded (cannot open shared object file): ignored. _XSERVTransmkdir: ERROR: euid != 0,directory /tmp/.X11-unix will not be created. X.Org X Server 1.15.1 Release Date: 2014-04-13 X Protocol Version 11, Revision 0 Build Operating System: Linux 3.2.0-76-generic x86_64 Ubuntu Current Operating System: Linux localhost 3.8.11 #1 SMP Tue Apr 14 18:57:27 PDT 2015 x86_64 Kernel command line: cros_secure console= loglevel=7 init=/sbin/init cros_secure oops=panic panic=-1 root=/dev/dm-0 rootwait ro dm_verity.error_behavior=3 dm_verity.max_bios=-1 dm_verity.dev_wait=1 dm="1 vroot none ro 1,0 2506752 verity payload=PARTUUID=099cd7d7-cadb-7040-9095-0f14f26fe098/PARTNROFF=1 hashtree=PARTUUID=099cd7d7-cadb-7040-9095-0f14f26fe098/PARTNROFF=1 hashstart=2506752 alg=sha1 root_hexdigest=a066bff2dc004585fe2b5c44be0c33ce6314a3a4 salt=d9d62c9699d89416b72843e002fe7a0e273b0d9678a826be2a1517e0e06658ae" noinitrd vt.global_cursor_default=0 kern_guid=099cd7d7-cadb-7040-9095-0f14f26fe098 add_efi_memmap boot=local noresume noswap i915.modeset=1 tpm_tis.force=1 tpm_tis.interrupts=0 nmi_watchdog=panic,lapic iTCO_vendor_support.vendorsupport=3 Build Date: 12 February 2015 02:49:29PM xorg-server 2:1.15.1-0ubuntu2.7 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) Current version of pixman: 0.30.2 Before reporting problems, check [http://wiki.x.org](http://wiki.x.org) to make sure that you have the latest version. Markers: (--) probed, (**) from config file, (==) default setting, (++) from command line, (!!) notice, (II) informational, (WW) warning, (EE) error, (NI) not implemented, (??) unknown. (++) Log file: "/tmp/Xorg.crouton.1.log", Time: Thu Apr 30 20:44:06 2015 (==) Using system config directory "/usr/share/X11/xorg.conf.d" (EE) (EE) Backtrace: (EE) 0: /usr/bin/Xorg (xorg_backtrace+0x48) [0x7f6924a57848] (EE) 1: /usr/bin/Xorg (0x7f69248ae000+0x1ad539) [0x7f6924a5b539] (EE) 2: /lib/x86_64-linux-gnu/libpthread.so.0 (0x7f69239aa000+0x10340) [0x7f69239ba340] (EE) 3: /usr/bin/Xorg (0x7f69248ae000+0xb57a6) [0x7f69249637a6] (EE) 4: /usr/bin/Xorg (xf86BusProbe+0x9) [0x7f6924937099] (EE) 5: /usr/bin/Xorg (InitOutput+0x74d) [0x7f69249456fd] (EE) 6: /usr/bin/Xorg (0x7f69248ae000+0x59bab) [0x7f6924907bab] (EE) 7: /lib/x86_64-linux-gnu/libc.so.6 (__libc_start_main+0xf5) [0x7f69223eaec5] (EE) 8: /usr/bin/Xorg (0x7f69248ae000+0x451ee) [0x7f69248f31ee] (EE) (EE) Segmentation fault at address 0x0 (EE) Fatal server error: (EE) Caught signal 11 (Segmentation fault). Server aborting (EE) (EE) Please consult the The X.Org Foundation support at [http://wiki.x.org](http://wiki.x.org) for help. (EE) Please also check the log file at "/tmp/Xorg.crouton.1.log" for additional information. (EE) (EE) Server terminated with error (1). Closing log file. /usr/bin/xinit: giving up /usr/bin/xinit: unable to connect to X server: Connection refused /usr/bin/xinit: server error Unmounting /usr/local/chroots/trusty... chronos@localhost / $ crosh> shell bash: shell: Read-only file system chronos@localhost / $ chronos@localhost / $ sudo startunity bash: chronos@localhost: command not found chronos@localhost / $ Password: bash: Password:: command not found chronos@localhost / $ Enter encryption passphrase for trusty: bash: Enter: command not found chronos@localhost / $ Entering /usr/local/chroots/trusty... bash: Entering: command not found chronos@localhost / $ chronos@localhost / $ ERROR: ld.so: object '/usr/local/lib/croutonfreon.so' from LD_PRELOAD cannot be preloaded (cannot open shared object file): ignored. bash: syntax error near unexpected token `(' chronos@localhost / $ _XSERVTransmkdir: ERROR: euid != 0,directory /tmp/.X11-unix will not be created. bash: _XSERVTransmkdir:: command not found chronos@localhost / $ chronos@localhost / $ X.Org X Server 1.15.1 bash: X.Org: command not found chronos@localhost / $ Release Date: 2014-04-13 bash: Release: command not found chronos@localhost / $ X Protocol Version 11, Revision 0 bash: X: command not found chronos@localhost / $ Build Operating System: Linux 3.2.0-76-generic x86_64 Ubuntu bash: Build: command not found chronos@localhost / $ Current Operating System: Linux localhost 3.8.11 #1 SMP Tue Apr 14 18:57:27 PDT 2015 x86_64 bash: Current: command not found chronos@localhost / $ Kernel command line: cros_secure console= loglevel=7 init=/sbin/init cros_secure oops=panic panic=-1 root=/dev/dm-0 rootwait ro dm_verity.error_behavior=3 dm_verity.max_bios=-1 dm_verity.dev_wait=1 dm="1 vroot none ro 1,0 2506752 verity payload=PARTUUID=099cd7d7-cadb-7040-9095-0f14f26fe098/PARTNROFF=1 hashtree=PARTUUID=099cd7d7-cadb-7040-9095-0f14f26fe098/PARTNROFF=1 hashstart=2506752 alg=sha1 root_hexdigest=a066bff2dc004585fe2b5c44be0c33ce6314a3a4 salt=d9d62c9699d89416b72843e002fe7a0e273b0d9678a826be2a1517e0e06658ae" noinitrd vt.global_cursor_default=0 kern_guid=099cd7d7-cadb-7040-9095-0f14f26fe098 add_efi_memmap boot=local noresume noswap i915.modeset=1 tpm_tis.force=1 tpm_tis.interrupts=0 nmi_watchdog=panic,lapic iTCO_vendor_support.vendorsupport=3 bash: Kernel: command not found chronos@localhost / $ Build Date: 12 February 2015 02:49:29PM bash: Build: command not found chronos@localhost / $ xorg-server 2:1.15.1-0ubuntu2.7 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) bash: syntax error near unexpected token `(' chronos@localhost / $ Current version of pixman: 0.30.2 bash: Current: command not found chronos@localhost / $ Before reporting problems, check [http://wiki.x.org](http://wiki.x.org) bash: Before: command not found chronos@localhost / $ to make sure that you have the latest version. bash: to: command not found chronos@localhost / $ Markers: (--) probed, (**) from config file, (==) default setting, bash: syntax error near unexpected token `--' chronos@localhost / $ (++) from command line, (!!) notice, (II) informational, (++) from command line, (Markers: (--) probed, (**) from config file, (==) default setting,) notice, (II) informational, bash: syntax error near unexpected token `from' chronos@localhost / $ (WW) warning, (EE) error, (NI) not implemented, (??) unknown. bash: syntax error near unexpected token `warning,' chronos@localhost / $ (++) Log file: "/tmp/Xorg.crouton.1.log", Time: Thu Apr 30 20:44:06 2015 bash: syntax error near unexpected token `Log' chronos@localhost / $ (==) Using system config directory "/usr/share/X11/xorg.conf.d" bash: syntax error near unexpected token `Using' chronos@localhost / $ (EE) bash: EE: command not found chronos@localhost / $ (EE) Backtrace: bash: syntax error near unexpected token `Backtrace:' chronos@localhost / $ (EE) 0: /usr/bin/Xorg (xorg_backtrace+0x48) [0x7f6924a57848] bash: syntax error near unexpected token `0:' chronos@localhost / $ (EE) 1: /usr/bin/Xorg (0x7f69248ae000+0x1ad539) [0x7f6924a5b539] bash: syntax error near unexpected token `1:' chronos@localhost / $ (EE) 2: /lib/x86_64-linux-gnu/libpthread.so.0 (0x7f69239aa000+0x10340) [0x7f69239ba340] bash: syntax error near unexpected token `2:' chronos@localhost / $ (EE) 3: /usr/bin/Xorg (0x7f69248ae000+0xb57a6) [0x7f69249637a6] bash: syntax error near unexpected token `3:' chronos@localhost / $ (EE) 4: /usr/bin/Xorg (xf86BusProbe+0x9) [0x7f6924937099] bash: syntax error near unexpected token `4:' chronos@localhost / $ (EE) 5: /usr/bin/Xorg (InitOutput+0x74d) [0x7f69249456fd] bash: syntax error near unexpected token `5:' chronos@localhost / $ (EE) 6: /usr/bin/Xorg (0x7f69248ae000+0x59bab) [0x7f6924907bab] bash: syntax error near unexpected token `6:' chronos@localhost / $ (EE) 7: /lib/x86_64-linux-gnu/libc.so.6 (__libc_start_main+0xf5) [0x7f69223eaec5] bash: syntax error near unexpected token `7:' chronos@localhost / $ (EE) 8: /usr/bin/Xorg (0x7f69248ae000+0x451ee) [0x7f69248f31ee] bash: syntax error near unexpected token `8:' chronos@localhost / $ (EE) bash: EE: command not found chronos@localhost / $ (EE) Segmentation fault at address 0x0 bash: syntax error near unexpected token `Segmentation' chronos@localhost / $ (EE) bash: EE: command not found chronos@localhost / $ Fatal server error: bash: Fatal: command not found chronos@localhost / $ (EE) Caught signal 11 (Segmentation fault). Server aborting bash: syntax error near unexpected token `Caught' chronos@localhost / $ (EE) bash: EE: command not found chronos@localhost / $ (EE) bash: EE: command not found chronos@localhost / $ Please consult the The X.Org Foundation support bash: Please: command not found chronos@localhost / $ at [http://wiki.x.org](http://wiki.x.org) bash: at: command not found chronos@localhost / $ for help. > (EE) Please also check the log file at "/tmp/Xorg.crouton.1.log" for additional information. bash: syntax error near unexpected token `(' chronos@localhost / $ (EE) bash: EE: command not found chronos@localhost / $ (EE) Server terminated with error (1). Closing log file. bash: syntax error near unexpected token `Server' chronos@localhost / $ /usr/bin/xinit: giving up bash: /usr/bin/xinit:: No such file or directory chronos@localhost / $ /usr/bin/xinit: unable to connect to X server: Connection refused bash: /usr/bin/xinit:: No such file or directory chronos@localhost / $ /usr/bin/xinit: server error bash: /usr/bin/xinit:: No such file or directory chronos@localhost / $ Unmounting /usr/local/chroots/trusty...
```


I am new to ubuntu and don't know a lot about it. I installed it on my son's chromebook so he could play minecraft. I am going someone can help me fix this problem so I don't have to install it again. I don't want him to lose everything he installed on the ubuntu OS.I thank you in advance for any help you can provide. 
Jason

---

### Post by wildmanne39 on 2015-05-01
Please use code tags.

After you type the command copy and paste it here by clicking new reply then above the window you click on # and put the information in between the two code boxes.

---

### Post by lindee-keller on 2015-05-02
Hi, Jayfin. I'm having the same problem. Here's what's happening for me:

```


chronos@localhost / $ sudo startunity
Entering /mnt/stateful_partition/crouton/chroots/trusty...


X.Org X Server 1.15.1
Release Date: 2014-04-13
X Protocol Version 11, Revision 0
Build Operating System: Linux 3.2.0-61-generic x86_64 Ubuntu
Current Operating System: Linux localhost 3.10.18 #1 SMP Tue Apr 14 18:59:06 PDT 2015 x86_64
Kernel command line: cros_secure console= loglevel=7 init=/sbin/init cros_secure oops=panic panic=-1 root=/dev/dm-0 rootwait ro dm_verity.error_behavior=3 dm_verity.max_bios=-1 dm_verity.dev_wait=1 dm="1 vroot none ro 1,0 2506752 verity payload=PARTUUID=db5e6fad-1ba0-7341-afb6-b29da4aa9b1d/PARTNROFF=1 hashtree=PARTUUID=db5e6fad-1ba0-7341-afb6-b29da4aa9b1d/PARTNROFF=1 hashstart=2506752 alg=sha1 root_hexdigest=3d41fbcacc4111aade908a95e4998f4a5865c8c0 salt=341aac542a363846309038a85e8237e7844173c36ad747a6f9744377a5b4d8d5" noinitrd vt.global_cursor_default=0 kern_guid=db5e6fad-1ba0-7341-afb6-b29da4aa9b1d add_efi_memmap boot=local noresume noswap i915.modeset=1 tpm_tis.force=1 tpm_tis.interrupts=0 nmi_watchdog=panic,lapic  
Build Date: 09 December 2014  11:14:53PM
xorg-server 2:1.15.1-0ubuntu2.5 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.30.2
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.1.log", Time: Sat May  2 09:07:37 2015
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
(EE) 
(EE) Backtrace:
(EE) 0: /usr/bin/X (xorg_backtrace+0x48) [0x7f513da3a338]
(EE) 1: /usr/bin/X (0x7f513d891000+0x1ad029) [0x7f513da3e029]
(EE) 2: /lib/x86_64-linux-gnu/libpthread.so.0 (0x7f513c98e000+0x10340) [0x7f513c99e340]
(EE) 3: /usr/bin/X (0x7f513d891000+0xb5346) [0x7f513d946346]
(EE) 4: /usr/bin/X (xf86BusProbe+0x9) [0x7f513d919d69]
(EE) 5: /usr/bin/X (InitOutput+0x74d) [0x7f513d9282bd]
(EE) 6: /usr/bin/X (0x7f513d891000+0x5985b) [0x7f513d8ea85b]
(EE) 7: /lib/x86_64-linux-gnu/libc.so.6 (__libc_start_main+0xf5) [0x7f513b3cdec5]
(EE) 8: /usr/bin/X (0x7f513d891000+0x44eae) [0x7f513d8d5eae]
(EE) 
(EE) Segmentation fault at address 0x0
(EE) 
Fatal server error:
(EE) Caught signal 11 (Segmentation fault). Server aborting
(EE) 
(EE) 
Please consult the The X.Org Foundation support 
         at http://wiki.x.org
 for help. 
(EE) Please also check the log file at "/var/log/Xorg.1.log" for additional information.
(EE) 
(EE) Server terminated with error (1). Closing log file.
/usr/bin/xinit: giving up
/usr/bin/xinit: unable to connect to X server: Connection refused
/usr/bin/xinit: server error
Not unmounting /mnt/stateful_partition/crouton/chroots/trusty as another instance is using it.


```

What I think I know so far is that this was caused by an update to Chrome OS without the corresponding update to Xorg. 
But I can't figure out how to manage packages from this shell. No apt-get, no yum, no zypper, no emerge (which is what
Gentoo uses and what a web search told me Chromium uses). Can somebody please help us figure out either how to update Xorg, or
how else to overcome this error and get our Ubuntu back? Thank you.

Also, I wanted to encourage you to not give up and reinstall your Ubuntu yet! There;s probably a solution that doesn't involve 
your son losing his secondary OS.

---

### Post by lindee-keller on 2015-05-02
Jason, I solved it on my machine. The problem is that you need to update crouton after every Chrome OS update, or things will eventually stop working.
Try this:
[FONT=monospace]sudo sh ~/Downloads/crouton -u -n trusty[/FONT]

---

### Post by charlescarroll1 on 2015-05-04
I'm also having a difficult time and it looks like I'm having the same problem. I've ran sudo sh ~/Downloads/crouton -u -n trusty and still not having any luck.

---

