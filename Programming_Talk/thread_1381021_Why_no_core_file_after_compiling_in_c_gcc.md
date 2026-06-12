---
title: "Why no core file after compiling in c gcc?"
date: 2010-01-14
forum: Programming Talk
---

### Post by ThePhilosopher57 on 2010-01-14
Hi all
 
I'm suposed to get a core file after compiling with this command : 
[SIZE=2]gcc -D_GNU_SOURCE bloc.c -o wipeout [/SIZE]
[SIZE=2]I have also try :[/SIZE]
[SIZE=2][SIZE=2]gcc -g -D_GNU_SOURCE bloc.c -o wipeout [/SIZE]
 
[SIZE=2]and no sing of the core file.[/SIZE]
 
[SIZE=2]I am suposed to see 
[SIZE=2](core dumped) at the end of the compliation process but I don't.[/SIZE]
 
[SIZE=2]thanks for the help.[/SIZE]
[/SIZE][/SIZE]

---

### Post by MadCow108 on 2010-01-14
why should you get a coredump after compiling?
unless you manage to crash gcc you won't.

coredumps are the memory state of a process to a certain time.
so you at least need to execute your program to get one and also this only if you have enabled coredumps, have enough space reserved (ulimit -c) and your program crashes or explicitly requests a coredump.

---

### Post by ThePhilosopher57 on 2010-01-14
> **MadCow108 said:**
> why should you get a coredump after compiling?
unless you manage to crash gcc you won't.
 
coredumps are the memory state of a process to a certain time.
so you at least need to execute your program to get one and also this only if you have enabled coredumps, have enough space reserved (ulimit -c) and your program crashes or explicitly requests a coredump.
 
 
Well, I got this from a book to learn programming in c for Linux.
I guess he did a mistake or something.
 
He is really saying there should be a core file after compiling. Maybe the source code should crash gcc but it's not what he say and it's not crashing it.

---

### Post by MadCow108 on 2010-01-14
he probably means there should be a core dump after compiling and executing.
getting gcc to crash is hard and if you manage please file a bug report.

Is there an abort() in the source code?
that function creates an abnormal termination of the process and a core dump (when enabled)

---

### Post by zippaplick on 2010-01-15
Also note you probably need to run "ulimit -c unlimited" in the shell before trying to generate a core file.  Otherwise the core file size is set to 0 by default and it wont get generated.

---

### Post by ThePhilosopher57 on 2010-01-15
> **MadCow108 said:**
> he probably means there should be a core dump after compiling and executing.
getting gcc to crash is hard and if you manage please file a bug report.

 
:D
 
 
> **MadCow108 said:**
> 
Is there an abort() in the source code?
that function creates an abnormal termination of the process and a core dump (when enabled)
 
No, I don't think so. I'll try this, give you some news tomorow.
 
thanks

---

### Post by ThePhilosopher57 on 2010-01-15
> **zippaplick said:**
> Also note you probably need to run "ulimit -c unlimited" in the shell before trying to generate a core file. Otherwise the core file size is set to 0 by default and it wont get generated.
 
 
I will try this too. 
Thanks.

---

### Post by ThePhilosopher57 on 2010-01-15
Yes, you are right. I have not read corectly. There is an error on the codesource and the compiler do not see it. But when I run the program, it crash.
 
But I see no core file anyway, I have try the unlimit command of **zippaplick.**

---

