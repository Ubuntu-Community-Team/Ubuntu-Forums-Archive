---
title: "[SOLVED] Network Manager Icon disappeared?"
date: 2008-10-28
forum: New to Ubuntu
---

### Post by germanix on 2008-10-28
After updating my system today, and after the reboot, I noticed that the Network Manager Icon no longer made its appearance on the top right hand part of the panel. I am connected via Lan and I do have internet connection, so this is no real problem, but I would like it back. Had anyone had similar problems after todays update? Can anyone perhaps offer an explanation or advice how to get it back?

---

### Post by CatKiller on 2008-10-28
Normally when this icon disappears, it's because the Notification Area isn't there, which is easy to put back by right-clicking on the panel and selecting Add to Panel...

Not that I've updated today, or noticed it going recently.

---

### Post by germanix on 2008-10-28
The notification area is there. It shows the date and the volume control. By adding it to the panel as you suggested, just added a second one. I tried making it bigger in case it needs more space to show the Network manager Icon (although it showed up before in the same space) but I could not do this. I unlocked it from the panel and tried to drag it but it wont move.
No, the icon is just not there and I cannot explain it.

---

### Post by CatKiller on 2008-10-28
The date and volume control are different panel applets to the Notification Area. But since you've added it in with no effect, the icon's clearly not there. The two options I can think of are either that the update you did has added in an option to hide the icon (which would be nice) - or something's making Network Manager not start when you log in. Which doesn't stop the network from working.

I believe the command to start it manually is ```
nm-applet --sm-disable
``` You could run this command to see if the icon comes back, and if you'd like it to start each time you log in, you can add it to System -> Preferences -> Sessions.

---

### Post by germanix on 2008-10-28
Hi CatKiller, I found the answer to the problem. I did not use your code, but the second part of your advice led me to the solution. I had forgotten that yesterday I was reading a new book I had bought on Ubuntu, called "Beginning Ubuntu Linux". In this book the author suggested how to configure the start-up programs in "sessions" to start your system quicker. Well, as far as the network manager was concerned, he suggested that the network manager can be stopped from starting by un-ticking the box. This can be done in cases where the computer is static and has a permanent IP adress. I un-ticked it as this is my desktop pc and permanently has Lan connected over my router. I now ticked the box again and the icon re-appeared. You seem to like the icon not being there, judging from your comments above. So this is one way to get it not to appear. For laptops, moving around, this would not be a good thing however. I thank you for your help.

---

