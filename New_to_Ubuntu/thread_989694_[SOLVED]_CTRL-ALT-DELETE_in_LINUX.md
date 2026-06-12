---
title: "[SOLVED] CTRL-ALT-DELETE in LINUX ?"
date: 2008-11-21
forum: New to Ubuntu
---

### Post by dblxx on 2008-11-21
Every so often the system locks up and I don't know how to release stuck programs?

I have the "force misbehaving apps to quit" icon but I am not sure I am using it right.  Sometimes that doesn't work either.

Thanks....I appreciate the help.

---

### Post by taurus on 2008-11-21
If a program hangs and you want to terminate it, you can "kill" it from a terminal.  This command 

```
ps -A
```
will show you all the processes with the PID (first column).  You can kill a process by typing in the PID.  Let's say you want to kill a program that has a PID of 1234, you would do

```
sudo kill -9 1234
```
or you can use the name of the program too.

---

### Post by Zantaskan on 2008-11-21
there is also a Force-quit panel applet that kills the program selected.

Also you can use System monitor Tool to kill programs. This looks very similar to the Windows Task Manager window 

System-> Administration-> System Moniter

---

### Post by Kinst on 2008-11-21
Ctrl + Esc

---

### Post by kreeten9996 on 2008-11-21
There is no pre configured Ctrl, Alt, Delete button for Linux, but if you go to System > Administration > System Monitor. its the same as the task manager. What I did was add the launcher to my panel, its just as easy and Ctrl, Alt, Delete.

---

### Post by daimaru on 2008-11-21
If your system is unresponsive you probably wont be able to open a terminal (the normal way) so you will have to hit ctrl+F2 to get to a console prompt and then you can follow the advice given by taurus . 
```
ctrl+F2
log in with your username and password
ps aux
kill -9 [processID number]
```if you can still run console from within your graphical desktop environment you can use 
```
killx
```your cursor will turn into a skull and you can click the application you want to kill.

Another way is to restart the gdm (graphical display manager) by hitting ctrl+alt+backspace.

If the system is totally non-responsive use the *Alt*+*PrtSc+*(R-E-I-S-U-B) command.
PrtSc = PrintScreen button also called "SysReq".

---

### Post by Keen101 on 2008-11-22
I set up a keyboard shortcut for System Monitor on my system. I had to edit some files though, and it took me awhile to figure it out. I couldn't get Ctrl + Alt + Del keys mapped to it, but i got Ctrl + Alt + Break to work.

---

### Post by lykwydchykyn on 2008-11-22
The key sequences of desperation:

ctrl-esc = bring up process list, kill processes
ctrl-alt-esc = launch xkill, and kill a stuck program
ctrl-alt-backspace = kill your GUI session and return to the login prompt
(alt-sysrq)+ rseiub (hold alt and sysrq while typing "rseiub") = attempt to safely reboot in the event that you can't get any response from keyboard or mouse.

---

### Post by jyaan on 2008-11-22
If a full-screen app ever locks up I just use CTRL+ALT+F1 to get a console. F1-F6 all work, and F7 will is the GUI. CTRL+ALT+SysReq is good when there's no other choice, and definitely worth mentioning. You'll want to look it up since there are various keystrokes involved with it. The SysReq key, if not labeled on your keyboard, is the same key as Print Screen.

---

### Post by lykwydchykyn on 2008-11-22
to be clear, jyaan, it's just alt-sysrq, not ctrl-alt-sysrq.  Though I don't know if adding ctrl would make it not work.

[http://en.wikipedia.org/wiki/Magic_SysRq_key](http://en.wikipedia.org/wiki/Magic_SysRq_key)

---

### Post by dblxx on 2008-11-22
CRAP....I did the ctrl+alt+F1 and a black screen came up.  I was lost and didn't know how to get back :)

I need to learn this system.

---

### Post by lykwydchykyn on 2008-11-22
You'd hit ctrl-alt-f7 to get back to the GUI.

---

### Post by jyaan on 2008-11-22
You're right about SysReq. I overlooked it somehow. I don't mean to give out bad info, sorry! I have no idea whether it would work with CTRL pressed either, though.

---

