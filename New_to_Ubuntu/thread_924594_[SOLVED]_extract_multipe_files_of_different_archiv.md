---
title: "[SOLVED] extract multipe files of different archive types"
date: 2008-09-19
forum: New to Ubuntu
---

### Post by lolzlolz on 2008-09-19
hey, I was wondering if there is a way to extract multiple archives that are different types (some are zip and some are rar) all at once,
because it's quite  time consuming to extract each seperately.
thanks a bunch

---

### Post by MegaJim on 2008-09-19
You can try something like

```
find . -name "*.tar.gz"-exec tar -xvvzf {} \;
```

Queue up multiple searches / file types with the appropriate command for as many archive types as you are dealing with, e.g.

```
find . -name "*.tar.gz" -exec tar -xvvzf {} \;
find . -name "*.rar" -exec unrar e {} \;
find . -name "*.zip" -exec unzip {} \;
```

Or whatever archive progs you use

---

### Post by lolzlolz on 2008-09-25
thanks

---

