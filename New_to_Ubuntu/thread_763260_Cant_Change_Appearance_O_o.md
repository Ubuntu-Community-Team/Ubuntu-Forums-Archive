---
title: "Cant Change Appearance O_o"
date: 2008-04-22
forum: New to Ubuntu
---

### Post by necronzero on 2008-04-22
This is weird... I have an intel embedded 945G graphics card.
Everything was fine... I installed Wine, emule, and some other programs...
Then I added the extra effects on my desktop and it was working... so i decided to try the emerald themes.

I installed everything (except beryl-manager) (cause i cant >_> if anyone shows me how tnx... (ubuntu 7.10)

I managed to get the theme to work. I reboot my PC for updates n stuff and i didnt have the theme anymore, and whats worse, i cant even change my appearance now, evry time i click the extra effects button it tells me it cant change it.

I didnt care, I installed cedega and installed Guild Wars. to my surprise it said I cant run the game because i have no 3D acceleration.

Can someone show me how to turn on 3D acceleration on this graphics card?
Can someone tell me how to fix the desktop effects thing???

THANKS IN ADVANCE

---

### Post by SunnyRabbiera on 2008-04-22
well when you were playing around, did you install packages for compiz or compiz fusion?
There is a difference between the two and if you installed normal compiz stuff as opposed to stuff from compiz fusion then no wonder why you have issues.
Tel us what you have installed and we might be able to help.

---

### Post by -gabe-noob- on 2008-04-22
yea, the themes may matter, though I thought compiz and compiz-fusion themes could be interchangeible (since compiz-fusion is just compiz and beryl to my understanding) and I have an embended intell 945gm and games run very choppily, have you been able to run guild wars atall before this screw up, if so, how was it?

---

### Post by SunnyRabbiera on 2008-04-22
> **-gabe-noob- said:**
> yea, the themes may matter, though I thought compiz and compiz-fusion themes could be interchangeible (since compiz-fusion is just compiz and beryl to my understanding) and I have an embended intell 945gm and games run very choppily, have you been able to run guild wars atall before this screw up, if so, how was it?

No, you have to use one or the other, if you install the compiz themes they will freak out compiz-fusion.

---

### Post by -gabe-noob- on 2008-04-22
ooh, hmm well I never had this problem with my chip, maybe Its somthing like the xgl is not running (i read about that somewhere)
299 posts, does it only count as 300 if I post here? as in a support forum, not community cafe

---

### Post by SunnyRabbiera on 2008-04-22
Yes...
So say it...


THIS IS SPARTAAAAAAAAAAAAAAAAAA!!!!!!!!!!!!

---

### Post by leomelo on 2008-04-22
necronzero,let installed 'xserver-xorg-video-intel','xserver-xorg-video-intel-dbg'and 'xserver-xorg-video-i810' and uninstall all the other 'xserver-xorg-video-...'.This is to get direct rendering.

---

