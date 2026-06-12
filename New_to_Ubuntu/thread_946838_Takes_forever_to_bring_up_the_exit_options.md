---
title: "Takes forever to bring up the exit options"
date: 2008-10-13
forum: New to Ubuntu
---

### Post by kl2bmark on 2008-10-13
Hi there, I have no idea where to start in order to figure out whats doing this, but when I click on the exit button to shut down my system, it takes about 20+ seconds to show up the options part (log off, standby, shut down) etc....

any suggestions?

---

### Post by Partyboi2 on 2008-10-14
Have you disabled "gnome-power-manager" in Sessions? It should be enabled you can check by System>Preferences>Sessions and make sure that "gnome-power-manager" is enabled.

---

### Post by kl2bmark on 2008-10-15
> **Partyboi2 said:**
> Have you disabled "gnome-power-manager" in Sessions? It should be enabled you can check by System>Preferences>Sessions and make sure that "gnome-power-manager" is enabled.
It was disabled, but re-enabling it did not solve the problem.
I use a desktop, not a laptop (if thats any information you need)

---

### Post by ajmorris on 2008-10-22
hi there,
firstly, has your ubuntu always done this, right from its initial install? And are you using a composited WM/DE? (i.e compiz)

But, we are going to trouble shoot your 'exit' button... can you please do the following :)  :
open up a terminal (Applications --> Accessories --> terminal  sorry if this is not the exact menu path, it should be something like this though...) Then run the following:
```
pkill gnome-panel
```
```
gnome-panel
```
then click on the exit button, and post here any output that is printed to the terminal.


AJ

---

