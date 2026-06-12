---
title: "List of &quot;int 80h&quot; calls"
date: 2009-05-22
forum: Programming Talk
---

### Post by rCXer on 2009-05-22
Does anyone know where I can find a complete list of "int 80h" calls?  I haven't had much luck with Google.

---

### Post by slavik on 2009-05-22
look for after instealling kernel headers syscall.h

or search for linux syscall assembly

---

### Post by samjh on 2009-05-23
On my system (Arch x86_64 with kernel version 2.6.29)...

x86 call numbers: /usr/lib/klibc/include/asm/unistd_32.h
x86_64 call numbers: /usr/lib/klibc/include/asm/unistd_64.h

function prototypes: /usr/lib/klibc/include/unistd.h

You can also look up specific syscalls by using the section option for man-pages.  Section 2 are the system calls.  You use the form: man -S 2 <syscall>.  So to look up write():
```
man -S 2 write
```

---

### Post by rCXer on 2009-05-25
Are there any online references?

---

### Post by soltanis on 2009-05-25
[http://asm.sourceforge.net/syscall.html](http://asm.sourceforge.net/syscall.html)

---

