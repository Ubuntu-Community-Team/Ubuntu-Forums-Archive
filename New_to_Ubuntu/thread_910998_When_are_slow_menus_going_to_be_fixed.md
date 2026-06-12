---
title: "When are slow menus going to be fixed?"
date: 2008-09-05
forum: New to Ubuntu
---

### Post by tjajab on 2008-09-05
I am experiencing slow menus when I use multiple screens, since Hardy came out. It can be fixed, by applying the following patch when the system has started:
```
DISPLAY=:0.0 compiz --only-current-screen --replace &
disown $!
sleep 3
DISPLAY=:0.1 compiz --only-current-screen --replace &
disown $!

```

I still have to use this, more than four months after the Hardy LTS release.

My question is, as many users are using two screens, why doesn't this bug(?) get fixed, so that new users doesn't get scared away from Ubuntu?

---

### Post by kalesh7 on 2008-09-05
umm I don't have the answer to your question but
have you filed a bug report? if not then doing so may help get it fixed faster.

---

### Post by Too Late on 2008-09-05
Well, there are [46213](https://bugs.launchpad.net/ubuntu) open bugs in Ubuntu... :roll:

---

### Post by Saint Angeles on 2008-09-05
i'm not sure if this will help, but you can add this line to your theme's gtkrc file:
```
gtk-menu-popup-delay = 0
```this has helped my menus pop up fast

or, sometimes the line is already in there like ```
gtk-menu-popup-delay = 50
``` in which case, just change the value to "0"

---

### Post by Elfy on 2008-09-05
I think it's a nvidia/compiz thing with more than one screen - I have a similar script in sessions for when I run gnome.

Not sure who's bug it is though...

---

### Post by jimmy the saint on 2008-09-17
according to the launchpad bug report, the fix should be incorporated into ibex.

---

