---
title: "assign a keyboard key to lock the mouse's button (start the &quot;drag&quot; in &quot;drag&amp;drop&quot;)"
date: 2013-12-01
forum: New to Ubuntu
---

### Post by lamigam on 2013-12-01
Hi

I have an injury in both my wrists in which I cannot "[drag and drop]("http://en.wikipedia.org/wiki/Drag_and_drop")" with the mouse. but it is very important to me to do so....

for years I have been using an application in my windows desktop in which I can click a key on a keyboard (for example the "F8" key) that holds down the left mouse button for me, than I can "drag"
 using the mouse, and finally release the F8 key in order to "drop" (finish the "drag and drop")

recently I installed Ubuntu 12.04 and need to be able to perform the same action.

an example of something that does just that in 12.04 is by setting "pointer can be controlled by using the keypad" on:
[http://www.bbc.co.uk/accessibility/guides/keyboard_mouse/computer/linux/gnome/#setup](http://www.bbc.co.uk/accessibility/guides/keyboard_mouse/computer/linux/gnome/#setup)

than I use the "INS" key to "Lock Mouse Button":
[http://www.bbc.co.uk/accessibility/guides/keyboard_mouse/computer/linux/gnome/#howtouse](http://www.bbc.co.uk/accessibility/guides/keyboard_mouse/computer/linux/gnome/#howtouse)

problem is, this disables the keypad as a keypad (the numbers on it, the "Enter" button, the plus key etc.) and I really want the keypad to work as a keypad.
**if only I could assign a different key to "Lock Mouse Button"... ?**

there is another option: my mouse has 6 button.
if I could assign one of those buttons to start the drag and click it again to release it - that would be just as good.

---

### Post by stinkeye on 2013-12-01
This xdotool command will simulate holding down left mouse....
```
xdotool mousedown 1
```

Bind this command to a keyboard shortcut or use easystroke to bind it to a spare mouse button....
```
sh -c "sleep 0.2 && xdotool mousedown 1" 
```

I describe [**_[COLOR="#B22222"]HERE[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=1694352&p=10495426#post10495426") how to use easystroke.
Just alter to use a command instead of key.
You will need to install xdotool and easystroke.

Whichever way you set it up, once activated you just need to press left mouse to release the dragged item.


Another option would be use this script as a left mouse up/down toggle and bind to a single key like F8.
Press your shortcut key once for left mouse down....press again to release.
Use the full path to the script as the command.
_toggle-mouse1.sh_
```
#!/bin/bash

# script to toggle left mouse button up/down.
# Initial run will create ~/.mouse-state.txt and will then toggle with subsequent runs.

if [ "$(cat ~/.mouse-state.txt)" = "0" ]; then
   	sleep 0.2 && xdotool mousedown 1 && echo 1 > ~/.mouse-state.txt
else
	sleep 0.2 && xdotool mouseup 1 && echo 0 > ~/.mouse-state.txt
fi
```

---

### Post by lamigam on 2013-12-03
:) thank you. the xdotool solution worked perfectly for me.
now I would like to do the same at work on which I have redhat installed.

would this work on redhat as well ?

---

### Post by stinkeye on 2013-12-03
> **lamigam said:**
> :) thank you. the xdotool solution worked perfectly for me.
now I would like to do the same at work on which I have redhat installed.

would this work on redhat as well ?

Don't see why not.
Fedora should have an xdotool rpm.

---

### Post by lamigam on 2013-12-11
thanks [**[COLOR=#000000]stinkeye[/COLOR]**]("http://ubuntuforums.org/member.php?u=684510").
it works on redhat too.

---

