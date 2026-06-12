---
title: "One screen blank when attempting multiple xscreens"
date: 2011-10-24
forum: New to Ubuntu
---

### Post by MrWeaver on 2011-10-24
Hi guys.

Spent a while Googling this problem, and I can't find anything satisfactory to answer it, so I hope it's not too much of a pain that I ask here.

I'm sat behind my shiny new workstation, and something I've been meaning to do for a long time is set up multiple monitors with their own, independent workspaces, rather than both changing simultaneously.

It seems people are talking about setting up multiple x screens, so I tried this. I used the nVidia manager that ships with Ubuntu 11.10 to configure the screens and they work great with twinscreen, but when attempting separate x screens I have screen 0 working normally with windows stopping at the edges, but screen 1 simply shows the desktop background, and the cursor becomes a thick "X" when I move over to it.

I'll attach images of the nvidia settings window which shows entries identical entries for screen 0 and 1, and my xorg.conf file.

Thanks a ton for any help, will try to provide anything extra I can if it would help.

---

### Post by MrWeaver on 2011-10-26
The answer to this one was that the new xscreen does not automatically start a window manager, but I don't know how to do this myself.

I'm now a Kubuntu user. KDE handles this stuff for you. Worked first time with the attached xorg.conf file.

---

### Post by Drowz0r on 2011-10-26
Hello there

I had a dual screens issue. What exactly does X screen do? Twinscreen is the same as extended desktop on Windows but I've not used the X screen function. When trying to enable it I get the exact same result as yourself.

---

