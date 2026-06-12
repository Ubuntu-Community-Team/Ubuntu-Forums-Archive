---
title: "[SOLVED] modprobe lsmod commands have stopped working"
date: 2008-07-01
forum: New to Ubuntu
---

### Post by dixonstalbert on 2008-07-01
hello

I am trying to remove kernel module em28xx

When I type```
sudo modprobe -rf em28xx
```

nothing happens and I lose terminal command prompt until I press ctrl-c

If I type ```
lsmod
``` the same thing happens

If I type ```
sudo modprobe -lv
``` then command works, but it shows that em28xx still loaded

This happened one time last year and I found post with solution, but I cannot find it now :(

---

### Post by Hospadar on 2008-07-01
try blacklisting it.  I believe the blacklist is at /etc/modules.d/blacklist or somewhere in that region.  After you add the module to that file, restart.  It could ef up your system though if it's a crucial module (even if it is faulty), so I'd have a livecd on hand before I did it.

---

### Post by dixonstalbert on 2008-07-01
thanks for quick reply!

I think you are correct; em28xx was what was blocking lsmod and modprobe commands.

em28xx is driver for hauppauge usb Tv tuner. I unplugged it and rebooted. kernel did not try load it at boot and now lsmod and modprobe work properly

thanks again

---

