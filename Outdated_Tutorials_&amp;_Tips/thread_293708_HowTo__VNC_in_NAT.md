---
title: "HowTo : VNC in NAT"
date: 2006-11-05
forum: Outdated Tutorials &amp; Tips
---

### Post by _Q_ on 2006-11-05
unfortunately, this isnt the full howto (it contains problems, as you will see), but i am hoping that it will be resolved so at the end it will be usefull as a real HowTo....

so, the scenario is :

Machine1 - running WinXP - has full access to internet
Machine2 - running Ubuntu Edgy - behind NAT router (which isn't accessible)

Goal : accomplish native VNC GUI connection from Machine1 to Machine2 (Machine2 as the server)

the obvious problem is - we can't connect directly to Machine2 since we can't forward the 5900 port on the router...

Solution :

First, install TightVNC on Machine1 ([http://www.tightvnc.com)](http://www.tightvnc.com)), and run Viewer in Listening Mode.

Second, go to Machine2 and install vnc
```
sudo apt-get install tightvncserver
```

now, run the server
```
vncserver
```

it should print out something like this

> user@Machine2:~$ vncserver

New 'X' desktop is Machine2:1

Starting applications specified in /home/user/.vnc/xstartup
Log file is /home/user/.vnc/Machine2:1.log

now, we need to connect to our listener on Machine1

```
vncconnect -display :1 Machine1_IP:5500
```

after this, it should work...., but i'm getting the following errror (on Machine2)

```
*** glibc detected *** Xtightvnc: free(): invalid pointer: 0x081ff704 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7df98bd]
/lib/tls/i686/cmov/libc.so.6(__libc_free+0x84)[0xb7df9a44]
Xtightvnc(ChangeWindowProperty+0x268)[0x8082ed8]
Xtightvnc(ProcChangeProperty+0x151)[0x80830e1]
Xtightvnc(Dispatch+0x129)[0x8078009]
Xtightvnc(main+0x79c)[0x8060b0c]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc)[0xb7da88cc]
Xtightvnc[0x8060051]
======= Memory map: ========
08048000-08182000 r-xp 00000000 16:01 3910736    /usr/bin/Xtightvnc
08182000-08189000 rw-p 00139000 16:01 3910736    /usr/bin/Xtightvnc
08189000-08233000 rw-p 08189000 00:00 0          [heap]
b7800000-b7821000 rw-p b7800000 00:00 0 
b7821000-b7900000 ---p b7821000 00:00 0 
b798b000-b7995000 r-xp 00000000 16:01 4693091    /lib/libgcc_s.so.1
b7995000-b7996000 rw-p 00009000 16:01 4693091    /lib/libgcc_s.so.1
b79a2000-b7a02000 rw-s 00000000 00:07 3833881    /SYSV00000000 (deleted)
b7a0d000-b7a6d000 rw-s 00000000 00:07 3801112    /SYSV00000000 (deleted)
b7a6d000-b7a82000 rw-p b7a6d000 00:00 0 
b7a89000-b7a8c000 rw-p b7a89000 00:00 0 
b7a91000-b7d93000 rw-p b7a91000 00:00 0 
b7d93000-b7ec0000 r-xp 00000000 16:01 4726366    /lib/tls/i686/cmov/libc-2.4.so
b7ec0000-b7ec2000 r--p 0012c000 16:01 4726366    /lib/tls/i686/cmov/libc-2.4.so
b7ec2000-b7ec4000 rw-p 0012e000 16:01 4726366    /lib/tls/i686/cmov/libc-2.4.so
b7ec4000-b7ec7000 rw-p b7ec4000 00:00 0 
b7ec7000-b7ee5000 r-xp 00000000 16:01 3909858    /usr/lib/libjpeg.so.62.0.0
b7ee5000-b7ee6000 rw-p 0001d000 16:01 3909858    /usr/lib/libjpeg.so.62.0.0
b7ee6000-b7ee7000 rw-p b7ee6000 00:00 0 
b7ee7000-b7ee9000 r-xp 00000000 16:01 4726372    /lib/tls/i686/cmov/libdl-2.4.so
b7ee9000-b7eeb000 rw-p 00001000 16:01 4726372    /lib/tls/i686/cmov/libdl-2.4.so
b7eeb000-b7f0f000 r-xp 00000000 16:01 4726374    /lib/tls/i686/cmov/libm-2.4.so
b7f0f000-b7f11000 rw-p 00023000 16:01 4726374    /lib/tls/i686/cmov/libm-2.4.so
b7f11000-b7f24000 r-xp 00000000 16:01 3910122    /usr/lib/libz.so.1.2.3
b7f24000-b7f25000 rw-p 00012000 16:01 3910122    /usr/lib/libz.so.1.2.3
b7f27000-b7f33000 rw-p b7f27000 00:00 0 
b7f33000-b7f34000 r-xp b7f33000 00:00 0          [vdso]
b7f34000-b7f4d000 r-xp 00000000 16:01 4693046    /lib/ld-2.4.so
b7f4d000-b7f4f000 rw-p 00018000 16:01 4693046    /lib/ld-2.4.so
bfeeb000-bff01000 rw-p bfeeb000 00:00 0          [stack]
X connection to :1.0 broken (explicit kill or server shutdown).
```

on Machine1, VNC just pops a window saying that its an unexpected connection termination...

any ideas? :S

---

