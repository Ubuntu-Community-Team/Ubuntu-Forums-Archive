---
title: "Program Run Problem..Please give some suggestions"
date: 2008-09-05
forum: New to Ubuntu
---

### Post by u_kuser250 on 2008-09-05
I am trying to run a Network simulator software where I get the following error any suggestions would be great.

error:
###############################################################
*** glibc detected *** ../ns: realloc(): invalid next size: 0x0864b740 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7caf18a]
/lib/tls/i686/cmov/libc.so.6(realloc+0xfe)[0xb7cb108e]
../ns(TclpRealloc+0x24)[0x84c4524]
../ns(Tcl_Realloc+0x2c)[0x844c91c]
../ns(Tcl_SetObjLength+0x7a)[0x84a4bda]
../ns(TclpNativeJoinPath+0xa8)[0x8478ec8]
../ns(Tcl_FSJoinPath+0x367)[0x848bd67]
../ns(Tcl_JoinPath+0x68)[0x8478c48]
../ns(TclpInitLibraryPath+0x6ad)[0x84b8fed]
../ns[0x8469d1a]
../ns(Tcl_FindExecutable+0x9c)[0x8469e7c]
../ns(Tcl_Main+0x43)[0x8492293]
../ns(nslibmain+0x20)[0x8439b1a]
../ns(main+0x22)[0x8439b76]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc)[0xb7c5bebc]
../ns(__gxx_personality_v0+0x33d)[0x81bf731]
======= Memory map: ========
08048000-0859c000 r-xp 00000000 08:04 1346257    /home/pavan/Blueware-new/ns-allinone-2.33/ns-2.33/ns
0859c000-08638000 rw-p 00553000 08:04 1346257    /home/pavan/Blueware-new/ns-allinone-2.33/ns-2.33/ns
08638000-08664000 rw-p 08638000 00:00 0          [heap]
b7b00000-b7b21000 rw-p b7b00000 00:00 0
b7b21000-b7c00000 ---p b7b21000 00:00 0
b7c3c000-b7c3d000 rw-p b7c3c000 00:00 0
b7c3d000-b7c41000 r-xp 00000000 08:04 4376221    /usr/lib/libXdmcp.so.6.0.0
b7c41000-b7c42000 rw-p 00003000 08:04 4376221    /usr/lib/libXdmcp.so.6.0.0
b7c42000-b7c44000 r-xp 00000000 08:04 4376210    /usr/lib/libXau.so.6.0.0
b7c44000-b7c45000 rw-p 00001000 08:04 4376210    /usr/lib/libXau.so.6.0.0
b7c45000-b7c46000 rw-p b7c45000 00:00 0
b7c46000-b7d81000 r-xp 00000000 08:04 1117407    /lib/tls/i686/cmov/libc-2.5.so
b7d81000-b7d82000 r--p 0013b000 08:04 1117407    /lib/tls/i686/cmov/libc-2.5.so
b7d82000-b7d84000 rw-p 0013c000 08:04 1117407    /lib/tls/i686/cmov/libc-2.5.so
b7d84000-b7d87000 rw-p b7d84000 00:00 0
b7d87000-b7d92000 r-xp 00000000 08:04 1114174    /lib/libgcc_s.so.1
b7d92000-b7d93000 rw-p 0000a000 08:04 1114174    /lib/libgcc_s.so.1
b7d93000-b7e72000 r-xp 00000000 08:04 4377114    /usr/lib/libstdc++.so.6.0.8
b7e72000-b7e75000 r--p 000de000 08:04 4377114    /usr/lib/libstdc++.so.6.0.8
b7e75000-b7e77000 rw-p 000e1000 08:04 4377114    /usr/lib/libstdc++.so.6.0.8
b7e77000-b7e7d000 rw-p b7e77000 00:00 0
b7e7d000-b7ea2000 r-xp 00000000 08:04 1117415    /lib/tls/i686/cmov/libm-2.5.so
b7ea2000-b7ea4000 rw-p 00024000 08:04 1117415    /lib/tls/i686/cmov/libm-2.5.so
b7ea4000-b7ea6000 r-xp 00000000 08:04 1117413    /lib/tls/i686/cmov/libdl-2.5.so
b7ea6000-b7ea8000 rw-p 00001000 08:04 1117413    /lib/tls/i686/cmov/libdl-2.5.so
b7ea8000-b7ebb000 r-xp 00000000 08:04 1117418    /lib/tls/i686/cmov/libnsl-2.5.so
b7ebb000-b7ebd000 rw-p 00012000 08:04 1117418    /lib/tls/i686/cmov/libnsl-2.5.so
b7ebd000-b7ec0000 rw-p b7ebd000 00:00 0
b7ec0000-b7fad000 r-xp 00000000 08:04 4376206    /usr/lib/libX11.so.6.2.0
b7fad000-b7fb1000 rw-p 000ed000 08:04 4376206    /usr/lib/libX11.so.6.2.0
b7fb1000-b7fbe000 r-xp 00000000 08:04 4376223    /usr/lib/libXext.so.6.4.0
b7fbe000-b7fbf000 rw-p 0000d000 08:04 4376223    /usr/lib/libXext.so.6.4.0
b7fd1000-b7fd3000 rw-p b7fd1000 00:00 0
b7fd3000-b7fec000 r-xp 00000000 08:04 1114133    /lib/ld-2.5.so
b7fec000-b7fee000 rw-p 00019000 08:04 1114133    /lib/ld-2.5.so
bfd18000-bfd2d000 rw-p bfd18000 00:00 0          [stack]
ffffe000-fffff000 r-xp 00000000 00:00 0          [vdso]
Aborted (core dumped)



