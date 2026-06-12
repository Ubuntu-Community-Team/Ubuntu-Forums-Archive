---
title: "Stopping processes such as TCPReplay programmatically"
date: 2006-05-18
forum: Programming Talk
---

### Post by Aramis on 2006-05-18
Hi y'all,

As you can see everything is in the title. I would like to know how I can stop processes such as TCPReplay, TCPDump, Snort and so on programmatically. Typi cally, you have to kill these processes by either pressing CTRL+C in their respective terminals, or using the "sudo kill *PID*" command. The reason why I would like to control when to stop such task is because I have developpe a piece of software for my PhD that is able to start various tasks around a network and report back to a **Master Application**. TCPReplay and the like are typically tasks that I would start at the beginning of an experiment and stop before moving on to the next phase of the experiment.

Of course, my current solution, at the moment, is to start 2 deamons:
* one would start, say, TCPReplay
* one would search for the PID and kill the application accordingly

Not the best of solution I admit, thus this post :mrgreen:

Help much appreciated

Ar@mi$

PS: I went throught the man pages for TCPReplay apparently it supports 2 signals. These do not "stop" the process as such but "pause/restart" it rather. I can't find how to send these signals :'( and I believe these do not fit my requirements.

---

### Post by IYY on 2006-05-18
There is a command called "killall" that kills by name rather than PID.

sudo killall TCPReplay

---

### Post by Aramis on 2006-05-18
**@IYY**

Thanks a lot for this very quick reply, I did not know about *killall*. However, I do not believe that it exactly answer my needs. Granted it is far simpler to perform a *killall* rather than search, find PID and perform *kill*.

I have to say, I was suprised that I could not find any material explaining how to stop such processes programmatically.

Cheers,

Ar@mi$

---

### Post by bboozzoo on 2006-05-21
first off, write several scripts that handle starting and stopping of any deamon you want

```

#!/bin/sh
<yourprog> &
echo $! > /var/run/<yourprog>.pid

```

and for stopping

```

#!/bin/sh
kill < /var/run/yourprog.pid

```

or even one script for starting all the deamons you need, see it's always easier to do such things from shell than from C or any other language program

---

