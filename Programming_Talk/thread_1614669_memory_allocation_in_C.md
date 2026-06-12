---
title: "memory allocation in C"
date: 2010-11-05
forum: Programming Talk
---

### Post by c2tarun on 2010-11-05
what if we allocate certain amount of memory by malloc at the beginning of the program but dont free it at the end???
will it be remain like that or when the program terminates it will be freed automatically.

---

### Post by TiBaal89 on 2010-11-05
It will be freed.  I think that task gets thrown to the OS if you don't do it yourself.  In something like Ubuntu, I'd definitely expect it would be freed.

---

### Post by trent.josephsen on 2010-11-05
It probably will be freed, but you should free it anyway.  There are systems where malloc'ed memory is not freed on program termination, and the C standard says nothing about the matter, so don't depend on it.

A good rule of thumb (for C) is to structure your program so that a call to malloc() and the corresponding call to free() are in the same subroutine.

---

### Post by saulgoode on 2010-11-05
More specifically, memory is allocated to a particular process and will automatically be freed when that process terminates. (So if your program forks a process which malloc's some memory then when that process ends, the malloc'ed memory will automatically be free'd, even though your *program* is still running.)

---

### Post by msakms on 2010-11-05
The Linux kernel memory management procedure insures that the allocated memory address space is cleaned up once the process is terminated 
Resource "Understanding the Linux Virtual Memory Manager"

---

