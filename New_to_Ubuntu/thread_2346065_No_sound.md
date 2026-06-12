---
title: "No sound"
date: 2016-12-10
forum: New to Ubuntu
---

### Post by filipe8 on 2016-12-10
I[COLOR=#1D2129][FONT=&amp]'m using Ubuntu 16.04 and my sound disapeared. I was on the "Sound Settings" (see the first attachment) where on the box "mode" I chose one of the 3 possibilities. After that there is no sound and no sound system appears on the "play sound through" box (se attachment 2).

It is interesting that if I logon as another user, every thing works well. [/FONT][/COLOR]

---

### Post by Yellow Pasque on 2016-12-10
Log in as problematic user and try resetting pulseaudio config:
```
rm -r ~/.config/pulse; pulseaudio -k
```

---

### Post by filipe8 on 2016-12-11
Thanks. Your solution works.

---

