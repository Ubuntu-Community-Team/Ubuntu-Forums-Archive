---
title: "[SOLVED] im new, sorry...."
date: 2008-08-20
forum: New to Ubuntu
---

### Post by hyperhopper on 2008-08-20
sorry, im new to linux, just installed it via wubi yesterday, and am trying it before i use my boot disc to wipe out windows. it was going fine, and i was in about:config in firefox speeding it up, but then i acidentally hit something (maybe ctrl+alt+f1) and it turned into a black text screen only.it just says something about a tye help for a list of internal commands, and when i try exit i just get the help message again. can anybody help me???:confused:

*im  doomed*

---

### Post by tarps87 on 2008-08-20
Yep you've killed it, only joking. press ctrl+alt+F7
ctrl+alt+F1 took you into a unix session (technically POSIX but that's a different story)
ctrl+alt+F7 is your gui session
If ctrl+alt+F7 does not work login and type
```
sudo reboot
```

---

### Post by decoherence on 2008-08-20
alt F7 will get you back to the GUI

you accidentally switched to a virtual console. The thermo-nuclear version of Ctrl Alt Delete

---

### Post by cpetercarter on 2008-08-20
Welcome aboard. You're not doomed. You just found out how to run a terminal from the keyboard. You can in fact run up to 6 terminal screens at once (ctrl+alt+F1 to F6), and ctrl+alt+F7 brings back the normal desktop.

---

### Post by hyperhopper on 2008-08-20
THANK YOU!:KS 
i hope i can get used to linux, but this will at least get me started :) im getting used to it because my family has about 4 comuters without an os so I am trying to gain enough knowledge to fix whatever they screwup (they didnt know what a desktop was a few days ago..), and whetever i screw up too!

---

### Post by kaboodle_fish on 2008-08-20
> **hyperhopper said:**
> THANK YOU!:KS 
i hope i can get used to linux, but this will at least get me started :) im getting used to it because **my family has about 4 comuters without an os** so I am trying to gain enough knowledge to fix whatever they screwup (they didnt know what a desktop was a few days ago..), and whetever i screw up too!
 
Why not take one of these four and put Ubuntu on it and then you can learn without worrying about breaking it or the having to stress about the loss of data.

---

### Post by linuxguymarshall on 2008-08-20
I have a question relating to CTRL + ALT + F1. When I do this how can I close an application? Sometimes I load an app and it freezes in fullscreen and I need a way to close it.

---

### Post by tarps87 on 2008-08-20
> **hyperhopper said:**
> THANK YOU!:KS 
i hope i can get used to linux, but this will at least get me started :) im getting used to it because my family has about 4 comuters without an os so I am trying to gain enough knowledge to fix whatever they screwup (they didnt know what a desktop was a few days ago..), and whetever i screw up too!

Don't worry if you can't fix it there will be someone here who can and will be willing to help

---

### Post by Troll_the_Great on 2008-08-20
> **linuxguymarshall said:**
> I have a question relating to CTRL + ALT + F1. When I do this how can I close an application? Sometimes I load an app and it freezes in fullscreen and I need a way to close it.

You have 2 ways of doing it.If you now the name of the application just type
```
killall name_of_application
```
If you don't know what's wrong, type ```
top
``` and this will tell you what applications are running.On the left side is a number called PID.It's different for each application.When you identify the application you want to close you can do as above, or
```
kill PID_number
```
Hope this helps.
Cheers!

---

### Post by tarps87 on 2008-08-20
Also this will list all running programs
```
ps -A
```
and this will list a program by name
```
ps -C <program name>
```
both will give to a pid number and memory/cpu usage which can be used with this Troll_the_Great mentioned:
```

kill <pid number>
```

---

### Post by Sef on 2008-08-20
> Sometimes I load an app and it freezes in fullscreen and I need a way to close it.

With the cursor on the top panel, right click > add to panel > Force Quit > Add > Close.

---

