---
title: "[SOLVED] Sound System No Longer Working in Ubuntu"
date: 2008-09-17
forum: New to Ubuntu
---

### Post by RedStarYellowSun on 2008-09-17
Hey! What's up?
I just started using some of the 3D strategy games and military simulators when I noticed that there were no sound effects whatsoever. When I restarted later, I found that, now, no sound came out of my speakers when I am in Ubuntu (even when it is on maximum setting). Ubuntu THINKS it works but it doesn't. The sound system still works in my Vista Business. Why is this? Is there some setting that has to be fixed? Should I uninstall the games and simulators? Is there something that can be done about it?

Thanks for your time.

Take care,
RedStarYellowSun

---

### Post by jbrown96 on 2008-09-17
Is it only in the games or all of Ubuntu? Are you using Wine to play the games? If so, check the settings in wine-cfg to see if the audio is set to Null or something strange. 
If the problem is system-wide, try ```
alsamixer
``` and check to make sure no essential channels are muted (if you unmute a channel and it doesn't work, remute it because it may cause hissing later).

---

### Post by markbuntu on 2008-09-17
You can look in the first part of my guide for some basic troubleshooting steps:

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by RedStarYellowSun on 2008-09-17
Thanks for your help! it's working again!

Thanks again!

Take care,
RedStarYellowSun

---

