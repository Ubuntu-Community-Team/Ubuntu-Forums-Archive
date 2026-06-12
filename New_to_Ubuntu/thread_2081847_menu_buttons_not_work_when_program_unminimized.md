---
title: "menu buttons not work when program unminimized"
date: 2012-11-07
forum: New to Ubuntu
---

### Post by monkeybrain2012 on 2012-11-07
Hi,

I am using Ubuntu 12.04 and I have noticed a strange behaviour of the launcher. For some applications docked to the launcher the menu buttons (or some of them) stop working when the program is minimized and then unminimized (by clicking the icon on the laucher) For example, launch smplayer by clicking on the icon on the launcher, check that the buttons "Open, Play, Options ..etc" all work, minimize it, then restore it by clicking the launcher icon, some or all of the menu buttons stop working (click and no response) sometimes this happens right the way, sometime it happens only minimize and unminimize twice.


This seems to happen only to a few programs (e.g smplayer, vlc and rstudio) while others are fine. Can someone please test and confirm this? (or tell me that this doesn't happen so it may be something in my configuration) Thanks.

---

### Post by monkeybrain2012 on 2012-11-08
Just checked that this doesn't occur in 12.10. Hi people I am not necessarily asking for a fix at this point. I am only asking if anyone can confirm this behaviour so that I can decide whether to file a bug or not. 


If you are running 12.04 with Unity all you need to do is to lock Smplayer or vlc  to the launcher, start it, minimize it, unminimize it several times and see if the menu buttons work. Not a very difficult thing to do. :) Thanks.

---

### Post by monkeybrain2012 on 2012-11-09
Bump!

---

### Post by monkeybrain2012 on 2012-11-11
Well all I am asking is if anyone can reproduce this by minimizing and unminimizing an application and no one has bother to do this.

I know the answer now, this turns out to be yet another Unity bug, which has been fixed in 12.10. [https://code.launchpad.net/~aacid/unity/ignore_unmapped_on_minimize_unminimize](https://code.launchpad.net/~aacid/unity/ignore_unmapped_on_minimize_unminimize)

Guess I will just have to wait for a new version of Unity to be backported to precise in 12.04.2

---

