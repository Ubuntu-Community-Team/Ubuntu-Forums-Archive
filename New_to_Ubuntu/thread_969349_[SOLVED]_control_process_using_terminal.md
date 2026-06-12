---
title: "[SOLVED] control process using terminal"
date: 2008-11-03
forum: New to Ubuntu
---

### Post by melrokz on 2008-11-03
Melvin here. I'd like to know how to close non-responding apps using the terminal.(using ctrl-alt-f1).I mean, a terminal equivalent of system monitor. This is because I get a lot of non-responding apps, and I'm not able to launch system monitor as my full screen hangs.  Please enlighten me?

---

### Post by snova on 2008-11-03
Try xkill. When you run it, it changes the cursor. Click on a window and that's it.

---

### Post by melrokz on 2008-11-03
The whole screen hangs, and I have to use ctrl-alt-f1 and log into non-graphical terminal.

---

### Post by puppywhacker on 2008-11-03
using a terminal I always use the following commands

1. top
top, to show which process eats the most CPU time
and press M to see which one eats the most memory
CTRL+C to break

2. ps auxwww
ps shows you all the processes from all the users, with as much information as possible. You can see in the second row the process id (PID)

3. kill -9 <PID>
ofcourse replace <PID> by the actual process-id
sends the KILL signal to the process, to really kill it without any mercy. In the same way you could also
kill -HUP <PID> ... which is the same as kill -1 <PID>
to reinit a process
or just kill <PID> to go through the normal program's shutdown routine.

goodluck

---

### Post by snova on 2008-11-03
Well, if the entire thing is hanging, try Ctrl-Alt-Backspace, which will restart the X server.

Try htop. I don't think it's installed by default, but it's a nice curses-based process manager.

---

### Post by beercz on 2008-11-03
You could also install top - or even better - htop (in the repos) and run it in terminal (sudo htop).  htop allows you to see what processes are running and you can kill them.

---

