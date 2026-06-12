---
title: "[SOLVED] Bigloo 3.1a does not compile on Win32 with MinGW"
date: 2008-07-28
forum: Packaging and Compiling Programs
---

### Post by LinuxRocks713 on 2008-07-28
Hi everyone:

Bigloo 3.1a does not compile on windows. Here are the configure and make logs:

./configure log: [http://1516.pastebin.com/m568adcb8](http://1516.pastebin.com/m568adcb8)
make log: [http://1516.pastebin.com/m949e905](http://1516.pastebin.com/m949e905)

The interesting thing is, though the configure program says MinGW has termio.h, it doesn't actually:

[quote=Configure Log]
termio: yes
termios: no
[/quote]

[quote=Make Log]
Clib/cports.c:48:24: termio.h: No such file or directory
Clib/cports.c: In function `sysputc_with_timeout':
Clib/cports.c:448: warning: return makes integer from pointer without a cast
Clib/cports.c: In function `bgl_password':
Clib/cports.c:2189: error: storage size of 't' isn't known
Clib/cports.c:2190: error: `tcflag_t' undeclared (first use in this function)
Clib/cports.c:2190: error: (Each undeclared identifier is reported only once
Clib/cports.c:2190: error: for each function it appears in.)
Clib/cports.c:2190: error: syntax error before "lflag"
Clib/cports.c:2197: error: `lflag' undeclared (first use in this function)
Clib/cports.c:2198: error: `ICANON' undeclared (first use in this function)
Clib/cports.c:2198: error: `ECHO' undeclared (first use in this function)
Clib/cports.c:2199: error: `VMIN' undeclared (first use in this function)
Clib/cports.c:2200: error: `VTIME' undeclared (first use in this function)
Clib/cports.c:2201: error: `TCSANOW' undeclared (first use in this function)
[/quote]

Hope someone has a solution/patch/fix for this nnaasty problem.

---

### Post by LinuxRocks713 on 2008-08-19
Solved - see [http://ubuntuforums.org/showthread.php?t=875438](http://ubuntuforums.org/showthread.php?t=875438)

---

