---
title: "make file open terminal and run commands"
date: 2020-07-18
forum: New to Ubuntu
---

### Post by e-sans on 2020-07-18
i have been trying to make a file that i can double click and it will open gnome terminal then go to a different disk partition and then to a directory and run a command
i have been able to make the file open the gnome terminal but i do not know how to make it automatically run commands
is it possible for the file to open at boot too?

Ubuntu 20.04

Edit:
would it also be possible to run the command with higher priority?

---

### Post by GhX6GZMB on 2020-07-18
You need to look at writing "scripts". Those are text files that contain commands. A script can be made executable.

---

### Post by monkeybrain20122 on 2020-07-20
> **e-sans said:**
> i have been trying to make a file that i can double click and it will open gnome terminal then go to a different disk partition and then to a directory and run a command
i have been able to make the file open the gnome terminal but i do not know how to make it automatically run commands
is it possible for the file to open at boot too?

Ubuntu 20.04

Edit:
would it also be possible to run the command with higher priority?

It is not very clear what you want to do but if I understand correctly you can just make a script to run the command without invoking the terminal since the script is not interactive (that seems to be your whole point, right? otherwise you can just type the command in the terminal yourself) So it is something like
```

#! /bin/bash

cd /path/to/directory &&  command
```

(or command "$@" if your command acts on a file, in that case also add %F to the end of the EXEC= line in the .desktop file, see below)

Where "command" is the command you want to run. Make this file executable (right click, properties > Permission and check the allow to execute box), put it in your $PATH (either /home/your_username/bin or /home/your_username/.bin,  if the bin folder doesn't already exist, just create them, but in that case you have to logout and login afterwards for it to be picked up) 

Now you can make a .desktop file (a launcher) so you can click it to launch your script. You can lookup any .desktop file in /usr/share/applications to copy the template. Now  put this file in /home/user_name/.local/share/applications and make it executable and you should see the launcher in your menu or dash (Now gnome-shell might have remove the ability to launch desktop files in .local/share/applications. If that is the case you may need other workaround, like moving it to /usr/local/share/applications)

---

