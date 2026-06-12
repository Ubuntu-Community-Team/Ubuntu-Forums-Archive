---
title: "How to terminate running programs like windows?"
date: 2008-08-07
forum: New to Ubuntu
---

### Post by darren884 on 2008-08-07
How do I terminate running programs like windows control alt delete? Thanks

---

### Post by hitlist diary on 2008-08-07
> **darren884 said:**
> How do I terminate running programs like windows control alt delete? Thanks

add the force quit button to your panel

---

### Post by adult swim on 2008-08-07
you might try alt-f4 or ctrl-q

---

### Post by Locutus_of_Borg on 2008-08-08
use xbindkeys to bind the key sequence ctrl+shift+escape to launch gnome-system-monitor

thats what i have at least, and works the same as task manager on windows

---

### Post by Yuki_Nagato on 2008-08-08
From a terminal:

```
top
```
Then press 'q'.
```
killall XXX
```

XXX is the program in "top" that was giving you problems.

---

### Post by darren884 on 2008-08-08
Hey guys also any idea on how to open windows for running programs that are closed but still running?

---

### Post by loligager on 2008-08-08
ok if you go to terminal
type in 
ps aux
then
kill [PID#] 
without []


and there are many process managers
just search in synaptics

---

### Post by Rolcol on 2008-08-08
System > Administration > System Monitor > *Processes Tab.  Find the process and click "End _P_rocess".

> **darren884 said:**
> Hey guys also any idea on how to open windows for running programs that are closed but still running?
What kind of programs?

---

### Post by kpkeerthi on 2008-08-08
Press ALT + F2, then type **xkill** <press-enter>. Now click on the application you want to nuke.

---

### Post by gjoellee on 2008-08-08
the most Windows-like  way must be to go to System->Administration->System Monitor and go to the processes tab

---

### Post by PHATSPEED7x on 2008-08-08
I just added the force quite button to my bottom tool bar next to the desktop button.

---

### Post by spencer218 on 2008-08-08
> **PHATSPEED7x said:**
> I just added the force quite button to my bottom tool bar next to the desktop button.

How do you add a force quit button ? I am using Xubuntu , will I be able to do that ?  thanks

---

### Post by ooobuntooo on 2008-08-08
> **spencer218 said:**
> How do you add a force quit button ? I am using Xubuntu , will I be able to do that ?  thanks

yeah, how u do that?

---

