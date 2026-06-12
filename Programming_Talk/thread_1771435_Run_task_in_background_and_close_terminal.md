---
title: "Run task in background and close terminal"
date: 2011-05-30
forum: Programming Talk
---

### Post by mogeb on 2011-05-30
Hi all,
i have to something similar to this in a .bash script:

gksudo gedit
exit

After double-clicking on the .bash file and selecting "Run in terminal", a terminal opens, then gksudo asks for a password and gedit runs. I would like to hide the terminal at this point, so gedit would still run but the terminal window would be closed or hidden (so the exit wouldnt wait gedit to return). 
Any way to do that?

Thank you

---

### Post by juancarlospaco on 2011-05-30
nohup gksudo gedit

---

### Post by mogeb on 2011-05-30
Thanks for your reply.. Already tried it, doesnt work. The terminal window stays.

---

### Post by juancarlospaco on 2011-05-30
Do NOT "Run in terminal", just run it...

---

### Post by mogeb on 2011-05-30
I have to run it in a terminal because there is interaction between the user and the console that happens before..

Is there anyway to know if the user clicked on "Run" or "Run in terminal"?

---

### Post by epicoder on 2011-05-30
```
nohup command &
```The script will continue without waiting for command to finish, and if it exits before command does, command will stay running.
Nohup catches the hangup signal sent by a terminal/script when it exits. & runs the command in the background and allows the script to continue while the command is running.

---

### Post by mogeb on 2011-05-31
Tried it too, but didn't work. I found another solution though. By adding the following lines: 

```

gnome-terminal --command=$0
exit

```That way, a terminal opens even if the user selects "Run"

---

