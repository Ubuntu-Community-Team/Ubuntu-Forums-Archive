---
title: "[SOLVED] buggy video playback after hardy upgrade"
date: 2008-07-03
forum: New to Ubuntu
---

### Post by gorgon on 2008-07-03
Hi all,

After upgrading to hardy i cant play back most videos. That is, they play but the only colors are sharp red, blue and green (one color at the time), but mostly black. This happens in xine and vlc (the ones ive tried) with movie files (many different codecs) and DVDs.

Ive tried turning off compiz, if turning it off is selecting "no visual effects" in the appearance preferences.

Anyone have an idea or could point me in a direction id be very thankfull!

gorgon

---

### Post by RomeReactor on 2008-07-03
Hi. What video card do you have? Try the solution posted by myle in [this thread]("http://ubuntuforums.org/showthread.php?t=671994") (seventh post); if that doesn't help, try the solutions in [UbuntuGuide]("http://ubuntuguide.org/wiki/Ubuntu_Feisty#How_to_fix_black_windows_during_video_playback").

---

### Post by gorgon on 2008-07-03
> Try the solution posted by myle in this thread (seventh post);

ah, great. Using opengl as video output module in vlc solves it, for vlc at least.

out of curiosity - anyone know how to use opengl as output in totem/xine?

---

### Post by RomeReactor on 2008-07-03
See if you have a ~/.gnome2/totem_config file:
```
ls ~/.gnome2
```
If you do, try aamukahvi's suggestion [here]("http://ubuntuforums.org/showthread.php?t=158055") (third post).

---

### Post by gorgon on 2008-07-03
i dont have a totem config file on my system, however there's a xine config file in:
~/.gnome2/Totem/xine_config
~/.config/totem/xine_config

editing the ~/.config one solves it :D thanks!

---

### Post by RomeReactor on 2008-07-03
Glad you got it working! Please mark your thread as 'Solved' by going to 'Thread Tools' in the upper part of the page, so that other people with a similar issue can find the solution more easily.

---

