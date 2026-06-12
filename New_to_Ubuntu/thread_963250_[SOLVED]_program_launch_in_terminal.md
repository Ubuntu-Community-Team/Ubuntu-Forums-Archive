---
title: "[SOLVED] program launch in terminal"
date: 2008-10-30
forum: New to Ubuntu
---

### Post by jsshere on 2008-10-30
is there a way to launch a program in terminal as a separate process rather than as a process that runs under gnome-terminal?

---

### Post by nhasian on 2008-10-30
so it doesnt tie up the terminal?  Yes, just add the & (ampersand) sign after the command.  it will run the command in the background and allow you to keep working in the terminal.

---

### Post by ad_267 on 2008-10-30
Sometimes the program will still output stuff to the terminal which can be annoying so you can do:
```
command_name >& /dev/null &
```

---

### Post by blesbok on 2008-10-30
alternatively, if you want to be able to close the terminal without the child process dying:

setsid command_name

the command will then run under a session with a separate identity

---

