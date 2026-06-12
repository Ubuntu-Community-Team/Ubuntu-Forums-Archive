---
title: "System program problem detected error"
date: 2014-01-14
forum: New to Ubuntu
---

### Post by jrs2 on 2014-01-14
I get this error in Ubuntu 12.10.

[http://screencast.com/t/7wwv5VrYOwMN](http://screencast.com/t/7wwv5VrYOwMN)

After a bit of Google seaching (that eventually led me to joining this forum :) ), I found that if I run this from terminal, that it will clear all crash logs and the error will disappear for awhile :** sudo rm /var/crash/***

What would be causing this? The machine runs fine other than that error. It's actually used for digital signage, so having the error in front of the content is annoying. Is there a way to disable the error message without constantly needing to run the above command? And as I mentioned, the machine and content runs fine other than this pop-up.

Below is the content of the log file found in /var/crash/ (before removing it).

Any help is much appreciated.

---

### Post by jrs2 on 2014-01-14
```
ProblemType: Crash
Architecture: i386
Date: Sat Dec 28 12:38:55 2013
DistroRelease: Ubuntu 12.10
ExecutablePath: /usr/bin/Xorg
ExecutableTimestamp: 1365685102
ProcCmdline: /usr/bin/X :0 -core -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch -background none
ProcCwd: /etc/X11
ProcEnviron: 
ProcMaps:
 b6e59000-b6e5d000 r-xp 00000000 08:01 3619       /usr/lib/xorg/modules/libfbdevhw.so
 b6e5d000-b6e5e000 r--p 00003000 08:01 3619       /usr/lib/xorg/modules/libfbdevhw.so
 b6e5e000-b6e5f000 rw-p 00004000 08:01 3619       /usr/lib/xorg/modules/libfbdevhw.so
 b6e5f000-b6e80000 r-xp 00000000 08:01 1569978    /usr/lib/i386-linux-gnu/libdrm_intel.so.1.0.0
 b6e80000-b6e81000 r--p 00020000 08:01 1569978    /usr/lib/i386-linux-gnu/libdrm_intel.so.1.0.0
 b6e81000-b6e82000 rw-p 00021000 08:01 1569978    /usr/lib/i386-linux-gnu/libdrm_intel.so.1.0.0
 b6e83000-b6e87000 r-xp 00000000 08:01 3169       /usr/lib/xorg/modules/drivers/fbdev_drv.so
 b6e87000-b6e88000 r--p 00003000 08:01 3169       /usr/lib/xorg/modules/drivers/fbdev_drv.so
 b6e88000-b6e89000 rw-p 00004000 08:01 3169       /usr/lib/xorg/modules/drivers/fbdev_drv.so
 b6e89000-b6e92000 r-xp 00000000 08:01 3173       /usr/lib/xorg/modules/drivers/modesetting_drv.so
 b6e92000-b6e93000 r--p 00008000 08:01 3173       /usr/lib/xorg/modules/drivers/modesetting_drv.so
 b6e93000-b6e94000 rw-p 00009000 08:01 3173       /usr/lib/xorg/modules/drivers/modesetting_drv.so
 b6e94000-b6fb6000 r-xp 00000000 08:01 1509       /usr/lib/xorg/modules/drivers/intel_drv.so
 b6fb6000-b6fb7000 ---p 00122000 08:01 1509       /usr/lib/xorg/modules/drivers/intel_drv.so
 b6fb7000-b6fba000 r--p 00122000 08:01 1509       /usr/lib/xorg/modules/drivers/intel_drv.so
 b6fba000-b6fbd000 rw-p 00125000 08:01 1509       /usr/lib/xorg/modules/drivers/intel_drv.so
 b6fbd000-b702d000 r-xp 00000000 08:01 3621       /usr/lib/xorg/modules/extensions/libglx.so
 b702d000-b702e000 r--p 00070000 08:01 3621       /usr/lib/xorg/modules/extensions/libglx.so
 b702e000-b7030000 rw-p 00071000 08:01 3621       /usr/lib/xorg/modules/extensions/libglx.so
 b7030000-b706b000 rw-p 00000000 00:00 0 
 b706b000-b7087000 r-xp 00000000 08:01 393168     /lib/i386-linux-gnu/libgcc_s.so.1
 b7087000-b7088000 r--p 0001b000 08:01 393168     /lib/i386-linux-gnu/libgcc_s.so.1
 b7088000-b7089000 rw-p 0001c000 08:01 393168     /lib/i386-linux-gnu/libgcc_s.so.1
 b7089000-b708b000 rw-p 00000000 00:00 0 
 b708b000-b7090000 r-xp 00000000 08:01 1574758    /usr/lib/i386-linux-gnu/libfontenc.so.1.0.0
 b7090000-b7091000 r--p 00004000 08:01 1574758    /usr/lib/i386-linux-gnu/libfontenc.so.1.0.0
 b7091000-b7092000 rw-p 00005000 08:01 1574758    /usr/lib/i386-linux-gnu/libfontenc.so.1.0.0
 b7092000-b7093000 rw-p 00000000 00:00 0 
 b7093000-b70a2000 r-xp 00000000 08:01 393142     /lib/i386-linux-gnu/libbz2.so.1.0.4
 b70a2000-b70a3000 r--p 0000e000 08:01 393142     /lib/i386-linux-gnu/libbz2.so.1.0.4
 b70a3000-b70a4000 rw-p 0000f000 08:01 393142     /lib/i386-linux-gnu/libbz2.so.1.0.4
 b70a4000-b7139000 r-xp 00000000 08:01 1570221    /usr/lib/i386-linux-gnu/libfreetype.so.6.9.0
 b7139000-b713d000 r--p 00094000 08:01 1570221    /usr/lib/i386-linux-gnu/libfreetype.so.6.9.0
 b713d000-b713e000 rw-p 00098000 08:01 1570221    /usr/lib/i386-linux-gnu/libfreetype.so.6.9.0
 b713e000-b7155000 r-xp 00000000 08:01 393277     /lib/i386-linux-gnu/libz.so.1.2.7
 b7155000-b7156000 r--p 00016000 08:01 393277     /lib/i386-linux-gnu/libz.so.1.2.7
 b7156000-b7157000 rw-p 00017000 08:01 393277     /lib/i386-linux-gnu/libz.so.1.2.7
 b7157000-b715a000 r-xp 00000000 08:01 393174     /lib/i386-linux-gnu/libgpg-error.so.0.8.0
 b715a000-b715b000 r--p 00002000 08:01 393174     /lib/i386-linux-gnu/libgpg-error.so.0.8.0
 b715b000-b715c000 rw-p 00003000 08:01 393174     /lib/i386-linux-gnu/libgpg-error.so.0.8.0
 b715c000-b72ff000 r-xp 00000000 08:01 399785     /lib/i386-linux-gnu/libc-2.15.so
 b72ff000-b7300000 ---p 001a3000 08:01 399785     /lib/i386-linux-gnu/libc-2.15.so
 b7300000-b7302000 r--p 001a3000 08:01 399785     /lib/i386-linux-gnu/libc-2.15.so
 b7302000-b7303000 rw-p 001a5000 08:01 399785     /lib/i386-linux-gnu/libc-2.15.so
 b7303000-b7307000 rw-p 00000000 00:00 0 
 b7307000-b730e000 r-xp 00000000 08:01 409290     /lib/i386-linux-gnu/librt-2.15.so
 b730e000-b730f000 r--p 00006000 08:01 409290     /lib/i386-linux-gnu/librt-2.15.so
 b730f000-b7310000 rw-p 00007000 08:01 409290     /lib/i386-linux-gnu/librt-2.15.so
 b7310000-b733a000 r-xp 00000000 08:01 409203     /lib/i386-linux-gnu/libm-2.15.so
 b733a000-b733b000 r--p 00029000 08:01 409203     /lib/i386-linux-gnu/libm-2.15.so
 b733b000-b733c000 rw-p 0002a000 08:01 409203     /lib/i386-linux-gnu/libm-2.15.so
 b733c000-b7341000 r-xp 00000000 08:01 1574549    /usr/lib/i386-linux-gnu/libXdmcp.so.6.0.0
 b7341000-b7342000 r--p 00004000 08:01 1574549    /usr/lib/i386-linux-gnu/libXdmcp.so.6.0.0
 b7342000-b7343000 rw-p 00005000 08:01 1574549    /usr/lib/i386-linux-gnu/libXdmcp.so.6.0.0
 b7343000-b7345000 r-xp 00000000 08:01 1574538    /usr/lib/i386-linux-gnu/libXau.so.6.0.0
 b7345000-b7346000 r--p 00001000 08:01 1574538    /usr/lib/i386-linux-gnu/libXau.so.6.0.0
 b7346000-b7347000 rw-p 00002000 08:01 1574538    /usr/lib/i386-linux-gnu/libXau.so.6.0.0
 b7347000-b7380000 r-xp 00000000 08:01 1572613    /usr/lib/libXfont.so.1.4.1
 b7380000-b7381000 ---p 00039000 08:01 1572613    /usr/lib/libXfont.so.1.4.1
 b7381000-b7382000 r--p 00039000 08:01 1572613    /usr/lib/libXfont.so.1.4.1
 b7382000-b7383000 rw-p 0003a000 08:01 1572613    /usr/lib/libXfont.so.1.4.1
 b7383000-b7385000 rw-p 00000000 00:00 0 
 b7385000-b7417000 r-xp 00000000 08:01 1575092    /usr/lib/i386-linux-gnu/libpixman-1.so.0.26.0
 b7417000-b741b000 r--p 00092000 08:01 1575092    /usr/lib/i386-linux-gnu/libpixman-1.so.0.26.0
 b741b000-b741c000 rw-p 00096000 08:01 1575092    /usr/lib/i386-linux-gnu/libpixman-1.so.0.26.0
 b741c000-b7427000 r-xp 00000000 08:01 1571458    /usr/lib/i386-linux-gnu/libdrm.so.2.4.0
 b7427000-b7428000 r--p 0000a000 08:01 1571458    /usr/lib/i386-linux-gnu/libdrm.so.2.4.0
 b7428000-b7429000 rw-p 0000b000 08:01 1571458    /usr/lib/i386-linux-gnu/libdrm.so.2.4.0
 b7429000-b7440000 r-xp 00000000 08:01 409201     /lib/i386-linux-gnu/libpthread-2.15.so
 b7440000-b7441000 r--p 00016000 08:01 409201     /lib/i386-linux-gnu/libpthread-2.15.so
 b7441000-b7442000 rw-p 00017000 08:01 409201     /lib/i386-linux-gnu/libpthread-2.15.so
 b7442000-b7444000 rw-p 00000000 00:00 0 
 b7444000-b744d000 r-xp 00000000 08:01 1575086    /usr/lib/i386-linux-gnu/libpciaccess.so.0.11.1
 b744d000-b744e000 r--p 00008000 08:01 1575086    /usr/lib/i386-linux-gnu/libpciaccess.so.0.11.1
 b744e000-b744f000 rw-p 00009000 08:01 1575086    /usr/lib/i386-linux-gnu/libpciaccess.so.0.11.1
 b744f000-b7452000 r-xp 00000000 08:01 409062     /lib/i386-linux-gnu/libdl-2.15.so
 b7452000-b7453000 r--p 00002000 08:01 409062     /lib/i386-linux-gnu/libdl-2.15.so
 b7453000-b7454000 rw-p 00003000 08:01 409062     /lib/i386-linux-gnu/libdl-2.15.so
 b7454000-b7455000 rw-p 00000000 00:00 0 
 b7455000-b74d6000 r-xp 00000000 08:01 410816     /lib/i386-linux-gnu/libgcrypt.so.11.7.0
 b74d6000-b74d7000 r--p 00080000 08:01 410816     /lib/i386-linux-gnu/libgcrypt.so.11.7.0
 b74d7000-b74d9000 rw-p 00081000 08:01 410816     /lib/i386-linux-gnu/libgcrypt.so.11.7.0
 b74d9000-b74e5000 r-xp 00000000 08:01 393262     /lib/i386-linux-gnu/libudev.so.0.13.0
 b74e5000-b74e6000 r--p 0000b000 08:01 393262     /lib/i386-linux-gnu/libudev.so.0.13.0
 b74e6000-b74e7000 rw-p 0000c000 08:01 393262     /lib/i386-linux-gnu/libudev.so.0.13.0
 b74f0000-b74f5000 r-xp 00000000 08:01 3187       /usr/lib/xorg/modules/drivers/vesa_drv.so
 b74f5000-b74f6000 ---p 00005000 08:01 3187       /usr/lib/xorg/modules/drivers/vesa_drv.so
 b74f6000-b74f7000 r--p 00005000 08:01 3187       /usr/lib/xorg/modules/drivers/vesa_drv.so
 b74f7000-b74f8000 rw-p 00006000 08:01 3187       /usr/lib/xorg/modules/drivers/vesa_drv.so
 b74f8000-b74fb000 rw-p 00000000 00:00 0 
 b74fb000-b74fc000 r-xp 00000000 00:00 0          [vdso]
 b74fc000-b751c000 r-xp 00000000 08:01 409258     /lib/i386-linux-gnu/ld-2.15.so
 b751c000-b751d000 r--p 0001f000 08:01 409258     /lib/i386-linux-gnu/ld-2.15.so
 b751d000-b751e000 rw-p 00020000 08:01 409258     /lib/i386-linux-gnu/ld-2.15.so
 b751e000-b773b000 r-xp 00000000 08:01 1571961    /usr/bin/Xorg
 b773b000-b773d000 r--p 0021c000 08:01 1571961    /usr/bin/Xorg
 b773d000-b7744000 rw-p 0021e000 08:01 1571961    /usr/bin/Xorg
 b7744000-b7752000 rw-p 00000000 00:00 0 
 b83a8000-b83d9000 rw-p 00000000 00:00 0          [heap]
 bfb6f000-bfb90000 rw-p 00000000 00:00 0          [stack]
ProcStatus:
 Name:	Xorg
 State:	S (sleeping)
 Tgid:	1021
 Pid:	1021
 PPid:	987
 TracerPid:	0
 Uid:	0	0	0	0
 Gid:	0	0	0	0
 FDSize:	32
 Groups:	
 VmPeak:	    9480 kB
 VmSize:	    9480 kB
 VmLck:	       0 kB
 VmPin:	       0 kB
 VmHWM:	    2524 kB
 VmRSS:	    2524 kB
 VmData:	     552 kB
 VmStk:	     136 kB
 VmExe:	    2164 kB
 VmLib:	    6308 kB
 VmPTE:	      28 kB
 VmSwap:	       0 kB
 Threads:	1
 SigQ:	0/30893
 SigPnd:	0000000000000000
 ShdPnd:	0000000000000000
 SigBlk:	000000001a392000
 SigIgn:	0000000000001000
 SigCgt:	00000001c18066cf
 CapInh:	0000000000000000
 CapPrm:	ffffffffffffffff
 CapEff:	ffffffffffffffff
 CapBnd:	ffffffffffffffff
 Cpus_allowed:	f
 Cpus_allowed_list:	0-3
 Mems_allowed:	1
 Mems_allowed_list:	0
 voluntary_ctxt_switches:	38
 nonvoluntary_ctxt_switches:	5
Signal: 6
Uname: Linux 3.5.0-39-generic i686
UserGroups: 
CoreDump: base64
 H4sICAAAAAAC/0NvcmVEdW1wAA==

```
(followed by a lot of random characters that exceed post limit)

---

### Post by phyothiha96 on 2014-01-14
I had the same problem. Anyhow, I searched around and couldn't find the answer. so I just disabled it. I edited this file as root /etc/default/apport and changed the line says enabled=1 to enabled=0. I have had no error messages ever since.

Regards

---

