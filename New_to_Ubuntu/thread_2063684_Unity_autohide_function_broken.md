---
title: "Unity autohide function broken"
date: 2012-09-27
forum: New to Ubuntu
---

### Post by DanR01 on 2012-09-27
The Unity panel no long appears when I move the mouse over to the left of the screen. I can get it back briefly by pressing Super.

I've used Ubuntu tweak to set the hide mode to never.

Both unity and my graphics driver (NVIDIA 304.51) were updated yesterday which I'm guessing has broken the functionality.

I'll file a bug report with launchpad but does anyone have any suggestions on how to restore the autohide function? 

Thanks in advance

---

### Post by daslinkard on 2012-09-27
Have you tried resetting Unity?  You can do so with the following sudo command:
```

unity --reset
```

---

### Post by NikTh on 2012-09-27
> **DanR01 said:**
> 

I'll file a bug report with launchpad but does anyone have any suggestions on how to restore the autohide function? 

Hi , 
if you file a bug report then please give the bug link here. 

For your problem , try to search in ccsm , or myunity and/or appearance preferences and try to increase the sensitivity. 

I will subscribe to this thread so I can watch the developments , cuz I have at least 2 other users (local forums) with same problem after recently updates.

Thanks

---

### Post by NikTh on 2012-09-28
Yes , it is a Bug. Nvidia 304 and new Unity 5.16. 

[https://bugs.launchpad.net/unity/+bug/1057000](https://bugs.launchpad.net/unity/+bug/1057000)

---

### Post by DanR01 on 2012-10-06
For anyone still having problems a solution is available here:  [https://bugs.launchpad.net/unity/+bug/1057000](https://bugs.launchpad.net/unity/+bug/1057000)

 if no current /etc/X11/xorg.conf then create one with this in it
 Section "Device"
  Identifier "NVIDIA GeForce"
  Driver     "nvidia"
  Option     "ConstrainCursor" "no"
EndSection


 If there already is an xorg.conf with a device section then just add a line line in the section
 Option     ConstrainCursor" "no"

---

### Post by fmmarzoa on 2012-12-03
That workaround didn't work for me.

Ok, my problem was different. For some reason autohide had been disabled after 12.04 update.

---

