---
title: "Intel graphics driver for Dell dimension 2400"
date: 2013-06-12
forum: New to Ubuntu
---

### Post by c0mputerguy on 2013-06-12
I have a dell dimension 2400 with Intel 845 onboard graphics and Ubuntu 13.04. lspci -k displays it as this:

```
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
    Subsystem: Dell Device 0160
    Kernel driver in use: i915
```

The Intel drivers don't seem to work as when I log in unity doesn't load, all I get is the desktop background, which looks like it is in 16-bit colors. Xubuntu desktop works, but also only with 16-bit colors. I've tried the Intel graphics installer wizard, which makes no difference. Uninstalling xserver-xorg-video-intel makes it use the cpu for graphics, which works, but gives me very poor performance.

---

### Post by squakie on 2013-06-12
Edit your boot options and put i915.modeset=0 in by quiet,nosplash.  If that doesn't work, try i915.modeset=1 instead.  When that works we can walk you through making it permanent.  The 845 is not real great in Linux, but changing the modeset usually helps.  Some say nomodeset - I don't know if this superceeded i915.modeset or nor - I just know i915.modeset is the option that has been recommended for this GPU in the past.

---

### Post by c0mputerguy on 2013-06-12
Both i915.modeset=0 and nomodeset - I result in a blank screen requiring a hard shutdown. i915.modeset=1 doesn't make any difference. Also, the boot options say quiet splash, not quiet nosplash. Should I change that?

---

### Post by squakie on 2013-06-13
the quite splash doesn't hurt anything.  You may want to try using ACPI=off and APIC=no and see if that makes any difference.  I used to have a 2500 series years ago and it's seems like I had to do something like that to get it to work.

Oh, and by the way I made a typo I just caught in the previous thread:

should be:  nomodeset  

I don't think this will make any difference, as both i915.modeset and nomodeset are telling the kernel not to set the video mode for you as this often results in unreadable, black, white or blank screens.

---

### Post by c0mputerguy on 2013-06-14
acpi=off(only lowercase) makes it 640x480 resolution, but doesn't fix it. apic=no doesn't do anything, but it prevents the computer from turning itself off (It gives a halt message, then sits there until you press the power button). nomodeset results in a black screen. I noticed that with the default boot parameters, when the splash screen comes up (xubuntu splash screen) it will display correctly, freeze, switch to a black screen, then come back up with it in 16-bit colors and continue booting, as if that is the point where it loads the graphics drivers.

---

### Post by Mark Phelps on 2013-06-14
I've been  messing around with installs lately, and a parm that I found worked well with difficult video situations was "xforcevesa".  You could try that and see if it helps.

---

### Post by c0mputerguy on 2013-06-14
xforcevesa doesn't do anything either.

---

### Post by hwertz10 on 2014-01-15
I was looking up specs on a Dimesnion 2400 since I just came across one.  I know this thread is old *shrug*.  Anyway, when I did some Ubuntu installs onto 845-vintage Optiplexes, GX240s were no sweat, quite a few GX260s had SERIOUS video issues until I updated the BIOS.  This makes me think the 2400 probably needs a BIOS update.

---

### Post by sireangelus on 2014-01-16
i don't think that the intel 845 is capable of running unity, or any compositing engine, try running xubuntu disabling the compositor in the window manager settings

---

### Post by lchurch2 on 2014-06-07
> **sireangelus said:**
> i don't think that the intel 845 is capable of running unity, or any compositing engine, try running xubuntu disabling the compositor in the window manager settings

To quote the CIA Director in Independence Day: " That may not be entirely accurate Mr. President "  The key to have compositing work with these GPU's seems to be to make sure the most current Microcode is installed and set the memory share to max... I think its 8 on these units. You will however not have a pleasant experience trying to run something like Unity as the GPU/CPU are being tasked to the max.  Going with a lighter Desktop such as Razorqt, LXDE, Lubuntu, or XFCE / Xubuntu and not going Christmas tree with the visual bells and whistles make these units still functional.  The compositors that I have actually had working were Compiz, Metacity, and a really weird private testing one called Flexcomp which I don't think is being developed any longer / it was some variant of Compiz.

---

### Post by squakie on 2014-06-07
And you could also just try

i845.modeset=0  if that doesn't work, then try i845.modeset=1

---

