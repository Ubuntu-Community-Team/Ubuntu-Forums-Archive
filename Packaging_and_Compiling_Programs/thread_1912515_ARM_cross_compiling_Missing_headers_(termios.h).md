---
title: "ARM cross compiling: Missing headers (termios.h)"
date: 2012-01-20
forum: Packaging and Compiling Programs
---

### Post by Mikkelsen on 2012-01-20
Hello,

I have a problem with my ARM cross compiling when I try to compile my project.
It doesnt seems to find my termios header and gives me the error:
*error: sys/termios.h: No such file or directory*

If I then try to change it to *"termios.h*" it gives me the following error:
*#include nested too deeply*

I have been searching for simular problem on the net the whole day, and tried everything that I though could solve the problem but without sucess.

Except that the ARM compiler can't find the header files it works very well.
The ARM compiler I am using is from GNUarm.com (arm-elf)

If anyone knows what might cause this problem or can help me try solve it I really would appreciate it and be very grateful.

Thanks.

---

