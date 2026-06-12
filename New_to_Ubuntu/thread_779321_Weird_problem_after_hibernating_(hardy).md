---
title: "Weird problem after hibernating (hardy)"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by wheels. on 2008-05-02
Just tried hibernation out on my laptop ( see sig for specs)
It worked!! or so I thought, upon coming out of hibernation everything was black, big deal I thought, so I restarted.
Logging in I get my awn dock show up and compiz is working, I can rotate the cube, but there is no dekstop background, its just black, no panels, can't open any programs, nothing! so I went to failsafe gnome and just unchecked some things from starting up and then logged back out and tried my normal session, nothing changed!
I have zero idea what to do, It seems like gnome doesn't start its just sort of compiz fusion running and thats it, or so it seems to me anyway.

any help or ideas are much appreciated!

---

### Post by jimv on 2008-05-02
Try resetting your settings like this:

press control+alt+f1 to drop to a command line

type
> 
mv ~/.gnome ~/.gnome_old
mv ~/.gnome2 ~/.gnome2_old

That will reset all the gnome settings to default.

---

### Post by wheels. on 2008-05-02
Thanks, but it fixed itself after I shutdown for a while.

---

