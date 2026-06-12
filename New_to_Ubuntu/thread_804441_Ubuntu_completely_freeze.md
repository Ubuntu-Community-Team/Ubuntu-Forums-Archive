---
title: "Ubuntu completely freeze"
date: 2008-05-23
forum: New to Ubuntu
---

### Post by wariskampar on 2008-05-23
Hello, 
I notice that my sys will complete freeze(any combination will not work!) when i deal with audio video file. I'll give two examples:
1) When I click any .avi files(especially on the first time), TOTEM (and subsequently my sys) will completely freeze. However,like I said this problem is just temporary. On the second time, it is OK
2) When listen music using Rhythmbox, my sys will freeze when I click on visualization. 
IN both cases, i have to reset my sys(Turn Off Completely) because no key combination(ctrl+alt+backspace, alt+f2, esc, etc) will work.(after have to Shut Off my laptop twice, I dumb Rhythmbox for Amarok)

I hope Compiz do not cause this problem because I love it!In XP I can easily ctrl+alt+delete to escape the situation.This problem really 'haunt' me because I migrate to Ubuntu for the promise of stability.

---

### Post by bluefrog on 2008-05-23
usually combination of "magic" keys will avoid a hard stop.

alt sysreq REISUB should "unfreeze" the PC. 
Stop at I and switch to console mode, login, sudo invoke-rc.d gdm restart and you should be back online.

---

### Post by wariskampar on 2008-05-23
REISUB?
Stop at I?

Are you sure combination will work because my keyboard was totally not functioning(during freeze).

---

### Post by bluefrog on 2008-05-23
try it

you push and keep pushed alt sysreq (the printscreen key) and you press one after the other the keys R E I S U B (basically SUB will make your computer stop and boot).

You can try now if you want to see what it does. Even if everything seems frozen, it should work.

of course it is not fighting the problem but giving you a way to have your PC back without rebooting or stopping it.

---

### Post by sayakb on 2008-05-23
Seems like a gstreamer problem. If you have VLC, just change the output module to X11 and play the AVIs in VLC.

---

### Post by wariskampar on 2008-05-23
OK, i will try this the next time my sys freeze. Thanks

@LinuxIsInnovation; i dont have VLC. but if this problem persist i will dumb TOTEM once and for all. (VLC is my default media player in XP!)

---

### Post by Andreas1 on 2008-06-28
same here

opening .avi in totem or vlc will in most cases freeze complete system
as you said: first time freeze, second time ok, that could be it, i'm not totally sure, but i pay attention next time
i also have compiz enabled, on hardy heron

---

### Post by wariskampar on 2008-06-28
I can confirm this problem. What is the alternative video player beside VLC and TOTEM. I am really piss off having to hard boot my system everytime it freeze

---

### Post by Andreas1 on 2008-07-26
I think it is a compiz problem, or at least compiz is involved. Since i switched compiz off (for it has too many bugs and my laptop is too old...) i have had no more problems with freezing.

---

