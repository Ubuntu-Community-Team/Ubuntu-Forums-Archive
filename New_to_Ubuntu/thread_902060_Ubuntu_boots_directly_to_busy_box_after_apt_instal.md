---
title: "Ubuntu boots directly to busy box after apt installs kernel patch"
date: 2008-08-27
forum: New to Ubuntu
---

### Post by 89vision on 2008-08-27
Apt installed some kernel patches this afternoon and then told me to reboot.  So I reboot and then it just hangs there on the splash screen for 10 minutes and finally drops to a busybox shell.  I rebooted it in Verbose mode and here is what it outputted:
```

Starting up ...
Loading, please wait...
    check root= bootarg cat /proc/cmdline
    or missing modules, devices: cat /proc/modules ls /dev
 Reading all physical volumes.  This may take a while...
ALERT! /dev/mapper/lappy-root does not exist. Dropping to a shell!
```

Normally I would suspect a bad harddrive but it's just too suspicious when apt messes around with the kernel.  I'm pretty lost on what to do right now, any help would be appreciated.

---

### Post by 89vision on 2008-08-27
bump

---

### Post by 89vision on 2008-08-27
Ok I just tried booting with the previous kernel and I still have the same problem.  I am using encrypted LVM, is it possible that apt did something to my bootup scripts that would prevent ubuntu from recognizing encrypted LVM?

---

