---
title: "Total computer freezes"
date: 2015-01-31
forum: New to Ubuntu
---

### Post by IpNuCheerios on 2015-01-31
My computer keeps freezing up. It has done it while running a number of different programs that have no visible relation. Is there a linix alternative to windows ctl+alt+del or task manager? If not is there another way to solve this problem with out Hard booting? Also how do I uninstall a program not installed with a software center? Thanks.

---

### Post by Stefan_Vukanovic on 2015-01-31
Try with Ctrl+Alt+F1, it should open tty1. Login and type: "ps -A | grep (your program name)"
It should give you the list of programs currently running whos name contains characters you entered above.
Now, can you see first digits? Those are PIDs, or Process IDs. Now type: "skill (PID)"
That should send the kill signal to the program.
To check is it killed, type "ps -A | grep (your program name)" again.
Notice: If you ran the program as root, you need to add sudo before skill command in order to get rights to kill the program.
So, for example, if I would like to kill firefox, I would type 
~$ ps -A | grep firefox
5539 ?        00:29:26 [COLOR=#ff0000]firefox[/COLOR]
~$ skill 5539
~$ ps -A | grep firefox

---

### Post by grahammechanical on 2015-01-31
Ctrl+Alt+Del can do a restart in Ubuntu. But not always. Especially if the system is not responding. If you can get to a console (Ctrl+Alt+F1) or the terminal (Ctrl+Alt+T) then this command will restart

```
sudo shutdown -r now
```

and this command will shutdown

```
sudo shutdown -h now
```

Regards.

---

