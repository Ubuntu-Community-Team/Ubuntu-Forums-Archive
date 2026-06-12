---
title: "Xorg internal error"
date: 2015-07-05
forum: New to Ubuntu
---

### Post by mzurligen1 on 2015-07-05
I'm getting an error when I log in(or soon thereafter) in the past couple days. The details are sketchy as the problem report is "damaged and cannot be processed". Everything seems to run fine after the report, though. Is this something I need to worry about?

Here's the contents of /var/crash/_usr_bin_Xorg.0.crash:

```
ProblemType: Crash
Architecture: amd64
CrashCounter: 1
Date: Sun Jul  5 16:24:41 2015
DistroRelease: Ubuntu 14.04
ExecutablePath: /usr/bin/Xorg
ExecutableTimestamp: 1423782785
ProcCmdline: /usr/bin/X -core :0 -seat seat0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
ProcCwd: /etc/X11
ProcEnviron: 
ProcMaps:
 7fa3d63be000-7fa3e00ad000 rw-p 00000000 00:00 0 
 7fa3e9f78000-7fa3e9f91000 r-xp 00000000 08:01 271494                     /usr/lib/xorg/modules/input/wacom_drv.so
 7fa3e9f91000-7fa3ea191000 ---p 00019000 08:01 271494                     /usr/lib/xorg/modules/input/wacom_drv.so
 7fa3ea191000-7fa3ea192000 r--p 00019000 08:01 271494                     /usr/lib/xorg/modules/input/wacom_drv.so
 7fa3ea192000-7fa3ea194000 rw-p 0001a000 08:01 271494                     /usr/lib/xorg/modules/input/wacom_drv.so
 7fa3ef0b8000-7fa3ef0c3000 r-xp 00000000 08:01 1703955                    /lib/x86_64-linux-gnu/libnss_files-2.19.so
 7fa3ef0c3000-7fa3ef2c2000 ---p 0000b000 08:01 1703955                    /lib/x86_64-linux-gnu/libnss_files-2.19.so
 7fa3ef2c2000-7fa3ef2c3000 r--p 0000a000 08:01 1703955                    /lib/x86_64-linux-gnu/libnss_files-2.19.so
 7fa3ef2c3000-7fa3ef2c4000 rw-p 0000b000 08:01 1703955                    /lib/x86_64-linux-gnu/libnss_files-2.19.so
 7fa3ef2c8000-7fa3ef2d3000 r-xp 00000000 08:01 1707934                    /lib/x86_64-linux-gnu/libnss_nis-2.19.so
 7fa3ef2d3000-7fa3ef4d2000 ---p 0000b000 08:01 1707934                    /lib/x86_64-linux-gnu/libnss_nis-2.19.so
 7fa3ef4d2000-7fa3ef4d3000 r--p 0000a000 08:01 1707934                    /lib/x86_64-linux-gnu/libnss_nis-2.19.so
 7fa3ef4d3000-7fa3ef4d4000 rw-p 0000b000 08:01 1707934                    /lib/x86_64-linux-gnu/libnss_nis-2.19.so
 7fa3ef4d8000-7fa3ef4ef000 r-xp 00000000 08:01 1704030                    /lib/x86_64-linux-gnu/libnsl-2.19.so
 7fa3ef4ef000-7fa3ef6ee000 ---p 00017000 08:01 1704030                    /lib/x86_64-linux-gnu/libnsl-2.19.so
 7fa3ef6ee000-7fa3ef6ef000 r--p 00016000 08:01 1704030                    /lib/x86_64-linux-gnu/libnsl-2.19.so
 7fa3ef6ef000-7fa3ef6f0000 rw-p 00017000 08:01 1704030                    /lib/x86_64-linux-gnu/libnsl-2.19.so
 7fa3ef6f0000-7fa3ef6f2000 rw-p 00000000 00:00 0 
 7fa3ef6f8000-7fa3ef701000 r-xp 00000000 08:01 1704029                    /lib/x86_64-linux-gnu/libnss_compat-2.19.so
 7fa3ef701000-7fa3ef900000 ---p 00009000 08:01 1704029                    /lib/x86_64-linux-gnu/libnss_compat-2.19.so
 7fa3ef900000-7fa3ef901000 r--p 00008000 08:01 1704029                    /lib/x86_64-linux-gnu/libnss_compat-2.19.so
 7fa3ef901000-7fa3ef902000 rw-p 00009000 08:01 1704029                    /lib/x86_64-linux-gnu/libnss_compat-2.19.so
 7fa3f0b10000-7fa3f0b22000 r-xp 00000000 08:01 270622                     /usr/lib/x86_64-linux-gnu/libevdev.so.2.0.1
 7fa3f0b22000-7fa3f0d22000 ---p 00012000 08:01 270622                     /usr/lib/x86_64-linux-gnu/libevdev.so.2.0.1
 7fa3f0d22000-7fa3f0d27000 r--p 00012000 08:01 270622                     /usr/lib/x86_64-linux-gnu/libevdev.so.2.0.1
 7fa3f0d27000-7fa3f0d28000 rw-p 00017000 08:01 270622                     /usr/lib/x86_64-linux-gnu/libevdev.so.2.0.1
 7fa3f0d28000-7fa3f0d2d000 r-xp 00000000 08:01 271010                     /usr/lib/x86_64-linux-gnu/libmtdev.so.1.0.0
 7fa3f0d2d000-7fa3f0f2c000 ---p 00005000 08:01 271010                     /usr/lib/x86_64-linux-gnu/libmtdev.so.1.0.0
 7fa3f0f2c000-7fa3f0f2d000 r--p 00004000 08:01 271010                     /usr/lib/x86_64-linux-gnu/libmtdev.so.1.0.0
 7fa3f0f2d000-7fa3f0f2e000 rw-p 00005000 08:01 271010                     /usr/lib/x86_64-linux-gnu/libmtdev.so.1.0.0
 7fa3f0f50000-7fa3f0f5d000 r-xp 00000000 08:01 271490                     /usr/lib/xorg/modules/input/evdev_drv.so
 7fa3f0f5d000-7fa3f115c000 ---p 0000d000 08:01 271490                     /usr/lib/xorg/modules/input/evdev_drv.so
 7fa3f115c000-7fa3f115d000 r--p 0000c000 08:01 271490                     /usr/lib/xorg/modules/input/evdev_drv.so
 7fa3f115d000-7fa3f115e000 rw-p 0000d000 08:01 271490                     /usr/lib/xorg/modules/input/evdev_drv.so
 7fa3f1797000-7fa3f1810000 rw-p 00000000 00:00 0 
 7fa3f46b0000-7fa3f5361000 r-xp 00000000 08:01 402292                     /usr/lib/fglrx/xorg/modules/glesx.so
 7fa3f5361000-7fa3f5461000 ---p 00cb1000 08:01 402292                     /usr/lib/fglrx/xorg/modules/glesx.so
 7fa3f5461000-7fa3f54fd000 rw-p 00cb1000 08:01 402292                     /usr/lib/fglrx/xorg/modules/glesx.so
 7fa3f54fd000-7fa3f5588000 rw-p 00000000 00:00 0 
 7fa3f65d2000-7fa3f6628000 rw-p 00000000 00:00 0 
 7fa3f6628000-7fa3f664b000 r-xp 00000000 08:01 271459                     /usr/lib/xorg/modules/libfb.so
 7fa3f664b000-7fa3f684a000 ---p 00023000 08:01 271459                     /usr/lib/xorg/modules/libfb.so
 7fa3f684a000-7fa3f684b000 r--p 00022000 08:01 271459                     /usr/lib/xorg/modules/libfb.so
 7fa3f684b000-7fa3f684c000 rw-p 00023000 08:01 271459                     /usr/lib/xorg/modules/libfb.so
 7fa3f6850000-7fa3f6855000 r-xp 00000000 08:01 271465                     /usr/lib/xorg/modules/libvbe.so
 7fa3f6855000-7fa3f6a55000 ---p 00005000 08:01 271465                     /usr/lib/xorg/modules/libvbe.so
 7fa3f6a55000-7fa3f6a56000 r--p 00005000 08:01 271465                     /usr/lib/xorg/modules/libvbe.so
 7fa3f6a56000-7fa3f6a57000 rw-p 00006000 08:01 271465                     /usr/lib/xorg/modules/libvbe.so
 7fa3f6a58000-7fa3f6a98000 rw-s 000c0000 00:05 1028                       /dev/mem
 7fa3f6a9f000-7fa3f6b90000 rw-p 00000000 00:00 0 
 7fa3f6b90000-7fa3f6b97000 r-xp 00000000 08:01 271466                     /usr/lib/xorg/modules/libvgahw.so
 7fa3f6b97000-7fa3f6d96000 ---p 00007000 08:01 271466                     /usr/lib/xorg/modules/libvgahw.so
 7fa3f6d96000-7fa3f6d97000 r--p 00006000 08:01 271466                     /usr/lib/xorg/modules/libvgahw.so
 7fa3f6d97000-7fa3f6d98000 rw-p 00007000 08:01 271466                     /usr/lib/xorg/modules/libvgahw.so
 7fa3f6daf000-7fa3f6dec000 rw-p 00000000 00:00 0 
 7fa3f6ed8000-7fa3f6eef000 r-xp 00000000 08:01 402297                     /usr/lib/fglrx/xorg/modules/amdxmm.so
 7fa3f6eef000-7fa3f6fef000 ---p 00017000 08:01 402297                     /usr/lib/fglrx/xorg/modules/amdxmm.so
 7fa3f6fef000-7fa3f7009000 rw-p 00017000 08:01 402297                     /usr/lib/fglrx/xorg/modules/amdxmm.so
 7fa3f7010000-7fa3f70f6000 r-xp 00000000 08:01 264757                     /usr/lib/x86_64-linux-gnu/libstdc++.so.6.0.19
 7fa3f70f6000-7fa3f72f5000 ---p 000e6000 08:01 264757                     /usr/lib/x86_64-linux-gnu/libstdc++.so.6.0.19
 7fa3f72f5000-7fa3f72fd000 r--p 000e5000 08:01 264757                     /usr/lib/x86_64-linux-gnu/libstdc++.so.6.0.19
 7fa3f72fd000-7fa3f72ff000 rw-p 000ed000 08:01 264757                     /usr/lib/x86_64-linux-gnu/libstdc++.so.6.0.19
 7fa3f72ff000-7fa3f7314000 rw-p 00000000 00:00 0 
 7fa3f7a40000-7fa3f7a41000 r-xp 00000000 08:01 271468                     /usr/lib/xorg/modules/drivers/ati_drv.so
 7fa3f7a41000-7fa3f7c41000 ---p 00001000 08:01 271468                     /usr/lib/xorg/modules/drivers/ati_drv.so
 7fa3f7c41000-7fa3f7c42000 r--p 00001000 08:01 271468                     /usr/lib/xorg/modules/drivers/ati_drv.so
 7fa3f7c42000-7fa3f7c43000 rw-p 00002000 08:01 271468                     /usr/lib/xorg/modules/drivers/ati_drv.so
 7fa3f7c48000-7fa3f7c58000 r-xp 00000000 08:01 275693                     /usr/lib/libatiuki.so.1.0
 7fa3f7c58000-7fa3f7d57000 ---p 00010000 08:01 275693                     /usr/lib/libatiuki.so.1.0
 7fa3f7d57000-7fa3f7d67000 rw-p 0000f000 08:01 275693                     /usr/lib/libatiuki.so.1.0
 7fa3f7d67000-7fa3f7d68000 rw-p 00000000 00:00 0 
 7fa3f7d68000-7fa3f8a91000 r-xp 00000000 08:01 402294                     /usr/lib/fglrx/xorg/modules/drivers/fglrx_drv.so
 7fa3f8a91000-7fa3f8b91000 ---p 00d29000 08:01 402294                     /usr/lib/fglrx/xorg/modules/drivers/fglrx_drv.so
 7fa3f8b91000-7fa3f91fc000 rw-p 00d29000 08:01 402294                     /usr/lib/fglrx/xorg/modules/drivers/fglrx_drv.so
 7fa3f91fc000-7fa3f9207000 rw-p 00000000 00:00 0 
 7fa3f9208000-7fa3f921e000 r-xp 00000000 08:01 1708034                    /lib/x86_64-linux-gnu/libgcc_s.so.1
 7fa3f921e000-7fa3f941d000 ---p 00016000 08:01 1708034                    /lib/x86_64-linux-gnu/libgcc_s.so.1
 7fa3f941d000-7fa3f941e000 rw-p 00015000 08:01 1708034                    /lib/x86_64-linux-gnu/libgcc_s.so.1
 7fa3f9420000-7fa3f9445000 r-xp 00000000 08:01 1708122                    /lib/x86_64-linux-gnu/libpng12.so.0.50.0
 7fa3f9445000-7fa3f9644000 ---p 00025000 08:01 1708122                    /lib/x86_64-linux-gnu/libpng12.so.0.50.0
 7fa3f9644000-7fa3f9645000 r--p 00024000 08:01 1708122                    /lib/x86_64-linux-gnu/libpng12.so.0.50.0
 7fa3f9645000-7fa3f9646000 rw-p 00025000 08:01 1708122                    /lib/x86_64-linux-gnu/libpng12.so.0.50.0
 7fa3f9648000-7fa3f9661000 r-xp 00000000 08:01 1704036                    /lib/x86_64-linux-gnu/libpthread-2.19.so
 7fa3f9661000-7fa3f9860000 ---p 00019000 08:01 1704036                    /lib/x86_64-linux-gnu/libpthread-2.19.so
 7fa3f9860000-7fa3f9861000 r--p 00018000 08:01 1704036                    /lib/x86_64-linux-gnu/libpthread-2.19.so
 7fa3f9861000-7fa3f9862000 rw-p 00019000 08:01 1704036                    /lib/x86_64-linux-gnu/libpthread-2.19.so
 7fa3f9862000-7fa3f9866000 rw-p 00000000 00:00 0 
 7fa3f9868000-7fa3f986e000 r-xp 00000000 08:01 270656                     /usr/lib/x86_64-linux-gnu/libfontenc.so.1.0.0
 7fa3f986e000-7fa3f9a6d000 ---p 00006000 08:01 270656                     /usr/lib/x86_64-linux-gnu/libfontenc.so.1.0.0
 7fa3f9a6d000-7fa3f9a6e000 r--p 00005000 08:01 270656                     /usr/lib/x86_64-linux-gnu/libfontenc.so.1.0.0
 7fa3f9a6e000-7fa3f9a6f000 rw-p 00006000 08:01 270656                     /usr/lib/x86_64-linux-gnu/libfontenc.so.1.0.0
 7fa3f9a6f000-7fa3f9a70000 rw-p 00000000 00:00 0 
 7fa3f9a70000-7fa3f9a7f000 r-xp 00000000 08:01 1708006                    /lib/x86_64-linux-gnu/libbz2.so.1.0.4
 7fa3f9a7f000-7fa3f9c7e000 ---p 0000f000 08:01 1708006                    /lib/x86_64-linux-gnu/libbz2.so.1.0.4
 7fa3f9c7e000-7fa3f9c7f000 r--p 0000e000 08:01 1708006                    /lib/x86_64-linux-gnu/libbz2.so.1.0.4
 7fa3f9c7f000-7fa3f9c80000 rw-p 0000f000 08:01 1708006                    /lib/x86_64-linux-gnu/libbz2.so.1.0.4
 7fa3f9c80000-7fa3f9d1d000 r-xp 00000000 08:01 264338                     /usr/lib/x86_64-linux-gnu/libfreetype.so.6.11.1
 7fa3f9d1d000-7fa3f9f1c000 ---p 0009d000 08:01 264338                     /usr/lib/x86_64-linux-gnu/libfreetype.so.6.11.1
 7fa3f9f1c000-7fa3f9f22000 r--p 0009c000 08:01 264338                     /usr/lib/x86_64-linux-gnu/libfreetype.so.6.11.1
 7fa3f9f22000-7fa3f9f23000 rw-p 000a2000 08:01 264338                     /usr/lib/x86_64-linux-gnu/libfreetype.so.6.11.1
 7fa3f9f28000-7fa3f9f40000 r-xp 00000000 08:01 1708170                    /lib/x86_64-linux-gnu/libz.so.1.2.8
 7fa3f9f40000-7fa3fa13f000 ---p 00018000 08:01 1708170                    /lib/x86_64-linux-gnu/libz.so.1.2.8
 7fa3fa13f000-7fa3fa140000 r--p 00017000 08:01 1708170                    /lib/x86_64-linux-gnu/libz.so.1.2.8
 7fa3fa140000-7fa3fa141000 rw-p 00018000 08:01 1708170                    /lib/x86_64-linux-gnu/libz.so.1.2.8
 7fa3fa148000-7fa3fa14c000 r-xp 00000000 08:01 1708040                    /lib/x86_64-linux-gnu/libgpg-error.so.0.10.0
 7fa3fa14c000-7fa3fa34b000 ---p 00004000 08:01 1708040                    /lib/x86_64-linux-gnu/libgpg-error.so.0.10.0
 7fa3fa34b000-7fa3fa34c000 r--p 00003000 08:01 1708040                    /lib/x86_64-linux-gnu/libgpg-error.so.0.10.0
 7fa3fa34c000-7fa3fa34d000 rw-p 00004000 08:01 1708040                    /lib/x86_64-linux-gnu/libgpg-error.so.0.10.0
 7fa3fa350000-7fa3fa357000 r-xp 00000000 08:01 1704038                    /lib/x86_64-linux-gnu/librt-2.19.so
 7fa3fa357000-7fa3fa556000 ---p 00007000 08:01 1704038                    /lib/x86_64-linux-gnu/librt-2.19.so
 7fa3fa556000-7fa3fa557000 r--p 00006000 08:01 1704038                    /lib/x86_64-linux-gnu/librt-2.19.so
 7fa3fa557000-7fa3fa558000 rw-p 00007000 08:01 1704038                    /lib/x86_64-linux-gnu/librt-2.19.so
 7fa3fa558000-7fa3fa59c000 r-xp 00000000 08:01 1708021                    /lib/x86_64-linux-gnu/libdbus-1.so.3.7.6
 7fa3fa59c000-7fa3fa79b000 ---p 00044000 08:01 1708021                    /lib/x86_64-linux-gnu/libdbus-1.so.3.7.6
 7fa3fa79b000-7fa3fa79c000 r--p 00043000 08:01 1708021                    /lib/x86_64-linux-gnu/libdbus-1.so.3.7.6
 7fa3fa79c000-7fa3fa79d000 rw-p 00044000 08:01 1708021                    /lib/x86_64-linux-gnu/libdbus-1.so.3.7.6
 7fa3fa7a0000-7fa3fa7a8000 r-xp 00000000 08:01 1708069                    /lib/x86_64-linux-gnu/libnih-dbus.so.1.0.0
 7fa3fa7a8000-7fa3fa9a8000 ---p 00008000 08:01 1708069                    /lib/x86_64-linux-gnu/libnih-dbus.so.1.0.0
 7fa3fa9a8000-7fa3fa9a9000 r--p 00008000 08:01 1708069                    /lib/x86_64-linux-gnu/libnih-dbus.so.1.0.0
 7fa3fa9a9000-7fa3fa9aa000 rw-p 00009000 08:01 1708069                    /lib/x86_64-linux-gnu/libnih-dbus.so.1.0.0
 7fa3fa9b0000-7fa3fa9c7000 r-xp 00000000 08:01 1708071                    /lib/x86_64-linux-gnu/libnih.so.1.0.0
 7fa3fa9c7000-7fa3fabc6000 ---p 00017000 08:01 1708071                    /lib/x86_64-linux-gnu/libnih.so.1.0.0
 7fa3fabc6000-7fa3fabc7000 r--p 00016000 08:01 1708071                    /lib/x86_64-linux-gnu/libnih.so.1.0.0
 7fa3fabc7000-7fa3fabc8000 rw-p 00017000 08:01 1708071                    /lib/x86_64-linux-gnu/libnih.so.1.0.0
 7fa3fabc8000-7fa3fabe1000 r-xp 00000000 08:01 1708012                    /lib/x86_64-linux-gnu/libcgmanager.so.0.0.0
 7fa3fabe1000-7fa3fade0000 ---p 00019000 08:01 1708012                    /lib/x86_64-linux-gnu/libcgmanager.so.0.0.0
 7fa3fade0000-7fa3fade2000 r--p 00018000 08:01 1708012                    /lib/x86_64-linux-gnu/libcgmanager.so.0.0.0
 7fa3fade2000-7fa3fade3000 rw-p 0001a000 08:01 1708012                    /lib/x86_64-linux-gnu/libcgmanager.so.0.0.0
 7fa3fade8000-7fa3fafa3000 r-xp 00000000 08:01 1704035                    /lib/x86_64-linux-gnu/libc-2.19.so
 7fa3fafa3000-7fa3fb1a2000 ---p 001bb000 08:01 1704035                    /lib/x86_64-linux-gnu/libc-2.19.so
 7fa3fb1a2000-7fa3fb1a6000 r--p 001ba000 08:01 1704035                    /lib/x86_64-linux-gnu/libc-2.19.so
 7fa3fb1a6000-7fa3fb1a8000 rw-p 001be000 08:01 1704035                    /lib/x86_64-linux-gnu/libc-2.19.so
 7fa3fb1a8000-7fa3fb1ad000 rw-p 00000000 00:00 0 
 7fa3fb1b0000-7fa3fb2b5000 r-xp 00000000 08:01 1703951                    /lib/x86_64-linux-gnu/libm-2.19.so
 7fa3fb2b5000-7fa3fb4b4000 ---p 00105000 08:01 1703951                    /lib/x86_64-linux-gnu/libm-2.19.so
 7fa3fb4b4000-7fa3fb4b5000 r--p 00104000 08:01 1703951                    /lib/x86_64-linux-gnu/libm-2.19.so
 7fa3fb4b5000-7fa3fb4b6000 rw-p 00105000 08:01 1703951                    /lib/x86_64-linux-gnu/libm-2.19.so
 7fa3fb4b8000-7fa3fb4bd000 r-xp 00000000 08:01 270367                     /usr/lib/x86_64-linux-gnu/libXdmcp.so.6.0.0
 7fa3fb4bd000-7fa3fb6bc000 ---p 00005000 08:01 270367                     /usr/lib/x86_64-linux-gnu/libXdmcp.so.6.0.0
 7fa3fb6bc000-7fa3fb6bd000 r--p 00004000 08:01 270367                     /usr/lib/x86_64-linux-gnu/libXdmcp.so.6.0.0
 7fa3fb6bd000-7fa3fb6be000 rw-p 00005000 08:01 270367                     /usr/lib/x86_64-linux-gnu/libXdmcp.so.6.0.0
 7fa3fb6c0000-7fa3fb6c1000 r-xp 00000000 08:01 271434                     /usr/lib/x86_64-linux-gnu/libxshmfence.so.1.0.0
 7fa3fb6c1000-7fa3fb8c0000 ---p 00001000 08:01 271434                     /usr/lib/x86_64-linux-gnu/libxshmfence.so.1.0.0
 7fa3fb8c0000-7fa3fb8c1000 r--p 00000000 08:01 271434                     /usr/lib/x86_64-linux-gnu/libxshmfence.so.1.0.0
 7fa3fb8c1000-7fa3fb8c2000 rw-p 00001000 08:01 271434                     /usr/lib/x86_64-linux-gnu/libxshmfence.so.1.0.0
 7fa3fb8c8000-7fa3fb8ca000 r-xp 00000000 08:01 270356                     /usr/lib/x86_64-linux-gnu/libXau.so.6.0.0
 7fa3fb8ca000-7fa3fbaca000 ---p 00002000 08:01 270356                     /usr/lib/x86_64-linux-gnu/libXau.so.6.0.0
 7fa3fbaca000-7fa3fbacb000 r--p 00002000 08:01 270356                     /usr/lib/x86_64-linux-gnu/libXau.so.6.0.0
 7fa3fbacb000-7fa3fbacc000 rw-p 00003000 08:01 270356                     /usr/lib/x86_64-linux-gnu/libXau.so.6.0.0
 7fa3fbad0000-7fa3fbaff000 r-xp 00000000 08:01 264475                     /usr/lib/x86_64-linux-gnu/libXfont.so.1.4.1
 7fa3fbaff000-7fa3fbcfe000 ---p 0002f000 08:01 264475                     /usr/lib/x86_64-linux-gnu/libXfont.so.1.4.1
 7fa3fbcfe000-7fa3fbcff000 r--p 0002e000 08:01 264475                     /usr/lib/x86_64-linux-gnu/libXfont.so.1.4.1
 7fa3fbcff000-7fa3fbd01000 rw-p 0002f000 08:01 264475                     /usr/lib/x86_64-linux-gnu/libXfont.so.1.4.1
 7fa3fbd08000-7fa3fbda9000 r-xp 00000000 08:01 271114                     /usr/lib/x86_64-linux-gnu/libpixman-1.so.0.30.2
 7fa3fbda9000-7fa3fbfa9000 ---p 000a1000 08:01 271114                     /usr/lib/x86_64-linux-gnu/libpixman-1.so.0.30.2
 7fa3fbfa9000-7fa3fbfb0000 r--p 000a1000 08:01 271114                     /usr/lib/x86_64-linux-gnu/libpixman-1.so.0.30.2
 7fa3fbfb0000-7fa3fbfb1000 rw-p 000a8000 08:01 271114                     /usr/lib/x86_64-linux-gnu/libpixman-1.so.0.30.2
 7fa3fbfb8000-7fa3fbfc3000 r-xp 00000000 08:01 264209                     /usr/lib/x86_64-linux-gnu/libdrm.so.2.4.0
 7fa3fbfc3000-7fa3fc1c2000 ---p 0000b000 08:01 264209                     /usr/lib/x86_64-linux-gnu/libdrm.so.2.4.0
 7fa3fc1c2000-7fa3fc1c3000 r--p 0000a000 08:01 264209                     /usr/lib/x86_64-linux-gnu/libdrm.so.2.4.0
 7fa3fc1c3000-7fa3fc1c4000 rw-p 0000b000 08:01 264209                     /usr/lib/x86_64-linux-gnu/libdrm.so.2.4.0
 7fa3fc1c8000-7fa3fc1d0000 r-xp 00000000 08:01 271107                     /usr/lib/x86_64-linux-gnu/libpciaccess.so.0.11.1
 7fa3fc1d0000-7fa3fc3cf000 ---p 00008000 08:01 271107                     /usr/lib/x86_64-linux-gnu/libpciaccess.so.0.11.1
 7fa3fc3cf000-7fa3fc3d0000 r--p 00007000 08:01 271107                     /usr/lib/x86_64-linux-gnu/libpciaccess.so.0.11.1
 7fa3fc3d0000-7fa3fc3d1000 rw-p 00008000 08:01 271107                     /usr/lib/x86_64-linux-gnu/libpciaccess.so.0.11.1
 7fa3fc3d8000-7fa3fc3db000 r-xp 00000000 08:01 1703966                    /lib/x86_64-linux-gnu/libdl-2.19.so
 7fa3fc3db000-7fa3fc5da000 ---p 00003000 08:01 1703966                    /lib/x86_64-linux-gnu/libdl-2.19.so
 7fa3fc5da000-7fa3fc5db000 r--p 00002000 08:01 1703966                    /lib/x86_64-linux-gnu/libdl-2.19.so
 7fa3fc5db000-7fa3fc5dc000 rw-p 00003000 08:01 1703966                    /lib/x86_64-linux-gnu/libdl-2.19.so
 7fa3fc5e0000-7fa3fc65c000 r-xp 00000000 08:01 1708022                    /lib/x86_64-linux-gnu/libgcrypt.so.11.8.2
 7fa3fc65c000-7fa3fc85c000 ---p 0007c000 08:01 1708022                    /lib/x86_64-linux-gnu/libgcrypt.so.11.8.2
 7fa3fc85c000-7fa3fc85d000 r--p 0007c000 08:01 1708022                    /lib/x86_64-linux-gnu/libgcrypt.so.11.8.2
 7fa3fc85d000-7fa3fc860000 rw-p 0007d000 08:01 1708022                    /lib/x86_64-linux-gnu/libgcrypt.so.11.8.2
 7fa3fc860000-7fa3fc870000 r-xp 00000000 08:01 1707944                    /lib/x86_64-linux-gnu/libudev.so.1.3.5
 7fa3fc870000-7fa3fca6f000 ---p 00010000 08:01 1707944                    /lib/x86_64-linux-gnu/libudev.so.1.3.5
 7fa3fca6f000-7fa3fca70000 r--p 0000f000 08:01 1707944                    /lib/x86_64-linux-gnu/libudev.so.1.3.5
 7fa3fca70000-7fa3fca71000 rw-p 00010000 08:01 1707944                    /lib/x86_64-linux-gnu/libudev.so.1.3.5
 7fa3fca78000-7fa3fca9b000 r-xp 00000000 08:01 1704032                    /lib/x86_64-linux-gnu/ld-2.19.so
 7fa3fcab8000-7fa3fcb41000 r-xp 00000000 08:01 402290                     /usr/lib/fglrx/xorg/modules/extensions/libglx.so
 7fa3fcb41000-7fa3fcc41000 ---p 00089000 08:01 402290                     /usr/lib/fglrx/xorg/modules/extensions/libglx.so
 7fa3fcc41000-7fa3fcc4d000 rw-p 00089000 08:01 402290                     /usr/lib/fglrx/xorg/modules/extensions/libglx.so
 7fa3fcc4d000-7fa3fcc99000 rw-p 00000000 00:00 0 
 7fa3fcc9a000-7fa3fcc9b000 r--p 00022000 08:01 1704032                    /lib/x86_64-linux-gnu/ld-2.19.so
 7fa3fcc9b000-7fa3fcc9c000 rw-p 00023000 08:01 1704032                    /lib/x86_64-linux-gnu/ld-2.19.so
 7fa3fcc9c000-7fa3fcc9d000 rw-p 00000000 00:00 0 
 7fa3fcca0000-7fa3fcec6000 r-xp 00000000 08:01 262159                     /usr/bin/Xorg
 7fa3fced8000-7fa3fcef8000 rw-s 000a0000 00:05 1028                       /dev/mem
 7fa3fcef8000-7fa3fcf38000 rw-s fea00000 00:0f 16750                      /sys/devices/pci0000:00/0000:00:02.1/0000:01:00.0/resource5
 7fa3fcf38000-7fa3fcf45000 r-xp 00000000 08:01 402296                     /usr/lib/fglrx/xorg/modules/linux/libfglrxdrm.so
 7fa3fcf45000-7fa3fd045000 ---p 0000d000 08:01 402296                     /usr/lib/fglrx/xorg/modules/linux/libfglrxdrm.so
 7fa3fd045000-7fa3fd048000 rw-p 0000d000 08:01 402296                     /usr/lib/fglrx/xorg/modules/linux/libfglrxdrm.so
 7fa3fd099000-7fa3fd0a0000 rw-p 00000000 00:00 0 
 7fa3fd0a5000-7fa3fd0a6000 rw-s 00005000 00:05 12788                      /dev/ati/card0
 7fa3fd0a8000-7fa3fd0b8000 rw-s 000a0000 00:05 1028                       /dev/mem
 7fa3fd0be000-7fa3fd0c6000 rw-p 00000000 00:00 0 
 7fa3fd0c6000-7fa3fd0c8000 r--p 00226000 08:01 262159                     /usr/bin/Xorg
 7fa3fd0c8000-7fa3fd0d4000 rw-p 00228000 08:01 262159                     /usr/bin/Xorg
 7fa3fd0d4000-7fa3fd0e5000 rw-p 00000000 00:00 0 
 7fa3fea5a000-7fa40052b000 rw-p 00000000 00:00 0                          [heap]
 7ffff64df000-7ffff6500000 rw-p 00000000 00:00 0                          [stack]
 7ffff6548000-7ffff654a000 r-xp 00000000 00:00 0                          [vdso]
 7ffff654a000-7ffff654c000 r--p 00000000 00:00 0                          [vvar]
 ffffffffff600000-ffffffffff601000 r-xp 00000000 00:00 0                  [vsyscall]
ProcStatus:
 Name:	Xorg
 State:	S (sleeping)
 Tgid:	1155
 Ngid:	0
 Pid:	1155
 PPid:	1142
 TracerPid:	0
 Uid:	0	0	0	0
 Gid:	0	0	0	0
 FDSize:	64
 Groups:	0 
 VmPeak:	  633492 kB
 VmSize:	  321140 kB
 VmLck:	       0 kB
 VmPin:	       0 kB
 VmHWM:	  323052 kB
 VmRSS:	  216892 kB
 VmData:	  191384 kB
 VmStk:	     136 kB
 VmExe:	    2200 kB
 VmLib:	   34952 kB
 VmPTE:	     672 kB
 VmSwap:	       0 kB
 Threads:	1
 SigQ:	2/31371
 SigPnd:	0000000000000000
 ShdPnd:	0000000010002000
 SigBlk:	000000001a392400
 SigIgn:	0000000000001000
 SigCgt:	00000001d18066cf
 CapInh:	0000000000000000
 CapPrm:	0000003fffffffff
 CapEff:	0000003fffffffff
 CapBnd:	0000003fffffffff
 Seccomp:	0
 Cpus_allowed:	f
 Cpus_allowed_list:	0-3
 Mems_allowed:	00000000,00000001
 Mems_allowed_list:	0
 voluntary_ctxt_switches:	826071
 nonvoluntary_ctxt_switches:	29488
Signal: 6
Uname: Linux 3.16.0-41-generic x86_64
UserGroups: 
CoreDump: base64
```

Everything after the CoreDump line is alphanumeric gibberish when I open the .crash file in gedit, dozens of lines each over 50,000 characters long. The first several lines are rendered on top of each other and cause gedit to lag when I scroll past.

Again, the system seems to be running fine after the report. I've seen this twice now, in the last 2 days. What's up?

Edit: more info in the "Report a problem" window:
```

This problem report is damaged and cannot be processed.

OSError('Invalid core dump: BFD: Warning: /tmp/apport_core_l4vvz57b is truncated: expected core file size >= 204439552, found: 33619968.',)

```

---

