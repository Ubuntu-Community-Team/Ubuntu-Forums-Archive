---
title: "Ubuntu stops during startup"
date: 2013-06-19
forum: New to Ubuntu
---

### Post by Charles2531 on 2013-06-19
I had been running wubi for about two weeks and due to some issues, I decided to remove it, buy a blank CD, install it on there, and then set it up so that I could boot from both Ubuntu and Windows. I had no problem with that; it works fine.

At first, Ubuntu was running perfectly fine. Then I oddly ran into some system errors (which was not much of a problem when I was using wubi), and the package manager and several other programs began closing themselves shortly after I opened them. I checked the internet for solutions, went with what seemed to be the best solutions I could find, and ended up getting errors such as "Problem with MergeList/package lists or status file could not be parsed or opened" errors. I looked up ways to fix this, but when I tried them, they gave me the same error; the advice seemed to be like telling someone who's house was on fire that the best way to set it out was with gasoline, as it always seemed to require downloading a new update to fix the computer's inability to download files correctly. I decided to reboot the computer. Upon reboot, Ubuntu opened, but stayed at the purple startup screen; the whole Ubuntu text with the flashing dots underneath wouldn't show up even if I waited an hour. I looked up possible solutions to this, and I managed to get the terminal to open (ctrl+alt+f1), but nothing I could find would give me any results different to things I tried before.

Does anyone have any possible solutions?

---

### Post by justynt on 2013-06-19
You said you had terminal? try sudo apt-get update. then sudo apt-get upgrade.

---

### Post by Charles2531 on 2013-06-19
That was one of the things that I tried. I got the problem with mergelist/package lists or status file... error.

---

### Post by justynt on 2013-06-19
That sounds like something else, in my opinion i would do a fresh install, download the iso and run either a usb install or a disk.

---

