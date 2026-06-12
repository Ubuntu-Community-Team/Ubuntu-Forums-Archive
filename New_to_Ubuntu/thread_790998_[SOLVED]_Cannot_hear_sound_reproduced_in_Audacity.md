---
title: "[SOLVED] Cannot hear sound reproduced in Audacity"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by sdim on 2008-05-11
Hi,everyone.
It's been some days now that I can't hear any sound when I play songs on Audacity.The meter is displayed normally and The songs play normally on Amarok and any other application,but not on Audacity.It's been a problem as I want to edit a few songs,but I can't hear them...
Any help would be considered valuable.
Thank you.

---

### Post by sdim on 2008-05-13
Solution found.

---

### Post by nothingspecial on 2008-05-13
What is it `cause I`ve got the same problem.

---

### Post by redbob on 2008-05-13
One of the problems from Audacity is because it doesn't share sound with other sound makers, like Amarok and Totem. If you close all other sound makers, reopen Audacity and you'll hear the sound!

---

### Post by sdim on 2008-05-13
In my case,the sound source (below the PLAY and the other buttons),the drop-down menu with the little speaker on the left,was set to "digital" whereas it needed to be set to "analog",which was my sound card.
The manual says that almost always,the sound source and the other drop-down menu on the right with the microphone on the left of it,have to be set to the same settings,as source and recording are achieved through the (one and)same sound card.
I agree with redbob:it may be that if you play something through Audacity and open something else with,e.g. Amarok,the sound card may be occupied with that,so it opens the song file,but sound cannot be heard.

---

