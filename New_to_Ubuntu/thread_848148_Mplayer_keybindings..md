---
title: "Mplayer keybindings."
date: 2008-07-03
forum: New to Ubuntu
---

### Post by ethoxyethaan on 2008-07-03
I deleted the content of "input.conf" file in /usr/share/mplayer

then made a file in ~/.mplayer called input.conf and added my own key bindings...

example Button X skips 2 seconds forward by default 
BUT even tho i deleted all the setting button X still skips 2 seconds in m player.

it gets more odd because: i get the following output on verbose...

```
No bind found for key 'MOUSE_BTN3_DBL'.                         ?% 0 0 
SEEK: i=29388 (max:29411) dpos=9813139 (wanted:9813146)  ??% ??,?% 0 0 
SEEK: idx=29388  (a:29388 v:29411)  v.skip=11  a.skip=7/0.000  

```

if i set MOUSE_BTN3_DBL to volume up: it will work but it will skip 2 seconds forward as well. Help appreciated.

---

