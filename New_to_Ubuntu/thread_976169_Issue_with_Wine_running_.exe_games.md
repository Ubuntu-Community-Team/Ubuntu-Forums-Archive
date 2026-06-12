---
title: "Issue with Wine running .exe games"
date: 2008-11-09
forum: New to Ubuntu
---

### Post by Darkeiya on 2008-11-09
I'm trying to run an .exe game that my friend made. I've installed Wine and it loads up the window just fine, but when it should show the title screen, all it does is come up with a bunch of glitchy-looking rectangles. I tried this with another custom .exe game and got the same results. Is there something I can do to fix this?

---

### Post by hyper_ch on 2008-11-09
wine will not run everything that is written for windows. if it's a self made program then can't even check the wine application database... I don't think that with more infos or the game anyone here can help you.

---

### Post by Durden on 2008-11-09
Probably not since they are custom games. You can go to winehq.com though and ask there for some help, there are settings in wine to emulate different versions of windows etc etc but since they are custom games, I really wouldn't count on it. Wine is just bad with 3d windows apps. The occasional one will run but often with a lot of tweaking.

Anyway, head over to winehq and see. Good luck.

---

### Post by Kellemora on 2008-11-09
Hi Dark

If the game makes any calls OUTSIDE the API it will not work in Wine.
You can ask your friend if he did this in this game or not.
Another thing you can try is put ALL of the dependencies the game requires into the folder you are running the game from.
For example, the old original JessBall game, requires the wep4util.dll file in order to run and the jessball.gid, the jessdead.wav for sound and if you want the jezzball.hlp file.
If you include those files in the Jezzball folder with jezzball.exe it will run just fine.  But without that wep4util.dll a whole lot of self-contained small games won't run at all.

I used to keep an old windows box around with bare minimum on it, just to test what dependencies games and programs required to run.  Interestingly, it's nearly every single game or program out there.
So good luck!

TTUL
Gary

---

