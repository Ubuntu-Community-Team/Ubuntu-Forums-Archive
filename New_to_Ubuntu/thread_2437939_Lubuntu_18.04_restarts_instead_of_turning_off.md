---
title: "Lubuntu 18.04 restarts instead of turning off"
date: 2020-03-03
forum: New to Ubuntu
---

### Post by vap25 on 2020-03-03
Hi, I'm new to Linux world, decided to start with Lubuntu whick looked good for my old and weak PC. I've installed it yesterday and it's working good but I just can't turn off it using that menu ([https://www.clubedohardware.com.br/applications/core/interface/imageproxy/imageproxy.php?img=https://www.mundoubuntu.com.br/images/desktops/lubuntu1710/screenshot5.jpg&key=2b7c83b2f94d6054d98079c4bc99d0bec58a82e82024d9875989bd810f2d269b](https://www.clubedohardware.com.br/applications/core/interface/imageproxy/imageproxy.php?img=https://www.mundoubuntu.com.br/images/desktops/lubuntu1710/screenshot5.jpg&key=2b7c83b2f94d6054d98079c4bc99d0bec58a82e82024d9875989bd810f2d269b)). Instead of turning off, it restarts. Does anybody know how to solve this?

My PC is a Intel x64 and the installation file of Lubuntu was written "amd64" (because i have chose Desktop 64 version) may that be the problem? Should I download the x32 version?

[ATTACH=CONFIG]285141[/ATTACH]

Thanks!

---

### Post by MoebusNet on 2020-03-03
I am not a native Portugese speaker, but according to Google Translate, you should be selecting 'Desligar' to shut down your PC from the menu. Selecting 'Reiniciar' should lead to your PC rebooting. If these are not happening correctly, I would suspect a bug in the shutdown process. If your PC is indeed 64-bit capable, then amd64 is the recommended Desktop version. May I suggest that you install the OS without updates, attempt to shut the PC down with the menu and see if that makes a difference? If not, apply any updates to see if that fixes the issue.

---

### Post by vap25 on 2020-03-03
Hi, MoebusNet! Thanks for helping me! I'll try to reinstall it even though I've already tried both x32 and x64. Now without updates as you've said. And Yes, I was trying "Desligar" which means "Turn off/Shut down".

But now i've realized that what happens is actually the PC shuts down all normally (pretty fast, in 1-2 seconds). But it turns on again, it's not like a normal restart. It really dies, then comes back on, makes the boot "beeps" and ask me for my password again.

I'll be back with news.

---

### Post by oldrocker99 on 2020-03-03
This should work:
```
shutdown -P now
```

---

### Post by rbmorse on 2020-03-03
Check the power options in BIOS/EFI.  There's one that dictates how the system is supposed to react when power is lost.  Make sure that it's set to "power off" and not restart on power error. 

Also, check the ACPI settings for power button options.  

One more thing to try (low probability) if the button battery that preserves CMOS memory settings is more than about three years old, you should replace it.  When that is done, load "optimized" settings from the setup menu, perform a full power cycle and the  reneter BIOS/EFI setup and load your preferred options.  Sometimes the settings in CMOS memory can get confused if the battery voltage falls below threshold.

---

### Post by guiverc on 2020-03-04
This may not apply, but I've got an old nokia box that refuses to turn off. If I `sudo shutdown -h now` it'll perform the shutdown correctly, and actually does turn off, but then not quite instantly (but probably .5 seconds or less) it'll turn back on.

I booted different 'live' systems and no OS I tried with the box was any different, so I concluded it wasn't the OS & it was just my quirky hardware (or it's age & something no longer works exactly like it was supposed to) and adjusted it so I can kill the power switch during before it restarts.  On mine I've installed debian, opensuse, freebsd & of course ubuntu & it reacted the same for each  (*I didn't try windows, it's never had windows on it*).  

I'd try booting other 'live' systems and seeing if they act the same. If they do, it'll likely mean it's a BIOS setting, or if your box is like mine maybe some component isn't working as it should.

---

### Post by vap25 on 2020-03-04
Hi guys! I've been working on it, and I've found out the same problem happens to any SO (I've tried Tails and Lubuntu distros and Chrome OS), except for Windows (I'm killing my SSD installing all these SOs). But, as [COLOR=#000000]guiverc and rbmorse said, I went on BIOS settings and the problem stopped happening when I switched the "Restore On AC Power Loss" from OFF to ON (weird, was it not supposed to work the other way around?). Then I discovered the problem does not happen in "Last State" too.

So which one should I choose? OFF or LAST STATE?

[/COLOR]

---

### Post by vap25 on 2020-03-04
Here are the photos I took from the BIOS. It's an old PC.
[ATTACH=CONFIG]285148[/ATTACH][ATTACH=CONFIG]285149[/ATTACH]

---

### Post by MoebusNet on 2020-03-06
Thinking about it, especially if this is a desktop model rather than a notebook model, it is possible that what you are seeing is the result of a dying battery on the motherboard that maintains the BIOS settings. Try replacing the battery and see if the BIOS now retains the proper settings. Like you, I would expect the BIOS setting 'Restore On AC Power Loss' to need to be set to 'Off' to be able to stay shut down; if low battery is the problem it may be defaulting to the 'Restore On AC Power Loss' setting.

---

