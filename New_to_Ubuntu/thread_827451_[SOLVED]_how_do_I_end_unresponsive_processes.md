---
title: "[SOLVED] how do I end unresponsive processes?"
date: 2008-06-12
forum: New to Ubuntu
---

### Post by Yondergod22 on 2008-06-12
In Ubuntu is there a task manager like the one you press ctrl+alt+del to get to in windows? if not, what's another way to end unresponsive processes?

---

### Post by Xerp on 2008-06-12
You have some choices :) 

kill (or kill -9) from the command prompt

Use the "force quit" applet

Kill the task from the System Monitor

---

### Post by easybake on 2008-06-12
system>administration>system monitor

---

### Post by powerpleb on 2008-06-12
> **Yondergod22 said:**
> In Ubuntu is there a task manager like the one you press ctrl+alt+del to get to in windows? if not, what's another way to end unresponsive processes?

There is, it's in System menu I think

you can also do ```
killall processname
```
in terminal

---

### Post by sam_delta on 2008-06-12
type alt-f2 
then type ```
xkill
``` and your mouse pointer will become a 'cross' just click at the unresponsive window, and it will get killed

sam

---

### Post by bruce89 on 2008-06-12
*xkill* is useful for graphical programs. Just start it in the Alt+F2 dialogue, then click on the program to be killed.

---

### Post by iaculallad on 2008-06-12
Check if the process ID's has the latest process number:

```
ps
```

To kill a process ID (xxx) from ps:

```
kill xxx
```

To kill a process that refuses to die (xxx) from ps:

```
kill -9 xxx
```

---

### Post by Yuki_Nagato on 2008-06-12
GUI:  System>Administration>System Monitor - Click to the processes tab.

For the terminal: 

enter "man killall" for more information.  Allows killing processes if you know the name.

---

### Post by Yondergod22 on 2008-06-12
thanks

---

