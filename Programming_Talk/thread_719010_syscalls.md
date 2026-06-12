---
title: "syscalls"
date: 2008-03-08
forum: Programming Talk
---

### Post by itendtoinfinity on 2008-03-08
Hello, 
so i want to list all syscalls a program uses. can anyone give me a pointer? how can i do this C programming. 

thank you.

---

### Post by unutbu on 2008-03-08
This will dump the system calls to tmp.out
```

strace gedit 2> tmp.out

```

Change gedit to whatever you want.

---

### Post by itendtoinfinity on 2008-03-08
i know about strace. i want to travel with the execution thread and see what syscalls are used and print them along the way, also time them. BUT i don't know how to implement this in C programming language.

that's where i need help.

---

### Post by stroyan on 2008-03-08
It is not clear to me what you want that strace will not provide.
You can get the time of syscalls from strace with the -ttt option.
You can get the time in each syscall with the -T option.
You can see the source code for strace.
You may also be interested in the ltrace command that reports shared library calls using a similar mechanism.

---

### Post by itendtoinfinity on 2008-03-08
i just want to write my own code to better understand how things work. it's not that i don't want to use strace or ltrace or systemtap or whatever. i just began working with kernel modules but i can't figure out this issue.

so please help.

---

### Post by unutbu on 2008-03-08
Sorry for presuming you just wanted strace. Your knowledge probably far exceeds mine. Have you considered downloading the source code for strace and seeing how it does it? Probably easier said than done...

---

### Post by Mr. C. on 2008-03-09
For you to trace system calls, you need to intercept the basic system call trap that occurs, and for this you need a) to link into the application, and b) learn how a system call is handle by the machine's exception handlers.  Each program is linked with the C runtime library, which provides this support.  You need to work at this level.

Alternatively, you can operate at the same level as a debugger, which executes instruction traps in one or more forms.

---

### Post by the_unforgiven on 2008-03-09
This wikipedia page gives general understanding of strace:
[http://en.wikipedia.org/wiki/Strace](http://en.wikipedia.org/wiki/Strace)

The main syscall that allows you/strace to trace the process execution is called [ptrace(2)]("http://linux.die.net/man/2/ptrace").

HTH ;)

---

