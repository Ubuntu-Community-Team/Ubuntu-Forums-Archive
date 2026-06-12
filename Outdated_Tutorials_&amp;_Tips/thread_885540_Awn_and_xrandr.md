---
title: "Awn and xrandr"
date: 2008-08-10
forum: Outdated Tutorials &amp; Tips
---

### Post by bmxr on 2008-08-10
This is my tip how to get awn to rotate along with the screen. 

I have created this script and called it rotate.sh

```
#!/bin/sh
# rotate.sh Terry Stenvold 2008
if [ -n "$(xrandr | grep 800x1280)" ]; then
        xrandr -o normal
        xsetwacom set "stylus" Rotate NONE
	killall awn
	gconftool-2 --set /apps/avant-window-navigator/monitor_height --type integer 800 
	gconftool-2 --set /apps/avant-window-navigator/monitor_width --type integer 1280
	avant-window-navigator
else
        xrandr -o left
        xsetwacom set "stylus" Rotate CCW
	killall awn
	gconftool-2 --set /apps/avant-window-navigator/monitor_height --type integer 1280 
	gconftool-2 --set /apps/avant-window-navigator/monitor_width --type integer 800
	avant-window-navigator
fi
```

hope that helps

---

