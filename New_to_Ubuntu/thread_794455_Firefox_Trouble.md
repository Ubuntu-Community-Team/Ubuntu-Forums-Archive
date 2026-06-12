---
title: "Firefox Trouble"
date: 2008-05-14
forum: New to Ubuntu
---

### Post by mr-Kirch on 2008-05-14
When i open up firefox it is in full screen and my toolbars with applications etc. are gone and my bottom toolbar is gone..there is also no minimize, maximize, or close buttons!help

---

### Post by shifty_powers on 2008-05-14
firefox3beta5 or firefox 2?

---

### Post by Thingymebob on 2008-05-14
Sounds like firefox is running in some sort of kiosk mode try opening in safe mode, from a terminal type```
firefox -safe-mode
```
disable all your add-ons & plugins and restart firefox. Re-enable them 1 at a time.

---

### Post by bumbleskull on 2008-05-14
based on what you are saying, it sounds like you are stuck in full screen mode, so try hitting F11 to get out of it.

if it is more than that, Thingymebob's solution should work. If it doesn't you could make a new profile and start over (or copy your history/saved passwords/etc into the new profile) and reinstall/setup everything

---

