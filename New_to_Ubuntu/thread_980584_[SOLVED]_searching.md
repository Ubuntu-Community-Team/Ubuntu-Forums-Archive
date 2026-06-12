---
title: "[SOLVED] searching"
date: 2008-11-13
forum: New to Ubuntu
---

### Post by aszxcv on 2008-11-13
i have a file name HelloWorld.py in 
/home/ray/Desktop

but when i search for files in desktop it doesnt showup

this happpen for all my files i search for even when i search in the correct directory

---

### Post by nhasian on 2008-11-13
i like to use the *locate* command to search for things from the terminal.  Its super fast and the database is automatically updated every morning.  if you recently added files you can update the database manually with the command

```
sudo updatedb
```

---

