---
title: "openGL &quot;can't create direct rendering context&quot; 50%+ of time"
date: 2009-12-14
forum: Programming Talk
---

### Post by akashiraffee on 2009-12-14
Ubuntu 9.10 32 bit

I'm working on an openGL app and very often I get "can't create direct rendering context", which is an xorg/driver issue.  This causes a lot of flickering and other problems; it is not usuable.

If I reboot, the problem *may* disappear.  Like of the past 3 times, the first two it occurred right away, the third time it started the second or third time I launched the app test.

The forth time I switched back to FC10-64, where this never happens.  Anyone heard of this or know anything of it?

---

### Post by Can+~ on 2009-12-14
Xorg driver issue, or is it compiz fusion screwing things up? 
To enable/disable compiz-fusion if it's giving you trouble, create two launchers in your desktop:

```
metacity --replace
compiz --replace
```

On the other hand, are you running with intel graphics card?

---

### Post by akashiraffee on 2009-12-16
> **Can+~ said:**
> On the other hand, are you running with intel graphics card?

An ATI 4350.   No problems on FC10-64, but then I just used the drivers direct from ATI for that.

I didn't try disabling compiz, because AFAIK that may slow things down, but it should not prevent other GL applications from running.

For posterity: I removed the driver via the "Hardware Drivers" panel, then installed the same one I used in FC10, from ATI.  I think these are the same version number, but perhaps ATI linked the ubuntu package against the default kernel.  I rebuilt my kernel earlier also, altho it is the same version from  the ubuntu source, and at that point I also reinstalled fglrx to be safe.  I hadn't worked much on the OGL stuff on ubuntu prior to that, so I'm not sure if the kernel rebuild caused the problem.

Anyway, it seems to be fine for now...

---

