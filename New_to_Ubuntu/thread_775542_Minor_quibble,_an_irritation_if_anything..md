---
title: "Minor quibble, an irritation if anything."
date: 2008-04-30
forum: New to Ubuntu
---

### Post by chrispche on 2008-04-30
I have all the screensaver's installed included the config utility. Now and then if I leave my computer downloading or compiling. The screensaver crashes. Any idea's? It never happened on Gutsy.

I have an nVidia Gforce 8400 512Mb of Mem. 2 Gig of ram and Core 2. So plenty of resources there.

It's a rather annoying irritation.

---

### Post by hermes0710 on 2008-04-30
What do you mean by saying "it crashes"? Does the hole system become unstable? Or just you prompted with an error? (Sounds like your graphics card problem)

---

### Post by chrispche on 2008-04-30
The whole system halt's so I have to reboot. Unlikely to be a problem with the Graphics Card. Like I said never happened in Gutsy. Too much of a coincidence for it to be a fault with the sudden change over of versions.

Although in writing this it appears to have stabled out since the last update. Which had compiz updates in it. Could have been that.

I understand Hardy is new so I guess there's going to be a few corrections.

I'll see how it pan's out.

---

### Post by bilal.17 on 2008-04-30
It might have been that compiz was giving you some slight problems, and if its true that after you updated compiz and it now works, then it looks like that is the case.

---

### Post by Tux Aubrey on 2008-04-30
I did have a similar problem in gutsy - I had "random" screensaver selected but one particular screensaver called "Braid" would sometimes freeze on screen and I'd have no choice but to reboot.  If I opened the Screensaver gui and selected Braid, that would freeze everthing too.

The answer was to open gconf-editor from the command line, navigate to apps>gnome-screensaver and change the mode (dbl click) back to random. You can then quit and use the gui to select a particular (functional) screeny or turn it off altogether.

---

### Post by chrispche on 2008-04-30
Actually it's still happening. I have un-installed xscreensavers-extra and it seems to have fixed it. Funny that the GL extra screensavers are fine though. It seems the silly 2D savers are locking my machine. One would have thought the 3D intensive ones would have caused the problems. Anyway with that removed no more problems.

---

