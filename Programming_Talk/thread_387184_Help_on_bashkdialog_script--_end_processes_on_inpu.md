---
title: "Help on bash/kdialog script-- end processes on input?"
date: 2007-03-18
forum: Programming Talk
---

### Post by Paradoxdruid on 2007-03-18
So, I was throwing together a little bash/KDialog script for displaying movies in the background of my desktop, and it works like a charm.
```
#!/bin/bash
MOVIE=`kdialog --getopenfilename .`
xwinwrap -ni -o 1 -fs -s -st -sp -b -nf -- mplayer -wid WID -quiet "$MOVIE"
```

**The problem:**
I want to add a second dialog to this script, so that if I click "Ok", it will kill xwinwrap and mplayer and end the script.  (A "stop playback" button, essentially)  I'm not sure how to do this with my very-limited scripting knowledge.  My first, VERY naive thought was
```
#!/bin/bash
MOVIE=`kdialog --getopenfilename .`
xwinwrap -ni -o 1 -fs -s -st -sp -b -nf -- mplayer -wid WID -quiet "$MOVIE" &
STOP=`kdialog --error "Click to stop movie"`
until [ $STOP = 0 ]
do
done
exit 0
```

But clearly this won't work--  it just leaves mplayer and xwinwrap running and ends the script.

How can I tell the program to kill the processes it spawned and exit when I click the exit button?

Thanks for any help or advice, I really appreciate it.

---

### Post by Mr. C. on 2007-03-18
My brief look at the xwinwrap documentation shows no useful diagnostics or return values, so you may have to do things manually.

You need to find the process id of the xwinwrap application and kill it upon exit.  Use:

```
kill -TERM $(pidof xwinwrap)
```

This will get the pid of the xwinwrap application, and send it a signal to terminate.  If TERM doesn't kill xwinwrap, replace -TERM with -KILL (or -9, same thing).

You may find you need to perform the same with mplayer.

MrC

---

### Post by Paradoxdruid on 2007-03-18
Thanks!  I changed the script and it's working great.
```
#!/bin/bash
MOVIE=`kdialog --getopenfilename .`
xwinwrap -ni -o 1 -fs -s -st -sp -b -nf -- mplayer -wid WID -quiet "$MOVIE" &
kdialog --error "Click to stop movie"
kill -TERM $(pidof xwinwrap)
exit 0
```

Still seems a little bit of a kludge, having the program just wait on the dialog like that...  but it works, I guess.

---

