---
title: "session problems, some help please"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by techno-mole on 2008-05-04
okay i have a small problem.

ive been messing around with stalonetray and awn and all things eye candy, which is going quite well, but, and ive tried to fix it myself, but i havent had much luck.

what ive done is remove the gnome-panel (you normally have one that cant be removed, but it can)

what i did (following something i found) was to open sessions, then select the middle tab (current session) then i found the gnome-panel entry and set it to " trash " then clicked apply (i left the sessions window open)

next i opened terminal and typed in killall gnome-panel (which shut down the remaining panel) i went back to the sessions window and selected the "session options" tab then i clicked the "remember currently running applications" and checked the "automatically remember running applications when logging out"

the idea was that by doing this when i restarted the gnome-panels wouldnt run, and i would have a panel im not using lying about the desktop.

but when i logged in i couldnt use have of the things on my system, i cant get alt + f2 to work, none of the menus on awn work, basically ive stuffed the system up.

i can log in and have a functioning system if i select failsafe gnome session at the login screen, but i cant fix the session i broke.

so how do i get rid of the broken session (if thats what you wnat to call it) and create a new default session (one that works) so i dont have to keep using the failsafe gnome session.

cheers

---

### Post by kellemes on 2008-05-04
Try removing /home/<USERNAME>/.gnome2/session

---

### Post by techno-mole on 2008-05-04
cheers, got it working now.
any ideas why removing the panels causes just about everything to stop working ?
none of the launchers work on awn if i remove the panels, and alt + f2 doesnt do anything either ?

do you have to have a gnome panel running to get the menus / launchers etc to work, like do they depend on something thats part of the panels ?

---

