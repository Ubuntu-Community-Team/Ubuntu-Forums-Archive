---
title: "[C] Is Ubuntu not exporting the _syscall macros? Why?"
date: 2007-09-06
forum: Programming Talk
---

### Post by lilcoder on 2007-09-06
Hi,
I'm having a serious problem accessing the syscalls from C. I'm following this paper [http://www.ibm.com/developerworks/linux/library/l-system-calls/](http://www.ibm.com/developerworks/linux/library/l-system-calls/) and it seems that Ubuntu doesn't have the _syscall macros in /usr/include/linux/unistd.h . Has anybody a clue about it or knows some ubuntu developer I can contact about this topic?

bye

---

### Post by talowe on 2007-09-06
> **lilcoder said:**
> Hi,
I'm having a serious problem accessing the syscalls from C. I'm following this paper [http://www.ibm.com/developerworks/linux/library/l-system-calls/](http://www.ibm.com/developerworks/linux/library/l-system-calls/) and it seems that Ubuntu doesn't have the _syscall macros in /usr/include/linux/unistd.h . Has anybody a clue about it or knows some ubuntu developer I can contact about this topic?

bye

On my system, unistd.h includes <asm.unistd.h>, which includes (depending what  macros are defined) either <asm-x86_64/unistd.h> or <asm-i386/unistd.h>.

They have a whole bunch of defines.

---

### Post by fct on 2007-09-07
The _syscall* macros are obsoleted in newer kernels, for most architectures. Bad luck, the article seems to have been written few months before they were removed.

---

### Post by lilcoder on 2007-09-07
@talowe: yes there are the syscalls defined but no macros...

@fct: could you explain shortly how to do it now on newer kernels or point me to a place where it is described? it would be very nice :)

---

### Post by lilcoder on 2007-09-20
and up again...

---

### Post by hod139 on 2007-09-20
You can use syscall().  See man 2 syscall.

---

### Post by lilcoder on 2007-09-20
I know I can use syscall() but that's not what I want ;) syscall() is accessing the libC which then wrappes around the actual syscalls. But the _syscallN-macros give direct access to the syscalls without going through the libC.

---

### Post by hod139 on 2007-09-20
I guess I wasn't being clear.  The _syscall macros were removed from the headers starting around kernel version 2.6.18.  This was not a ubuntu decision, but the kernel developers decision.  You have to use syscall(2).

---

### Post by lilcoder on 2007-09-20
ohh ftc already said something in this direction, so they are defentifly depreciated :( then I'll have to use syscall() thanks

---

### Post by [h2o] on 2007-09-20
Is there any special reason why you want to access the syscalls directly instead of using the syscall wrapper?

---

### Post by lilcoder on 2007-09-20
yes I wanted them to use within a lkm (kernel module) and I can't access the libC through that.. so now I have to find another way. I want e.g. just to open a file on my HD and read it within a lkm.

---

### Post by Lux Perpetua on 2007-09-20
You can prevent dynamic linking with the **-static** option to GCC. That'll force the compiler to pull any libc dependencies into your program. Would that work for you?

---

### Post by lilcoder on 2007-09-20
No I think I can't access the libC from inside the kernel.

---

### Post by [h2o] on 2007-09-21
> **lilcoder said:**
> No I think I can't access the libC from inside the kernel.
I am no kernel expert, but if it is compiled statically, then I don't understand why it wouldn't work. It should be very easy to test.

---

### Post by Lux Perpetua on 2007-09-21
> **'[h2o] said:**
> I am no kernel expert, but if it is compiled statically, then I don't understand why it wouldn't work. It should be very easy to test.That's what I was getting at. 

lilcoder, would it work if you wrote your own replacement for syscall() and compiled it with the rest of your code? Because linking it statically from libc has the same effect. All libc dependencies in your code would be eliminated by the linker, but the linker would require a statically linkable libc library file, if that might be a problem. 

I'm sorry if I'm way off-base here; I don't know much about kernel modules.

---

### Post by winch on 2007-09-22
The kernel is open source. Look at other kernel modules that do what you want and see how they do it.
Something like khttpd which is a kernel space web server.
[http://www.linux.it/~rubini/docs/khttpd/](http://www.linux.it/~rubini/docs/khttpd/)
[http://www.linux.it/~rubini/docs/ksys/](http://www.linux.it/~rubini/docs/ksys/)

---

