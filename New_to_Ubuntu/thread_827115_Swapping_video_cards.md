---
title: "Swapping video cards"
date: 2008-06-12
forum: New to Ubuntu
---

### Post by silkstone on 2008-06-12
I've recently rebuilt a desktop machine which now runs Hardy. There's an occasional glitch on power-up (garbage on screen instead of the BIOS splash screen, and then nothing) and I suspect the video card - a BFG 8400GS.

I have another 8400GS card but of a different make. Can I just swap them without any reconfiguration?

I'm also running nvidia-settings - do I need to reinstall that to detect the new video BIOS etc?

Thanks for any advice.

---

### Post by defrex on 2008-06-12
You should be able to just swap the video card. You may need to install a new restricted driver to get compiz back though.

---

### Post by Titan8990 on 2008-06-12
Last time I changed cards I didn't have to do anything in Ubuntu. Of course Windows needed a driver reinstallation even though they were the same drivers however Ubuntu required no effort from me.

Also, if your BIOS screen isn't being displayed correctly (and that is the only problem) there is a good chance that you don't have the first video device configured correctly.

The setting should be "PEG" for pci-e graphics and of course not onboard or PCI.

---

### Post by silkstone on 2008-06-12
Thanks for that. It's an intermittent fault so I'll swap the cards next time it happens.

---

### Post by silkstone on 2008-06-13
Update... It glitched again this morning (garbage instead of BIOS splash screen) so I've swapped the card for a similar one of a different make.

So far, so good. It wasn't necessary to reload the drivers, and nvidia-settings picked up the new card - different video BIOS number.

Fingers are now crossed that this solves it, and it isn't a PSU or MB fault. :)

---

