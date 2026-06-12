---
title: "Urgent buffer=*END*"
date: 2006-04-17
forum: Programming Talk
---

### Post by mbb on 2006-04-17
Hi everyone,
I need to run an executable in my ubuntu, this executable is basically basicle complied version of a script containing namd2,vmd commands and some several shell comands like grep. I personally did not create the executable and don't have the source source code. I receive an error message like :
Reason: FATAL ERROR: ABNORMAL EOF FOUND - buffer=*END*
Do you have any idea how to fix that problem. Is this buffer problem related with my machine or any part of linux ? Same executable works with red hat 3.

Thanks for help....
mbb

---

### Post by thumper on 2006-04-18
chances are that an executable that works with red hat 3 (do you mean fedora core 3?) will not work with ubuntu without being recompiled.

Recompile under ubuntu and try again.

---

### Post by mbb on 2006-04-18
Sorry I solved the problem, one of my input files had an unneccesary whiteline. Thta was the problem.
It is the first time I have seen this kind of error message.
sorry...

and thanks for the reply

mbb

[QUOTE=mbb]Hi everyone,
I need to run an executable in my ubuntu, this executable is basically basicle complied version of a script containing namd2,vmd commands and some several shell comands like grep. I personally did not create the executable and don't have the source source code. I receive an error message like :
Reason: FATAL ERROR: ABNORMAL EOF FOUND - buffer=*END*
Do you have any idea how to fix that problem. Is this buffer problem related with my machine or any part of linux ? Same executable works with red hat 3.

Thanks for help....
mbb[/QUOTE]

---

