---
title: "Center Windows Keyboard Shortcut"
date: 2016-04-27
forum: New to Ubuntu
---

### Post by dannymichel on 2016-04-27
Is there is a keyboard shortcut(maybe for compiz) that centers windows?

---

### Post by CantankRus on 2016-04-27
You can set windows to be opened in the centre using ccsm....
[ATTACH=CONFIG]268663[/ATTACH]

You can also use  a wmctrl command to move and resize a window.
See [**_[COLOR="#B22222"]HERE[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=1942500&p=11776457#post11776457")
The wmctrl command I use is...
```
wmctrl -r :ACTIVE: -b remove,maximized_vert,maximized_horz && wmctrl -r :ACTIVE: -e 0,450,260,850,531
```
This command will also work on maximized windows.

---

### Post by dannymichel on 2016-04-27
Thank you. I'm not sure what to do with that.
Do I open something and paste that in, creating a custom keyboard shortcut somehow?

---

### Post by CantankRus on 2016-04-27
If you want to use a keyboard short cut to centre the focused window use this as the command...
```
sh -c "wmctrl -r :ACTIVE: -b remove,maximized_vert,maximized_horz **&&** wmctrl -r :ACTIVE: -e 0,450,260,850,531"
```
You may need to install **wmctrl**.
Use the link in my previous post to modify the settings after **&&** for the placement and size of the window.

---

### Post by dannymichel on 2016-04-27
Ok, thanks

---

### Post by dannymichel on 2016-04-28
Wait, so from what I understand, this will re-size the window or i need to know the size i want the window im centering should be? There is no universal option?

---

### Post by CantankRus on 2016-04-28
> **dannymichel said:**
> Wait, so from what I understand, this will re-size the window or i need to know the size i want the window in centring should be? There is no universal option?
Not that I know of?
The wmctrl command uses the top lefthand corner of the window to determine position so the command sets a window to a uniform size and position you determine.
In the attached video I use easystroke mouse gestures to resize and centre windows using the command in post #4.
My screensize is 1680 x 1050.

---

### Post by dannymichel on 2016-04-29
I guess what im having a hard time figuring out is
1 - what numbers dictate the center of 1920x1080
2 - can i use this wmctrl method to center and not resize a window

---

### Post by vasa1 on 2016-04-29
> **dannymichel said:**
> ...
2 - can i use this wmctrl method to center and not resize a window

The code posted in [http://askubuntu.com/a/571711/](http://askubuntu.com/a/571711/) works for me. You will need to install *xdotool*. From the looks of it, you don't have to specify sizes.

I'm surprised that your window manager doesn't provide an option to center windows. Have you looked at all its possibilities?

---

### Post by dannymichel on 2016-04-29
> **vasa1 said:**
> From the looks of it, you don't have to specify sizes.
Specify my screen size at 1920x1080 or specify all window sizes, effectively making it useless as a universal shortcut?

> **vasa1 said:**
>  Have you looked at all its possibilities?

Compiz does control + alt + 5, but it centers and makes the window 100% which actually makes the center part useless since the window is 100%

---

### Post by vasa1 on 2016-04-29
> **dannymichel said:**
> Specify my screen size at 1920x1080 or specify all window sizes, effectively making it useless as a universal shortcut?
...
What are you talking about? The code I linked to does not mention 1920x1080 or ask you to specify anything. Did you look at the code?

---

### Post by CantankRus on 2016-04-29
vasa1's link works.

Install xdotool.

Copy and save then make executable.
```
#!/bin/bash

IFS='x' read screenWidth screenHeight < <(xdpyinfo | grep dimensions | grep -o '[0-9x]*' | head -n1)

width=$(xdotool getactivewindow getwindowgeometry --shell | head -4 | tail -1 | sed 's/[^0-9]*//')
height=$(xdotool getactivewindow getwindowgeometry --shell | head -5 | tail -1 | sed 's/[^0-9]*//')

newPosX=$((screenWidth/2-width/2))
newPosY=$((screenHeight/2-height/2))

xdotool getactivewindow windowmove "$newPosX" "$newPosY"
```

Use the path to where you saved the script in the command box of keyboard shortcuts.
Will recentre the window while maintaining original size.

---

### Post by dannymichel on 2016-04-29
> **CantankRus said:**
> vasa1's link works.

Install xdotool.

Copy and save then make executable.
```
#!/bin/bash

IFS='x' read screenWidth screenHeight < <(xdpyinfo | grep dimensions | grep -o '[0-9x]*' | head -n1)

width=$(xdotool getactivewindow getwindowgeometry --shell | head -4 | tail -1 | sed 's/[^0-9]*//')
height=$(xdotool getactivewindow getwindowgeometry --shell | head -5 | tail -1 | sed 's/[^0-9]*//')

newPosX=$((screenWidth/2-width/2))
newPosY=$((screenHeight/2-height/2))

xdotool getactivewindow windowmove "$newPosX" "$newPosY"
```

Use the path to where you saved the script in the command box of keyboard shortcuts.
Will recentre the window while maintaining original size.
PERFECT
Thank you

---

