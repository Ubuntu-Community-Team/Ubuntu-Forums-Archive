---
title: "System shuts down since updates"
date: 2008-10-20
forum: New to Ubuntu
---

### Post by Vistawho? on 2008-10-20
Ok, so here's the thing.
I installed the latest updates (yesterday) as per the update manager and was told that I required a reboot.
When I tried to reboot, Ubuntu starts to load, and then my computer just shuts down (actually it doesn't turn off, I just get a message on the screen saying "No Signal".
I have a second HDD on which I have installed Ubuntu and it starts ok.
Does anyone have any suggestions?

---

### Post by iaculallad on 2008-10-20
It could just be something related to your xorg file: maybe a change in your refresh rate. You could just try checking that file using LiveCD as your boot media.

HTH.

---

### Post by ajgreeny on 2008-10-20
Just as a test, try booting to the previous kernel when the grub menu comes up.  If you are using 8.04, it may be the problem a lot of people have had following the new kernel.  If that does not work, try checking these forums and looking at the threads about the last kernel update and various solutions to that problem.  Finally it is just possible that the system kept a backup of the previous menu.lst file which you could restore using the live CD.  That might still work if you are lucky.

---

