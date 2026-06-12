---
title: "Startup Script?"
date: 2007-02-21
forum: Programming Talk
---

### Post by jacobdis on 2007-02-21
I want to create a script that runs on startup (obviously) and runs a terminal on every command in a specified file, i.e ~/startupcmds.txt. This will be so I can make it easy to add any neccasery programs to my startup, just by modifying the startupcmds.txt file. Any suggestions?

---

### Post by Ramses de Norre on 2007-02-21
Add the commands in /etc/rc.local.

---

### Post by nereid on 2007-02-21
You can just add a bash script to your session (GNOME) or to the autostart (KDE). This script will then run your commands (something like *xterm -e top*, I'm sure this also works with the equivalent counterpart terminal from GNOME or KDE).

**EDIT:**
The commands in /etc/rc.local will be executed right after booting. My solution will be executed after you've logged into your desktop environment.

---

### Post by jacobdis on 2007-02-21
Thanks for the quick replies.  The rc.local file did infact attempt to execute my commands before Ubuntu was fully booted, which may come in handy later, but I was looking for the latter.

nereid: I remember modifying a session when I was following the instructions of a beryl installation, but I can't recall where exactly the file was?

---

### Post by nereid on 2007-02-21
Just write your bash script and then add it to the session manager (Settings->Session or something like that).

---

### Post by jacobdis on 2007-02-21
The session manager had a Startup Programs tab, precisely what I was looking for. Thanks for your kind help.

---

### Post by whac on 2007-02-28
I made a script and added it to my homedirectory for easy-editing. Then i added it to system>settings>sessions.

First make a file named start.sh (with nano for example)

```
nano start.sh
```

then you add to your file for example:

```
#!/bin/sh
sleep 2
tilda &
sleep 2
pygmy &
sleep 6
adesklets
sleep 10
adesklets --nautilus &
sleep 2
tilda &
sleep 4
amsn
```

then you save and goto system>settings>session> and add /home/user/start.sh and reboot or ctrl+alt+backspace

---

