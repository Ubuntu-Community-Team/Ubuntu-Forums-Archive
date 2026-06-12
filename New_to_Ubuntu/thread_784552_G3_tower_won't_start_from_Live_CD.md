---
title: "G3 tower won't start from Live CD"
date: 2008-05-06
forum: New to Ubuntu
---

### Post by mzurligen1 on 2008-05-06
I'm trying to get Ubuntu onto an old G3 machine, about  8 years old. I haven't gotten it to start up completely yet from the live CD. The Issues I'm having seem to be related to the 2 graphics cards in the tower: and old ATI, and an older ATI. 
With the monitor connected to the older card, it skips  yaboot and goes right to the splash screen, where it freezes.
If I start it with the monitor connected to the less-old card, then I can select an image in yaboot.
I have to specify "video=ofonly" or it freezes on the white screen, and one of the "nosplash" options, or else it freezes before the spalsh screen appears.

If I can get past these two problems(only by typing "live-nosplash-powerpc video=ofonly" in yaboot), then things start starting-up. Everything seems OK for a minute, then suddenly the screen clears, and is replaced with this:

```
*** glibc detected *** /usr/bin/X: free(): invalid pointer: 0x101f0000 ***
======= Backtrace: =========
/lib/libc.so.6[0xfbce3d8]
/lib/libc.so.6(cfree+0xc8)[0xfbd0858]
/lib/libc.so.6(closedir+0x34)[0xfbf5c14]
/usr/bin/X(chooseVideoDriver+0x3a0)[0x100943c0]
/usr/bin/X(autoConfigDevice+0xf4)[0x10094624]
/usr/bin/X(InitOutput+0x7ac)[0x1007041c]
/usr/bin/X(main+0x2e8)[0x1002bb08]
/lib/libc.so.6[0xfb6db10]
/lib/libc.so.6[0xfb6dcd0]
======= Memory map: ========
00100000-00103000 r-xp 00100000 00:00 0         [vdso]
0f813000-0f820000 r-xp 00000000 07:00 82922     /rofs/usr/lib/libdrm.so.2.3.0
0f820000-0f82f000 ---p 0000d000 07:00 82922     /rofs/usr/lib/libdrm.so.2.3.0
0f82f000-0f830000 rw-p 0000c000 07:00 82922     /rofs/usr/lib/libdrm.so.2.3.0
0f840000-0f84b000 r-xp 00000000 07:00 86458     /rofs/usr/lib/xorg/modules/extensions/libdri.so
0f84b000-0f85a000 ---p 0000b000 07:00 86458     /rofs/usr/lib/xorg/modules/extensions/libdri.so
0f85a000-0f85b000 rw-p 0000a000 07:00 86458     /rofs/usr/lib/xorg/modules/extensions/libdri.so
0f86b000-0f873000 r-xp 00000000 07:00 86461     /rofs/usr/lib/xorg/modules/extensions/librecord.so
0f873000-0f883000 ---p 00008000 07:00 86461     /rofs/usr/lib/xorg/modules/extensions/librecord.so
0f883000-0f884000 rw-p 00008000 07:00 86461     /rofs/usr/lib/xorg/modules/extensions/librecord.so
0f894000-0f896000 r-xp 00000000 07:00 86463     /rofs/usr/lib/xorg/modules/font
bfc5d000-bfc72000 rw-p bffeb000 00:00 0         [stack]ib/ld-2.7.so.so.so.1.4.1
```

Here it freezes.
Any suggestions? Should I pull out the old card? Is this not really a graphics issue?:confused:

---

### Post by mapes12 on 2008-05-06
Remove one of the graphics cards from the tower, preferably the older one but see which is recognised best. And use the alternate CD iso instead of the Live CD so that you can control the screen resolution at install. F4 at the first installation screen will give you your options. (only 7.10 supports this). 8.04 has screen res issues.

---

### Post by mzurligen1 on 2008-05-07
I removed the older card(an ATI mach 64, the newer one is a rage 128 ), and am waiting on the 7.10 download. I tried starting from the 8.04 Live CD while I wait, and I don't get the error anymore, and it seems it started up, but the GUI didn't start. I'm left staring at the command line, and my bash skillz are weak. 
I guess I can just read the man pages till the download finishes on my other mac.:???:
How do I start up the GUI from the shell?

---

### Post by mapes12 on 2008-05-07
> How do I start up the GUI from the shell?

Go to this page: [http://www.aboutdebian.com/packages.htm](http://www.aboutdebian.com/packages.htm)

Scroll to just over half way down the page where there are instructions for starting a basic GUI from the command line.

---

### Post by mzurligen1 on 2008-05-07
More problems:(

I typed "startx" like the link you gave me told me to do, but I got some errors. I'm left with a screen like this:

```

X.Org X Server 1.4.0.90
Release Date: 5 September 2007
X Protocol Version 11, Revision 0
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9)
Current Operating System: Linux ubuntu 2.6.24-16-powerpc #1 Thu Apr 10 12:48:35 UTC 2008 ppc
Build Date: 15 April 2008  07:53:08PM

        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Module Loader present
Markers: (--) probed. (**) from config file. (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed May  7 14:15:33 2008
(==) Using config file: "/etc/X11/xorg.conf"
(WW) ****INVALID IO ALLOCATION**** b: 0xfe002000 e: 0xfe0020ff correcting
(EE) end of block range 0xfdffffff < begin 0xfe000000
(EE) R128(0): mmap mmio: Invalid argument

Backtrace:
0: /usr/bin/X11/X(xf8sSigHandler+0x94) [0x10092df4]
1: [0x100344]
2: /usr/lib/xorg/modules/drivers//r128_drv.so(R128PreInit+0x1054) [0xf7c5374]
3: /usr/bin/X11/X(InitOutput+0xb9c) [0x1007080c]
4: /usr/bin/X11/X(main+0x2e8) [0x1002bb08]
5: /lib/libc.so.6 [0xfb6db10]
6: /lib/libc.so.6 [0xfb6dcd0]

Fatal server error:
Caught signal 11. Server aborting


waiting for X server to begin accepting connections
giving up.
xinit:  Connection reset by peer (errno 104):  unable to connect to X server
xinit:  No such process (errno 3): Server error.

```
And I'm back at the prompt. There were a dozen or so more lines that scrolled off the top of the screen too fast for me to read.
 I seem to remember reading about a problem with Ubuntu 8.04 and ATI cards. In the "backtrace" section, line 2, it seems to be interacting with the Rage 128 driver, if I'm reading it right. Any Ideas?
2 hours to go on my 7.10 download.

update: I tried swapping out the Rage 128 for the older Mach 64 just to see what would happen. It starts up exactly the same, all the way up to X server failing and leaving me at the command line. X seems to fail for slightly different reasons though. The error messages seemed to be saying that the older card lacked certain features that the window manager needed, and no display was found.

---

