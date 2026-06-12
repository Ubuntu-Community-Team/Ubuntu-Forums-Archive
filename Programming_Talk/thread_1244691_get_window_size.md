---
title: "get window size"
date: 2009-08-19
forum: Programming Talk
---

### Post by pfanne on 2009-08-19
well i wanted to write a small bashscript to help me with my desktop needs ;)
my mainproblem is that i need to get the size of the focused window...
i know tools like xdotool or wmctrl that help you move windows and allow you to resize them but thoroughly questioning google i cant find a tool that allows me to read the window size.
does anyone know a tool allowing me to get the window size of a window?

---

### Post by DaithiF on 2009-08-19
strange, just answered this very question (more or less) a minute ago... :)
see [http://ubuntuforums.org/showthread.php?t=1244653](http://ubuntuforums.org/showthread.php?t=1244653)
to get dimensions of a particular window with xwininfo you can use the -name parameter and pass the window title

```
xwininfo -name "Music Player" 
```
for example
```
xwininfo: Window id: 0x4000029 "Music Player"

  Absolute upper-left X:  328
  Absolute upper-left Y:  52
  Relative upper-left X:  1
  Relative upper-left Y:  27
  Width: 951
  Height: 854
  Depth: 24
  Visual Class: TrueColor
  Border width: 0
  Class: InputOutput
  Colormap: 0x20 (installed)
  Bit Gravity State: NorthWestGravity
  Window Gravity State: NorthWestGravity
  Backing Store State: NotUseful
  Save Under State: no
  Map State: IsViewable
  Override Redirect State: no
  Corners:  +328+52  -1+52  -1-118  +328-118
  -geometry 951x854-0+25

```

---

### Post by pfanne on 2009-08-19
great! thanks!
since im writing this script to lock the mouse to a certain window (the cursor cant leave the boundaries of the window, like having the cursor locked to your virtualbox vm) you dont happen to know a tool that exactly does this? (been looking for ages)

---

### Post by DaithiF on 2009-08-19
> you dont happen to know a tool that exactly does this?
no I don't, sorry.

---

