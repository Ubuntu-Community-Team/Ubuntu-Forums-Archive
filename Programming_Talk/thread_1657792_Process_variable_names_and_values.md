---
title: "Process variable names and values"
date: 2011-01-01
forum: Programming Talk
---

### Post by Kesarion on 2011-01-01
Hello, is there something like a process memory scanner for ubuntu that I can use to find variables in a process and change values ?

I'd also like to learn how to do this in C++ but I don't know where to start since I'm new to ubuntu. I do know basic to advanced C++ I learned it when I had windows.

So where would I start learning how to do this ? I want to use this on games, like cheats, changing health, view distance, and whatever is changeable.

---

### Post by worksofcraft on 2011-01-01
> **Kesarion said:**
> Hello, is there something like a process memory scanner for ubuntu that I can use to find variables in a process and change values ?

I'd also like to learn how to do this in C++ but I don't know where to start since I'm new to ubuntu. I do know basic to advanced C++ I learned it when I had windows.

So where would I start learning how to do this ? I want to use this on games, like cheats, changing health, view distance, and whatever is changeable.

Variable names are stripped out of compiled code by the linker because it's just a waste of space to keep them in there after it has been compiled. You can use the -g switch that retains debugging information and then you can access these variables using the run-time debugger, gdb.

However that is no use to you for cheating at games unless you have the source code to compile from and also cheating at games ruins it for everyone reducing it into a contest of who is the biggest cheat :P

---

### Post by Kesarion on 2011-01-01
Well that was just an example, I thought it would be easier to start there :)
The idea is learning not cheating, I don't like cheating.

I'll check out gdb.

---

