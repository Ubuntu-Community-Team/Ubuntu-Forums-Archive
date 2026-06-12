---
title: "Drivers on ARM architecture"
date: 2013-11-22
forum: New to Ubuntu
---

### Post by only.tiki on 2013-11-22
Hello, I am new to the forum :) yesterday I just installed Ubuntu 13.10 Saucy Salamander on my ARM v7 device with kernel 3.8.13. This is my first approach to Linux/Ubuntu and I am impressed that everything works fine out of the box, even the touchscreen.

However I am struggling to install my printer and several other devices on my new system. The printer is an EPSON XP-205.

From the EPSON website I found some drivers for Linux but they are for other architectures, like x86, x86_64, AMD64.

My questions is: since there are sources too, can I use them to compile the driver for another architecture (in my case, ARM v7)? I have nearly zero experience with Linux/Ubuntu, so I don't know if this is an idiocy or not.

Thank you for your patience.

---

### Post by sanderj on 2013-11-23
Ouch, you need a proprietary, binary driver for you EPSON XP-205?

I would *try* two things:
- connect the printer via USB, type "lsusb", and find the line with the printer. Copy-paste the line here, and google for it
- go into the printer settings, select EPSON, and see if existing drivers work.

Personally I only buy hardware that works out-of-the-box on Linux and with open source drivers.

---

### Post by DuckHook on 2013-11-23
> **only.tiki said:**
> ...since there are sources too, can I use them to compile the driver for another architecture (in my case, ARM v7)?If the driver makes only common system calls and is not written to be architecture-specific, then compiling from source should work. However, too many drivers are architecture-specific because that is an easy way to squeeze out additional performance. Also, many so-called "sources" are not actually source code but just a script that compiles a source wrapper with proprietary firmware blobs. This is almost always the case with WIFI chipsets, offbeat NICs, FakeRAID cards and especially video drivers. If so, then the blobs were likely compiled for x86/_64 and won't work with ARM. It is impossible to tell in the Epson case without going over the code, which I am not remotely qualified to do. But since printers are relatively simple peripherals, you have a fighting chance that the "source" code is true source and may work.

This ignores the larger issue that compiling from source is not an exercise recommended for absolute beginners. You need at least a rudimentary understanding of how the system works, and what packages are needed for a proper compilation. There are guides all over the internet and it's not really all that hard once you get the hang of it, but it is frustrating at the start.

In my opinion, the best strategy for your situation is to find a driver from the repository that provides most of the functionality that you need. Often, drivers for older printer models will still work with newer models. I don't own any Epson printers, so can't help with which might be good candidates. As always, experimentation can provide a quick confirmation.

---

