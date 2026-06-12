---
title: "Compiling on ubuntu then running on debian"
date: 2008-05-19
forum: Programming Talk
---

### Post by Hodge Podge on 2008-05-19
Hi.

Right now, my main computer runs ubuntu (gutsy). I have recently set up a server running a bare bones install of debian (etch) with apache. What I would like to do is write and compile my programs on my ubuntu computer (as it is the one I use all the time) and then transfer the binary to the server. I would rather NOT bloat the server system installing gcc and would prefer compiling on my ubuntu machine while keeping the server on the lean side.

Right now, when try running my program on my debian machine, I get an error telling me that "version 'GLIBC_2.4' not found (required by ./myprog)".

I see that on the debian machine that there is a libc-2.3.6.so. How would I tell gcc to have my program link against this library as opposed to the default libraries that would be found on my ubuntu computer?

I posted this over at the debian forum and the only response I got was someone telling me to install a debian system on my ubuntu machine and do a chroot when I wanted to compile my program.  I thought I'd post over here to see if anybody has any other ideas.

Thanks for your help.

---

### Post by dtmilano on 2008-05-19
Static linking would be the solution in most of the cases.

---

### Post by LaRoza on 2008-05-19
> **dtmilano said:**
> Static linking would be the solution in most of the cases.

@OP Here is the gcc option for that:
```

-static-libgcc

```

---

