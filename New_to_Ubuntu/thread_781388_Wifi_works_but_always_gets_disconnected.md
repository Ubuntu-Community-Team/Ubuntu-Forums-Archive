---
title: "Wifi works but always gets disconnected"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by smlgph on 2008-05-04
Hi. I have successfully installed 8.04 and the wifi works:
1) It can see the available networks (whether locked or unlocked)
2) There is a signal-strength bar

...but it always gets disconnected within just a few minutes while my other laptop on XP does not get disconnected.

Is there something I should do to stay connected via wifi?

---

### Post by volkswagner on 2008-05-04
If you have other wireless in your area, you may want to disable roaming mode to see if that helps.  You may also try a different channel on your router to avoid conflicts with neighbors.

---

### Post by joshsmith on 2008-05-04
do you have broadcom wifi?
could you name the wifi chip.
run lspci in the terminal will   give us the info we need to know what wifi card you have.

if someone doesnt suggest a simpler fix, check out some guides to use ndiswrapper to load you windows drivers to control the wifi on ubuntu, instead of the official linux ones. this works for a lot of people

---

