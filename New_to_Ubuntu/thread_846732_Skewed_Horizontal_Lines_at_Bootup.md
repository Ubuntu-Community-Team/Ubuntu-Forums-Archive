---
title: "Skewed Horizontal Lines at Bootup"
date: 2008-07-01
forum: New to Ubuntu
---

### Post by condar on 2008-07-01
Hi all!  I just installed Ubuntu on my laptop, as I want to start getting used to Linux (to be honest, the primary reason is because I don't want to deal with Vista - at least not too much).

Everything seems to working well enough - I had no problems during the install (except partitioning - it's a dual boot with XP already installed, and had some problems using the guided option, but I worked my way through the manual option), and I can play around in the OS itself with no problem (so far).

My problem, however, is immediately after GRUB has me select how I want to boot up - either Ubuntu or XP.  I select Ubuntu, and I get a bunch of horizontal / skewed lines where the Ubuntu logo and loading bar would be.  I know this because when I first installed it, this appeared, and I can kind of see the orange scrolling bar (actually, it's just one of the horizontal lines that gets bigger every now and then, so it looks like it's pulsing).

I checked my hardware drivers, and they're nVidia proprietary (for a 7800 Go, I have a XPS Gen 2).

It's not a critical issue, but it'd be nice to know what's going on!  If you have any potential fixes or ideas, please let me know and try to dumb it down just a bit for the newbie :)

Thanks!!!

---

### Post by wrtpeeps on 2008-07-01
Sounds like X is configured incorrectly I think?

---

### Post by coolaj86 on 2008-07-01
The boot-up Splash Screen is what I think you're describing. If that's the case, you're nVidia driver hasn't been loaded yet.

If that's the case, perhaps the image was corrupted when it was installed. As long as things work, don't worry about it and sooner or later an update will come along that replaces the corrupted file.

If these lines appear only momentarily (a few seconds) and it's between the end of the boot screen and the start of the login, then it's normal behavior. In my experience I've noticed that the video card somehow keeps in memory pieces of the a recent image (the the splash screen or a movie, etc) and sometimes when the driver is initialized it spews pieces of that image or skewed crap onto the screen for just a second.

FYI: X is the program that loads the user interface and things that you click on (this is the program that makes the log on screen possible).

---

### Post by condar on 2008-07-01
coolaj86, that's correct - thanks for articulating it better for me.

The problem is the initial splash screen which loads immediately after GRUB - it appears as a few streaked, skewed lines across the screen.  It lasts the entire time during bootup and shutdown.

When I checked the hardware section, it said my nVidia driver was loaded, so now I'm thoroughly confused :confused: It noted that, being a proprietary driver, it wouldn't get any updates - so what update should I be looking for / waiting for?

Thanks for all the help!

---

### Post by coolaj86 on 2008-07-02
I could be mistaken (I've become a lot less familiar with the system internals since switching to Ubuntu), but I think that the splash screen uses the kernel's **f**rame **b**uffer driver, not the official nVidia driver, but as soon as you load X it switches to that driver.

Honestly, I just wouldn't worry about it unless you have problems in other areas. I know it's annoying, but aside from forcing a reinstall of the splash screen package (and I don't know what that is off the top of my head), I don't know what would help.

My guess is that it's a corrupt image file or a bug in the kernel's fb driver. Try running software update and see if that doesn't fix it for you.

:-D

---

