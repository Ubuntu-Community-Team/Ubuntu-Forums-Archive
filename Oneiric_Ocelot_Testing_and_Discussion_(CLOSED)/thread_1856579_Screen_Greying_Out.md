---
title: "Screen Greying Out"
date: 2011-10-08
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by pkg9991 on 2011-10-08
I found a bug in Ubuntu Oneiric Ocelot for the turning off, of the screen.
Please try this out and see if anybody does face the same issue..
When I go to the System settings and click on screen and change the "Turn Off After :" option to Never, the screen starts greying out on its own in just 1 sec as you leave your mouse or don't touch your keyboard or mouse.
It's like a hang state, unless either you move your mouse or press a key on keyboard 2-3 times..
It was really frustrating and I searched a lot for any help on different forums of ubuntu but all in vain.. I was using like that almost past 2 weeks.
Any-ways now I fixed it, just changed the Never option to 1 hour and the problem is solved.
This problem was caused after the 29th Sept. Updates.
So, is anybody else facing the problem?.. has the issue already been reported and fixed? please do let me know...

---

### Post by Quackers on 2011-10-08
Have a look here
[http://ubuntuforums.org/showthread.php?t=1855686](http://ubuntuforums.org/showthread.php?t=1855686)

---

### Post by mc4man on 2011-10-08
Make sure you're fully updated, preferably from the main or US server  - that bug was fix released
(the never option causing an almost immediate dim, ect.

---

### Post by pkg9991 on 2011-10-08
this bug has recently been added to launchpad
[https://bugs.launchpad.net/ubuntu/+source/gnome-screensaver/+bug/869401](https://bugs.launchpad.net/ubuntu/+source/gnome-screensaver/+bug/869401)
need some "This bug affects me too" for this to get fixed
Status of the bug is confirmed...
Please register guys for the bug if it's affecting you

---

### Post by pkg9991 on 2011-10-08
> **mc4man said:**
> Make sure you're fully updated, preferably from the main or US server  - that bug was fix released
(the never option causing an almost immediate dim, ect.

nope i don't think the fix has been released bro :(

---

### Post by mc4man on 2011-10-09
> **pkg9991 said:**
> nope i don't think the fix has been released bro :(

Been fine here since this fix released 2 days ago (there may have been another package upgraded also, forget
[https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/863038](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/863038)

Have had set to never since then, no issue as far as that bug


This one has only been partially fixed here - now show 0 instead of 600 but I still need to disable manually 
[https://bugs.launchpad.net/ubuntu/+source/gnome-desktop3/+bug/862139](https://bugs.launchpad.net/ubuntu/+source/gnome-desktop3/+bug/862139)

---

