---
title: "projector woes"
date: 2014-08-30
forum: New to Ubuntu
---

### Post by Joe_Clark on 2014-08-30
Hi, relative newbie here.  I've used Unix/Linux a few times before, but never on my main work computer.  Now I've got Ubuntu (latest version) running on my laptop, an HP Pavilion dm4 that's about 3 years old.  I am a professor and I need to plug in to projectors in several different classrooms -- all different models, natch -- and haven't gotten good results.  When I plug in with the HDMI cable, I'm forced to a lowest-common-denominator resolution, usually 640x480 although in one classroom it's a bit bigger (800x600 maybe).   When I plug in with the VGA cable, the resolution is fine BUT the operating system won't let me "mirror displays", so I have to turn my back to the class and treat the projector like a second monitor.  Is there an easy fix for this?  It's kind of a deal-breaker for me if I can't use my laptop with arbitrary projectors.

---

### Post by QIII on 2014-08-30
Hello!

Just to be sure, by "latest version", you do mean 14.04, correct?

Could you give us the complete hardware specs of your laptop?  The graphics adapter is very important.

Have you installed any proprietary drivers?

I'm going to say something that may Linux folks would consider anathema: If we can't get this fixed, use what works -- if that's Windows, then so be it.  You have a job to do.

:)

---

### Post by Joe_Clark on 2014-08-30
Yes, the version is 14.04.  I probably should have said "latest production version", right?  I'm pretty sure it's an Intel graphics card.  There are a few different HP Pavilion dm4 models, though, I'll have to check in the office on Monday.

---

### Post by Joe_Clark on 2014-08-30
I'm getting this from lspci:
> 00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09) (prog-if 00 [VGA controller])
        Subsystem: Hewlett-Packard Company Device 1650
        Flags: bus master, fast devsel, latency 0, IRQ 44
        Memory at c0000000 (64-bit, non-prefetchable) [size=4M]
        Memory at b0000000 (64-bit, prefetchable) [size=256M]
        I/O ports at 4000 [size=64]
        Expansion ROM at <unassigned> [disabled]
        Capabilities: <access denied>
        Kernel driver in use: i915


---

### Post by Joe_Clark on 2014-09-03
Just going to bump this one more time and see if anybody has an answer.  How do I get Ubuntu to work with a projector?

---

### Post by Joe_Clark on 2014-09-03
This is my specific model: **[SIZE=2][FONT=arial]HP Pavilion dm4-2033cl[/FONT][/SIZE]**
And the specs:
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c02863091&tmp_task=prodinfoCategory&cc=us&dlc=en&lc=en&product=5111904](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c02863091&tmp_task=prodinfoCategory&cc=us&dlc=en&lc=en&product=5111904)

The video card is: [COLOR=#000000][FONT=HPSimplified]Intel HD Graphics 3000[/FONT][/COLOR]

---

### Post by Joe_Clark on 2014-09-03
OK, this is interesting.  When I look at the System details in Ubuntu's "Settings" app, It describes the Graphics as "Intel(r) Sandybridge Mobile".  Does that mean I've got the wrong driver installed?  How would I fix that, if so?

---

### Post by JeQhdMD on 2014-09-04
On any given day, there are thousands of Linux laptops being hooked up to epson or similar OV projectors.  So, they work, and video drivers (modules) for Intel video are auto setup when you install ubuntu.   The module is pre-compiled to the kernel . . nothing to download or install, unless you want to try to screw up the display royal.

What I do with my Acer Timeline 4830T-6841 with Intel 3000 video is:   turn on the overhead projector first, let it warm up.  The connection setting will either be PC1 or PC2 on most projectors (with 1 being the default).    Then I connect the VGA connection cable to the laptop (with the other end connected to the projector or the built-in lead.   Then I boot up Ubuntu and IF it's the first time for the connection, I go to the System Settings>Displays>Detect Displays (if the projector not already listed as a second display)>Check Mirror Displays>Check Apply.    Give it a few seconds to set the display.   My laptop normal display is 1366 x 768, but the projector display will be slightly less (and the display on the laptop monitor is somewhat compressed (but very usable).

Give the above a try, and let us know how it goes.   Your laptop should work just fine with the specs you provided, unless your local projectors are setup different than most.   You might also want to play around with the menu options on the overhead projector.

PS - - Ive used a half dozen laptops with Linux in the past, and each one allowed me to "mirror displays" . . . . so it's not the OS but another setting or the timing that's getting messed up (the projector always has to be running first, then the laptop must be started so it can auto detect the device).  Also, your owners manual may have more info, especially about the key combos for overhead displays (fn+f5, f6, f7, f8 are used for many laptops).

---

