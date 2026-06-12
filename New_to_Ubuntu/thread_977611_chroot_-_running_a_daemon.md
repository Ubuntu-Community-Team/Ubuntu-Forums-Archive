---
title: "chroot - running a daemon"
date: 2008-11-10
forum: New to Ubuntu
---

### Post by timandjulz on 2008-11-10
Hi all,

I am no expert but a few years back, with the help of a good kb article, I created a chroot environment on a server for running a specific program.

I am curious if you can run a daemon in a chroot jail if it needs access to all the hardware.  This is a hardware monitoring app that I need to run occasionally to log what hardware is connected.  But I want to isolate it in case something goes haywire.

I figure it will need access to /dev, /proc and maybe /sys.  Chroot should prevent it from installing and messing up anything in the real root but I am not sure if it will still have access to the needed system folders.

Is this possible or should I use another method?

Thanks,
Tim

---

