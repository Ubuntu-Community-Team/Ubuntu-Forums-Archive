---
title: "QT4 Cross Platform"
date: 2010-07-02
forum: Programming Talk
---

### Post by shynthriir on 2010-07-02
I am beginning to write a program which I want to be able to run on a linux machine, windows XP machine, and a windows vista machine. I'm developing the graphics with QT4 on my linux machine. My question is: do I need to compile the program on each machine to get the proper executable file for each system? I've never writing a graphics program to be cross platform before...

---

### Post by Simian Man on 2010-07-02
> **shynthriir said:**
> I am beginning to write a program which I want to be able to run on a linux machine, windows XP machine, and a windows vista machine. I'm developing the graphics with QT4 on my linux machine. My question is: do I need to compile the program on each machine to get the proper executable file for each system? I've never writing a graphics program to be cross platform before...

Yes, you do.  Whenever you use a language that is compiled to machine code you must recompile for each system.

<edit> You won't need to compile on both XP and Vista.  The same executable should work on both just fine.

---

### Post by shynthriir on 2010-07-02
Thanks.

I thought that may be the case, but wanted to make sure before I did got too far into the design process.

---

