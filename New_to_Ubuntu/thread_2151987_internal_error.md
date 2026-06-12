---
title: "internal error"
date: 2013-06-06
forum: New to Ubuntu
---

### Post by amiralex32 on 2013-06-06
i got this message giving an internal error
executable path 
/usr/bin/update-notifier
package 
update notifier 0.134
problem type
crash
title
update notifier crashed with sigsegv in free()
apport version
2.9.20ubuntu8
archticture
i386
coredump
binary data

i have opened the var/crash folder
ProblemType: Crash
CrashCounter: 1
Date: Tue Jun  4 19:35:15 2013
ExecutablePath: /usr/bin/update-manager
ExecutableTimestamp: 1366140455
InterpreterPath: /usr/bin/python3.3
ProcCmdline: /usr/bin/python3 /usr/bin/update-manager --no-update
ProcCwd: /home/amiralex
ProcEnviron:
 PATH=(custom, no user)
 XDG_RUNTIME_DIR=<set>
 LANG=en_US.UTF-8
 SHELL=/bin/bash
ProcMaps:
 08048000-082db000 r-xp 00000000 08:16 523460     /usr/bin/python3.3
 082db000-082dc000 r--p 00292000 08:16 523460     /usr/bin/python3.3
 082dc000-0835a000 rw-p 00293000 08:16 523460     /usr/bin/python3.3
 0835a000-08370000 rw-p 00000000 00:00 0 
 089f6000-08d59000 rw-p 00000000 00:00 0          [heap]
 b2c00000-b2d00000 rw-p 00000000 00:00 0 
 b2d00000-b2ecc000 r-xp 00000000 08:16 523326     /usr/lib/i386-linux-gnu/libicui18n.so.48.1.1
 b2ecc000-b2ed3000 r--p 001cb000 08:16 523326     /usr/lib/i386-linux-gnu/libicui18n.so.48.1.1
 b2ed3000-b2ed4000 rw-p 001d2000 08:16 523326     /usr/lib/i386-linux-gnu/libicui18n.so.48.1.1
 b2ed4000-b2ef9000 r-xp 00000000 08:16 528362     /usr/lib/i386-linux-gnu/libunity/libunity-protocol-private.so.0.0.0
 b2ef9000-b2efa000 r--p 00025000 08:16 528362     /usr/lib/i386-linux-gnu/libunity/libunity-protocol-private.so.0.0.0
 b2efa000-b2efb000 rw-p 00026000 08:16 528362     /usr/lib/i386-linux-gnu/libunity/libunity-protocol-private.so.0.0.0
 b2efb000-b2f15000 r-xp 00000000 08:16 526785     /usr/lib/i386-linux-gnu/libdbusmenu-glib.so.4.0.12
 b2f15000-b2f16000 ---p 0001a000 08:16 526785     /usr/lib/i386-linux-gnu/libdbusmenu-glib.so.4.0.12
 b2f16000-b2f17000 r--p 0001a000 08:16 526785     /usr/lib/i386-linux-gnu/libdbusmenu-glib.so.4.0.12
 b2f17000-b2f18000 rw-p 0001b000 08:16 526785     /usr/lib/i386-linux-gnu/libdbusmenu-glib.so.4.0.12
 b2f18000-b2f51000 r-xp 00000000 08:16 526296     /usr/lib/i386-linux-gnu/libdee-1.0.so.4.2.1
 b2f51000-b2f52000 r--p 00038000 08:16 526296     /usr/lib/i386-linux-gnu/libdee-1.0.so.4.2.1
 b2f52000-b2f53000 rw-p 00039000 08:16 526296     /usr/lib/i386-linux-gnu/libdee-1.0.so.4.2.1
 b2f53000-b2fa7000 r-xp 00000000 08:16 528363     /usr/lib/i386-linux-gnu/libgee.so.2.0.0
 b2fa7000-b2fa9000 r--p 00053000 08:16 528363     /usr/lib/i386-linux-gnu/libgee.so.2.0.0
 b2fa9000-b2faa000 rw-p 00055000 08:16 528363     /usr/lib/i386-linux-gnu/libgee.so.2.0.0
 b2faa000-b301e000 r-xp 00000000 08:16 547645     /usr/lib/i386-linux-gnu/libunity.so.9.0.2
 b301e000-b3020000 r--p 00073000 08:16 547645     /usr/lib/i386-linux-gnu/libunity.so.9.0.2
 b3020000-b3021000 rw-p 00075000 08:16 547645     /usr/lib/i386-linux-gnu/libunity.so.9.0.2
 b3037000-b3057000 r--s 00000000 08:16 922114     /usr/share/mime/mime.cache
 b3057000-b3157000 rw-p 00000000 00:00 0 
 b3157000-b31a8000 r-xp 00000000 08:16 1178074    /lib/i386-linux-gnu/libssl.so.1.0.0
 b31a8000-b31aa000 r--p 00050000 08:16 1178074    /lib/i386-linux-gnu/libssl.so.1.0.0
 b31aa000-b31ae000 rw-p 00052000 08:16 1178074    /lib/i386-linux-gnu/libssl.so.1.0.0
 b31ae000-b31ee000 rw-p 00000000 00:00 0 
 b31ee000-b3380000 r-xp 00000000 08:16 1178073    /lib/i386-linux-gnu/libcrypto.so.1.0.0
 b3380000-b338f000 r--p 00192000 08:16 1178073    /lib/i386-linux-gnu/libcrypto.so.1.0.0
 b338f000-b3396000 rw-p 001a1000 08:16 1178073    /lib/i386-linux-gnu/libcrypto.so.1.0.0
 b3396000-b347a000 rw-p 00000000 00:00 0 
 b347a000-b3484000 r--p 00000000 08:16 528169     /usr/lib/girepository-1.0/Dee-1.0.typelib
 b3484000-b34a8000 r-xp 00000000 08:16 523730     /usr/lib/i386-linux-gnu/libdbus-glib-1.so.2.2.2
 b34a8000-b34a9000 r--p 00023000 08:16 523730     /usr/lib/i386-linux-gnu/libdbus-glib-1.so.2.2.2
 b34a9000-b34aa000 rw-p 00024000 08:16 523730     /usr/lib/i386-linux-gnu/libdbus-glib-1.so.2.2.2
 b34aa000-b34c2000 r-xp 00000000 08:16 524018     /usr/lib/python3/dist-packages/_dbus_bindings.cpython-33m-i386-linux-gnu.so
 b34c2000-b34c3000 r--p 00017000 08:16 524018     /usr/lib/python3/dist-packages/_dbus_bindings.cpython-33m-i386-linux-gnu.so
 b34c3000-b34ce000 rw-p 00018000 08:16 524018     /usr/lib/python3/dist-packages/_dbus_bindings.cpython-33m-i386-linux-gnu.so
 b34ce000-b34dd000 r-xp 00000000 08:16 1178038    /lib/i386-linux-gnu/libbz2.so.1.0.4
 b34dd000-b34de000 r--p 0000e000 08:16 1178038    /lib/i386-linux-gnu/libbz2.so.1.0.4
 b34de000-b34df000 rw-p 0000f000 08:16 1178038    /lib/i386-linux-gnu/libbz2.so.1.0.4
 b34df000-b35fd000 r-xp 00000000 08:16 524226     /usr/lib/i386-linux-gnu/libapt-pkg.so.4.12.0
 b35fd000-b35ff000 r--p 0011e000 08:16 524226     /usr/lib/i386-linux-gnu/libapt-pkg.so.4.12.0
 b35ff000-b3600000 rw-p 00120000 08:16 524226     /usr/lib/i386-linux-gnu/libapt-pkg.so.4.12.0
 b3600000-b3621000 rw-p 00000000 00:00 0 
 b3621000-b3700000 ---p 00000000 00:00 0 
 b3708000-b3747000 r-xp 00000000 08:16 532410     /usr/lib/python3/dist-packages/apt_pkg.cpython-33m-i386-linux-gnu.so
 b3747000-b3748000 r--p 0003e000 08:16 532410     /usr/lib/python3/dist-packages/apt_pkg.cpython-33m-i386-linux-gnu.so
 b3748000-b374d000 rw-p 0003f000 08:16 532410     /usr/lib/python3/dist-packages/apt_pkg.cpython-33m-i386-linux-gnu.so
 b374d000-b378d000 rw-p 00000000 00:00 0 
 b378d000-b3793000 r-xp 00000000 08:16 528526     /usr/lib/i386-linux-gnu/libogg.so.0.8.0
 b3793000-b3794000 r--p 00005000 08:16 528526     /usr/lib/i386-linux-gnu/libogg.so.0.8.0
 b3794000-b3795000 rw-p 00006000 08:16 528526     /usr/lib/i386-linux-gnu/libogg.so.0.8.0
 b3795000-b37be000 r-xp 00000000 08:16 528732     /usr/lib/i386-linux-gnu/libvorbis.so.0.4.5
 b37be000-b37bf000 ---p 00029000 08:16 528732     /usr/lib/i386-linux-gnu/libvorbis.so.0.4.5
 b37bf000-b37c0000 r--p 00029000 08:16 528732     /usr/lib/i386-linux-gnu/libvorbis.so.0.4.5
 b37c0000-b37c1000 rw-p 0002a000 08:16 528732     /usr/lib/i386-linux-gnu/libvorbis.so.0.4.5
 b37c1000-b37ca000 r-xp 00000000 08:16 524218     /usr/lib/i386-linux-gnu/libltdl.so.7.3.0
 b37ca000-b37cb000 r--p 00008000 08:16 524218     /usr/lib/i386-linux-gnu/libltdl.so.7.3.0
 b37cb000-b37cc000 rw-p 00009000 08:16 524218     /usr/lib/i386-linux-gnu/libltdl.so.7.3.0
 b37cc000-b37dd000 r-xp 00000000 08:16 523963     /usr/lib/i386-linux-gnu/libtdb.so.1.2.10
 b37dd000-b37de000 r--p 00010000 08:16 523963     /usr/lib/i386-linux-gnu/libtdb.so.1.2.10
 b37de000-b37df000 rw-p 00011000 08:16 523963     /usr/lib/i386-linux-gnu/libtdb.so.1.2.10
 b37df000-b37e7000 r-xp 00000000 08:16 528736     /usr/lib/i386-linux-gnu/libvorbisfile.so.3.3.4
 b37e7000-b37e8000 r--p 00007000 08:16 528736     /usr/lib/i386-linux-gnu/libvorbisfile.so.3.3.4
 b37e8000-b37e9000 rw-p 00008000 08:16 528736     /usr/lib/i386-linux-gnu/libvorbisfile.so.3.3.4
 b37f1000-b37fa000 r--p 00000000 08:16 527124     /usr/lib/girepository-1.0/Unity-6.0.typelib
 b37fa000-b37ff000 r--p 00000000 08:16 526772     /usr/lib/girepository-1.0/Dbusmenu-0.4.typelib
 b37ff000-b3800000 ---p 00000000 00:00 0 
 b3800000-b4000000 rw-p 00000000 00:00 0          [stack:3856]
 b4000000-b4021000 rw-p 00000000 00:00 0 
 b4021000-b4100000 ---p 00000000 00:00 0 
 b4102000-b4111000 r-xp 00000000 08:16 524387     /usr/lib/i386-linux-gnu/libcanberra.so.0.2.5
 b4111000-b4112000 r--p 0000e000 08:16 524387     /usr/lib/i386-linux-gnu/libcanberra.so.0.2.5
 b4112000-b4113000 rw-p 0000f000 08:16 524387     /usr/lib/i386-linux-gnu/libcanberra.so.0.2.5
 b4113000-b4123000 r-xp 00000000 08:16 1185930    /lib/i386-linux-gnu/libudev.so.1.2.2
 b4123000-b4124000 r--p 0000f000 08:16 1185930    /lib/i386-linux-gnu/libudev.so.1.2.2
 b4124000-b4125000 rw-p 00010000 08:16 1185930    /lib/i386-linux-gnu/libudev.so.1.2.2
 b4125000-b4127000 r-xp 00000000 08:16 523454     /usr/lib/python3/dist-packages/_dbus_glib_bindings.cpython-33m-i386-linux-gnu.so
 b4127000-b4128000 r--p 00001000 08:16 523454     /usr/lib/python3/dist-packages/_dbus_glib_bindings.cpython-33m-i386-linux-gnu.so
 b4128000-b4129000 rw-p 00002000 08:16 523454     /usr/lib/python3/dist-packages/_dbus_glib_bindings.cpython-33m-i386-linux-gnu.so
 b4129000-b412d000 r-xp 00000000 08:16 527891     /usr/lib/i386-linux-gnu/libcanberra-gtk3.so.0.1.9
 b412d000-b412e000 r--p 00003000 08:16 527891     /usr/lib/i386-linux-gnu/libcanberra-gtk3.so.0.1.9
 b412e000-b412f000 rw-p 00004000 08:16 527891     /usr/lib/i386-linux-gnu/libcanberra-gtk3.so.0.1.9
 b412f000-b4133000 r-xp 00000000 08:16 524825     /usr/lib/i386-linux-gnu/gtk-3.0/modules/libcanberra-gtk3-module.so
 b4133000-b4134000 ---p 00004000 08:16 524825     /usr/lib/i386-linux-gnu/gtk-3.0/modules/libcanberra-gtk3-module.so
 b4134000-b4135000 r--p 00004000 08:16 524825     /usr/lib/i386-linux-gnu/gtk-3.0/modules/libcanberra-gtk3-module.so
 b4135000-b4136000 rw-p 00005000 08:16 524825     /usr/lib/i386-linux-gnu/gtk-3.0/modules/libcanberra-gtk3-module.so
 b4136000-b4139000 r-xp 00000000 08:16 657093     /usr/lib/i386-linux-gnu/gtk-3.0/3.0.0/theming-engines/libunico.so
 b4139000-b413a000 r--p 00002000 08:16 657093     /usr/lib/i386-linux-gnu/gtk-3.0/3.0.0/theming-engines/libunico.so
 b413a000-b413b000 rw-p 00003000 08:16 657093     /usr/lib/i386-linux-gnu/gtk-3.0/3.0.0/theming-engines/libunico.so
 b413b000-b416d000 r-xp 00000000 08:16 527845     /usr/lib/i386-linux-gnu/gvfs/libgvfscommon.so
 b416d000-b416e000 ---p 00032000 08:16 527845     /usr/lib/i386-linux-gnu/gvfs/libgvfscommon.so
 b416e000-b4170000 r--p 00032000 08:16 527845     /usr/lib/i386-linux-gnu/gvfs/libgvfscommon.so
 b4170000-b4171000 rw-p 00034000 08:16 527845     /usr/lib/i386-linux-gnu/gvfs/libgvfscommon.so
 b4171000-b41a1000 r-xp 00000000 08:16 524047     /usr/lib/i386-linux-gnu/gio/modules/libgvfsdbus.so
 b41a1000-b41a2000 r--p 0002f000 08:16 524047     /usr/lib/i386-linux-gnu/gio/modules/libgvfsdbus.so
 b41a2000-b41a3000 rw-p 00030000 08:16 524047     /usr/lib/i386-linux-gnu/gio/modules/libgvfsdbus.so
 b41a3000-b41a4000 ---p 00000000 00:00 0 
 b41a4000-b49a4000 rw-p 00000000 00:00 0          [stack:3855]
 b49a4000-b49a9000 r--p 00000000 08:16 2097861    /home/amiralex/.config/dconf/user (deleted)
 b49a9000-b49b3000 r-xp 00000000 08:16 524197     /usr/lib/i386-linux-gnu/gio/modules/libdconfsettings.so
 b49b3000-b49b4000 r--p 00009000 08:16 524197     /usr/lib/i386-linux-gnu/gio/modules/libdconfsettings.so
 b49b4000-b49b5000 rw-p 0000a000 08:16 524197     /usr/lib/i386-linux-gnu/gio/modules/libdconfsettings.so
 b49b5000-b49f0000 r--p 00000000 08:16 932153     /usr/share/glib-2.0/schemas/gschemas.compiled
 b49f0000-b4ab0000 rw-p 00000000 00:00 0 
 b4ab0000-b5c1f000 r-xp 00000000 08:16 523684     /usr/lib/i386-linux-gnu/libicudata.so.48.1.1
 b5c1f000-b5c20000 r--p 0116e000 08:16 523684     /usr/lib/i386-linux-gnu/libicudata.so.48.1.1
 b5c20000-b5c21000 rw-p 0116f000 08:16 523684     /usr/lib/i386-linux-gnu/libicudata.so.48.1.1
 b5c21000-b5c3c000 r-xp 00000000 08:16 1178032    /lib/i386-linux-gnu/libgcc_s.so.1
 b5c3c000-b5c3d000 r--p 0001a000 08:16 1178032    /lib/i386-linux-gnu/libgcc_s.so.1
 b5c3d000-b5c3e000 rw-p 0001b000 08:16 1178032    /lib/i386-linux-gnu/libgcc_s.so.1
 b5c3e000-b5d1a000 r-xp 00000000 08:16 523616     /usr/lib/i386-linux-gnu/libstdc++.so.6.0.17
 b5d1a000-b5d1b000 ---p 000dc000 08:16 523616     /usr/lib/i386-linux-gnu/libstdc++.so.6.0.17
 b5d1b000-b5d1f000 r--p 000dc000 08:16 523616     /usr/lib/i386-linux-gnu/libstdc++.so.6.0.17
 b5d1f000-b5d20000 rw-p 000e0000 08:16 523616     /usr/lib/i386-linux-gnu/libstdc++.so.6.0.17
 b5d20000-b5d27000 rw-p 00000000 00:00 0 
 b5d27000-b5e7d000 r-xp 00000000 08:16 523288     /usr/lib/i386-linux-gnu/libicuuc.so.48.1.1
 b5e7d000-b5e87000 r--p 00155000 08:16 523288     /usr/lib/i386-linux-gnu/libicuuc.so.48.1.1
 b5e87000-b5e88000 rw-p 0015f000 08:16 523288     /usr/lib/i386-linux-gnu/libicuuc.so.48.1.1
 b5e88000-b5e8c000 rw-p 00000000 00:00 0 
 b5e8c000-b5ebf000 r-xp 00000000 08:16 523319     /usr/lib/i386-linux-gnu/libicule.so.48.1.1
 b5ebf000-b5ec0000 ---p 00033000 08:16 523319     /usr/lib/i386-linux-gnu/libicule.so.48.1.1
 b5ec0000-b5ec1000 r--p 00033000 08:16 523319     /usr/lib/i386-linux-gnu/libicule.so.48.1.1
 b5ec1000-b5ec2000 rw-p 00034000 08:16 523319     /usr/lib/i386-linux-gnu/libicule.so.48.1.1
 b5ec2000-b5ec7000 r-xp 00000000 08:16 528021     /usr/lib/i386-linux-gnu/libXdmcp.so.6.0.0
 b5ec7000-b5ec8000 r--p 00004000 08:16 528021     /usr/lib/i386-linux-gnu/libXdmcp.so.6.0.0
 b5ec8000-b5ec9000 rw-p 00005000 08:16 528021     /usr/lib/i386-linux-gnu/libXdmcp.so.6.0.0
 b5ec9000-b5ecb000 r-xp 00000000 08:16 528010     /usr/lib/i386-linux-gnu/libXau.so.6.0.0
 b5ecb000-b5ecc000 r--p 00001000 08:16 528010     /usr/lib/i386-linux-gnu/libXau.so.6.0.0
 b5ecc000-b5ecd000 rw-p 00002000 08:16 528010     /usr/lib/i386-linux-gnu/libXau.so.6.0.0
 b5ecd000-b5f65000 r-xp 00000000 08:16 524924     /usr/lib/i386-linux-gnu/libharfbuzz.so.0.913.0
 b5f65000-b5f66000 ---p 00098000 08:16 524924     /usr/lib/i386-linux-gnu/libharfbuzz.so.0.913.0
 b5f66000-b5f67000 r--p 00098000 08:16 524924     /usr/lib/i386-linux-gnu/libharfbuzz.so.0.913.0
 b5f67000-b5f68000 rw-p 00099000 08:16 524924     /usr/lib/i386-linux-gnu/libharfbuzz.so.0.913.0
 b5f68000-b5fb0000 r-xp 00000000 08:16 1188118    /lib/i386-linux-gnu/libdbus-1.so.3.7.2
 b5fb0000-b5fb1000 r--p 00047000 08:16 1188118    /lib/i386-linux-gnu/libdbus-1.so.3.7.2
 b5fb1000-b5fb2000 rw-p 00048000 08:16 1188118    /lib/i386-linux-gnu/libdbus-1.so.3.7.2
 b5fb2000-b5fd4000 r-xp 00000000 08:16 527575     /usr/lib/i386-linux-gnu/libatspi.so.0.0.1
 b5fd4000-b5fd5000 ---p 00022000 08:16 527575     /usr/lib/i386-linux-gnu/libatspi.so.0.0.1
 b5fd5000-b5fd6000 r--p 00022000 08:16 527575     /usr/lib/i386-linux-gnu/libatspi.so.0.0.1
 b5fd6000-b5fd7000 rw-p 00023000 08:16 527575     /usr/lib/i386-linux-gnu/libatspi.so.0.0.1
 b5fd7000-b5fdf000 r-xp 00000000 08:16 528043     /usr/lib/i386-linux-gnu/libXrender.so.1.3.0
 b5fdf000-b5fe0000 r--p 00007000 08:16 528043     /usr/lib/i386-linux-gnu/libXrender.so.1.3.0
 b5fe0000-b5fe1000 rw-p 00008000 08:16 528043     /usr/lib/i386-linux-gnu/libXrender.so.1.3.0
 b5fe1000-b5fe9000 r-xp 00000000 08:16 524695     /usr/lib/i386-linux-gnu/libxcb-render.so.0.0.0
 b5fe9000-b5fea000 r--p 00008000 08:16 524695     /usr/lib/i386-linux-gnu/libxcb-render.so.0.0.0
 b5fea000-b5feb000 rw-p 00009000 08:16 524695     /usr/lib/i386-linux-gnu/libxcb-render.so.0.0.0
 b5feb000-b5fed000 r-xp 00000000 08:16 524697     /usr/lib/i386-linux-gnu/libxcb-shm.so.0.0.0
 b5fed000-b5fee000 r--p 00001000 08:16 524697     /usr/lib/i386-linux-gnu/libxcb-shm.so.0.0.0
 b5fee000-b5fef000 rw-p 00002000 08:16 524697     /usr/lib/i386-linux-gnu/libxcb-shm.so.0.0.0
 b5fef000-b6016000 r-xp 00000000 08:16 1178172    /lib/i386-linux-gnu/libpng12.so.0.49.0
 b6016000-b6017000 r--p 00026000 08:16 1178172    /lib/i386-linux-gnu/libpng12.so.0.49.0
 b6017000-b6018000 rw-p 00027000 08:16 1178172    /lib/i386-linux-gnu/libpng12.so.0.49.0
 b6018000-b60ac000 r-xp 00000000 08:16 523631     /usr/lib/i386-linux-gnu/libpixman-1.so.0.28.2
 b60ac000-b60b1000 r--p 00093000 08:16 523631     /usr/lib/i386-linux-gnu/libpixman-1.so.0.28.2
 b60b1000-b60b2000 rw-p 00098000 08:16 523631     /usr/lib/i386-linux-gnu/libpixman-1.so.0.28.2
 b60b2000-b60d2000 r-xp 00000000 08:16 523647     /usr/lib/i386-linux-gnu/libxcb.so.1.1.0
 b60d2000-b60d3000 r--p 0001f000 08:16 523647     /usr/lib/i386-linux-gnu/libxcb.so.1.1.0
 b60d3000-b60d4000 rw-p 00020000 08:16 523647     /usr/lib/i386-linux-gnu/libxcb.so.1.1.0
 b60d4000-b616a000 r-xp 00000000 08:16 524689     /usr/lib/i386-linux-gnu/libfreetype.so.6.10.0
 b616a000-b616e000 r--p 00095000 08:16 524689     /usr/lib/i386-linux-gnu/libfreetype.so.6.10.0
 b616e000-b616f000 rw-p 00099000 08:16 524689     /usr/lib/i386-linux-gnu/libfreetype.so.6.10.0
 b616f000-b617f000 r-xp 00000000 08:16 528023     /usr/lib/i386-linux-gnu/libXext.so.6.4.0
 b617f000-b6180000 r--p 0000f000 08:16 528023     /usr/lib/i386-linux-gnu/libXext.so.6.4.0
 b6180000-b6181000 rw-p 00010000 08:16 528023     /usr/lib/i386-linux-gnu/libXext.so.6.4.0
 b6181000-b6184000 r-xp 00000000 08:16 524334     /usr/lib/i386-linux-gnu/libwayland-cursor.so.0.0.0
 b6184000-b6185000 r--p 00003000 08:16 524334     /usr/lib/i386-linux-gnu/libwayland-cursor.so.0.0.0
 b6185000-b6189000 rw-p 00004000 08:16 524334     /usr/lib/i386-linux-gnu/libwayland-cursor.so.0.0.0
 b6189000-b61c4000 r-xp 00000000 08:16 526940     /usr/lib/i386-linux-gnu/libxkbcommon.so.0.0.0
 b61c4000-b61c5000 ---p 0003b000 08:16 526940     /usr/lib/i386-linux-gnu/libxkbcommon.so.0.0.0
 b61c5000-b61cf000 r--p 0003b000 08:16 526940     /usr/lib/i386-linux-gnu/libxkbcommon.so.0.0.0
 b61cf000-b61d0000 rw-p 00045000 08:16 526940     /usr/lib/i386-linux-gnu/libxkbcommon.so.0.0.0
 b61d0000-b61d8000 r-xp 00000000 08:16 526936     /usr/lib/i386-linux-gnu/libwayland-client.so.0.1.0
 b61d8000-b61d9000 r--p 00007000 08:16 526936     /usr/lib/i386-linux-gnu/libwayland-client.so.0.1.0
 b61d9000-b61da000 rw-p 00008000 08:16 526936     /usr/lib/i386-linux-gnu/libwayland-client.so.0.1.0
 b61da000-b61dc000 r-xp 00000000 08:16 528019     /usr/lib/i386-linux-gnu/libXdamage.so.1.1.0
 b61dc000-b61dd000 r--p 00001000 08:16 528019     /usr/lib/i386-linux-gnu/libXdamage.so.1.1.0
 b61dd000-b61de000 rw-p 00002000 08:16 528019     /usr/lib/i386-linux-gnu/libXdamage.so.1.1.0
 b61de000-b61e0000 r-xp 00000000 08:16 528015     /usr/lib/i386-linux-gnu/libXcomposite.so.1.0.0
 b61e0000-b61e1000 r--p 00001000 08:16 528015     /usr/lib/i386-linux-gnu/libXcomposite.so.1.0.0
 b61e1000-b61e2000 rw-p 00002000 08:16 528015     /usr/lib/i386-linux-gnu/libXcomposite.so.1.0.0
 b61e2000-b61eb000 r-xp 00000000 08:16 528017     /usr/lib/i386-linux-gnu/libXcursor.so.1.0.2
 b61eb000-b61ec000 r--p 00008000 08:16 528017     /usr/lib/i386-linux-gnu/libXcursor.so.1.0.2
 b61ec000-b61ed000 rw-p 00009000 08:16 528017     /usr/lib/i386-linux-gnu/libXcursor.so.1.0.2
 b61ed000-b61f6000 r-xp 00000000 08:16 528028     /usr/lib/i386-linux-gnu/libXrandr.so.2.2.0
 b61f6000-b61f7000 r--p 00008000 08:16 528028     /usr/lib/i386-linux-gnu/libXrandr.so.2.2.0
 b61f7000-b61f8000 rw-p 00009000 08:16 528028     /usr/lib/i386-linux-gnu/libXrandr.so.2.2.0
 b61f8000-b61fa000 r-xp 00000000 08:16 528031     /usr/lib/i386-linux-gnu/libXinerama.so.1.0.0
 b61fa000-b61fb000 r--p 00001000 08:16 528031     /usr/lib/i386-linux-gnu/libXinerama.so.1.0.0
 b61fb000-b61fc000 rw-p 00002000 08:16 528031     /usr/lib/i386-linux-gnu/libXinerama.so.1.0.0
 b61fc000-b6233000 r-xp 00000000 08:16 524280     /usr/lib/i386-linux-gnu/libfontconfig.so.1.6.2
 b6233000-b6234000 r--p 00036000 08:16 524280     /usr/lib/i386-linux-gnu/libfontconfig.so.1.6.2
 b6234000-b6235000 rw-p 00037000 08:16 524280     /usr/lib/i386-linux-gnu/libfontconfig.so.1.6.2
 b6235000-b627e000 r-xp 00000000 08:16 547982     /usr/lib/i386-linux-gnu/libpango-1.0.so.0.3200.5
 b627e000-b627f000 r--p 00049000 08:16 547982     /usr/lib/i386-linux-gnu/libpango-1.0.so.0.3200.5
 b627f000-b6280000 rw-p 0004a000 08:16 547982     /usr/lib/i386-linux-gnu/libpango-1.0.so.0.3200.5
 b6280000-b6292000 r-xp 00000000 08:16 528443     /usr/lib/i386-linux-gnu/libpangoft2-1.0.so.0.3200.5
 b6292000-b6293000 r--p 00011000 08:16 528443     /usr/lib/i386-linux-gnu/libpangoft2-1.0.so.0.3200.5
 b6293000-b6294000 rw-p 00012000 08:16 528443     /usr/lib/i386-linux-gnu/libpangoft2-1.0.so.0.3200.5
 b6294000-b62bb000 r-xp 00000000 08:16 528080     /usr/lib/i386-linux-gnu/libatk-bridge-2.0.so.0.0.0
 b62bb000-b62bc000 r--p 00027000 08:16 528080     /usr/lib/i386-linux-gnu/libatk-bridge-2.0.so.0.0.0
 b62bc000-b62bd000 rw-p 00028000 08:16 528080     /usr/lib/i386-linux-gnu/libatk-bridge-2.0.so.0.0.0
 b62bd000-b62db000 r-xp 00000000 08:16 527572     /usr/lib/i386-linux-gnu/libatk-1.0.so.0.20809.1
 b62db000-b62dd000 r--p 0001d000 08:16 527572     /usr/lib/i386-linux-gnu/libatk-1.0.so.0.20809.1
 b62dd000-b62de000 rw-p 0001f000 08:16 527572     /usr/lib/i386-linux-gnu/libatk-1.0.so.0.20809.1
 b62de000-b62fe000 r-xp 00000000 08:16 523739     /usr/lib/i386-linux-gnu/libgdk_pixbuf-2.0.so.0.2800.0
 b62fe000-b62ff000 ---p 00020000 08:16 523739     /usr/lib/i386-linux-gnu/libgdk_pixbuf-2.0.so.0.2800.0
 b62ff000-b6300000 r--p 00020000 08:16 523739     /usr/lib/i386-linux-gnu/libgdk_pixbuf-2.0.so.0.2800.0
 b6300000-b6301000 rw-p 00021000 08:16 523739     /usr/lib/i386-linux-gnu/libgdk_pixbuf-2.0.so.0.2800.0
 b6301000-b6414000 r-xp 00000000 08:16 524707     /usr/lib/i386-linux-gnu/libcairo.so.2.11200.14
 b6414000-b6416000 r--p 00113000 08:16 524707     /usr/lib/i386-linux-gnu/libcairo.so.2.11200.14
 b6416000-b6417000 rw-p 00115000 08:16 524707     /usr/lib/i386-linux-gnu/libcairo.so.2.11200.14
 b6417000-b6418000 rw-p 00000000 00:00 0 
 b6418000-b641d000 r-xp 00000000 08:16 528082     /usr/lib/i386-linux-gnu/libcairo-gobject.so.2.11200.14
 b641d000-b641e000 r--p 00005000 08:16 528082     /usr/lib/i386-linux-gnu/libcairo-gobject.so.2.11200.14
 b641e000-b641f000 rw-p 00006000 08:16 528082     /usr/lib/i386-linux-gnu/libcairo-gobject.so.2.11200.14
 b641f000-b6424000 r-xp 00000000 08:16 528025     /usr/lib/i386-linux-gnu/libXfixes.so.3.1.0
 b6424000-b6425000 r--p 00004000 08:16 528025     /usr/lib/i386-linux-gnu/libXfixes.so.3.1.0
 b6425000-b6426000 rw-p 00005000 08:16 528025     /usr/lib/i386-linux-gnu/libXfixes.so.3.1.0
 b6426000-b6434000 r-xp 00000000 08:16 528144     /usr/lib/i386-linux-gnu/libXi.so.6.1.0
 b6434000-b6435000 r--p 0000d000 08:16 528144     /usr/lib/i386-linux-gnu/libXi.so.6.1.0
 b6435000-b6436000 rw-p 0000e000 08:16 528144     /usr/lib/i386-linux-gnu/libXi.so.6.1.0
 b6436000-b6568000 r-xp 00000000 08:16 524693     /usr/lib/i386-linux-gnu/libX11.so.6.3.0
 b6568000-b6569000 r--p 00132000 08:16 524693     /usr/lib/i386-linux-gnu/libX11.so.6.3.0
 b6569000-b656c000 rw-p 00133000 08:16 524693     /usr/lib/i386-linux-gnu/libX11.so.6.3.0
 b656c000-b6577000 r-xp 00000000 08:16 547981     /usr/lib/i386-linux-gnu/libpangocairo-1.0.so.0.3200.5
 b6577000-b6578000 r--p 0000a000 08:16 547981     /usr/lib/i386-linux-gnu/libpangocairo-1.0.so.0.3200.5
 b6578000-b6579000 rw-p 0000b000 08:16 547981     /usr/lib/i386-linux-gnu/libpangocairo-1.0.so.0.3200.5
 b6579000-b6601000 r-xp 00000000 08:16 547239     /usr/lib/i386-linux-gnu/libgdk-3.so.0.600.4
 b6601000-b6602000 ---p 00088000 08:16 547239     /usr/lib/i386-linux-gnu/libgdk-3.so.0.600.4
 b6602000-b6604000 r--p 00088000 08:16 547239     /usr/lib/i386-linux-gnu/libgdk-3.so.0.600.4
 b6604000-b6605000 rw-p 0008a000 08:16 547239     /usr/lib/i386-linux-gnu/libgdk-3.so.0.600.4
 b6605000-b6aed000 r-xp 00000000 08:16 547240     /usr/lib/i386-linux-gnu/libgtk-3.so.0.600.4
 b6aed000-b6af2000 r--p 004e7000 08:16 547240     /usr/lib/i386-linux-gnu/libgtk-3.so.0.600.4
 b6af2000-b6af5000 rw-p 004ec000 08:16 547240     /usr/lib/i386-linux-gnu/libgtk-3.so.0.600.4
 b6af5000-b6af6000 rw-p 00000000 00:00 0 
 b6af8000-b6b0a000 r-xp 00000000 08:16 524095     /usr/lib/i386-linux-gnu/gtk-3.0/modules/liboverlay-scrollbar.so
 b6b0a000-b6b0b000 r--p 00011000 08:16 524095     /usr/lib/i386-linux-gnu/gtk-3.0/modules/liboverlay-scrollbar.so
 b6b0b000-b6b0c000 rw-p 00012000 08:16 524095     /usr/lib/i386-linux-gnu/gtk-3.0/modules/liboverlay-scrollbar.so
 b6b0c000-b6bcc000 rw-p 00000000 00:00 0 
 b6bcc000-b6bdc000 r--p 00000000 08:16 537050     /usr/lib/girepository-1.0/Atk-1.0.typelib
 b6bdc000-b6be0000 r--p 00000000 08:16 537051     /usr/lib/girepository-1.0/GdkPixbuf-2.0.typelib
 b6be0000-b6c2b000 r--p 00000000 08:16 524724     /usr/lib/girepository-1.0/Gio-2.0.typelib
 b6c2b000-b6c55000 r--p 00000000 08:16 524727     /usr/lib/girepository-1.0/GLib-2.0.typelib
 b6c55000-b6c63000 r--p 00000000 08:16 524726     /usr/lib/girepository-1.0/GObject-2.0.typelib
 b6c63000-b6c97000 r--p 00000000 08:16 527478     /usr/lib/girepository-1.0/Gdk-3.0.typelib
 b6c97000-b6d23000 r--p 00000000 08:16 527479     /usr/lib/girepository-1.0/Gtk-3.0.typelib
 b6d23000-b6d63000 rw-p 00000000 00:00 0 
 b6d74000-b6d76000 r-xp 00000000 08:16 547511     /usr/lib/python3.3/lib-dynload/_bz2.cpython-33m-i386-linux-gnu.so
 b6d76000-b6d77000 r--p 00001000 08:16 547511     /usr/lib/python3.3/lib-dynload/_bz2.cpython-33m-i386-linux-gnu.so
 b6d77000-b6d78000 rw-p 00002000 08:16 547511     /usr/lib/python3.3/lib-dynload/_bz2.cpython-33m-i386-linux-gnu.so
 b6d78000-b6d7c000 r-xp 00000000 08:16 530228     /usr/lib/i386-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-png.so
 b6d7c000-b6d7d000 r--p 00003000 08:16 530228     /usr/lib/i386-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-png.so
 b6d7d000-b6d7e000 rw-p 00004000 08:16 530228     /usr/lib/i386-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-png.so
 b6d7e000-b6d8b000 r-xp 00000000 08:16 547492     /usr/lib/python3.3/lib-dynload/_ssl.cpython-33m-i386-linux-gnu.so
 b6d8b000-b6d8c000 r--p 0000c000 08:16 547492     /usr/lib/python3.3/lib-dynload/_ssl.cpython-33m-i386-linux-gnu.so
 b6d8c000-b6d8f000 rw-p 0000d000 08:16 547492     /usr/lib/python3.3/lib-dynload/_ssl.cpython-33m-i386-linux-gnu.so
 b6d8f000-b6d92000 r-xp 00000000 08:16 547507     /usr/lib/python3.3/lib-dynload/_hashlib.cpython-33m-i386-linux-gnu.so
 b6d92000-b6d93000 r--p 00003000 08:16 547507     /usr/lib/python3.3/lib-dynload/_hashlib.cpython-33m-i386-linux-gnu.so
 b6d93000-b6d94000 rw-p 00004000 08:16 547507     /usr/lib/python3.3/lib-dynload/_hashlib.cpython-33m-i386-linux-gnu.so
 b6d94000-b6dd4000 rw-p 00000000 00:00 0 
 b6dd4000-b6df2000 r-xp 00000000 08:16 785221     /usr/lib/python3/dist-packages/gi/_gobject/_gobject.cpython-33m-i386-linux-gnu.so
 b6df2000-b6df3000 r--p 0001d000 08:16 785221     /usr/lib/python3/dist-packages/gi/_gobject/_gobject.cpython-33m-i386-linux-gnu.so
 b6df3000-b6df5000 rw-p 0001e000 08:16 785221     /usr/lib/python3/dist-packages/gi/_gobject/_gobject.cpython-33m-i386-linux-gnu.so
 b6df5000-b6e08000 r-xp 00000000 08:16 1191254    /lib/i386-linux-gnu/libresolv-2.17.so
 b6e08000-b6e09000 r--p 00013000 08:16 1191254    /lib/i386-linux-gnu/libresolv-2.17.so
 b6e09000-b6e0a000 rw-p 00014000 08:16 1191254    /lib/i386-linux-gnu/libresolv-2.17.so
 b6e0a000-b6e0c000 rw-p 00000000 00:00 0 
 b6e0c000-b6e29000 r-xp 00000000 08:16 1178145    /lib/i386-linux-gnu/libselinux.so.1
 b6e29000-b6e2a000 r--p 0001c000 08:16 1178145    /lib/i386-linux-gnu/libselinux.so.1
 b6e2a000-b6e2b000 rw-p 0001d000 08:16 1178145    /lib/i386-linux-gnu/libselinux.so.1
 b6e2b000-b6e6a000 r-xp 00000000 08:16 1177438    /lib/i386-linux-gnu/libpcre.so.3.13.1
 b6e6a000-b6e6b000 r--p 0003f000 08:16 1177438    /lib/i386-linux-gnu/libpcre.so.3.13.1
 b6e6b000-b6e6c000 rw-p 00040000 08:16 1177438    /lib/i386-linux-gnu/libpcre.so.3.13.1
 b6e6c000-b6e71000 r-xp 00000000 08:16 523653     /usr/lib/i386-linux-gnu/libffi.so.6.0.1
 b6e71000-b6e72000 r--p 00005000 08:16 523653     /usr/lib/i386-linux-gnu/libffi.so.6.0.1
 b6e72000-b6e73000 rw-p 00006000 08:16 523653     /usr/lib/i386-linux-gnu/libffi.so.6.0.1
 b6e73000-b6fd3000 r-xp 00000000 08:16 524332     /usr/lib/i386-linux-gnu/libgio-2.0.so.0.3600.0
 b6fd3000-b6fd5000 r--p 00160000 08:16 524332     /usr/lib/i386-linux-gnu/libgio-2.0.so.0.3600.0
 b6fd5000-b6fd6000 rw-p 00162000 08:16 524332     /usr/lib/i386-linux-gnu/libgio-2.0.so.0.3600.0
 b6fd6000-b6fd7000 rw-p 00000000 00:00 0 
 b6fd7000-b70d6000 r-xp 00000000 08:16 1181541    /lib/i386-linux-gnu/libglib-2.0.so.0.3600.0
 b70d6000-b70d7000 r--p 000fe000 08:16 1181541    /lib/i386-linux-gnu/libglib-2.0.so.0.3600.0
 b70d7000-b70d8000 rw-p 000ff000 08:16 1181541    /lib/i386-linux-gnu/libglib-2.0.so.0.3600.0
 b70d8000-b7126000 r-xp 00000000 08:16 528173     /usr/lib/i386-linux-gnu/libgobject-2.0.so.0.3600.0
 b7126000-b7127000 r--p 0004d000 08:16 528173     /usr/lib/i386-linux-gnu/libgobject-2.0.so.0.3600.0
 b7127000-b7128000 rw-p 0004e000 08:16 528173     /usr/lib/i386-linux-gnu/libgobject-2.0.so.0.3600.0
 b7128000-b715d000 r-xp 00000000 08:16 524710     /usr/lib/libgirepository-1.0.so.1.0.0
 b715d000-b715e000 r--p 00034000 08:16 524710     /usr/lib/libgirepository-1.0.so.1.0.0
 b715e000-b715f000 rw-p 00035000 08:16 524710     /usr/lib/libgirepository-1.0.so.1.0.0
 b715f000-b7160000 rwxp 00000000 00:00 0 
 b7160000-b7161000 r--s 00000000 00:14 19965      /run/user/amiralex/dconf/user (deleted)
 b7161000-b716e000 r--p 00000000 08:16 537053     /usr/lib/girepository-1.0/Pango-1.0.typelib
 b716e000-b7173000 r-xp 00000000 08:16 785880     /usr/lib/python3/dist-packages/gi/_glib/_glib.cpython-33m-i386-linux-gnu.so
 b7173000-b7174000 r--p 00004000 08:16 785880     /usr/lib/python3/dist-packages/gi/_glib/_glib.cpython-33m-i386-linux-gnu.so
 b7174000-b7175000 rw-p 00005000 08:16 785880     /usr/lib/python3/dist-packages/gi/_glib/_glib.cpython-33m-i386-linux-gnu.so
 b7175000-b7197000 r-xp 00000000 08:16 657129     /usr/lib/python3/dist-packages/gi/_gi.cpython-33m-i386-linux-gnu.so
 b7197000-b7198000 r--p 00021000 08:16 657129     /usr/lib/python3/dist-packages/gi/_gi.cpython-33m-i386-linux-gnu.so
 b7198000-b719b000 rw-p 00022000 08:16 657129     /usr/lib/python3/dist-packages/gi/_gi.cpython-33m-i386-linux-gnu.so
 b719b000-b731b000 rw-p 00000000 00:00 0 
 b731b000-b751b000 r--p 00000000 08:16 523394     /usr/lib/locale/locale-archive
 b751b000-b751c000 rw-p 00000000 00:00 0 
 b751c000-b755d000 r-xp 00000000 08:16 1178224    /lib/i386-linux-gnu/libm-2.17.so
 b755d000-b755e000 r--p 00040000 08:16 1178224    /lib/i386-linux-gnu/libm-2.17.so
 b755e000-b755f000 rw-p 00041000 08:16 1178224    /lib/i386-linux-gnu/libm-2.17.so
 b755f000-b7560000 rw-p 00000000 00:00 0 
 b7560000-b770d000 r-xp 00000000 08:16 1191243    /lib/i386-linux-gnu/libc-2.17.so
 b770d000-b770f000 r--p 001ad000 08:16 1191243    /lib/i386-linux-gnu/libc-2.17.so
 b770f000-b7710000 rw-p 001af000 08:16 1191243    /lib/i386-linux-gnu/libc-2.17.so
 b7710000-b7713000 rw-p 00000000 00:00 0 
 b7713000-b772a000 r-xp 00000000 08:16 1178058    /lib/i386-linux-gnu/libz.so.1.2.7
 b772a000-b772b000 r--p 00016000 08:16 1178058    /lib/i386-linux-gnu/libz.so.1.2.7
 b772b000-b772c000 rw-p 00017000 08:16 1178058    /lib/i386-linux-gnu/libz.so.1.2.7
 b772c000-b7751000 r-xp 00000000 08:16 1178050    /lib/i386-linux-gnu/libexpat.so.1.6.0
 b7751000-b7753000 r--p 00025000 08:16 1178050    /lib/i386-linux-gnu/libexpat.so.1.6.0
 b7753000-b7754000 rw-p 00027000 08:16 1178050    /lib/i386-linux-gnu/libexpat.so.1.6.0
 b7754000-b775b000 r-xp 00000000 08:16 1178220    /lib/i386-linux-gnu/librt-2.17.so
 b775b000-b775c000 r--p 00006000 08:16 1178220    /lib/i386-linux-gnu/librt-2.17.so
 b775c000-b775d000 rw-p 00007000 08:16 1178220    /lib/i386-linux-gnu/librt-2.17.so
 b775d000-b775f000 r-xp 00000000 08:16 1191255    /lib/i386-linux-gnu/libutil-2.17.so
 b775f000-b7760000 r--p 00001000 08:16 1191255    /lib/i386-linux-gnu/libutil-2.17.so
 b7760000-b7761000 rw-p 00002000 08:16 1191255    /lib/i386-linux-gnu/libutil-2.17.so
 b7761000-b7762000 rw-p 00000000 00:00 0 
 b7762000-b7765000 r-xp 00000000 08:16 1191252    /lib/i386-linux-gnu/libdl-2.17.so
 b7765000-b7766000 r--p 00002000 08:16 1191252    /lib/i386-linux-gnu/libdl-2.17.so
 b7766000-b7767000 rw-p 00003000 08:16 1191252    /lib/i386-linux-gnu/libdl-2.17.so
 b7767000-b777e000 r-xp 00000000 08:16 1191247    /lib/i386-linux-gnu/libpthread-2.17.so
 b777e000-b777f000 r--p 00016000 08:16 1191247    /lib/i386-linux-gnu/libpthread-2.17.so
 b777f000-b7780000 rw-p 00017000 08:16 1191247    /lib/i386-linux-gnu/libpthread-2.17.so
 b7780000-b7782000 rw-p 00000000 00:00 0 
 b7782000-b7783000 r--p 00000000 08:16 1062824    /usr/share/locale-langpack/en/LC_MESSAGES/gtk30.mo
 b7783000-b7784000 r--p 00000000 08:16 524725     /usr/lib/girepository-1.0/GModule-2.0.typelib
 b7784000-b7785000 r--p 00000000 08:16 524715     /usr/lib/girepository-1.0/cairo-1.0.typelib
 b7785000-b7786000 r--p 00000000 08:16 524718     /usr/lib/girepository-1.0/xlib-2.0.typelib
 b7786000-b7789000 r-xp 00000000 08:16 524330     /usr/lib/i386-linux-gnu/libgmodule-2.0.so.0.3600.0
 b7789000-b778a000 r--p 00002000 08:16 524330     /usr/lib/i386-linux-gnu/libgmodule-2.0.so.0.3600.0
 b778a000-b778b000 rw-p 00003000 08:16 524330     /usr/lib/i386-linux-gnu/libgmodule-2.0.so.0.3600.0
 b778b000-b778e000 r-xp 00000000 08:16 529487     /usr/lib/i386-linux-gnu/libpyglib-gi-2.0-python3.3.so.0.0.0
 b778e000-b778f000 r--p 00002000 08:16 529487     /usr/lib/i386-linux-gnu/libpyglib-gi-2.0-python3.3.so.0.0.0
 b778f000-b7790000 rw-p 00003000 08:16 529487     /usr/lib/i386-linux-gnu/libpyglib-gi-2.0-python3.3.so.0.0.0
 b7790000-b7797000 r--s 00000000 08:16 543590     /usr/lib/i386-linux-gnu/gconv/gconv-modules.cache
 b7797000-b7798000 r--p 002c5000 08:16 523394     /usr/lib/locale/locale-archive
 b7798000-b779a000 rw-p 00000000 00:00 0 
 b779a000-b779b000 r-xp 00000000 00:00 0          [vdso]
 b779b000-b77bb000 r-xp 00000000 08:16 1191256    /lib/i386-linux-gnu/ld-2.17.so
 b77bb000-b77bc000 r--p 0001f000 08:16 1191256    /lib/i386-linux-gnu/ld-2.17.so
 b77bc000-b77bd000 rw-p 00020000 08:16 1191256    /lib/i386-linux-gnu/ld-2.17.so
 bfb5d000-bfb7e000 rw-p 00000000 00:00 0          [stack]
