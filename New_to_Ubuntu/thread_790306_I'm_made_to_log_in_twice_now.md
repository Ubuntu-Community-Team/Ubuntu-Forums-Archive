---
title: "I'm made to log in twice now"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by gottabeandrew on 2008-05-11
It used to work like normal when i logged in with just making me log in once but it changed a few days ago and now i have to log in, it goes to one of those white writing on black background screens then it gets me to log in again. Why?

I'm running ubuntu 8.04 and installed it with wubi.

---

### Post by SunnyRabbiera on 2008-05-11
you mean its having you log in with a terminal correct?
maybe GDM is having issues, but lets check.

did you install any updates or change anything recently on your system?

---

### Post by gottabeandrew on 2008-05-11
I've only had it a week. So yes, loads of stuff. Both times it makes me log in, it's the proper log in screen.

---

### Post by SunnyRabbiera on 2008-05-11
Hmm, then it might be GDM (your log in manager)
you may want to try another log in manager like KDM, getting it is easy by going up to system then to administration and into synaptic.
synaptic is very easy to figure out once you see it, use its search to search for kdm, and once it finds it install it (but DONT install the kdm for kde4, it sucks)
mark kdm for installation by right or left clicking on the box next to the name and selecting "mark for installation"
and go to "apply"
the rest should be very strieghtforward, and when it prompts you to choose between gdm and kdm you have a little pulldown menu to choose...
like I said it should be easy to figure out.

---

### Post by gottabeandrew on 2008-05-12
Ok, i installed that but now it isn't straightforward at all. It's installed and i now have absolutely no clue where to go next. I can't see a KDM option in the menus or anything. Assistance please. :-)

---

### Post by oilfan22 on 2008-05-16
I was having the same problem.
I just went into the synaptic package manager, did a search for "gdm", clicked on it and selected "Mark for Reinstallation".
Then I restarted, chose "select session" from the options menu at the login screen, and selected gnome. It then asked me if I wanted this to be default. I said yes. I then logged in as normal and only had to log in once.
(I wanted to use gdm and not kdm)

---

