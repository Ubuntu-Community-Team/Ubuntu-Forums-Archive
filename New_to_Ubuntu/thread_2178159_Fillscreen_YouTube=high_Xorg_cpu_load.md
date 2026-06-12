---
title: "Fillscreen YouTube=high Xorg cpu load"
date: 2013-10-02
forum: New to Ubuntu
---

### Post by KzKs3JF on 2013-10-02
I'm having problems with Youtube and some other stuff lately. Fullscreen videos are stuttering/freezing, I guess theres a problem with my Xorg process:

[http://ubuntuone.com/6oEf3PVMt8DofYCO2CyPnH](http://ubuntuone.com/6oEf3PVMt8DofYCO2CyPnH) -Normal
[http://ubuntuone.com/45pEIWd2THZWwqQpuA4W6C](http://ubuntuone.com/45pEIWd2THZWwqQpuA4W6C) -After exiting fullscreen
[http://ubuntuone.com/1QjvmR1nsaXvPiH0gzgkMQ](http://ubuntuone.com/1QjvmR1nsaXvPiH0gzgkMQ) -When browsing launchpad.net

Is it corrupted driver data or something?

I'm running Ubuntu 13.04 32bit on:
 Core 2 Duo e8400 3.00GHz
GF 9600gt 512MB with 313 update driver
4GB RAM

---

### Post by DuckHook on 2013-10-02
Likely a driver issue. Have you tried the nouveau (open source) driver? If so, what result?

BTW, not necessary to post further screenshots (they take up lots of bandwidth). Just CPU usage will do.

---

### Post by KzKs3JF on 2013-10-02
Well its a bit less choppy with this driver, xorg is at ~26% and FF's plugin container went up to 43% for some reason. I did a fresh installations 2 times today but the videos are still choppy. Its the same in chromium browser... Everything was ok like 2 days ago.

---

### Post by KzKs3JF on 2013-10-02
Hmm... HTML5 videos are working perfectly fine. I think it has something to do with flash and xorg.

---

### Post by DuckHook on 2013-10-02
I have some laptops with very similar specs. Your video card is actually superior to the chip in my boxes, so Ubuntu should run nicely with the right driver.

We already see that your initial problem was a driver issue. The nouveau driver (I assume you are referring to nouveau when you say "this driver") has decreased CPU load significantly. Being open-source, it is not optimized for nVidia video (this may get me into trouble with some posters), so finding the right proprietary driver will hopefully push you over the hump and yield quite acceptable performance.

I see that you have re-installed 2 times already. While I feel badly for you that you are going through all of this work, at least you don't seem to be fazed by the prospect, so I would recommend one further install based on the following: unless you have a reason for sticking with 32-bit, I would encourage you to go to 64-bit Ubuntu. I suspect that most future development will be directed to the OS of the future rather than the OS of the past. Your system should run a 64-bit OS with no problems, and there is even a remote chance that this alone may be enough to increase video performance.

So, if you are game, please install 64-bit and tell us what performance you get afterwards (it will be called amd64 on the download site--don't let the "amd" fool you--it works on Intel without problems). I predict that you won't see much improvement, but first things first. After 64-bit is installed on your system with default open-source drivers, we can proceed step by step to installing the proprietary driver (there are a number of them).

---

### Post by KzKs3JF on 2013-10-02
Ok so now I'm running 64bit 13.04 and the problem still persists(on the default Nouveau driver). Nothing has been Installed exept for the updates. Sould I Install the 313 driver or the older ones first(173,304,304-updates,310,310-updates)? =/

---

### Post by DuckHook on 2013-10-02
Since previous issue was 313 driver, I would try older ones first. Just a flying stab, but 304 is what I have installed.

---

### Post by KzKs3JF on 2013-10-02
Welp its a tad bit better but still choppy. Guess its time for 310 xD

---

### Post by KzKs3JF on 2013-10-02
Nope, still the same. :( Tested them all and the videos are the same on every single driver.

---

### Post by DuckHook on 2013-10-02
Be prepared to have to re-install. My experience with switching proprietary drivers was that after two or three changes, the video subsystem became so unstable that I would go to black screen.

Last but not least, I just noticed that your card is a 9600GT, not 9600M GT. So it's based on technology almost 6 years old. Didn't register in my brain before. It is possible that even optimized performance will not yield insanely good results. Let's cross that bridge when we come to it. For now, tell us what resolution monitor you are running. You can also try invoking nVidia settings to see if you can fine-tune the card to work more smoothly.

Edit

Just got ninja'd by your last post.

/Edit

---

### Post by DuckHook on 2013-10-02
> **KzKs3JF said:**
> Nope, still the same. :( Tested them all and the videos are the same on every single driver.Choppy is one thing, but does every single driver run your CPU at 99%?

---

### Post by KzKs3JF on 2013-10-03
Yes, every single one is running at~90%cpu when youtube is in fullscreen. The thing is, everything was perfectly fine 2-3 days ago. My gf runs great on winXP no choppyness or high cpu usage at all.

---

### Post by DuckHook on 2013-10-03
> **KzKs3JF said:**
> ... everything was perfectly fine 2-3 days ago.You did mention this in your first post. Were you running with proprietary drivers at that time? Do you recall an update that may have destabilized your system? Does XP run without problems now? Please check XP while you have YouTube up and running full screen (using task manager) to see what your CPU load is.

If the system is stable with Nouveau, but not proprietary drivers, you may be stuck with Nouveau.

You could also try the 319 driver linked to [here]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia"). But if the older drivers don't work, there's no reason to assume that this newer one will work either.

---

