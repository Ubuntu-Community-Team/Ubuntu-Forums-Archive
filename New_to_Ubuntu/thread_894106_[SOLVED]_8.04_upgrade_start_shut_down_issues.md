---
title: "[SOLVED] 8.04 upgrade start/ shut down issues"
date: 2008-08-18
forum: New to Ubuntu
---

### Post by LTFC2020 on 2008-08-18
Hi
I upgraded to 8.04 from 7.10 yesterday
the install was far from smooth as there was a locale bug which I managed to get around using killall
when starting up for the first time I did sudo apt- get update/ upgrade and things looked Ok
however when I went to shut down I got a brown screen which hung indefinately until I manually shutdown by holding the off button
today on start up I have nothing but a black screen
any help appreciated

---

### Post by LTFC2020 on 2008-08-18
I went in through recovery mode and that worked but when I get to the desktop there is the following message

Error activating XKB configuration.
It can happen under various circumstances:
- a bug in libxklavier library
- a bug in X server (xkbcomp, xmodmap utilities)
- X server with incompatible libxkbfile implementation

X server version data:
The X.Org Foundation
10400090

If you report this situation as a bug, please include:
- The result of xprop -root | grep XKB
- The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd

and all the keyboard symbols are mixed up?!:confused:

---

### Post by meanburrito920 on 2008-08-18
What process did you use killall on?

---

### Post by LTFC2020 on 2008-08-19
one of the language locales - sorry dont remember exactly

---

### Post by LTFC2020 on 2008-08-19
again solvedish...
only a total reinstall with cd iso sorted it out
now to reinstall all my favourite packages and reconfigure my settings...:shock:

---