ProcStatus:
 Name:    python3
 State:    R (running)
 Tgid:    3854
 Pid:    3854
 PPid:    3853
 TracerPid:    0
 Uid:    1000    1000    1000    1000
 Gid:    1000    1000    1000    1000
 FDSize:    32
 Groups:    4 24 27 30 46 107 124 1000 
 VmPeak:      107800 kB
 VmSize:       84156 kB
 VmLck:           0 kB
 VmPin:           0 kB
 VmHWM:       42428 kB
 VmRSS:       24644 kB
 VmData:       29164 kB
 VmStk:         136 kB
 VmExe:        2636 kB
 VmLib:       46520 kB
 VmPTE:         120 kB
 VmSwap:           0 kB
 Threads:    3
 SigQ:    0/7820
 SigPnd:    0000000000000000
 ShdPnd:    0000000000000000
 SigBlk:    0000000000000000
 SigIgn:    0000000001001000
 SigCgt:    0000000180000002
 CapInh:    0000000000000000
 CapPrm:    0000000000000000
 CapEff:    0000000000000000
 CapBnd:    0000001fffffffff
 Seccomp:    0
 Cpus_allowed:    3
 Cpus_allowed_list:    0-1
 Mems_allowed:    1
 Mems_allowed_list:    0
 voluntary_ctxt_switches:    102
 nonvoluntary_ctxt_switches:    243
