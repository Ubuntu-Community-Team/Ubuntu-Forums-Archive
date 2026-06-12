---
title: "Search Function Doesn't Locate Files"
date: 2008-11-03
forum: New to Ubuntu
---

### Post by leeraconteur on 2008-11-03
Ibex 8.10.
New install as of yesterday.

Search in Application Launcher never returns any hits.
I search for known apps - nothing.

How do I search my machine for files, folders, extensions, wildcards, etc?

---

### Post by taurus on 2008-11-03
Maybe something like

Applications -> Accessories -> Terminal
```
sudo find / -name bash -print
```

---

