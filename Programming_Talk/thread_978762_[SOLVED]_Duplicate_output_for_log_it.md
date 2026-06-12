---
title: "[SOLVED] Duplicate output for log it"
date: 2008-11-11
forum: Programming Talk
---

### Post by debuti on 2008-11-11
Hi all.

I'm making a bash script.
I want it's output is printed to the console as well as to a file.
How to do that ?

Currently I do that plainly stupid like this
-----------------------
LOG=/var/log/mylog

echo Hello
echo Hello >> $LOG

echo Hello again
echo Hello again >> $LOG

echo Another hello again
echo Another hello again >> $LOG
---------------------

There must be a smarter way.  Please show me. Thanks

---

### Post by melopsittacus on 2008-11-11
I am not sure whether this works, but you could try removing the lines that write into files. Then you could call the script with two redirections:

./yourscript >/var/log/mylog >&1

Unfortunately I cannot try this out right now in Ubuntu as I am logged in Windows.

---

### Post by dwhitney67 on 2008-11-11
Use 'tee'.

For example:
```

#!/bin/sh
LOG=/var/log/mylog

echo My message is | tee -a $LOG
echo not that important. | tee -a $LOG
...

```
Of course, you will need the appropriate permissions to create a file in /var/log.

---

### Post by geirha on 2008-11-13
You can also do some bash magic at the beginning and the end of the script to avoid piping to tee for every echo.

```

#!/bin/bash

LOG=/tmp/logfile
# Save current stdout to file descriptor 3, and redirect stdout to tee
exec 3>&1 > >(tee -a "$LOG")

echo This will be output both to the logfile
echo and stdout

# Restore stdout and close file descriptor 3 before we exit
exec 1>&3 3>&-

```

---

