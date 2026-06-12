---
title: "Java heap size, bigger than memory?"
date: 2007-09-24
forum: Programming Talk
---

### Post by ppl on 2007-09-24
To run Weka, I need a relative huge heap size for Java VM. 

When I tried in Windows it will allocate maximum 1.2G ram for Java using Xmx if I am lucky, in a machine with 2 G ram; but in Ubuntu however I can easily get 2G out of 1G ram and 1.5G swap.

How could it managed do that, I mean as we know that you can't get more memory than what available to you more than hardware? And you need some memory for OS and other application as well?

Is Ubuntu or Java doing some kind of cheating?

---

### Post by Tuna-Fish on 2007-09-24
Virtual memory.

The application only ever sees a 2GB flat address space (on 32 bit), or 131TB flat address space (on 64 bit ). How much of that is in actual ram, how much is on disk in swap, or how much is not even allocated yet, is entirely out of control of the application, and is decided by the kernel.

---

### Post by CptPicard on 2007-09-24
Theoretically, from a software point of view on a virtual memory OS, you've got as much RAM as you can address... whether there actually is as much available as RAM+swap is a whole different matter, and the OS will just complain when it runs out of real space ;)

Seems to me that Windows is just somehow extra cautious...

---

### Post by ppl on 2007-09-24
> **CptPicard said:**
> 
Seems to me that Windows is just somehow extra cautious...

Yeah, that is the bit I am not sure: is it safe or optimal solution to give away such a big chunk of memory to Java. But I think since Linux did that way, it must have reasons for believe it will be safe or optimal.

But in fact, for some reason, my machine running unusually slow after giving out 2G memory to Java, actually it is unusable and I need ctrl + Alt + Backspace to shut it down. 

After all, I think Linux just give more control to the hand of user about how memory could use for what, and assume users know what they are doing.

---

### Post by ppl on 2007-09-24
The title totally make no sense now as I realized later that my swap size is 1.5G not 0.5G as I thought before, and was surprised that it could managed  give Java more memory than it has in Ram + swap.

---

### Post by ppl on 2007-09-24
Another update, I managed allocated 4G memory in Linux for Java VM in a machine with 2G ram and 1G swap and I assume the it is a 32bit system. Weka runs much more happier than the prerious one and at least I can still post to forums now:).

---

### Post by Ramses de Norre on 2007-09-25
> **ppl said:**
> But in fact, for some reason, my machine running unusually slow after giving out 2G memory to Java, actually it is unusable and I need ctrl + Alt + Backspace to shut it down.

Doesn't surprise me much... Java'll use the memory it gets when needed, if that's almost all your memory then yes, other apps will need to swap everything and will run terribly slow...
Solution: give healthy values to java;)

---

### Post by ppl on 2007-09-25
> **ppl said:**
> Another update, I managed allocated 4G memory in Linux for Java VM in a machine with 2G ram and 1G swap and I assume the it is a 32bit system. Weka runs much more happier than the prerious one and at least I can still post to forums now:).

This time, it suffered the same from previous one eventually and I think Java VM crushed by it self. It was a fun experiments, but I wasted my good half day:(.

---

