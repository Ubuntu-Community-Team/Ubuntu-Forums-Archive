---
title: "How can I compile such a C code?"
date: 2008-02-03
forum: Programming Talk
---

### Post by intijk on 2008-02-03
```

int main()
{
       char far *p;
       asm{
                    mov ax,0ffffh
        }
       return 0;
}
```


Can gcc do it? or other compilers? Could you give me an answer particularly?
I'll  appreciate it.

---

### Post by aks44 on 2008-02-03
Two points of interest:

1) **char far *p**
Linux, like many other *_modern_* operating systems, only supports flat addressing in 32-bit (or 64-bit) protected mode. The **far**, **near** etc modifiers are relics from the 16-bit real mode PC era, they've been deprecated more than 10 years ago.

2) inline assembly: gcc uses the AT&T syntax (in fact, gcc relies on gas which in turn uses that syntax) rather than the Intel syntax which is common on Microsoft platforms.


So basically, I'd say that such code is both too outdated and platform-specific to compile on Linux. You'd probably have trouble compiling it on (a recent) Windows too, given its age.

---

### Post by intijk on 2008-02-03
Thank you for your reply.

I'll try to change the inline assembly to AT&T syntax.
I'm developing a OS, so I need to run code in real mode .Then jump to protected mode. I need far pointer, can any way to use it ?





By the way, forgive my bad english.

---

### Post by aks44 on 2008-02-03
Ok, I assumed this was application-level code... :)


I can't really help you more on that specific matter, but I can suggest you to look into the Linux kernel source code, specifically the bootstrap part and the whole build process (I know gcc has flags to generate "free-standing" code that doesn't require a working kernel/libc to execute correctly).
My best guess regarding far pointers would be to write the real mode bootstrapping part in pure assembly, and switch to protected mode ASAP so you can use C. Don't quote me on that though...


Hope this helps anyway, and good luck. :)

---

