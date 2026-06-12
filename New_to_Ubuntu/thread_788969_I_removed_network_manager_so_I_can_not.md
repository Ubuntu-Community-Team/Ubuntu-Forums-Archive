---
title: "I removed network manager so I can not"
date: 2008-05-10
forum: New to Ubuntu
---

### Post by captgadget on 2008-05-10
connect to the internet. Any suggestions on how I can reinstall network manager?

---

### Post by warbread on 2008-05-10
How did you uninstall it?  Can't you just reinstall through synaptic?

---

### Post by DieB on 2008-05-10
atleast you should have an ubuntu-cd somewhere, so insert that, then there should pop up a window askin you want to start packagemanager/synaptic klick yes and istall it again, if it is not in the cache anymore (means the post above didn't work)

hope that helps

---

### Post by captgadget on 2008-05-10
Reinstalled - solved

---

### Post by ugm6hr on 2008-05-10
> **captgadget said:**
> Reinstalled - solved

Solved for you - but for future readers, reinstallation is overkill.

The packages network-manager & network-manager-gnome need to be installed, and the systray applet can be run with:
```
nm-applet --sm-disable
```

---

