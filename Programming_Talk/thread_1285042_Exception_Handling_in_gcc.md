---
title: "Exception Handling in gcc"
date: 2009-10-07
forum: Programming Talk
---

### Post by vgokul on 2009-10-07
Hello all,
I am new to exception handling and I have some problems. Can you please help?
 
I have a legacy code that has divide by zero error at the start for the first few function calls but has no functional effect if they are ignored (I have checked this in Windows with SEH). Now I need the same in the Linux environment and I tried in a smaller test code that is representative of my original code - please see the code below. The exception is ignored the first time but in the second call float point exception occurs. Can you please let me know how to handle this? Is this the correct way to handle this?
 
 
[SIZE=2][COLOR=#0000ff][SIZE=2][COLOR=#0000ff]#include[/COLOR][/SIZE][/COLOR][/SIZE][SIZE=2][COLOR=#800000][SIZE=2][COLOR=#800000]<stdio.h>[/COLOR][/SIZE]
[/COLOR][/SIZE][SIZE=2][COLOR=#0000ff][SIZE=2][COLOR=#0000ff]#include[/COLOR][/SIZE][/COLOR][/SIZE][SIZE=2][COLOR=#800000][SIZE=2][COLOR=#800000]<signal.h>[/COLOR][/SIZE]
[/COLOR][/SIZE][SIZE=2][COLOR=#0000ff][SIZE=2][COLOR=#0000ff]#include[/COLOR][/SIZE][/COLOR][/SIZE][SIZE=2][COLOR=#800000][SIZE=2][COLOR=#800000]<setjmp.h>[/COLOR][/SIZE]
[/COLOR][/SIZE][SIZE=2][COLOR=#0000ff][SIZE=2][COLOR=#0000ff]void[/COLOR][/SIZE][/COLOR][/SIZE][SIZE=2] test();[/SIZE]
[SIZE=2]jmp_buf sjbuf;[/SIZE][SIZE=2][COLOR=#008000][SIZE=2][COLOR=#008000]/*Buffer to store stack position*/[/COLOR][/SIZE]
 
[/COLOR][/SIZE][SIZE=2][COLOR=#0000ff][SIZE=2][COLOR=#0000ff]void[/COLOR][/SIZE][/COLOR][/SIZE][SIZE=2] handler([/SIZE][SIZE=2][COLOR=#0000ff][SIZE=2][COLOR=#0000ff]int[/COLOR][/SIZE][/COLOR][/SIZE][SIZE=2] signum)[/SIZE]
[SIZE=2]{[/SIZE]
[SIZE=2][COLOR=#0000ff][SIZE=2][COLOR=#0000ff]if[/COLOR][/SIZE][/COLOR][/SIZE][SIZE=2](signum == SIGFPE)[/SIZE]
[SIZE=2]printf([/SIZE][SIZE=2][COLOR=#800000][SIZE=2][COLOR=#800000]"Handler called - Signal error is SIGFPE\n"[/COLOR][/SIZE][/COLOR][/SIZE][SIZE=2]);[/SIZE]
[SIZE=2]signal(SIGFPE, handler);[/SIZE][SIZE=2][COLOR=#008000][SIZE=2][COLOR=#008000]/*Refresh the handle*/[/COLOR][/SIZE]
[/COLOR][/SIZE][SIZE=2]longjmp(sjbuf,1); [/SIZE][SIZE=2][COLOR=#008000][SIZE=2][COLOR=#008000]/* return to saved state */[/COLOR][/SIZE]
[/COLOR][/SIZE][SIZE=2][COLOR=#0000ff][SIZE=2][COLOR=#0000ff]return[/COLOR][/SIZE][/COLOR][/SIZE][SIZE=2];[/SIZE]
[SIZE=2]}[/SIZE]
 
[SIZE=2][COLOR=#0000ff][SIZE=2][COLOR=#0000ff]int[/COLOR][/SIZE][/COLOR][/SIZE][SIZE=2] main()[/SIZE]
[SIZE=2]{[/SIZE]
[SIZE=2]signal(SIGFPE, handler);[/SIZE]
[SIZE=2][COLOR=#008000][SIZE=2][COLOR=#008000]//signal(SIGFPE, SIG_IGN);[/COLOR][/SIZE]
[/COLOR][/SIZE]
[SIZE=2]printf([/SIZE][SIZE=2][COLOR=#800000][SIZE=2][COLOR=#800000]"Inside main\n"[/COLOR][/SIZE][/COLOR][/SIZE][SIZE=2]);[/SIZE]
[SIZE=2][COLOR=#0000ff][SIZE=2][COLOR=#0000ff]if[/COLOR][/SIZE][/COLOR][/SIZE][SIZE=2](setjmp(sjbuf)==0) [/SIZE][SIZE=2][COLOR=#008000][SIZE=2][COLOR=#008000]/* save current stack position */[/COLOR][/SIZE]
[/COLOR][/SIZE][SIZE=2]{[/SIZE]
[SIZE=2]printf([/SIZE][SIZE=2][COLOR=#800000][SIZE=2][COLOR=#800000]"Saved Stack\n"[/COLOR][/SIZE][/COLOR][/SIZE][SIZE=2]);[/SIZE]
[SIZE=2]test();[/SIZE]
[SIZE=2]}[/SIZE]
 
[SIZE=2]printf([/SIZE][SIZE=2][COLOR=#800000][SIZE=2][COLOR=#800000]"Continuing main\n"[/COLOR][/SIZE][/COLOR][/SIZE][SIZE=2]);[/SIZE]
[SIZE=2][COLOR=#0000ff][SIZE=2][COLOR=#0000ff]if[/COLOR][/SIZE][/COLOR][/SIZE][SIZE=2](setjmp(sjbuf)==0) [/SIZE][SIZE=2][COLOR=#008000][SIZE=2][COLOR=#008000]/* save current stack position */[/COLOR][/SIZE]
[/COLOR][/SIZE][SIZE=2]{[/SIZE]
[SIZE=2]printf([/SIZE][SIZE=2][COLOR=#800000][SIZE=2][COLOR=#800000]"Saved Stack\n"[/COLOR][/SIZE][/COLOR][/SIZE][SIZE=2]);[/SIZE]
[SIZE=2]test();[/SIZE]
[SIZE=2]}[/SIZE]
[SIZE=2]getchar();[/SIZE]
[SIZE=2][COLOR=#0000ff][SIZE=2][COLOR=#0000ff]return[/COLOR][/SIZE][/COLOR][/SIZE][SIZE=2] 1;[/SIZE]
[SIZE=2]}[/SIZE]
[SIZE=2][COLOR=#0000ff][SIZE=2][COLOR=#0000ff]void[/COLOR][/SIZE][/COLOR][/SIZE][SIZE=2] test()[/SIZE]
[SIZE=2]{[/SIZE]
[SIZE=2][COLOR=#0000ff][SIZE=2][COLOR=#0000ff]int[/COLOR][/SIZE][/COLOR][/SIZE][SIZE=2] x;[/SIZE]
[SIZE=2][COLOR=#0000ff][SIZE=2][COLOR=#0000ff]int[/COLOR][/SIZE][/COLOR][/SIZE][SIZE=2] y;[/SIZE]
[SIZE=2]printf([/SIZE][SIZE=2][COLOR=#800000][SIZE=2][COLOR=#800000]"Inside test\n"[/COLOR][/SIZE][/COLOR][/SIZE][SIZE=2]);[/SIZE]
[SIZE=2]y= 0;[/SIZE]
[SIZE=2]x = 1/y;[/SIZE]
 
[SIZE=2]}[/SIZE]
 
[SIZE=2]Regards[/SIZE]
[SIZE=2]V.Gokul[/SIZE]

---

### Post by dwhitney67 on 2009-10-07
Use sigsetjmp() so that your signal handler setup is preserved.

```

...
if (sigsetjmp(sjbuf, SIGFPE)==0)
...

```

---

### Post by vgokul on 2009-10-12
Hi ,
     Thanks. It works.
 
Is the use of signal and jmp functions the only way to handle this or is there a better way - when the function itself that generates the divide by zero error cannot be changed?
 
Regards
V.Gokul
 
PS: Sorry for a delayed response. I was out of office for the last few days.

---

### Post by grayrainbow on 2009-10-12
Divide by zero is in general something undefined. On x86 integer divizon by zero produce hardware exception and Linux will inform you with signal for this, so in this case signals are the best IMO. But...in general Linux does not run only on x86, some platforms will happily consider this as zero.

---

