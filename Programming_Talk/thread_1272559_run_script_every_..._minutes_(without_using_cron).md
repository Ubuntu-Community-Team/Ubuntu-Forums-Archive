---
title: "run script every ... minutes (without using cron)"
date: 2009-09-22
forum: Programming Talk
---

### Post by Claus7 on 2009-09-22
Hello,

I have a script that it runs ok when I invoke it in the folder I'm interested in.
The thing is that I want to make it run every 15 minutes or so and test if a process is running or not. If it finds that this process is not running I want it to finish running as well.

I used crontab for the situation, yet I face some problems with the commands I have in the script and I cannot find a workaround to this, so I do not want to follow such a procedure.

What I want to do is:

I want to run this script every 15 minutes (not all the time). If the process I want to test is on, then keep the script running, if not then stop.

I do not want to use a do loop with finite steps, as I do not know beforehand how much time the process I test will be running (e.g. for i=1, 100000...).

I want to achieve running this script as specific intervals of time, without using cron.

My thought up to now is using the wait command, yet I'm in the stage of how to implement this command in my code.

Thank you,
Regards!

---

### Post by scragar on 2009-09-22
```
#!/bin/bash

while true; do
  [ -z "$(ps -A | grep $1)" ] && exit
  sleep 15m
done
```
```
chmod +x myscript.sh
./myscript.sh programName
```

---

### Post by Claus7 on 2009-09-24
Hello,

thanks very much *scragar* for your answer. About the thing I asked, you already know, that it is working like a charm. The thing is that I want to make it a little bit broader, and come and fit it to the code you supplied, yet the time is pressing a little bit now.

Thanks again,
Regards!

---

### Post by arrange on 2009-09-24
Doesn't work for programName > 15 :(```
ps -A | tail
 3009 ?        00:00:37 multiload-apple
 3012 ?        00:00:00 gweather-applet
 3035 ?        00:00:06 gnome-screensav
 3039 ?        00:00:00 evolution-data-
 3056 ?        00:06:41 firefox
 3738 ?        00:00:07 gnome-terminal
 3739 ?        00:00:00 gnome-pty-helpe
 3740 pts/0    00:00:00 bash
 9791 pts/0    00:00:00 ps
 9792 pts/0    00:00:00 tail
```

---

### Post by scragar on 2009-09-24
> **arrange said:**
> Doesn't work for programName > 15 :(```
ps -A | tail
 3009 ?        00:00:37 multiload-apple
 3012 ?        00:00:00 gweather-applet
 3035 ?        00:00:06 gnome-screensav
 3039 ?        00:00:00 evolution-data-
 3056 ?        00:06:41 firefox
 3738 ?        00:00:07 gnome-terminal
 3739 ?        00:00:00 gnome-pty-helpe
 3740 pts/0    00:00:00 bash
 9791 pts/0    00:00:00 ps
 9792 pts/0    00:00:00 tail
```

Well honestly I'd do it this way then:
```
#!/bin/bash
program_to_launch_here & ## & means background it
PROGRAMS_PID=$! ## keep hold of the PID

while [ ! -z  "$(ps $PROGRAMS_PID | grep $PROGRAMS_PID)" ]
do
  ## stuff
  sleep 15m
done
```

---

### Post by jpkotta on 2009-09-24
Try
```
ps -e -o cmd | grep -vE '^(grep|ps)' | grep $program_name
```

---

### Post by Bodsda on 2009-09-24
What happened to posting links instead of code? 

Giving the OP a fully functional piece of code is hardly going to help him.

===

I would do exactly as the OP said, use a while loop with a wait/pause statement. Something along the lines of

```

def check_for_prog(progname:
    # Check if progname is running, then:
    if "yes":
        return True
    else: 
        return False
check_prog = prog_name
while check_for_prog(check_prog):
    perform stuff
    sleep(sometime)

```

---

