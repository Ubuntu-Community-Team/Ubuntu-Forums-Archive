---
title: "Removing shells"
date: 2014-05-29
forum: New to Ubuntu
---

### Post by gijs2 on 2014-05-29
Hi,

Is there a way to remove all my shells besides the ubuntu default shell?
Thanks :D

---

### Post by Frogs Hair on 2014-05-29
What shells are installed ?

---

### Post by gijs2 on 2014-05-29
> **Frogs Hair said:**
> What shells are installed ?

```
FVWM-Crystal
Fvwm
GNOME Flashback
Unity8-Mir
```

And Ubuntu Default but I want to keep that one.

---

### Post by Frogs Hair on 2014-05-29
Copy and paste/run the following in the terminal one at a time.```
 sudo apt-get remove --purge gnome-session-flashback 
``````
sudo apt-get remove --purge fvwm-crystal
``````
sudo apt-get remove --purge unity8-desktop-session-mir
``` ```
sudo apt-get autoremove
``````
sudo apt-get install --reinstall ubuntu-desktop 
```

---

### Post by gijs2 on 2014-05-29
That worked only Fvwm is still there.
But the rest is gone so thanks for that :)

---

### Post by Frogs Hair on 2014-05-29
You're Welcome , try the following.```
sudo apt-get remove --purge fvwm
```

---

### Post by gijs2 on 2014-05-29
> **Frogs Hair said:**
> You're Welcome , try the following.```
sudo apt-get remove --purge fvwm
```

It worked like a charm, cheers!

---

