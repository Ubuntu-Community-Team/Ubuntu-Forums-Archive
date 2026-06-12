---
title: "I get logged out soon after logging in (HELP :()"
date: 2008-04-22
forum: New to Ubuntu
---

### Post by dannytatom on 2008-04-22
As soon as I log in, it attempts to load my last session, then logs right back out (abouy 3 seconds max, not long enough to do anything).  It's been doing it all day, and I have no clue how to fix it.  :/

---

### Post by Ub1476 on 2008-04-22
Have you tried to log into failsafe gnome session? Did you install/modify anything when this happened? If it logs out after 3sec, I suppose it's a program which autostart, and crash Gnome..

---

### Post by dannytatom on 2008-04-22
Yeah, I've tried failsafe mode.  Also, the only big change I've made is setting compiz to remember/reload all apps and windows from the last session when I log in.

---

### Post by Ub1476 on 2008-04-22
Just a guess but, try to use session "failsafe terminal", then in the terminal run **ccsm**. Now uncheck that option. Remember Compiz is pretty much in Alpha/Beta stage for some people.

---

### Post by dannytatom on 2008-04-22
So going to terminal worked, and it did open the settings menu, but the font sizes are so large(at least 72px) and scroll the page vertically that I can't navigate it to uncheck/check anything.  :/

example (this would be the whole screen)
```

C       A
O       D
M       D
P       O

```

and it's impossible to scroll down it.  :/

---

### Post by dannytatom on 2008-04-22
If there's a way to completely remove compiz, I wouldn't mind going with that.

I tried *apt-get remove* compiz, but it didn't work. :x

---

### Post by Ub1476 on 2008-04-22
You can try to remove the configuration folder. It should be located somewhere in /home.

Probably ~/.compiz.

```
rm -dir .compiz
```

---

### Post by dannytatom on 2008-04-22
I did that and have restarted it a few times since, and it's still doing it.  :/

---

