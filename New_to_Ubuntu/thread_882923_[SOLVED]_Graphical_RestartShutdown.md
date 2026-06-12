---
title: "[SOLVED] Graphical Restart/Shutdown"
date: 2008-08-07
forum: New to Ubuntu
---

### Post by diego898 on 2008-08-07
Now when I shutdown or restart its all text based. There is no more ubuntu screen with the bar moving backwards. Any ideas?

---

### Post by Majorix on 2008-08-07
That might be due to an error/warning during the boot. If that's the case Ubuntu breaks out of the splash animation to the console.

Carefully observe what FAILs and look for a way to fix it.

---

### Post by diego898 on 2008-08-07
booting up is graphical though, so can the error be there?

---

### Post by z.s.tar.gz on 2008-08-07
I would say no, as when I have errors booting it goes into the console.
Like Majorix said, I would watch for anything that fails (it says [fail] on the right-hand side) and post back.

---

### Post by ajgreeny on 2008-08-07
This is a known bug with gdm, I think.

Go to System>>Administration>>Login Window and on the second tab (Local) change the theme, then change it back again.  Now in the first tab (General) click the "Edit Commands" button at the bottom and you will see a drop down dialog.  In the Shutdown part of that, highlight the text that shows, right click it and copy then delete, then paste it back.  Now close Login Window down and I suspect you will get the usplash when you next login, as you did before, and also when you logout.  Weird, I know but it worked for me, and I found all this info somewhere in the bugs info on this forum, I think.

Good luck.

---

