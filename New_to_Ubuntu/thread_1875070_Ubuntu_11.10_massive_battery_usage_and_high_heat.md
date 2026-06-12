---
title: "Ubuntu 11.10 massive battery usage and high heat"
date: 2011-11-04
forum: New to Ubuntu
---

### Post by Dunti21 on 2011-11-04
Hello guys,

I just bought a dell xps 15z, and decided to install ubuntu 11.10 on it. In windows I get around 7 hours of battery, but when I boot with ubuntu, I end with with under 2 hours on a full charge. The computer heats up drastically. I have read that this is a problem with the kernel, and I tried with kernel 3.0, 3.1, and 2.6 and it's always the same result. I installed bumblebee for the graphics as well. I also edited the grub file with what everyone is talking about, and no help. 

Is there nothing that can be done to fix this? Why isn't canonical getting right on this with the kernel?

---

### Post by cavh on 2011-11-04
Consider installing the Jupiter power management applet:

[http://www.jupiterapplet.org/]("http://www.jupiterapplet.org/")

And post back here with results, please.

---

### Post by Dunti21 on 2011-11-04
Yes, I installed that too. I chose powersave, but that did absolutely nothing...

---

### Post by aeronutt on 2011-11-04
This has worked for quite a few with Intel processors.

This significantly decreased power draw on my i3 based laptop.

[http://ubuntuforums.org/showpost.php...78&postcount=9](http://ubuntuforums.org/showpost.php...78&postcount=9)

My current draw went from ~1500mA to ~800mA with the following kernel options

change
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
To
GRUB_CMDLINE_LINUX_DEFAULT="i915.i915_enable_rc6=1 i915.i915_enable_fbc=1 i915.lvds_downclock=1"

then sudo update-grub

The one that made the majority (nearly all) of the difference was the first.

---

### Post by Dunti21 on 2011-11-04
aeronutt, I had tried something similar but without the "downclock" bit. So I tried yours and the problem persists. Just using Mozilla, I have CPU at 54 degrees, the fan blowing and a battery consumption of 22.4 W. Before I did your update I had around 56 degrees and around 28W consumption I think. So it did help a bit, but I still have very low battery.

Still need a fix :(

---

