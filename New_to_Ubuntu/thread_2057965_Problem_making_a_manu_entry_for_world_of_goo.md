---
title: "Problem making a manu entry for world of goo"
date: 2012-09-14
forum: New to Ubuntu
---

### Post by Falc7 on 2012-09-14
I installed World of Goo from a deb, it makes a link in the menu, but the shortcut doesnt work, so I specify manually where the file is, i edit the command part of the menu so it reads as follows: 
/opt/WorldOfGoo/WorldOfGoo.bin64
When I try and start it, the screen changes resolution indicating its trying to start the program, but evenually it returns to the desktop.

However when i manually navigate to that folder and click on WorldOfGoo.bin64 it starts up just fine.
Very frustrating.

---

### Post by Falc7 on 2012-09-15
Another related problem, if i make a link to the executable the link works if its in the folder with the executable, but if i move the link to the desktop it no longer works. Seems really buggy.

---

### Post by mcduck on 2012-09-15
That sounds simply like the game requires you to run it from the same directory where the game is located.

...which makes the problem a really simple one to solve, just create a shell script that moves you to correct location and then launches the game, and point your menu launcher to that script instead of the game's executable.

```
#!/bin/sh
cd /opt/WorldOfGoo/
./WorldOfGoo.bin64
```

---

### Post by Falc7 on 2012-09-19
Great that worked thanks!

---

