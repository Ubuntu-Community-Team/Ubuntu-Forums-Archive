---
title: "Running a Python program in the background"
date: 2010-03-18
forum: Programming Talk
---

### Post by DanielJackins on 2010-03-18
Hello, I'm looking for some programming practice, and thought of a program I might like to create (if possible).

I'd like to make a program that runs in the background, collecting information about another running program (Diablo II, specifically). I'd want it to be able to collect data like knowing when a monster was killed, or a level gained, or some such event.

Is this possible? And if so, could anyone give me a nudge in the right direction?

Thanks!

---

### Post by aeiah on 2010-03-18
it would be simple if diablo II could output these events to a logfile, but i doubt it does. when launched from the command line, does it output any status events? (like monsters killed etc)

whilst people here will be able to help you with python and programming, its people in the diablo II modding community that'll be able to help you with how to interact with it.

---

### Post by roccivic on 2010-03-18
This ought to launch a python script in the background:

[PHP]#!/bin/bash
python /path/to/my/script/myscript.py &[/PHP]

save as pylauncher.sh (or the likes) and don't forget to

[PHP]chmod +x pylauncher.sh[/PHP]

---

### Post by era86 on 2010-03-18
You might be able to read the actual memory when the game is running.  This would take a little reverse engineering perhaps.

---

### Post by soltanis on 2010-03-18
If you end up having to watch memory, things are gonna get messy, and Python perhaps would not be the best suited for this as it might be too slow.

Something like Diablo II doesn't really want you knowing what's going on inside (Blizzard worked hard to hide this from you because it could probably be used for cheating). If you work with a different program, perhaps one that likes to be examined (free software has this tendency), then this is a little more feasible.

---

