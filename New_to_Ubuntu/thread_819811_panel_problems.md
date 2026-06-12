---
title: "panel problems"
date: 2008-06-05
forum: New to Ubuntu
---

### Post by bob16 on 2008-06-05
i am not new to ubuntu.

a few weeks ago, my panels dissapeared! i couldnt get them back so i just reinstalled ubuntu (for other reasons too).

today, i tried to reconfigure my panels and the both dissapeared! again

i tried restarting alot of times but now theres only 1 (the top one) and theres nothing on it. its just white and i cant even right-click on it.

i tried typing gnome-panel in terminal but it says theres already a panel running so i rly dont know what to do.

what should i do?

---

### Post by sayakb on 2008-06-05
Try:
```
killall gnome-panel
gnome-panel &
```

---

### Post by PinkFloyd102489 on 2008-06-05
In the terminal:

```
sudo killall gnome-panel
```

Then in Alt+F2:

```
gnome-panel
```



EDIT: Sniped. ;-)

---

### Post by bob16 on 2008-06-05
> **LinuxIsInnovation said:**
> Try:
```
killall gnome-panel
gnome-panel &
```
thanks alot man

IT WORKED!!!

btw are you a developper?

---

