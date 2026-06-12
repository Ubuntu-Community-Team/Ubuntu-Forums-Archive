---
title: "shutdown from task manager"
date: 2018-10-23
forum: New to Ubuntu
---

### Post by cybervigilante on 2018-10-23
Now and then things don't work and I can't get a shutdown. ctrl-alt-bksp doesn't do anything, but ctrl-alt-del raises the task manager. So the question is, what do I shut down in the task manager to shut down lubuntu?

---

### Post by ajgreeny on 2018-10-23
Not sure about the task-manager but if you can open a terminal you can shutdown with command ```
shutdown -h now
```
You shouldn't need to use sudo for this.

If the system has completely frozen you can try holding **R-Alt (Alt-Gr) + PrintSc** then slowly type **r e i s u b** with about one second between presses.

---

### Post by Holger_Gehrke on 2018-10-23
If ctrl+alt+del gives you a task manager, then the system is not completely hung. The task manager in Ubuntu and its various flavours is not a special privileged program as it is in Windows, it's just a normal application which has been assigned a key combination. You should be able to open a terminal either with a hot key (windows-key+t, ctrl+alt+t) or from the menu. If neither works you can use one of the virtual terminals. Hit ctrl+alt+(one of the function keys from f1 to f6). The system will switch to a text mode and you'll be prompted for your username and your password (which is not echoed when you enter it; not even as a row of asterisks). You now have a shell and can either try to kill whatever process is hanging (use top or htop or ps to find the process and kill or pkill to stop it; there are manual pages for all of these on your system which you can read by entering man and the name of the command in a shell). Or you can 'shutdown -h now' to shut down or 'shutdown -r now' for reboot.

Holger

---

