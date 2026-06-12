---
title: "Why does the top of my window disappear?"
date: 2008-11-19
forum: New to Ubuntu
---

### Post by CryptiniteDemon on 2008-11-19
Often the top of any windows will turn completely white.  It seems to do it using any theme I have.  Never does it on any part of any window except for the top part with the x, max, and min.

---

### Post by aeiah on 2008-11-19
are you using compiz? what graphics card do you have? what version of ubuntu are you using?

---

### Post by CryptiniteDemon on 2008-11-19
Using ubuntu 8.10.  Yes I'm running compiz.  I have a nvidia 7600 gs card and I'm using the proprietary driver for it.

---

### Post by tuxxy on 2008-11-19
Try selecting a theme with Emerald theme manager as you maybe using compiz window decorator

```
sudo apt-get install emerald
```

If you select a theme and it doesnt change maybe you need to replace window manager with this command
```

emerald --replace
```

---

### Post by CryptiniteDemon on 2008-11-19
I don't want to use emerald.  My other computer uses the themes without this mistake, so I don't think emerald would be treating the problem, merely covering it up.

---

### Post by GH68 on 2008-11-22
I have had the same problem since upgrading to 8.10. Finally I've solved it by upgrading the NVIDIA driver to V180.06. I just downloaded from [http://www.nvidia.com/object/linux_display_ia32_180.06.html]("http://www.nvidia.com/object/linux_display_ia32_180.06.html") and followed the instructions. Hope it works for others as well.

---

### Post by CryptiniteDemon on 2008-11-22
The driver update seems to have worked.  It still has the smallest little pixel problems on the top of the window, but it's largely fixed I guess.

Thank you sir.

---

### Post by SamNSane on 2008-11-22
> **CryptiniteDemon said:**
> I don't want to use emerald.  My other computer uses the themes without this mistake, so I don't think emerald would be treating the problem, merely covering it up.

I'm not saying that you're wrong, but I am saying that you might be missing something in your analysis.

I'll give you an example from my own experience. I use Hardy on two personal systems. One system has a really expensive nVidia graphics workstation subsystem optimized for CAD/CAM, rendering, etc. The other has an inexpensive integrated Intel graphics subsystem, half the processor speed / power, and less than half as much memory.

The graphics workstation right from the start underperformed the teensy-weensy subnotebook with the integrated Intel video system. The expensive system not only did everything (graphics-wise) slower than the subnotebook, it also suffered many more glitches in display behavior -- disappearing title bars on windows, choppy video playback, window and cursor trails, you name it.

I finally fixed most of that system's display issues by installing compizconfig-settings-manager and then the Compiz Fusion icon applet (compiz-fusion) from Synaptic and experimenting with the simplest settings. The thing that finally resolved most of the glitches and the crappy performance on that system was to use compiz-fusion to change the window manager from Compiz to Metacity. Dumb. But it worked.

Obviously, there was some sort of issue between the Compiz window manager and the restricted nVidia driver on my system. It's possible that changing some other setting -- some setting that the two window managers implement differently -- might have worked as well.

Unfortunately, conflicts between complex hardware drivers and software can be caused by truly arcane issues. Often, the only effective way to sort them out on an affected system is to go through a rather laborious process of changing one little setting at a time and testing after each change. I'm glad I did it for the workstation, but I'll admit I was pretty annoyed while I was doing it.

This would obviously be a much smoother process for people like us if nVidia would pull its head out and go Open Source with its drivers. That would give the Open Source community a much better chance to sort stuff like this out before each new distro release. Right now, we're stuck with an okay-try-this-oops-no?-okay-then-try-this-better?-no?-okay-then-try-this-okay-that's-a-little-better-but-something-else-broke hamster wheel.

If nVidia doesn't change it's stance, then I'll be avoiding purchasing anything with their hardware in it at all costs in the future. I'd rather accept lower performance levels than have to do a half-witted glitchy-driver two-step every time I upgrade or change my distro.

My advice is to try to solve the issue via the scientific / painstaking / one-tiny-step-at-a-time method. If a change doesn't work, revert to the previous setting, and change some thing else, test, revert, etc. It'll drive you nuts, but not quite as nuts as just living with glitchy video. At least if you're as nutty about these matters as I am.

;)

---

