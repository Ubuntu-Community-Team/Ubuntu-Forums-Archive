---
title: "HOWTO: Display now playing with Conky and BMPx"
date: 2009-04-09
forum: Outdated Tutorials &amp; Tips
---

### Post by pcrhckyman on 2009-04-09
Just started using BMPx, and although it hasn't been updated in a LONG time, it's still the best in my opinion.

After trying to compile conky with BMPx support (media player) and having it fail time and time again, I decided to make a python script for it. Very simple, but it was a pain for me (never done python before) to make, and others might share the same issues. :/

Anyway, download the file below or copy the code at the bottom into bmpx-conky.py and put it where you want it :)

To install it, open .conkyrc and add
```
${execi 5 ~/scripts/bmpx-conky.py}
```

Replace /scripts with the directory you put it in.

----

```
#! /usr/bin/python

import dbus
import os
import commands

output = commands.getoutput('ps aux | grep beep-media-player-2-bin | grep -v grep | wc -l')
if '1' in output:
    bus = dbus.SessionBus()
    Root = bus.get_object('org.mpris.bmp', '/')
    Player = bus.get_object('org.mpris.bmp', '/Player')
    try: Player.GetMetadata()
    except dbus.exceptions.DBusException:
     print 'not playing'
    else:
     info = Player.GetMetadata()
     decode = lambda x: unicode(x).encode('utf-8')         
     title = decode(info['title'])
     print title
else:
    print "not running"
```

---

