---
title: "[BASH] Scripting Questions"
date: 2011-11-06
forum: Programming Talk
---

### Post by hantechbl on 2011-11-06
I have a several questions pertaining to a combination of BASH functions:

1) Is it possible to read output from screen (in the background), and if so only parse new lines, then based upon those parsed lines perform certain actions?

2) Is it possible to cycle through a BASH array?

3) Is there a way I can download PHP output from a webserver and save it as a file without WGET.

4) Is there a way that I can have the INIT start a script as a different user and have it run in the background?

5) Can I set a description for a Process so I can retrieve PID for multiple of the same process, or as I launch the program can I export the PID to a variable?  If so How?

6) Is it possible that I can save data to a remote MySQL server, if so how?

---

### Post by ofnuts on 2011-11-06
> **hantechbl said:**
> I have a several questions pertaining to a combination of BASH functions:

1) Is it possible to read output from screen (in the background), and if so only parse new lines, then based upon those parsed lines perform certain actions?Depends where the output comes from
> **hantechbl said:**
> 2) Is it possible to cycle through a BASH array?Yes
> **hantechbl said:**
> 3) Is there a way I can download PHP output from a webserver and save it as a file without WGET.Yes, use curl instead. Seriously, don't expect to do this properly on your own, unless you have lots of time on your hands. There are plenty of details to take care of, even for fairly basic connections.
> **hantechbl said:**
> 4) Is there a way that I can have the INIT start a script as a different user and have it run in the background?A bit outside of my knowledge but should be doable since I see several daemons running under their own ids.
> **hantechbl said:**
> 5) Can I set a description for a Process so I can retrieve PID for multiple of the same process, or as I launch the program can I export the PID to a variable?  If so How? When you start a process its PID is avaialble in the special variable "$!", so to start several processes in the background and wait for them to terminate:
```

# where we keep the PIDs of the launched stuff
set -a pids

# launch background processes and store the PID
for f in ***stuff_to_launch***
do
 *** launch_stuff ***&
  pids[${#pids
[*]}]=$!
done

# Wait for all processes to terminate
for pid in ${pids
[*]}
do
  wait $pid
  print "Sensed end of $pid"
done

```

> **hantechbl said:**
> 6) Is it possible that I can save data to a remote MySQL server, if so how?I never used mySQL, but if it's like the others, its 1) a matter of configuring the DB to accept remote connections, and 2) configure the remote client (ie, your side) to tell it where (IP/port/name, usually) the DB is.

---

### Post by hantechbl on 2011-11-06
So for detecting the PID, if I wanted to get the ProcessID of the screen I created I would do this?:
```
command &
  processid=$!
```
More Specifically I want to create a screen session.

---

### Post by ofnuts on 2011-11-06
> **hantechbl said:**
> So for detecting the PID, if I wanted to get the ProcessID of the screen I created I would do this?:
```
command &
  processid=$!
```More Specifically I want to create a screen session.Yes

---

