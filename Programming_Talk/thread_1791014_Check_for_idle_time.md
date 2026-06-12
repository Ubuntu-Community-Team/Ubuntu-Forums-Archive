---
title: "Check for idle time"
date: 2011-06-26
forum: Programming Talk
---

### Post by Derek Karpinski on 2011-06-26
In an effort to keep my external drive from spinning down, I've created the following script, and am successfully running it as root in cron:

```
#!/bin/bash
# Script to keep external drive from spinning down

diskmounted=$(mount | grep Backup | wc -c)

if [ $diskmounted -gt 0 ]
then
   touch /mnt/Backup/.nosleep
fi
```

Now, I'd like to make it a bit 'smarter'.  I don't nessecarily need the drive to be spinning all night.  I'd really like to check to see how long the computer has been idle before running this script.  If the computer has been idle for 30 minutes, I'd like to not 'touch' a file on the drive, and let it spin down.

I know I can check for idle time with the 'w' command, but how do I parse the idle time out of all that info?

Example output from 'w -s' command:
```
derek@home-pc:~$ w -s
 22:01:59 up  1:57,  2 users,  load average: 0.04, 0.12, 0.15
USER     TTY      FROM               IDLE WHAT
derek    tty7     :0                1:57m gnome-session --session=ubuntu
derek    pts/0    :0                0.00s gnome-terminal

```

---

### Post by uRock on 2011-06-26
Moved to "Programming Talk."

---

### Post by Derek Karpinski on 2011-06-26
Sorry, I didn't even know a programming talk forum existed. :)

Anyways, I've got something to work fairly well.  I found out how to parse the info from the 'w' command using awk.  The problem is the number is returns is not the actual idle time.  It's the idle time for tty7, which I don't quite understand..........so more digging lead me to think about screensavers and dbus infomation.  I'm putting the time in a file on the desktop temporarily to see if it is working.  What I've come up with is this:

```
#!/bin/bash
# Script to keep external drive from spinning down

scnsav=$(gnome-screensaver-command -q | grep -w inactive | wc -c)
diskmounted=$(mount | grep Backup | wc -c)

if [ $scnsav -gt 0 ]
then
   if [ $diskmounted -gt 0 ]
   then
      touch /mnt/Backup/.nosleep
      date >> /home/derek/Desktop/date.txt
   fi
fi

```

I'm new to all of this so if anyone has time maybe they could suggest something cleaner?  I'm not really too happy about using 'wc -c' to return a byte count to get the results of a 'true/false' statement.  And I'm thinking I'd rather use d-bus or something more universal than gnome-screensaver to check for idle.  Like I said, I'm new to Linux, and bash, but have some experience in tcl, so I'm excited to learn! :)

BTW, neither 'hdparm' or 'sdparm' could override the factory power settings of this drive.

---

### Post by Vaphell on 2011-06-26
drop wc -c part and test for null string instead

```
x=''; if [ "$x" ]; then echo true; else echo false; fi
false
x='x'; if [ "$x" ]; then echo true; else echo false; fi
true
```

---

### Post by juancarlospaco on 2011-06-26
Its Python but...

```

#!/usr/bin/python
# -*- coding: utf-8 -*-
# runs a program when screensaver comes up and stop it when not
import os
import time

RUNME = "echo"** # Program**
ARGS = "lol"** # Arguments**

screensaver_started = 0
running = 0
while 1:
	active = 0
	out = ""
	pid = 0
	if screensaver_started == 0:
		s = os.popen("pidof gnome-screensaver")
		spid = s.read()
		s.close()
		if len(spid) > 0:
			screensaver_started = 1
	else:
		h = os.popen("gnome-screensaver-command -q", "r")
		out = h.read()
		active = out.find("inactive")
		h.close()
		if active < 0 and running == 0:
			os.system("%s %s &" % (RUNME, ARGS))
			running = 1
		elif active > 0 and running == 1:
			os.system("pkill %s" % RUNME)
			running = 0
	time.sleep(5)

```

Edit the  # Program and # Arguments

---

### Post by Derek Karpinski on 2011-06-26
```
#!/bin/bash
# Script to keep external drive from spinning down

export DISPLAY=:0.0

scnsav=$(gnome-screensaver-command -q | grep -w -c inactive)
diskmounted=$(mount | grep -w -c Backup)

if [ $scnsav -eq 1 ]
then
   if [ $diskmounted -eq 1 ]
   then
      touch /mnt/Backup/.nosleep
   fi
fi

```

Note: I did drop the wc part, and I think grep -w -c is just as elegant as testing for a null value. Am I wrong?

Anyways, this works........but not as root.  I cannot get this script to run as root from cron.  I know it has everything to do with:
```
export DISPLAY=:0.0
```

I wonder if root does not have environment variables or a place to set them?  I've found tons of threads where people are having problems running cron jobs as root.

I appreciate the help!

As far as the python script, I'll have to get to that after I understand bash a bit more.  Thanks though.

---

### Post by Vaphell on 2011-06-26
> Note: I did drop the wc part, and I think grep -w -c is just as elegant as testing for a null value. Am I wrong?

no, you are not - you get the same info but in different form. Btw, you can combine switches so -w -c = -wc. Minor thing but shaves off few chars :)

---

### Post by Derek Karpinski on 2011-06-26
Thank you, I'll change it.  I like efficient, clean code. :)

I guess I'll mark this as 'solved' since my original question was answered.  I'll post another question about running cron as root in another thread.

Thanks again.

---

### Post by cgroza on 2011-06-26
> **Derek Karpinski said:**
> Thank you, I'll change it.  I like efficient, clean code. :)

Then do it in C.

---

### Post by Derek Karpinski on 2011-06-26
I don't know C.......yet.

---

