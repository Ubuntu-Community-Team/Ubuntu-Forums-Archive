---
title: "Nvidia quit working after last update"
date: 2013-08-30
forum: New to Ubuntu
---

### Post by Autodave on 2013-08-30
Nvidia card was working great ubtil last night when I found some Nvidia updates pending in the UPDATE MANAGER.  Installed the updates and everything was fine until machine rebooted: now, just have black screen.

What do I do now?  I have the normal stuff come up before Xubuntu loads, but then just black: not even a flashing cursor.  I did remove the Nvidia card and rebooted and the onboard ATI kicked in and machine is running fine with that.

---

### Post by eternal243 on 2013-08-30
Well, I have experienced something similar about 2 years ago when trying to update my graphics drivers, it turned out the update worked fine, but that I hade forgot to run nvidia-xconfig after the update. X11 was still trying to display the contents of the screen with drivers that didn't exist. Can't tell for sure if this will solve your issue though.

---

### Post by ant2 on 2013-08-30
I had a similar problem after messing up xorg.conf 

You could try deleting etc/X11/xorg.conf
 
or, more sensibly, renaming it xorg.conf.OLD or something so it can be easily restored should you require.

---

