---
title: "Why does this simple bash script pause after the first command?"
date: 2011-08-27
forum: Programming Talk
---

### Post by malien on 2011-08-27
I want to open three programs with this simple bash script, but it stops after opening the first program. If I close that program the others open, but why? And how can I open them all at once?
```

#! /usr/bin/bash
thunderbird
firefox google.com
python3 /usr/lib/python3.2/idlelib/idle.py

```Thanks

---

### Post by JupiterV2 on 2011-08-28
Because the script is waiting for your command to exit. You need to use the ampersand '&' character after each command in order to spawn a new process for the individual program and allow your script to continue running.

---

### Post by ofnuts on 2011-08-28
> **JupiterV2 said:**
> Because the script is waiting for your command to exit. You need to use the ampersand '&' character after each command in order to spawn a new process for the individual program and allow your script to continue running.
However... when doing so there are cases where the started programs will be children or grandchildren of the bash shell(*), so closing the terminal will kill them without any warnings (which may be a problem, especially for IDLE).
In KDE there is a "kstart" command to start commands as children of the desktop process (it will take the command as a parameter or a .desktop file). There is very likely an equivalent for Gnome and other environments.

(*) I haven't determined exactly what happens... in some cases it seems bash Does The Right Thing so you may be lucky.

---

### Post by Karlchen on 2011-08-28
Hello, malien.

thunderbird (/usr/bin/thunderbird) and firefox (/usr/bin/firefox) are shell scripts. They will return control to the calling script, your script, only after they have finished.
To work around this challenge it is suggested you modify your script to read:
```
#! /bin/bash
# My Ubuntu tells me there is /bin/bash, but no /usr/bin/bash

# Go to a folder where you are guaranteed to have write privileges
cd

# detach thunderbird and firefox from this script
nohup thunderbird &
nohup firefox google.com &

python3 /usr/lib/python3.2/idlelib/idle.py
```Maybe you will have to surround the python commandline by "nohup" - "&", too.

HTH,
Karl

---

