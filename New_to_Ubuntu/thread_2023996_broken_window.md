---
title: "broken window"
date: 2012-07-13
forum: New to Ubuntu
---

### Post by seeker.k3 on 2012-07-13
I think the window system needs fixing. But I have no idea what to do, or if that's the problem at all.
I'm having problems with the desktop, and I can't start the Window Manager or Window Manager Tweaks. The things I'm calling problems with the desktop are things such as: only one workspace, broken frames (no title bars, windows won't resize or minimize), windows at the back can't be brought forward (I have to move the front ones off to the side to get to those at the back, and if I move one at the back off to the side too, it slips in behind! the other windows), mouse doesn't behave as it should. 

I tired to fix the problems by installing Xfce 4.10 (upgrade from Xfce 4.08 to 4.10), but it didn't change anything. I think I'm to blame for the problem because I shut down while some applications were still running, and then the next day...problems. 

Any comments appreciated, as always.

---

### Post by Toz on 2012-07-13
Sounds like the window manager has crashed. Try Alt-F2 (or from a terminal window) and running:
```
xfwm4 --replace
```

You _may_ also have an xfdesktop crash. If you still can't access the Window Manager or Window Manager Tweaks, try running:
```
xfdesktop
```

You can also clean this mess up totally by deleting your ~/.cache/sessions folder (note that .cache is a hidden folder on your home directory) and logging out and back in again. Or from the command prompt:
```
rm -rf ~/.cache/sessions
```

Be extra careful with the "rm -rf" command.

---

### Post by seeker.k3 on 2012-07-13
Thank you so much.
I just typed <xfwm4 --replace> and Hey Presto! I didn't get to the part where I have to be extra careful.
Thank you.

---

