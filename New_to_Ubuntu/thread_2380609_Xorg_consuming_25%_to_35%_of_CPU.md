---
title: "Xorg consuming 25% to 35% of CPU"
date: 2017-12-19
forum: New to Ubuntu
---

### Post by singhislion on 2017-12-19
Hi All, I am new to Ubuntu. I installed this on my old laptop last weekend and here are the details for the start

Linux singhs-355V4C-356V4C-3445VC-3545VC 4.10.0-42-generic #46~16.04.1-Ubuntu SMP Mon Dec 4 15:57:59 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

Laptop config
Memory : 8 GB
Processor : AMD E2 1800 APU with Radeon(tm) HD Graphics x2
Graphics : Gallium 0.4 on AMD CAICOS (DRM 2.49.0/ 4.10.0-42-generic, LLVM 4.0.0)
OS type: 64 bit
Swap: 4 GB
My problem is that the performance is sluggish, especially for browser. Chromium or firefox both are very very slow. Top command on terminal shows Xorg eating 25% to 35% of CPU. Pls advise.

---

### Post by QIII on 2017-12-19
Hello.  Would you please edit your post to remove the tags and the image elements?

Thanks.

---

### Post by singhislion on 2017-12-19
done

---

### Post by mastablasta on 2017-12-20
you are on radeon driver: [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

you could try and upgrade the kernel: [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

the chip is not a sprinter, but it should still work relatively well, particularly for desktop/office apps.

---

