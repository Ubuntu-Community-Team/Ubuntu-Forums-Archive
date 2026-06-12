---
title: "Ubuntu won't reboot after updates"
date: 2013-06-28
forum: New to Ubuntu
---

### Post by bnjrpkr on 2013-06-28
Hello all,

After cracking the screen on my laptop in a freak accident I was forced to buy a new one with Windows 8 preloaded. After 9 days of that I couldn't take it anymore so I downloaded Ubuntu 64 bit 13.04 and Ubuntu 64 bit 12.04. I first installed 13.04 and removed Windows completely. Later that day the update center popped up and after the updates it said I needed to restart. After restarting the Laptop would not reboot. I tried a few different times to get it to come on but after awhile I gave up and put in the 12.04 disc. Curiously it didn't see the 13.04 OS on the computer at all.

After installing 12.04 I was very happy. I was starting to get used to everything and liking it a lot more than I ever liked Windows. A couple times it wanted to update and everything was fine. It's about 3 or 4 weeks later now and I just got back from a 4 day business trip to Greenville, NC. The 3rd day I was there I was messing around on the internet and the update center came up again so I went ahead and installed the updates. After finishing what I was doing I shut the computer down and went to a meeting. When I returned to the hotel room it wouldn't boot back up. I came home today and it still wouldn't boot so I put the 13.04 disc in the computer. It recognized the 12.04 OS this time so I chose to update to 13.04 instead of erasing everything. I kept getting a partition error so I said screw it and just went ahead and installed 13.04 on top of everything.

I'm curious as to what is causing Ubuntu to not be able to reboot after the updates though. Does anyone know what could be the problem?

---

### Post by Peripheral Visionary on 2013-06-29
I think there has been some issue with later kernels conflicting with video drivers.  You can just use the older kernel that was working fine instead of the newer one that doesn't.  An older thread [here]("http://ubuntuforums.org/showthread.php?t=1524913") talks about using GRUB to boot from a previous kernel.

---

### Post by grahammechanical on 2013-06-29
> [COLOR=#000000]not be able to reboot[/COLOR]

Why? It is impossible to say because you fail to give any information about how it fails to boot. You need to describe what is happening. Otherwise we do not any a clues. And we cannot identify at what stage of the boot/loading process the error occurred.

Regards.

---

