---
title: "Wallpaper keeps changing on reboot."
date: 2013-04-28
forum: New to Ubuntu
---

### Post by SpongeBob SquarePants on 2013-04-28
The subject line says it all, I can't change the wallpaper. Well, I can -- it changes and holds for that session, but when I reboot it reverts back to the default distro wallpaper. 

Even if I change it and log out, it holds as far as the log-in screen, but when I put in my password and hit enter, again, it reverts back to default.

Any ideas? I'm running Xubuntu 13.04.

---

### Post by ajgreeny on 2013-04-28
Is the image you are changing to in a system accessible folder all the time, or could it perhaps be in a folder that is not mounted, for example, when you login or reboot?

---

### Post by SpongeBob SquarePants on 2013-04-28
Yes, all the images are in /usr/share/XFCE4/backdrops. Out of curiosity, I copied an image to my home folder, set it as a background by right clicking on the desktop, then desktop settings, rebooted, and it held until after I logged in for about two seconds, and then flipped to the default again.

---

### Post by SpongeBob SquarePants on 2013-04-28
Problem solved. A program called Dynamic Walls was overriding the manual setting. I simply stopped it from running in Sessions & Startup, rebooted, and the wallpaper doesn't switch any more.

---

