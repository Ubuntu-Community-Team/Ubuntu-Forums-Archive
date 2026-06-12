---
title: "Python 3.3 script to augment xrandr --pos command"
date: 2013-12-07
forum: Programming Talk
---

### Post by molder on 2013-12-07
I want to write a simple script to increment the xrand --pos 0x0 command.  I have an HDMI overscan issue with my Plama TV that does not have a menu option for overscanning.  There are no GUI frontends for xrandr that I could find that worked with the --pos option, scale or transform. I took a look to see if I could hijack part of the XBMC screen adjustment code but I'm not quite to the level with programming.

Here is what I have so far:
```
#!/usr/bin/env python

import os
import time

for pos in range(0 , 1000):

    xrandr = xrandr = "xrandr --output HDMI1 --pos %dx%d" % (pos,pos)

    print(xrandr)
    
    os.system(xrandr)

    time.sleep(3)
```

Unfortunately nothing happens when I execute it from Idle.

---

### Post by molder on 2013-12-07
It kinda worked from the command line.  However, no crtc 0: changes

```
andrew@andrew-laptop-wired:~$ python hdmi_scaler.py
xrandr --output HDMI1 --pos 0x0 --verbose
crtc 0:     1280x720   60.0 +0+0 "HDMI1"
xrandr --output HDMI1 --pos 10x10 --verbose
crtc 0:     1280x720   60.0 +0+0 "HDMI1"
xrandr --output HDMI1 --pos 20x20 --verbose
crtc 0:     1280x720   60.0 +0+0 "HDMI1"
xrandr --output HDMI1 --pos 30x30 --verbose
crtc 0:     1280x720   60.0 +0+0 "HDMI1"
xrandr --output HDMI1 --pos 40x40 --verbose
crtc 0:     1280x720   60.0 +0+0 "HDMI1"
xrandr --output HDMI1 --pos 50x50 --verbose
crtc 0:     1280x720   60.0 +0+0 "HDMI1"
xrandr --output HDMI1 --pos 60x60 --verbose
crtc 0:     1280x720   60.0 +0+0 "HDMI1"
```


> **molder said:**
> I want to write a simple script to increment the xrand --pos 0x0 command.  I have an HDMI overscan issue with my Plama TV that does not have a menu option for overscanning.  There are no GUI frontends for xrandr that I could find that worked with the --pos option, scale or transform. I took a look to see if I could hijack part of the XBMC screen adjustment code but I'm not quite to the level with programming.

Here is what I have so far:
```
#!/usr/bin/env python

import os
import time

for pos in range(0 , 1000):

    xrandr = xrandr = "xrandr --output HDMI1 --pos %dx%d" % (pos,pos)

    print(xrandr)
    
    os.system(xrandr)

    time.sleep(3)
```

Unfortunately nothing happens when I execute it from Idle.

---

