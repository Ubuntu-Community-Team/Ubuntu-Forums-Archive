---
title: "gedit programming interface"
date: 2006-04-26
forum: Programming Talk
---

### Post by lee_connell on 2006-04-26
I wan to setup gedit with the side panel and additional plugins like python console and external program executor. At the same time I want to be able to use gedit in it's default setup mode for viewing documents.

Is there a way to run a command with a switch or something to run gedit with different startup settings so I can create desktop shortcuts to run the two different modes?

---

### Post by ow50 on 2006-04-27
All Gedit's settings are stored in GConf under /apps/gedit-2. You could write a script that uses gconftool-2 to change the settings and then start gedit.

For example
```
#!/bin/bash

gconftool-2 --type bool --set /apps/gedit-2/preferences/editor/line_numbers/display_line_numbers false
gedit
```

---

### Post by lee_connell on 2006-04-27
great, thanks for the tip, i'll give that a shot.

---

### Post by lee_connell on 2006-04-29
where does gedit stores its window size?  I want to preset these as well.

thanks

---

### Post by ow50 on 2006-04-30
[QUOTE=lee_connell]where does gedit stores its window size?  I want to preset these as well.[/QUOTE]
~/.gnome2/gedit-2

---

### Post by lee_connell on 2006-05-01
Yeah I looked in there, I just didn't see where it was holding window position, will continue to look a bit more.

thanks

---

### Post by ow50 on 2006-05-01
[QUOTE=lee_connell]Yeah I looked in there, I just didn't see where it was holding window position, will continue to look a bit more.[/QUOTE]
I don't think the window position is stored anywhere. At least for me Gedit doesn't remember its position. The point, I believe, is to allow the window manager to place the window so that there's no overlap. At least Metacity seems to do that.

---

