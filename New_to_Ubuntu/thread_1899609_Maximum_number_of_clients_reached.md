---
title: "Maximum number of clients reached"
date: 2011-12-23
forum: New to Ubuntu
---

### Post by The Titan on 2011-12-23
Using Openbox on 3 different x screens I commonly get this error

Maximum number of clients reached

when trying to run applications from the terminal.

not much is really running so I dont think im actually reaching the 255 limit for X

```

daniel@dungeon:~$ xlsclients -a
dungeon  xfce4-panel
dungeon  update-notifier
dungeon  nm-applet
dungeon  blueman-applet
dungeon  applet.py
dungeon  firefox
dungeon  xfce4-terminal
dungeon  wrapper
dungeon  wrapper
dungeon  xfce4-terminal
daniel@dungeon:~$ 


```This is how I am opening openbox, maybe I did something wrong here:

```
daniel@dungeon:~$ cat .xinitrc
#!/usr/bin/env bash

DISPLAY=:0.0 openbox & exec openbox-session &
DISPLAY=:0.1 openbox & exec openbox-session &
DISPLAY=:0.2 openbox & exec openbox-session &

xfce4-panel

daniel@dungeon:~$ 

```I'm super lost if anyone could shed some light on the topic for me that would be great

---

### Post by The Titan on 2011-12-24
Hope this helps somebody but a reboot seems to have cleared it up.  Not really sure what was going on.

---

