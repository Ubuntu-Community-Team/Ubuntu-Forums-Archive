---
title: "Equivalent of Windows Task Manager?"
date: 2008-09-22
forum: New to Ubuntu
---

### Post by lavadisco on 2008-09-22
When a program goes on the fritz, I sometimes cannot for the life of me find the "force quit" function no matter where I look. Is there the equivalent of a Windows task manager in Ubuntu? Or perhaps a keystroke that will allow me to force-quit an app?

---

### Post by nowshining on 2008-09-22
have u tried system monitor -that and there should be an applet to add right-click add to panel and find something called xkill, kill, quit, force quit, or something as i don't use gnome but have and forgotten the name of it...

or in a terminal try the command xkill then move the now eXed cursor over the program u'd like to force quit..

U can also quit from the terminal as well

killall nameofprogram and add sudo infront of that if the program wasn't started from u, etc..

then u got killall -9 then the name of the program and same as above but the -9 does a force kill while just killall tires to shut it down gracefully and now if you get into a real jam, freeze, try ctrl+alt+backspace on ur keyboard to force a logout and re-login and everything should be fine..

---

### Post by thunk77 on 2008-09-22
Hello,

You can either open up a terminal and type "killall [Name Of Application], or Alt+F2 and do as above.
Hope this is helpful.

Best Regards

thunk

---

### Post by ghostdog74 on 2008-09-22
> **lavadisco said:**
> When a program goes on the fritz, I sometimes cannot for the life of me find the "force quit" function no matter where I look. Is there the equivalent of a Windows task manager in Ubuntu? Or perhaps a keystroke that will allow me to force-quit an app?

use the command line ps. Then check which pid the process takes, then issue kill -9 <pid>

---

### Post by prshah on 2008-09-22
> **lavadisco said:**
> When a program goes on the fritz, I sometimes cannot for the life of me find the "force quit" function no matter where I look. Is there the equivalent of a Windows task manager in Ubuntu? Or perhaps a keystroke that will allow me to force-quit an app?

Right click any of the panels, then click "Add" and choose the applet "Force quit". When next an application misbehaves, click the "Force quit" icon on the panel (the cursor changes to a crosshair) and then click anywhere in the misbehaving (probably grey) application window. It will forcibly close down the application after confirmation.

Of course the other tips in this thread are handy as well (what will you do if the "panel" itself misbehaves :) )

Also, if you have the system-monitor applet running, you can click on it for a "windows task-manager"-like window, Right click the process you want to kill (probably having status of "Zombie") and choose "Kill process".

---

### Post by schmick on 2008-09-22
There are 2 aproaches:
Windows-like-taskmanager (gnome-system-monitor)
  Press ALT-F2
  Type gnome-system-monitor
  Press Enter
  There you got it!.. 
  Go to the process tab
  Find the offending app, and RightClick-End Process. (that's the nice way.)
  App won't go? KILL IT!
  Still there?.. hmm.. it's a Zombie (Check Status column)
  Then press Ctrl-D (show dependencies)
  Find the Parent process, and END/KILL that one. (Be carefull with what you kill).

Command line approach
  Open a Terminal
  Type ps aux|grep <badd app name> (i.e ps aux|grep wine)
  The second column is your PID (process ID)
  Try to end it nicely with kill <pid> (i.e. kill 23912)
  Search for it again (the ps aux thing)
  Still there? KILL it until it's dead!... with a stone or something.. (KungPow I)
  type kill -9 <pid> (I guess you get the idea now).

OK. Homework.
¿How to get the PPID (Parent) of a PID?
Read the manual!
Type man ps and see what you have to type to get the PPID of a zombie.

---

### Post by lazyart on 2008-09-22
System>Administration>System Monitor

---

### Post by natman on 2008-09-22
i always open a terminal and
[HTML]top[/HTML]
Loads of detail and friendly, also in KDE there is a nice system trap applet for usuage

---

### Post by jemate18 on 2008-09-22
to find out process running

Applications -> Accessories -> Terminal

```
top
```

then find the process id.

to scroll press > or <

if you found the process id and want to quit

type q

then type 
```
kill -s 9 theprocessid 
```

---

### Post by lavadisco on 2008-09-22
Thanks very much guys!

---

### Post by brawnypandora0 on 2011-05-01
DO these commands apply for all Linux distributions, or just Ubuntu?

---

