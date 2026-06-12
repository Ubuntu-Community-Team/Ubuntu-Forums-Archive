---
title: "64 bit applications ... duh what?"
date: 2007-07-24
forum: Programming Talk
---

### Post by destructchaos on 2007-07-24
so, i was reading a thread in the gutsy dev forum about 64 bit apps not working quite right some this guy was using the 32 bit version instead and that got me wondering:  what is the difference between 32 bit coding and 64 bit coding.  is it just the libraries that are used when compiling, because i'm sure that 64 bit "hello world" source would look the same as its 32 bit equivalent?

thanks for any clarifications you can make to my cloudy view of the 64 bit world.

---

### Post by slavik on 2007-07-25
a hello world program yes, but something doing memory access could be different, because a pointer on a 64bit system is most likely 8 bytes instead of 4.

also, think of an ipv4 address ... it currently needs only 4 bytes, so on a 64bit system when you store it in a register that is 64bits, you need to handle the other half of the register (even though you don't have to bother since amd64 allows things like eax, ax, al, ah)

---

### Post by destructchaos on 2007-07-25
ok, so some things are handled differently by the compiler, but is there any difference in the code that i would write for a 64 bit system?

---

