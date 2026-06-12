---
title: "One bash script, two processes"
date: 2010-06-28
forum: Programming Talk
---

### Post by qwertyuiop96 on 2010-06-28
I have a rather simple bash script, used for changing channels with a video encoder card.  Here is the code:

```

#!/bin/bash

channel=3
ZERO=0

while [ $channel -gt $ZERO ]; do
	echo -e "Channel: \c "
	read channel
	ivtv-tune -c $channel
	ivtv-tune -c $channel #changing channels down sometimes needs 2 tries
done
```

It works fine.  However, I would like it to launch mplayer in the first place, so all users-who-don't-know-what-they-are-doing just have one command to put in. (bash tv.sh)  However, if I add the mplayer launch to the beginning, mplayer takes over the terminal window and my script can't accept input.  The way I have been doing it is with 2 terminal windows, one with the script, one running mplayer.  So, is there any way to make a new tab/window in bash and transfer a process to that other window?  Or are there other easier ways to do this?

---

### Post by ankit.vader on 2010-06-28
try this

```

mplayer & 
#then your code

```

---

### Post by qwertyuiop96 on 2010-06-28
> **ankit.vader said:**
> try this

```

mplayer & 
#then your code

```

Sort of.  Just mplayer ran, and when I closed its window, the script took over.  My echo pring printed at the very beginning.  I couldn't interact with the script while mplayer was running, though.  BTW, here is the exact code I'm using to start mplayer: 

mplayer /dev/video0

---

### Post by splargle on 2010-06-28
This thread talks about opening and executing a command in a new terminal window, would that do the trick?

[http://ubuntuforums.org/showthread.php?t=33641](http://ubuntuforums.org/showthread.php?t=33641)

---

### Post by qwertyuiop96 on 2010-06-28
> **splargle said:**
> This thread talks about opening and executing a command in a new terminal window, would that do the trick?

[http://ubuntuforums.org/showthread.php?t=33641](http://ubuntuforums.org/showthread.php?t=33641)

Perfect, that did it, thanks!

---

