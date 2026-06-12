---
title: "no sound in ubuntbu"
date: 2008-08-28
forum: New to Ubuntu
---

### Post by krikitos on 2008-08-28
i dont have sound in ubuntu and i cant realize how to figure it out any help?

---

### Post by halitech on 2008-08-28
open a terminal (Applications - Accessories - Terminal) and type in 
```
lspci
``` and post the info back here

---

### Post by kansasnoob on 2008-08-28
I would begin by installing gnome-alsamixer. You can either install from synaptic package manager or:

```
sudo apt-get install gnome-alsamixer
```

in terminal. It'll then show up in the menu under Sound & Video. Note mine:

[ATTACH]83131[/ATTACH]

[ATTACH]83132[/ATTACH]

---

