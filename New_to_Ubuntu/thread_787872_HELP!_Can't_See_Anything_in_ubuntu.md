---
title: "HELP! Can't See Anything in ubuntu"
date: 2008-05-09
forum: New to Ubuntu
---

### Post by Ashmadai on 2008-05-09
Hi, I recently installed ubuntu and set up the compiz stuff, then activated the cube settings etc. everything was good. However, out of curiosity, in the original "cube" feature settings i moved the öpacity while not rotating slider, immediately after, i could not see any text or interfaces. just the empty windows and menus and background. I can still interact with everything but i just can't see where i'm going.

I need for somebody to take screenshots of each step of how to get to that screen again so i can set the slider back to 100.

Please, please, please. I NEED some files in my computer and can't access them. PLEASE!

---

### Post by hermes0710 on 2008-05-09
FAST: If you don't mind losing your compiz settings find compiz settings in your home folder and delete it
```
cd ~
find -name *compiz*
```

Locate the file with the settings and delete it.

SLOW: Find the compiz settings file and try to find an entry with name like "opacity" and fix it's value to 100

---

### Post by Ashmadai on 2008-12-07
Thank you. I solved the problem by blindly clicking through it. I couldn't see the menu though. The problem was that ADD helper compiz thing, grr. ADD helper...you were no help at all. Thank you hermes.

---

