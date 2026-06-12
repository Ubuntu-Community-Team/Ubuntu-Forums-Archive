---
title: "problem with IDLE"
date: 2006-07-12
forum: Programming Talk
---

### Post by corefile on 2006-07-12
Running Dapper and I get the following when I try to start IDLE

corefile@penguin:~$ idle
Traceback (most recent call last):
  File "/usr/bin/idle", line 5, in ?
    main()
  File "/usr/lib/python2.4/idlelib/PyShell.py", line 1350, in main
    root = Tk(className="Idle")
  File "/usr/lib/python2.4/lib-tk/Tkinter.py", line 1569, in __init__
    self.tk = _tkinter.create(screenName, baseName, className, interactive, want objects, useTk, sync, use)
_tkinter.TclError: this isn't a Tk applicationunknown color name "Black"

anyone esle get this?

---

