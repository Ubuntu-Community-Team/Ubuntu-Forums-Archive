---
title: "[SOLVED] Latest Kernel Update (Hardy) kills USB sound"
date: 2008-11-28
forum: New to Ubuntu
---

### Post by coolbrook on 2008-11-28
I just downloaded the latest kernel update through Update Manager and was prompted to restart.  Once I rebooted, my USB sound card is no longer working.  It is detected by lsusb

```
steven@LEONARDO:~$ lsusb
Bus 001 Device 003: ID 046d:c216 Logitech, Inc. Dual Action Gamepad
Bus 001 Device 002: ID 0d8c:0103 C-Media Electronics, Inc. Turtle Beach Audio Advantage Micro
Bus 001 Device 001: ID 0000:0000
```

When I go to the System > Preferences > Sound, next to 'USB Audio' it says (not connected)

What should I try?

---

### Post by coolbrook on 2008-11-28
Well I just rolled back to version 2.6.24-21 from 2.6.24-22 and my sound is functional, so it definitely has to do with the new kernel version.  I'll leave this thread 'unsolved' until I can test again with an even newer update, but feel free to add any suggestions in the meantime.  Perhaps I'll learn how to use launchpad to file a bug report.

---

### Post by coolbrook on 2008-12-01
I'm not 100% certain if this was a missing package after my update but I installed:

**linux-ubuntu-modules-2.6.24-22-generic**

I went into Synaptic (and in my case) enabled all of the packages that were related to both '2.6.24-22' and 'generic' (since my system is SMP enabled) and I now have audio working with the 2.6.24-22 version of the kernel.

Under the modules' description there's a note about selecting the linux-generic meta-package, so I also installed:

[B]linux-generic
linux-image-generic
[/B]

I filed bug report #303220 in Launchpad if this happens to anyone else.

---

