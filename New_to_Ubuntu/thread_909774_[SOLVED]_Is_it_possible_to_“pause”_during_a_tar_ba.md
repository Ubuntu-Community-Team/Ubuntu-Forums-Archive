---
title: "[SOLVED] Is it possible to “pause” during a tar backup?"
date: 2008-09-03
forum: New to Ubuntu
---

### Post by ityro on 2008-09-03
I have already searched everywhere I can think of and experimented with keyboard shortcuts.  My reason for wanting to pause a backup job is heat.  By the time the backup is halfway  through /usr it is bouncing between 62 and 63 °C.  Can someone please point me in the right direction?  Thank You for your time.

My System:  Dual boot Ubuntu 8.04 (separate home folder) with XP on a HP COMPAQ   nx9010 Notebook,  Intel Pentium 4 CPU 2.66GHz,  706MB RAM,  40GB HDD,  USB 2.0,  CD-R Drive,  Floppy Drive,  80GB External HDD.  Single user for home use only.

---

### Post by unutbu on 2008-09-03
Any command-line (um...) command can be paused. For example, if you type

```
tar cf backup.tar /backup/dir
Ctrl-Z
```
The tar command will be paused. 
To resume, type

```
fg
```

fg puts the process back in the foreground.

---

### Post by Cheesehead on 2008-09-03
If you are allergic to the command line, you can also 'stop' (pause) and 'continue' (resume) a process using System Monitor. Simply right-click on the process.

---

### Post by ityro on 2008-09-03
> **unutbu said:**
> Any command-line (um...) command can be paused. For example, if you type

```
tar cf backup.tar /backup/dir
Ctrl-Z
```
The tar command will be paused. 
To resume, type

```
fg
```

fg puts the process back in the foreground.

Have tried CTRL+Z but will try again. Will try the system monitor trick also. Thank you both for your reply and thanks again for your time.

---

### Post by unutbu on 2008-09-03
Here is a little script I wrote which might make the task a little easier. Save the script as slowcmd.sh

```

#!/bin/bash

# Usage:
# slowcmd.sh tar cf ~/backup.tar /usr/src/linux-2.6.25

"$@" &
PID=$!
echo "PID is $PID"
TOGGLE='Resume'
RUN_SECONDS=2
PAUSE_SECONDS=10

function procnumber () {
    echo `ps ax | awk -v var=$1 '{if($1==var){printf("%d", $1)}}'`
}

while [ "$PID" != "" ]; do
    if [ "$TOGGLE" = "Pause" ]; then
	echo "Stopping PID $PID"
	kill -s STOP $PID
	sleep "$PAUSE_SECONDS"
	TOGGLE='Resume'
    else
	echo "Resuming PID $PID"
	kill -s CONT $PID
	sleep "$RUN_SECONDS"
	PID=$(procnumber $PID)
	TOGGLE='Pause'
    fi
done

```

Make it executable:
```

chmod 755 slowcmd.sh

```
Run it like this:
```

slowcmd.sh tar cf ~/backup.tar /usr/src/linux-2.6.25
```
You can put any command you wish after slowcmd.sh.
It will run for 2 seconds, then pause for 10 seconds, run, then pause, run, then pause...
You can edit the script's RUN_SECONDS and PAUSE_SECONDS to tweak the behavior. It will keep on flip-flopping until the tar command is done.

---

### Post by ityro on 2008-09-03
Both the Ctrl+Z and system monitor methods work. My problem was finding the word stop when I was looking for pause. Thanks again.

I will try the script but will take awhile because that's new ground for me. Thank You.

---

