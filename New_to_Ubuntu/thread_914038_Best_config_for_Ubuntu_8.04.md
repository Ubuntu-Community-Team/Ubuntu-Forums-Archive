---
title: "Best config for Ubuntu 8.04"
date: 2008-09-08
forum: New to Ubuntu
---

### Post by tiredbywindows on 2008-09-08
Hi, I'm an absolute newbie, I just want to know what is the recommended config to get the best result with "Hardy Heron". I installed it on an HP with AMD XP 2000+(1.67GHz), nVidia GeForce4 MX 420, 256 Mo RAM(DDR PC2100), HD 40 Go, Ethernet card 10/100 BT. As a matter of fact it works for every piece of the soft, but I find it somehow sluggish and slow. I ordered 1 Go to replace the existing one but I'm not sure that it will correct that slow way of working. Anyone get an explanation for this and could say if my plateform is ok for this ubuntu distribution?
Thanks for all infos.
D."Tiredbywindows"

---

### Post by MegaJim on 2008-09-08
You say you have 256mb of ram, if that is system ram (as opposed to graphics card ram) that would indeed slow it down.

As regards the speed, 1gb should be plenty for all the standard internet/email/video/music type things, of course it does depend what sort of programs you want to execute, but in general 512mb is enough for a simple internet/email ubuntu install

---

### Post by Oldsoldier2003 on 2008-09-08
As MegaJim stated, the most likely reason is the low amount of system ram. Once you have upgraded your ram you should be fine. If you are interested in trying low memory alternatives until you get more memory, feel free to post a new thread.

---

### Post by tiredbywindows on 2008-09-11
Many thanks for the advice, I was sure that my RAM amount was a bit low, so when I'll receive the ordered giga, I'll come back to give the results.
Friendly.
D.Tiredbywindows.

---

### Post by gregphil on 2008-09-11
Ubuntu also defaults to NOT using the true nVidia drivers and instead using a much slower open-source version of video drivers (to remain "pure")

However it is easy to tell ubuntu to go ahead and download the real nVidia drivers (and use them) even though they are not true "open source".

You can check or change this setting in the ubuntu 8.04.1 menu System==>Administration==>Hardware Drivers

---

