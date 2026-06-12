---
title: "A way to change runlevel"
date: 2007-04-24
forum: Programming Talk
---

### Post by energiya on 2007-04-24
Does anyone know a way to put together a script or gcc program to:
1) run some commands (save some status)     .....not a problem
2) switch from init 4 to init 3                          .....not a problem
3) run some commands (save some status)   .....problem
4) run a script (the hibernate script)             .....problem

A standard script running in a terminal window will execute steps 1 and 2 and then die (quite normal). The thing is I never programmed for linux (only for windows in linux). Could someone help me running step 2 and the next one work?

---

### Post by Tuna-Fish on 2007-04-24
Whenever the runlevel is changed, certain init scripts get run. You'll have to put the rest of your script in one of them. Remember that the same scripts get run whenever the runlevel gets changed, so put in some conditionals to make sure you really want to exec the script.

---

