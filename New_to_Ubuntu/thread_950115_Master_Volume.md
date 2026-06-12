---
title: "Master Volume"
date: 2008-10-16
forum: New to Ubuntu
---

### Post by liuzerus87 on 2008-10-16
I just installed Kubuntu 8.10 on a Thinkpad T400 with an Intel sound card. The master volume right now is set to the PCM channel, which is fine, except the PCM channel doesn't seem to affect the volume coming out of the headphone jack. The other solution I tried was setting the master channel to the front channel, which I believe is the headphone jack, but then when I set the volume buttons (through Keyboard Shortcuts) to change the front channel, they don't work. Any ideas?

---

### Post by Mark_in_Hollywood on 2008-10-16
Open a terminal. Applications/Accessories/Terminal.

at the prompt 

mark@Lexington-19:~$ (you will see a different xxx@yyy than mine)

type

alsamixer

use the cursor arrow keys to move the settings around

if that solves the problem, please come back to this thread and mark it as SOLVED.

---

### Post by liuzerus87 on 2008-10-16
Thanks Mark. Using AlsaMixer, I confirmed that the front channel is the master channel. However, my volume buttons seem to only work on the PCM, even after I go into System Settings -> Keyboard & Mouse -> Keyboard Shortcuts -> KMix and changing the shortcut to the Front channel. Any ideas, or is this a KMix issue? Thanks again.

---

### Post by aktiwers on 2008-10-16
In Gnome you can go to System => Preferences => Sound

And change the last one to Master. I guess this is not much help for you in KDE?
Sorry I am no KDE user..

---

