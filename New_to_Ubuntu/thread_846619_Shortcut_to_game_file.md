---
title: "Shortcut to game file"
date: 2008-07-01
forum: New to Ubuntu
---

### Post by remixx on 2008-07-01
Well I finally got all this stuff working, I installed Enemy Territory and can run it fine. Here's the problem, though. If I go into my enemy-territory directory and access the shell script 'et', everything goes fine. However, if I go through the K Menu to the Enemy Territory shortcut, which points to the same exact file, the game not only asks me to make another user account but also prevents me from auto-updating the game (it even tries to download files I already have). If I try to run the 'et' command, the same thing happens. Any ideas?

---

### Post by ninjabob7 on 2008-07-01
Sounds like the game stores its files in the working directory.
You could try this:
Create a file called et.sh in the game directory.
Put this in it:
```
#!/bin/sh
cd /full/path/to/game/directory
./et

```
(obviously change the path) then run
```
chmod +x et.sh
```
to make it executable.
Change the KDE shortcut to point to et.sh and it should work.

---