PythonArgs: ['/usr/bin/update-manager', '--no-update']
Traceback:
 Traceback (most recent call last):
   File "/usr/bin/update-manager", line 114, in <module>
     app = UpdateManager(data_dir, options)
   File "/usr/lib/python3/dist-packages/UpdateManager/UpdateManager.py", line 111, in __init__
     self.options and self.options.use_proposed)
   File "/usr/lib/python3/dist-packages/UpdateManager/MetaReleaseGObject.py", line 44, in __init__
     MetaReleaseCore.__init__(self, useDevelopmentRelease, useProposed)
   File "/usr/lib/python3/dist-packages/UpdateManager/Core/MetaRelease.py", line 90, in __init__
     self.flavor_name = get_ubuntu_flavor_name()
   File "/usr/lib/python3/dist-packages/UpdateManager/Core/utils.py", line 447, in get_ubuntu_flavor_name
     pkg = get_ubuntu_flavor_package(cache=cache)
   File "/usr/lib/python3/dist-packages/UpdateManager/Core/utils.py", line 437, in get_ubuntu_flavor_package
     cache = apt.Cache()
   File "/usr/lib/python3/dist-packages/apt/cache.py", line 105, in __init__
     self.open(progress)
   File "/usr/lib/python3/dist-packages/apt/cache.py", line 150, in open
     self._cache = apt_pkg.Cache(progress)
 SystemError: E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/eg.archive.ubuntu.com_ubuntu_dists_raring_multiverse_i18n_Translation-en, E:The package lists or status file could not be parsed or opened.
