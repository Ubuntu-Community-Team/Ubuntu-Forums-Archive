---
title: "Stack Smashing"
date: 2007-02-03
forum: Programming Talk
---

### Post by EricDallal on 2007-02-03
Hello, I just ran a program C++ program that I created a while back for the first time on Ubuntu. The program was originally created on Windows using Dev C++ and run on cygwin and on a number of different distributions of Linux. I never obtained an error before, but now I obtain a "stack smashing error":

*** stack smashing detected ***: ./cluster terminated
Aborted (core dumped)

I assume that the complaint is some kind of stack overflow? The program traverse a tree of a thousands of nodes in size (which I have no reason to believe is a balanced tree). The final output seems to print, but I am not certain that the file output was complete. I have a number of questions.

1) Can this feature be disabled?

2) Is it possible to determine whether or not the program really completed?

3) In cygwin, I was able to look at the stack dump file after a crash. Is there something equivalent that I can do here?

---

### Post by Lux Perpetua on 2007-02-03
I think "stack smashing" refers to a buffer overflow clobbering data on the stack. That would be a serious enough bug in your program that  I wouldn't advise looking for ways to disable the feature (unless you feel like participating in the "fun with buffer overflow" thread). 

You should get a debugger, like GDB. Running the program in the debugger would show where it crashed, so you'd know if the output completed or not. If I'm not mistaken, GDB can also help you read a core dump, but I've never used that feature.

---

### Post by lnostdal on 2007-02-03
1: you most likely do not want to do that as there is probably a bug in your program that should be fixed instead of ignored
2: it did not complete; it was "aborted" as stated
3: i think you'll get more info if you compile with -g then run your application under gdb .. when things crash type bt and press enter and you'll get a backtrace

---

### Post by jblebrun on 2007-02-03
You can also turn on core dumps using the **ulimit** command. By default, core dump max size is set to zero. You can enable arbitrary-size core dumps using:
```

ulimit -c unlimited

```

---

### Post by EricDallal on 2007-02-03
Isn't it weird that I never had any problems when running the program on other operating systems though? I think I've run it on at least 3 other operating systems. Also, regarding the core dump file, is that the same thing as a stack dump file? I know that I've seen systems dump the entire memory in use by the program to a text file when it crashes. Is a core dump file the memory in use by the program or simply the stack?

---

### Post by jblebrun on 2007-02-03
> **EricDallal said:**
> Isn't it weird that I never had any problems when running the program on other operating systems though? I think I've run it on at least 3 other operating systems. Also, regarding the core dump file, is that the same thing as a stack dump file? I know that I've seen systems dump the entire memory in use by the program to a text file when it crashes. Is a core dump file the memory in use by the program or simply the stack?

It's not that weird. When it comes to memory related bugs, different operating systems have different behavior. There are lots of things that behave differently under different OSs. 

A core dump is all of the memory in use by the program.

---

### Post by lnostdal on 2007-02-03
> **EricDallal said:**
> Isn't it weird that I never had any problems when running the program on other operating systems though? I think I've run it on at least 3 other operating systems.

just note that a program "working" like this is not a good thing.. the error is _still_ there, even when the program works for years..  any random thing can trigger the error .. it might suddenly start crashing almost all the time (minor change in an external library?) or only crash occasionally at random times every other day

a program that "works" like this is actually wayway worse than something that fails instantly and predictably every time because of the error which really is there .. sadly this is not how things are in C; these kinds of errors are not prevented by the language itself

edit: uhm, i thought i was answering another post about an almost similar issue .. oh well

---

### Post by LordHunter317 on 2007-02-03
The reason is that Windows didn't include stack-smashing detection support in MSVC until recently.  Your code is likely missing it.

Your code on Linux likely isn't  If the code must absolutely run without modifications, you can recompile the code with stack smashing support disabled.  I forget the GCC option, however it is in the documentation.

---

### Post by EricDallal on 2007-02-04
I checked it out in GDB and figured out the error immediately. Turns out you guys were right, there was a bug in my code. But it had nothing whatsoever to do with tree traversal or with too many stack frames (there were only 6; of those, only 2 belonged to my program, and only one other than main). This is why I was doubtful that there was an error. I've had stack overflows before but usually when there is some kind of loop. Since I know the program can terminate and give meaningfull output, I found that extremely unlikely. Here is the error:

char name[10];
sprintf(name, "%s%d%s", "Tree", root->num_leaves, ".txt");

root->num_leaves is a number over a thousand, so I hadn't allocated enough memory to name. Changing it to:

char name[20]

fixed the problem entirely (yes, I know this is a newbie error and that I'm always supposed to allocate more memory than I need). Does anyone know why this is called a "stack smashing" error?

---

### Post by LordHunter317 on 2007-02-04
Local storage is stack allocated.  You overran the space on the stack into another portion of memory.

BTW, you can't trust the output of gdb in thise case for hte number of frames, because the bug trashes the stack in it's error.  

Also, use snprintf or slprintf or similiar, please.  Especially after making an error such as this.

---

### Post by Wybiral on 2007-02-04
Whew... I can tell you that that is a dangerous error that can easily result in exploits. As Lux Perpetua mentioned, check out the "fun with buffer overflow" thread... Thats how all of that is done. Writing things outside of an array's dimensions can cause some very unwanted behavior ranging from changing the value of other variables to changing the return address of functions (which can cause some seriously strange errors since you have no idea what machine code will end up being executed... If it's even machine code)

---

