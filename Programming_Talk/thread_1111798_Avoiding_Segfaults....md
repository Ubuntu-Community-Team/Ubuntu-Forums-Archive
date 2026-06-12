---
title: "Avoiding Segfaults..."
date: 2009-03-31
forum: Programming Talk
---

### Post by zjagannatha on 2009-03-31
I am using C++ for class, and I was wondering if there was a unix command that will allow me to see if a specific position in memory was used.
For example,
```

int main(){
    int *p;
    p = 5; // p points to spot 5 in memory
    *p = 25; // integer at p is 25
}

```
In some cases this would return a segfault, in others it would run. Either way, I am trying to access memory that doesn't belong to my program. Is there any way to test and see if a spot in memory has been reserved to another program?

Thanks

---

### Post by movieman on 2009-03-31
> **zjagannatha said:**
> Is there any way to test and see if a spot in memory has been reserved to another program?

Assuming you're running a version of Unix with a memory management unit (i.e. pretty much anything other than a low-power embedded CPU), then all the memory your program can see belongs to it... the memory management unit separates the address space of each process from every other process, and you have to deliberately set up shared memory regions if you want two processes to be able to see the same area of memory.

I'm surprised your program ever runs without crashing, I thought Linux set the lowest memory page to read-only to catch writes to NULL pointers.

---

### Post by Arndt on 2009-03-31
> **zjagannatha said:**
> I am using C++ for class, and I was wondering if there was a unix command that will allow me to see if a specific position in memory was used.
For example,
```

int main(){
    int *p;
    p = 5; // p points to spot 5 in memory
    *p = 25; // integer at p is 25
}

```
In some cases this would return a segfault, in others it would run. Either way, I am trying to access memory that doesn't belong to my program. Is there any way to test and see if a spot in memory has been reserved to another program?

Thanks

It will not be the case that you access memory that belongs to another process, but it will probably be the case that you access memory that your process hasn't allocated, and that will result in a segmentation violation.

You can see (as text) what memory your process is using, by looking at /proc/maps/1234 (if the pid of your process is 1234). See "man proc".

If you want to guard against your program doing things like that (at runtime), you can use the 'valgrind' program. It doesn't preclude the errors, but it shows exactly where they happen.

To guard against it at compile time, turn on compiler warnings - the compiler should warn against "p = 5". (You did it intentionally, but at some other time, it may happen inadvertently.)

If you do want to communicate with another process by letting both see the same memory area, you can do that with the system call 'mmap'.

---

### Post by zjagannatha on 2009-03-31
What I'm trying to do is to make a program that will track and archive memory usage at a specific point in time. To do that, I would need to have a function that (at the very least) tells if a place in memory has been allocated or not. It would also be nice to see, if it has been allocated, which process is using it. Is there a function that will tell me any of this?

---

### Post by Frank Kotler on 2009-04-01
getrusage(), and perhaps getrlimit() might interest you. I haven't explored 'em much, and I'm not really sure how to interpret what they return.

You might be interested in observing a few of those /proc/<pid>/maps files. Notice that all programs start at 0x08048000! From there, depending on how much code is in the program, is "section .text" - readable and executable, but not writable. c=*p would work, but *p=c would segfault (I think). Following that is "section .data" - readable/writeable, but not executable. This is where your "static" variables would be located. "p" should work fine, in that range. Following that is "section .bss", uninitialized memory (actually initialized to zero by the loader). Same attributes as ".data". Following that is the "break". Attempting to access memory above that will segfault. But the "break" can be moved to allocate more memory. I'm familiar with the low-level int 80h sys_brk function - brk() and sbrk() work slightly different. You wouldn't normally do that - malloc() would do it (and associated housekeeping) for you.

Then (in those maps files) you'll see memory starting at 0x4000000. This is where mmap() allocates memory. In any but an idiot-simple assembly language program, the dynamic linker will have mapped libc and a bunch of other stuff into this area. Protection can be read/write/exec, so "p" would depend on what mmap() had done. I think trying to access memory in that numerical range that *hadn't* been mmapped would segfault - haven't tried it. That 0x4000000 number is the default - we can ask to mmap memory at other numerical ranges that we normally wouldn't have access to, such as below 0x08048000. I don't know what the "limit" is - answer in getrlimit, perhaps?

Above that is the stack - starts at 0xC0000000 and works down, so when we first see it, it's probably 0xBFFF???? - since args and environment pointers are on the stack at startup, the exact number is not predictable. Stack should be readable/writeable/executable, I think, so "p" ought to work in that range. The stack is "dynamic" - if we run off the bottom of it, the memory-manager will map in a new page for us, and we can keep going. This is accomplished (I understand) by a "guard page" below the valid stack pages, marked "not present". If we attempt to access this, it causes a page fault, but instead of throwing SIGSEGV, the handler maps in a new page for us... and presumably a new guard page under it. I imagine this comes to an end when the stack, going down, meets mmapped memory, going up. Dunno what happens, but I'll bet it's not good! Above 0xC0000000, dunno.

You may be able to predict whether accessing "p" would segfault or not by abusing another system call. I've used access(). Supposed to tell us if a *file* is accessable (or exists) for read/write, etc. But if the "path" (first) parameter points outside of valid memory, instead of segfaulting, returns -EFAULT. We don't *expect* there to be a file at "p", so we don't expect it to succeed, but if the error is -EFAULT, don't try to access "*p"! (this technique gives puzzling results in certain Slackware distros, in an xterm only - very strange!) I just noticed in the man page that getrlimit and getrusage behave the same way if the pointer to buffer (structure) is out of range, so maybe we could kill two birds with one stone! Experiment - it's only ones and zeros! :)

But to get back to your question, if you wanted to know if some arbitrary address in your process - say 0x0804A000 - was allocated to another program - say by reading the other program's /proc/<pid>/maps file - you'd probably find that it was. Yet the two programs don't conflict! This is made possible by the magic of "virtual memory". I'm fuzzy on the details, but essentially our "memory addresses" are actually indexes into page tables (a heirarchy of 'em) which eventually say what physical memory is involved. If any! If your system is out of physical memory, the memory manager will swap some page(s) of RAM off to disk (your swap partition), and map that physical memory into a process that needs it. If that swapped out page is then needed, it's swapped back to physical RAM - perhaps not at the same address it was at before... (this slows the system, so we want to avoid it)

So even if you could find out that virtual 0x08048001 (the letter 'E' in your ELF header, most likely) was at physical 0x1234, it wouldn't help you much. 0x08048001 is also allocated to "Program B", but not at the same physical address - at least, not at the same time - unless your memory-manager's broken.

So it isn't really possible/useful to do what you want. A Protected Mode OS is protected from *us*, y'know! But you *can* get some information about memory usage. Besides the /proc/<pid>/maps files, look at /proc/meminfo. Running "top" (as root) and watching it for a while is interesting, too. Memory usage doesn't stand still! I imagine that the source code for "top" and/or whoever is creating /proc/meminfo would probably be enlightening, if you want to get into it at that level.

Best,
Frank

---

