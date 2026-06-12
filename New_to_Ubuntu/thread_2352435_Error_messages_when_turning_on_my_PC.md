---
title: "Error messages when turning on my PC"
date: 2017-02-12
forum: New to Ubuntu
---

### Post by tziulm on 2017-02-12
Hello,
relatively recently (on August) I installed for the first time Ubuntu 16.04 on my PC, in dual boot with Windows 8.1. Since then, every time I use Ubuntu, this message shows up, and says open for a while:

  
[ATTACH=CONFIG]273663[/ATTACH]



[    2.179406]  [drm: intel_set_pch_fifo_underrun_reporting  [1915]  *ERROR* uncleared pch fifo underrun on pch transcoder A

 [    2.179427]  [drm: intel_pch_fifo_underrun_irq_handler [1915]  *ERROR* PCH transcoder A FIFO underrun

   /dev/sda6: clean, 1279282/2804368 files, 5977556/11212544 blocks




 The booting time is also quite slow.

---

### Post by ajgreeny on 2017-02-12
You can ignore the ** /dev/sda6: clean, 1279282/2804368 files, 5977556/11212544 blocks**which is not an error, just a notification that the filesystem is clean and does not need a full fsck filesystem check to be run. It very often shows at boot in 16.04 on many systems but is of no consequence.

The first two I can not help with in detail but it would appear to be a bug.
See [https://bugzilla.kernel.org/show_bug.cgi?id=79261](https://bugzilla.kernel.org/show_bug.cgi?id=79261)

---

### Post by tziulm on 2017-02-16
Ok, thank you very much!

---

