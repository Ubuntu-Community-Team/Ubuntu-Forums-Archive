---
title: "[SOLVED] Help with python script"
date: 2007-10-19
forum: Programming Talk
---

### Post by Omega2Four on 2007-10-19
Hey, 
I'm trying to write a python script that opens a sopcast stream, waits for 30 seconds and then opens vlc to view that stream. I know how to write it for the most part but when I run the script it opens the stream, buffers it and wont go any further in the script. essentially what i think is happening is since the sopcast program never exits its not moving on to the next step in the script (the 30 second sleep before opening vlc) can anyone help?

```
 
#!/bin/sh
echo "What is the channel that you seek?"
read number 
echo "Starting: $number "


sp-sc sop://broker.sopcast.com:3912/$number 6112 8908

#this is where the script hangs, it opens sopcast and continually buffers without going to the next step...is there a command i can stick here to get it to move?

sleep 30

vlc http://localhost:8908/tv.asf
 
```

---

### Post by tkharris on 2007-10-19
That's a shell script, not a python script.

You're right in that your sp-sc script is not exiting.  You can toss it into the background with:

```
sp-sc sop://broker.sopcast.com:3912/$number 6112 8908 &
``` and you should be golden.

---

### Post by Omega2Four on 2007-10-19
haha thanks your right i started writing it in python and then decide to go with a shell script..thanks a lot!

-Greg

---

### Post by tkharris on 2007-10-19
> **Omega2Four said:**
> haha thanks your right i started writing it in python and then decide to go with a shell script..thanks a lot!

-Greg

No problem.  =D

You might want to mark the topic [SOLVED], although I'm new so I don't know if the user who opened the thread can do that or just the admins/mods?

---

