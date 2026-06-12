---
title: "I really messed something up and I have no idea how to fix it"
date: 2012-03-09
forum: New to Ubuntu
---

### Post by coldjeanz on 2012-03-09
Running 11.10 Unity.

Literally all I did was press Alt+right click on the top panel thinking it might have the same effect as Classic but what ended up happening was my global menu went all funky and then disappeared. The "Desktop" part has disappeared as well and I can't do anything on my desktop itself. Can't right click on it or add new folders and the global menu there is completely gone. I can't figure out how to bring it back. Global menu still works everywhere else, if I minimize Firefox or Chrome it will still think I have those programs open when I'm on the desktop and the global menu for them shows instead. Same with every other program.

Please help!

EDIT: Also my CPU usage skyrockets when I am on the desktop now and try to click around. It eventually just freezes.

---

### Post by wojox on 2012-03-09
Can you get to a terminal? (Ctrl+Alt+T or Ctrl+Alt+F1-6) and run:
```
unity --reset
```

---

### Post by coldjeanz on 2012-03-09
Reset it and it's still broken. This is absolutely insane, how could it be that easy to ruin everything? I literally did exactly what I said earlier, I held down alt and right clicked on the panel and the Global Menu got all glitchy and then it disappeared. Desktop has no function now and the CPU usage just goes crazy.

---

### Post by souravc83 on 2012-03-09
Try to remove and reinstall unity

---

### Post by coldjeanz on 2012-03-09
How can I do that?

---

### Post by coldjeanz on 2012-03-09
Ugh I figured it out, I had turned off "Let desktop handle file manager" or something like that in Advanced Settings earlier and I didn't realize it. Reenabled it and now it's working fine.

Solved

---