UserGroups: adm cdrom dip lpadmin plugdev sambashare sudo

---

### Post by dino99 on 2013-06-06
glance at /var/crash/ folder and right-click on the crash file to report the issue on launchpad

---

### Post by amiralex32 on 2013-06-12
ProblemType: Crash
CrashCounter: 1
Date: Tue Jun  4 19:35:15 2013
ExecutablePath: /usr/bin/update-manager
ExecutableTimestamp: 1366140455
InterpreterPath: /usr/bin/python3.3
ProcCmdline: /usr/bin/python3 /usr/bin/update-manager --no-update
ProcCwd: /home/amiralex
ProcEnviron:
 PATH=(custom, no user)
 XDG_RUNTIME_DIR=<set>
 LANG=en_US.UTF-8
 SHELL=/bin/bash
ProcMaps:
 08048000-082db000 r-xp 00000000 08:16 523460     /usr/bin/python3.3
 082db000-082dc000 r--p 00292000 08:16 523460     /usr/bin/python3.3
 082dc000-0835a000 rw-p 00293000 08:16 523460     /usr/bin/python3.3
 0835a000-08370000 rw-p 00000000 00:00 0 
 089f6000-08d59000 rw-p 00000000 00:00 0          [heap]
 b2c00000-b2d00000 rw-p 00000000 00:00 0 
 b2d00000-b2ecc000 r-xp 00000000 08:16 523326     /usr/lib/i386-linux-gnu/libicui18n.so.48.1.1
 b2ecc000-b2ed3000 r--p 001cb000 08:16 523326     /usr/lib/i386-linux-gnu/libicui18n.so.48.1.1
 b2ed3000-b2ed4000 rw-p 001d2000 08:16 523326     /usr/lib/i386-linux-gnu/libicui18n.so.48.1.1
 b2ed4000-b2ef9000 r-xp 00000000 08:16 528362     /usr/lib/i386-linux-gnu/libunity/libunity-protocol-private.so.0.0.0
 b2ef9000-b2efa000 r--p 00025000 08:16 528362     /usr/lib/i386-linux-gnu/libunity/libunity-protocol-private.so.0.0.0
 b2efa000-b2efb000 rw-p 00026000 08:16 528362     /usr/lib/i386-linux-gnu/libunity/libunity-protocol-private.so.0.0.0
 b2efb000-b2f15000 r-xp 00000000 08:16 526785     /usr/lib/i386-linux-gnu/libdbusmenu-glib.so.4.0.12
 b2f15000-b2f16000 ---p 0001a000 08:16 526785     /usr/lib/i386-linux-gnu/libdbusmenu-glib.so.4.0.12
 b2f16000-b2f17000 r--p 0001a000 08:16 526785     /usr/lib/i386-linux-gnu/libdbusmenu-glib.so.4.0.12
 b2f17000-b2f18000 rw-p 0001b000 08:16 526785     /usr/lib/i386-linux-gnu/libdbusmenu-glib.so.4.0.12
 b2f18000-b2f51000 r-xp 00000000 08:16 526296     /usr/lib/i386-linux-gnu/libdee-1.0.so.4.2.1
 b2f51000-b2f52000 r--p 00038000 08:16 526296     /usr/lib/i386-linux-gnu/libdee-1.0.so.4.2.1
 b2f52000-b2f53000 rw-p 00039000 08:16 526296     /usr/lib/i386-linux-gnu/libdee-1.0.so.4.2.1
 b2f53000-b2fa7000 r-xp 00000000 08:16 528363     /usr/lib/i386-linux-gnu/libgee.so.2.0.0
 b2fa7000-b2fa9000 r--p 00053000 08:16 528363     /usr/lib/i386-linux-gnu/libgee.so.2.0.0
 b2fa9000-b2faa000 rw-p 00055000 08:16 528363     /usr/lib/i386-linux-gnu/libgee.so.2.0.0
 b2faa000-b301e000 r-xp 00000000 08:16 547645     /usr/lib/i386-linux-gnu/libunity.so.9.0.2
 b301e000-b3020000 r--p 00073000 08:16 547645     /usr/lib/i386-linux-gnu/libunity.so.9.0.2
 b3020000-b3021000 rw-p 00075000 08:16 547645     /usr/lib/i386-linux-gnu/libunity.so.9.0.2
 b3037000-b3057000 r--s 00000000 08:16 922114     /usr/share/mime/mime.cache
 b3057000-b3157000 rw-p 00000000 00:00 0 
 b3157000-b31a8000 r-xp 00000000 08:16 1178074    /lib/i386-linux-gnu/libssl.so.1.0.0
 b31a8000-b31aa000 r--p 00050000 08:16 1178074    /lib/i386-linux-gnu/libssl.so.1.0.0
 b31aa000-b31ae000 rw-p 00052000 08:16 1178074    /lib/i386-linux-gnu/libssl.so.1.0.0
 b31ae000-b31ee000 rw-p 00000000 00:00 0 
 b31ee000-b3380000 r-xp 00000000 08:16 1178073    /lib/i386-linux-gnu/libcrypto.so.1.0.0
 b3380000-b338f000 r--p 00192000 08:16 1178073    /lib/i386-linux-gnu/libcrypto.so.1.0.0
 b338f000-b3396000 rw-p 001a1000 08:16 1178073    /lib/i386-linux-gnu/libcrypto.so.1.0.0
 b3396000-b347a000 rw-p 00000000 00:00 0 
 b347a000-b3484000 r--p 00000000 08:16 528169     /usr/lib/girepository-1.0/Dee-1.0.typelib
 b3484000-b34a8000 r-xp 00000000 08:16 523730     /usr/lib/i386-linux-gnu/libdbus-glib-1.so.2.2.2
 b34a8000-b34a9000 r--p 00023000 08:16 523730     /usr/lib/i386-linux-gnu/libdbus-glib-1.so.2.2.2
 b34a9000-b34aa000 rw-p 00024000 08:16 523730     /usr/lib/i386-linux-gnu/libdbus-glib-1.so.2.2.2
 b34aa000-b34c2000 r-xp 00000000 08:16 524018     /usr/lib/python3/dist-packages/_dbus_bindings.cpython-33m-i386-linux-gnu.so
 b34c2000-b34c3000 r--p 00017000 08:16 524018     /usr/lib/python3/dist-packages/_dbus_bindings.cpython-33m-i386-linux-gnu.so
 b34c3000-b34ce000 rw-p 00018000 08:16 524018     /usr/lib/python3/dist-packages/_dbus_bindings.cpython-33m-i386-linux-gnu.so
 b34ce000-b34dd000 r-xp 00000000 08:16 1178038    /lib/i386-linux-gnu/libbz2.so.1.0.4
 b34dd000-b34de000 r--p 0000e000 08:16 1178038    /lib/i386-linux-gnu/libbz2.so.1.0.4
 b34de000-b34df000 rw-p 0000f000 08:16 1178038    /lib/i386-linux-gnu/libbz2.so.1.0.4
 b34df000-b35fd000 r-xp 00000000 08:16 524226     /usr/lib/i386-linux-gnu/libapt-pkg.so.4.12.0
 b35fd000-b35ff000 r--p 0011e000 08:16 524226     /usr/lib/i386-linux-gnu/libapt-pkg.so.4.12.0
 b35ff000-b3600000 rw-p 00120000 08:16 524226     /usr/lib/i386-linux-gnu/libapt-pkg.so.4.12.0
 b3600000-b3621000 rw-p 00000000 00:00 0 
 b3621000-b3700000 ---p 00000000 00:00 0 
 b3708000-b3747000 r-xp 00000000 08:16 532410     /usr/lib/python3/dist-packages/apt_pkg.cpython-33m-i386-linux-gnu.so
 b3747000-b3748000 r--p 0003e000 08:16 532410     /usr/lib/python3/dist-packages/apt_pkg.cpython-33m-i386-linux-gnu.so
 b3748000-b374d000 rw-p 0003f000 08:16 532410     /usr/lib/python3/dist-packages/apt_pkg.cpython-33m-i386-linux-gnu.so
 b374d000-b378d000 rw-p 00000000 00:00 0 
 b378d000-b3793000 r-xp 00000000 08:16 528526     /usr/lib/i386-linux-gnu/libogg.so.0.8.0
 b3793000-b3794000 r--p 00005000 08:16 528526     /usr/lib/i386-linux-gnu/libogg.so.0.8.0
 b3794000-b3795000 rw-p 00006000 08:16 528526     /usr/lib/i386-linux-gnu/libogg.so.0.8.0
 b3795000-b37be000 r-xp 00000000 08:16 528732     /usr/lib/i386-linux-gnu/libvorbis.so.0.4.5
 b37be000-b37bf000 ---p 00029000 08:16 528732     /usr/lib/i386-linux-gnu/libvorbis.so.0.4.5
 b37bf000-b37c0000 r--p 00029000 08:16 528732     /usr/lib/i386-linux-gnu/libvorbis.so.0.4.5
 b37c0000-b37c1000 rw-p 0002a000 08:16 528732     /usr/lib/i386-linux-gnu/libvorbis.so.0.4.5
 b37c1000-b37ca000 r-xp 00000000 08:16 524218     /usr/lib/i386-linux-gnu/libltdl.so.7.3.0
 b37ca000-b37cb000 r--p 00008000 08:16 524218     /usr/lib/i386-linux-gnu/libltdl.so.7.3.0
 b37cb000-b37cc000 rw-p 00009000 08:16 524218     /usr/lib/i386-linux-gnu/libltdl.so.7.3.0
 b37cc000-b37dd000 r-xp 00000000 08:16 523963     /usr/lib/i386-linux-gnu/libtdb.so.1.2.10
 b37dd000-b37de000 r--p 00010000 08:16 523963     /usr/lib/i386-linux-gnu/libtdb.so.1.2.10
 b37de000-b37df000 rw-p 00011000 08:16 523963     /usr/lib/i386-linux-gnu/libtdb.so.1.2.10
 b37df000-b37e7000 r-xp 00000000 08:16 528736     /usr/lib/i386-linux-gnu/libvorbisfile.so.3.3.4
 b37e7000-b37e8000 r--p 00007000 08:16 528736     /usr/lib/i386-linux-gnu/libvorbisfile.so.3.3.4
 b37e8000-b37e9000 rw-p 00008000 08:16 528736     /usr/lib/i386-linux-gnu/libvorbisfile.so.3.3.4
 b37f1000-b37fa000 r--p 00000000 08:16 527124     /usr/lib/girepository-1.0/Unity-6.0.typelib
 b37fa000-b37ff000 r--p 00000000 08:16 526772     /usr/lib/girepository-1.0/Dbusmenu-0.4.typelib
 b37ff000-b3800000 ---p 00000000 00:00 0 
 b3800000-b4000000 rw-p 00000000 00:00 0          [stack:3856]
 b4000000-b4021000 rw-p 00000000 00:00 0 
 b4021000-b4100000 ---p 00000000 00:00 0 
 b4102000-b4111000 r-xp 00000000 08:16 524387     /usr/lib/i386-linux-gnu/libcanberra.so.0.2.5
 b4111000-b4112000 r--p 0000e000 08:16 524387     /usr/lib/i386-linux-gnu/libcanberra.so.0.2.5
 b4112000-b4113000 rw-p 0000f000 08:16 524387     /usr/lib/i386-linux-gnu/libcanberra.so.0.2.5
 b4113000-b4123000 r-xp 00000000 08:16 1185930    /lib/i386-linux-gnu/libudev.so.1.2.2
 b4123000-b4124000 r--p 0000f000 08:16 1185930    /lib/i386-linux-gnu/libudev.so.1.2.2
 b4124000-b4125000 rw-p 00010000 08:16 1185930    /lib/i386-linux-gnu/libudev.so.1.2.2
 b4125000-b4127000 r-xp 00000000 08:16 523454     /usr/lib/python3/dist-packages/_dbus_glib_bindings.cpython-33m-i386-linux-gnu.so
 b4127000-b4128000 r--p 00001000 08:16 523454     /usr/lib/python3/dist-packages/_dbus_glib_bindings.cpython-33m-i386-linux-gnu.so
 b4128000-b4129000 rw-p 00002000 08:16 523454     /usr/lib/python3/dist-packages/_dbus_glib_bindings.cpython-33m-i386-linux-gnu.so
 b4129000-b412d000 r-xp 00000000 08:16 527891     /usr/lib/i386-linux-gnu/libcanberra-gtk3.so.0.1.9
 b412d000-b412e000 r--p 00003000 08:16 527891     /usr/lib/i386-linux-gnu/libcanberra-gtk3.so.0.1.9
 b412e000-b412f000 rw-p 00004000 08:16 527891     /usr/lib/i386-linux-gnu/libcanberra-gtk3.so.0.1.9
 b412f000-b4133000 r-xp 00000000 08:16 524825     /usr/lib/i386-linux-gnu/gtk-3.0/modules/libcanberra-gtk3-module.so
 b4133000-b4134000 ---p 00004000 08:16 524825     /usr/lib/i386-linux-gnu/gtk-3.0/modules/libcanberra-gtk3-module.so
 b4134000-b4135000 r--p 00004000 08:16 524825     /usr/lib/i386-linux-gnu/gtk-3.0/modules/libcanberra-gtk3-module.so
 b4135000-b4136000 rw-p 00005000 08:16 524825     /usr/lib/i386-linux-gnu/gtk-3.0/modules/libcanberra-gtk3-module.so
 b4136000-b4139000 r-xp 00000000 08:16 657093     /usr/lib/i386-linux-gnu/gtk-3.0/3.0.0/theming-engines/libunico.so
 b4139000-b413a000 r--p 00002000 08:16 657093     /usr/lib/i386-linux-gnu/gtk-3.0/3.0.0/theming-engines/libunico.so
 b413a000-b413b000 rw-p 00003000 08:16 657093     /usr/lib/i386-linux-gnu/gtk-3.0/3.0.0/theming-engines/libunico.so
 b413b000-b416d000 r-xp 00000000 08:16 527845     /usr/lib/i386-linux-gnu/gvfs/libgvfscommon.so
 b416d000-b416e000 ---p 00032000 08:16 527845     /usr/lib/i386-linux-gnu/gvfs/libgvfscommon.so
 b416e000-b4170000 r--p 00032000 08:16 527845     /usr/lib/i386-linux-gnu/gvfs/libgvfscommon.so
 b4170000-b4171000 rw-p 00034000 08:16 527845     /usr/lib/i386-linux-gnu/gvfs/libgvfscommon.so
 b4171000-b41a1000 r-xp 00000000 08:16 524047     /usr/lib/i386-linux-gnu/gio/modules/libgvfsdbus.so
 b41a1000-b41a2000 r--p 0002f000 08:16 524047     /usr/lib/i386-linux-gnu/gio/modules/libgvfsdbus.so
 b41a2000-b41a3000 rw-p 00030000 08:16 524047     /usr/lib/i386-linux-gnu/gio/modules/libgvfsdbus.so
 b41a3000-b41a4000 ---p 00000000 00:00 0 
 b41a4000-b49a4000 rw-p 00000000 00:00 0          [stack:3855]
 b49a4000-b49a9000 r--p 00000000 08:16 2097861    /home/amiralex/.config/dconf/user (deleted)
 b49a9000-b49b3000 r-xp 00000000 08:16 524197     /usr/lib/i386-linux-gnu/gio/modules/libdconfsettings.so
 b49b3000-b49b4000 r--p 00009000 08:16 524197     /usr/lib/i386-linux-gnu/gio/modules/libdconfsettings.so
 b49b4000-b49b5000 rw-p 0000a000 08:16 524197     /usr/lib/i386-linux-gnu/gio/modules/libdconfsettings.so
 b49b5000-b49f0000 r--p 00000000 08:16 932153     /usr/share/glib-2.0/schemas/gschemas.compiled
 b49f0000-b4ab0000 rw-p 00000000 00:00 0 
 b4ab0000-b5c1f000 r-xp 00000000 08:16 523684     /usr/lib/i386-linux-gnu/libicudata.so.48.1.1
 b5c1f000-b5c20000 r--p 0116e000 08:16 523684     /usr/lib/i386-linux-gnu/libicudata.so.48.1.1
 b5c20000-b5c21000 rw-p 0116f000 08:16 523684     /usr/lib/i386-linux-gnu/libicudata.so.48.1.1
 b5c21000-b5c3c000 r-xp 00000000 08:16 1178032    /lib/i386-linux-gnu/libgcc_s.so.1
 b5c3c000-b5c3d000 r--p 0001a000 08:16 1178032    /lib/i386-linux-gnu/libgcc_s.so.1
 b5c3d000-b5c3e000 rw-p 0001b000 08:16 1178032    /lib/i386-linux-gnu/libgcc_s.so.1
 b5c3e000-b5d1a000 r-xp 00000000 08:16 523616     /usr/lib/i386-linux-gnu/libstdc++.so.6.0.17
 b5d1a000-b5d1b000 ---p 000dc000 08:16 523616     /usr/lib/i386-linux-gnu/libstdc++.so.6.0.17
 b5d1b000-b5d1f000 r--p 000dc000 08:16 523616     /usr/lib/i386-linux-gnu/libstdc++.so.6.0.17
 b5d1f000-b5d20000 rw-p 000e0000 08:16 523616     /usr/lib/i386-linux-gnu/libstdc++.so.6.0.17
 b5d20000-b5d27000 rw-p 00000000 00:00 0 
 b5d27000-b5e7d000 r-xp 00000000 08:16 523288     /usr/lib/i386-linux-gnu/libicuuc.so.48.1.1
 b5e7d000-b5e87000 r--p 00155000 08:16 523288     /usr/lib/i386-linux-gnu/libicuuc.so.48.1.1
 b5e87000-b5e88000 rw-p 0015f000 08:16 523288     /usr/lib/i386-linux-gnu/libicuuc.so.48.1.1
 b5e88000-b5e8c000 rw-p 00000000 00:00 0 
 b5e8c000-b5ebf000 r-xp 00000000 08:16 523319     /usr/lib/i386-linux-gnu/libicule.so.48.1.1
 b5ebf000-b5ec0000 ---p 00033000 08:16 523319     /usr/lib/i386-linux-gnu/libicule.so.48.1.1
 b5ec0000-b5ec1000 r--p 00033000 08:16 523319     /usr/lib/i386-linux-gnu/libicule.so.48.1.1
 b5ec1000-b5ec2000 rw-p 00034000 08:16 523319     /usr/lib/i386-linux-gnu/libicule.so.48.1.1
 b5ec2000-b5ec7000 r-xp 00000000 08:16 528021     /usr/lib/i386-linux-gnu/libXdmcp.so.6.0.0
 b5ec7000-b5ec8000 r--p 00004000 08:16 528021     /usr/lib/i386-linux-gnu/libXdmcp.so.6.0.0
 b5ec8000-b5ec9000 rw-p 00005000 08:16 528021     /usr/lib/i386-linux-gnu/libXdmcp.so.6.0.0
 b5ec9000-b5ecb000 r-xp 00000000 08:16 528010     /usr/lib/i386-linux-gnu/libXau.so.6.0.0
 b5ecb000-b5ecc000 r--p 00001000 08:16 528010     /usr/lib/i386-linux-gnu/libXau.so.6.0.0
 b5ecc000-b5ecd000 rw-p 00002000 08:16 528010     /usr/lib/i386-linux-gnu/libXau.so.6.0.0
 b5ecd000-b5f65000 r-xp 00000000 08:16 524924     /usr/lib/i386-linux-gnu/libharfbuzz.so.0.913.0
 b5f65000-b5f66000 ---p 00098000 08:16 524924     /usr/lib/i386-linux-gnu/libharfbuzz.so.0.913.0
 b5f66000-b5f67000 r--p 00098000 08:16 524924     /usr/lib/i386-linux-gnu/libharfbuzz.so.0.913.0
 b5f67000-b5f68000 rw-p 00099000 08:16 524924     /usr/lib/i386-linux-gnu/libharfbuzz.so.0.913.0
 b5f68000-b5fb0000 r-xp 00000000 08:16 1188118    /lib/i386-linux-gnu/libdbus-1.so.3.7.2
 b5fb0000-b5fb1000 r--p 00047000 08:16 1188118    /lib/i386-linux-gnu/libdbus-1.so.3.7.2
 b5fb1000-b5fb2000 rw-p 00048000 08:16 1188118    /lib/i386-linux-gnu/libdbus-1.so.3.7.2
 b5fb2000-b5fd4000 r-xp 00000000 08:16 527575     /usr/lib/i386-linux-gnu/libatspi.so.0.0.1
 b5fd4000-b5fd5000 ---p 00022000 08:16 527575     /usr/lib/i386-linux-gnu/libatspi.so.0.0.1
 b5fd5000-b5fd6000 r--p 00022000 08:16 527575     /usr/lib/i386-linux-gnu/libatspi.so.0.0.1
 b5fd6000-b5fd7000 rw-p 00023000 08:16 527575     /usr/lib/i386-linux-gnu/libatspi.so.0.0.1
 b5fd7000-b5fdf000 r-xp 00000000 08:16 528043     /usr/lib/i386-linux-gnu/libXrender.so.1.3.0
 b5fdf000-b5fe0000 r--p 00007000 08:16 528043     /usr/lib/i386-linux-gnu/libXrender.so.1.3.0
 b5fe0000-b5fe1000 rw-p 00008000 08:16 528043     /usr/lib/i386-linux-gnu/libXrender.so.1.3.0
 b5fe1000-b5fe9000 r-xp 00000000 08:16 524695     /usr/lib/i386-linux-gnu/libxcb-render.so.0.0.0
 b5fe9000-b5fea000 r--p 00008000 08:16 524695     /usr/lib/i386-linux-gnu/libxcb-render.so.0.0.0
 b5fea000-b5feb000 rw-p 00009000 08:16 524695     /usr/lib/i386-linux-gnu/libxcb-render.so.0.0.0
 b5feb000-b5fed000 r-xp 00000000 08:16 524697     /usr/lib/i386-linux-gnu/libxcb-shm.so.0.0.0
 b5fed000-b5fee000 r--p 00001000 08:16 524697     /usr/lib/i386-linux-gnu/libxcb-shm.so.0.0.0
 b5fee000-b5fef000 rw-p 00002000 08:16 524697     /usr/lib/i386-linux-gnu/libxcb-shm.so.0.0.0
 b5fef000-b6016000 r-xp 00000000 08:16 1178172    /lib/i386-linux-gnu/libpng12.so.0.49.0
 b6016000-b6017000 r--p 00026000 08:16 1178172    /lib/i386-linux-gnu/libpng12.so.0.49.0
 b6017000-b6018000 rw-p 00027000 08:16 1178172    /lib/i386-linux-gnu/libpng12.so.0.49.0
 b6018000-b60ac000 r-xp 00000000 08:16 523631     /usr/lib/i386-linux-gnu/libpixman-1.so.0.28.2
 b60ac000-b60b1000 r--p 00093000 08:16 523631     /usr/lib/i386-linux-gnu/libpixman-1.so.0.28.2
 b60b1000-b60b2000 rw-p 00098000 08:16 523631     /usr/lib/i386-linux-gnu/libpixman-1.so.0.28.2
 b60b2000-b60d2000 r-xp 00000000 08:16 523647     /usr/lib/i386-linux-gnu/libxcb.so.1.1.0
 b60d2000-b60d3000 r--p 0001f000 08:16 523647     /usr/lib/i386-linux-gnu/libxcb.so.1.1.0
 b60d3000-b60d4000 rw-p 00020000 08:16 523647     /usr/lib/i386-linux-gnu/libxcb.so.1.1.0
 b60d4000-b616a000 r-xp 00000000 08:16 524689     /usr/lib/i386-linux-gnu/libfreetype.so.6.10.0
 b616a000-b616e000 r--p 00095000 08:16 524689     /usr/lib/i386-linux-gnu/libfreetype.so.6.10.0
 b616e000-b616f000 rw-p 00099000 08:16 524689     /usr/lib/i386-linux-gnu/libfreetype.so.6.10.0
 b616f000-b617f000 r-xp 00000000 08:16 528023     /usr/lib/i386-linux-gnu/libXext.so.6.4.0
 b617f000-b6180000 r--p 0000f000 08:16 528023     /usr/lib/i386-linux-gnu/libXext.so.6.4.0
 b6180000-b6181000 rw-p 00010000 08:16 528023     /usr/lib/i386-linux-gnu/libXext.so.6.4.0
 b6181000-b6184000 r-xp 00000000 08:16 524334     /usr/lib/i386-linux-gnu/libwayland-cursor.so.0.0.0
 b6184000-b6185000 r--p 00003000 08:16 524334     /usr/lib/i386-linux-gnu/libwayland-cursor.so.0.0.0
 b6185000-b6189000 rw-p 00004000 08:16 524334     /usr/lib/i386-linux-gnu/libwayland-cursor.so.0.0.0
 b6189000-b61c4000 r-xp 00000000 08:16 526940     /usr/lib/i386-linux-gnu/libxkbcommon.so.0.0.0
 b61c4000-b61c5000 ---p 0003b000 08:16 526940     /usr/lib/i386-linux-gnu/libxkbcommon.so.0.0.0
 b61c5000-b61cf000 r--p 0003b000 08:16 526940     /usr/lib/i386-linux-gnu/libxkbcommon.so.0.0.0
 b61cf000-b61d0000 rw-p 00045000 08:16 526940     /usr/lib/i386-linux-gnu/libxkbcommon.so.0.0.0
 b61d0000-b61d8000 r-xp 00000000 08:16 526936     /usr/lib/i386-linux-gnu/libwayland-client.so.0.1.0
 b61d8000-b61d9000 r--p 00007000 08:16 526936     /usr/lib/i386-linux-gnu/libwayland-client.so.0.1.0
 b61d9000-b61da000 rw-p 00008000 08:16 526936     /usr/lib/i386-linux-gnu/libwayland-client.so.0.1.0
 b61da000-b61dc000 r-xp 00000000 08:16 528019     /usr/lib/i386-linux-gnu/libXdamage.so.1.1.0
 b61dc000-b61dd000 r--p 00001000 08:16 528019     /usr/lib/i386-linux-gnu/libXdamage.so.1.1.0
 b61dd000-b61de000 rw-p 00002000 08:16 528019     /usr/lib/i386-linux-gnu/libXdamage.so.1.1.0
 b61de000-b61e0000 r-xp 00000000 08:16 528015     /usr/lib/i386-linux-gnu/libXcomposite.so.1.0.0
 b61e0000-b61e1000 r--p 00001000 08:16 528015     /usr/lib/i386-linux-gnu/libXcomposite.so.1.0.0
 b61e1000-b61e2000 rw-p 00002000 08:16 528015     /usr/lib/i386-linux-gnu/libXcomposite.so.1.0.0
 b61e2000-b61eb000 r-xp 00000000 08:16 528017     /usr/lib/i386-linux-gnu/libXcursor.so.1.0.2
 b61eb000-b61ec000 r--p 00008000 08:16 528017     /usr/lib/i386-linux-gnu/libXcursor.so.1.0.2
 b61ec000-b61ed000 rw-p 00009000 08:16 528017     /usr/lib/i386-linux-gnu/libXcursor.so.1.0.2
 b61ed000-b61f6000 r-xp 00000000 08:16 528028     /usr/lib/i386-linux-gnu/libXrandr.so.2.2.0
 b61f6000-b61f7000 r--p 00008000 08:16 528028     /usr/lib/i386-linux-gnu/libXrandr.so.2.2.0
 b61f7000-b61f8000 rw-p 00009000 08:16 528028     /usr/lib/i386-linux-gnu/libXrandr.so.2.2.0
 b61f8000-b61fa000 r-xp 00000000 08:16 528031     /usr/lib/i386-linux-gnu/libXinerama.so.1.0.0
 b61fa000-b61fb000 r--p 00001000 08:16 528031     /usr/lib/i386-linux-gnu/libXinerama.so.1.0.0
 b61fb000-b61fc000 rw-p 00002000 08:16 528031     /usr/lib/i386-linux-gnu/libXinerama.so.1.0.0
 b61fc000-b6233000 r-xp 00000000 08:16 524280     /usr/lib/i386-linux-gnu/libfontconfig.so.1.6.2
 b6233000-b6234000 r--p 00036000 08:16 524280     /usr/lib/i386-linux-gnu/libfontconfig.so.1.6.2
 b6234000-b6235000 rw-p 00037000 08:16 524280     /usr/lib/i386-linux-gnu/libfontconfig.so.1.6.2
 b6235000-b627e000 r-xp 00000000 08:16 547982     /usr/lib/i386-linux-gnu/libpango-1.0.so.0.3200.5
 b627e000-b627f000 r--p 00049000 08:16 547982     /usr/lib/i386-linux-gnu/libpango-1.0.so.0.3200.5
 b627f000-b6280000 rw-p 0004a000 08:16 547982     /usr/lib/i386-linux-gnu/libpango-1.0.so.0.3200.5
 b6280000-b6292000 r-xp 00000000 08:16 528443     /usr/lib/i386-linux-gnu/libpangoft2-1.0.so.0.3200.5
 b6292000-b6293000 r--p 00011000 08:16 528443     /usr/lib/i386-linux-gnu/libpangoft2-1.0.so.0.3200.5
 b6293000-b6294000 rw-p 00012000 08:16 528443     /usr/lib/i386-linux-gnu/libpangoft2-1.0.so.0.3200.5
 b6294000-b62bb000 r-xp 00000000 08:16 528080     /usr/lib/i386-linux-gnu/libatk-bridge-2.0.so.0.0.0
 b62bb000-b62bc000 r--p 00027000 08:16 528080     /usr/lib/i386-linux-gnu/libatk-bridge-2.0.so.0.0.0
 b62bc000-b62bd000 rw-p 00028000 08:16 528080     /usr/lib/i386-linux-gnu/libatk-bridge-2.0.so.0.0.0
 b62bd000-b62db000 r-xp 00000000 08:16 527572     /usr/lib/i386-linux-gnu/libatk-1.0.so.0.20809.1
 b62db000-b62dd000 r--p 0001d000 08:16 527572     /usr/lib/i386-linux-gnu/libatk-1.0.so.0.20809.1
 b62dd000-b62de000 rw-p 0001f000 08:16 527572     /usr/lib/i386-linux-gnu/libatk-1.0.so.0.20809.1
 b62de000-b62fe000 r-xp 00000000 08:16 523739     /usr/lib/i386-linux-gnu/libgdk_pixbuf-2.0.so.0.2800.0
 b62fe000-b62ff000 ---p 00020000 08:16 523739     /usr/lib/i386-linux-gnu/libgdk_pixbuf-2.0.so.0.2800.0
 b62ff000-b6300000 r--p 00020000 08:16 523739     /usr/lib/i386-linux-gnu/libgdk_pixbuf-2.0.so.0.2800.0
 b6300000-b6301000 rw-p 00021000 08:16 523739     /usr/lib/i386-linux-gnu/libgdk_pixbuf-2.0.so.0.2800.0
 b6301000-b6414000 r-xp 00000000 08:16 524707     /usr/lib/i386-linux-gnu/libcairo.so.2.11200.14
 b6414000-b6416000 r--p 00113000 08:16 524707     /usr/lib/i386-linux-gnu/libcairo.so.2.11200.14
 b6416000-b6417000 rw-p 00115000 08:16 524707     /usr/lib/i386-linux-gnu/libcairo.so.2.11200.14
 b6417000-b6418000 rw-p 00000000 00:00 0 
 b6418000-b641d000 r-xp 00000000 08:16 528082     /usr/lib/i386-linux-gnu/libcairo-gobject.so.2.11200.14
 b641d000-b641e000 r--p 00005000 08:16 528082     /usr/lib/i386-linux-gnu/libcairo-gobject.so.2.11200.14
 b641e000-b641f000 rw-p 00006000 08:16 528082     /usr/lib/i386-linux-gnu/libcairo-gobject.so.2.11200.14
 b641f000-b6424000 r-xp 00000000 08:16 528025     /usr/lib/i386-linux-gnu/libXfixes.so.3.1.0
 b6424000-b6425000 r--p 00004000 08:16 528025     /usr/lib/i386-linux-gnu/libXfixes.so.3.1.0
 b6425000-b6426000 rw-p 00005000 08:16 528025     /usr/lib/i386-linux-gnu/libXfixes.so.3.1.0
 b6426000-b6434000 r-xp 00000000 08:16 528144     /usr/lib/i386-linux-gnu/libXi.so.6.1.0
 b6434000-b6435000 r--p 0000d000 08:16 528144     /usr/lib/i386-linux-gnu/libXi.so.6.1.0
 b6435000-b6436000 rw-p 0000e000 08:16 528144     /usr/lib/i386-linux-gnu/libXi.so.6.1.0
 b6436000-b6568000 r-xp 00000000 08:16 524693     /usr/lib/i386-linux-gnu/libX11.so.6.3.0
 b6568000-b6569000 r--p 00132000 08:16 524693     /usr/lib/i386-linux-gnu/libX11.so.6.3.0
 b6569000-b656c000 rw-p 00133000 08:16 524693     /usr/lib/i386-linux-gnu/libX11.so.6.3.0
 b656c000-b6577000 r-xp 00000000 08:16 547981     /usr/lib/i386-linux-gnu/libpangocairo-1.0.so.0.3200.5
 b6577000-b6578000 r--p 0000a000 08:16 547981     /usr/lib/i386-linux-gnu/libpangocairo-1.0.so.0.3200.5
 b6578000-b6579000 rw-p 0000b000 08:16 547981     /usr/lib/i386-linux-gnu/libpangocairo-1.0.so.0.3200.5
 b6579000-b6601000 r-xp 00000000 08:16 547239     /usr/lib/i386-linux-gnu/libgdk-3.so.0.600.4
 b6601000-b6602000 ---p 00088000 08:16 547239     /usr/lib/i386-linux-gnu/libgdk-3.so.0.600.4
 b6602000-b6604000 r--p 00088000 08:16 547239     /usr/lib/i386-linux-gnu/libgdk-3.so.0.600.4
 b6604000-b6605000 rw-p 0008a000 08:16 547239     /usr/lib/i386-linux-gnu/libgdk-3.so.0.600.4
 b6605000-b6aed000 r-xp 00000000 08:16 547240     /usr/lib/i386-linux-gnu/libgtk-3.so.0.600.4
 b6aed000-b6af2000 r--p 004e7000 08:16 547240     /usr/lib/i386-linux-gnu/libgtk-3.so.0.600.4
 b6af2000-b6af5000 rw-p 004ec000 08:16 547240     /usr/lib/i386-linux-gnu/libgtk-3.so.0.600.4
 b6af5000-b6af6000 rw-p 00000000 00:00 0 
 b6af8000-b6b0a000 r-xp 00000000 08:16 524095     /usr/lib/i386-linux-gnu/gtk-3.0/modules/liboverlay-scrollbar.so
 b6b0a000-b6b0b000 r--p 00011000 08:16 524095     /usr/lib/i386-linux-gnu/gtk-3.0/modules/liboverlay-scrollbar.so
 b6b0b000-b6b0c000 rw-p 00012000 08:16 524095     /usr/lib/i386-linux-gnu/gtk-3.0/modules/liboverlay-scrollbar.so
 b6b0c000-b6bcc000 rw-p 00000000 00:00 0 
 b6bcc000-b6bdc000 r--p 00000000 08:16 537050     /usr/lib/girepository-1.0/Atk-1.0.typelib
 b6bdc000-b6be0000 r--p 00000000 08:16 537051     /usr/lib/girepository-1.0/GdkPixbuf-2.0.typelib
 b6be0000-b6c2b000 r--p 00000000 08:16 524724     /usr/lib/girepository-1.0/Gio-2.0.typelib
 b6c2b000-b6c55000 r--p 00000000 08:16 524727     /usr/lib/girepository-1.0/GLib-2.0.typelib
 b6c55000-b6c63000 r--p 00000000 08:16 524726     /usr/lib/girepository-1.0/GObject-2.0.typelib
 b6c63000-b6c97000 r--p 00000000 08:16 527478     /usr/lib/girepository-1.0/Gdk-3.0.typelib
 b6c97000-b6d23000 r--p 00000000 08:16 527479     /usr/lib/girepository-1.0/Gtk-3.0.typelib
 b6d23000-b6d63000 rw-p 00000000 00:00 0 
 b6d74000-b6d76000 r-xp 00000000 08:16 547511     /usr/lib/python3.3/lib-dynload/_bz2.cpython-33m-i386-linux-gnu.so
 b6d76000-b6d77000 r--p 00001000 08:16 547511     /usr/lib/python3.3/lib-dynload/_bz2.cpython-33m-i386-linux-gnu.so
 b6d77000-b6d78000 rw-p 00002000 08:16 547511     /usr/lib/python3.3/lib-dynload/_bz2.cpython-33m-i386-linux-gnu.so
 b6d78000-b6d7c000 r-xp 00000000 08:16 530228     /usr/lib/i386-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-png.so
 b6d7c000-b6d7d000 r--p 00003000 08:16 530228     /usr/lib/i386-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-png.so
 b6d7d000-b6d7e000 rw-p 00004000 08:16 530228     /usr/lib/i386-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-png.so
 b6d7e000-b6d8b000 r-xp 00000000 08:16 547492     /usr/lib/python3.3/lib-dynload/_ssl.cpython-33m-i386-linux-gnu.so
 b6d8b000-b6d8c000 r--p 0000c000 08:16 547492     /usr/lib/python3.3/lib-dynload/_ssl.cpython-33m-i386-linux-gnu.so
 b6d8c000-b6d8f000 rw-p 0000d000 08:16 547492     /usr/lib/python3.3/lib-dynload/_ssl.cpython-33m-i386-linux-gnu.so
 b6d8f000-b6d92000 r-xp 00000000 08:16 547507     /usr/lib/python3.3/lib-dynload/_hashlib.cpython-33m-i386-linux-gnu.so
 b6d92000-b6d93000 r--p 00003000 08:16 547507     /usr/lib/python3.3/lib-dynload/_hashlib.cpython-33m-i386-linux-gnu.so
 b6d93000-b6d94000 rw-p 00004000 08:16 547507     /usr/lib/python3.3/lib-dynload/_hashlib.cpython-33m-i386-linux-gnu.so
 b6d94000-b6dd4000 rw-p 00000000 00:00 0 
 b6dd4000-b6df2000 r-xp 00000000 08:16 785221     /usr/lib/python3/dist-packages/gi/_gobject/_gobject.cpython-33m-i386-linux-gnu.so
 b6df2000-b6df3000 r--p 0001d000 08:16 785221     /usr/lib/python3/dist-packages/gi/_gobject/_gobject.cpython-33m-i386-linux-gnu.so
 b6df3000-b6df5000 rw-p 0001e000 08:16 785221     /usr/lib/python3/dist-packages/gi/_gobject/_gobject.cpython-33m-i386-linux-gnu.so
 b6df5000-b6e08000 r-xp 00000000 08:16 1191254    /lib/i386-linux-gnu/libresolv-2.17.so
 b6e08000-b6e09000 r--p 00013000 08:16 1191254    /lib/i386-linux-gnu/libresolv-2.17.so
 b6e09000-b6e0a000 rw-p 00014000 08:16 1191254    /lib/i386-linux-gnu/libresolv-2.17.so
 b6e0a000-b6e0c000 rw-p 00000000 00:00 0 
 b6e0c000-b6e29000 r-xp 00000000 08:16 1178145    /lib/i386-linux-gnu/libselinux.so.1
 b6e29000-b6e2a000 r--p 0001c000 08:16 1178145    /lib/i386-linux-gnu/libselinux.so.1
 b6e2a000-b6e2b000 rw-p 0001d000 08:16 1178145    /lib/i386-linux-gnu/libselinux.so.1
 b6e2b000-b6e6a000 r-xp 00000000 08:16 1177438    /lib/i386-linux-gnu/libpcre.so.3.13.1
 b6e6a000-b6e6b000 r--p 0003f000 08:16 1177438    /lib/i386-linux-gnu/libpcre.so.3.13.1
 b6e6b000-b6e6c000 rw-p 00040000 08:16 1177438    /lib/i386-linux-gnu/libpcre.so.3.13.1
 b6e6c000-b6e71000 r-xp 00000000 08:16 523653     /usr/lib/i386-linux-gnu/libffi.so.6.0.1
 b6e71000-b6e72000 r--p 00005000 08:16 523653     /usr/lib/i386-linux-gnu/libffi.so.6.0.1
 b6e72000-b6e73000 rw-p 00006000 08:16 523653     /usr/lib/i386-linux-gnu/libffi.so.6.0.1
 b6e73000-b6fd3000 r-xp 00000000 08:16 524332     /usr/lib/i386-linux-gnu/libgio-2.0.so.0.3600.0
 b6fd3000-b6fd5000 r--p 00160000 08:16 524332     /usr/lib/i386-linux-gnu/libgio-2.0.so.0.3600.0
 b6fd5000-b6fd6000 rw-p 00162000 08:16 524332     /usr/lib/i386-linux-gnu/libgio-2.0.so.0.3600.0
 b6fd6000-b6fd7000 rw-p 00000000 00:00 0 
 b6fd7000-b70d6000 r-xp 00000000 08:16 1181541    /lib/i386-linux-gnu/libglib-2.0.so.0.3600.0
 b70d6000-b70d7000 r--p 000fe000 08:16 1181541    /lib/i386-linux-gnu/libglib-2.0.so.0.3600.0
 b70d7000-b70d8000 rw-p 000ff000 08:16 1181541    /lib/i386-linux-gnu/libglib-2.0.so.0.3600.0
 b70d8000-b7126000 r-xp 00000000 08:16 528173     /usr/lib/i386-linux-gnu/libgobject-2.0.so.0.3600.0
 b7126000-b7127000 r--p 0004d000 08:16 528173     /usr/lib/i386-linux-gnu/libgobject-2.0.so.0.3600.0
 b7127000-b7128000 rw-p 0004e000 08:16 528173     /usr/lib/i386-linux-gnu/libgobject-2.0.so.0.3600.0
 b7128000-b715d000 r-xp 00000000 08:16 524710     /usr/lib/libgirepository-1.0.so.1.0.0
 b715d000-b715e000 r--p 00034000 08:16 524710     /usr/lib/libgirepository-1.0.so.1.0.0
 b715e000-b715f000 rw-p 00035000 08:16 524710     /usr/lib/libgirepository-1.0.so.1.0.0
 b715f000-b7160000 rwxp 00000000 00:00 0 
 b7160000-b7161000 r--s 00000000 00:14 19965      /run/user/amiralex/dconf/user (deleted)
 b7161000-b716e000 r--p 00000000 08:16 537053     /usr/lib/girepository-1.0/Pango-1.0.typelib
 b716e000-b7173000 r-xp 00000000 08:16 785880     /usr/lib/python3/dist-packages/gi/_glib/_glib.cpython-33m-i386-linux-gnu.so
 b7173000-b7174000 r--p 00004000 08:16 785880     /usr/lib/python3/dist-packages/gi/_glib/_glib.cpython-33m-i386-linux-gnu.so
 b7174000-b7175000 rw-p 00005000 08:16 785880     /usr/lib/python3/dist-packages/gi/_glib/_glib.cpython-33m-i386-linux-gnu.so
 b7175000-b7197000 r-xp 00000000 08:16 657129     /usr/lib/python3/dist-packages/gi/_gi.cpython-33m-i386-linux-gnu.so
 b7197000-b7198000 r--p 00021000 08:16 657129     /usr/lib/python3/dist-packages/gi/_gi.cpython-33m-i386-linux-gnu.so
 b7198000-b719b000 rw-p 00022000 08:16 657129     /usr/lib/python3/dist-packages/gi/_gi.cpython-33m-i386-linux-gnu.so
 b719b000-b731b000 rw-p 00000000 00:00 0 
 b731b000-b751b000 r--p 00000000 08:16 523394     /usr/lib/locale/locale-archive
 b751b000-b751c000 rw-p 00000000 00:00 0 
 b751c000-b755d000 r-xp 00000000 08:16 1178224    /lib/i386-linux-gnu/libm-2.17.so
 b755d000-b755e000 r--p 00040000 08:16 1178224    /lib/i386-linux-gnu/libm-2.17.so
 b755e000-b755f000 rw-p 00041000 08:16 1178224    /lib/i386-linux-gnu/libm-2.17.so
 b755f000-b7560000 rw-p 00000000 00:00 0 
 b7560000-b770d000 r-xp 00000000 08:16 1191243    /lib/i386-linux-gnu/libc-2.17.so
 b770d000-b770f000 r--p 001ad000 08:16 1191243    /lib/i386-linux-gnu/libc-2.17.so
 b770f000-b7710000 rw-p 001af000 08:16 1191243    /lib/i386-linux-gnu/libc-2.17.so
 b7710000-b7713000 rw-p 00000000 00:00 0 
 b7713000-b772a000 r-xp 00000000 08:16 1178058    /lib/i386-linux-gnu/libz.so.1.2.7
 b772a000-b772b000 r--p 00016000 08:16 1178058    /lib/i386-linux-gnu/libz.so.1.2.7
 b772b000-b772c000 rw-p 00017000 08:16 1178058    /lib/i386-linux-gnu/libz.so.1.2.7
 b772c000-b7751000 r-xp 00000000 08:16 1178050    /lib/i386-linux-gnu/libexpat.so.1.6.0
 b7751000-b7753000 r--p 00025000 08:16 1178050    /lib/i386-linux-gnu/libexpat.so.1.6.0
 b7753000-b7754000 rw-p 00027000 08:16 1178050    /lib/i386-linux-gnu/libexpat.so.1.6.0
 b7754000-b775b000 r-xp 00000000 08:16 1178220    /lib/i386-linux-gnu/librt-2.17.so
 b775b000-b775c000 r--p 00006000 08:16 1178220    /lib/i386-linux-gnu/librt-2.17.so
 b775c000-b775d000 rw-p 00007000 08:16 1178220    /lib/i386-linux-gnu/librt-2.17.so
 b775d000-b775f000 r-xp 00000000 08:16 1191255    /lib/i386-linux-gnu/libutil-2.17.so
 b775f000-b7760000 r--p 00001000 08:16 1191255    /lib/i386-linux-gnu/libutil-2.17.so
 b7760000-b7761000 rw-p 00002000 08:16 1191255    /lib/i386-linux-gnu/libutil-2.17.so
 b7761000-b7762000 rw-p 00000000 00:00 0 
 b7762000-b7765000 r-xp 00000000 08:16 1191252    /lib/i386-linux-gnu/libdl-2.17.so
 b7765000-b7766000 r--p 00002000 08:16 1191252    /lib/i386-linux-gnu/libdl-2.17.so
 b7766000-b7767000 rw-p 00003000 08:16 1191252    /lib/i386-linux-gnu/libdl-2.17.so
 b7767000-b777e000 r-xp 00000000 08:16 1191247    /lib/i386-linux-gnu/libpthread-2.17.so
 b777e000-b777f000 r--p 00016000 08:16 1191247    /lib/i386-linux-gnu/libpthread-2.17.so
 b777f000-b7780000 rw-p 00017000 08:16 1191247    /lib/i386-linux-gnu/libpthread-2.17.so
 b7780000-b7782000 rw-p 00000000 00:00 0 
 b7782000-b7783000 r--p 00000000 08:16 1062824    /usr/share/locale-langpack/en/LC_MESSAGES/gtk30.mo
 b7783000-b7784000 r--p 00000000 08:16 524725     /usr/lib/girepository-1.0/GModule-2.0.typelib
 b7784000-b7785000 r--p 00000000 08:16 524715     /usr/lib/girepository-1.0/cairo-1.0.typelib
 b7785000-b7786000 r--p 00000000 08:16 524718     /usr/lib/girepository-1.0/xlib-2.0.typelib
 b7786000-b7789000 r-xp 00000000 08:16 524330     /usr/lib/i386-linux-gnu/libgmodule-2.0.so.0.3600.0
 b7789000-b778a000 r--p 00002000 08:16 524330     /usr/lib/i386-linux-gnu/libgmodule-2.0.so.0.3600.0
 b778a000-b778b000 rw-p 00003000 08:16 524330     /usr/lib/i386-linux-gnu/libgmodule-2.0.so.0.3600.0
 b778b000-b778e000 r-xp 00000000 08:16 529487     /usr/lib/i386-linux-gnu/libpyglib-gi-2.0-python3.3.so.0.0.0
 b778e000-b778f000 r--p 00002000 08:16 529487     /usr/lib/i386-linux-gnu/libpyglib-gi-2.0-python3.3.so.0.0.0
 b778f000-b7790000 rw-p 00003000 08:16 529487     /usr/lib/i386-linux-gnu/libpyglib-gi-2.0-python3.3.so.0.0.0
 b7790000-b7797000 r--s 00000000 08:16 543590     /usr/lib/i386-linux-gnu/gconv/gconv-modules.cache
 b7797000-b7798000 r--p 002c5000 08:16 523394     /usr/lib/locale/locale-archive
 b7798000-b779a000 rw-p 00000000 00:00 0 
 b779a000-b779b000 r-xp 00000000 00:00 0          [vdso]
 b779b000-b77bb000 r-xp 00000000 08:16 1191256    /lib/i386-linux-gnu/ld-2.17.so
 b77bb000-b77bc000 r--p 0001f000 08:16 1191256    /lib/i386-linux-gnu/ld-2.17.so
 b77bc000-b77bd000 rw-p 00020000 08:16 1191256    /lib/i386-linux-gnu/ld-2.17.so
 bfb5d000-bfb7e000 rw-p 00000000 00:00 0          [stack]
