---
title: "help for a simple BEEP MEDIA PLAYER script"
date: 2006-03-02
forum: Programming Talk
---

### Post by ashrack on 2006-03-02
I would like to have a script that would first check if BEEP MEDIA PLAYER is running and if it is it would lunch the following:
```
beep-media-player -s
```
but if BEEP MEDIA PLAYER isn't running than the script should just exit.
How could I accomplish this?

---

### Post by colo on 2006-03-02
```
#!/bin/bash
pgrep beep-media-play || beep-media-player -s
```

There's an option for bmp to disallow multiple instances of the program, though.

---

### Post by ashrack on 2006-03-06
Your line does the opposite of what I want. It does this:
if BMP is started than it does nothing.
if BMP isn't started then it will do 'beep-media-player -s'

---

### Post by ashrack on 2006-03-06
this script works:
```
result=`ps -A | grep beep-media-player`
if [ "$result" == "" ]
then
exit
else
beep-media-player -s
fi
```

---

### Post by colo on 2006-03-06
Ah well, sorry - stupid me ;)

Change it to
```
#!/bin/bash
pgrep beep-media-play && beep-media-player -s
```
and you're done.

---

### Post by ashrack on 2006-03-07
I knew there that had to be D error:
||  = or
&& = and

will try the new script. should work

---

