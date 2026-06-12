---
title: "Strange little error message while booting"
date: 2013-09-15
forum: New to Ubuntu
---

### Post by ImTroyMiller on 2013-09-15
Here's what I have for hardware...
Gigabyte 970A-D3 Rev 3.0 motherboard
NVidia GeForce GTX 650 Ti Boost video/graphics card
AMD FX 6300 Six Core Processor
32gb of RAM(4x8gb sticks) Corsair Vengence
Asus DVD/Blu-Ray
1tb Hard Drive "00RKKA0"(With Windows 7 Professional)
1tb Hard Drive "07ZF5A0"(With Ubuntu 12.04 Precise Pangolin)
75gb Hard Drive "00FLA1"(No OS)

I get a strange little error message that says "mmio address 0xbafe00 already in use".

Here is a video I've put YouTube that shows this error...

[http://www.youtube.com/watch?v=ClAVBK_bIrQ](http://www.youtube.com/watch?v=ClAVBK_bIrQ)

I've also attached an image.

Why do I get this error?

---

### Post by oldfred on 2013-09-16
Found this, but the suggested blacklist does not always work?

[http://askubuntu.com/questions/38920/boot-splash-broken-by-sp5100-tco-timer-mmio-address-0xyyyyyyy-already-in-use](http://askubuntu.com/questions/38920/boot-splash-broken-by-sp5100-tco-timer-mmio-address-0xyyyyyyy-already-in-use)
[https://bbs.archlinux.org/viewtopic.php?id=125482](https://bbs.archlinux.org/viewtopic.php?id=125482)

---

### Post by ImTroyMiller on 2013-09-17
Is this something that I should even be worried about?

---

### Post by ibjsb4 on 2013-09-17
Got the same thing happening on one of my 12.04 installs.  Its been flashing that message for about a month now will no ill effects to my system.  I thought this was something I did, but after reading this thread I think this (for me) may get fixed with a kernel upgrade.  Have to try that next time I boot it up, but i say that its not a big deal.

---

### Post by shadytv on 2013-09-17
I heard somewhere that there is an unsolved conflict between Plymouth (The splash screen) and Nvidia graphics cards both my PC (the one I'm on ATM) and my laptop do this and they are both using Geforce cards and have the same problem. Honestly, I've spent hours playing with Plymouth and Google and still have no real fix.
I'm currently running Ubuntu 13.04 and have had this issue since at least 11.04.

---

### Post by ImTroyMiller on 2013-09-18
I guess I'll leave it.

---

