---
title: "When screensaver kicks in, it makes fan start working hard in Hardy"
date: 2008-05-12
forum: New to Ubuntu
---

### Post by swarup on 2008-05-12
I use both Ubuntu and Xubuntu Hardy on my laptop, and find that when I am not using the computer for some time and the screen saver starts up, then for some reason it makes the fan start working hard-- as though the computer is having to work harder because the computer has gone into power-saving mode. But the computer should be at rest in that mode, not working harder. Is there some defect in the way Hardy goes into power-save mode?

---

### Post by crjackson on 2008-05-12
> **swarup said:**
> I use both Ubuntu and Xubuntu Hardy on my laptop, and find that when I am not using the computer for some time and the screen saver starts up, then for some reason it makes the fan start working hard-- as though the computer is having to work harder because the computer has gone into power-saving mode. But the computer should be at rest in that mode, not working harder. Is there some defect in the way Hardy goes into power-save mode?

Screen Saver mode is not power saver mode.  Do you have a 3D screen saver running?  That requires processor power and video card power to draw and manipulate the graphics on your screen.  What you are looking for IS your power saving options.  Turn off the screen saver or chose "Blank" adjust your powersaving options to kick in at about the same time as your blank screen and see if that has an effect...

---

### Post by swarup on 2008-05-12
Well, right now I'm in Xubuntu. I see the screen saver utility. It is set to "random" for the screensaver, not 3D. I have an old laptop actually, so it would not be able to run any sort of fancy screen saver. But I do not see where the power saver utility is. Do you know? But at any rate, the fan should not start going wild like this when the screen saver comes on. It is just a simple screen saver, with some random line design on it. My guess is even if I set it to blank screen, the fan will still come on.

I remember seeing somewhere some concerns that in Hardy when power saver kicks in, it makes the computer start doing some sort of very rapid cycling which is not good for either the processor or some other component (was it the HD?). Anyhow, perhaps I'm wrong about it. But I thought I recalled seeing something about this, so when I saw my computer doing this I got concerned.

---

### Post by stream303 on 2008-05-13
If the screensaver is in any way animated, then the cpu is working harder than it has to and wasting power if you aren't looking at the screensaver.

For example, my computer idles at around 88 watts (not sleeping or hibernating, just sitting there doing nothing.)

When an animated screensaver is active, even just a little bit animated, power consumption shoots up to 120 watts or so.

I measured this with a specialized consumer wattmeter, P3 International's "kill a watt"(tm).

You may also want to verify that cpu frequency scaling is actually working with an applet, or looking at

```
cat /proc/cpuinfo
```

when you think the system is idle.

In my case, I found that the default powernowd scaler wasn't working, and I had to substitute another one, cpudyn instead.

---

### Post by swarup on 2008-05-13
That's really interesting stuff. Here is the output from the command you gave. Can you interpret it for me? Is cpu frequency scaling is actually working?

```
swarup@swarup-laptop:~$ cat /proc/cpuinfo
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 6
model name	: Celeron (Mendocino)
stepping	: 10
cpu MHz		: 432.269
cache size	: 128 KB
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 2
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr up
bogomips	: 865.70
clflush size	: 32
```

---

