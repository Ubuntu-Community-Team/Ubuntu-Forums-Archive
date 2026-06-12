---
title: "[SOLVED] a way to open certain applications in a seperate session?"
date: 2008-07-23
forum: New to Ubuntu
---

### Post by tjwoosta on 2008-07-23
so my problem is that i have a bunch of applications that dont like compiz
(like googleearth and alot of games and emulators)


is there any way that i can open them in a seperate userspace or whatever (without compiz)

for example: i know i can switch sessions (or something like that) with ctrl-alt-f buttons and i can easily change back with ctrl-alt-f7

but when i do change sessions it brings me to a command line and if i type the command to run a program like googleearth nothing happens

what am i doing wrong?

is what i am trying to do even possible?

the reason i dont want to just disable compiz every time i use one of the problematic programs is because i have to completly reconfigure compiz every time i disable it and turn it back on

---

### Post by jordanmthomas on 2008-07-23
You could start up a second X session like so
```
X :1 &
DISPLAY=:1 googleearth

```

Then, Ctrl - Alt - F8 (probbaly f8, maybe not) to get to googleearth.  When you're done, quit google earth and press Crtl - Alt - Backspace to kill the session.

You should be able to switch back and forth between the sessions with the ctrl-alt-f buttons like you mentioned.

---

### Post by tjwoosta on 2008-07-23
awesome thanks


also, while i was waiting for a reply i did some searching and i found a post with a simple script that will switch to metacity while running certain apps 
[http://ubuntuforums.org/showthread.php?t=867562]("http://ubuntuforums.org/showthread.php?t=867562")

before what i was doing was going to system-preferences-appearance and clicking visual effects and choosing none, but that made my ccsm reset

switching to metacity with metacity --replace and switching back with compiz --replace seems to work fine though

---

