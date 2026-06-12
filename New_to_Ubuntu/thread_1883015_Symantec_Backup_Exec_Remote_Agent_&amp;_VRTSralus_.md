---
title: "Symantec Backup Exec Remote Agent &amp; VRTSralus on Ubuntu 11.10"
date: 2011-11-18
forum: New to Ubuntu
---

### Post by talishka on 2011-11-18
Hi guys, after the update of one of my servers to Ubuntu 11.10, i cannot run the symantec backup exec remote agent because the daemon crashes 3 segs after starting. I tried the newest version of 
VRTSralus (backupexec v13) but it didn't work.

This is the error.. 

root@rockyourbody:/opt/2011# /etc/init.d/VRTSralus.init start
Starting Symantec Backup Exec Remote Agent ......
Starting Symantec Backup Exec Remote Agent:                              [  OK  ]
root@rockyourbody:/opt/2011# *** glibc detected *** /opt/VRTSralus/bin/beremote: free(): invalid pointer: 0xb5c88d10 ***
======= Backtrace: =========
/lib/i386-linux-gnu/libc.so.6(+0x6ebc2)[0xb5c84bc2]
/lib/i386-linux-gnu/libc.so.6(+0x6f862)[0xb5c85862]
/lib/i386-linux-gnu/libc.so.6(cfree+0x6d)[0xb5c8894d]
/opt/VRTSralus/bin/libbesocket.so(_Z11freeifaddrsP7ifaddrs+0x41)[0xb62f2331]
/opt/VRTSralus/bin/libbesocket.so(_Z10getifaddrsPP7ifaddrs+0x72c)[0xb62f22c8]
/opt/VRTSralus/bin/libbesocket.so(_Z20GetAdaptersAddressesmmPvP21_IP_ADAPTER_ADDRESSESPm+0x69)[0xb62f2c19]
/opt/VRTSralus/bin/libbesocket.so(_ZN8BESocket13BENetConfigEx18RefreshInformationEPKb+0x41)[0xb62fbb49]
/opt/VRTSralus/bin/libbesocket.so(_ZN8BESocket13BENetConfigExC1Eb+0xf4)[0xb62fb9f0]
/opt/VRTSralus/bin/libbesocket.so(_ZN8BESocket13BENetConfigEx23GetNetworkConfigurationEb+0x2c)[0xb62fbf9c]
/opt/VRTSralus/bin/libbedsvx.so(_Z14VX_EnumSelfDLEP6BE_CFGP8HEAD_DLE+0x300)[0xb64d3c10]
/opt/VRTSralus/bin/libndmpcomm.so(+0x22e74)[0xb636ae74]
/opt/VRTSralus/bin/libndmpcomm.so(+0x2325d)[0xb636b25d]
/opt/VRTSralus/bin/libndmpcomm.so(_Z20NrdsAdvertiserThreadPv+0x124)[0xb636bad0]
/opt/VRTSralus/bin/libvxACEI.so.3(_ZN18ACE_Thread_Adapter8invoke_iEv+0x52)[0xb77f09d6]
/opt/VRTSralus/bin/libvxACEI.so.3(_ZN18ACE_Thread_Adapter6invokeEv+0x61)[0xb77f0941]
/opt/VRTSralus/bin/libvxACEI.so.3(ace_thread_adapter+0xe)[0xb77b9d1a]
/lib/i386-linux-gnu/libpthread.so.0(+0x6d31)[0xb6b68d31]
/lib/i386-linux-gnu/libc.so.6(clone+0x5e)[0xb5ce80ce]
======= Memory map: ========
08048000-08092000 r-xp 00000000 fc:00 7873194    /opt/VRTSralus/bin/beremote
08092000-08095000 rw-p 0004a000 fc:00 7873194    /opt/VRTSralus/bin/beremote
08095000-08104000 rw-p 00000000 00:00 0
09a84000-09ac5000 rw-p 00000000 00:00 0          [heap]
b36ff000-b3700000 ---p 00000000 00:00 0
b3700000-b3f00000 rwxp 00000000 00:00 0
b3f00000-b3f21000 rw-p 00000000 00:00 0
b3f21000-b4000000 ---p 00000000 00:00 0
b4018000-b4019000 ---p 00000000 00:00 0
b4019000-b4819000 rwxp 00000000 00:00 0
b4819000-b481a000 ---p 00000000 00:00 0
b481a000-b501a000 rwxp 00000000 00:00 0
b501a000-b5033000 r-xp 00000000 fc:00 7873234    /opt/VRTSralus/VRTSvxms/lib/libvfutil.so
b5033000-b5035000 rw-p 00018000 fc:00 7873234    /opt/VRTSralus/VRTSvxms/lib/libvfutil.so
b5035000-b5037000 rw-p 00000000 00:00 0
b5037000-b5237000 r--p 00000000 fc:00 789954     /usr/lib/locale/locale-archive
b5237000-b524f000 r-xp 00000000 fc:00 7873206    /opt/VRTSralus/bin/libbedsedir.so
b524f000-b5253000 rw-p 00018000 fc:00 7873206    /opt/VRTSralus/bin/libbedsedir.so
b5253000-b5254000 rw-p 00000000 00:00 0
b5254000-b5331000 r-xp 00000000 fc:00 7873188    /opt/VRTSralus/bin/libvxcrypto.so
b5331000-b5343000 rw-p 000dc000 fc:00 7873188    /opt/VRTSralus/bin/libvxcrypto.so
b5343000-b5346000 rw-p 00000000 00:00 0
b5346000-b5381000 r-xp 00000000 fc:00 7873198    /opt/VRTSralus/bin/libbedsrman.so
b5381000-b5383000 rw-p 0003b000 fc:00 7873198    /opt/VRTSralus/bin/libbedsrman.so
b5383000-b53bb000 rw-p 00000000 00:00 0
b53bb000-b53bc000 ---p 00000000 00:00 0
b53bc000-b5bbc000 rwxp 00000000 00:00 0
b5bbc000-b5bc2000 r-xp 00000000 fc:00 1048592    /lib/libnss_winbind.so.2
b5bc2000-b5bc3000 r--p 00005000 fc:00 1048592    /lib/libnss_winbind.so.2
b5bc3000-b5bc4000 rw-p 00006000 fc:00 1048592    /lib/libnss_winbind.so.2
b5bc4000-b5bc9000 rw-p 00000000 00:00 0
b5bc9000-b5bd4000 r-xp 00000000 fc:00 2362415    /lib/i386-linux-gnu/libnss_files-2.13.so
b5bd4000-b5bd5000 r--p 0000a000 fc:00 2362415    /lib/i386-linux-gnu/libnss_files-2.13.so
b5bd5000-b5bd6000 rw-p 0000b000 fc:00 2362415    /lib/i386-linux-gnu/libnss_files-2.13.so
b5bd6000-b5be0000 r-xp 00000000 fc:00 2362417    /lib/i386-linux-gnu/libnss_nis-2.13.so
b5be0000-b5be1000 r--p 00009000 fc:00 2362417    /lib/i386-linux-gnu/libnss_nis-2.13.so
b5be1000-b5be2000 rw-p 0000a000 fc:00 2362417    /lib/i386-linux-gnu/libnss_nis-2.13.so
b5be2000-b5bf7000 r-xp 00000000 fc:00 2362412    /lib/i386-linux-gnu/libnsl-2.13.so
b5bf7000-b5bf8000 r--p 00015000 fc:00 2362412    /lib/i386-linux-gnu/libnsl-2.13.so
b5bf8000-b5bf9000 rw-p 00016000 fc:00 2362412    /lib/i386-linux-gnu/libnsl-2.13.so
b5bf9000-b5bfb000 rw-p 00000000 00:00 0
b5bfb000-b5c03000 r-xp 00000000 fc:00 2362413    /lib/i386-linux-gnu/libnss_compat-2.13.so
b5c03000-b5c04000 r--p 00007000 fc:00 2362413    /lib/i386-linux-gnu/libnss_compat-2.13.so
b5c04000-b5c05000 rw-p 00008000 fc:00 2362413    /lib/i386-linux-gnu/libnss_compat-2.13.so
b5c0e000-b5c12000 rw-p 00000000 00:00 0
b5c12000-b5c14000 r-xp 00000000 fc:00 2362425    /lib/i386-linux-gnu/libutil-2.13.so
b5c14000-b5c15000 r--p 00001000 fc:00 2362425    /lib/i386-linux-gnu/libutil-2.13.so
b5c15000-b5c16000 rw-p 00002000 fc:00 2362425    /lib/i386-linux-gnu/libutil-2.13.so
b5c16000-b5d8c000 r-xp 00000000 fc:00 2362406    /lib/i386-linux-gnu/libc-2.13.so
b5d8c000-b5d8e000 r--p 00176000 fc:00 2362406    /lib/i386-linux-gnu/libc-2.13.so
b5d8e000-b5d8f000 rw-p 00178000 fc:00 2362406    /lib/i386-linux-gnu/libc-2.13.so
b5d8f000-b5d93000 rw-p 00000000 00:00 0
b5d93000-b5daf000 r-xp 00000000 fc:00 2360885    /lib/i386-linux-gnu/libgcc_s.so.1
b5daf000-b5db0000 r--p 0001b000 fc:00 2360885    /lib/i386-linux-gnu/libgcc_s.so.1
b5db0000-b5db1000 rw-p 0001c000 fc:00 2360885    /lib/i386-linux-gnu/libgcc_s.so.1
b5db1000-b5dd9000 r-xp 00000000 fc:00 2362410    /lib/i386-linux-gnu/libm-2.13.so
b5dd9000-b5dda000 r--p 00028000 fc:00 2362410    /lib/i386-linux-gnu/libm-2.13.so
b5dda000-b5ddb000 rw-p 00029000 fc:00 2362410    /lib/i386-linux-gnu/libm-2.13.so
b5ddb000-b5e8b000 r-xp 00000000 fc:00 919643     /usr/lib/i386-linux-gnu/libstdc++.so.5.0.7
b5e8b000-b5e90000 rw-p 000af000 fc:00 919643     /usr/lib/i386-linux-gnu/libstdc++.so.5.0.7
b5e90000-b5e95000 rw-p 00000000 00:00 0
b5e95000-b5e98000 r-xp 00000000 fc:00 7873225    /opt/VRTSralus/bin/libsth.so
b5e98000-b5e99000 rw-p 00002000 fc:00 7873225    /opt/VRTSralus/bin/libsth.so
b5e99000-b5e9a000 r-xp 00000000 fc:00 7873224    /opt/VRTSralus/bin/libsthapi.so
b5e9a000-b5e9b000 rw-p 00000000 fc:00 7873224    /opt/VRTSralus/bin/libsthapi.so
b5e9b000-b5e9c000 rw-p 00000000 00:00 0
b5e9c000-b5eaa000 r-xp 00000000 fc:00 7873230    /opt/VRTSralus/bin/libsts.so
b5eaa000-b5eab000 rw-p 0000e000 fc:00 7873230    /opt/VRTSralus/bin/libsts.so
b5eab000-b5ead000 r-xp 00000000 fc:00 7873227    /opt/VRTSralus/bin/libstsapi.so
b5ead000-b5eae000 rw-p 00001000 fc:00 7873227    /opt/VRTSralus/bin/libstsapi.so
b5eae000-b5ed2000 r-xp 00000000 fc:00 7873208    /opt/VRTSralus/bin/libbescsicap.so
b5ed2000-b5fd1000 rw-p 00023000 fc:00 7873208    /opt/VRTSralus/bin/libbescsicap.so
b5fd1000-b622b000 r-xp 00000000 fc:00 7873209    /opt/VRTSralus/bin/libDeviceIo.so
b622b000-b6263000 rw-p 0025a000 fc:00 7873209    /opt/VRTSralus/bin/libDeviceIo.so
b6263000-b6281000 rw-p 00000000 00:00 0
b6281000-b6292000 r-xp 00000000 fc:00 7873210    /opt/VRTSralus/bin/libtapesrvr.so
b6292000-b6293000 rw-p 00010000 fc:00 7873210    /opt/VRTSralus/bin/libtapesrvr.so

Any ideas? thanks in advance!

---

### Post by armstrtw on 2011-12-05
same issue here.  no solution at this point.

---

### Post by talishka on 2011-12-06
Damn, i looked up on the symantec website and there is no reference to this error.. It looks like we're gonna have to wait for the solution a little big longer. Or... rollback the version of Ubuntu.

---

### Post by krishanr on 2011-12-14
Also having this issue, came across this thread.. which looks like its having same issue. They rolled back the kernel to 2.6 to fix, either that or wait for fix. 

[http://www.symantec.com/connect/forums/ralus-kernel-30-issues](http://www.symantec.com/connect/forums/ralus-kernel-30-issues)

---