Thanks

---

### Post by Pro-reason on 2008-09-05
Could you perhaps give more information?

---

### Post by MPanda on 2010-12-19
Hello all.  

I have installed NS-2 in a new Dell Desktop ***puter. I substitute windows with Ubuntu 10.10 and then succesfully installed NS-2. However, when I try to run a simulation which I previously run with good results in another ***puter, i got the next error message:

pandita@pandita-Inspiron-570:~/ns-allinone-2.34/ns-2.34/tcl$ ns
*** glibc detected *** ns: realloc(): invalid next size: 0x08a6a368 ***

also this lines:

```
======= Backtrace: =========
/lib/libc.so.6(+0x6c501)[0xb73f3501]
/lib/libc.so.6(+0x71c6d)[0xb73f8c6d]
/lib/libc.so.6(realloc+0xe3)[0xb73f8f53]
ns(TclpRealloc+0x24)[0x8473474]
ns(Tcl_Realloc+0x29)[0x83f7da9]
ns(Tcl_SetObjLength+0x7a)[0x845284a]
ns(TclpNativeJoinPath+0xb5)[0x84274f5]
ns(Tcl_FSJoinPath+0x3d5)[0x8438cc5]
ns(Tcl_JoinPath+0x6c)[0x8425c9c]
ns(TclpInitLibraryPath+0x755)[0x84676a5]
ns[0x84161ba]
ns(Tcl_FindExecutable+0x9c)[0x841631c]
ns(Tcl_Main+0x43)[0x843f5a3]
ns(nslibmain+0x20)[0x83e7118]
ns(main+0x1b)[0x83e728b]
/lib/libc.so.6(__libc_start_main+0xe7)[0xb739dce7]
ns[0x819c811]
======= Memory map: ========
08048000-08597000 r-xp 00000000 08:01 14293879   /usr/local/bin/ns
08597000-08598000 r--p 0054f000 08:01 14293879   /usr/local/bin/ns
08598000-08633000 rw-p 00550000 08:01 14293879   /usr/local/bin/ns
08633000-0863b000 rw-p 00000000 00:00 0
08a66000-08a87000 rw-p 00000000 00:00 0          [heap]
b7200000-b7221000 rw-p 00000000 00:00 0
b7221000-b7300000 ---p 00000000 00:00 0
b735f000-b7362000 rw-p 00000000 00:00 0
b7362000-b7366000 r-xp 00000000 08:01 13896460   /usr/lib/libXdmcp.so.6.0.0
b7366000-b7367000 r--p 00003000 08:01 13896460   /usr/lib/libXdmcp.so.6.0.0
b7367000-b7368000 rw-p 00004000 08:01 13896460   /usr/lib/libXdmcp.so.6.0.0
b7368000-b736a000 r-xp 00000000 08:01 13896449   /usr/lib/libXau.so.6.0.0
b736a000-b736b000 r--p 00001000 08:01 13896449   /usr/lib/libXau.so.6.0.0
b736b000-b736c000 rw-p 00002000 08:01 13896449   /usr/lib/libXau.so.6.0.0
b736c000-b7384000 r-xp 00000000 08:01 13897411   /usr/lib/libxcb.so.1.1.0
b7384000-b7385000 r--p 00017000 08:01 13897411   /usr/lib/libxcb.so.1.1.0
b7385000-b7386000 rw-p 00018000 08:01 13897411   /usr/lib/libxcb.so.1.1.0
b7386000-b7387000 rw-p 00000000 00:00 0
b7387000-b74de000 r-xp 00000000 08:01 42205229   /lib/libc-2.12.1.so
b74de000-b74df000 ---p 00157000 08:01 42205229   /lib/libc-2.12.1.so
b74df000-b74e1000 r--p 00157000 08:01 42205229   /lib/libc-2.12.1.so
b74e1000-b74e2000 rw-p 00159000 08:01 42205229   /lib/libc-2.12.1.so
b74e2000-b74e5000 rw-p 00000000 00:00 0
b74e5000-b74ff000 r-xp 00000000 08:01 42205263   /lib/libgcc_s.so.1
b74ff000-b7500000 r--p 00019000 08:01 42205263   /lib/libgcc_s.so.1
b7500000-b7501000 rw-p 0001a000 08:01 42205263   /lib/libgcc_s.so.1
b7501000-b75e0000 r-xp 00000000 08:01 13897301   /usr/lib/libstdc++.so.6.0.14
b75e0000-b75e4000 r--p 000de000 08:01 13897301   /usr/lib/libstdc++.so.6.0.14
b75e4000-b75e5000 rw-p 000e2000 08:01 13897301   /usr/lib/libstdc++.so.6.0.14
b75e5000-b75ec000 rw-p 00000000 00:00 0
b75ec000-b7610000 r-xp 00000000 08:01 42205278   /lib/libm-2.12.1.so
b7610000-b7611000 r--p 00023000 08:01 42205278   /lib/libm-2.12.1.so
b7611000-b7612000 rw-p 00024000 08:01 42205278   /lib/libm-2.12.1.so
b7612000-b7614000 r-xp 00000000 08:01 42205243   /lib/libdl-2.12.1.so
b7614000-b7615000 r--p 00001000 08:01 42205243   /lib/libdl-2.12.1.so
b7615000-b7616000 rw-p 00002000 08:01 42205243   /lib/libdl-2.12.1.so
b7616000-b7629000 r-xp 00000000 08:01 42205289   /lib/libnsl-2.12.1.so
b7629000-b762a000 r--p 00012000 08:01 42205289   /lib/libnsl-2.12.1.so
b762a000-b762b000 rw-p 00013000 08:01 42205289   /lib/libnsl-2.12.1.so
b762b000-b762e000 rw-p 00000000 00:00 0
b762e000-b7747000 r-xp 00000000 08:01 13896445   /usr/lib/libX11.so.6.3.0
b7747000-b7748000 r--p 00118000 08:01 13896445   /usr/lib/libX11.so.6.3.0
b7748000-b774a000 rw-p 00119000 08:01 13896445   /usr/lib/libX11.so.6.3.0
b774a000-b774b000 rw-p 00000000 00:00 0
b774b000-b7759000 r-xp 00000000 08:01 13896462   /usr/lib/libXext.so.6.4.0
b7759000-b775a000 r--p 0000d000 08:01 13896462   /usr/lib/libXext.so.6.4.0
b775a000-b775b000 rw-p 0000e000 08:01 13896462   /usr/lib/libXext.so.6.4.0
b7768000-b776a000 rw-p 00000000 00:00 0
b776a000-b776b000 r-xp 00000000 00:00 0          [vdso]
b776b000-b7787000 r-xp 00000000 08:01 42205205   /lib/ld-2.12.1.so
b7787000-b7788000 r--p 0001b000 08:01 42205205   /lib/ld-2.12.1.so
b7788000-b7789000 rw-p 0001c000 08:01 42205205   /lib/ld-2.12.1.so
bfccb000-bfcec000 rw-p 00000000 00:00 0          [stack]
Aborted
pandita@pandita-Inspiron-570:~/ns-allinone-2.34/ns-2.34/tcl$ 

```

I hope someone can help me to solve this issue.
Many thanks in advance

---

