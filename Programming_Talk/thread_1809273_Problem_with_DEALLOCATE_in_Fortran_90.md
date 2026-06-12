---
title: "Problem with DEALLOCATE in Fortran 90"
date: 2011-07-21
forum: Programming Talk
---

### Post by highflie on 2011-07-21
Hi all,
I ran a F90 code and there was a runtime error while performing the DEALLOCATE Step. The error looked like this.

[/B]

*** glibc detected *** ./a.out: free(): invalid next size (normal): 0x094138a8 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(+0x6b591)[0x20c591]
/lib/tls/i686/cmov/libc.so.6(+0x6cde8)[0x20dde8]
/lib/tls/i686/cmov/libc.so.6(cfree+0x6d)[0x210ecd]
./a.out[0x805ff3c]
./a.out[0x804ced0]
./a.out[0x804c410]
./a.out[0x8049cb1]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe6)[0x1b7bd6]
./a.out[0x8049bc1]
======= Memory map: ========
00110000-00112000 r-xp 00000000 08:07 2737133    /lib/tls/i686/cmov/libdl-2.11.1.so
00112000-00113000 r-xp 00001000 08:07 2737133    /lib/tls/i686/cmov/libdl-2.11.1.so
00113000-00114000 rwxp 00002000 08:07 2737133    /lib/tls/i686/cmov/libdl-2.11.1.so
00184000-0019f000 r-xp 00000000 08:07 2687122    /lib/ld-2.11.1.so
0019f000-001a0000 r-xp 0001a000 08:07 2687122    /lib/ld-2.11.1.so
001a0000-001a1000 rwxp 0001b000 08:07 2687122    /lib/ld-2.11.1.so
001a1000-002f4000 r-xp 00000000 08:07 2737116    /lib/tls/i686/cmov/libc-2.11.1.so
002f4000-002f5000 ---p 00153000 08:07 2737116    /lib/tls/i686/cmov/libc-2.11.1.so
002f5000-002f7000 r-xp 00153000 08:07 2737116    /lib/tls/i686/cmov/libc-2.11.1.so
002f7000-002f8000 rwxp 00155000 08:07 2737116    /lib/tls/i686/cmov/libc-2.11.1.so
002f8000-002fb000 rwxp 00000000 00:00 0 
00320000-00321000 rwxp 00000000 00:00 0 
00387000-003a4000 r-xp 00000000 08:07 2687059    /lib/libgcc_s.so.1
003a4000-003a5000 r-xp 0001c000 08:07 2687059    /lib/libgcc_s.so.1
003a5000-003a6000 rwxp 0001d000 08:07 2687059    /lib/libgcc_s.so.1
005e5000-00609000 r-xp 00000000 08:07 2737194    /lib/tls/i686/cmov/libm-2.11.1.so
00609000-0060a000 r-xp 00023000 08:07 2737194    /lib/tls/i686/cmov/libm-2.11.1.so
0060a000-0060b000 rwxp 00024000 08:07 2737194    /lib/tls/i686/cmov/libm-2.11.1.so
0060b000-008a1000 rwxp 00000000 00:00 0 
008a1000-008a2000 r-xp 00000000 00:00 0          [vdso]
00904000-00a10000 rwxp 00000000 00:00 0 
00c40000-00c41000 rwxp 00000000 00:00 0 
00f02000-05915000 rwxp 00000000 00:00 0 
08048000-080b9000 r-xp 00000000 08:05 288        /media/Learn/St-Tet-F Dy-Tet/a.out
080b9000-080bd000 rwxp 00071000 08:05 288        /media/Learn/St-Tet-F Dy-Tet/a.out
080bd000-080c1000 rwxp 00000000 00:00 0 
0940a000-0942b000 rwxp 00000000 00:00 0          [heap]
1c200000-1c221000 rwxp 00000000 00:00 0 
1c221000-1c300000 ---p 00000000 00:00 0 
1c3f4000-b78e2000 rwxp 00000000 00:00 0 
bfbe1000-bfbf6000 rwxp 00000000 00:00 0          [stack]
Aborted
[/B]

Just for clarification, there was no error while compiling. This is a run-time error.

Can anyone tell me why this problem is happening?

Thanks in Advance.

---

