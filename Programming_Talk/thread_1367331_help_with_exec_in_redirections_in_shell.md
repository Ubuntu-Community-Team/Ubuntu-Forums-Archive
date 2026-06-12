---
title: "help with exec in redirections in shell"
date: 2009-12-29
forum: Programming Talk
---

### Post by piyush.neo on 2009-12-29
plz help me to understand exec better...eg in the script below
```

[COLOR=#000000]#!/bin/bash
# reassign-stdout.sh
LOGFILE=logfile.txt
exec 6>&1           # Link file descriptor #6 with stdout.
                    # Saves stdout.

exec > $LOGFILE     # stdout replaced with file "logfile.txt".

# ----------------------------------------------------------- #
# All output from commands in this block sent to file $LOGFILE.

echo -n "Logfile: "
date
echo "-------------------------------------"
echo

echo "Output of \"ls -al\" command"
echo
ls -al
echo; echo
echo "Output of \"df\" command"
echo
df

# ----------------------------------------------------------- #

exec 1>&6 6>&-      # Restore stdout and close file descriptor #6.

echo
echo "== stdout now restored to default == "
echo
ls -al
echo

exit 0[/COLOR]

```

whats the use of using **exec 6>&1** in the 4th line. Even if we remove it the script will still redirect the output..

---

### Post by Brandon Williams on 2009-12-31
Here are the important parts for understanding the use of exec in that script.
```
exec 6>&1
exec > $LOGFILE
...
exec 1>&6 6>&-
```

The first line opens a new file descriptor, 6, to remember where file descriptor 1 (stdout) was going. The second line redirects stdout to the logfile. The last line directs stdout back to the previously saved location that fd 6 is still pointing to and then closes fd 6.

---

### Post by Arndt on 2010-01-01
> **Brandon Williams said:**
> Here are the important parts for understanding the use of exec in that script.
```
exec 6>&1
exec > $LOGFILE
...
exec 1>&6 6>&-
```

The first line opens a new file descriptor, 6, to remember where file descriptor 1 (stdout) was going. The second line redirects stdout to the logfile. The last line directs stdout back to the previously saved location that fd 6 is still pointing to and then closes fd 6.

Maybe the question is why one bothers to restore stdout. In the script, it's only used in order to say it's been done, nothing more.

---

### Post by Brandon Williams on 2010-01-01
> **Arndt said:**
> Maybe the question is why one bothers to restore stdout. In the script, it's only used in order to say it's been done, nothing more.

Judging from the name of the script, it's an example that shows how input and output redirection is done.

---

### Post by piyush.neo on 2010-01-02
hhmmmm so it is used only to restore the stdout...
thanks....:guitar:

---

