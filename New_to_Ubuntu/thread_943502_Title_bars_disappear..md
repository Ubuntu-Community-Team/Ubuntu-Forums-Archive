---
title: "Title bars disappear."
date: 2008-10-10
forum: New to Ubuntu
---

### Post by GameGuru on 2008-10-10
After installing compiz I lose all my title bars on windows.  It will be there then I will hover over them or something and it turns white and disappears fully or sometimes just half the bar.  A quick wiggle of the window brings it back but it is annoying.

---

### Post by sipickles on 2008-10-10
I believe this may help:

metacity --replace

See [http://ubuntuforums.org/showthread.php?t=917764&highlight=metacity](http://ubuntuforums.org/showthread.php?t=917764&highlight=metacity)

---

### Post by perlluver on 2008-10-10
Metacity will replace compiz, instead you will want to type, either ```
emerald --replace
``` or ```
gtk-window-decorator --replace
``` that will bring back the title bars.

---

