---
title: "Fix Broken packages...? add/remove software"
date: 2008-11-24
forum: New to Ubuntu
---

### Post by Gennn89 on 2008-11-24
Hey Just trying to update some packages but my computer shut off during previous installation due to stupid cheap battery anyways now it won't let me update any more packages until I fix my broken packages what do i do? I don't know which packages are broken

---

### Post by halitech on 2008-11-24
try opening a terminal and type this```
sudo dpkg --configure -a
```

---

### Post by bodhi.zazen on 2008-11-24
Are you getting a specific error message ?

Usually the error message will give a clue ;)

Post it here if you can

---

### Post by ajgreeny on 2008-11-24
usually I find it easiest to open synaptic and click the **Edit->Fix Broken Packages **menu item.  It has never let me down on the few times I have needed it.  You can see the details of what is going to be done by looking in the **Custom Filters - Marked Changes** in the left hand pane of the window.

---

