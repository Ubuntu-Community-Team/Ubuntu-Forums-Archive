---
title: "Command to put after binary to not tie up the termniall"
date: 2011-10-12
forum: New to Ubuntu
---

### Post by jacob.feltman on 2011-10-12
I seem to have forgotten what this command is. Can someone help me out?

---

### Post by spiky001 on 2011-10-12
Command &
is that what you mean

---

### Post by Lisiano on 2011-10-12
Say your command is ```
sleep 60s
```
If you type it, you can't use the terminal for 60 seconds or until you Ctrl+C it, you can put a **&** (Ampersand) after it to make it run in the background
```
sleep 60s &
```
Or if you are already running the app, press Ctrl+Z then type ```
bg
```
If you want to interact with the program, type ```
fg
```
Same for the ampersand method

---

