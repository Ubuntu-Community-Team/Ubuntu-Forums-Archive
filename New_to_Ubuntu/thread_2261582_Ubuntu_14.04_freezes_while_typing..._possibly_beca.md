---
title: "Ubuntu 14.04 freezes while typing... possibly because video driver?"
date: 2015-01-19
forum: New to Ubuntu
---

### Post by Sam_Osman on 2015-01-19
I recently updated to nvidia-340 drive and I'm using nvidia prime becaus my laptop is hybrid intel/nvidia.  My laptop is ASUS N56JN with Intel 4xxx HD Graphics and GeForce 840M.  The laptop is also i7 4700HQ @ 2.4 GHz & 8 GB RAM (if relevant).

The mouse and keyboard freeze when I'm typing here in the forums and when I am typing in LibreOffice Writer.  I am not sure if it will freeze in anything else at this time because I haven't tried it and I haven't noticed it freezing elsewhere.

When it freezes I can do Alt + Ctrl + F1 (which opens that login terminal thing) and then Alt + Ctrl + F7 and it will go back to where I was and it will be not-frozen.  It then freezes again after some seemingly random interval of time.

I have tried the Alt + Print Scrn + REISUB and it works...it restarts the system, BUT then it still does the random freezing!

I was going to try either upgrading or downgrading the nvidia driver to see if it makes a difference.  But first,  I will try using prime to switch to the intel card and see if it also freezes.

Let me know what else I can do to fix this!

Thank you in advance!

---

### Post by bobhandley on 2015-01-25
I also have an Asus N56JN and it started to freeze after installing the nvidia-340 driver. It did not do so when using the Intel graphics driver. Anyone have any ideas?

---

### Post by NilPointer on 2015-01-25
Those freezes probably are happening not because of typing per se, but rather because of likely side-effect of touching the touchpad during typing.

The thing is that there's a very old, infamous and annoying bug with NVidia cards and many laptop touchpads that cause freezes while using touchpad and GPU is in NVidia mode.

[https://bugs.launchpad.net/xorg-server/+bug/1220426](https://bugs.launchpad.net/xorg-server/+bug/1220426)

Unfortunately, even though NVidia's engineers are informed about the problem, they apparently have problem fixing that. This bug was there for more that 1.5 years. There are still workarounds. None are close to be perfect, but might help you:

1) You can switch your touchpad to a more simpler driver. The major downside of that workaround is that you will lose all multitouch touchpad gestures (scaling, two-finger scrolling, etc., only moving cursor and scrolling will remain).
2) You can switch off your touchpad (either temporarily or permanently) and use a USB mouse. This solves the problem of freezes completely, but it's an option only if you don't need touchpad and can use mouse.
3) Switch your GPU into Intel mode. Touchpad doesn't conflict with Intel driver. This may be best option for typing documents. And when you need NVidia card again (games, etc) - you can switch it back.

---

