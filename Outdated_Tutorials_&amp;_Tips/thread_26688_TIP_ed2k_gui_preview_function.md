---
title: "TIP: ed2k_gui preview function"
date: 2005-04-13
forum: Outdated Tutorials &amp; Tips
---

### Post by yanik on 2005-04-13
To make the preview function work in ed2k_gui, edit the file /home/user/.ed2k_gui/ed2k_gui_preview and replaced the following (6th line)
```
VIDPLAYER="mplayer -idx"
```
With this
```

VIDPLAYER="mplayer -idx -ao esd"
``` 
or this if you want the mplayer gui
```

VIDPLAYER="gmplayer -idx -ao esd"
``` 
It should now work.

Yanik

---

