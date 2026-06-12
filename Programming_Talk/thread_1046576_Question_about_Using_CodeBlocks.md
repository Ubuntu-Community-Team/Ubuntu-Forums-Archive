---
title: "Question about Using CodeBlocks"
date: 2009-01-21
forum: Programming Talk
---

### Post by flylehe on 2009-01-21
Hi,
I have some problems regarding how to add source code already given in CodeBlocks.
1. I created an empty project and added my c file "eg1.c" into it. When I hit the build button, I recieved such an error message "Fatal error: can't create obj/Debug/program/eg1/eg1.o: No such file or directory".
2.  when I started over with adding my c file to the workspace instead of creating an empty project and adding to int my  file, I can build and run although the are is no project but I cannot debug.

Thanks for help!

BTW: I did some search but couldn't find any tutorial explaining the same issue. Maybe that is too straightforward? I appreciate if someone could let me know if there are some.

---

### Post by PC-XT on 2009-02-14
Have you tried creating directory obj/Debug/program/eg1 manually?

---

### Post by jondiced on 2009-02-21
Hey PC-XT,

I'm having the same problem and I have tried creating the directory manually. The same error comes up, "Couldn't create the project directory: <directory>"

> **PC-XT said:**
> Have you tried creating directory obj/Debug/program/eg1 manually?

Flylehe, have you had any sucess?

---

### Post by PC-XT on 2009-02-22
Sometimes that happens if the disk [partition] is full (or not enough space to create necessary files) or the folder is marked as read-only (or permission trouble).

I also just discovered these two threads on the subject from the Code::Blocks forums:
[http://forums.codeblocks.org/index.php?topic=8508.0](http://forums.codeblocks.org/index.php?topic=8508.0)
[http://forums.codeblocks.org/index.php?topic=9965.0](http://forums.codeblocks.org/index.php?topic=9965.0)

I'm not sure if they have been solved yet, but maybe they will be soon? Someone said it worked to use the home directory.

---

