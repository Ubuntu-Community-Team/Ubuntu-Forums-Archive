---
title: "can getty run a program other than shell?"
date: 2008-11-14
forum: New to Ubuntu
---

### Post by sahra_kavir on 2008-11-14
Hi,

I have discovered that getty first runs a login program and 
after verifying the password, it runs (possibly forks) the shell
program. 
I am a bit confused... can getty run a program other than shell and X window?
in the case of mgetty (for modems) probably a program other than shell is running?
can we bind a virtual console to a new serial port or serial device? 
Do all the virtual terminals running (1 to 6) do the same thing?
They are just shell programs to work with the system and nothing else?
and the last thing: there in the linux source code can I find the getty related code?

---

### Post by kerry_s on 2008-11-14
open a terminal and type> man getty

---

