---
title: "gnome panel problem"
date: 2008-06-19
forum: New to Ubuntu
---

### Post by asaad399 on 2008-06-19
i;ve setup Ubuntu and it was doing well
now when i start ubuntu 
then desktop and icons appear
but up and down panels not
i repaired packages , reinstalled g-panels with no benefit
any solution??????

another bug

in another installation x-server logs off automatically after i log on 
but in failsafe not

---

### Post by vikramaditya on 2008-06-19
Re the panels, are you sure they are not set to "autohide"?  Try hovering your mouse cursor at the top or bottom edge of your screen and see if they show that way.  If so, then right-click the expanded panel, choose "properties" from the context menu, uncheck "autohide", and check "expand".

Re x-server, sorry . . . no clue! :)

---

### Post by asaad399 on 2008-06-20
how can i open synaptec manager????

---

### Post by sayakb on 2008-06-20
Goto System->Preferences->Sessions and click *Current Session* tab. Check whether the *Style* of gnome-panel is set to *Restart*. You may also add *gnome-panel* to startup by clicking Add button under the *Startup programs* tab. See if this helps.

---

### Post by kuvark on 2008-06-26
> **asaad399 said:**
> i;ve setup Ubuntu and it was doing well
now when i start ubuntu 
then desktop and icons appear
but up and down panels not
i repaired packages , reinstalled g-panels with no benefit
any solution??????

another bug

in another installation x-server logs off automatically after i log on 
but in failsafe not
hi... maybe  u can taste this...
ctrl+alt+f1   and login in konsol
and write this:
$ DISPLAY=:0 gnome-panel

i think u delete the panel..
so if u delete it... konsol tells you to install.. and install it.. then
alt+f7 to gnome 
restart;) it works i think

---

