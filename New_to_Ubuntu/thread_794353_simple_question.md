---
title: "simple question"
date: 2008-05-14
forum: New to Ubuntu
---

### Post by betterthanjordan79 on 2008-05-14
i was just wondering what was the equivalent to pressing ctrl+alt+delete in ubuntu iof a program freezes cus ive had some problemes with this and i dont know what to do if a program freezes in ubuntu-thanks in advance!

---

### Post by fmartinez on 2008-05-14
In a terminal type: 
$sudo top           #this will give adim rights to a task manager
Here you can kill any application with the "k + PID" 
or
you can press the ctl+backspace to end that xsession.

---

### Post by Elementality on 2008-05-14
Ctrl+Alt+Del will bring up the "Shutdown" panel for Ubuntu, giving you your options to log out, restart, sleep, etc.

---

### Post by Bigtime_Scrub on 2008-05-14
You can do a "force quit" of the program that crashes by hitting

Alt+F2 and then typing in <xkill> and then clicking Run Program.

Your curser will change from a point to an "X". Just left click that x over a program and it will "Force Quit" it for you.

---

### Post by Cypher on 2008-05-14
You can put the System Monitor applet into the top panel on your desktop. Now you can double-click on it to bring up the process viewer if a program should freeze and kill it safely.

The other alternate is to do it from the command line, you can pop up a terminal and then use the "ps" and "kill" commands like
```

ps -eaf | grep <program>
kill -11 <pid>

```

---

### Post by nowshining on 2008-05-14
u can use killall in the Terminal to close it + there should be program - in the applets that will allow u to use a graphical way to do this. Right-clcok on the panel to add an applet.

if u want u c an use TAB completion in the Term to finish up the name, if u type killall +  TAB twice it will show u all running apps. Some need sudo privs to stop.

---

