---
title: "Lost all sound after partial upgrade on Hardy"
date: 2008-06-08
forum: New to Ubuntu
---

### Post by jamere on 2008-06-08
Hi all,
Upgraded to Hardy several weeks ago and it has been running fine with no apparent problems. A few days ago I was offered a partial upgrade from Update Manager, which I installed. Everything seems to be running fine with the exception of NO Sound capabilities at all now. I've never seen a "partial upgrade" offered before. All previous changes offered by Update Mgr have been very reliable in the past. I've noticed quite a few Hardy related sound problems in the forums. Is this a known glitch or what?
The kernel version I have is: 2.6,24-18

Anyone know if fixes will be coming through the channels for this problem? Any advice or suggestions much appreciated.
Jim M

---

### Post by jbrown96 on 2008-06-09
A couple of things to try. System-->Preferences-->Sound and mess with the sound playback device. Check ```
alsamixer
``` and make sure none of the playback channels are muted.
What type of sound card do you have? ```
lspci
```
What version of alsa do you have? Alsamixer should have a version number at the top.

---

### Post by jamere on 2008-06-09
jbrown,

Thanks for the reply and suggestions. Hard to believe, but the sound problem miraculously cured itself after booting. Not being one to believe in self-healing software (yet), I'm thinking that I must have neglected to re-boot after the partial upgrade by Update Mgr. I specifically remember seeing the re-boot icon after the changes were applied. So anyway, I'm betting the fault was mine.

I have an Intel sound card in a Dell desktop.

Thanks again for the help!

jim m

---

