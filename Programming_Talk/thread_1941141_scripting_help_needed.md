---
title: "scripting help needed"
date: 2012-03-15
forum: Programming Talk
---

### Post by radon7 on 2012-03-15
I am looking to find how to call a program and send it hotkeys from a script before the script exits. Specifically, I want to start dvtm from a script, then set it up the way I prefer it before the script exits. Dvtm uses emac style hotkeys like "Ctrl+J C" to create new windows. I prefer bash or python but any scripting language will work. I want to call the script when I log into a terminal and have it set up dvtm automatically. Is there a way to send the hotkeys to the program?

---

### Post by CynicRus on 2012-03-15
[http://python-xlib.sourceforge.net/doc/html/python-xlib_14.html](http://python-xlib.sourceforge.net/doc/html/python-xlib_14.html)

---

### Post by radon7 on 2012-03-15
Thanks for the reply, but not what I am looking for. I want to start a command line program and send it hotkeys. I will not be working with any gui so xlib wont work.

---

### Post by Toz on 2012-03-15
Have a look at xdotool ([http://manpages.ubuntu.com/manpages/lucid/man1/xdotool.1.html]("http://manpages.ubuntu.com/manpages/lucid/man1/xdotool.1.html")). A command like this should work:
```
xdotool key ctrl+J C
```

---

### Post by radon7 on 2012-03-16
xdotool is for X11 which I will not be using.  I will be using a terminal by pressing Ctrl+Alt+F1 or logging in remotely so I won't be running any X11 gui.  If you don't know what dvtm is then the same problem could be used to write a script to start emacs and send it some hotkeys.  Starting a program from a script usually kills the script or suspends it untill the called program exits. I would like to know how to override this action to send the started program hotkeys. I will be working exclusively at the terminal though so xlib or any other x librarys won't work.

---

### Post by xorgnak on 2012-11-12
xdotool doesn't work.  But I'm also in need of a solution to this problem.  I use dvtm inside of a screen window to show top, tty-clock, bwm-ng, and a little function to run df every few minutes all at the same time.  Only using one window instead of four is great, but manually starting each of them is a huge pain.  Perhaps what is needed is a solution like screen's which allows a new window to be opened from within a running instance of screen.  Something like:```
dvtm; dvtm --nest cmd0; dvtm --nest cmd1; dvtm --nest cmd2
``` might be be possible after digging into the code.  Or it may be possible to take advantage of the suckless community's affinity for plan9 and build a filesystem based interface.  Fixing this problem would be a huge help.  anyone have any other ideas?

---

