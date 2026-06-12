---
title: "[SOLVED] Killing an errant application"
date: 2008-05-22
forum: New to Ubuntu
---

### Post by rabidninjawombat on 2008-05-22
Need a bit o' help here.. What is the way to kill an errant application (ala alt+f4 in windows)  This has happned a couple times to me where a full screen application will go crazy,and cant alt-tab outa it. Thanks in advance.

---

### Post by shifty_powers on 2008-05-22
right click on your top panel, add to panel and select force quite.

to run it otherwise, alt+f2 and then enter gksudo xkill ;)

---

### Post by KingTermite on 2008-05-22
In gnome, alt+F4 should work same as in windows.

Another alternative is to kill it from a terminal window. Open up a terminal window and type "ps" to show the running processes (command line version of task manager sort of). When you identify the process, type "kill %%%" where %%% is the process number.

---

### Post by rabidninjawombat on 2008-05-22
Thanks for the info!

---

### Post by shifty_powers on 2008-05-22
no probs, happy to help ;)

---

