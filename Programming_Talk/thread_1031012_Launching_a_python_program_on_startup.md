---
title: "Launching a python program on startup?"
date: 2009-01-04
forum: Programming Talk
---

### Post by tuxpenguin on 2009-01-04
I know this is probably better posted elsewhere, but this is probably a quick fix...I just can't find the answer anywhere. :(

I'd like to start a Python program I wrote [computer/network administration shortcut program] on startup. It needs to be run in a terminal, as I have no idea how to go about doing a GUI for it. [I'm new to python ;)]

I've tried putting the following commands in the gnome's startup programs manager:

```
gnome-terminal -e python /home/matt/Documents/login/login.py
```

```
python /home/matt/Documents/login/login.py
```

With the second one I was hoping there was an option for launching in a terminal...there isn't.

Any help would be great.
-Matt

---

### Post by Paul Miller on 2009-01-05
Well, if you're using GNOME, and by "at startup," you mean "when GNOME starts up," all you have to do is start your program up, then save your session with gnome-session (sorry, I forget where in the menus it is).  Next time you start GNOME, the exact same programs you had running when you previously saved the session will be started up for you.

---

### Post by efexD on 2009-01-05
Try putting it in "Sessions" using the command you posted above in the command box.

---

### Post by tuxpenguin on 2009-01-05
> **efeXor said:**
> Try putting it in "Sessions" using the command you posted above in the command box.

Yea that's what I meant when I said "Gnome's startup programs manager". It doesn't work. Terminal opens, but all that's in it is the version info for Python.

---

### Post by Greyed on 2009-01-05
Set the script executable, ensure it has a proper shebang at the top and run it directly?

---

