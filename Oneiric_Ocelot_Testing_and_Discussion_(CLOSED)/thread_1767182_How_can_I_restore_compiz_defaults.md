---
title: "How can I restore compiz defaults"
date: 2011-05-25
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by kansasnoob on 2011-05-25
I was futzing around this AM and hosed my compiz settings to the point I no longer have anything but a blank desktop :redface:

I can however launch a tty, or I could chroot the bugger, but I know less than nothing about compiz.

Is there a command that would restore all oem compiz/unity settings?

I promise not to break it again for at least an hour :)

I did try just purging and reinstalling the package "compiz" but that didn't do the trick, too many libs I suspect.

---

### Post by Framli on 2011-05-25
*unity --reset* restores default Unity & Compiz settings.
*unity --replace*, *compiz --replace* and *unity* do the same thing: they restart Compiz.
*unity --reset-icons* restores default launcher icons.

---

### Post by kansasnoob on 2011-05-25
Thanks, I generally just play with unity-2d (or the classic DE) but I decided to give compiz another whirl :)

And I'm trying to leave this as pure as possible ATM, only minimal package changes, no PPA's, etc. No better way to see how the default works for me.

I expect to see lots of new packages before Alpha1 iso-testing so I wanted to get a general feel of things before then.

---

