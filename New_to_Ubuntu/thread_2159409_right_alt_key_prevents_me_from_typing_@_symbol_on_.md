---
title: "right alt key prevents me from typing @ symbol on a german keyboard"
date: 2013-07-03
forum: New to Ubuntu
---

### Post by innn on 2013-07-03
On a german keyboard that symbol is typed with R_Alt+q
and I have this in .bashrc for switching layouts:
```
setxkbmap -option grp:switch,grp:alt_shift_toggle "de,us,ro(std)"
```
meaning I guess that I switch languages with L_Alt + shift but as I said pressing R_Alt also does this preventing me from typing specific keys
How do I disable that
I am using lubuntu 13.04 I have keyboard switch indicator in lxpanel allowing me to see that pressing R_Alt key switches from one language to another.

---

### Post by HermanAB on 2013-07-03
Howdy,

You may be able to tweak things using xev and xbindkeys.  I would use the useless Windows key if there is one. Worth a try anyway.

---

### Post by innn on 2013-07-03
ok, but before going that route is there sth wrong with the way I change layouts ?
Why R_Alt key changes them ? 
Why deleting key layout switcher form panel leaves me with a two items only start menu: run command and logout ? This may be another thread starting point I know.

later edit:
ok now I discovered that **keyboard layout handler** applet had this radio button called*** keep system layouts ***
that if unchecked I could proceed to add layouts right there from the applet and with the preferred shortcut
 no need of editing **.bashrc** or** /etc/xdg/lxsession/Lubuntu/autostart**.
Right Alt key behaves now as expected no interference anymore
I guess this should be the preferred way of adding layouts for anyone that likes ot have visual indicator in the tray and not messing with config files.
sorry to bother.

---

