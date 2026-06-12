---
title: "pid of program itself, c++"
date: 2008-01-12
forum: Programming Talk
---

### Post by monkeyking on 2008-01-12
Is there a command to get the the pid of the running program.

that is, the program itself.

thanks in advancd

---

### Post by amo-ej1 on 2008-01-12
sure there is  man 2 getpid


> 
       #include <sys/types.h>
       #include <unistd.h>

       pid_t getpid(void);
       pid_t getppid(void);

DESCRIPTION
       getpid() returns the process ID of the current process.  (This is often
       used by routines that generate unique temporary filenames.)

       getppid() returns the process ID of the parent of the current  process.



---

### Post by geraldm on 2008-01-12
ps aux output line:
gerald    2658  0.2  1.5   8400  3980 tty1     S    17:20   0:32 /usr/bin/icewm
```

pidof icewm

```
the output:
2658

Gerald

---

### Post by monkeyking on 2008-01-13
thanks,
solved my problems

---

