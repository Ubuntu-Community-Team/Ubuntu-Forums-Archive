---
title: "Screenlets"
date: 2008-06-29
forum: New to Ubuntu
---

### Post by sundar261 on 2008-06-29
I have sysmonitor screenlet.  I have checked the "keep below" option.  But everytime I log in, it goes to the default option of "Keep above".  I have other screenlets which does not have this problem. 

Any help in solving this problem is appreciated.

-Sundar

---

### Post by PinkFloyd102489 on 2008-06-29
Try closing it out after you select that option, then starting the screenlet again.

---

### Post by sayakb on 2008-06-29
**_Workaround 1:_** Set it to **Keep Below**. Then goto System->Preferences->Sessions, click on **Session Options **tab and **Check** the *Automatically remember running applications... *checkbox.Now log out and login again. Now goto the Sys->Pref->Sessions and **Uncheck** the box.

_**Workaround 2:**_ Open a terminal and type:
```
rm ~/.gnome2/session
```And logout and login again.

---

