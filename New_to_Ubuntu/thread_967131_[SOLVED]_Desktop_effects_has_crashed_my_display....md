---
title: "[SOLVED] Desktop effects has crashed my display...how to turn it off?"
date: 2008-11-01
forum: New to Ubuntu
---

### Post by browny254 on 2008-11-01
Sorry for the quality of this post but im having to use my phones browser to post this because my display has crashed. I tried enabling desktop effects in kubuntu 8.10 but it has made all my windows just display in different shades of grey. I have a command line open though so how can i undo this. I have tried booting in failsafe mode but that isnt working either. I have to do it all blind so there has to be a way to do it that doesnt rely on me responding to things on the screen. Please help! Thanks.

---

### Post by Mazza558 on 2008-11-01
A very temporary and unusual solution would be:

> sudo aptitude install metacity

followed by 

> metacity --replace

Now effects are disabled you can then disable the option in the settings manager, and run

> kwin --replace

to get your kde borders back.

But there's probably a way to restart kwin without desktop effects.

---

### Post by browny254 on 2008-11-01
How big is that to download? I cant see whats happening in my terminal so i dont know when to do that second line...

---

### Post by Mazza558 on 2008-11-01
I can't imagine it'd be that big - it's gnome's window manager. Then again, it might be pulling in all the core gnome files as well.

---

### Post by browny254 on 2008-11-01
Hmm well i dont know what has happened now. I have tried that metacity replace and nothing has happened but i dont know if i even managed to get it downloaded or not. Is there anything else i can try?

---

### Post by jenee on 2008-11-01
do you run nvidia?

your graphics driver may not support the new X.org shipped 
with 8.10 so many people are having trouble with the drivers nvidia

if thats the case then
search [http://www.nvnews.net/vbulletin/forumdisplay.php?f=14](http://www.nvnews.net/vbulletin/forumdisplay.php?f=14)

drivers are being updated

---

### Post by browny254 on 2008-11-01
Yeah i do have nvidia so thats probably the problem but now that i activated the desktop effects and lost all my graphics how do i turn it off from the command line and return to default settings?

---

### Post by browny254 on 2008-11-01
OK. After a lot of very slow browsing on my phone I found how to turn off desktop effects and everything is now back to normal. I hope.

Anyway incase anyone else has this problem I did
```
nano home/username/.kde/share/config/kwinrc
```

Then under Compositing changed Enabled=true to Enabled=false

then saved and rebooted and all is ok.

---

