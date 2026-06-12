---
title: "Memory Problem..."
date: 2005-12-29
forum: Programming Talk
---

### Post by superr on 2005-12-29
I have this book: "Jon Erickson - Hacking The Art Of Exploitation" and it says:
"Luckily, the address of an environment invoked in this manner is easy to calculate. In Linux, the address will be 0xbffffffa, minus the length of the environment, minus the length of the name of the executed program."

But this method isn't working... then i tried something different:

$ export SHELLCODE = <...>

And make a program in C that uses getenv(SHELLCODE)... but the memory address always change... 
superr@bruno:~/test$ ./get_addr
SHELLCODE is located at 0xbfa519ce
superr@bruno:~/test$ ./get_addr
SHELLCODE is located at 0xbfe319ce

Anyone can help me to understanding anyone of this methods?

---

### Post by coredump on 2005-12-29
I think the book is wrong.  Your little test program has shown that the address is not constant at all, but changes from one run to the next.  Maybe the book was written for a very old version of Linux?  Or for Linux based on a different architecture than you are using?

Perhaps you could post the source code for your test program?

I certainly wouldn't expect the environment to be located at a fixed address in any Unix-like system.  In MS-DOS, maybe it is (or was..).

---

### Post by superr on 2005-12-29
Thk, it seems is a stack protection in Linux 2.6 (adds some randomisation).

---

