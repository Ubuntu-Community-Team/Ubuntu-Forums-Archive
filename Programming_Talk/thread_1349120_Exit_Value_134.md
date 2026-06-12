---
title: "Exit Value 134"
date: 2009-12-07
forum: Programming Talk
---

### Post by PBT on 2009-12-07
Hey,

I've been programming C++ for ust a short while and i'm currently encountering error while programming the vector class template. It's not the one from stl but i just want to know what this sort of error would mean. I'm kind of aware it is memory related and that i cannot access through some type of memory, but what exactly? I'm a sort of newbie when it comes to memory allocation by programming software.

Thanks,
PB

It's called run failed: exit value 134
This is whats my terminal outputs
code:
*** glibc detected *** /home/patrick/NetBeansProjects/tp8/dist/Debug/GNU-Linux-x86/tp8: free(): invalid next size (fast): 0x096ee060 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0x1b0ff1]
/lib/tls/i686/cmov/libc.so.6[0x1b26f2]
/lib/tls/i686/cmov/libc.so.6(cfree+0x6d)[0x1b579d]
/usr/lib/libstdc++.so.6(_ZdlPv+0x21)[0x8616f1]
/usr/lib/libstdc++.so.6(_ZdaPv+0x1d)[0x86174d]
/home/patrick/NetBeansProjects/tp8/dist/Debug/GNU-Linux-x86/tp8[0x80489ae]
/home/patrick/NetBeansProjects/tp8/dist/Debug/GNU-Linux-x86/tp8[0x804915c]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe6)[0x15cb56]
/home/patrick/NetBeansProjects/tp8/dist/Debug/GNU-Linux-x86/tp8[0x80487c1]
======= Memory map: ========
00129000-00144000 r-xp 00000000 08:05 419763     /lib/ld-2.10.1.so
00144000-00145000 r--p 0001a000 08:05 419763     /lib/ld-2.10.1.so
00145000-00146000 rw-p 0001b000 08:05 419763     /lib/ld-2.10.1.so
00146000-00284000 r-xp 00000000 08:05 436269     /lib/tls/i686/cmov/libc-2.10.1.so
00284000-00286000 r--p 0013e000 08:05 436269     /lib/tls/i686/cmov/libc-2.10.1.so
00286000-00287000 rw-p 00140000 08:05 436269     /lib/tls/i686/cmov/libc-2.10.1.so
00287000-0028a000 rw-p 00000000 00:00 0 
0032c000-00350000 r-xp 00000000 08:05 436279     /lib/tls/i686/cmov/libm-2.10.1.so
00350000-00351000 r--p 00023000 08:05 436279     /lib/tls/i686/cmov/libm-2.10.1.so
00351000-00352000 rw-p 00024000 08:05 436279     /lib/tls/i686/cmov/libm-2.10.1.so
005ae000-005ca000 r-xp 00000000 08:05 416982     /lib/libgcc_s.so.1
005ca000-005cb000 r--p 0001b000 08:05 416982     /lib/libgcc_s.so.1
005cb000-005cc000 rw-p 0001c000 08:05 416982     /lib/libgcc_s.so.1
0065b000-0065e000 r-xp 00000000 08:05 753238     /home/patrick/.netbeans/6.7/tools/Linux-x86/bin/prof_agent.so
0065e000-0065f000 r--p 00002000 08:05 753238     /home/patrick/.netbeans/6.7/tools/Linux-x86/bin/prof_agent.so
0065f000-00660000 rw-p 00003000 08:05 753238     /home/patrick/.netbeans/6.7/tools/Linux-x86/bin/prof_agent.so
0069c000-0069e000 r-xp 00000000 08:05 436278     /lib/tls/i686/cmov/libdl-2.10.1.so
0069e000-0069f000 r--p 00001000 08:05 436278     /lib/tls/i686/cmov/libdl-2.10.1.so
0069f000-006a0000 rw-p 00002000 08:05 436278     /lib/tls/i686/cmov/libdl-2.10.1.so
007a9000-0088f000 r-xp 00000000 08:05 335388     /usr/lib/libstdc++.so.6.0.13
0088f000-00893000 r--p 000e6000 08:05 335388     /usr/lib/libstdc++.so.6.0.13
00893000-00894000 rw-p 000ea000 08:05 335388     /usr/lib/libstdc++.so.6.0.13
00894000-0089b000 rw-p 00000000 00:00 0 
00997000-0099e000 r-xp 00000000 08:05 436291     /lib/tls/i686/cmov/librt-2.10.1.so
0099e000-0099f000 r--p 00006000 08:05 436291     /lib/tls/i686/cmov/librt-2.10.1.so
0099f000-009a0000 rw-p 00007000 08:05 436291     /lib/tls/i686/cmov/librt-2.10.1.so
00b9a000-00baf000 r-xp 00000000 08:05 436289     /lib/tls/i686/cmov/libpthread-2.10.1.so
00baf000-00bb0000 r--p 00014000 08:05 436289     /lib/tls/i686/cmov/libpthread-2.10.1.so
00bb0000-00bb1000 rw-p 00015000 08:05 436289     /lib/tls/i686/cmov/libpthread-2.10.1.so
00bb1000-00bb3000 rw-p 00000000 00:00 0 
00e88000-00e89000 r-xp 00000000 00:00 0          [vdso]
08048000-0804a000 r-xp 00000000 08:05 1074921    /home/patrick/NetBeansProjects/tp8/dist/Debug/GNU-Linux-x86/tp8
0804a000-0804b000 r--p 00001000 08:05 1074921    /home/patrick/NetBeansProjects/tp8/dist/Debug/GNU-Linux-x86/tp8
0804b000-0804c000 rw-p 00002000 08:05 1074921    /home/patrick/NetBeansProjects/tp8/dist/Debug/GNU-Linux-x86/tp8
096ee000-0970f000 rw-p 00000000 00:00 0          [heap]
b7700000-b7721000 rw-p 00000000 00:00 0 
b7721000-b7800000 ---p 00000000 00:00 0 
b78d1000-b78d4000 rw-p 00000000 00:00 0 
b78eb000-b78ee000 rw-p 00000000 00:00 0 
bfd0d000-bfd22000 rw-p 00000000 00:00 0          [stack]
Aborted

