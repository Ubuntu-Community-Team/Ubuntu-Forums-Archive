---
title: "Execute Terminal Command"
date: 2009-02-25
forum: Programming Talk
---

### Post by DeadRobot on 2009-02-25
Is there anyway to create a file that when you double click it it will execute a specified terminal command?

---

### Post by monkeyking on 2009-02-25
shure you just need to shebang it

something like

[PHP]
#!/bin/bash
date
[/PHP]

then make it executable with
chmod u+x yourfile.sh

---

### Post by ajgreeny on 2009-02-25
Yes, it's a shell script.
One of mine looks like this:-
```
#!/bin/bash
/usr/bin/streamripper http://media-ice.musicradio.com:80/ClassicFMMP3 -t -d /home/andrew/Audio_recording/Radio -l 10800
```The first line is a code to tell the system that it is a script to run in the standard bash, the second line is the command with all its options etc.  This is just a plain text file but saved with a .sh suffix (filename.sh)  Double click will work on it if you make the file executable.

EDIT:  Drat it!  Too slow.

---

