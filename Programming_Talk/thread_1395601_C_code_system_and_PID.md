---
title: "C code: system and PID"
date: 2010-02-01
forum: Programming Talk
---

### Post by erotavlas on 2010-02-01
Hi,

How can I get PID of the process called by system call?

---

### Post by Some Penguin on 2010-02-01
man getpid

Or, alternately, syscall (SYS_getpid, specifically).

---

### Post by napz on 2010-02-01
how can i use syscall (SYS_getpid)? any headers i need to include?

---

### Post by Linteg on 2010-02-01
> **napz said:**
> how can i use syscall (SYS_getpid)? any headers i need to include?
[http://www.kernel.org/doc/man-pages/online/pages/man2/syscall.2.html](http://www.kernel.org/doc/man-pages/online/pages/man2/syscall.2.html)
[http://www.kernel.org/doc/man-pages/online/pages/man2/getpid.2.html](http://www.kernel.org/doc/man-pages/online/pages/man2/getpid.2.html)

---

### Post by napz on 2010-02-03
i have this error


`SYS_getppid' undeclared (first use in this function)
(Each undeclared identifier is reported only once
 for each function it appears in.)

hw can i solve it?

i try

cid = syscall(SYS_getpid);
parid = syscall(SYS_getppid);

is it correct?

---

### Post by Zugzwang on 2010-02-03
If you are writing a "regular" application: what's wrong with "getpid"? This way you don't have to mess with kernel calls yourself.

---

### Post by dwhitney67 on 2010-02-03
The OP appears to be MIA.

I think he was asking how to get the PID of a process that is invoked via a system() call.  I could be wrong though!

---

### Post by napz on 2010-02-03
oh.. i need to get pid via system call. i read the article example but i cant compile it.

cid = syscall(SYS_getpid);
parid = syscall(SYS_getppid);
cwdir = syscall(SYS_getcwd);

anithing wrong with the codes?

---

### Post by napz on 2010-02-03
> **dwhitney67 said:**
> The OP appears to be MIA.

I think he was asking how to get the PID of a process that is invoked via a system() call.  I could be wrong though!

Yes. correct. I like to invoked via a system() call. What's OP? How can i get pid ppid and cwd via system call?

---

### Post by Zugzwang on 2010-02-03
> **napz said:**
> Yes. correct. I like to invoked via a system() call. What's OP? How can i get pid ppid and cwd via system call?

Wait, wait, wait. You need to pay a little bit more attention to your usage of the English language as otherwise your question is ambiguous. These sentences allow the following interpretations:

[LIST]
[*] You invoke another program using the system(...) command in C or C++, e.g., system("/usr/bin/myprogram myfile.txt"). This command gives you the error level as return value. However, you also want to know which process ID the process that had been spawned by that command had.
[*] You want to get the process ID of your program at its runtime and try to avoid using getpid() and instead rather want to use a so called system call: [http://en.wikipedia.org/wiki/Syscall](http://en.wikipedia.org/wiki/Syscall) 
[/LIST]

Which one is it?

By the way: "OP" means original poster, i.e., the one who started this thread. However, I must admit that I don't know what "MIA", as used by dwhitney67, means.

---

### Post by napz on 2010-02-03
> **Zugzwang said:**
> Wait, wait, wait. You need to pay a little bit more attention to your usage of the English language as otherwise your question is ambiguous. These sentences allow the following interpretations:

[LIST]
[*] You invoke another program using the system(...) command in C or C++, e.g., system("/usr/bin/myprogram myfile.txt"). This command gives you the error level as return value. However, you also want to know which process ID the process that had been spawned by that command had.
[*] You want to get the process ID of your program at its runtime and try to avoid using getpid() and instead rather want to use a so called system call: [http://en.wikipedia.org/wiki/Syscall](http://en.wikipedia.org/wiki/Syscall) 

[/LIST]

Which one is it?

By the way: "OP" means original poster, i.e., the one who started this thread. However, I must admit that I don't know what "MIA", as used by dwhitney67, means.

the second interpretation. I just want to write a c program in linux to print out the pid ppid cwd when the program is run.

---

### Post by dwhitney67 on 2010-02-03
> **Zugzwang said:**
> 
By the way: "OP" means original poster, i.e., the one who started this thread. However, I must admit that I don't know what "MIA", as used by dwhitney67, means.

MIA = Missing In Action

---

### Post by napz on 2010-02-04
ok now i can print out the process id. but still have error for the parent process id.

int cid = syscall(SYS_getpid);
int parid = syscall(SYS_getppid);

`SYS_getppid' undeclared (first use in this function)

what does this err means? how can i solve it?

ty

---

### Post by Some Penguin on 2010-02-04
You should consider reading the syscall() manpage.

---

### Post by dwhitney67 on 2010-02-04
> **Some Penguin said:**
> You should consider reading the syscall() manpage.

I agree 100%.

Why is it that some programmers find it so damn hard to read the documentation?  Is the internet breeding a generation of lazy programmers.

In an effort that napz learns nothing, other than how to copy one's code, here's a silly example:
```

#include <sys/syscall.h>
#include <sys/types.h>
#include <unistd.h>
#include <stdio.h>
#include <assert.h>

int main()
{
   int   sysPID = syscall(SYS_getpid);
   pid_t getPID = getpid();

   printf("sysPID = %d\n", sysPID);
   printf("getPID = %d\n", (int)getPID);

   assert(sysPID == (int)getPID);

   return 0;
}

```

---

