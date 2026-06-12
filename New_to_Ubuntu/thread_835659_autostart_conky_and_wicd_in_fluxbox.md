---
title: "autostart conky and wicd in fluxbox"
date: 2008-06-20
forum: New to Ubuntu
---

### Post by vocalstud69 on 2008-06-20
I've been trying to get conky and wicd to start on startup in fluxbox.  Wicd doesn't bother me that much, but I would like conky to start automatically when I startup.  I tried putting 

conky &

in the /.fluxbox/startup file, and it worked with netapplet in the same way, with 

netapplet &

Neither of them worked.  

Next I tried making a autostart.sh file with:

#!/bin/bash
sleep 5 && conky;

And I made it executable with chmod a+x and it doesn't work.  I'm stumped, because it worked with netapplet in the startup file.  I did put in the init file the sh /home/*/.fluxbox/autostart.sh in 

session.screen0.rootCommand: sh /home/*/.fluxbox/autostart.sh

I'm going to keep trying.  I've tried every way I could find here on the forums.  Please help!

Running Xubuntu 8.04 with fluxbox installed.  I prefer fluxbox to Xfce.

---

### Post by geo909 on 2008-06-20
This is my .startup file and conky starts just fine, no problems at all.
```
# fluxbox startup-script:
#
# Lines starting with a '#' are ignored.

# You can set your favourite wallpaper here if you don't want
# to do it from your style.
#

#fbsetbg -f /media/sdb1/Pictures/WallPapers/download.jpg
#
# This sets a black background

/usr/bin/fbsetroot -solid black

# This shows the fluxbox-splash-screen
# fbsetbg -C /usr/share/fluxbox/splash.jpg

# Other examples. Check man xset for details.
#
# Turn off beeps:
# xset -b
#
# Increase the keyboard repeat-rate:
# xset r rate 195 35
#
# Your own fonts-dir:
# xset +fp "/home/jorge/.fonts"
#
# Your favourite mouse cursor:
# xsetroot -cursor_name right_ptr
#
# Change your keymap:
# xmodmap "/home/jorge/.Xmodmap"



# Applications you want to run with fluxbox.
# MAKE SURE THAT APPS THAT KEEP RUNNING HAVE AN ''&'' AT THE END.
#
# unclutter -idle 2 &
# wmnd &
# wmsmixer -w &
# idesk &

conky &
klipper &


# And last but not least we start fluxbox.
# Because it is the last app you have to run it with ''exec'' before it.

exec /usr/bin/fluxbox
# or if you want to keep a log:
# exec /usr/bin/fluxbox -log "/home/jorge/.fluxbox/log"

```

Maybe you put it in the wrong line?

---

### Post by kerry_s on 2008-06-20
try in your ~/.fluxbox/startup:
sleep 5;conky &

---

### Post by walkerk on 2008-06-20
Or:

(sleep 3 && conky) &

---

### Post by diafanos on 2008-06-20
What about:
          **conky -d**


You don't need to use **&**, cause with **-d** option, conky runs as a deamon.

---

### Post by vocalstud69 on 2008-06-20
Unfortunately, nothing has worked.  Please help me, it's really starting to annoy me.

---

### Post by jeffCC on 2010-08-20
I know this is an old thread but I had the same problem, only with Xubuntu 10.04, and thought that if two people had the same problem two years apart then maybe more people might.

I had set up conky and networking to autostart in Xfce and tried to get the same in Fluxbox using every solution suggested here and many more,with no success, but it would start and run when I started it in a terminal even if I closed the terminal. 

Finally I removed Xfce and xfwm ( it was using 50% more RAM to do the same job ) as soon as I did and rebooted conky and network autostarted and has worked since.



         Jeff

---

### Post by Drahreg13 on 2011-09-01
> **kerry_s said:**
> try in your ~/.fluxbox/startup:
sleep 5;conky &

This worked for me!
I've just changed the "...conky &" for the "...conky -d &"

:D

PS: Sleep 5s is too much! :S

---

