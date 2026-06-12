---
title: "stack smashing detected"
date: 2014-06-11
forum: Packaging and Compiling Programs
---

### Post by Harsh_Parikh on 2014-06-11
[RIGHT][INDENT]
[/INDENT]
[/RIGHT]
Hey,I have written a c program in gedit and also compile it with gcc compiler but when i run it and enter any big value,the program automatically terminates and show error :

*** stack smashing detected ***: ./b2d terminated
======= Backtrace: =========
/lib/i386-linux-gnu/libc.so.6(__fortify_fail+0x50)[0x323df0]
/lib/i386-linux-gnu/libc.so.6(+0xe5d9a)[0x323d9a]
./b2d[0x8048913]
/lib/i386-linux-gnu/libc.so.6(__libc_start_main+0xe7)[0x254e37]
./b2d[0x80484b1]
======= Memory map: ========
0023e000-00398000 r-xp 00000000 08:05 7078721    /lib/i386-linux-gnu/libc-2.13.so
00398000-00399000 ---p 0015a000 08:05 7078721    /lib/i386-linux-gnu/libc-2.13.so
00399000-0039b000 r--p 0015a000 08:05 7078721    /lib/i386-linux-gnu/libc-2.13.so
0039b000-0039c000 rw-p 0015c000 08:05 7078721    /lib/i386-linux-gnu/libc-2.13.so
0039c000-0039f000 rw-p 00000000 00:00 0
003c2000-003dc000 r-xp 00000000 08:05 7078749    /lib/i386-linux-gnu/libgcc_s.so.1
003dc000-003dd000 r--p 00019000 08:05 7078749    /lib/i386-linux-gnu/libgcc_s.so.1
003dd000-003de000 rw-p 0001a000 08:05 7078749    /lib/i386-linux-gnu/libgcc_s.so.1
00822000-0083e000 r-xp 00000000 08:05 7078708    /lib/i386-linux-gnu/ld-2.13.so
0083e000-0083f000 r--p 0001b000 08:05 7078708    /lib/i386-linux-gnu/ld-2.13.so
0083f000-00840000 rw-p 0001c000 08:05 7078708    /lib/i386-linux-gnu/ld-2.13.so
00a92000-00a93000 r-xp 00000000 00:00 0          [vdso]
08048000-08049000 r-xp 00000000 08:05 7084094    /home/hparikh/data1/Programmes/b2d
08049000-0804a000 r--p 00000000 08:05 7084094    /home/hparikh/data1/Programmes/b2d
0804a000-0804b000 rw-p 00001000 08:05 7084094    /home/hparikh/data1/Programmes/b2d
09906000-09927000 rw-p 00000000 00:00 0          [heap]
b7770000-b7771000 rw-p 00000000 00:00 0
b777d000-b7781000 rw-p 00000000 00:00 0
bfd4d000-bfd6e000 rw-p 00000000 00:00 0          [stack]
Aborted

If there anyone,who can help me....please help....

---

