---
title: "Ubuntu logs out when playing a video"
date: 2016-06-13
forum: New to Ubuntu
---

### Post by michael-91 on 2016-06-13
Hi,

When I watch a video in Firefox then Ubuntu logs me out after a time.
I have found a solution by changing "Turn screen off when inactive for" -setting in "Brightness & Lock Settings" to Never.

It would be good if Ubuntu was fixed, so that it is active when a video is playing in Firefox. The problem is that Ubuntu logs out when playing a video.

---

### Post by ian-weisser on 2016-06-13
"Inactive" usually means user input. The system has no way to tell if you are actually watching the movie, or have wandered off to make a sandwich or fallen asleep.

Since the system is not psychic, applications need to tell Ubuntu to when prevent sleep...and when to restore sleep when finished.
Please file a bug report with Firefox.

---

### Post by ashwin.kj on 2016-06-14
Hi 
You can install Caffeine [https://launchpad.net/caffeine](https://launchpad.net/caffeine). It is a status bar application able to temporarily prevent the activation of both the screensaver and the "sleep" powersaving mode.
```
sudo apt install caffeine
``` should do the trick. It is not a good fix, but for temporary solution.

---

### Post by michael-91 on 2016-07-04
> **ian-weisser said:**
> "Inactive" usually means user input. The system has no way to tell if you are actually watching the movie, or have wandered off to make a sandwich or fallen asleep.

Since the system is not psychic, applications need to tell Ubuntu to when prevent sleep...and when to restore sleep when finished.
Please file a bug report with Firefox.
Okay.

> **ashwin.kj said:**
> Hi 
You can install Caffeine [https://launchpad.net/caffeine](https://launchpad.net/caffeine). It is a status bar application able to temporarily prevent the activation of both the screensaver and the "sleep" powersaving mode.
```
sudo apt install caffeine
``` should do the trick. It is not a good fix, but for temporary solution.
Interesting application. The page says that it is a "untrusted PPA". 

Is it possible to see the code for a PPA application before installing it?

---

### Post by mc4man on 2016-07-04
> **michael-91 said:**
> Okay.


Interesting application. The page says that it is a "untrusted PPA". 

Is it possible to see the code for a PPA application before installing it?
Of course, ppa's are very transparent. If one is enabled then simply apt-get source package. Otherwise on any ppa page click on the "View package details" link, all build sources are available thru the dropdowns. Ex. for caffeine thru 15.04 - 
[https://launchpad.net/~caffeine-developers/+archive/ubuntu/ppa/+packages](https://launchpad.net/~caffeine-developers/+archive/ubuntu/ppa/+packages)
Additionally in those dropdowns are diffs from previous to current build.

Note that as of 15.10 caffeine is now in the official Ubuntu repos.

---

### Post by michael-91 on 2016-07-05
Okay. I have installed Caffeine and it is a nice status bar application. When I played a video in Firefox I could watch it and Ubuntu did not log me out. "Turn screen off when inactive for" was set for a period of time and after that time had passed the video was still playing.

---