ProcStatus:
 Name:	python3
 State:	R (running)
 Tgid:	3854
 Pid:	3854
 PPid:	3853
 TracerPid:	0
 Uid:	1000	1000	1000	1000
 Gid:	1000	1000	1000	1000
 FDSize:	32
 Groups:	4 24 27 30 46 107 124 1000 
 VmPeak:	  107800 kB
 VmSize:	   84156 kB
 VmLck:	       0 kB
 VmPin:	       0 kB
 VmHWM:	   42428 kB
 VmRSS:	   24644 kB
 VmData:	   29164 kB
 VmStk:	     136 kB
 VmExe:	    2636 kB
 VmLib:	   46520 kB
 VmPTE:	     120 kB
 VmSwap:	       0 kB
 Threads:	3
 SigQ:	0/7820
 SigPnd:	0000000000000000
 ShdPnd:	0000000000000000
 SigBlk:	0000000000000000
 SigIgn:	0000000001001000
 SigCgt:	0000000180000002
 CapInh:	0000000000000000
 CapPrm:	0000000000000000
 CapEff:	0000000000000000
 CapBnd:	0000001fffffffff
 Seccomp:	0
 Cpus_allowed:	3
 Cpus_allowed_list:	0-1
 Mems_allowed:	1
 Mems_allowed_list:	0
 voluntary_ctxt_switches:	102
 nonvoluntary_ctxt_switches:	243
