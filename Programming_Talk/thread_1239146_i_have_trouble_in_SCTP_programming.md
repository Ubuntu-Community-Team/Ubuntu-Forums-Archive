---
title: "i have trouble in SCTP programming"
date: 2009-08-13
forum: Programming Talk
---

### Post by retsuseiba on 2009-08-13
when i compile file this error message is show up

undefined reference to 'sctp_sendmsg'
collect2 : ld returned 1 exit status

how can i fix this problem?

thanks for all comment

---

### Post by regala on 2009-08-13
> **retsuseiba said:**
> when i compile file this error message is show up

undefined reference to 'sctp_sendmsg'
collect2 : ld returned 1 exit status

how can i fix this problem?

thanks for all comment

without a complete description (content of Makefile, maybe content of source code, but in this case shouldn't be necessary, last command issued by make if you were using make...), it may be difficult to debug your problem.
from what I see, you have got a linkage error, meaning that your C code was correctly compiled, but the executable could not be created because you didn't tell in which library to look for the SCTP API.

If you have just one C file and you tried
```
gcc file.c
``` it couldn't create an executable because, by default, gcc doesn't look for other libraries than libc.
here it should be ```
gcc -lsctp file.c
``` which creates the executable a.out.
you should definitly read the GCC manual and a quick introduction to executable format linkage.

br, mathieu

---

### Post by retsuseiba on 2009-08-13
thanks alot regala i can run it

thank you very much:P

---

