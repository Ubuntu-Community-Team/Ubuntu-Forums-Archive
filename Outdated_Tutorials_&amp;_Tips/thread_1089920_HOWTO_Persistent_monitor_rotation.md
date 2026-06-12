---
title: "HOWTO: Persistent monitor rotation"
date: 2009-03-07
forum: Outdated Tutorials &amp; Tips
---

### Post by jackmcslay on 2009-03-07
This is a fix that allows for persistent configuration of tho monitor's pivot rotation. You most create two scripts:

[FONT="Courier New"]screen-rotate[/FONT]
```
#!/bin/bash
if [ "$1" = "right" ] 
then
	rotate="right"
else 
	rotate="left"
fi


if xrandr | grep "$rotate ("

then
	rotate="normal"
fi
xrandr -o "$rotate"

echo $rotate > ~/.screen-orientation
```

[FONT="Courier New"]screen-rotate-setup[/FONT]
```
#!/bin/bash
rotate=`cat ~/.screen-orientation`
xrandr -o $rotate
```

save both scripts to /usr/bin (via sudo, of course) and give them execution permissions to everyone (chmod +x)

Now go to System>Preferences>Sessions, click add and put [FONT="Courier New"]screen-rotate-setup[/FONT] as the command. Name it as you see fit.

Now create a shortcut somewhere (the taskbar, perhaps?) put as a the command [FONT="Courier New"]screen-rotate[/FONT](in case your monitor rotates clockwise) or [FONT="Courier New"]screen-rotate right[/FONT](in case your monitor rotates counter-clockwise).

New click on the shortcut, log out ane then log n again and... voilá!

---