---

### Post by johnl on 2009-12-07
Looks like memory corruption.  You probably wrote past the end of an array of wrote to freed memory.

---

### Post by Arndt on 2009-12-08
> **johnl said:**
> Looks like memory corruption.  You probably wrote past the end of an array of wrote to freed memory.

Exit statuses 128+n where n is a small positive number usually mean that the program crashed with signal n - in that case it's not really an exit status.

---

### Post by A_Fiachra on 2009-12-08
Fire up the debugger!

---

### Post by johnl on 2009-12-08
> **Arndt said:**
> Exit statuses 128+n where n is a small positive number usually mean that the program crashed with signal n - in that case it's not really an exit status.

Good to know.  I actually didn't even look at the exit code, just the error message :)

---

### Post by Arndt on 2009-12-08
> **johnl said:**
> Good to know.  I actually didn't even look at the exit code, just the error message :)

It's the subject of the thread, after all.

---

### Post by nvteighen on 2009-12-08
From the error message, it seems you free()'d a certain chunk of memory more than once.

---

### Post by johnl on 2009-12-08
> **Arndt said:**
> It's the subject of the thread, after all.

OK, I did *look* at the exit code; I didn't consider or investigate it's meaning. The included error message is more conducive to root causing the issue -- that's what I meant.

---

### Post by Arndt on 2009-12-09
> **johnl said:**
> OK, I did *look* at the exit code; I didn't consider or investigate it's meaning. The included error message is more conducive to root causing the issue -- that's what I meant.

Yes, that's certainly true. 6 is SIGABRT, and we already knew that the program did an abort. 7 and 11 are common, but I don't think I've ever found the difference between them useful in finding out why something goes wrong.

---

