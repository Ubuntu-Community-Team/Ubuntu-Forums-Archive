---
title: "Help!  New HP w2207h stopped display"
date: 2008-08-02
forum: New to Ubuntu
---

### Post by gkiteguy on 2008-08-02
I have a dual boot system with Windows XP. I installed a new HP w2207h today and initially it started at a reduced resolution, but upon adjusting the resolution up, then rebooting, I have no display at all. Does anyone have any help?

Thanks

---

### Post by jualin on 2008-08-02
If the problem is in ubuntu you need to go a terminal as soon as Ubuntu Boots up(CTRL+ALT+F1 when you log in and get no screen) and then run > sudo dpkg-reconfigure xserver-xorg This will reconfigure the xserver for you and should work if you had the display working before.

---

### Post by gkiteguy on 2008-08-04
> **jualin said:**
> If the problem is in ubuntu you need to go a terminal as soon as Ubuntu Boots up(CTRL+ALT+F1 when you log in and get no screen) and then run  This will reconfigure the xserver for you and should work if you had the display working before.

Super! It is a bit disheartening to see a resolution of only 800 X 600. I looked at the Xorg.conf and it didn't detect my graphics or the monitor. <sigh> I'll keep trying. 
Thanks.

---

### Post by gkiteguy on 2008-08-04
> **gkiteguy said:**
> Super! It is a bit disheartening to see a resolution of only 800 X 600. I looked at the Xorg.conf and it didn't detect my graphics or the monitor. <sigh> I'll keep trying. 
Thanks.

I think this is solved! I found another post that recommended to install the screens and graphic selector. 
"sys->prefs->main menu->other->screeens and grpahics and tick then select from the menu and selected my monitor from the list (A HP W2207)"

I got a resolution of 1024 X 768 which is fine for my purposes with a lot of selections. My graphics is an integrated NVIDIA GE Force2 which I had to specify as a Legacy. That will do until I build the new system when my wife isn't looking. 

Thanks:KS

---

