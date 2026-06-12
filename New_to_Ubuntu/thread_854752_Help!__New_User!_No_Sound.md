---
title: "Help!  New User! No Sound"
date: 2008-07-09
forum: New to Ubuntu
---

### Post by Tujumaster on 2008-07-09
So this is quite a funny story.  I've been using Ubuntu for about a week now and everything was working fine up until today.  I had installed Adobe's Flash when I first installed the application and, due to sound problems, I had to download libflashsupport.  Ever since then, everything seemed to be working fine with the exception of intermittent sound problems using other applications.  Usually, a quick reset solves everything, but today, no applications produce any audio with the exception of flash and the startup Ubuntu sound.  

What I have tried is to uninstall libflashsupport to see if that would work, but I have still have had no luck.  But I do get the startup chimes still.  Anyone have any suggestions?  I'm quite a noob at this so please bare with me for a probably stupid question but I can't find anything about this anywhere.  Thanks for the help.

---

### Post by scragar on 2008-07-09
just because pulse audio has been the problem on 99% of sound complaints try killing it and seeing if you get sound back then, press alt+F2 and type:
```
killall pulseaudio
```
restart your media player or whatever and see if you have sound now.

---

### Post by zenzizenzizenzic on 2008-07-09
Try typing in alsamixer into a terminal and see if your volume levels are screwy if you haven't already.

---

### Post by Tujumaster on 2008-07-09
Thanks to you both for the information, but I still don't have any sound.  I can still get Flash but that's about it.  Any other ideas?  I appreciate your help sincerely.

---

