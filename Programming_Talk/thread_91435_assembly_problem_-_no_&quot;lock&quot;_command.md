---
title: "assembly problem - no &quot;lock&quot; command?"
date: 2005-11-17
forum: Programming Talk
---

### Post by rattusdatorum on 2005-11-17
Hi!

I am trying to implement a semaphore, well the problem is the inline assembly of gcc doesn't recognize the "lock" command, which is needed prior to cmpxchg to make cmpxchg atomic :(
I am not quite sure why it doesn't works, could it be that it doesn't works because ubuntu uses a 386 architecture and the "lock" command was first used on the
486 architecture?

btw. as (gnu assembly compiler) has the same problem:
cmpxchg.s:6: Error: suffix or operands invalid for `cmpxchg'

if my assumptions is correct is there a way to get "lock" work and how?
if I am wrong, whats the real cause for my problem?

thx in advance

---

### Post by rattusdatorum on 2005-12-11
bump

---

### Post by LordHunter317 on 2005-12-11
Post your assembly, but you're not going to get a truly atomic lock without kernel assistance, unless the lock is meant to be completely internal to your process only.  Why are you trying to revent the wheel anyway?

---

### Post by rattusdatorum on 2005-12-11
oops, well I figured out, I don't need the lock anyway, at least if I stay with single cpu's.

Hmm I don't think need kernel support, because the cmpxchg instruction is only one machine instruction and prevents a race condition, because everything which is needed to prevent/allow entering a critical section is done by cmpxchg


why to reinvent the wheel? Well for better understanding!

asm code: (in Intel syntax!)
```

loop:
  movl eax,1
  cmpxchg 0,1
  jz eax,loop         ! I don't know if the syntax is correct (jump to loop if eax == zero)
criticial section:
  !doSomethingHere

```



c code with inline asm: (AT/T syntax!)
```

void p(int s[1])
{
        while (s[0] == 0) {}; //busy-wait
        int dummy = 0; 
        
        asm("movl $1, %%eax\n\t" // eax = 1;
                "cmpxchg %1, %0" // dummy, semaphore (src, dest); AT/T syntax != Intel Syntax
                :"=r"(s[0]) //output %0
                :"r"(dummy)//input %1
                :"%eax"); //IMPORTANT, don't change eax in the asm command
}

void v(int s[1])
{
        s[0] = 1;
}

```

---

