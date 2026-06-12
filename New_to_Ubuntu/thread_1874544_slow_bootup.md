---
title: "slow bootup"
date: 2011-11-03
forum: New to Ubuntu
---

### Post by ericstrom on 2011-11-03
Wondering if there is someone that can help me figure out what's causing slow boot up. I have old hardware and I think that's the issue. But I'd like to be able to isolate the specific hardware component that's causing the problem (hard drive, bios, motherboard ...etc). 

Here's what I'm observing when I boot:

Asus (A7-V8X-X)splash screen comes on after turning the PC on
Asus splash screen continues for close to one minute.
bios screen (I think) comes on for about a second
Black sceen with cursor for about 3 seconds
Ubuntu (Lucid Lynx)splash screen for approximately 20 seconds.
Computer on and fully operational.

Any idea what's causing the Asus splash screen to linger for almost a minute ? Is there an easy way to conform the problem ?

---

### Post by Azdour on 2011-11-03
Hi,

To the best of my knowledge the splash screen usually hides the POST screen. There should be a key to press to see the POST (or a setting in the bios to disable the splash). Maybe that will give you a clue as to what it is getting stuck on?

I think it does sounds like the POST is having problems with something. On my PC it takes quite a while for my HDD's on SATA to be detected and displayed on the POST screen - I think that is telling me my motherboard is faulty as it was not always like this.

---

### Post by Goldiescorpio on 2011-11-03
Hi there Ericstrom,

Can you try and press tab while seeing that screen?
Normally it will switch to POST screen instantly.
You can also change it in your BIOS, but only if you now what you are doing.
Normally it should say something like: "Display (full)logo" or "Display splash screen".
If you disable this option you should see the normal POST screen.

Good luck !

Grtz

---

### Post by drbono on 2011-11-03
Try this...worked great for me.
[http://ubuntuforums.org/showthread.php?t=1749924&page=2](http://ubuntuforums.org/showthread.php?t=1749924&page=2)

---

