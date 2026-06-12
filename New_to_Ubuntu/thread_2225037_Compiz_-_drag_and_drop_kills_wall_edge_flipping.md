---
title: "Compiz - drag and drop kills wall edge flipping"
date: 2014-05-19
forum: New to Ubuntu
---

### Post by monkeybrain20122 on 2014-05-19
As the title says, in Ubuntu 14.04 drag and drop items into folder, across tabs or from dash to the unity launcher bar kills wall's edge flipping right the way and has to be re-enabled from ccsm. This used to happen in one of my 13.10 installations but the current 13.10 which is my main productive system doesn't have this problem. This manifests in 14.04 again booting off this very same machine. Graphic card is intel ironlake, with i915 driver.

At this point I am not looking for fixes,--compiz bugs apparently never get fixed,-- just wonder if there is a workaround.

---

### Post by monkeybrain20122 on 2014-05-21
Anyone?

---

### Post by monkeybrain20122 on 2014-06-12
Any theory? A work around or a 'me too'. Anything?

---

### Post by mc4man on 2014-06-14
I have to think it's the wall plugin. (for this & all your on & off issues with edge flipping
  I just put up a fresh 14.04 & before adding my builds, preferences, ect. tried edge flipping with wall which failed.
On the other hand rotate has no such issues, never breaks here & haven't had to disable auto-sorting in quite some time (at least since 13.10

---

### Post by monkeybrain20122 on 2014-06-14
Hi,

Interesting. I used to use cube and rotate until around 11.04 (iirc the cube wasn't even supported in 11.04) when It was totally broken then I switched to wall, rotate remained broken at least til 12.10, that was the last time I checked. I would check out rotate again but now  I am really used to wall, I didn't experience this problem in 12.04 or 13.04.

---

### Post by mc4man on 2014-06-14
i could never get used to wall, particularly with 'scroll on desktop' which I use alot.
(rotate is always linear, ie. starting on 1 -  12341234... or 43214321... ect where wall goes 1234(32)1 or 4321(23)4, ect.

At this point rotate works perfectly in all areas, here I altered unity's launcher expo icon to work with a 1x4 set up so it reflects current Ws - as in 
12
34

(- as far as your other sometimes issues with bindings disappearing that may have been fixed in 14.10's compiz, if so it should show up in 14.04 at some point. I run a slightly modified 14.10 compiz here now, this new install is to see if it creates any issue.

---

### Post by monkeybrain20122 on 2014-06-14
> **mc4man said:**
> 
(- as far as your other sometimes issues with bindings disappearing that may have been fixed in 14.10's compiz, if so it should show up in 14.04 at some point. I run a slightly modified 14.10 compiz here now, this new install is to see if it creates any issue.

Not sure what these updates will be but I recently got a unity upgrade (7.2.0 -> 7.2.1) which creates more problems for me. After that hot corners for scale is forgotten on reboot, also the desktop switcher on the unity launcher is only half working (click it once expose the desktops, but click again does not unexpose)

I downgraded it back to 7.2.0 and things work again.

---

### Post by adam-p on 2014-08-12
I'll give you a "me too", although the behavior for me seems a bit more erratic.  Through the 12s and 13s, I encountered a lot of problems with the edge flipping functionality not "sticking" after being enabled in ccsm.  Sometimes it would die after one flip, sometimes at some point seemingly at random.

Under 14.04, everything was more or less resolved. However, I have since moved to a new machine and to 14.10, and it looks like there's a regression.

---

### Post by monkeybrain20122 on 2014-11-09
Still drag and drop kills edge flip in 14.10

---

### Post by monkeybrain20122 on 2014-11-13
Hahahaha!! Problem solved! Open ccsm > Desktop Wall > Edge Flipping  and uncheck Edge Flip DnD and now drag and drop no longer kills edge flip! Not quite sure what Edge Flip DnD does (except that DnD means drag and drop, how could I miss it?)

I can't tell you how much this has bothered me. :)

---

