---
title: "Posix Timers source code"
date: 2008-01-24
forum: Packaging and Compiling Programs
---

### Post by Bob beck on 2008-01-24
Hi,

I am developing an application that uses the posix clock and timers.
( clock_settime, timer_create, timer_settime )
My host development system is a Dell laptop with gutsy ubuntu.
I am using gcc-3.2.2 since this is the version of the compiler supported by the target board.

When linking my program I found out that I needed to link
librt.so. This causes a problem since librt.so was compiled
using gcc-4.x.x. 

Where can I find the source code for librt so I can rebuild it 
using gcc-3.2.2?

If this is not a good approach, let me know of a better
one.

Thanks,
Bob Beck

---

