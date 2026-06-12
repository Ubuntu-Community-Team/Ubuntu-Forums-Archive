---
title: "Debug embedded Midori crash"
date: 2010-07-18
forum: Programming Talk
---

### Post by teachop on 2010-07-18
What techniques can/should I use to debug a Midori browser crashing?  My experience is "bare" embedded systems mostly, with no OS.  For the last year I have been working my way up on embedded linux applications.

The hardware is an Arm-based embedded linux board, Overo Water with omap3530 CPU.  It is running Angstrom / openEmbedded.  Midori is crashing like crazy, segmentation fault.

The linux images are downloaded - I have tried the offical Gumstix versions, Angstrom overo stable and unstable versions, and in other ways, the system is operating well.  Midori seems really nice actually.

My connections to the sytem are via a USB/Serial console, and primarily an HDMI monitor with USB keyboard and mouse.  The on-board ethernet is also working great.

The system is booting the kernel and rootfs from an SD card.

Just need some advice about if/how to get gdb working for me, or what is a better way, whatever I need to dig into this...

---

### Post by phrostbyte on 2010-07-20
Try compiling it with debug symbols enabled. Then run it through a debugger (eg: gdb). GDB usually will be able to pin-point the exact line of code that the application crashed on, as well as provide you with the contents of the stack/registers.

---

