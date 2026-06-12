---
title: "[SOLVED] Make shell script exit as soon as a command in it returns an error?"
date: 2008-12-11
forum: Programming Talk
---

### Post by jasper.davidson on 2008-12-11
I would like to make my shell script so that if any of the commands in it return an error, the script immmediately exits without executing the rest of the commands. What might be the best way of doing this? One way that seems to work is:
```
#!/bin/bash
cmd1 || exit 1
cmd2 || exit 1
cmd3 || exit 1
etc.
```
In other words, putting "|| exit 1" at the end of each executed command. Is there a better way I hope? Thanks in advance.

---

### Post by dwhitney67 on 2008-12-11
Do something like this:
```

#!/bin/sh

set -e

...

```

If you are using bash script, then change the "sh" to "bash".

---

### Post by jasper.davidson on 2008-12-11
Thank you very much, dwhitney67, that's exactly what I was looking for. I knew there had to be a better way than putting "|| exit 1" at the end of each command. :)

---

### Post by jasper.davidson on 2008-12-11
One more question though if you have time; is there any way to exclude a single command from causing the script to exit when I use "set -e" at the beginning? In other words, there are just a few commands in my script that it doesn't matter if they return an error, and I don't want the entire script to terminate for those few commands. Is there possibly some way around that? Thanks again.

EDIT: I think I found a workaround, although it probably isn't the best solution again:
```

#!/bin/bash
set -e
cmd1
cmd2
#exclude next command from causing script to terminate:
set +e; cmd3; set -e
#continue:
cmd4

```

---

### Post by dwhitney67 on 2008-12-11
If you only have a few cases where the failure of a command is not important, then I would toggle the "e" option as you have done.

Or you could do something cheesy like:
```

#!/bin/bash

function execCmd()
{
  eval "$1"

  status=$?

  if [[ $status -ne 0 && "$2" != "ignore" ]]
  then
        echo "stopping..."
        exit $status
  fi
}


# Main

execCmd "ls"
echo "continuing..."
echo

execCmd "touch /foo" "ignore"        # ignore error for this command
echo "continuing..."
echo

execCmd "touch /foo"                 # terminate script if this fails

# should not reach here
echo "done"

```

---

### Post by mssever on 2008-12-11
> **jasper.davidson said:**
> One more question though if you have time; is there any way to exclude a single command from causing the script to exit when I use "set -e" at the beginning? In other words, there are just a few commands in my script that it doesn't matter if they return an error, and I don't want the entire script to terminate for those few commands. Is there possibly some way around that? Thanks again.

EDIT: I think I found a workaround, although it probably isn't the best solution again:
```

#!/bin/bash
set -e
cmd1
cmd2
#exclude next command from causing script to terminate:
set +e; cmd3; set -e
#continue:
cmd4

```
The easiest way to ignore errors from one single command is to do ```
somecommand || true
```

---

### Post by dwhitney67 on 2008-12-11
> **mssever said:**
> The easiest way to ignore errors from one single command is to do ```
somecommand || true
```
Why didn't I think of that??!

That does make it easier.

---

### Post by jasper.davidson on 2008-12-11
That's a great way to exclude a command from causing the script to terminate, mssever. Thanks for the help. :)

---

