---
title: "Chromebook - Screen goes black when launching ubuntu"
date: 2017-11-13
forum: New to Ubuntu
---

### Post by henrikssonlucas on 2017-11-13
When I try to launch ubuntu, all I get is a black screen with the mouse cursor visible.

```
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&amp]chronos@localhost / $ sudo startunity[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&amp]Entering /mnt/stateful_partition/crouton/chroots/trusty...[/FONT][/COLOR]

[COLOR=rgba(0, 0, 0, 0.87)][FONT=&amp]_XSERVTransmkdir: Owner of /tmp/.X11-unix should be set to root[/FONT][/COLOR]

[X.Org]("http://x.org/")[COLOR=rgba(0, 0, 0, 0.87)][FONT=&amp] X Server 1.15.1[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&amp]Release Date: 2014-04-13[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&amp]X Protocol Version 11, Revision 0[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&amp]Build Operating System: Linux 4.4.0-97-generic x86_64 Ubuntu[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&amp]Current Operating System: Linux localhost 3.14.0 #1 SMP PREEMPT Tue Nov 7 03:27:09 PST 2017 x86_64[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&amp]Kernel command line: cros_secure console= loglevel=7 init=/sbin/init cros_secure oops=panic panic=-1 root=/dev/dm-0 rootwait ro dm_verity.error_behavior=3 dm_verity.max_bios=-1 dm_verity.dev_wait=1 dm="1 vroot none ro 1,0 3584000 verity payload=PARTUUID=8f7f09fd-3fa9-c04b-8582-dd9473131ef9/PARTNROFF=1 hashtree=PARTUUID=8f7f09fd-3fa9-c04b-8582-dd9473131ef9/PARTNROFF=1 hashstart=3584000 alg=sha1 root_hexdigest=8ee125e1ad6990685678c87e3d115879675b76d9 salt=8f3445403bb16efc755979d0ee0f4c1133bf124b16ff7af09d6e3890c24ac050" noinitrd vt.global_cursor_default=0 kern_guid=8f7f09fd-3fa9-c04b-8582-dd9473131ef9 add_efi_memmap boot=local noresume noswap i915.modeset=1 tpm_tis.force=1 tpm_tis.interrupts=0 nmi_watchdog=panic,lapic i915.enable_psr=1  [/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&amp]Build Date: 13 October 2017  01:59:06PM[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&amp]xorg-server 2:1.15.1-0ubuntu2.11 (For technical support please see [/FONT][/COLOR][http://www.ubuntu.com/support](http://www.ubuntu.com/support)[COLOR=rgba(0, 0, 0, 0.87)][FONT=&amp]) [/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&amp]Current version of pixman: 0.30.2[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&amp]        Before reporting problems, check [/FONT][/COLOR][http://wiki.x.org]("http://wiki.x.org/")
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&amp]        to make sure that you have the latest version.[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&amp]Markers: (--) probed, (**) from config file, (==) default setting,[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&amp]        (++) from command line, (!!) notice, (II) informational,[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&amp]        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&amp](++) Log file: "/tmp/Xorg.crouton.2.log", Time: Mon Nov 13 09:39:31 2017[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&amp](==) Using system config directory "/usr/share/X11/xorg.conf.d"[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&amp]Initializing built-in extension Generic Event Extension[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&amp]Initializing built-in extension SHAPE[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&amp]Initializing built-in extension MIT-SHM[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&amp]Initializing built-in extension XInputExtension[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&amp]Initializing built-in extension XTEST[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&amp]Initializing built-in extension BIG-REQUESTS[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&amp]Initializing built-in extension SYNC[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&amp]Initializing built-in extension XKEYBOARD[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&amp]Initializing built-in extension XC-MISC[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&amp]Initializing built-in extension SECURITY[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&amp]Initializing built-in extension XINERAMA[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&amp]Initializing built-in extension XFIXES[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&amp]Initializing built-in extension RENDER[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&amp]Initializing built-in extension RANDR[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&amp]Initializing built-in extension COMPOSITE[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&amp]Initializing built-in extension DAMAGE[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&amp]Initializing built-in extension MIT-SCREEN-SAVER[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&amp]Initializing built-in extension DOUBLE-BUFFER[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&amp]Initializing built-in extension RECORD[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&amp]Initializing built-in extension DPMS[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&amp]Initializing built-in extension Present[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&amp]Initializing built-in extension DRI3[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&amp]Initializing built-in extension X-Resource[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&amp]Initializing built-in extension XVideo[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&amp]Initializing built-in extension XVideo-MotionCompensation[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&amp]Initializing built-in extension SELinux[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&amp]Initializing built-in extension XFree86-VidModeExtension[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&amp]Initializing built-in extension XFree86-DGA[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&amp]Initializing built-in extension XFree86-DRI[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&amp]Initializing built-in extension DRI2[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&amp]Loading extension GLX[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&amp]Error org.freedesktop.DBus.Error.UnknownMethod: Method "ReleaseDisplayOwnership" with signature "" on interface "org.chromium.LibCrosServiceInterface" doesn't exist[/FONT][/COLOR]

[COLOR=rgba(0, 0, 0, 0.87)][FONT=&amp]xf86EnableIOPorts: failed to set IOPL for I/O (Operation not permitted)[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&amp]Error executing command as another user: Not authorized[/FONT][/COLOR]

[COLOR=rgba(0, 0, 0, 0.87)][FONT=&amp]This incident has been reported.[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&amp]crouton: version 1-20171109145451~master:35a16889[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&amp]release: trusty[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&amp]architecture: amd64[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&amp]xmethod: xorg[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&amp]targets: xorg,xiwi,unity,extension[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&amp]host: version 10106.0.0 (Official Build) dev-channel samus [/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&amp]kernel: Linux localhost 3.14.0 #1 SMP PREEMPT Tue Nov 7 03:27:09 PST 2017 x86_64 x86_64 x86_64 GNU/Linux[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&amp]freon: yes[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&amp]Another instance of croutonclip running, waiting...[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&amp]Another instance of croutontriggerd running, waiting...[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&amp](II) AIGLX: Suspending AIGLX clients for VT switch[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.87)][FONT=&amp]Error org.freedesktop.DBus.Error.UnknownMethod: Method "TakeDisplayOwnership" with signature "" on interface "org.chromium.LibCrosServiceInterface" doesn't exist[/FONT][/COLOR] 
```

---

