---
title: "Titlebar in Ubuntu"
date: 2008-11-28
forum: New to Ubuntu
---

### Post by Nedimm on 2008-11-28
I have updated from Ubuntu 8.04 to 8.10 and after I have installed nVidia drivers my windows doesn't have title bar.
When I disable Visual Effects everything is ok

Here is picture:
[http://img379.imageshack.us/img379/6294/screenshotpg8.png](http://img379.imageshack.us/img379/6294/screenshotpg8.png)

---

### Post by Elfy on 2008-11-28
Open the run dialogue box - Alt+F2

Run this command and reboot

```
sudo nvidia-xconfig --add-argb-glx-visuals -d 24
```

---

### Post by Nedimm on 2008-11-28
Alt+F2 doesnt work.
It works when I disable Visual Effects
I have done that (sudo nvidia-xconfig --add-argb-glx-visuals -d 24) and enable Visual Effects, reboot but problem still exists.
My graphic card is Nvidia GeForce 8600 GT 
Resolution 1440x900

---

### Post by Kareeser on 2008-11-28
Ctrl-Alt-F2 instead.

---

