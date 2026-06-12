---
title: "Mouse / graphic card driver"
date: 2012-01-28
forum: New to Ubuntu
---

### Post by BlueAZ on 2012-01-28
Hello, good Ubuntu people -- thanks for the help so far!!
Today, I'm asking about a driver for my M$ wireless optical mouse.  I'd buy a new one, but...;~}    It works fine when in my Windows XP hard drive, but in Ubuntu it's all jerky & doesn't scroll smoothly at all.  I've tried settings in Firefox, but no difference.  Is there a driver?  Update?

Next:  I downloaded a driver update for my ATI graphics card.  It's called Catalyst 12.something.  Found link on Upubuntu.  Downloaded it fine, just can't figure out how to install it.  Doesn't open to anything I recognize.

Loving my Ubuntu Natty with Unity 2D!!!!!!!   Thanks again!:P

---

### Post by wolfen69 on 2012-01-28
Just go to *additional drivers* and use the ati driver offered. No need to download it off the internet. As far as the mouse, there are no drivers for mice. They either work or they don't. Most do.

---

### Post by halitech on 2012-01-28
which particular video card do you have?

---

### Post by Mark Phelps on 2012-01-29
To see your make and model video chipset, open a terminal and enter "lspci" (without the quotes).  Look for the line containing "VGA" -- and post that info back here.

Unless you have one of the newer "HD" series of ATI cards, those drivers you downloaded will not work -- and will only trash your display, causing you a LOT of work to get your display back working again.

---

### Post by BlueAZ on 2012-02-01
> **Mark Phelps said:**
> To see your make and model video chipset, open a terminal and enter "lspci" (without the quotes).  Look for the line containing "VGA" -- and post that info back here.

Unless you have one of the newer "HD" series of ATI cards, those drivers you downloaded will not work -- and will only trash your display, causing you a LOT of work to get your display back working again.

:)  Thank You!  I performed the terminal option you suggested & voila!  Lots of info about my graphics card including VGA version [tried to copy & paste here; couldn't].  Looks like it's all installed & working properly.
I guess that's why Optional Drivers doesn't show anything at all.
Still working on the jumpy scrolling w/ mouse.  Seems it's related to Mozilla products Firefox & T-Bird.    Any fixes?    Thanks again!

---

### Post by halitech on 2012-02-01
the info in the terminal simply tells you what the hardware is, not what driver it is using.

to copy from the terminal use either right click - copy or ctrl + shift + C and then paste it here so we can see what you have there.

---

