---
title: "random logouts"
date: 2008-06-09
forum: New to Ubuntu
---

### Post by flowevd on 2008-06-09
weird problem here.

i just watched a video in totem, hit 'esc' to leave fullscreen, and found myself at a login screen having lost everything i had running before. this also happened yesterday when i tried to open a pdf in firefox. 9/10 times it all works fine.

anyone know what's going on?

---

### Post by Trail on 2008-06-09
It seems your X is crashing (the engine that draws the graphics on screen). When it crashes, by default it restarts itself, and presents you the login screen.

Do you have any gfx driver issues?

If you want to dig in a bit deeper, open the file /var/log/Xorg.0.log with a text editor and look for errors to determine what caused the crash.

---

### Post by flowevd on 2008-06-09
> **Trail said:**
> It seems your X is crashing (the engine that draws the graphics on screen). When it crashes, by default it restarts itself, and presents you the login screen.

Do you have any gfx driver issues?

If you want to dig in a bit deeper, open the file /var/log/Xorg.0.log with a text editor and look for errors to determine what caused the crash.

thanks for the response. there are no (EE) lines in Xorg.0.log - i guess it's only telling me about the present session, which obviosuly hasn't crashed yet.

now you mention gfx drivers... over the past week i've been dumped out of compiz for no apparent reason a couple of times. it restarts perfectly happily if i run fusion-icon.

---

