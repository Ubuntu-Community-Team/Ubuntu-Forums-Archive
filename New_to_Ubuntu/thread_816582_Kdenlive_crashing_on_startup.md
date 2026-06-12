---
title: "Kdenlive crashing on startup"
date: 2008-06-02
forum: New to Ubuntu
---

### Post by linkmaster03 on 2008-06-02
I just installed Kdenlive, and when I try to boot for the first time, I get this:

[img]http://img110.imageshack.us/img110/2163/monjun021711ne3.png[/img]

Backtrace:

```
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread 0xb672a6c0 (LWP 31504)]
[New Thread 0xb35e1b90 (LWP 31520)]
[New Thread 0xb3de2b90 (LWP 31519)]
[New Thread 0xb514db90 (LWP 31508)]
[New Thread 0xb494cb90 (LWP 31507)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
0xb7fac410 in __kernel_vsyscall ()
#0  0xb7fac410 in __kernel_vsyscall ()
#1  0xb765299b in read () from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb68831d3 in ?? () from /usr/lib/libxcb.so.1
#3  0xb688383b in xcb_poll_for_event () from /usr/lib/libxcb.so.1
#4  0xb76afcc9 in ?? () from /usr/lib/libX11.so.6
#5  0xb76affcf in ?? () from /usr/lib/libX11.so.6
#6  0xb76b071f in _XEventsQueued () from /usr/lib/libX11.so.6
#7  0xb76999d2 in XPending () from /usr/lib/libX11.so.6
#8  0xb79eb983 in QEventLoop::processEvents () from /usr/lib/libqt-mt.so.3
#9  0xb7a61f90 in QEventLoop::enterLoop () from /usr/lib/libqt-mt.so.3
#10 0xb7a61c8e in QEventLoop::exec () from /usr/lib/libqt-mt.so.3
#11 0xb7a487df in QApplication::exec () from /usr/lib/libqt-mt.so.3
#12 0x081c5a9e in main ()

```

---

### Post by SunnyRabbiera on 2008-06-02
yes this is an error, it goes away if you turn off desktop effects.

---

### Post by linkmaster03 on 2008-06-03
How do I disable desktop effects?

---

### Post by xdavidx on 2008-06-04
right click on your desktop-> change the back of your desktop-->visual effects tab-->none

---

