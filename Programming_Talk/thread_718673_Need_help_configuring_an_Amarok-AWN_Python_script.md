---
title: "Need help configuring an Amarok-AWN Python script"
date: 2008-03-08
forum: Programming Talk
---

### Post by picpak on 2008-03-08
Ok...so first off, I have no experience in Python whatsoever. I have no clue what I'm doing.

This is the script I'm using in question:

[http://awn.wetpaint.com/page/Amarok+Script?t=anon](http://awn.wetpaint.com/page/Amarok+Script?t=anon)

It does what I want: it shows the cover art (Dream Theater ftw). However, I don't want it showing the pie chart of how much time is remaining. I checked the source code and found what does that:

```

            total = int(getoutput('dcop amarok player trackTotalTime 2> /dev/null'))
            if total > 0:
                print "setting progress",
                current = int(getoutput('dcop amarok player trackCurrentTime 2> /dev/null'))
                progress = int(round(100.0 / total * current))
                awn.SetProgressByName ("amarok", progress)
                print "[done]"
```

So I comment that code out, but I get errors that have to do with Python's indentation rules. :roll:

I have no clue when to indent, when not to indent, stuff like that. Can someone tell me what to do with the rest of the code so I can take advantage of all that indent-y goodness?

I've attached the script below:

---

### Post by Acglaphotis on 2008-03-08
Does this work?
[php]
#!/usr/bin/env python

from commands import getoutput
import dbus
import signal
from time import sleep
from os import system
from sys import exit


current_cover = "-"


# dbus connection
print "+ creating dbus object",
bus = dbus.SessionBus()
obj = bus.get_object("com.google.code.Awn", "/com/google/code/Awn")
awn = dbus.Interface(obj, "com.google.code.Awn")
print "[done]"


# termination handling
def cleanup(signum, frame):
    global current_cover
    if current_cover != "":
        print "unsetting cover and progress"
        if getoutput("pidof avant-window-navigator") != "":
            awn.SetProgressByName ("amarok", 100)
            awn.UnsetTaskIconByName("amarok")
        current_cover = ""
signal.signal(signal.SIGTERM, cleanup)


# main loop
while(1):
    if getoutput("pidof avant-window-navigator") != "":
        print "\nawn is running"
        if (getoutput('dcop amarok player isPlaying') == "true"):
            print "amarok is playing a track"
            total = int(getoutput('dcop amarok player trackTotalTime 2> /dev/null'))
            if total > 0:
                print "setting progress",
#               current = int(getoutput('dcop amarok player trackCurrentTime 2> /dev/null'))
#               progress = int(round(100.0 / total * current))
#awn.SetProgressByName ("amarok", progress)
                print "[done]"

                print "setting cover",
                cover = getoutput('dcop amarok player coverImage 2> /dev/null')
                if current_cover != cover or current_cover == "" or current_cover == "-":
                    coverpath = "cp "+cover+" /tmp/amarok-cover.png"
                    system(coverpath)
                    current_cover = cover
                    awn.SetTaskIconByName ("amarok", "/tmp/amarok-cover.png")
                    print "[done:new]"
                else:
                    print "[done:old]"
            else:
                print "not playing"
                cleanup(0, 0)
        else:
            cleanup(0, 0)
            
    if getoutput("pidof amarok") == "" and getoutput("pidof amarokapp") == "":
        print "amarok not running"
        cleanup(0, 0)
        print "exiting"
        exit()
    sleep(1)
[/php]

---

### Post by picpak on 2008-03-08
Yes it did! Thank you so much! :)

---

### Post by Acglaphotis on 2008-03-08
No problem, glad i could help.

---

