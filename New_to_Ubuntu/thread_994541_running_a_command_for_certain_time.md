---
title: "running a command for certain time"
date: 2008-11-26
forum: New to Ubuntu
---

### Post by drsyntax on 2008-11-26
hello,

i want to know if there is a way to run a command that never ends for certain time, i want to do this as i want to use airodump-ng output file with python, but when i run airodump-ng command it keeps running, and it never ends so my program stops at this point :(

thanks,
Tamer

---

### Post by amauk on 2008-11-26
fork airodump-ng and pass the PID to your python script

setup some kind of timer to kill the PID

---

