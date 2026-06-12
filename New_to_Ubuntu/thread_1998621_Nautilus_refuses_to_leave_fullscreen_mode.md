---
title: "Nautilus refuses to leave fullscreen mode"
date: 2012-06-07
forum: New to Ubuntu
---

### Post by blackbird34 on 2012-06-07
Thats it, really.  Naautilus starts up full screen, and refuses to leave it even with F11 (the keyboard shortcut. And as its Unity, i can't get at the menu bar any more.

---

### Post by blackbird34 on 2012-06-08
bump

---

### Post by traditionalist on 2012-06-08
It's a workaround, but useful for emergencies, and you might find yourself using it a lot! :)

[http://www.linuxnov.com/add-classic-menu-indicator-to-ubuntu-12-04-lts-precise-pangolin-panel/](http://www.linuxnov.com/add-classic-menu-indicator-to-ubuntu-12-04-lts-precise-pangolin-panel/)

Otherwise;

```
unity --reset
```

should get you back to defaults, but if you have changed anything you will lose it.

---

### Post by blackbird34 on 2012-06-09
I've had that indicator. That's not really the problem, as i can't get at the Unity panel when Nautilus is open. 
Doesn't ```
unity --replace
``` simply restart unity? There used to be a similar command for Compiz.

I've given up for now anyway and i just give the fullscreen Nautilus a workspace of its own. It's too good a file manager to loose.

---

### Post by Frogs Hair on 2012-06-09
Open the terminal and try to restart Nautilus.```
nautilus -q
```

---

### Post by blackbird34 on 2012-06-10
In the end I set up a new fullscreen command, using CompizConfig Settings Manager instead of the Keyboard Shortcuts utility, so really it was a window manager problem.

---

