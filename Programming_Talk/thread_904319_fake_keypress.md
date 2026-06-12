---
title: "fake keypress"
date: 2008-08-29
forum: Programming Talk
---

### Post by Okar on 2008-08-29
I'm looking for a possibility to fake a keypress of multimedia keys.
for example the program key_play creates an play keystroke.
Does anyone know how to do this?

can't find any multimedia keys in /usr/include/X11/keysymdef.h, are there no multimedia keysyms?

[http://www.thinkwiki.org/wiki/How_to_inject_fake_keystrokes](http://www.thinkwiki.org/wiki/How_to_inject_fake_keystrokes) describes how to fake a keystroke, but I don't know the keycodes of multimedia keys.

---

### Post by rangalo on 2008-08-29
I think you need to install xautomation package

then

[code]
xte 'key <keysym>'
[code]

where keysym is the keyseym you can get in xev by pressing that key.

[edit:] sorry, this works with bash, but may be there is also C/C++ API for this. 

regards,
Hardik

---

### Post by Okar on 2008-08-29
and what are the keysms for Play/Pause/Next/Previous (multimedia vise)?
or can I use those XF86 keysms too?

---

### Post by signifer123 on 2008-08-29
> **Okar said:**
> and what are the keysms for Play/Pause/Next/Previous (multimedia vise)?
or can I use those XF86 keysms too?

There are XF86 Keysyms for those too. 

Look at: /usr/share/X11/XKeysymDB

Here are ones I've used before.

XF86AudioLowerVolume
XF86AudioMute
XF86AudioRaiseVolume
XF86AudioPlay
XF86AudioStop
XF86AudioPrev
XF86AudioNext

---

### Post by Okar on 2008-08-29
ok great, thx

---