PythonArgs: ['/usr/bin/update-manager', '--no-update']
Traceback:
 Traceback (most recent call last):
   File "/usr/bin/update-manager", line 114, in <module>
     app = UpdateManager(data_dir, options)
   File "/usr/lib/python3/dist-packages/UpdateManager/UpdateManager.py", line 111, in __init__
     self.options and self.options.use_proposed)
   File "/usr/lib/python3/dist-packages/UpdateManager/MetaReleaseGObject.py", line 44, in __init__
     MetaReleaseCore.__init__(self, useDevelopmentRelease, useProposed)
   File "/usr/lib/python3/dist-packages/UpdateManager/Core/MetaRelease.py", line 90, in __init__
     self.flavor_name = get_ubuntu_flavor_name()
   File "/usr/lib/python3/dist-packages/UpdateManager/Core/utils.py", line 447, in get_ubuntu_flavor_name
     pkg = get_ubuntu_flavor_package(cache=cache)
   File "/usr/lib/python3/dist-packages/UpdateManager/Core/utils.py", line 437, in get_ubuntu_flavor_package
     cache = apt.Cache()
   File "/usr/lib/python3/dist-packages/apt/cache.py", line 105, in __init__
     self.open(progress)
   File "/usr/lib/python3/dist-packages/apt/cache.py", line 150, in open
     self._cache = apt_pkg.Cache(progress)
 SystemError: E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/eg.archive.ubuntu.com_ubuntu_dists_raring_multiverse_i18n_Translation-en, E:The package lists or status file could not be parsed or opened.
UserGroups: adm cdrom dip lpadmin plugdev sambashare sudo

---

### Post by obernhardt on 2014-03-27
Same problem.  Googled for it.  Appear this page as solved.  Solved??

---

### Post by ibjsb4 on 2014-03-27
What same problem?  The package lists or status file could not be parsed or opened?

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=The+package+lists+or+status+file+could+not+be+parsed+or+opened.&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=The+package+lists+or+status+file+could+not+be+parsed+or+opened.&sa=Search&cof=FORID:9)

---

