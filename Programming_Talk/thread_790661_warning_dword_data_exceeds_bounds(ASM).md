---
title: "warning: dword data exceeds bounds(ASM)"
date: 2008-05-11
forum: Programming Talk
---

### Post by Chicken Dinner on 2008-05-11
warning: dword data exceeds bounds

That's the warning I am getting from NASM for these instructions:
    push 15
    push 13

The program will run but not anything like it's supposed to, so hopefully eliminating that warning will fix it.

I've looked through example codes that have told me to use these very same instructions, so this problem has me quite baffled.  Any help will be greatly appreciated.

---

### Post by RIchard James13 on 2008-05-12
push seems to have three opcodes for immediate mode. One each for 8bit, 16bit and 32bit data. You might need to prefix your data with the size you are trying to tell it to push down on the stack. Otherwise it won't know how many bits to use.

Most of the sample code I have seen seems to use dword.
```
        push    dword fmt       ; address of format string

```
Maybe that is because of the size of the stack is expected to be 32bit?

---

### Post by Chicken Dinner on 2008-05-12
That very well could be it.
Now I can continue my attempt to figure out the rest of this assembly business.
Thanks for the answer!

---

### Post by NathanB on 2008-05-12
> **Chicken Dinner said:**
> warning: dword data exceeds bounds

That's the warning I am getting from NASM for these instructions:
    push 15
    push 13



You are looking at the wrong lines.  Those two instructions are perfectly legal and do not produce warnings.  However, a line something like this...
```
     mov eax, 23548489665745
```
...will produce the warning that you quote.  So look for something of that nature...  or post the full source here.

Also, there is the possibility that you've gotten a broken version of Nasm (it has experienced rapid development recently); so download the latest daily build and try again.

[ftp://ftp.zytor.com/pub/nasm/snapshots/](ftp://ftp.zytor.com/pub/nasm/snapshots/)

Nathan.

---

### Post by Chicken Dinner on 2008-05-12
Yeah, I was looking at the wrong lines, but I figured it out.  I think my version of NASM is alright since that's the only problem I had (and I solved it).  But I'll keep that in mind if I have any other trouble.
Thanks for the advice.

---

### Post by jal_nl on 2008-09-08
Just for those who find this thread via a google: I experienced the same problem, and it in my case it is *not* another line, but the push-line. As suggested by someone above, adding dword between push and the immediate value fixes the warning. So e.g.:

```
push 1
```

should be:

```
push dword 1
```


JAL

---

