---
title: "Sylvania Smartbook ARM-WM8650"
date: 2012-06-04
forum: New to Ubuntu
---

### Post by TLScott93 on 2012-06-04
I have a Sylvania Smartbook ARM-WM8650 not 8505.
to keep it brief.  how do I install ubuntu on it?

---

### Post by mastablasta on 2012-06-04
i don't think you can. Unless there is an arm version out. btu as i know only intel and AMD are supported at the moment. but there is pllan to have it: [https://wiki.ubuntu.com/ARM](https://wiki.ubuntu.com/ARM)
 
you can (maybe) install Debian on it.

---

### Post by TLScott93 on 2012-06-04
> **mastablasta said:**
> i don't think you can. Unless there is an arm version out. btu as i know only intel and AMD are supported at the moment. but there is pllan to have it: [https://wiki.ubuntu.com/ARM](https://wiki.ubuntu.com/ARM)
 
you can (maybe) install Debian on it.
thanks i've read that other places too. thing is, i dont even know how to do that. before encountering this P.O.S. i actually thought i was tech savvy

---

### Post by mastablasta on 2012-06-04
get debian arm image and try to boot from it. if it boots, continue with install.

---

### Post by birdie1234 on 2012-06-04
thanks i've read that other places too.

---

### Post by 3rdalbum on 2012-06-04
ARM is not like x86. With x86, any x86 operating system can be booted on any x86 CPU.

With ARM, they're actually kinda incompatible with eachother, mainly due to the other hardware that comes with a particular ARM SoC. For example, the ARM in a smartbook might not run the same code as the ARM in a different smartbook, or in a Raspberry Pi, or in an iPad.

Unfortunately this means that, unless Debian has got a specific version for the ARM SoC in your smartbook, you basically can't run it. To make matters worse, your smartbook probably has no provisions for running an operating system from anywhere other than the integrated flash memory or HDD.

If I were you, I'd probably sell it and buy something x86-based so I can run Ubuntu. But if the device is useful to you as it is, then by all means continue to use it.

---

### Post by mörgæs on 2012-06-04
Changed the thread title to a more informative one.

---

### Post by TLScott93 on 2012-06-04
> **3rdalbum said:**
> ARM is not like x86. With x86, any x86 operating system can be booted on any x86 CPU.

With ARM, they're actually kinda incompatible with eachother, mainly due to the other hardware that comes with a particular ARM SoC. For example, the ARM in a smartbook might not run the same code as the ARM in a different smartbook, or in a Raspberry Pi, or in an iPad.

Unfortunately this means that, unless Debian has got a specific version for the ARM SoC in your smartbook, you basically can't run it. To make matters worse, your smartbook probably has no provisions for running an operating system from anywhere other than the integrated flash memory or HDD.

If I were you, I'd probably sell it and buy something x86-based so I can run Ubuntu. But if the device is useful to you as it is, then by all means continue to use it.

well that sucks.  should've known it was too good to be true.

---

### Post by ultrasquid on 2012-07-25
No need to get down in the mouth just yet... I just bought one of these off newegg for $52 shipped and you do have some options.

Do a search for "wm8650-Angstrom-Gnome-v2.tar.bz2" make a 50 mb fat 32 partition on a a sd card and format the rest ext2. Extract the files from the fat archive to the fat partition and the ext2 archive to the ext2 partition. Stick the sd card in the machine and power it on :) BTW, it comes with doom installed

You might also want to look at uberoid for the wm8650. I plan on giving that a try along with debian tonight. The embeded windows this thing comes with inhales vigorously.

---

