---
title: "Help in gedit for C programming"
date: 2010-07-03
forum: Programming Talk
---

### Post by mrkorig on 2010-07-03
hi, i have created a simple C code in gedit, but i have problems in compiling.

cc -c sample.c works fine in the terminal

but when i input cc -o sample sample.c it gives me this msgs.

mark@mark-laptop:~$ cc -o sample sample.c
/usr/bin/ld: cannot open output file sample: Is a directory
collect2: ld returned 1 exit status


thank u in advance for the help

---

### Post by Milliways on 2010-07-03
> **mrkorig said:**
> hi, i have created a simple C code in gedit, but i have problems in compiling.

cc -c sample.c works fine in the terminal

but when i input cc -o sample sample.c it gives me this msgs.

mark@mark-laptop:~$ cc -o sample sample.c
/usr/bin/ld: cannot open output file sample: Is a directory
collect2: ld returned 1 exit status


thank u in advance for the help

Do you have a directory "sample" ?
This seems to be what the error message is telling you.

---

### Post by StephenF on 2010-07-04
Agree with the first reply. Call your program something else or rename that directory.

---

### Post by mrkorig on 2010-07-04
i got it ur right i got a folder named sample..

thanks so much for the help...

---

