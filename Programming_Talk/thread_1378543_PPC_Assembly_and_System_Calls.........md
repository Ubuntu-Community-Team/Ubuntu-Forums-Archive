---
title: "PPC Assembly and System Calls........"
date: 2010-01-11
forum: Programming Talk
---

### Post by navic on 2010-01-11
I'm trying to learn PowerPC assembly on a iBook with Ubuntu. I've searched google and this forum for a system call reference that shows the input/output in the form of PPC assembly.  There's some x86 resources out there but that doesn't help me with PPC.  To illustrate my point I'll show you the only system call I found full I/O for:

(always place system call in r0)
System Call 4 = write
Input:
r3 = destination (0 = stdin, 1 = stdout, etc)
r4 = buffer address
f5 = length

I still don't know what other values I can use for the destination, a file handle maybe?  Playing around with a System Call Quick Reference (just names and numbers) I figured out that syscall 3 read will take a single character from stdin and put it into a buffer specified by r4.  It's pretty much impossible to figure out all 190+ syscalls.

If there's a resource out there that clarifies system calls, parameters and values for PPC I'd really want that link!

Thanks!

---

### Post by rajatkhanduja on 2011-07-12
Hi

I realize that this post is very old; but that makes me hopeful that you might have found some resource in the meanwhile. I have been looking for PPC input/output and other syscall related information for quite some time but have not been able to find it. 

If you have some information/link , please share. 

Thanks .

---

### Post by slavik on 2011-07-13
this isn't java ranch. closing.

---

