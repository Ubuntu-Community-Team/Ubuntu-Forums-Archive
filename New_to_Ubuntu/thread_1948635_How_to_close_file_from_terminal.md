---
title: "How to close file from terminal"
date: 2012-03-28
forum: New to Ubuntu
---

### Post by Eleness on 2012-03-28
Hi! I just want to know how can I close a file from the terminal. I open it with gnome-open and want to close from there also... there is a way to do that?

And can I see and close processes from the terminal? (Linux has "processes", right? Like those from ctrl+alt+del in windows?). Yes, absolute begginer =]

---

### Post by kc1di on 2012-03-28
usually you can just exit the terminal and file will close.

---

### Post by forrestcupp on 2012-03-28
The terminal command for killing a process is 
```
killall *name-of-process*
```

But it's easier to see all of the processes and end them with the System Monitor, instead of the command line. That's kind of like what you get with ctrl-alt-del in Windows.

---

### Post by audiomick on 2012-03-28
The equivalent to ctrl + alt + del on Ubuntu is the system monitor. It has a tab from which you can choose a process and stop it.

From the terminal, I believe the appropriate command is "kill". I don't know how to use it, but you could have a look at the man page
```
man kill
```

---

### Post by winh8r on 2012-03-28
I use```
 terminator 
```as my preferred terminal emulator.

When working in the terminal you can split the screen up into as many terminal windows as you need, and I usually have one with ```
htop
```
running in it.

If there is a process I want to kill, I just need to highlight it in the terminal and hit F9 and enter, process killed cleanly and you are still in the same screen you were in.

It might work for you or it might not, but it is worth a try.

hope this helps.

---

