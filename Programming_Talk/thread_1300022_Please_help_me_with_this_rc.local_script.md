---
title: "Please help me with this rc.local script"
date: 2009-10-24
forum: Programming Talk
---

### Post by barisurum on 2009-10-24
```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

chrt -f -p 95 5
chrt -f -p 95 11
chrt -f -p 95 19
chrt -f -p 95 25
chrt -f -p 95 772

chrt -f -p 90 1552

exit 0
```

I can succesfully increase the priorities of the first five processes (timers) as their process ids don't change with boot, but the last id changes with every boot (soundcard driver). How can I change the last line of the script to find out the process id of the alsa driver? (module name is ICE1724). Thanks.

---

### Post by barisurum on 2009-10-26
anyone pliiiiz 'elp meee! :)

---

### Post by Stochastic on 2009-10-26
Moved to Programming Talk, as many more bash experts will be able to help you here.

---

### Post by barisurum on 2009-10-27
Bump

---

### Post by falconindy on 2009-10-28
If you know the name of a process, you can use pgrep to find the process ID, ergo:
```
chrt -f -p 90 `pgrep name-of-program`
```
Those backquotes (to the left of your 1 key) are necessary.

This seems... dangerous and unnecessary. What are you trying to accomplish?

---

### Post by barisurum on 2009-10-28
I'm willing to increase the priority of system timers and my soundcard driver. Hoping this will provide a more sane rt environment for studio work. So you say it's dangerous... What could be the consequences? 

Thanks for your info and stochastic for moving the thread to programming talk.

---

### Post by falconindy on 2009-10-28
Altering behavior and priorities of processes, especially system processes, can lead to instability. You do have a legit reason for wanting to do so, though. Save your work often ;)

---

### Post by Zugzwang on 2009-10-28
It should be enough to alter the process priorities *once* after the system has booted. Is there a special reason why you do it at every run-level?

---

### Post by barisurum on 2009-10-28
> Is there a special reason why you do it at every run-level?

The process ids of realtime processes default to 50 with every boot. 

The reason why I need to increase the priority of my soundcard is no matter what I do in BIOS ubuntu gives IRQ number 18 to my soundcard and its a bad number for realtime audio work. So I have to hack the driver priority to remedy this problem.

edit: by the way this hack works quite well.. :)) cheerz! :)

---

