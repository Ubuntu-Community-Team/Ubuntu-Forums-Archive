---
title: "[SOLVED] Check if Firefox Running in Linux Bash"
date: 2008-09-09
forum: Programming Talk
---

### Post by niccholaspage on 2008-09-09
Another question about the Linux Bash.
I setup a Portable Version of Firefox for Linux with a simple script.Now if the user has a normal copy of firefox running and opens up the Portable Version,The Portable version will use the profile on the computer.Can I somehow check if firefox is running and if it is I can show A Message about this but if it isn't just start firefox? And here is the code I got to start Firefox up portably:
```
#!/bin/sh

./AppLinux/run-mozilla.sh ./AppLinux/firefox-bin -profile ./Data/profile
```It just executes Firefox with a profile in the folder.This is an easy fix probably.


EDIT:fixed.scroll down.

---

### Post by LaRoza on 2008-09-09
If exit value is "0", it is running, else, not running.

```
ps -e | grep "firefox"
```

---

### Post by niccholaspage on 2008-09-09
Ugh...Can you tell me how to do something like this:
```
check=ps -e | grep firefox
```I could probably do this if the command had no spaces.Please guide this stupid guy...

---

### Post by LaRoza on 2008-09-09
> **niccholaspage said:**
> Ugh...Can you tell me how to do something like this:
```
check=ps -e | grep firefox
```I could probably do this if the command had no spaces.Please guide this stupid guy...
```

check=`ps -e | grep "firefox"`
```

should work (note, those are back tics, not quotes)

Or you could just run it, and check the variable $? right after.

---

### Post by niccholaspage on 2008-09-09
Thanks so much!

---

### Post by niccholaspage on 2008-09-09
Now it says Firefox is open any time I run the script.Here is the code right now:
```

#!/bin/sh
check=`ps -e | grep "firefox"`
if check=0
then
zenity --info --text "Please Close any Firefox Proccesses"
else
./AppLinux/run-mozilla.sh ./AppLinux/firefox-bin -profile ./Data/profile
fi

```

---

### Post by ghostdog74 on 2008-09-09
why don't you do it all for the user
```

#!/bin/bash
pgrep firefox 1> /dev/null && pkill firefox
./AppLinux/run-mozilla.sh ./AppLinux/firefox-bin -profile ./Data/profile

```

---

### Post by niccholaspage on 2008-09-09
Killall will force the application to quit.I don't want it to do this.

---

### Post by mssever on 2008-09-09
Note that the normal purpose of doing ./some_file is to provide a path for the shell to look up the executable you're referencing. Normally, there's no reason to use the ./ if you're just referencing a file (e.g., in the parameters to another command).

---

### Post by Martin Witte on 2008-09-10
> **niccholaspage said:**
> Now it says Firefox is open any time I run the script.Here is the code right now:
```

#!/bin/sh
check=`ps -e | grep "firefox"`
if check=0
then
zenity --info --text "Please Close any Firefox Proccesses"
else
./AppLinux/run-mozilla.sh ./AppLinux/firefox-bin -profile ./Data/profile
fi

```
You probably want to check the exit code of the grep command, if it is 0 then firefox is found in the output of ps -ef, without the grep command, that's why I added the grep -v grep to the command
```

#!/bin/sh
check=`ps -ef|grep firefox|grep -v grep`
if [ $? -eq 0 ]
then
.....

```

---

### Post by niccholaspage on 2008-09-10
Thanks! Now it works great.

---

