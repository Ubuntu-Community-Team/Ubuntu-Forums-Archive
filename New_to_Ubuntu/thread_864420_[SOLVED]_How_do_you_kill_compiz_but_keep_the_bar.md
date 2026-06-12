---
title: "[SOLVED] How do you kill compiz but keep the bar?"
date: 2008-07-19
forum: New to Ubuntu
---

### Post by Bigbob22 on 2008-07-19
Compiz has been making my screen flash in full screen games, but when I kill it the bar that you use to move windows is gone. How do I kill compiz and keep the bar?

---

### Post by damis648 on 2008-07-19
Thats because you have no window manager or decorations. Press Alt+F2 and type
```
metacity --replace
```
to use metacity instead and
compiz --replace
```
to bring it back.
```

---

### Post by |{urse on 2008-07-19
run this in your terminal.

> metacity

if that doesnt work try this

> metacity --replace

---

### Post by |{urse on 2008-07-19
lawl too slow

---

### Post by Bigbob22 on 2008-07-19
Thanks it works fine except when i bring it back avant window manager's icons is on the to top right and the bar for that holds the icons is on the bottom where it is supposed to be

---

### Post by sub2007 on 2008-07-19
That happens a lot to me. The workaround I find works best is to press ALT+F2 (to bring up the Run Program dialogue) and that will reset the bar. You can then close the Run Program dialogue as AWN will have reset.

---

