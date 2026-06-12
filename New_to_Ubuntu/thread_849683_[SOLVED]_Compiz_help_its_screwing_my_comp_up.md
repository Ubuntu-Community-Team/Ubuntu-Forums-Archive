---
title: "[SOLVED] Compiz help its screwing my comp up"
date: 2008-07-04
forum: New to Ubuntu
---

### Post by deadlySniper on 2008-07-04
I just need to know how to get compiz to turn off and uninstall it. I also need to know how to set it back to xfc

---

### Post by sayakb on 2008-07-04
Which version of Ubuntu are you using? Are you using XFCE? Then at a terminal, do:
```
xfwm4 --replace &
```

---

### Post by Dutch70 on 2008-07-04
put this in terminal to disable compiz, 

```
metacity --replace
```

to uninstall just use synaptic

Dutch

---

### Post by tjwoosta on 2008-07-04
the easiest way to get back to a working desktop if compiz is messing it up is just to login with safe-mode

there is a menu on the bottom left of the login screen, just choose safe mode

after logging in you can undo whatever you did to mess things up and restart in normal mode again

---

### Post by deadlySniper on 2008-07-04
thanks its back to mormal

---

